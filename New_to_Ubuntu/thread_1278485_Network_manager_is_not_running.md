---
title: "Network manager is not running"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by HomoGleek on 2009-09-29
Hi

Sometimes when my USB dongle gets knocked the network manager stops running, meaning I cant reconnect.

Is there any way too restart it without restarting ubuntu?

(Not really sure what forum this belongs in?)

---

### Post by Michael.Godawski on 2009-09-29
```
sudo /etc/init.d/networking restart
```This is what I use. But you need to remain the terminal window into which you type this open, you close it, nm-applet closes too. ;)

---

### Post by HomoGleek on 2009-09-29
> **Michael.Godawski said:**
> ```
sudo /etc/init.d/networking restart
```This is what I use. But you need to remain the terminal window into which you type this open, you close it, nm-applet closes too. ;)

Many Thanks :)

Is there anyway too create a shortcut for the 'command' (is command the correct term?)
for example is there anyway I could create a icon for it, or say I type something like networkmanstart in terminal and it would run that 'command', as I **will** forget this :P

---

### Post by rasungod_7 on 2009-09-29
Yes.

Right click on the desktop and select "create launcher"

Name it what ever you want, and put the command in the command window.

Hope this works

---

### Post by HomoGleek on 2009-09-29
Created a custom application launcher on one of my panels, select application run in terminal, and it appears too work.

Thanks

---

### Post by HomoGleek on 2009-10-02
> **Michael.Godawski said:**
> ```
sudo /etc/init.d/networking restart
```This is what I use. But you need to remain the terminal window into which you type this open, you close it, nm-applet closes too. ;)

NetworkManager stopped today, tried that command but It didn't work, so I looked around the /etc/init.d/ and worked out that 
```
sudo /etc/init.d/NetworkManager restart
```
I am looking for.

Rather pleased with myself for my first 'fix', even though it is rather small :P

---

