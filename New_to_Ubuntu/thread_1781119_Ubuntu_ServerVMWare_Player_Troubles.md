---
title: "Ubuntu Server/VMWare Player Troubles"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by Zach D on 2011-06-13
Hi all,

Some background:
I'm a Computer Science major who just completed my first year of college. The second class I took was called Information Security. The last section of the course was on web security. Throughout the course we used VMWare Player (I'm not sure which version, 3.something . . .) and various operating systems (Debian 5, Ubuntu Server, and the Ubuntu desktop OS for a little bit) to break systems and gain information, etc. During the web security portion of the class we used Ubuntu Server and a little website for us to perform SQL Injections, Cross-Site Scripting attacks, Cross-Site Request Forgeries, etc., etc. There's the background.

The issue:
I'm into web development, my very first Computer Science class was a beginning programming class in which we learned JavaScript. I'm very much into web development and would love to be able to use PHP, MySQL and the like. Now, for a while I had been using the machine that I used for homework, and it worked fine. But for months VMWare had been bothering me to download version 3.1.4. One day I decided I had enough time to go for it: big mistake. I tried to download it but it didn't work (can't remember why). So I uninstalled the application then downloaded and older version that I thought we might have used. Ever since I've downloaded an older version of VMWare Player (3.1) and have re-downloaded the Ubuntu Server machine a few different times, but the connection always times out and I have no idea what to do.

I just really want a server where I can practice PHP, MySQL, etc. I don't have a spare computer to make a server out of and this whole virtual machine thing was going great until I messed up cause I'm a n00b. Is there anyone who can help? I'm so thankful for this community!

---

### Post by jake.anq on 2011-06-13
Hi

One option is to install a server directly on to your computer.  The server can then be accessed via [http://localhost/](http://localhost/)
This can be done by installing:
```
sudo apt-get install apache2 php5 mysql-server
```
The webpages can then be placed in the /var/www/ directory

If you still want to continue along the virtual machine route, could you please provide some more information about the operating system.

---

### Post by Zach D on 2011-06-13
> **jake.anq said:**
> Hi

One option is to install a server directly on to your computer.  The server can then be accessed via [http://localhost/](http://localhost/)
This can be done by installing:
```
sudo apt-get install apache2 php5 mysql-server
```
The webpages can then be placed in the /var/www/ directory

If you still want to continue along the virtual machine route, could you please provide some more information about the operating system.

Thank you very much, I'll go ahead and try that command! And I'm not sure if you're talking about the operating system on the virtual machine or on my own computer.

On my own computer I'm running Windows 7, on the virtual machine I am running Ubuntu Server . . . does that help?

---

### Post by VOT Productions on 2011-06-13
Try VirtualBox. It is better than VMware. But you won't get Unity. (You will stuck with GNOME 2)

---

### Post by Zach D on 2011-06-13
> **VOT Productions said:**
> Try VirtualBox. It is better than VMware. But you won't get Unity. (You will stuck with GNOME 2)

Thanks for the suggestion I'll definitely check it out! Will I be able to run Ubuntu Server on it and be able to play around with PHP and MySQL as I did with VMware? Thanks again!

---

### Post by Zach D on 2011-06-13
I installed VirtualBox on my computer, then downloaded the Ubuntu Server iso file. I went through the virtual machine set up and when I finally got to the actual machine, I selected "English", then "Install Ubuntu Server" and got this error message: "This kernel requires an x86-64 CPU, but only detected an i686 CPU. Unable to boot - please use a kernel appropriate for your CPU."

Does anyone have any idea what I can do?

---

### Post by Zach D on 2011-06-13
Ugh! I finally got Ubuntu Server set up on a VirtualBox virtual machine, but I'm having the same trouble I did last time, it can't connect to the server. Can anyone help me? :(

---

### Post by jake.anq on 2011-06-13
> **Zach D said:**
> Thank you very much, I'll go ahead and try that command! And I'm not sure if you're talking about the operating system on the virtual machine or on my own computer.

On my own computer I'm running Windows 7, on the virtual machine I am running Ubuntu Server . . . does that help?
These commands assumed you were running Ubuntu as the host operating system
There are web servers available for Windows though.

---

### Post by Zach D on 2011-06-14
> **jake.anq said:**
> These commands assumed you were running Ubuntu as the host operating system
There are web servers available for Windows though.

Would I be able to install WAMP on my laptop but still be able to use it for school? This is my personal computer and I'm just looking for a way to practice PHP and MySQL and stuff . . .

---

### Post by Zach D on 2011-06-14
Oh my god WAMP worked like a charm . . . I feel so stupid right now!!!!!!!!!!!!!!!!!!!!! Thank you all so much, you've been great helps!!!

---

