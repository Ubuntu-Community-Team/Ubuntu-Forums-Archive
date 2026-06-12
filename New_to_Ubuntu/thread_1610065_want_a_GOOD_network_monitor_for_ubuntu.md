---
title: "want a GOOD network monitor for ubuntu"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by dhiman33 on 2010-10-31
:roll:I've noticed the network monitor of system monitor doesn't show accurate ul/dl status. For example, whenver I poff my net connection, the recieved data decreases(like from 12 mb to 6 mb).Also, the usage data according to the network monitor doesn't match the usage details that I see from my broadband usage details page.

Is there a fine network monitor in ubuntu(GUI please!) that shows in real time how much data in bytes or kbs are being recieved/sent without any glitch like the default one? #-o

---

### Post by Zill on 2010-10-31
dhiman33:  Is your internet router connected to a *single* PC?

If there are other PCs connected then your ISP bandwidth monitor will show the *total* usage, which will be greater than that shown by each PC's network monitor.

ps.  Internal LAN traffic can skew the figures both ways!

---

### Post by NickJones on 2010-10-31
Have you tried the built in one via system monitor. If the numbers are different to that of your ISP, it's most likely that your ISP takes some time to register your usage. 

You must also remember that any other computers, phones, games consoles etc, all go out, so unless it's just you, you must count these too.

---

### Post by waynefoutz on 2010-10-31
What I use:
Look in synaptic for
gnome-netstatus-applet

After you install this, you can add "Network Monitor" to your top or bottom panel, by right clicking on it and selecting "add to panel." It might require a reboot before you find it in the list. Once it's diplayed right click on it and choose "properties," and make sure it's set to monitor the PPP connection.

It won't keep a running total, but it will  tell you what you've used in a session. In other words, once you disconnect, it will zero out. But it will give you an idea of what you are using, plus the lights flicker on the icon when there is activity happening. I simply check it, make a mental note and do the math in my head. If you have a 5 gig plan, then you know to keep usage under 166 megabytes a day. If I log on in the morning and use 40 megabytes, I Know I have 126 left when I come home from work. 

This is the best method I can find. 

If you have Verizon, which I don't, there is a Firefox add-on that actually logs on with Verizon and shows you Verizon's numbers displayed right there on Firefox's tool bar.

---

### Post by dhiman33 on 2010-11-01
:lolflag:First, yes my pc is the single one that uses this connection. Nothing else is ever connected to it.

:-\"Second, the usage data on the bb site shows me the date and time interval of usage along with data transfer(ul+dl).I've checked that in a time interval, my usage is much lower than shown on the network monitor which is a part of the system monitor.

](*,)Third,I've already told when I cut the connection, the usage shown on the system monitor drops, and i think this might be the actul data transfer happening during the session.

