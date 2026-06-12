---
title: "wireless stability between kubuntu and ubuntu"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by dope540 on 2008-09-10
hi,

i was wondering if the wireless in kubuntu is more stable than in ubuntu.

this is because a few days ago i installed ubuntu 8.04 on my compaq presario v3000 laptop with a broadcom bcm 4312 wireless card.

for the first three days it worked fine, then it jsut stopped. even when i sat right next to the router. i know its not a router problem as my sis's laptop running vista has its wireless running fine.

am now running opensuse as its a bit more stable, but would like to return to ubuntu or kubuntu as theres more support for it and its easier to use.

so just wondered if kubuntu 8.04 has any stability issues.

---

### Post by dope540 on 2008-09-10
bump.

anyone?

---

### Post by arunvir on 2008-09-11
do check whether you are able to scan any networks through the command line
like 

sudo iwlist wlan0 scan(I think thats the command)

and check whether your network identified by your SSID(BSSID) shows up there.

also mention the network manager that you have been using.
Try using wifi-radar or wicd and report back if you any more issues.

I would prefer wifi-radar it works for me like a gem in kubuntu. I'm sure it'll do fine in ubuntu more than it does in kubuntu.

All the Best!!!

---

### Post by dope540 on 2008-09-11
> **arunvir said:**
> do check whether you are able to scan any networks through the command line
like 

sudo iwlist wlan0 scan(I think thats the command)

and check whether your network identified by your SSID(BSSID) shows up there.

also mention the network manager that you have been using.
Try using wifi-radar or wicd and report back if you any more issues.

I would prefer wifi-radar it works for me like a gem in kubuntu. I'm sure it'll do fine in ubuntu more than it does in kubuntu.

All the Best!!!

hi,

thank you very much for your reply.

when i was on ubuntu, it can find the networks and their names, just wouldn't connect after a few days.

---

### Post by arunvir on 2008-09-11
just do check with wifi-radar....... As far as I know It does work well with ubuntu. And reply back if you have any problems.

One Note:- remove the wireless configurations that you have given in the default network manager and then try wifi-radar..... It could just work to your liking......

check whether you have enabled any MAC filtering on your router and check in your router whether your Laptop MAc is getting detected on station info....

---

### Post by dope540 on 2008-09-11
> **arunvir said:**
> just do check with wifi-radar....... As far as I know It does work well with ubuntu. And reply back if you have any problems.

One Note:- remove the wireless configurations that you have given in the default network manager and then try wifi-radar..... It could just work to your liking......

check whether you have enabled any MAC filtering on your router and check in your router whether your Laptop MAc is getting detected on station info....

cool, thanks.

sorry to be a noob, but how do i remove the wireless configurations.

i think the mac filtering is enabled as initially ubuntu works, then stops after a few days.

---

### Post by arunvir on 2008-09-11
by remove configuration from network manager I just meant to remove the ip addresses, SSID and other stuff that you might have entered into the network manager

then just install wifi-radar and start working remember that you have to connect when using wifi-radar at each startup and it doesn't connect by itself.

for Mac filtering, I meant whether you have added your Wireless MAC address to be the only one that can access your router or you have allowed access for all the systems in the range. If you have added only your MAC to access the router, then no one else can access your router(Access point).

Simple don't worry.
try wifi-radar and tell me whether you can work with it.

before entering details about your network into it, just try getting as much info as possible from the command line

sudo iwlist wlan0 scan

and from your router settings.

Just try this and reply back whether everything works

---

### Post by dope540 on 2008-09-11
> **arunvir said:**
> by remove configuration from network manager I just meant to remove the ip addresses, SSID and other stuff that you might have entered into the network manager

then just install wifi-radar and start working remember that you have to connect when using wifi-radar at each startup and it doesn't connect by itself.

for Mac filtering, I meant whether you have added your Wireless MAC address to be the only one that can access your router or you have allowed access for all the systems in the range. If you have added only your MAC to access the router, then no one else can access your router(Access point).

Simple don't worry.
try wifi-radar and tell me whether you can work with it.

before entering details about your network into it, just try getting as much info as possible from the command line

sudo iwlist wlan0 scan

and from your router settings.

Just try this and reply back whether everything works

thank you very much.

will try out wifi radar tonight.

not too sure about the mac address, i setted up teh router when i was using windows waay back. pretty much left most of the stuff there as default and just added a wpa password.

---

### Post by arunvir on 2008-09-11
I think you do know about certain security measures that you have to take for the wireless like:-

Setup MAC Filtering (though it seems it can be broken)
Hide your Access point
enable some kind password(WEP or WPA)
for network authentication I generally prefer open with WEP ebcryption
I mainly disable DHCP in my network

I think you also did this once you had windows with wifi.:):):)
I think that can help here too.
All the best with wifi radar.......... I'm too sure that it'll help you!!

:guitar::guitar::guitar:

---

### Post by dope540 on 2008-09-11
yeah, it rings a bell. it was a looong time ago. lol.

dont really want to change the settings as besides me running ubuntu, all the other laptops that my family use are fine with the wireless.

knowing my luck with tinkering things, i'll hash up the wireless.

will keep you posted on how wifi radar goes and will post any problem i get.

---

### Post by arunvir on 2008-09-11
ok.......... 

even i used to have that touch of yours...... But my family members kind of got used to it........

All the best.........

:):):):)

---

### Post by arunvir on 2008-09-11
I did face some hickups recently and I have found out how to deal with them with wifi-radar

after installing it in kubuntu right click on properties and change the command option in the application tab from 

gksudo -S wifi-radar

to

kdesudo wifi-radar(if you are using kubuntu, I mean)

The bottom line before the close button in wifi radar lets you get so much info. Do check it now and then.

The following are the possible things there in that place and what they mean to you:-

connected to none(ip address:none) -> you are not connected to any network or your wifi card is turned off.

connected to <your network name>(ip address:none) -> you have got no ip from your network or you need to set one manually or you have been disconnected recently.


connected to <your network name>(ip address:something) -> means that you are connected to your network.

(if you are not able to browse after that the last step too, try disabling the eth0 interface temporarily in the network manager. try disconnecting and re-connecting to the wireless network. then you must have internet connection. finally you can enable your eth interface if you want.

The reason I ask you to disable it temporarily because you could have manually given the gateway for both as nearly same which could be considered by the system to be a conflict.)


All the Best!!!!!!

---

