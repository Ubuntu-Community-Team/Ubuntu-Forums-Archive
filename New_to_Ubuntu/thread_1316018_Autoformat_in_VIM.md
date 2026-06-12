---
title: "Autoformat in VIM"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by noorez on 2009-11-05
here is my current .vimrc file

:syntax on
:set number
:set cindent
:set smartindent
:set noexpandtab

the additions I want to make are:

a tab key will be width of 4
no spaces should be used to fill the tabs
the auto indenting should insert enough tabs of width 4 as well

what do i need to add on to .vimrc ?

---

### Post by harakiri1976 on 2009-11-12
try:
```
:set tabstop=4
```


Here is mine .vimrc:
```

set showmatch
set expandtab
set tabstop=4
set shiftwidth=4
set nocompatible
set number
syntax on

```

---

### Post by feodor on 2011-03-09
You should use following configuration :

```
:set tabstop=4 softtabstop=4 shiftwidth=4 noexpandtab
```

Tabs will have four columns wide. Each indentation level is defined in one tab.

---

