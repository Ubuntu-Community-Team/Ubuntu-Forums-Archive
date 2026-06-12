---
title: "New to Ubuntu - Wireless help"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by dean881 on 2009-06-03
Finally fed up with Microsoft.  Just installed Ubuntu & want to know how to get my wireless pci  card to work.  It's a linksys WMP54G.  Thanks for any help.:p

---

### Post by keplerspeed on 2009-06-03
EDIT: see utnubuuser's link, you can either use ndiswrapper as I have started to explain or CVS the driver. 

You can get it working via ndiswrapper. We can pretty much follow this [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

To start you off, go to system>admin>synaptic. Search for ndiswrapper and install 'ndisgtk' this will also install everything else you need.

Next open a terminal from applications>accessories and enter this:
```

lspci

```

Find the line that the terminal output about your wireless card to find the version. Then go to here [http://www.linksysbycisco.com/US/en/support/WMP54G/download](http://www.linksysbycisco.com/US/en/support/WMP54G/download) and download the correct windows version driver.

After downloading you will need to install cabextract with synaptic, and use that tool to extract the driver. This is done by:
```

cabextract drivename.exe

```

Next you need to blacklist some default drivers, see this section of the ubuntu wiki "3.1. Disable Free Drivers"

Then in system>admin>win wireless drivers, find the .inf file extracted earlier with cabextract and wireless should be working.

---

### Post by utnubuuser on 2009-06-03
try:
[http://ubuntuforums.org/showthread.php?t=588045]("http://ubuntuforums.org/showthread.php?t=588045")
and
[http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=4970]("http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=4970")

---

### Post by 1BigBore on 2009-06-03
Wow... I feel soooo blessed, my Linksys atapter (WUSB54G) worked out of the box.  I have no Idea why, but it did. Would the USB aspect make it easier?  
(no help, just a thought)

---

### Post by eMJayy on 2009-06-03
> **dean881 said:**
> Finally fed up with Microsoft.  Just installed Ubuntu & want to know how to get my wireless pci  card to work.  It's a linksys WMP54G.  Thanks for any help.:p

That card is supposed to work out of the box. 

I know because I have one and I was using it up to a few months ago when I was still using Ubuntu 8.10.
The card's Windows driver was causing BSODs in XP so I took it out of the machine (I'll dual-boot Ubuntu and Windows), but the card itself worked perfectly in Ubuntu. The only thing I needed to do to use it was to have it detect my network and provide the passkey. You are supposed to be able to manage it by going to System > Preferences > Network Tools and clicking on the Wireless tab. 

If you don't get it sorted out soon, I'll reinstall my card to see how it's set up. I also want to test it to see if it works in Windows 7, which I am currently testing.

---

### Post by blueearthmn on 2009-06-04
I find plenty of help for the WMP54G  but anybody have any input into making the WMP54GS with Speed Booster work?

---

### Post by blueearthmn on 2009-06-04
how does one tell ubuntu 9.04 to search for available networks?  and how do you verify if ubuntu is indeed seeing your wireless card and if it is working properly with it?

---

### Post by keplerspeed on 2009-06-04
Easiest way to see if you have wireless: right click on the network icon in notification area, and see if wireless in enabled! There should be a ticked box saying 'enable wireless'

---

### Post by dean881 on 2009-06-04
Wow, I feel like I went to sleep & woke up in a different country.  Having a few language barrier problems.  I'll get working on it tonight & I'll get back if I have other questions.

---

