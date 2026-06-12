---
title: "PCMCIA wireless card problem - Buffalo WLI-CB-G54 / Dell trumobile 1150 mini-PCI card"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by plusman on 2008-09-03
I've just installed the latest verion of Ubuntu (Hardy Heron, 8.04) on a Dell Latitude C400 laptop and am having problems configuring it to link with my wireless network.

There are 2 specific problems:

**_PROBLEM 1: Dell TrueMobile 1150 mini-PCI card_**

The laptop has an in-built Dell trueMobile 1150 mini-PCI card which is only IEEE 802.11b rated and so far I have been unable to get it working with my WPA-encrypted network. It sees the network, but since it will only allow no- or WEP-encryption, it cannot successfully link to the network. I have tried upgrading the driver details as indicated in a thread on this forum

[http://ubuntuforums.org/showthread.php?t=304217&page=11](http://ubuntuforums.org/showthread.php?t=304217&page=11)

using the information given in response #107 but I am stuck partway through at the point where it suggests:

[I]"You need to make a couple of edits to avoid compilation errors. You will need to master a Linux editor to do this, but gedit is pretty simple if you don’t want to get into the mysteries of ‘vi’.

Move into the subdirectory where the driver source lives, then firstly edit the Makefile and secondly one of the source files.


Code:
cd wlags49-h1-cs
gedit Makefile
gedit wl_cs.c

In Makefile, on line 2 change CFLAGS to EXTRA_CFLAGS. "
[/I]

When I "gedit makefile" I get a blank "document" and don't know how to proceed. So I'm not sure what to do next.

(I also appear to be blocked from adding to the above thread as is it is old, and so cannot ask for help there (hence this new thread)).

Can anybody help with what I should do?


**_PROBLEM 2: Buffalo WLI-CB-G54 PCMCIA card_**

Because of the above problem, and also because the inbuilt card is slow ("b" rated), I want to use a IEEE 802.11g rated PCMCIA card, a Buffalo WLI-CB-G54.

This does not have a linux/Ubuntu driver, but I have downloaded the existing XP driver and tried to install it using NDISwrapper. The driver seems to have installed successfully and when I insert the PCMCIA card it seems to recognise that it is there (Under System - Administration - Wireless Network Drivers it shows that "netcbg54 is installed and that hardware is present", but there is no power or communication light coming on on the card. 

When I go to Terminal and enter "iwconfig", it only seems to see the internal Dell card:

"IEEE 802.11b ESSID:"" Nickname "Hermes I"
etc etc

Also, when in the Wireless Network Drivers box, I try and configure the network, the "Unlock" button is greyed out and it will not allow me to make any changes to the configuration.

(The WLI-CB-54G card is working OK when I try it in another C400 laptop which is running XP. So the card itself is OK. The PCMCIA slot on the laptop also appears OK as when I plug in a USB2.0 PCMCIA card it works fine).

Can anybody suggest a route to get the PCMCIA card working?

Many thanks

---

### Post by plusman on 2008-09-04
Can anybody help?

---

### Post by plusman on 2008-09-06
Still no response. Can anybody please help?

---

### Post by plusman on 2008-11-06
I am still having this problem. If anybody can help, then it would be appreciated. Thanks

---

### Post by setag on 2008-11-07
> **plusman said:**
> 
When I "gedit makefile" I get a blank "document" and don't know how to proceed. So I'm not sure what to do next.

If you start an editor with the name of a file, that does not exist, it simply creates a  blank document. The file you are supposed to edit is called "Makefile", not "makefile".

[[COLOR="Blue"]_This thread_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=940944") may also be of interest for you.

---

### Post by plusman on 2008-11-07
setag:

Thanks for the response. Apologies for my typo (I dodn't realise until recently that Ubuntu commands were case sensitive). I have been typing gedit Makefile and it still opens with a blank document, and I can't seem to get past this point.

I still have had no luck with either the Dell 1150 or the Buffalo PCMCIA card.

I've had a look at the other thread - but to be honest (as I'm new to Linux) I really don't understand what the thread is talking about nor how it might help me. (For example I have no idea what Hermes I or II or Arch Linux are, and whether or not this is relevant to me). :confused:

Any help appreciated.

---

### Post by setag on 2008-11-07
And there is no error message when you extract the archive
```
tar -xjvf wlags49-h1-cs.tar.bz2
```
and try to change to the directory that was created
```
cd wlags49-h1-cs
```
before running gedit?

Concerning the other thread:
The old code didn't compile here on kernel 2.6.27 (*uname -r* gives you the version you have), the new code did.
Hermes I and II are WLAN chipsets. If
```
pccardctl ident
```
reports
```
 manfid: 0x0156, 0x0002
```
you have a Hermes I card.
Arch Linux is, like Ubuntu, a Linux distribution.

---

