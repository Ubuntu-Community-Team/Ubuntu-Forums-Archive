---
title: "firestarter pwned ubuntu!!"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by Shwick2 on 2008-08-14
So I connected to the internetz with ubuntu 8.04 and I needed protection so I DLed firestarter through add/remove programs.  My internet was working fine after I started firestarter, but then there was this big lock button and I pressed it and firestarter went all Charlie on me and burned my internet :lolflag:.

 Now I have to sudo internetz :confused: or something cause I can't connect anymore.  Using Rogers Internet ethernet modem and interface eth0 set to acquire IP using DHCP.

---

### Post by Shwick2 on 2008-08-14
Someone was telling me 

**edit by oldsoldier: deleted malicious command**

 would delete firestarter and fix my internet?

---

### Post by Ayuthia on 2008-08-14
> **Shwick2 said:**
> Someone was telling me 

** edited by oldsoldier: removed malicious command**

 would delete firestarter and fix my internet?

No!  Do not do that!  That will mess up a lot of things on your computer and will force you to reinstall Ubuntu.

---

### Post by Ayuthia on 2008-08-14
> **Shwick2 said:**
> So I connected to the internetz with ubuntu 8.04 and I needed protection so I DLed firestarter through add/remove programs.  My internet was working fine after I started firestarter, but then there was this big lock button and I pressed it and firestarter went all Charlie on me and burned my internet :lolflag:.

 Now I have to sudo internetz :confused: or something cause I can't connect anymore.  Using Rogers Internet ethernet modem and interface eth0 set to acquire IP using DHCP.

Have you tried pressing the unlock firewall button on it?

---

### Post by Shwick2 on 2008-08-14
I couldn't press unlock because every time I tried to start firestarter I wouldn't be able to see the gui :mad:.  I could see the processes after a "ps -ef | grep firestarter" but the gui I couldn't see.

 I ended up killing the processes, scouring my system for all firestarter files and deleting them, but that didn't even solve the problem :(.  It's like firestarter locked more than it's own files.

---

### Post by Vivaldi Gloria on 2008-08-14
firestarter is a dead project. remove it. ubuntu comes with ufw. See

```
man ufw 
```

for more info. For example, to disable firewall use

```
sudo ufw disable
``` 

and reboot.

---

### Post by Ayuthia on 2008-08-14
> **Vivaldi Gloria said:**
> firestarter is a dead project. remove it. ubuntu comes with ufw. See

```
man ufw 
```

for more info. For example, to disable firewall use

```
sudo ufw disable
``` 

and reboot.
Are you sure that Firestarter is a dead project?  Their website still looks up to date and their mailing list still looks active.  

@Shwick2 - Did you remove everything in /etc/firestarter?  If so, have you tried reinstalling it to see if you can get the application running?  Even if you do use ufw, you might need to clean up the files that Firestarter has modified.

---

### Post by Vivaldi Gloria on 2008-08-14
> **Ayuthia said:**
> Are you sure that Firestarter is a dead project?  Their website still looks up to date and their mailing list still looks active.  

The last update was in 2005. The developers are not working on it anymore. The list is not as active as before. From the list:

> It would appear (sadly) to be a dead project. I have not heard a word from any of the developers in 2 years or more and have heard of FS
having problems with newer libraries for Gnome and other fundamental iptables changes in newer kernels.

I also heard that it crashes.

ufw is better anyway.

---

### Post by Ayuthia on 2008-08-14
> **Vivaldi Gloria said:**
> The last update was in 2005. The developers are not working on it anymore. The list is not as active as before. From the list:



I also heard that it crashes.

ufw is better anyway.

I just downloaded the source and confirm your remarks.  You are also correct that it does crash.

Anyway, I did attempt the same thing as Shwick2 and it did lock everything up.  You cannot get it to come back up until you kill all the processes and restart.  I logged out and disconnected my internet connection, firestarter came back and was promptly shutdown.  Once I logged back in, it unlocked.

I would recommend that you try and reinstall firestarter and see if it will fix the files that you have removed.  Hopefully it will clear everything out.

If you are just using firestarter as a firewall and nothing else, you might want to try out ufw.  It comes built in with Ubuntu.

---

### Post by Shwick2 on 2008-08-15
Don't worry I fixed the problem- reinstalled ubuntu and not installing ****** fire**** ever again!  TY

---

### Post by thefunnyman on 2008-08-15
ya know, when I start firestarter on my machine, it puts an icon in the system tray and launches into that only.  So, when I launch, I don't see the GUI by default, I have to click the icon in the tray to show the gui.  I'll bet that's what happened.

firestarter isn't all that bad.  It does what you need it to for a basic firewall and allows you to see blocked traffic on certain ports/services without opening a terminal.

---

