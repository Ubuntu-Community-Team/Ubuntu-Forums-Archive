---
title: "Installing Command Programs"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by walkerchuckwalker on 2010-05-23
How do you install command line programs? Are scripts and command line programs the same? Are there any repos that have helpful command programs?

---

### Post by UnknownFear on 2010-05-23
Could you maybe elaborate on what exactly you are wanting to know? If you mean by installing applications/programs via the terminal, you only need "apt-get". For example. say I wanted to install the Empathy IM client. I would open a terminal and type:

```
sudo apt-get install empathy
```

---

### Post by lovinglinux on 2010-05-23
> **walkerchuckwalker said:**
> How do you install command line programs?

The same way, although I'm not sure they are available in the Software Center, because I don't use it. Nevertheless, you can find any program available in the Ubuntu repositories using Synaptic Package Manager (System >> Administration >> Synaptic). Search for "command-line" and you will find a lot of programs.

> **walkerchuckwalker said:**
> HAre scripts and command line programs the same?

No. Scripts are essentially a bunch of commands put together in a file and executed one after another. They can interact with each other, to create a complex data flow or not. Command-line programs are just programs that don't have a graphical interface and thus are only controlled from command-line. Nevertheless, some command-line programs might be scripts as well, which depends on the language used to create the program.

> **walkerchuckwalker said:**
> Are there any repos that have helpful command programs?

The Ubuntu repositories are full of them, but unless you are looking for something specific, searching form them might be overwhelming.

---

### Post by wojox on 2010-05-23
Try 

```
sudo apt-get install irssi
```

It's a great cli IRC client. 

[http://www.irssi.org/](http://www.irssi.org/)

---

### Post by qjmoss on 2010-05-24
I agree, give irssi a go.

not only will it allow you to get comfortable with looking at a terminal, but if you use IRC, it's a great client :D

---

