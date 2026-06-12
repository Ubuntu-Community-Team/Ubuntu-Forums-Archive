---
title: "Vodafone Broadband Adaptor (3G) with ubuntu?"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by Nightstrike2009 on 2009-09-25
Hello everyone,

I recently purchased a Vodafone 3G Broadband USB Dongle to access the internet. I uses a program called "Vodafone Mobile Connect Lite" under windows XP to connect to the internet. 

It's classed as a "HUAWEI Mobile Connect - 3G Modem #4" in device manager, if that info is any use.

I am wondering can I use this with Ubuntu 9.04 and would I need any additional (Ubuntu Linux) software to connect under Ubuntu? 
(If Possible at all)

Thanks In Advance

PS: Got no reponse staight away but found this looks as if it may help [http://ubuntuforums.org/showthread.php?t=1240240&highlight=vodafone+mobile+broadband]("http://ubuntuforums.org/showthread.php?t=1240240&highlight=vodafone+mobile+broadband")

---

### Post by GeorgeVita on 2009-09-25
Hi **Nightstrike2009**,
most times a **Huawei** 3G modem works directly with network manager and Ubuntu 9.04. Some users prefer other s/w as VMC or WiCD just to get signal strength and send/receive SMS which is not provided via network manager.

Just to be sure, find the 'real product name' from the sticker (bottom of the modem or at the package) and post/search here.

Regards,
George

---

### Post by Nightstrike2009 on 2009-09-27
In Reply to GeorgeVita, it's marked as

VODAFONE MOBILE CONNECT
MODEL: K3565 - REV 2
HSDPA USB STICK

---

### Post by lemmy999 on 2009-09-27
@Nightstrike2009

Network-manager should detect the dongle and configure it for you. You'll have to select your airtime provider and package ( vodafone payg/contract) and thats about it. Ready to go!!

---

### Post by FreewheelinFrank on 2009-09-27
There seems to be a Linux driver for this you need to install:

> The following operator(s) are known to replace Huawei's software with their own:

    * Vodafone puts on its E220 (Vodafone Mobile Connect USB Modem) its Windows Vodafone Mobile Connect Lite software, which is a lighter version of Vodafone Mobile Connect. In Windows it uses the excutable VodafoneUSBPP.exe. This device is also supported in Linux, using Vodafone Mobile Connect Card driver for Linux, which can be downloaded from Vodafone Betavine.

[http://en.wikipedia.org/wiki/Huawei_E220](http://en.wikipedia.org/wiki/Huawei_E220)

---

### Post by GeorgeVita on 2009-09-27
Hi to all!

Although at least a user is using it with Ubuntu 9.04:
[http://ubuntuforums.org/showpost.php?p=7964575&postcount=2](http://ubuntuforums.org/showpost.php?p=7964575&postcount=2)
[http://ubuntuforums.org/showpost.php?p=7947822&postcount=29](http://ubuntuforums.org/showpost.php?p=7947822&postcount=29)

and a lot of posts exist at betavine site:
[http://www.betavine.net/bvportal/search.html?cx=013328705597064244943%3Aupfqra5bloi&cof=FORID%3A11&q=k3565+ubuntu&sa.x=0&sa.y=0&sa=Search#1114](http://www.betavine.net/bvportal/search.html?cx=013328705597064244943%3Aupfqra5bloi&cof=FORID%3A11&q=k3565+ubuntu&sa.x=0&sa.y=0&sa=Search#1114)

...it is not very clear, but always thinking positively we could try if above did not work. Also I believe 9.10 could handle it better.

Regards,
George

---

### Post by Nightstrike2009 on 2009-11-03
Got it working in jaunty before i upgraded? to karmic and it borked the networkmanager again sigh :(

---

### Post by Nightstrike2009 on 2009-11-13
Has the bug in networkmanager been resolved yet? Where do i download it from?

(I am using Ubuntu 9.04 until fix is available as Vodafone 3G Modem doesn't connect on Ubuntu 9.10)

---

### Post by GeorgeVita on 2009-11-13
Hi **Nightstrike2009**,
The most possible cause for your problem is: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)

which solved (Huawei E169, E220) with the release of Karmic kernel 2.6.31-15 (was at 'proposed' updates)

... however you must try it to be sure!

Regards,
George

---

### Post by Nightstrike2009 on 2010-01-19
I have heard you can resolve it by downgrading to a lower kernel this is beyond my ubuntu know how thou.

> lemmy999:@Nightstrike2009

Network-manager should detect the dongle and configure it for you. You'll have to select your airtime provider and package ( vodafone payg/contract) and thats about it. Ready to go!!

I know it should mate thats the problem the wizard comes up you make you choices ok it, connect to internet and it fails to work, you just get page load errors in firefox that didn't occur in 9.04.

I hope to god this is fixed or resolved in 10.4LTS(Lucid) or may have to use 9.04 until ubuntu 10.10 is out.

Don't suppose its been fixed on 9.10 yet has it?

---

