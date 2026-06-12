---
title: "NetworkManager, nm-applet on ubuntu 7.10"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by eneth80 on 2008-11-20
Hi, I have an esprimo mobile v5535.
My problem is that the nm-applet and/or NetworkManager are unstable at boot, ie it is not always possible to do 
```
nm-applet --sm-disable &
```
and see the nm-applet. Here some more details. I hope somebody can help me!
Regards
Alessandro


 I managed somehow to install the drivers and the wireless was working. The only problem was that the nm-applet was not starting at boot. I had to do sudo NetworkManager to connect. 
Then I tried the method in this thread [HTML]http://ubuntuforums.org/showthread.php?t=956187 [/HTML]
adding
[HTML]http://ppa.launchpad.net/network-manager/ubuntu intrepid main[/HTML]
[HTML]http://ppa.launchpad.net/network-manager/ubuntu intrepid main[/HTML]
to my Software Source , and now it is even worse. Often at startup the nm-applet does not show, I try in vain 
```
sudo NetworkManager
```
```
nm-applet --sm-disable &
```
or I kill the processes,
```
sudo killall nm-applet
```
```
sudo killall NetworkManager
```
and to connect I have to toggle```
 nm-applet --sm-disable
``` on and off in System>Preferences>Sessions, and reboot 3/4 times before the nm-applet appears and connects. 
Sometimes I get: 
```
aless@aless-laptop:~$ sudo  nm-applet --sm-disable &
[2] 5938
[1]   Done                    sudo nm-applet --sm-disable
aless@aless-laptop:~$ 
** (nm-applet:5938): WARNING **: No connections defined  
```
Sometimes:

```
aless@aless-laptop:~$ sudo  nm-applet --sm-disable &
[2] 5873
aless@aless-laptop:~$ 
** (nm-applet:5873): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3

(nm-applet:5873): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

[2]+  Exit 1                  sudo nm-applet --sm-disable

```

My /etc/network/interfaces is
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

---

### Post by 80aless on 2008-11-25
At least could anybody tell me WHY MY POSTS ARE NOT APPEALING? HOW TO GET AN ANSWER??? 
in fact it is not the first time my posts get ignored
thanks

---

### Post by JayD3e2010 on 2011-05-22
This is a really old thread, but I just had a recent problem on Arch Linux that had all of these symptoms, and the solution was simply adding my user to the network group.  Hopefully someone finds this helpful.
> gpasswd -a username network

---

