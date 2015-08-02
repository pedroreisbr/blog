---
layout: default
title:  Blog PK
subTitle: Um pouco mais sobre TI & Telecom
date: "0001-01-01 00:00:00 America/Araguaina"
published: true
categories: post jekyll
tag: principais assuntos do blog
---

<section id="posts">
  {% assign enum = page.pager.init %}
  {% for post in site.posts %}
    {%if post.title != page.title %}
      {% capture thecycle %}{% cycle 'a', 'b' %}{% endcapture %}
        <div class="content-section-{{thecycle}}">
          <div class="container">
            <div class="row">
              <div class="col-md12">
                <div class="clearfix"></div>
                <h2> $ {% increment enum %} - {{ post.title | downcase  }} # <small> {{ post.subTitle }} </small></h2>
                {{ post.date | localize: "%A, %-d de %B de %Y" }}
                <br />
                {% for category in post.categories %}
                  {% capture button %}{% cycle 'primary', 'success', 'info', 'warning', 'danger' %}{% endcapture %}
                  {% assign url = '/posts/category/' | append: category | append: '/' | prepend: site.baseurl %}
                    <a class="btn btn-{{button}} btn-xs" href="{{url}}">
                    {{category}}
                    </a>
                {% endfor %}
                {{ post.excerpt | markdownify }}
                <a class="btn btn-default btn-lg pull-right" href="{{ post.url | prepend: site.baseurl }}">Saiba Mais <span aria-hidden="true">&rarr;</span></a>
              </div>
            </div>
          </div>
        </div>
    {% else %}
      {% increment enum %}
    {% endif %}
  {% endfor %}
</section>