[-(Fourth, I'm not very interested to use that applet 'cause it depends on the network monitor data,isn't it. So if network monitor is wrong, it should also be wrong.

Now what to do?:confused:

---

### Post by dhiman33 on 2010-11-01
O.K, can someone tell me why the usage shown on the netwrk mon decreases when I cut the net connection?

---

### Post by Zill on 2010-11-01
> **dhiman33 said:**
> O.K, can someone tell me why the usage shown on the netwrk mon decreases when I cut the net connection?
Maybe I am missing the point but surely that is what you expect to happen. :confused:  The internet traffic *should* stop when you cut the net connection!

---

### Post by dhiman33 on 2010-11-01
[-XNo no. I'm saying the total recieved data decreases when I cut off the connection. For example, right now I'm connected, and network monitor says till now I've received a total of 15.2 mb data and sent a total of 1.5 mb data.I've cut off from net, net. mon.shows total received data=8.2 mb and total sent data=1.5 mb. So the TOTAL received data drops by nearly half when I cut off the net connection.#-o

---

### Post by Zill on 2010-11-01
dhiman33:  Thank you for the clarification.  I don't know exactly how you connect to your router but if I pull the ethernet plug from my PC, totally disconnecting the internet connection, then the totals shown in System Monitor, Network History remain unchanged.

My System Monitor is v2.28.0 on 10.04 Lucid.  Which version are you running?

Please also clarify what you mean by "...whenver I poff my net connection...".  My broadband router is permanently on and connected to my PCs via a LAN so they are never disconnected.

---

### Post by dhiman33 on 2010-11-02
:grin:Thanks for ur reply Zill; I use ubuntu maverick meerkat's system monitor.

Here's how I connect to my router.

First step:
sudo ifconfig wlan0 192.168.1.2
sudo route add default gw 192.168.1.1
sudo iwconfig wlan0 essid WA1003A
sudo vi /etc/resolv.conf

Second step:
sudo pppoeconf, and entering my bb username/password

Third step:
sudo pon dsl-provider to trigger the connection

And to stop the connection, I use "sudo poff"

That's why I'm saying the "poff" word.

Just now I've used "sudo poff" and then "sudo pon dsl-provider" to cut off and then retrigger my connection.This is what happened.

Before cutting off connection, total received data=3.2 mb, total sent data=435.8 kb
After cutting off, total received data=1.6 mb,total sent data=435.8 kb.
Now after triggering the connection once again,total received data=1.8 mb, total sent data=436.1kb(after using it for about 2-3 min)

I suspect when I poff my connection, total received data becomes half! How that can happen!@#$%^!:shock:

---

### Post by dhiman33 on 2010-11-02
Total data received=16.8mb total uploaded=3.2mb was a few moments before.I momentarily cut off the net connection.Now it shows tot. data received=9.3mb, total sent= 2mb. What's going on!:confused:

---

### Post by SeijiSensei on 2010-11-02
Try [ntop](http://www.ntop.org/news.php).  It's in the repositories.

---

### Post by Zill on 2010-11-02
> **dhiman33 said:**
> ...First step:
sudo ifconfig wlan0 192.168.1.2
sudo route add default gw 192.168.1.1
sudo iwconfig wlan0 essid WA1003A
sudo vi /etc/resolv.conf

Second step:
sudo pppoeconf, and entering my bb username/password

Third step:
sudo pon dsl-provider to trigger the connection

And to stop the connection, I use "sudo poff"...
I am slightly puzzled as to why you are using such a complicated method of connecting to the internet!

It should be simply a matter of entering the ISP configuration info once into your broadband router and then using the Ubuntu Network Manager (or a similar app) to connect when required.

Unfortunately, I have no idea about the "data totals" problem - maybe someone else can throw some light on this.

---

### Post by dhiman33 on 2010-11-03
[-o<Zill please tell me how to connect to internet using a simpler method than mine. Please tell everything assuming I'm a beginner and know NOTHING!:lolflag:Pls pls pls plssssssss....[-o<[-o<[-o<

---

### Post by migs73 on 2010-11-03
Try this;

[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)

---

### Post by Zill on 2010-11-03
dhiman33:  I would start by ensuring the broadband router is correctly configured.  Generally the default settings should be OK but you will certainly need to enter your broadband logon username and password.  The router configuration screen is generally accessed via your web browser using a local address such as [http://192.168.0.1](http://192.168.0.1).  Your router manual should give full setup information.

One top tip is to configure the router using an ethernet cable to your PC.  Once you have everything configured correctly so you can connect to the internet, you should then set up the wireless connection.

When the router is correctly configured, the default Gnome network manager in Ubuntu should recognise this (both wired and wireless) and connect when required.  The link supplied by migs73 gives more details on this.

There have been reports of *some* problems with the default network manager and so I personally do not use it.  However, if you do have any difficulties with this then just post all the relevant info and someone is sure to help. ;-)

---

### Post by dhiman33 on 2010-11-04
;-)Ok, I'm elaborating the infos.

First of all, the reason why I had to use the terminal method is that the network applet on the sys tray couldn't connect to my wireless router:cry:. It recognised it, tried to connect to it, then failed. I think I should change some options in my huawei router, but very panicked to do so as I don't understand any setting in it#-o.

Second, after I did this sudo things, the net.connection applet vanished from sys tray!:shock: I can't recall exactly after which command in the terminal etc. this happened, though I suspect after the ifconfig, adding default gw,doing iwconfig etc it vanished. How to get it back?:|

---

### Post by dhiman33 on 2010-11-04
U also say u don't use the default net manager. What do u use then?

---

### Post by Zill on 2010-11-04
> **dhiman33 said:**
> ;-)Ok, I'm elaborating the infos.

First of all, the reason why I had to use the terminal method is that the network applet on the sys tray couldn't connect to my wireless router:cry:. It recognised it, tried to connect to it, then failed. I think I should change some options in my huawei router, but very panicked to do so as I don't understand any setting in it#-o.

Second, after I did this sudo things, the net.connection applet vanished from sys tray!:shock: I can't recall exactly after which command in the terminal etc. this happened, though I suspect after the ifconfig, adding default gw,doing iwconfig etc it vanished. How to get it back?:|
This is one reason why I don't use the Gnome Network Manager. ;-)

Personally, I would break this problem into two parts.  *First* get the wired connection configured and working correctly.  Only *then* get the wireless connection configured and working correctly.

Establish if you use a static or a dynamic (DHCP) IP address to connect your PC to your router.  If you don't know this and/or have no reason to specify a static IP address then the default dynamic address should work fine.

I *do* use a static address and so have specified this in my /etc/network/interfaces file eg:
```
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.0.7
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0
```
To use a dynamic address, I understand I would need to change my interfaces file to something like this:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

See "[Network Configuration]("https://help.ubuntu.com/9.10/serverguide/C/network-configuration.html")" for more info.

With a similar entry in your interfaces file, the Gnome Network Manager becomes irrelevant as it is not used. :-)  With a correctly configured router, you should be online (with your wired connection) as soon as you boot your PC.

When this is achieved we can progress to setting up the wireless connection if you advise exactly what model router and wireless card you are using.

---

### Post by Zill on 2010-11-04
> **dhiman33 said:**
> U also say u don't use the default net manager. What do u use then?
As detailed in post [19]("http://ubuntuforums.org/showpost.php?p=10071205&postcount=19") above, I use the /etc/network/interfaces file to define my static wired connection.

For wireless connection I use [Wicd]("http://wicd.sourceforge.net/").  Unfortunately, the Lucid default version of Wicd (v1.7) has a "bad password" bug with my hardware and my workaround is to downgrade Wicd to the Karmic version 1.6.  This works fine for me and I can easily switch between wired and wireless connection - no cryptic or hazardous sudo commands needed. ;-)

---

### Post by dhiman33 on 2010-11-05
OMG:shock:, that's more complicated than my method. Actually I had to use all those commands to connect to net for the first time. Now I have to enter 3 commands to connect:O:)

1.sudo ifconfig wlan0 192.168.1.2
2.sudo iwconfig wlan0 essid WA1003A
3. sudo pon dsl-provider

And to turn off, "sudo poff". I've read the link,and now understand the basics, have changed interfaces file with no luck. Where to put the usrname/password? Please tell with more detail,first how do I connect to wireless(or ethernet 1st if u say so),then how to configure my usrname/password, and how to trigger the connection using the usrname/passwrd?

---

### Post by Zill on 2010-11-05
The point about "my method" is that I have only entered the necessary information *once* - not every time I connect!

I do suggest you configure everything initally using a wired (ethernet) connection - wireless is an unneccessary complication at this stage.

Your username/password should be *permanently* stored in your router and this is done by accessing the router setup screens as mentioned earlier.  Your router manual will show how to access these screens.

When the router is configured with this broadband logon information, your PC will then connect *automatically* if the /etc/network/interfaces file is *also* configured correctly.

I do suggest you read your router manual and then set up the router as discussed.  I strongly recommend using an ethernet cable between your PC and the router for this process!

---

