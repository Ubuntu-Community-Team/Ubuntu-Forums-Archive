---
title: "New user no idea"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by PHANTOM X on 2010-07-13
Hello everyone!

I'm new here and to Ubuntu,


I've installed Ubuntu side by side with Windows Vista and need to setup an internet connection. I did check [here]("http://ubuntuforums.org/showthread.php?t=801404"), but had a hard time understanding the commands. Is there a beginners guide to understanding the terminal, scripts, gnome, ndiswrapper and the kernel?

Thanks!

Edit: I did remove Ubuntu temporarily and installed in Virtualbox.

---

### Post by gr4nf on 2010-07-13
Hello, and welcome. :)

Could you post the contents of the file:
```

/etc/network/interfaces

```
which you can access by opening "filesystem" and then the folders in order...?

---

### Post by mbzn on 2010-07-13
Hi and Welcome

Firstly I would like to know more about your internet connection, how do you connect?

EDIT: The Ubuntu pocket guide is great.

---

### Post by PHANTOM X on 2010-07-13
> **gr4nf said:**
> Hello, and welcome. :)

Could you post the contents of the file:
```

/etc/network/interfaces

```which you can access by opening "filesystem" and then the folders in order...?

That's going to take some time. I'll be back in a bit or hopefully not too long.

@ mbzn-

I have dell wireless card(laptop).

I just downloaded that.:p

---

### Post by mbzn on 2010-07-13
When you click on the network icon at the top panel(close to the time), does it give you 'available wireless networks'?

If you are running in a virtual machine with a windows host this won't work.

---

### Post by PHANTOM X on 2010-07-13
> **mbzn said:**
> When you click on the network icon at the top panel(close to the time), does it give you 'available wireless networks'?

If you are running in a virtual machine with a windows host this won't work.

I'm back, but bare with me my second computer is down. On my Nintendo Wii. For the connection it says no connection and wireless disabled. It works fine under a vm, but mostly I want to get it side by side with windows. Forgot to list my card its a Dell Wireless 1395 Mini card. I think its related to Broadcom from looking at the beginner guides.

@grn4f-

I found the file it says

auto lo
iface lo inet loopback

---

### Post by Darkness Des on 2010-07-13
I have that same wireless card in my laptop. If you can get an ethernet connection, the just connect like that and click on Applications (at the top) -> Accessories -> Terminal. In there, type in
```
sudo apt-get install bcmwl-kernel-source
```
to get the driver. If you don't have a connection of any kind, put the installation CD in the drive and go to System -> Administration -> Software Sources. Enable the CD, then close the window (press reload if required in the dialogue box) then run the same command listed above. Reboot after it installs, and you can then setup your wireless connection.

---

### Post by PHANTOM X on 2010-07-13
> **Darkness Des said:**
> I have that same wireless card in my laptop. If you can get an ethernet connection, the just connect like that and click on Applications (at the top) -> Accessories -> Terminal. In there, type in
```
sudo apt-get install bcmwl-kernel-source
```to get the driver. If you don't have a connection of any kind, put the installation CD in the drive and go to System -> Administration -> Software Sources. Enable the CD, then close the window (press reload if required in the dialogue box) then run the same command listed above. Reboot after it installs, and you can then setup your wireless connection.


Thanks I'll try burning it.:)

---

### Post by PHANTOM X on 2010-07-13
> **Darkness Des said:**
> I have that same wireless card in my laptop. If you can get an ethernet connection, the just connect like that and click on Applications (at the top) -> Accessories -> Terminal. In there, type in
```
sudo apt-get install bcmwl-kernel-source
```to get the driver. If you don't have a connection of any kind, put the installation CD in the drive and go to System -> Administration -> Software Sources. Enable the CD, then close the window (press reload if required in the dialogue box) then run the same command listed above. Reboot after it installs, and you can then setup your wireless connection.

The instructions don't work. Also my computer won't read burnt discs or anything. Any other way I can do this?

---

### Post by themusicalduck on 2010-07-13
Have you tried going to System > Administration > Hardware Drivers, to see if you can install a driver from there?

You'll need to connect to the internet through ethernet to download them though.

Note: this will only work in an install. It won't work if it's running in Virtuabox, because Virtualbox doesn't use your actual hardware, but emulates it instead.

---

### Post by libssd on 2010-07-13
You didn't say what version of Ubuntu. Since your wireless question appears to have been answered, I'm just going to mention a couple of free printed guides that are available:

*Ubuntu Pocket Guide and Reference*, by Keir Thomas. Don't worry about the fact that this book was written for Ubuntu 8; much remains basically the same in later editions.
[http://www.ubuntupocketguide.com](http://www.ubuntupocketguide.com)

Also good (less technical, but applicable to specifically to 10.04) is *Getting Started with Ubuntu 10.04*. 
[http://ubuntu-manual.org](http://ubuntu-manual.org)

Don't waste your money buying big, fat, expensive books, except possibly for *Linux Phrasebook*, by Scott Granneman. It's (relatively) inexpensive, concise, accessible, and well-structured. You can get get essentially the same information from man pages (e.g., at command line type man [command], where [command] is the command you want information about. Example:

```
man ls


LS(1)                            User Commands                           LS(1)

NAME
       ls - list directory contents

SYNOPSIS
       ls [OPTION]... [FILE]...

DESCRIPTION
       List  information  about  the FILEs (the current directory by default).
       Sort entries alphabetically if none of -cftuvSUX nor --sort.
```
The problem with man pages is that you have to know in advance what command it is you are looking for, a problem that the Grenneman book solves.

---

### Post by PHANTOM X on 2010-07-13
> **themusicalduck said:**
> Have you tried going to System > Administration > Hardware Drivers, to see if you can install a driver from there?

You'll need to connect to the internet through ethernet to download them though.

Note: this will only work in an install. It won't work if it's running in Virtuabox, because Virtualbox doesn't use your actual hardware, but emulates it instead.

We have a router which connects directly to our modem. Plus we live in an older house so I don't think ethernet is a possibility. I'm downloading the netbook edition. Hopefully I can do that.:)

---

### Post by PHANTOM X on 2010-07-13
> **libssd said:**
> You didn't say what version of Ubuntu. Since your wireless question appears to have been answered, I'm just going to mention a couple of free printed guides that are available:


*Ubuntu Pocket Guide and Reference*, by Keir Thomas. Don't worry about the fact that this book was written for Ubuntu 8; much remains basically the same in later editions.

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

Also good (less technical, but applicable to specifically to 10.04) is *Getting Started with Ubuntu 10.04*. 

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)[/QUOTE]

Sorry.:D I'm running the latest(10.04)

---

### Post by PHANTOM X on 2010-07-13
I was looking at the pocket guide which recommends preparations first. Such as defragmenting. I'm going to do that first and install the netbook edition(for usb). May have to install it tomorrow. I'll update then on how it went.:)

---

### Post by PHANTOM X on 2010-07-14
Unfortunately, it still doesn't work. Installed with ndiswrapper and says successful, but doesn't work.:(

---

### Post by 3rdalbum on 2010-07-14
> **PHANTOM X said:**
> Unfortunately, it still doesn't work. Installed with ndiswrapper and says successful, but doesn't work.:(

Remove ndiswrapper entirely - you should use a native driver wherever possible, and ndiswrapper doesn't work with all Windows wireless drivers.

Connect your computer straight to your router via an Ethernet cable; that is, put your computer into the same room as the router. If you don't have a spare Ethernet cable, then just use the cable that connects the modem and the router, have it hooked up to your computer and to the **modem**.

Go to System > Administration > Software Sources and make sure that the first four checkboxes are ticked, so Ubuntu knows where to get software from.

Close the window. go to System > Administration > Synaptic Package Manager. Hit the Reload button to reload the list of packages that are available. After that's done, close Synaptic and go to System > Administration > Hardware Drivers and you should be offered a driver to install.

---

### Post by masque7 on 2010-07-14
To find out more about Ubuntu, commands, and scripting here is a great starting point in the form of a freely available book in PDF format.

[Ubuntu Pocket Guide]("http://www.ubuntupocketguide.com/download/ubuntupocketguide-v1-1.zip")

---

### Post by PHANTOM X on 2010-07-14
> **3rdalbum said:**
> Remove ndiswrapper entirely - you should use a native driver wherever possible, and ndiswrapper doesn't work with all Windows wireless drivers.

Connect your computer straight to your router via an Ethernet cable; that is, put your computer into the same room as the router. If you don't have a spare Ethernet cable, then just use the cable that connects the modem and the router, have it hooked up to your computer and to the **modem**.

Go to System > Administration > Software Sources and make sure that the first four checkboxes are ticked, so Ubuntu knows where to get software from.

Close the window. go to System > Administration > Synaptic Package Manager. Hit the Reload button to reload the list of packages that are available. After that's done, close Synaptic and go to System > Administration > Hardware Drivers and you should be offered a driver to install.

Thanks for the tip. It's working great! Ubuntu is fantastic. Starts fast unlike vista and runs very smooth. This  would be my OS if I didn't program in VB.net . Bummer. Really like it.:)

---

### Post by PHANTOM X on 2010-07-15
Having some issues getting the drivers to install. Keep getting 

```
SystemError Failed to lock /var/cache/apt/archives/lock

```

Edit: Updates seems to have fixed this. Everything solved.:)

---

