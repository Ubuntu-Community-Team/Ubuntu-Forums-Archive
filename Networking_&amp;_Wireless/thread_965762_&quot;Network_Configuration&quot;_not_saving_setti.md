---
title: "&quot;Network Configuration&quot; not saving settings"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by vitorgatti on 2008-10-31
Nice, I'm using Ubuntu 8.10 final version and "Network Configuration" is not translated to my language (Portuguese-Brazil)... :(

Anyway, it's not saving my settings. I wanna have Static IP in my eth0 (wired connection).
I go to that "Auto eth0", click EDIT, go to IPV4, type all needed, click OK, restart computer and... there you go, DHCP again.
I really don't understand, also, how I can make a lot of settings and WITHOUT having to type my password.

ALSO, setting wireless connections became very, very boring. Going on manual settings, now you can't just chose one of the WiFi SSID from the list. You have to TYPE the WiFi SSID. That's really awesome... :(

So, how can I fix this issue?
Thanks in advance

---

### Post by 1902 on 2008-11-01
Am having this problem also, when i enable port 1194 in my openvpn settings and press OK, then open it again to find it disabled by itself> 

---

### Post by MockY on 2008-11-01
Fire up the good ol' Terminal

```
sudo gedit /etc/network/interfaces 
```

Replace what's in this file with the following (replacing the ip info with what suits you:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

```

Save and run:

```
sudo /etc/init.d/networking restart
```

---

### Post by drbizzaro on 2008-11-01
I'm having the same problem and when I tried MockYs tip the network ended to work all together (and I did change the static data to my own values). Before that I could make changes through the Ubuntu admin and they were active, but if i restarted the computer it defaulted back to dhcp.

A follow up question also, how do you enter your dns servers into the config file?

---

### Post by yolsgens on 2008-11-01
> **drbizzaro said:**
> A follow up question also, how do you enter your dns servers into the config file?

Edit the file /etc/resolv.conf, then enter yours dns servers like this :
```

nameserver 212.27.40.240
nameserver 212.27.40.241

```

To finish, just enter the following command in order to the config takes effect :
```
sudo /etc/init.d/networking/restart
```

---

### Post by vitorgatti on 2008-11-01
I really don't understand WHY there could be such an idiot bug like that in a SERIOUS distro like Ubuntu.

Ubuntu is not a home-made distro. There are PAID Developers working on that.
So... WTF is that kind of bug?!?!

I can't set static IP using GUI anymore? I have to do it using terminal? This is not a problem for me, but WILL BE for a lot of users that are just starting with Linux.

I know Ubuntu is free and I can't complain too much, but this is unacceptable.

---

### Post by The Cog on 2008-11-01
I agree. The new network manager works very nicely providing you are roaming and using DHCP. But apparently (according to this post) it can't keep static IPs, and it can't get the wireless working unless a user is actually logged in on the GUI. You would think that sheer embarassment would prevent them from letting it out of the door like that. Still, it'll be nice if they ever finish it and get it working properly.

Oh, and the configuration pages don't always fit properly on a netbook screen (1024x600 in my case). You have to set the desktop wall to 2 rows and then switch desktops down to the bottom row, where the bottom part of the configuration page is protruding from above, including the OK button. 

In the meantime, I tried wicd instead, but it seems to have a problem on Intrepid and usually fails to connect - says it's authenticated but can't obtain an IP address. I haven't tried to investigated that one yet.

---

### Post by sephora on 2008-11-01
Hi everyone!

I followed the steps indicated in this post. But my network still doesn't work. When I open Network Connections I have the Ip address, Gateway and DNS Servers with the correct numbers. But in the Netmask box still appear a 24 instead of 255.255.255.0. I don't know what is happening?

The steps I followed are:

1. Edit interfaces: It looks now like this (i didn't write the numbers)

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static

          address ....
          netmask  ...
          network  ...
          broadcast ...
          gateway

2. sudo /etc/init.d/networking.restart

 * Reconfiguring network interfaces...
SIOCDELRT No such process

3. Finally the icon in the right top corner of the screen says: Now you are connected...but....when I open firefox I don't have internet


What am I doing wrong?

---

### Post by amorangi on 2008-11-01
Sephora: In part 2 there's a space not a full stop.

However when I try the above instructions my IP is still that assigned by DHCP. It seems every new version has 2 steps forwad, one step back - you'd have thought something as critical as assigning a static IP would have been tested.

---

### Post by robertbc on 2008-11-05
I'm not sure if I should duplicate my answer (today is the first time I write on a forum), but this is (I hope) the link

[http://ubuntuforums.org/showthread.php?p=6114149](http://ubuntuforums.org/showthread.php?p=6114149)

Hope this helps you!

---

### Post by Das Hammer on 2008-11-05
> **robertbc said:**
> I'm not sure if I should duplicate my answer (today is the first time I write on a forum), but this is (I hope) the link

[http://ubuntuforums.org/showthread.php?p=6114149](http://ubuntuforums.org/showthread.php?p=6114149)

Hope this helps you!

I read your answer at the linked post, robertc, and I appreciate your help.  Creating another connection with the same MAC address will work; however I am having a problem with this.  When booting up, the system chooses to use the "auto eth0" interface by default instead of the connection I just created.  I still have to choose the new connection manually in order to get my static IP.  In my setup, this is not going to work because I have some services that run automatically after I log in and they fail because of having the wrong IP address on this machine.  Perhaps there is a way to tell the system which of the wired connections is "preferred"??????  I have to assume there is some way to do this, similar to the Mac OS.

MockY suggested adding back in what we were used to seeing in the /etc/network/interfaces file.  This does work.  The system chooses to use auto eth0 by default (at least from what I've seen so far), so adding these lines back in changes the definition of what auto eth0 is.  

I do appreciate everyone's input and help.  By searching and reading I was able to get the problem solved here without begging!

---

### Post by shivathreya on 2008-11-07
USE WICD. Its GOD for roaming/static users.

Shiva

---

### Post by sirius56 on 2008-11-16
I too am having serious problems with network-manager in 8.10.

My system can't seem to hold on to a static IP address.  Even after I set up the static settings in network-manager  0.7.0,  my system reverts to a DHCP address.

This is the only bug I found in Intrepid

Can anyone tell me the purpose  of the "**System setting**"  checkbox in network-manager?

---

### Post by Nanthiel on 2008-11-22
Hello, I would also like to know what the 'System Settings' checkbox does.

Also, my Netmask changes automatically to "24" when I edit it into 255.255.255.0... any ideas?

---

### Post by sirius56 on 2008-11-22
Nanthiel,

The 24 is another representation of   255.255.255.0


255  represents 8 bits on.   so you have 8+8+8bits = 24


I hope that the Ubuntu team will fix the Network Manager bug soon because it is annoying.

Why can't we just roll back to the previous network-manager?

---

### Post by Nanthiel on 2008-11-22
Thanks, sirius56!

---

