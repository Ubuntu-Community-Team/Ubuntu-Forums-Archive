---
title: "Gui for ISDN connection in feisty needed"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by der_vegi on 2007-05-19
Hi!

I've got a problem: I'm sitting here in front of an old machine in a little village where the fastest internet connection available is ISDN. No DSL or so. I'm configuring a fresh install of Feisty for my parents. They are quite new to computers, copying images from a camera to a PC is a difficult task for them. :) So I need an easy, reliable way for them to connect to the internet, as I am living 5hours away from them and can't help. :)

The card (AVM Fritz) is already working and i can connect using
```
pppd call isdn/talkline
```. I've made capiinit start automatically by editing /etc/network/interfaces:
```
auto ppp0
iface ppp0 inet ppp
pre-up capiinit
provider ppp0

```
But I can't edit the configuration in Network Manager. When I set up the provider over manual configuartion it doesn't remember the setting, it simply doesn't work. i've tried gnome-ppp and kppp but there you can only set modems, can't find the ISDN card.
So is there a gui that makes it easy to execute the pppd command? Just like kinternet or so?

Thanks for your help!

---

### Post by ctsdownloads on 2007-05-19
I looked and looked and I guess the demand for ISDN is just not been strong enough for one yet. The best I found was this page for the most recent app for ISDN
[http://www.misdn.org/index.php/Main_Page](http://www.misdn.org/index.php/Main_Page)

Sorry

---

### Post by der_vegi on 2007-05-19
Well, I had Suse 9.2 installed on that machine and it worked over Kinternet without a problem. So is just an issue of Ubuntu not really supporting it? This would be a showstopper, forcing me to install Suse again... :(

---

### Post by der_vegi on 2007-05-19
I only need a very simple gui, one that shows an icon for "connected" after the command ```
pon talkline
``` has been executed and that executes ```
poff
``` after the second click, showing "disconnected" then. Isn't there something like this out there?

---

### Post by der_vegi on 2007-05-19
okay, by editing /etc/network/interfaces to
```
auto ppp0
iface ppp0 inet ppp
pre-up capiinit
provider talkline
down poff -a
```
I can start the internet connection via Network Manager => dial-up. But the symbol doesn't change to connected. The bigger problem is, that I can't disconnect... :confused:

---

### Post by suoko on 2007-06-20
fedora also let me configure isdn connections very easily.
Any chance to port its gui?

---

