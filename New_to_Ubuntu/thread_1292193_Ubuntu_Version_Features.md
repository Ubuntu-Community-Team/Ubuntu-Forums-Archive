---
title: "Ubuntu Version Features"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by jmcgeeALF on 2009-10-15
I'm new to Ubuntu/Linux. I've installed different distributions and have the following question:
 
What determines if a distribution is a server or a desktop?
I arrived at the question when I tried to install a DHCP server on my Ubuntu 9.04 install. I couldn't find a package listed. I'm pretty sure I installed a 32bit Desktop version. Other Linux distributions I have installed did not seem to have this limitation.
 
I plan to try to install/build the server directly from ISC. Will it work?
 
My understanding of Ubuntu is that the basic desktop install is Ubuntu (Gnome Desktop). KUbuntu is a workstation version wth KDE desktop. I assume the Ubuntu Server version would have either come with a DHCP server or had a package registered.
 
Other than performance tuning issues, is any version of Ubuntu limited in the services it can deploy?

---

### Post by zkriesse on 2009-10-15
No, I dont' believe that the initial install of the distribution that you download is limited...that's why it's opensource. You can make it or break it depending on what you do as it's all up to you.

---

### Post by kanikilu on 2009-10-15
My understanding is that the fundamental difference between the server and desktop editions is the [kernel]("http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel"), besides the lack of a GUI by default, of course.

I'm not aware of any restrictions on services - in fact I know there's not, because I have one machine that was setup using the server install, but later added X, and on another machine it was setup using the desktop install, but later added server functions (LAMP).

On my desktop install, I see the dhcp3-server package in Synaptic...

---

### Post by dearingj on 2009-10-15
I believe the package 'dhcp3-server' is the one you're looking for.
It's true that Ubuntu Server comes with more server-related packages installed whereas Ubuntu Desktop comes with things that are more likely to be used at home by end users, but 'behind the scenes' all official Ubuntu editions are essentially the same - they get the same packages from the same repositories. You can easily set up an Ubuntu Desktop computer to run as a server or vice versa.

---

### Post by jmcgeeALF on 2009-10-16
I found my mistake.  I was looking for the application under Add/Remove instead of the Synaptic Package Manager

---

