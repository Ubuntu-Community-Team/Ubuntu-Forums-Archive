---
title: "Network manager"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by baconlt72 on 2009-02-03
Hi:

I posted this question about 2 hours ago on the forum but it doesn't seem to have appeared. Which is a shame because it took me about 20 minutes to type it, and now I have to do it from memory.

Essentially I am having problems getting network manager to appear.

I start it via the terminal and it tells me that NetworkManagerServices or something can't be started, and also states "Return:3". I googled this problem and it appears that it can be solved by un-installing it using synaptic package manager, adding notification area to a panel, then re-installing (both network manager and network manager gnome).

So I try this and when I try to re-install network manager I'm told it's on the database but noit available.

I have ubuntu 8.10, can anyone help?

Thanks.

---

### Post by timcredible on 2009-02-03
why are you starting network manager from command line?  it starts automatically and sits in the top panel.  it's probably giving you an error because it's already running.

---

### Post by adam_kimber on 2009-02-03
Network manager (package name: network-manager) is probably already installed The little icon is actually an applet for Gnome called (wait for it), Network Manager Applet (package name network-manager-gnome). 

If you go to System --> Preferences --> Sessions you can see what is starting on startup. Scroll down and see if Network Manager is there. If not create an entry as follows

Name --> Network Manager
Command --> nm-applet --sm-disable
Comment --> Network Manager applet

You should not have to create it! Something has glitched and we might have fix the underlying problem first.......

---

### Post by baconlt72 on 2009-02-03
i'm pretty sure that Network Manager was not starting on boot-up. If it was I hope I would've noticed, but perhaps not. :-)

I can try adding Network Manager to the services and see what happens, but will it work if I've uninstalled and can't re-install it?

also, can someone please clarify for me what a panel actually is? Is it like a linux analogue of the windows system tray?

I don't have web access at home, so I have to rely on net cafes and the like, so for those who help me (thanks), I might not respond straight away.

---

### Post by adam_kimber on 2009-02-03
[Disclaimer: Apologies if this is a little condescending. I am unsure of the level of your knowledge of the working of Linux/Debian/Ubuntu] 

Ubuntu is based on Debian Linux, that is it is based on a Linux kernel (the core of the Operating System), which has many programs that can be loaded on top of it. These programs generally come in sets as when grouped together they serve a specific purpose. Groupings can be all sorts of reasons, one such grouping is Debian. Ubuntu takes the Debian grouping and customises it. 

Debian and therefore Ubuntu (and other OSes based on Debian) use package management to install these groupings of programs and also other programs. These are called deb files. Each deb file allows a program to be installed such as Openoffice. They are stored on servers throughout the world called Repositories or repos for short. Ubuntu has a few, securtiy, main, backports to name some. 

