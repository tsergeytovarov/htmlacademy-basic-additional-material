#Типичные ошибки, которые совершают студенты начиная использовать БЭМ

###Лесенка

Каждый внутренний блок начинается с имени элемента родителя. При этом, получается, что вложенные элементы не имеют никакого отношения к родителю.
```html
<div class="block__element">
  <div class="element__element2">
    <div class="element2__element3">
      ...
    </div>
  </div>
</div>
```

В данном случае, правильный вариант заключается в замене всех новых блоков на вложенные элементы
```html
<div class="block__element">
  <div class="block__element2">
    <div class="block__element3">
      ...
    </div>
  </div>
</div>
```

###Множественные элементы
Каждый вложенный элемент получает не только класс блока, но и класс элемента родителя.
```html
<nav class="navigation">
  <ul class="navigation__list">
    <li class="navigation__list__item">
      ...
    </li>
  </ul>
</nav>
```
Классы с несколькими вложенными элементами не допускаются. Верный вариант кода ниже.
```html
<nav class="navigation">
  <ul class="navigation__list">
    <li class="navigation__item">
      ...
    </li>
  </ul>
</nav>
```

###Потеря базового класса при использовании модификатора
```html
<nav class="navigation">
  <a href="#" class="navigation__link">Link1</a>
  <a href="#" class="navigation__link--active">Link2</a>
  <a href="#" class="navigation__link">Link3</a>
</nav>
```
В данном примере вторая ссылка получит только стили модификатора, при этом базовые стили потеряны. Верный вариант, когда ссылка имеет и базовый класс и класс модификатор.
```html
<nav class="navigation">
  <a href="#" class="navigation__link">Link1</a>
  <a href="#" class="navigation__link navigation__link--active">Link2</a>
  <a href="#" class="navigation__link">Link3</a>
</nav>
```
