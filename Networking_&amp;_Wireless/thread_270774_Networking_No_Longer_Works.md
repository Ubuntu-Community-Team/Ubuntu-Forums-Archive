---
title: "Networking No Longer Works"
date: 2006-10-03
forum: Networking &amp; Wireless
---

### Post by groberts1980 on 2006-10-03
So I power down the other day, and next time I power up I get these messages while booting:

Starting basic networking....failed
Configuring network interfaces....failed

And when I shutdown:
Deconfiguring network interfaces....failed


I didn't change a thing. Networking no longer works. When I go to the network settings, its a blank window that I have to force quit. Before this I had no problems whatsoever with the wireless.

I have a Dell Inspiron E1705 with built in Intel PRO/Wireless 3945ABG wireless.

Any ideas on how I can get this working again?

---

### Post by wieman01 on 2006-10-03
Have you pulled & installed any updates? Or possibly installed a firewall such as Firestarter? Let's try the obvious first.

---

### Post by groberts1980 on 2006-10-03
No recent updates, no firewall.

I do have firestarter installed, but it doesn't run at startup, and I don't usually run it (tired of typing root password every time it started).

There were updates available before networking quit, but I hadn't gotten around to updating. I believe a kernal update was on that list, but I can't be sure.

Also, I dual boot the computer with XP. Networking works fine in XP.

---

### Post by wieman01 on 2006-10-03
Firestarter is running by default... Don't confuse the GUI with the actual program that is running "in the background" as a process. You fire up the GUI by typing firestarter & punching in your password. The password is required because the GUI helps you configure Firestarter's settings.

So it's definitely running (you'll see the process being started during boot)... Try to run the GUI and press "shutdown firewall" for a minute, then re-establish your network connection:
> sudo /etc/init.d/networking restart

---

### Post by groberts1980 on 2006-10-03
When I started the firestarter GUI, I got the message:
"Failed to start the firewall. The device eth1 is not ready. Please check your network device settings and make sure your internet connection is active." I hit "Stop Firewall" anyway.

Should I uninstall firestarter just to make sure its not the problem?

I tried your command and got this:
```

 * Reconfiguring network interfaces...
/etc/network/interfaces:25:duplicate interface
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:25: duplicate interface
ifup: couldn't read interfaces file "/etc/network/interfaces"

                                            [fail]

```

Sorry about the formatting. I'm having to copy and paste to a text file on a thumbdrive, reboot into windows, and copy and paste into the reply window.

---

### Post by wieman01 on 2006-10-03
Oh... No, if Firestarter has fail to start it's actually down.

There is a problem with your "interfaces" file, however. Please do:
> gedit /etc/network/interfaces
There is probably something wrong with it (e.g. duplicate lines, etc.). Let's see what it is.

---

### Post by groberts1980 on 2006-10-04
sudo gedit /etc/network/interfaces

```

#auto lo
#iface lo inet loopback


#iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid linksys

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0

iface lo inet loopback

iface eth1 inet dhcp
wireless-essid linksys
wireless-key 642E4B369E

```

Those last three lines look strange. You said something about duplicate lines? I'm wondering why I have ssid's in there in the first place. Shouldn't it detect what ssid's are present each time, and go from there? Or is this file a way of storing common networks that you usually connect to?

---

### Post by wieman01 on 2006-10-04
Ok, edit your interfaces file & paste this (then save):
> auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid linksys
Please disable your router's security (WEP) first, then restart the network:
> sudo /etc/init.d/networking restart
If this is ok, we enable WEP security again. Please post the output of the last command.

I assume "linksys" is your networks ESSID, correct?

---

### Post by groberts1980 on 2006-10-04
Quick question: Do you want me to replace all the text in my interfaces file with the code you posted?

---

### Post by dannyboy79 on 2006-10-04
yes, he does. the problem is because ubuntu is getting confussed since you define what eth1 should do twice, once with wep and once without. i am curious though, you must have edited this in the past, why is your eth0 commented out? usually eth0 is the first interface. this is what I would try first

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
wireless-essid linksys

