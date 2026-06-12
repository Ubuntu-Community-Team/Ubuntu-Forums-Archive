---
title: "software installation"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by mystmaiden on 2009-04-22
I'm having all kinds of trouble with downloading needed software. I followed a couple of the tutorials here but Ubuntu is not behaving as the tutorial specifies. The repositories are out of date, and when I ran the search for cabextract in Synaptic, the search came up blank so I could not proceed with that tut. 

I just installed Ubuntu 7.04.. Someone point me to information on how to get the repositories and synaptic running please? I'm sure some of my difficulty here is that I am working on the after-the-windows-bsod-crash fatigue.

Thanks
mystmaiden

---

### Post by sydbat on 2009-04-22
If you can, upgrade to 8.04 (Hardy LTS) or 8.10 (Intrepid). I do not think 7.04 (Feisty) is supported anymore.

You should be able to do this by going into "Software Sources" and choosing "Normal Releases" under the "Updates" tab. When it refreshes, you will get the upgrade notification.

Alternately, download one of the above (8.04 or 8.10) and burn it to CD, then reinstall/upgrade.

Either way, make sure to back up all your important stuff first.

---

### Post by halitech on 2009-04-22
if you are unable to download and burn 8.04 there are instructions here to upgrade

[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

Edit: actually I think 7.10 is no longer supported either ( I think it just ended support) but you can try it, if it works, great, if not you'll need to get a copy of 8.04

---

### Post by sadaruwan12 on 2009-04-22
> **mystmaiden said:**
> I'm having all kinds of trouble with downloading needed software. I followed a couple of the tutorials here but Ubuntu is not behaving as the tutorial specifies. The repositories are out of date, and when I ran the search for cabextract in Synaptic, the search came up blank so I could not proceed with that tut. 

I just installed Ubuntu 7.04.. Someone point me to information on how to get the repositories and synaptic running please? I'm sure some of my difficulty here is that I am working on the after-the-windows-bsod-crash fatigue.

Thanks
mystmaiden

Yo BRO,

First of all Y did you go with a old version like 7.04 while you can get the newest version from canonical for free. Any way Ubuntu repos are little behind in there update rate 'cos they include the most stable version of software so the end user want get any hiccups after installing software from the repos. If you want the newest and latest you can got to any free software makers website ad there own distro link to you Ubuntu package manager sources.list. before you do anything update your system the there will be lesser troubles you to take turns with and I checked my Synaptic Package Manager (SPM) for cabextract it's there in the software list.

Do this Go to System (on the top panel) -> Administration -> Software Sources

Click Ubuntu software and check all the check boxers there and now click on third-party software and select all the software sources listed there now go to Update tab and select all the check boxers under ***Ubuntu Updates***. Click on close wait till the software rebuilds it's software date base if any notification come up saying there are system updates allow that update to go through after finishing that go to the SPM and search for you software it'll be there if not tell me I'll try to help you.


P.S: Support for 7.04 has died 'cos it's not a LTS version it's better to get V8.04(Hardy Haron) or V8.10(Intrepid Ibex) the newest version.

     [Click here to Get Ubuntu]("http://www.ubuntu.com/getubuntu/download") or [Here to get one CD shipped from Canonical]("https://shipit.ubuntu.com/")

---

### Post by Lunx on 2009-04-22
> **mystmaiden said:**
>  when I ran the search for cabextract in Synaptic, the search came up blank so I could not proceed with that tut. 

Thanks
mystmaiden


As stated earlier it may be a good idea to upgrade to 8.04. An alternative way I could suggest you could get it installed would be to install the Microsoft core fonts package (which is a good idea if you want the more "traditional" fonts). Installing them means cabextract is also downloaded automatically so the fonts can be installed (also once you have cabextract you will be able to install other fonts like Tahoma, which is one I can't live without as it renders so well on my screen)

Search the repositories for msttcorefonts, or you can install from command line by opening a terminal and entering
```
sudo apt-get install msttcorefonts
```

---

### Post by mystmaiden on 2009-04-22
As to why I used 7.04 - 'cause it's what I had, well, that and a completely dead windows, heh. I guess my little stash of Ubuntu cds needs refreshing!

I'll see if I can burn a cd for the newest version. Thanks to all for the very quick replies!

---

### Post by sadaruwan12 on 2009-04-22
> **mystmaiden said:**
> 'cause it's what I had, and I did not know it was out of date?

Yo mystmaiden it's a very good idea for you to upgrade your system to v8.04 or v8.10 'cos they are supported and backed up by all Ubuntu communities.

---

### Post by mystmaiden on 2009-04-22
One thing I didn't think of - I'll need a program to run my writable cd drive - is there any way to do that? 

As always, the help is appreciated!
mystmaiden

---

### Post by halitech on 2009-04-22
there are multiple programs for burning, brasero comes by default but you can install k3b or others if you want.

---

### Post by mystmaiden on 2009-04-22
Now for the really silly question - where do I find it on the system...

---

### Post by halitech on 2009-04-22
for brasero I think you just select the file(s) you want to burn and right click - burn(write) to disk but I don't use it so not 100% sure.

---

### Post by mystmaiden on 2009-04-22
Thanks a lot, I'll try that.

---

### Post by carml on 2009-04-22
> **mystmaiden said:**
> Now for the really silly question - where do I find it on the system...
If you're looking for Brasero,go to Applications->Audio & Video (should be there:) ).

---

### Post by mystmaiden on 2009-04-22
The plot thickens.. my first attempt at burning an iso didn't appear to work, in the end I had to reinstall  Feisty Fawn, but now it does not seem to 'see' my cd player. I know there was something I had to put  a check in to get it going before, now I can not remember where it is and can't find where I read that. Anyone know?

mystmaiden

---

