---
title: "Dlink DWL-520 help needed"
date: 2004-12-16
forum: Networking &amp; Wireless
---

### Post by Zeitgueist on 2004-12-16
I recently installed Warty as a dual boot with XP on my machine, and everything is going well, except for the fact that my wireless card isn't being recognized...it is a Dlink DWL-520, revision E.   I did a search and the last person with an issue with this card had version B, and was referred to  [this](http://support.dlink.com/faq/view.asp?prod_id=357&question=linux)  page.  I followed the link and ran into three problems.  One is that I have no idea what file I need.   The second is that the FAQ seems to say that this driver will not work with a Debian distro, which I understand Ubuntu is Debian-based.  Third, the readme says that I need kernel source, and I simply have no idea what they mean, or how to do it.  As you can guess, I'm a windows guy and thus a complete noob when it comes to Linux.

Can anyone help me out?

---

### Post by p!=f on 2004-12-17
[QUOTE=Zeitgueist]I recently installed Warty as a dual boot with XP on my machine, and everything is going well, except for the fact that my wireless card isn't being recognized...it is a Dlink DWL-520, revision E.   I did a search and the last person with an issue with this card had version B, and was referred to  [this](http://support.dlink.com/faq/view.asp?prod_id=357&question=linux)  page.  I followed the link and ran into three problems.  One is that I have no idea what file I need.   The second is that the FAQ seems to say that this driver will not work with a Debian distro, which I understand Ubuntu is Debian-based.  Third, the readme says that I need kernel source, and I simply have no idea what they mean, or how to do it.  As you can guess, I'm a windows guy and thus a complete noob when it comes to Linux.

Can anyone help me out?[/QUOTE]
I've never had that toy in my hands but I think I can be of help. :)
I hardly doubt it won't work under Debian as I can't see any reason why shouldn't. See those FAQ which say there's Debian package in testing/unstable.
Can you post uname -r output here?
```

[~] > uname -r
2.6.9-cko3

```
So we know what's your running kernel and which kernel-headers to use.
You will also need some development tools and module-assistant so just to be prepared, run
```

sudo apt-get install build-essential automake autoconf module-assistant

```
If you prefer GUI use Synaptic to install the package mentioned above.

---

### Post by Zeitgueist on 2004-12-18
My uname output is "2.6.8.1-3-386".


I also typed what you had reccommended, and got an error message saying that the "automake" package was not availible.

---

### Post by arago on 2005-01-05
I own a DWL 610 that works fine with ndiswrapper.

So look for ndiswrapper howto's.

---

### Post by sobralense on 2005-01-05
I'm just using the acx_pci module (acx100.sf.net) isnt the newer driver version that come with ubuntu, but thats ok for a bit of "kismet" working and free wireless access.

*I'm using the wireless card to access the internet and post this.


*Using the DWL 520+ (that comes with acx100 chip)

 I think your dwl 520 is better supported than mine.

---

### Post by klausi banausi on 2005-01-26
hello - as you can guess I'm a linux newbee too - I've got a d-link dwl g520+ - ubuntu recognizes my card but as soon as I what do activate it , it turns off a few seconds later - those anybody know how I can get this card working or how I can find out what kind of chip this card uses? merci in advance
klaus

---

### Post by nicholaspaul on 2005-01-26
i have the problem of check boxes clearing themselves too, and I've seen other posts concerning this, but no one seems to know why. Very strange.

---

