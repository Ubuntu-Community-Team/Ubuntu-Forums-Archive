---
title: "Linksys Network adapter help"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by mcclunyboy on 2009-11-06
Hi,

I have a linksys wireless - g - model number wmp54gs and need help.

I expected ubuntu to pick it up and connect straight away but without success...

How do i check if it is connected????  like ls usb but for PCI ports?

---

### Post by Lateralis on 2009-11-06
If it is a wireless card connected to your PC, type

```
lspci
```.

If it is connected and recognised by Ubuntu, it should be listed.

---

### Post by mcclunyboy on 2009-11-06
thanks...its not listed so it is not getting picked up :(

anyone any ideas what a noob like me has to do to get it to work?

---

### Post by Garyhans on 2009-11-06
You have to take the router out of the picture.. connect firstly that way...  then put the router back in..  then..  create the new communication..  with 192.168.1.1 admin.. name.. password none..  and set is for no bridge mode.. dchp.

---

### Post by mcclunyboy on 2009-11-06
is router/wireless card same thing?

how do i do those things though

---

### Post by Miljet on 2009-11-06
This thread is about a network adapter - not a router.

Sorry mcclunyboy, wish I could help, but is out of my league.

---

### Post by Garyhans on 2009-11-06
Your router has lost communication with..  the Modem.. hardwire your.. wireless lappy..  and type.. in the address..  192.168.1.1 in your..  browser..  and tell it to start talking again.
By my earlier comments.

---

### Post by mcclunyboy on 2009-11-06
no the connection to the router is not the problem

the ubuntu is not picking up my hardware..it doesn't know there is a wireless card installed?

---

### Post by walt.smith1960 on 2009-11-06
I'm not sure how old this is or whether it's still good info but if lspci doesn't list it, it seem like you may have to resort to NDISwrapper. Here is a link:
[https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WMP54GX](https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WMP54GX)
The link refe5rences WMP54G**X** but I'd expect the procedure to be the same for WMP54G**S**. I'm surprised this card is not recognized; I was using a Linksys  WUSB54G WiFi adapter for a period of time and it was recognized natively.  Good luck with your endeavor.

---

### Post by mcclunyboy on 2009-11-08
hi,

tried ndiswrapper

It seems to think the newer driver is installed (which is fine) but the older one won't install. i am not sure hwo to check whether or not my adapter is v1 or v1.1 but it still wouldn't find it.

When i do lspci it lists a netwrok adapter but its a broadcom one, would it list an "unidentified" connection if it couldnt find it?

---

### Post by The Funkbomb on 2009-11-08
That linksys card uses the broadcom chipset.  BCM4306 if my googling is correct.

Just like how my video card is an EVGA but it uses the Nvidia chipset.

My suggestion is to go into System>Administration>Hardware drivers

You might find the right driver in there but because it's a proprietary driver, Canonical cannot install it automatically.

---

### Post by bkratz on 2009-11-08
From what I see in the following thread

[http://ubuntuforums.org/showthread.php?t=1278694&highlight=wmp54gs](http://ubuntuforums.org/showthread.php?t=1278694&highlight=wmp54gs)

It seems that your card should be recognized out of the box.  Is there some key combination you have to disable wireless or could it be disabled in the bios itself?  It concerns me that you do not even see the card. I think you should post the lspci output so we can all see it, actually you probably should also post    lshw -C network.      

 note capital "C"

---

