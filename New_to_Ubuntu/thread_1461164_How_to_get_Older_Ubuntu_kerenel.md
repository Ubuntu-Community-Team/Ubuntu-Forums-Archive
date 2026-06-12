---
title: "How to get Older Ubuntu kerenel?"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by jestinjoy on 2010-04-23
From where could I get older versions of Ubuntu Kernels. Please help

---

### Post by byStanderone on 2010-04-23
...you can do a search for the kernel that you are looking for in the ubuntu package repository...clik the dropdown window of your browser and use the ubuntu package search engine, rather than google.

---

### Post by akand074 on 2010-04-23
> **jestinjoy said:**
> From where could I get older versions of Ubuntu Kernels. Please help

```
sudo apt-get install linux-image-(the kernal you want) 
```

you can always press tab twice to bring up a list of all of them. Or easier if you don't know the name off hand is to go to System > Administration > Synaptic Package Manager and just do a quick search for it and install it.

---

### Post by jestinjoy on 2010-04-23
> **akand074 said:**
> ```
sudo apt-get install linux-image-(the kernal you want) 
```

you can always press tab twice to bring up a list of all of them. Or easier if you don't know the name off hand is to go to System > Administration > Synaptic Package Manager and just do a quick search for it and install it.



when i tried for older kernel versions. It says couldnt find the package. New versions are there in the repository.

---

### Post by akand074 on 2010-04-23
> **jestinjoy said:**
> when i tried for older kernel versions. It says couldnt find the package. New versions are there in the repository.

hmm, how old are you thinking? The only supported kernels as far as I'm aware is the kernel that came installed when you first installed the OS and later

---

### Post by jestinjoy on 2010-04-24
2.6.11 ...

---

### Post by akand074 on 2010-04-24
> **jestinjoy said:**
> 2.6.11 ...

I'm pretty sure Jaunty comes default with 2.6.28-something, you would probably have to manually download and install it because it might not be in the repositories or it might not be supported and you'd have to recompile the kernel yourself. Though if the kernel is not in the repositories and its not installing correctly even if it is, then its past my knowledge. Sorry I can't be of more help.

---

### Post by snowpine on 2010-04-24
> **jestinjoy said:**
> 2.6.11 ...

All supported Ubuntu kernels are here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

It looks like the oldest is 2.6.15 (Dapper Drake)... 2.6.11 is 5 years old and untested with 9.10, what is the goal of your project?

---

### Post by jestinjoy on 2010-04-24
Thanks for the link. I was trying to add a new system call. When I tried it in the new kernel , it didnt work. So thinking of going back some versions and trying againn:(

---

### Post by Kafubie on 2010-04-24
Don't you mean different versions?
I am **confus** OP 
:confused::confused::confused::confused::confused::confused:

---

### Post by jestinjoy on 2010-04-29
hi,

I was studying how to add a new system call. i tried in new kernel it didnt work. So I thought of doing it in some older kernel. 2.6.18 like that. :)

---

