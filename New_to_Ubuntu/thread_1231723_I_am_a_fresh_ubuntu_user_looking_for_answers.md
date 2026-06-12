---
title: "I am a fresh ubuntu user looking for answers"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by theprince862 on 2009-08-04
Hi I am new using ubuntu and i have alot of questions so if any one can help please respond 

1- What is jaunty and what is gnome?
2- How can i be a root user?
3- What does i686 mean?
4- How do i safely remove a USB device?
5- what kind of download manager can i use instead of the Firefox default? 
6- I have got avg 8.5 Linux version when i install it finishes installation and appear on the  computer janitor but there is no GUI or tray icon or any thing to open or manage it from?
7- How do i disable my Internet connection?
8- What are the packages and how can i manage them?

---

### Post by aysiu on 2009-08-04
> **theprince862 said:**
> 
1- What is jaunty and what is gnome? Jaunty is a nickname for the latest Ubuntu release, which is 9.04.

Gnome is the user interface (also called *desktop environment* that comes with Ubuntu by default. > 2- How can i be a root user? ```
sudo -i
``` or ```
gksudo nautilus
``` More details at [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions) > 3- What does i686 mean? It refers to the architecture of your computer or the kernel you use on your computer. If you don't have a special processor (64-bit, lpia, or PowerPC), you should probably use an i686 or i386 kernel.
> 4- How do i safely remove a USB device? Right-click it and select *unmount*. > 5- what kind of download manager can i use instead of the Firefox default? Downthemall? > 6- I have got avg 8.5 Linux version when i install it finishes installation and appear on the  computer janitor but there is no GUI or tray icon or any thing to open or manage it from? Why do you have AVG? Are you running a mail server? > 7- How do i disable my Internet connection? Right-click on the network manager icon (near the clock) and uncheck *Enable Networking* > 8- What are the packages and how can i manage them? Read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by aesis05401 on 2009-08-04
aysiu, your PMs are full.

For clarification, is the first answer under section 2 something that falls under advice on logging in as root?

---

### Post by kpkeerthi on 2009-08-04
These would be a good (& must) read for beginners:

[https://help.ubuntu.com/9.04/index.html]("https://help.ubuntu.com/9.04/index.html")

[http://www.ubuntupocketguide.com/]("http://www.ubuntupocketguide.com/")

---

### Post by aysiu on 2009-08-04
> **aesis05401 said:**
> aysiu, your PMs are full.

For clarification, is the first answer under section 2 something that falls under advice on logging in as root?
No.

```
sudo -i
``` gives you a persistent root prompt in the terminal, but you aren't completely logged in as root. You have a persistent root prompt in that particular terminal window or tab and that's it. Once you type ```
exit
``` it's gone. Be sure **never** to use *sudo -s*. It can really screw up ownership of files and folders.

```
gksudo nautilus
``` does not make your entire session a root session. It just makes one file browser window have root privileges within an otherwise restricted session.

---

### Post by theprince862 on 2009-08-04
Thanks alot aysiu for your fast response but but i am still using microsoft windows with the ubuntu so some people adviced me to secure linux from viruses so as not to damage my windows and  i have got another question (why does some applications doesn't appear on the janitor such as wine and how can i uninstall them and some other applications doesn't appear in the applications menu at all?)

---

### Post by egalvan on 2009-08-04
> **aysiu said:**
>   Why do you have AVG? Are you running a mail server?  


Come on, aysiu, running a mail server isn't the only way to have Windows "stuff" pass through your machine :)

flash drives
USB hard drives

are two more examples of possible Windows "stuff" being attached to
your machine,,,
yeah, you're immune, but do you want to "pass it on"?
Isn't it better to stop them from getting any further?

I believe in being a "good neighbor"...
I run an automatic virus scan on *anything* that attaches to my Linux machines...
and I've de-loused many a flash drive.
Much to the chagrin of some users,
but they are usually thankfull.

I tell them it's all Linux.

---

### Post by aysiu on 2009-08-04
> **theprince862 said:**
> Thanks alot aysiu for your fast response but but i am still using microsoft windows with the ubuntu so some people adviced me to secure linux from viruses so as not to damage my windows Those people are misinformed. If you care about security, read [the security sticky](http://ubuntuforums.org/showthread.php?t=510812).

You should also read these two little write-ups I did... one for Ubuntu, one for Windows.
[The 6 Best Ways to Secure Windows](http://www.psychocats.net/ubuntucat/windowssecurity/)
[Does Ubuntu need antivirus?](http://www.psychocats.net/ubuntucat/does-ubuntu-need-antivirus/)

> and  i have got another question (why does some applications doesn't appear on the janitor such as wine and how can i uninstall them and some other applications doesn't appear in the applications menu at all?) Go to System > Administration > Synaptic Package Manager.

Applications > Add/Remove has a lot of popular graphical applications in it. Synaptic Package Manager has every package listed (popular or not, graphical or not).

---

### Post by theprince862 on 2009-08-04
Thanks alot aysiu

---

### Post by 3rdalbum on 2009-08-04
AVG for Linux is not a GUI program, it's a command-line program. They intend it for use with mail servers. Try looking for some documentation on the AVG website, for details on how to use it.

Ordinary desktop Linux users don't need anti-virus.

If a program is a command-line program, it doesn't appear on the menus. A couple of GUI programs don't appear on the menus either, but these are rare, and you can follow the link in my signature for how to find them and add them manually.

You can remove any program or package using Synaptic Package Manager, as long as you installed it via Add/Remove Applications, Synaptic or through a .deb package. If you didn't install it through any of those means, consult the program's documentation.

---

