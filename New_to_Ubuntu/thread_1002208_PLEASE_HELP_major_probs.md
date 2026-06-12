---
title: "PLEASE HELP major probs"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by cjc9280 on 2008-12-04
Hi I have an acer aspire one with linux. Everything was working perfectly yesterday but today when I booted my acer up I got a blank black screen with a box in top right corner. More alarmingly I got the message "Could not run command: xfdesktop2 --gohome:
Failed to execute child process "xfdesktop2" (No such file or directory)"

Any ideas??? I rely heavily on my acer so am somewhat scuppered - it won't even let me open a terminal box

---

### Post by Tatty on 2008-12-04
Sorry if this sounds odd, but are you running Ubuntu on your laptop?  You just said linux so I just want to make sure we are on the same wavelength.

Did you recently make any changes or do anything to your system which may have caused this?  Were there any hard shutdowns or anything?

Try pressing ctrl-alt-F1 to see if you can get a tty console.

---

### Post by cjc9280 on 2008-12-04
I have linux. Haven't had any probs at all until I turned it on just now. Can;t get a terminal or anything, basically the desktop has disappeared

---

### Post by utsuprainfra on 2008-12-04
something happened to the directory.  try contrl-alt-f1 and let me know if you get a terminal prompt.  if you can, try to see if that directory is located anywhere else on your filesystem.  maybe we can re-install the windowmanager.  try control-alt-f1 and let me know if you get a terminal.

---

### Post by cjc9280 on 2008-12-04
I can't get a terminal. Am I going to lose all my data?? I sm extremely new to linux so will need the simplest guide

---

### Post by linux_tech on 2008-12-04
boot
press ctrl-alt-f1 to get console
from cmd prompt try 

```
sudo / etc/init.d/gdm start
```
```
sudo startx
```

---

### Post by cjc9280 on 2008-12-04
when i press ctl alt f1 it doesnt give me anything

---

### Post by Tatty on 2008-12-04
It seems your laptop comes with "Linpus Linux Lite" as the OS, which I am not too familiar with but we can perservere.  It is based on Fedora, so it may be worth asking on their forums if we cant find a solution here.

First dont panic, im sure you have not lost your data at all.  It may be worth booting into a ubuntu live CD and backing up all your important data to a usb stick first, so you know its all safe.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)  Download a Ubuntu live CD here.

---

### Post by halitech on 2008-12-04
> **cjc9280 said:**
> Hi I have an acer aspire one with linux. Everything was working perfectly yesterday but today when I booted my acer up I got a blank black screen with a box in top right corner. More alarmingly I got the message "Could not run command: xfdesktop2 --gohome:
Failed to execute child process "xfdesktop2" (No such file or directory)"

Any ideas??? I rely heavily on my acer so am somewhat scuppered - it won't even let me open a terminal box

> **cjc9280 said:**
> I have linux. Haven't had any probs at all until I turned it on just now. Can;t get a terminal or anything, basically the desktop has disappeared

Ubuntu is linux but linux is not ubuntu. linux refers to the entire family (Fedora, Debian, Gentoo, etc) and assistance for one distro may not help on another. Did you install Ubuntu on it or is it still running the default install of Linpus?

---

### Post by cjc9280 on 2008-12-04
ok, that is not the major prob I have a massive meeting at 9am and have to have the acer there! I just dont get why or how this has happened.

I am still running the linux the acer came with

---

### Post by cjc9280 on 2008-12-04
I am guessing I am doomed on this one.

---

### Post by halitech on 2008-12-04
not necessarily but you would be better off asking in a forum that knows more about the acer one and the software that it comes with then here as the software is different. also if its still under warrenty, call acer and ask for help.

---

### Post by Tatty on 2008-12-04
The version of linux you have on your computer is Linpus Linux Lite.  You will probably want to contact your laptop manufacturer about this to guarentee it being fixed properly.

There are many ways we could get your system working again, however it may not be the same as before, as I dont think many people here will have specific knowledge of Linpus Linux Lite.

I have tried googling the error message you report, but there doesnt seem to be many references to it (and none i can find in english, lol).

Did you recieve any recovery CDs with your computer?  Due to your urgent need for a working computer and your data from it, I think the easiest thing to do for now is to boot into a LIVECD, rescue your data, then re-install linpus

---