and if that doesn't work, then try 

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid linksys 

also don't forget to do the rest of what he suggests
Please disable your router's security (WEP) first, then restart the network:

Quote:
sudo /etc/init.d/networking restart  

If this is ok, we enable WEP security again. Please post the output of the last command.

I assume "linksys" is your networks ESSID, correct?

wieman01, i am not trying to take over for ya, it's just a thought that there is no reason to comment out eth0. at least i don't see one.

---

### Post by groberts1980 on 2006-10-04
Okay, I put this code in my interfaces:

```

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid linksys

```

ran:
```

sudo /etc/init.d/networking restart 

```

and got this:
```

 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:13:02:1b:42:0b
Sending on   LPF/eth1/00:13:02:1b:42:0b
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.2.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.102 -- renewal in 42288 seconds.
                                                                         [ ok ]


```

Networking seems to be working now, in that its connected to the wireless network, no wep, and I can browse the web. But when I go to System->Administration->Networking, I still get a blank window that I have to force quit.

I rarely use wired ethernet, and wireless has always been eth1 (I think). Is eth0 for wired ethernet? Do I need it initializing eth0 if I hardly ever use it?

---

### Post by dannyboy79 on 2006-10-04
the gui might be getting confussed because you have a eth0 ethernet card but you commented it out in the interfaces file. try this and see if you can get to the networking gui without a blank window

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid linksys

or if that doesn't work, remove the auto from eth0. which may make it so you have to configure it manually instead of it being auto, so it would be 

auto lo
iface lo inet loopback

eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid linksys

otherwise I can't help anymore. i am pretty much a newbie. good luck

---

### Post by wieman01 on 2006-10-04
> **groberts1980 said:**
> Networking seems to be working now, in that its connected to the wireless network, no wep, and I can browse the web. But when I go to System->Administration->Networking, I still get a blank window that I have to force quit.

I rarely use wired ethernet, and wireless has always been eth1 (I think). Is eth0 for wired ethernet? Do I need it initializing eth0 if I hardly ever use it?
Good, we are once step further. No, if you don't need "eth0" that I'd just take Dannyboy79's suggestion and remove the "auto". "eth0" usually stands for your wired connection. 

As for the GUI, beats me. Perhaps Dannyboy79's proposal helps. 

That said, want to try WEP?

---

### Post by blueidealist on 2006-10-14
Ok - little story which will not make you feel so alone.
The same thing just happened to me 10 minutes ago.  Everything worked fine, I did no updates, did not touch internet settings in any way.  Shut down - now this morning I turn the computer on, and ...

Configuring network interfaces FAILED
Starting basic networking FAILED
and network-admin refuses to launch...

I normally connect on the internet via my wireless...
And somehow the ethernet connection here works (this is how I"m writing to you) while my wireless is down.

When doing:
//
david@David:~$ gedit /etc/network/interfaces

** (gedit:5188): CRITICAL **: egg_recent_model_open_fi le: assertion `file != NULL' failed

** (gedit:5188): CRITICAL **: egg_recent_model_add_ful l: assertion `file != NULL' failed
//

I haven't seen these errors before.  NEvertheless, gedit opens the file and returns:

auto lo
iface lo inet loopback

iface eth1 inet dhcp
wireless-essid WANADOO-09B8
wireless-key BF9B1B8479EF94B1E898A7404C



iface eth0 inet dhcp



auto eth0

iface ppp0 inet ppp
provider ppp0

auto eth1

iface  inet static
iface

---

### Post by blueidealist on 2006-10-14
Also, while connected to the internet right now, I tried this...

david@David:~$ sudo apt-get update
sudo: unable to lookup David via gethostbyname()

What is this error?

---

### Post by blueidealist on 2006-10-14
Update:

Using this thread:
[http://ubuntuforums.org/archive/index.php/t-78324.html](http://ubuntuforums.org/archive/index.php/t-78324.html)

I was able to solve the gethostbyname error.

I'm still stuck with my network interfaces errors though,

David

---

