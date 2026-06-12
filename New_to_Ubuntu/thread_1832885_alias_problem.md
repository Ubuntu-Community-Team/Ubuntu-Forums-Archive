---
title: "alias problem"
date: 2011-08-25
forum: New to Ubuntu
---

### Post by tgroves10 on 2011-08-25
i just installed ubuntu and to execute i have to type ./a.out and i would like to be able to do it with just a.out. i used gedit to edit .bashrc. when in .bashrc i added (alias a.out='./a.out')
without the parenthesis then i saved it exited out and ran touch .bashrc but when i use the command a.out it doesnt work.....can anyone help please

---

### Post by CharlesA on 2011-08-25
You'd have to use the full pah in the alias.

---

### Post by tgroves10 on 2011-08-25
so what do i need to do to be able to type a.out in the command line and it be able to work

---

### Post by fdrake on 2011-08-25
where is the a.out stored?

---

### Post by bodhi.zazen on 2011-08-25
> **tgroves10 said:**
> so what do i need to do to be able to type a.out in the command line and it be able to work

Easiest way is to put a.out in ~/bin

log out and back in ;)

If you want an alias you need to use the full path to a.out

alias a.out='/home/you/some_directory/a.out'

---

### Post by CharlesA on 2011-08-25
> **bodhi.zazen said:**
> easiest way is to put a.out in ~/bin

log out and back in ;)


+1 :)

---

