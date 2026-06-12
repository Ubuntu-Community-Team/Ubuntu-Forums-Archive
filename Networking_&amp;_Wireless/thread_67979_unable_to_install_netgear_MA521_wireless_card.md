---
title: "unable to install netgear MA521 wireless card"
date: 2005-09-21
forum: Networking &amp; Wireless
---

### Post by acejones on 2005-09-21
I have been working on this for 3 days now, and have gone through countless HowTo's on how to get this installed.  I have followed [this guide](https://wiki.ubuntu.com//SetupNdiswrapperHowto) to the T (which is the best i have found so far). 

 I run 
```
make deb
```
and everything seems to work ok untill i get to the end and it says 
```
make -C /usr/src/ndiswrapper-1.1/driver
make[3]: Entering directory '/usr/src/ndiswrapper-1.1/driver'
Can't find the kernel sources in /lib/modules/2.8.6.1-5-386/build;
   give the path to kernel sources with KSRC=<path> argument to make
make[3]; *** [prereq_check] Error 1
make[3]: leaving directory ' /usr/src/ndiswrapper-1.1/driver'
make[2]: *** [build-modules] error 2
make[2]: leaving directory '/usr/src/ndiswrapper-1.1 '
make[1]: *** [binary] Error 2
make[1]; leaving directory '/usr/src/ndiswrapper-1.1 '
make: *** [deb] Error 2
```
since this didn't work, its pointless to try the next step
```
cd /usr/src
dpkg -i --force-overwrite ndiswrapper-utils_1.1-1_i386.deb
dpkg -i --force-overwrite ndiswrapper-modules-$(uname -r)_1.1-1_i386.deb
```

[this site](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#N)  says to use the ndis5x-8180(xxx).zip driver at [ftp://210.51.181.211/cn/wlan/rtl8180l/](ftp://210.51.181.211/cn/wlan/rtl8180l/) (see number 11 under 'N').  i guess i need some help.  i'd like to get this card working.

---

### Post by acejones on 2005-09-22
> **acejones]I have been working on this for 3 days now, and have gone through countless HowTo's on how to get this installed.  I have followed [this guide](https://wiki.ubuntu.com//SetupNdiswrapperHowto) to the T (which is the best i have found so far). 

 I run 
```
make deb
```
and everything seems to work ok untill i get to the end and it says 
```
make -C /usr/src/ndiswrapper-1.1/driver
make[3]: Entering directory '/usr/src/ndiswrapper-1.1/driver'
Can't find the kernel sources in /lib/modules/2.8.6.1-5-386/build said:**
> ; *** [prereq_check] Error 1
make[3]: leaving directory ' /usr/src/ndiswrapper-1.1/driver'
make[2]: *** [build-modules] error 2
make[2]: leaving directory '/usr/src/ndiswrapper-1.1 '
make[1]: *** [binary] Error 2
make[1]; leaving directory '/usr/src/ndiswrapper-1.1 '
make: *** [deb] Error 2
```
since this didn't work, its pointless to try the next step
```
cd /usr/src
dpkg -i --force-overwrite ndiswrapper-utils_1.1-1_i386.deb
dpkg -i --force-overwrite ndiswrapper-modules-$(uname -r)_1.1-1_i386.deb
```

[this site](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#N)  says to use the ndis5x-8180(xxx).zip driver at [ftp://210.51.181.211/cn/wlan/rtl8180l/](ftp://210.51.181.211/cn/wlan/rtl8180l/) (see number 11 under 'N').  i guess i need some help.  i'd like to get this card working.
 no one?  only 3 people looked at this...

---

### Post by zugvogel on 2005-09-22
This is a difficult card. Like you, I spent days trying and failing to get this working (with suse 9.1). I tried again lately with ubuntu, though it quickley came apparent to me that it wasn't going to work.

That howto that you link to though looks interesting. I'm away now until next Tuesday, but I might give it another shot with that howto with the MA521 next week, and see if I get the same error and/or can get any further. The chipset for this card is "Realtek" which I have the impression is fairly unsupported. To be honest I gave up on this card a few weeks ago and bought a netgear WG511T instead, in the hope that I'd be able to get it working. Apparently others got it working, but I haven't had any luck with this one either.

Very frustrating. Sorry I can't be of more help at this stage. If I make any progress with the MA521 I'll let you know.

---

### Post by acejones on 2005-09-22
[QUOTE=zugvogel]This is a difficult card. Like you, I spent days trying and failing to get this working (with suse 9.1). I tried again lately with ubuntu, though it quickley came apparent to me that it wasn't going to work.

That howto that you link to though looks interesting. I'm away now until next Tuesday, but I might give it another shot with that howto with the MA521 next week, and see if I get the same error and/or can get any further. The chipset for this card is "Realtek" which I have the impression is fairly unsupported. To be honest I gave up on this card a few weeks ago and bought a netgear WG511T instead, in the hope that I'd be able to get it working. Apparently others got it working, but I haven't had any luck with this one either.

Very frustrating. Sorry I can't be of more help at this stage. If I make any progress with the MA521 I'll let you know.[/QUOTE]
 thanks.  i've got a linksys card at home that i may swap for this one.

---

### Post by acejones on 2005-09-22
[QUOTE=acejones]thanks.  i've got a linksys card at home that i may swap for this one.[/QUOTE]
 well, i stumbled upon this thread when working with the linksys card:
[http://www.ubuntuforums.org/showthread.php?p=334239](http://www.ubuntuforums.org/showthread.php?p=334239)

i started looking through it and realized i had installed ndiswrapper 1.1 and 1.3rc1, but never 1.2 and when i was working with the netgear card it was looking module 1.2.  so i decided to try 1.2 with the linksys card.  after installing ndiswrapper 1.2 and the net8180.inf driver, i plugged in my wireless card and then typed iwlist wlan0 scan and received information!  woohoo!!!  so i went to the network config gui and setup the wifi connection and then I noticed when i plugged in my wifi card, i accidently plugged in the netgear card instead of the linksys!  so the netgear card works afterall, and the instructions above worked like a charm!

---

