---
title: "Is Ubuntu server for me?"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by webcabbie on 2011-04-27
So Im one of the Ubuntu users who likes the GUI and rarely if ever runs anything in the terminal. 

I find myself in need of a half decent VPS server that can run windows programs with not much fuss. 

I have a provider I trust. Who offers this package:

Guaranteed RAM
256 MB
Burstable RAM
512 MB
Disk Space
20 GB
Bandwidth
Unlimited
Price
$10.50

The thing is it comes blank. He will install and support as best he can anything I like. So I was thinking since I have had such good luck with this provider and Ubuntu and especially you guys here at the Ubuntu forum i'll ask him to install ubuntu server on it for me run VM windows and use it. Whata you think?

I know the Ram and Diskspace in this package isn't heroic but the programs I use don't use much. Willing to consider any alternatives you can suggest.

---

### Post by earthpigg on 2011-04-27
> **webcabbie said:**
> i'll ask him to install ubuntu server on it for me run VM windows and use it. Whata you think?


i do not understand what that means. you want to run windows in a vm on a vps?

---

### Post by pi3.1415926535... on 2011-04-27
It would seem like that would work, assuming that the amount of RAM is sufficient. One assumes that that is the RAM that will be used by Ubuntu, and the VM running Windows. It would seem that the amount of RAM could be the major problem.

---

### Post by nebileix on 2011-04-27
Not a good idea as it'll lag like hell with that amount of ram.

---

### Post by webcabbie on 2011-04-27
> **earthpigg said:**
> i do not understand what that means. you want to run windows in a vm on a vps?


Yes that is what I wanted to do. What amount of ram would you suggest be the minimum to run VM windows on a VPS using Ubuntu server?

---

### Post by Darkness Des on 2011-04-27
I would go ahead and get the "Burstable" RAM package there, and that should be sufficient to run Ubuntu Server. However, the server distribution comes without a GUI. If this guy is supporting it entirely, then that shouldn't be much of an issue for you. If you need to do work on it yourself though, that can be tough.

---

### Post by bodhi.zazen on 2011-04-27
Depends on what you are wanting of a server.

On Linux, graphical interfaces, such as gnome, are of limited benefit as most of what you do is edit configuration files and start / stop services, all of which can be done from the command line.

See also: [https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

If you are unwilling to read that guide and use the command line, then, no a Linux server is not for you.

If you want a graphical interface, use a web based option such as webmin or phpmyadmin.

In terms of ram / bandwidth / etc it depends on what you are expecting to do with the server and what the load will be. Those are sufficient stats for a web server running mysql and php with light to moderate traffic.

If you want Windows support, please use a windows forums.

---

### Post by webcabbie on 2011-04-27
> **Darkness Des said:**
> I would go ahead and get the "Burstable" RAM package there, and that should be sufficient to run Ubuntu Server. However, the server distribution comes without a GUI. If this guy is supporting it entirely, then that shouldn't be much of an issue for you. If you need to do work on it yourself though, that can be tough.


Would there be better server software to run windows VM with? The software I need to run on the VM does not like Wine.. countless people have tired and no one can get it to run like that however some people have luck with VM

---

### Post by Paqman on 2011-04-27
If you want to run Windows apps, run Windows. 

With 256-512MB RAM there's no way you're going to be able to run Linux, a VM package, Windows and your Windows apps.

---

### Post by bodhi.zazen on 2011-04-27
> **Paqman said:**
> If you want to run Windows apps, run Windows.

This ^^

Linux is not a drop in replacement for Windows and several times you have mentioned your intention is to run Windows apps.

To be honest, it sounds as if you are very new to servers in general and you really have not given us any clue as to what exactly you are running other then "windows apps".

---

### Post by slooksterpsv on 2011-04-27
Let's see if we can break this down:

Are you wanting to run a VM Installation of Windows from a Dedicated Linux Server?
If so does the Linux Server have 512MB RAM and 20GB HDD? If so, that will not work, unless you run Windows 2000 with 64MB of RAM and like 5GB HDD, which would be the bare minimum you could run a Windows Environment from.

OR

Are you wanting to run a VM Installation of Linux from a Dedicated Windows Server (2003, 2003R2, 2008, 2008 R2)?
If so does the Linux VM have the 512MB RAM and 20GB HDD Specs? If so, that would work for light to moderate webpage serving. But won't run Windows Apps, but can run Web Apps.


The way I understand it is it's a Linux Server with a 20GB HDD and 512MB RAM wanting to Virtualize (have a VM of) Windows on it, which will not run well at all, if run at all.

---

