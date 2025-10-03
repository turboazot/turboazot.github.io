---
layout: page
title: категории
permalink: /categories/
---

<div class="categories-grid">
  {% assign sorted_categories = site.categories | sort %}
  {% for category in sorted_categories %}
    {% assign category_name = category[0] %}
    {% assign posts = category[1] %}
    {% assign post_count = posts | size %}
    
    <a href="{{ '/category/' | append: category_name | append: '/' | relative_url }}" class="category-card">
      <div class="category-icon">
        {% if site.data.categories[category_name].icon %}
          {{ site.data.categories[category_name].icon }}
        {% else %}
          📚
        {% endif %}
      </div>
      <h2 class="category-name">
        {% if site.data.categories[category_name] %}
          {{ site.data.categories[category_name].name }}
        {% else %}
          {{ category_name }}
        {% endif %}
      </h2>
      <div class="category-stats">
        <span class="post-count">{{ post_count }}</span>
        <span class="post-label">
          {% if post_count == 1 %}
            пост
          {% elsif post_count >= 2 and post_count <= 4 %}
            поста
          {% else %}
            постов
          {% endif %}
        </span>
      </div>
      <div class="recent-posts">
        <div class="recent-label">Последние посты:</div>
        <ul>
          {% for post in posts limit:3 %}
            <li>{{ post.title | truncate: 40 }}</li>
          {% endfor %}
        </ul>
      </div>
      <div class="view-all">Смотреть все →</div>
    </a>
  {% endfor %}
</div>

<style>
.categories-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 2em;
  max-width: 1000px;
  margin: 2em auto;
}

.category-card {
  display: block;
  background: white;
  border: 1px solid #e8e8e8;
  padding: 2em;
  text-decoration: none !important;
  color: inherit;
  cursor: pointer;
}

.category-card:hover {
  text-decoration: none !important;
  border: none;
  padding: calc(2em + 1px);
}

.category-card *,
.category-card *:hover {
  text-decoration: none !important;
}

.category-icon {
  font-size: 3em;
  margin-bottom: 0.5em;
  text-align: center;
}

.category-name {
  margin: 0 0 1em 0;
  font-size: 1.8em;
  text-align: center;
  color: #111;
}

.category-stats {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5em;
  margin-bottom: 1.5em;
  padding: 0.8em;
  background: #f7f7f7;
}

.post-count {
  font-size: 2em;
  font-weight: bold;
  color: #2a7ae2;
}

.post-label {
  font-size: 0.9em;
  color: #666;
}

.recent-posts {
  margin-bottom: 1.5em;
  padding-top: 1em;
  border-top: 1px solid #f0f0f0;
}

.recent-label {
  font-size: 0.85em;
  color: #999;
  margin-bottom: 0.5em;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.recent-posts ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.recent-posts li {
  font-size: 0.9em;
  color: #666;
  padding: 0.3em 0;
  padding-left: 1em;
  position: relative;
}

.recent-posts li::before {
  content: '•';
  position: absolute;
  left: 0;
  color: #2a7ae2;
}

.view-all {
  text-align: center;
  color: #2a7ae2;
  font-weight: 500;
  font-size: 0.95em;
  padding-top: 1em;
  border-top: 1px solid #f0f0f0;
}

@media (max-width: 768px) {
  .categories-grid {
    grid-template-columns: 1fr;
    gap: 1.5em;
    padding: 0 1em;
  }
  
  .category-card {
    padding: 1.5em;
  }
  
  .category-name {
    font-size: 1.5em;
  }
}
</style>