The reason for the above explanation is to make you aware that Ubuntu and Linux in general is broken down into lots of little programs that all interact to create the end result that you see. In theory you can remove one of these programs and replace it with another. I say in theory as some programs depend on others etc (you will come across dependancy problems if you try installing custom programs not in Ubuntu's repositories).

The panel is one of these programs. Its just the grey bar that sits at the top or bottom of the screen. That is it. Its a program that creates a grey bar. It does more than that though. It allows you to add shortcut icons to it (such as the Ubuntu menu). Window List (shows current open programs) and finally the Notification Area (another peice of software that allows icons to show for programs akin the System Tray in windows). 

The nm-applet (another piece of software that acts as a graphical frontend to network manager) should sit in the Notification Area. 

I hope this helps! 

PS if you open a terminal and type the following, what is the result? Paste here please! 

```
sudo apt-get install network-manager-gnome
```

---

### Post by baconlt72 on 2009-02-03
Hi Adam, no please don't worry, that is very useful.

I will post the print-out I get from that tomorrow.

I understand that there is a book recommendation in a sticky at the top of the page, but if you had your own recommendation then I would be very pleased to hear it.

Many thanks.

Bryan.

---

### Post by adam_kimber on 2009-02-03
> **baconlt72 said:**
> 
I understand that there is a book recommendation in a sticky at the top of the page, 


You mean[ this]("http://www.ubuntupocketguide.com/download.html") one? It looks pretty thorough.

One of the things I like about [Free Software]("http://www.gnu.org/philosophy/free-sw.html") is the reverse psychology that commercial software uses. With commercial, generally you pay for a product, and that's that, no chance of altering it or helping make it better. With free software you can contribute in many ways including financially. "If you like it pay for it" is my philosophy. Donating keeps projects alive. So if you like some other program - donate! :D

---

### Post by baconlt72 on 2009-02-04
Hi Adam:

I tried that command in terminal and got the following:
```

Package netwrok-manager-gnome is not available but is referred by another package.

This may mean that the package is missing, has been obsoleted or is only
available from another source.

E: Package network-manager-gnome has no installation candidate.
```

---

### Post by feb3 on 2009-02-04
I have exactly the same problem, hence joining this thread. I installed Ubuntu 8 with wubi yesterday on my Vista laptop. All is OK except that I have no Network Manager icon. Have tried both the solutions above - here is the result of the terminal one:

ohn@ubuntu:~$ sudo apt-get install network-manager-gnome 
[sudo] password for john: 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
The following packages will be upgraded: 
  network-manager-gnome 
1 upgraded, 0 newly installed, 0 to remove and 240 not upgraded. 
Need to get 297kB of archives. 
After this operation, 0B of additional disk space will be used. 
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main network-manager-gnome 0.7~~svn20081020t000444-0ubuntu1.8.10.1 [297kB] 
Fetched 297kB in 0s (431kB/s)                 
(Reading database ... 99825 files and directories currently installed.) 
Preparing to replace network-manager-gnome 0.7~~svn20081020t000444-0ubuntu1 (using .../network-manager-gnome_0.7~~svn20081020t000444-0ubuntu1.8.10.1_i386.deb) ... 
Unpacking replacement network-manager-gnome ... 
Setting up network-manager-gnome (0.7~~svn20081020t000444-0ubuntu1.8.10.1) ... 
Installing new version of config file /etc/xdg/autostart/nm-applet.desktop ... 

john@ubuntu:~$ 
john@ubuntu:~$ 

Still no Network Manager although it is connected to the Internet via wired connection and the two tv screens are in the taskbar.
The wireless card is Fujitsu Seimens WLAN 802.11b/g SiS 1634.
Is this a driver issue and if so, could someone please direct me to the place to get them?
Thanking you.
BTW there is only the waste bin in the system tray although I have activated the notification area as far as I can tell.

---

### Post by ncubede on 2009-02-04
You corrected your typo, right?  You should have network-manager and network-manager-gnome installed. the syslog in /var/log/syslog will typically contain more information about why/if the network manager daemon started or not. As root:
```

grep NetworkManager /var/log/daemon.log

```

If you run
```

ps axu | grep NetworkManager  

```
then you should see both the network manager daemon itself and the nm settings daemon running like this:
```

root      6632  0.0  0.0  62872  2912 ?        Ssl  Feb03   0:12 /usr/sbin/NetworkManager
root      6643  0.0  0.0  66800  3328 ?        S    Feb03   0:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf

```

Next the GUI icon (which will only be visible, if network manager thinks it has something to manage):
```

ps axu | grep -i nm-applet

```
```

stephan   7317  0.0  0.5 180292 18016 ?        S    Feb03   0:01 nm-applet --sm-disable

```

> **baconlt72 said:**
> Hi Adam:

I tried that command in terminal and got the following:
```

Package netwrok-manager-gnome is not available but is referred by another package.

This may mean that the package is missing, has been obsoleted or is only
available from another source.

E: Package network-manager-gnome has no installation candidate.
```

---

### Post by adam_kimber on 2009-02-04
> **baconlt72 said:**
> Hi Adam:

I tried that command in terminal and got the following:
```

Package netwrok-manager-gnome is not available but is referred by another package.

This may mean that the package is missing, has been obsoleted or is only
available from another source.

E: Package network-manager-gnome has no installation candidate.
```

As said above try typing network-manager-gnome rather than netwrok-manager-gnome :D

---

### Post by baconlt72 on 2009-02-05
Hi Guys:

What that was, was an error in writing down from my notes what had happened. I had actually typed "network" rather than "netwrok", but I just typed it incorrectly at the internet cafe (no web access at home).

I double-checked when I got home and that is the error I get (barring the incorrect spelling).

Thanks.

---

### Post by adam_kimber on 2009-02-05
> **baconlt72 said:**
> Hi Guys:

What that was, was an error in writing down from my notes what had happened. I had actually typed "network" rather than "netwrok", but I just typed it incorrectly at the internet cafe (no web access at home).

I double-checked when I got home and that is the error I get (barring the incorrect spelling).

Thanks.

Lets see if we can get you network manager running with the following. It appears that the package manager cannot find these files for some reason. You can use either method below. 

1) Download the network-manager and network-manager-gnome debs from [here]("http://packages.ubuntu.com/intrepid/network-manager") and [here]("http://packages.ubuntu.com/intrepid/network-manager-gnome"). Scroll to the bottom and click on the architecture of your system (e.g. is it 32bit or 64bit). Double click the debs that download and install.

