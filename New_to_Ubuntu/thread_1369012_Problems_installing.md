---
title: "Problems installing"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by Kevinmichael on 2009-12-31
Good morning. I am having trouble installing 9.10. It installed in ''Graphic Safe Mode'' but not in standard install mode. I tried all the boot parameters that I could find listed, no luck. I checked the disk for errors, no problems reported. The third to last line before the monitor goes to a very colorful but useless display is....AC'970 Access is not valid.

Any suggestions????:confused:

---

### Post by baltadt on 2009-12-31
maybe you can give a little more information. where does the problem start? after install or during?

---

### Post by Kevinmichael on 2009-12-31
Hi, thanx for the reply. It will go to the install page, but the only install option that I could get to work was the ''Graphics Safe Mode'' All other modes act like it is trying to install then it goes to a screen filled with bright colored vertical lines.

---

### Post by danastasio on 2009-12-31
so... you DID get it installed?

---

### Post by danastasio on 2009-12-31
Wait is this the LiveCD menu?

---

### Post by Kevinmichael on 2009-12-31
Hi, no it was downloaded from getubuntu on the Ubuntu home page. Yes, it was installed in ''Graphics Safe Mode''. It told me to remove disk and reboot, so it's not a ''live'' disk, is it? It will not let me go on-line or even configure a connection. nor can I add hardware or apply appearance effects. I'm assuming this is because it was installed in safe mode? ??? I am very much a rookie, so I don't know what other info I should add. Thanx

---

### Post by candtalan on 2009-12-31
> **Kevinmichael said:**
> Hi, no it was downloaded from getubuntu on the Ubuntu home page. 
This will be a normal Live CD. It has several ways of working. The live CD function runs after you see the initial menu (where F4 (??) offers a safe graphics mode).

The same menu offers to run the CD without any change to your computer (this is Live CD facility).

The menu also offers to check your CD for defects - very useful.....

The menu also offers to install directly. (maybe you should choose safe graphics mode first though).
My guess is that you did this install after selecting F4 safe graphics mode in the CD boot menu???

The Safe Graphics mode is not the same as Windows Safe Mode which is very restrictive. Ubuntu Safe Graphics still gives you a complete full system and it should work pretty well completely. However, its graphics drivers will be traditional and not the latest cutting edge stuff, but you should get good graphics still.
> 
Yes, it was installed in ''Graphics Safe Mode''. It told me to remove disk and reboot, so it's not a ''live'' disk, is it? 
True. Once you have installed onto hard disc, no, it is not a live cd system any more, it is installed.

> 
It will not let me go on-line or even configure a connection. nor can I add hardware 

Even a live CD will let you go online no problems usually, and you can add most hardware in live CD running too, such as printers, even install programs. You sure should be able to do this after an install too. You may need you password of course, after install.

> 
or apply appearance effects.


the fancy graphics will most likely need the latest graphics drivers for your chips and safe graphics may not be good for that. There may be some solutions, however they may need some work.

hth

---

### Post by Kevinmichael on 2009-12-31
The ONLY way it would install is in ''Safe Graphics Mode'' No other option worked. I used ''check disk'' utility, no errors reported. EVERY other install option failed or would produce various displays of colored lines. I tried EVERY boot parameter listed on the Ubuntu web site (total of 63). To no avail.

---

### Post by Kevinmichael on 2009-12-31
OK, I can live with ''Safe Graphics Mode'' if I can get on-line. I know my connection is good, cuz I'm using it on my laptop. But I can't get it to work on the desk top (Ubuntu). What the heck is a _M_ac? Is there some trick that I'm missing to configure the machine to connect to DSL?  By the way.....thank you for your help thus far.

---

### Post by danastasio on 2009-12-31
What are the specs of your computer? Is this a netbook? Perhaps its a proper burn of a bad .ISO? I dont know, im not really savvy with installs.

---

### Post by Kevinmichael on 2009-12-31
No, It's a Dell Pentium 4, dual processors, WD 1600 hard drive. I was wondering about a invalid ISO also, but, wouldn't that show up on ''check disk''? On the Ubuntu page it told me how to check if the disk was burnt properly. It shows that it was.

---

### Post by derekmbarnes on 2009-12-31
Addressing the installation problems: one thing I noticed with my installer disk (aka "Live CD") is that it would only install if I had shut down my laptop and then started it again; if I restarted the computer, the disk couldn't get past the main menu. Might this be your problem?

-----

Addressing connection issues: a good start would be seeing if you have any connections to begin with. Go to System > Preferences > Network Connections and see what you can find; at the very least the "Wired" tab should have something in it for your main controller (labeled "auto eth0" or similar). Whatever connection you're using, if it's not listed then you're probably missing a driver; Windows comes with these drivers pre-installed, but you have to find one for Linux.

Open Applications> Accessories > Terminal and type the following code:

```
lspci -v | less
```

This will list every PCI-based hardware device in your system. Scroll down in the list; your Internet machinery should be near the bottom ("ethernet controller" for a direct connection and "network controller" for wireless). Note the specs of the devices, specifically the primary line that lists the manufacturer and model number. Drivers are listed below "Capabilities;" if you don't see anything there, you need a compatible Linux-native driver for the card (in my case, a Realtek 8172 card worked with an rtl8192se driver). 

This page may be of use: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Best of luck.

---

### Post by Kevinmichael on 2009-12-31
Thank you very much. I'll try that when I get off work. Happy New Year!

---

### Post by kraus3742 on 2009-12-31
Do you have a integrated video card (i.e. Video card on the motherboard) and a PCI/AGP Video card?

---

### Post by Kevinmichael on 2009-12-31
PCI/AGP Video card.

---

