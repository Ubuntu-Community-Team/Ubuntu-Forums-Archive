---
title: "Wireless not working on HP 625, using Ubuntu 12.04.3 LTS"
date: 2013-11-10
forum: Networking &amp; Wireless
---

### Post by Niemil on 2013-11-10
I just installed **Ubuntu 12.04.3 LTS** on my computer **HP 625**.

The wireless network worked right in the start of the installation, I had the two options that I wanted to install updates and install 3 part plugin (or something) checked in as I continued.
However, short after the wireless network stopped to work and I haven't got to get it working.
Now I sitting on wire network and it works (but very uncomfortable sitting here where I am now).

I need to make this work, I been on "System settings" doing a scan for "Additional drivers", but it didn't find anything.

I been reading this topic ( [[COLOR=#008C00]**[all variants]**[/COLOR] HOWTO post a Wireless issue (ticket)]("http://ubuntuforums.org/showthread.php?p=6183681") ) and I don't really understand 100% of the commands and what I want out of it.
Shall I write the commands in the terminal and post the answers I get here? and shall I be connected to internet at all while doing this? I am currently on wire.

Thanks in advance.
*I also got 2 errors in start of Ubuntu, saying something in BIOS is turned off, but that's off topic but in case if that may have some problem with this wireless internet.*

[edit]
After google more on the topic, I found a deutsch forum on this. But I quite not understand what they do:
[http://translate.google.com/translate?sl=de&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&u=http%3A%2F%2Fforum.ubuntuusers.de%2Ftopic%2Fwlan-auf-hp--6511%2F&act=url](http://translate.google.com/translate?sl=de&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&u=http%3A%2F%2Fforum.ubuntuusers.de%2Ftopic%2Fwlan-auf-hp--6511%2F&act=url)

But it seems like they getting it to work, so it should work.

---

### Post by Bucky Ball on 2013-11-10
Post the output of these two commands:

```
sudo lshw -C network
iwconfig
```

If you're online with a cable, update and check Additional Drivers.

---

### Post by Niemil on 2013-11-10
> **Bucky Ball said:**
> Post the output of these two commands:

```
sudo lshw -C network
iwconfig
```

If you're online with a cable, update and check Additional Drivers.

Hey! I got wireless working now! :)
I were making some update on Ubuntu, and now somehow the wireless works :)
Thanks !

---

