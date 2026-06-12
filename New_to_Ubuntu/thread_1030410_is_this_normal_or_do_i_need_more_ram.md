---
title: "is this normal? or do i need more ram?"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by mishkin on 2009-01-04
I have a little ram meter on the right panel and it ussually says something like this: 33% in use by programs, 66% in use by cache

so 99% used... does that mean 1gb ram isn't enough?? Or will it always fill the ram with cacheing all the way?


Also where on the web do I go to find gui programs for ubuntu?

atm I am running urn eee 8.10 ubuntu (I got rid of most of the remix thing though) with gnome

so I guess I'm only interested in gnome applications??

thx

---

### Post by shifty_powers on 2009-01-04
it's perfectly normal, linux will just cache your ram, don't worry :D

[http://www.faqs.org/docs/linux_admin/buffer-cache.html](http://www.faqs.org/docs/linux_admin/buffer-cache.html)

> To make the most efficient use of real memory, Linux automatically uses all free RAM for buffer cache, but also automatically makes the cache smaller when programs need more memory.

---

### Post by zvacet on 2009-01-04
@ **mishkin**

I don´t know what exactly you are looking for,but [this]("http://www.gnomefiles.org/") shold be helpful.

---

### Post by linux_tech on 2009-01-04
what is output of
```
free -m
```

---

### Post by stderr on 2009-01-04
Full (or as close to) RAM usage is optimal. Logically, consider:

you copy a bunch of files that total 600MB from one directory to another. You have perhaps 200MB RAM used, therefore 800MB free. 

The contents of these files will be placed in RAM as they're copied. So, why not leave them all in RAM? If you need more RAM later for something else, the data can be copied over... but if it remains and you want to access one of those files later, you can simply retrieve it from RAM. No need to get it from a SLOW hard drive :)

What it's telling you is that only 33% of our RAM is actually needed at that point in time, and the rest is being used as cache... similar to the scenario above.

When considering if you need more RAM, it's always good to check how much swap space is/has been used. A swap file is a file on a hard drive which is used to store temporary data, i.e. stuff which should be put in RAM, when you run out of RAM. Under Ubuntu, no swap space is used unless you run out of RAM. This is optimal, because hard drives are **much, much** slower than RAM, so when swap files are used, this slows things down considerably. Under Windows, swap files tend to get used... a lot... seemingly regardless of RAM levels.

So, if you goto System Monitor (Alt + F2, System Monitor) and click the Resources tab, if you're regularly seeing the Swap indicator there showing quite a bit of swap load (100s of MB, perhaps), then that could be an indicator that a lack of RAM is an issue. 

Don't forget though, that if you had a lot of programs open, and swap has quite a bit in, that if you then close a load of programs, your available RAM (RAM which isn't "in use by programs") may increase considerably, but swap may still stay the same size. It depends which programs loaded their code first, while there was still available RAM :)

edit: As for GUI programs for Ubuntu, there are loads. Check your Synaptic Package Manager (under System -> Administration) for tens of thousands of software packages from ubuntu repositories. You can enable more repositories too. A simpler interface with a subset of packages is available under Applications -> Add/Remove...

When possible it's best to install from the repositories using Synaptic, the Add/Remove app, or the command line with apt. This way, the packages will be automatically updated and upgraded. If you download and install software from web/FTP sites yourself, you will have to upgrade that software automatically.

---

### Post by mishkin on 2009-01-04
thx for all the replys


the output for the guy that asked is

mishkin@mishkin-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           999        977         22          0         11        603
-/+ buffers/cache:        363        636
Swap:         3175          3       3172

---

### Post by The Cog on 2009-01-04
> **stderr said:**
> 
When possible it's best to install from the repositories using Synaptic, the Add/Remove app, or the command line with apt. This way, the packages will be automatically updated and upgraded. If you download and install software from web/FTP sites yourself, you will have to upgrade that software automatically.
Absolutely. This is a change in mind-set for Windows users, and is very important for your mental well-being. Often, any software you just download from the web will need compiling from source. This isn't anywhere near as hard on Linux as it is on Windows - in fact on Windows it's essentially impossible. But it can be daunting all the same, especially for newbies who've never compiled anything in their lives before. The repos should always be your first resort when looking for software.

---

### Post by oldos2er on 2009-01-04
"Also where on the web do I go to find gui programs for ubuntu?"

 I would start by searching Synaptic Package Manager, or Add/Remove Programs, whichever you prefer.

Edit: I just wanted to add that more RAM isn't necessary, but it's nice to have. Plus it's so cheap right now, it's difficult to resist buying more.

---

