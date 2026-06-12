---
title: "lost network manager, can't get on line"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by earl100 on 2011-04-28
I accidently deleted network manager, and now can't log on to wireless via google or firefox.

If you can propose a fix, can you also tell me why my netbook version 10.10 won't put anything on the desktop?

earl

via e-mail I'm [email]earldotcom@hotmail.com[/email]

---

### Post by pi3.1415926535... on 2011-04-28
If you have a LiveCD, you can reinstall the network manager through that. This can be enabled through Edit>Software Sources in Ubuntu Software Center, then clicking the box relating to the CD. Then you should be able to use a CD to install software.

---

### Post by earl100 on 2011-04-28
Don't have a live cd.  Installed via usb stick.

Have tried to re-install network manager with usb stick in place using software installer but it wants to go online.

Earl

---

### Post by spidertattoos on 2011-04-28
[SIZE=3]Go to terminal or alt+f2
and depending on your interface name ie: eth1 
and your security type(WEP/WPA) {preferably no WEP/WPA}
Enter the following

sudo ifconfig eth1 down
sudo iwconfig eth1 mode managed essid "[COLOR=Red]network name here[/COLOR]"
sudo ifconfig eth1 up
sudo dhclient eth1[/SIZE]

[SIZE=3]that should solve it [/SIZE]

---

### Post by grahammechanical on 2011-04-28
What do you mean 

> deleted network manager

Did you remove the icon or uninstall through Synaptic or the Software Centre?

In standard 10.10 you right click the panel and select add to panel and then select Notification Area. You can also make sure that Network Manager is one of your Startup Applications.

Regards.

---

### Post by earl100 on 2011-04-28
thanks for the quick replies.

I use public wifi.  I don't know what my interface name is.

Using the terminal is a new experience for me.

can I just copy your script word for word and hit "enter"?
Earl

---

### Post by earl100 on 2011-04-28
Graham,

Thanks for the reply.it  I accidently hit "remove" in the software manager.

I don't know what a 'panel' is.

If it's that bar at the top where the icon for networks used to be then right clicking on it doesn't do anything.

Earl

earl

---

### Post by KL_72_TR on 2011-04-28
Go to Applications > Ubuntu Software Center and type Network Manager. In the list see if Net. Man. is installed.
If so than you just have removed from the panel.

---

### Post by earl100 on 2011-04-28
I've gone to the manager, and Net. Mgr. is not installed.

I can't get back on line to re-install it.

I've reinstalled Ubuntu in a second partition which allows me to respond to your msg., for which I'm grateful, but would rather have the Ubuntu OS in the other partition running.  

any re-installation I try to do through the program manager fails because I can't get on-line.

Earl

---

### Post by earl100 on 2011-04-28
Is it possible that Net. Mgr. as you call it was acting as a driver for my wi fi card?

I have a  Toshiba Netbook...NB 205.  Don't know what brand wifi card it has.  Don't know how to fix drivers either.

Earl

---

### Post by KL_72_TR on 2011-04-28
I think this will give you a little help: [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

---

### Post by earl100 on 2011-04-28
Thank  you KL.  I'll check it out.

earl

---

### Post by KL_72_TR on 2011-04-28
> **earl100 said:**
> Is it possible that Net. Mgr. as you call it was acting as a driver for my wi fi card?
No. It is not a driver for the card.

---

### Post by earl100 on 2011-04-28
Went to the page KL recommended...it's way over my head.

Seems to require various scripts in the underlying programming language.  I'm using a Gui.  I mainly drag and drop.  The underlying programming, like ms-dos, is what I expect an operating system to do.

Since this operating system was touted as an alternative to the windows desktop I can't even get it to do the icons on the  desktop part.

The idea of hand copying lengthy lines of commands, and then accurately entering them without screwing something else up defeats me. I want an application, like an operating system, to do that for me.

I prefer to return to using windows, and I very much dislike windows.

Thanks for the attention,

Earl

---

### Post by KL_72_TR on 2011-04-28
> **earl100 said:**
> I've gone to the manager, and Net. Mgr. is not installed.

I can't get back on line to re-install it.
If I'm getting this right you are saying that when you go Applications > Ubuntu Software Center you see Network Manager is not installed. 
Click on the install button and you'll be asked to provide your password (do so), and the Software Center will take care of the installation process.

---

### Post by frank604 on 2011-04-28
First go run Synaptic package Manager. 
Then click on Settings, then click on Repositories, then click on the CD source near the bottom of the window that pops up.
This enables it to search your live cd, if you don't have it, then boot into your 2nd partition of ubuntu, download it and burn one.  
Now you can search "network, and choose network manager gnome for installation for your broken ubuntu.

---

### Post by earl100 on 2011-04-30
> **KL_72_TR said:**
> If I'm getting this right you are saying that when you go Applications > Ubuntu Software Center you see Network Manager is not installed. 
Click on the install button and you'll be asked to provide your password (do so), and the Software Center will take care of the installation process.



KL,
When I do this the Software Center wants to go on line to download Network Manager, and down loading is my obstacle.

---

### Post by KL_72_TR on 2011-05-01
Take a look at: System > Preferences > Network connections.
It will pop-up the same window as Network Manager. See if you can activate the connection there.
If that is not possible to, try and make a fresh installation, it will take only 20 min. Less trouble and will resolve the problem.
> **earl100 said:**
> Seems to require various scripts in the underlying programming language.  I'm using a Gui.  I mainly drag and drop.  The underlying programming, like ms-dos, is what I expect an operating system to do.

Since this operating system was touted as an alternative to the windows desktop I can't even get it to do the icons on the  desktop part.

The idea of hand copying lengthy lines of commands, and then accurately entering them without screwing something else up defeats me. I want an application, like an operating system, to do that for me.
Go to: [http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download](http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download) and download the PDF. After reading that you will smile.

---

