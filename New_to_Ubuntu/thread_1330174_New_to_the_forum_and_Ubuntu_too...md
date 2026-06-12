---
title: "New to the forum and Ubuntu too.."
date: 2009-11-18
forum: New to Ubuntu
---

### Post by mukulverma2408 on 2009-11-18
Hello Friends......

I am completely new to Ubuntu, please give me some suggestion on how can i improve my experience of working with ubuntu and also how can i do C programming in this new enviorment.:KS

---

### Post by camaron1 on 2009-11-18
Hi mukulverma2408, 

Have you installed yet?
You probably want to install **ubuntu restricted extras** to allow you watch flash and play many other media.
 
I recommend you install **ubuntu-tweak **from [here]("http://ubuntu-tweak.com/downloads") . Once installed you can very easily add many other repositories included **medibunto** repository.

Good luck and welcome

---

### Post by mvalviar on 2009-11-18
Check out the nice ubuntu e-book on the sticky. If you are to start doing c programming in ubuntu. Start with ```
sudo apt-get install built-essential
``` That will install stuff you need to build c programs.

---

### Post by Zoot7 on 2009-11-18
Codeblocks is a frontend to GCC that's quite nice for C programming, it's what I use for C.
```
sudo apt-get install codeblocks
```
And here's a great resource when it comes to getting started with Ubuntu.
[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)

Welcome too btw! :)

---

### Post by t0p on 2009-11-18
> **mukulverma2408 said:**
> Hello Friends......

I am completely new to Ubuntu, please give me some suggestion on how can i improve my experience of working with ubuntu and also how can i do C programming in this new enviorment.:KS

It's a tad difficult to suggest how your Ubuntu experience can be improved when you don't tell us what exactly you want from Ubuntu.  Ask a specific question and we can help.

The simplest way to program in C: first of all install the package build-essential: open a terminal **Applications > Accessories > Terminal ** ans type in:

```
sudo apt-get install build-essential
```

Now open a text editor (eg gedit **Applications > Accessories > Text Editor** and type in your code.  Save the file as, for example, file.c.  Open a terminal  and use the program **gcc** like so:

```
gcc file.c
```and your C program will be compiled, as filename **a.out**.

There's obviously a lot more to it than that, but that's the bare bones of it.  A web search for "c programming in linux" will turn up many excellent guides.  There are also integrated development environments available for Ubuntu, look in Synaptic **System > Administration > Synaptic Package Manager**, do a search for programming.

---