2) Add the original CD as a repo and then install the packages from there. Insert CD and type ```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install network-manager network-manager-gnome
```

Hope this helps. 

PS To find out if you are running 64bit Ubuntu type ```
uname -a
```
and you will get something like this

```
Linux zia 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux
```

Note the x64_64 part. That denotes that I am running 64bit.

---

### Post by baconlt72 on 2009-02-06
OK, cheers pal, will get back to you once I've given it a go.

Ta.

---

### Post by baconlt72 on 2009-02-06
OK, getting a bit frustrated with this now.

I got the nm applet installed, I get two little monitors in the panel, and it asks me about VPN connections when I left-click. Or when I right'click, I can edit connections and I get a multi-tabbed dialog box where I can add connections, but it doesn't list anz networks, despite me sitting in a wireless hotspot with a wireless usb stick that I intslled using ndisgtk.

On top of this, it has somehow stopped me from connecting to the internet with wifi in windows, I had to do a system restore.

I'm starting to wonder whether this is worth all of teh trouble.

---

### Post by adam_kimber on 2009-02-06
Don't give up. I am not sure why you are using ndiswrapper or its front end........ This could be causing all sorts of conflicts. Can you plug the USB device in and then type the following ```
lsusb
``` in a terminal and paste it here.

That will produce a list of usb items :D. Here is mine so that you get an idea of whether its displaying the correct info.
```

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04b8:0005 Seiko Epson Corp. Stylus D88+
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 03f0:0604 Hewlett-Packard DeskJet 840c
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 008: ID 045e:0719 Microsoft Corp. 
Bus 004 Device 007: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Its currently listing my mouse, some ports and my printers.

---

### Post by baconlt72 on 2009-02-06
Hi Adam:

I'll have to give up for now, got too much on.

Thanks for all your help, and I hope you're still OK to help me in about a month's time?

Looking for a job at the moment has to take precedence.

Thanks.

Bryan.

EDIT: It will also be much quicker to resolve when I am back in the UK and will have web access from home.

---

### Post by adam_kimber on 2009-02-06
NP. Just reply to this thread and hopefully sort the problem!

---

### Post by baconlt72 on 2009-09-30
Just a quick update many months on ,.. I am writing this in Mozilla on Linux platform from home, and I'm wirelessly connected to my router.

whooooooooooooooooo-hooooooooooooooooooooooooooo!

---

