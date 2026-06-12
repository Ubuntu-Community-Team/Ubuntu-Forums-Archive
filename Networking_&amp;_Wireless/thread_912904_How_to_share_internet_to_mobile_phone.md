---
title: "How to share internet to mobile phone?"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by kastekm on 2008-09-07
Yo!
I wanna to share Internet to my mobile phone (k750i).
How I can do that? (Phone -> Opera mini -> free internet via bluetooth)

---

### Post by conkerboy12 on 2009-04-08
Got the same problem, except im trying to get my Sony Ericsson k600i working with sharing!
Connor

---

### Post by wangsuda on 2009-04-08
Similar problem with an older W300i. Works great with the USB cable, but can't do anything with Bluetooth. Would love to use Bluetooth to connect to the internet through Ubuntu. Any help?

---

### Post by wangsuda on 2009-04-19
*bump*

---

### Post by inobe on 2009-04-19
oops

---

### Post by wangsuda on 2009-10-24
> **wangsuda said:**
> Similar problem with an older W300i. Works great with the USB cable, but can't do anything with Bluetooth. Would love to use Bluetooth to connect to the internet through Ubuntu. Any help?
As far as I have been able to figure out, there is no way to do bluetooth internet using mobile broadband. I've checked almost everywhere.

---

### Post by AlanR8 on 2009-10-24
Just solved this exact problem and can now access the web via bluetooth over my Nokia Navigator (6210).

Note I'm using Karmic Beta and had already paired the phone via the bluetooth manager. All I did was install blueman

code
> sudo apt-get install blueman

to install the bluman interface.

Once installed I opened the app to find the phone already paired. Next click Device/ Serial Ports/Dialup Services and the connection was made. Now my Nokia appears in network manager as if it was connected by USB.

Click to surf!

---

### Post by wangsuda on 2009-10-24
> **AlanR8 said:**
> Just solved this exact problem and can now access the web via bluetooth over my Nokia Navigator (6210).

Note I'm using Karmic Beta and had already paired the phone via the bluetooth manager. All I did was install blueman

code


to install the bluman interface.

Once installed I opened the app to find the phone already paired. Next click Device/ Serial Ports/Dialup Services and the connection was made. Now my Nokia appears in network manager as if it was connected by USB.

Click to surf!
Great to know, thanks! A quick search shows that blueman is only for Karmic. To learn more and/or download, go to [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=blueman](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=blueman)

---

### Post by walmis on 2009-10-24
> Yo!
I wanna to share Internet to my mobile phone (k750i).
How I can do that? (Phone -> Opera mini -> free internet via bluetooth)     To enable your computer to be a network access point, you have to enable it in "local services" in blueman.

[IMG]http://blueman-project.org/images/stories/screenshots/1.0/screenshot_02.png[/IMG]

Also i recommend installing blueman from it's official PPA:
[https://edge.launchpad.net/~blueman/+archive/ppa]("https://edge.launchpad.net/%7Eblueman/+archive/ppa")

---

### Post by wangsuda on 2009-10-25
I followed their instructions for the Jaunty release. Unfortunately, I cannot find where Blueman is, any way to activate it, or even bring up a window like you have. Any advice would be appreciated!

---

