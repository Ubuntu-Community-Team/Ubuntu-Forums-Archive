---
title: "Switching from Eternet to Wireless"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by daoud7 on 2008-07-04
I have a perfectly good ethernet running on Gutsy Gibbon.

Now I have terminated the ethernet connection and am in the process of trying for a Wireless connection.

It might be worth mentioning that using a Live Ubuntu or other Live Linux CD, there is no problem in obtaining the wireless connection.

But I have tried several options with network manager and nothing seems to work.

The usual suggestion is something like: Click on Network Manager >Manual Configuration> Select Wireless ...

But there are only: Wired Connection and Point to Point Connection.

How do I simply kill the ethernet part and install just the wireless option?

---

### Post by wdaniels on 2008-07-04
Sounds like your wireless driver isn't loaded - if there were any wireless interfaces you would see the relevant options. Just to check, run:

```
iwconfig
```

And see if it shows any interfaces with wireless extensions.

If this is a laptop, make sure that the wireless card is actually switched on. Otherwise, do you already know the make/model of the wireless card?

It' strange that it works fine on the live CD though...

---

### Post by tjwallace on 2008-07-04
I don't want to insult your intelligence but maybe the wireless card is turned off, either by a hardware switch or by a key combination (Fn + F2 maybe)?

---

### Post by daoud7 on 2008-07-05
re. iwconfig

No wireless interface shown :-(

Yes, Edimax IEEE 802.11g USB 2.0

---

### Post by daoud7 on 2008-07-05
AFAIK there is no way to turn the card off/on. Except by unplugging it from the USB port!

Maybe dropping it inside a tin box, or a bucket of water?  :-P

This is not a laptop.

---

### Post by wdaniels on 2008-07-05
> **daoud7 said:**
> re. iwconfig

No wireless interface shown :-(

Yes, but I don't have the info here.

Then you will have to post the output from this command so that we can identify it:

```
lshw
```

> **daoud7 said:**
> AFAIK there is no way to turn the card off/on. Except by unplugging it from the USB port!

Maybe dropping it inside a tin box, or a bucket of water?  :-P

This is not a laptop.

Usually for external adapters you can't switch them on/off.

---

### Post by kevdog on 2008-07-05
Is your wireless device usb or pci?

If you don't know, please post

lshw -C network
lsusb -v

---

### Post by wdaniels on 2008-07-05
> **kevdog said:**
> Is your wireless device usb or pci?

If you don't know, please post

lshw -C network
lsusb -v

Yes, my bad :D  It's lsusb you want since you already said it is a USB adapter!

---

### Post by daoud7 on 2008-07-05
I think you may have enough info now to identify the device.

I have the feeling that the whole thing hinges around having originally setup the machine as a wired ethernet. 

Some vital bit is therefore missing - which would account for the easy wireless availability from Live disks.

However, I tried everything I could think of.

I am very hesitant to do a new install since I have one of those Large HDD vs. old BIOS workarounds to contend with (set up ages ago!)

---

### Post by wdaniels on 2008-07-05
> **daoud7 said:**
> I think you may have enough info now to identify the device.

Did I miss something? You haven't provided the info from lsusb yet have you? There are hundreds of different USB wireless adapters.

> **daoud7 said:**
> I have the feeling that the whole thing hinges around having originally setup the machine as a wired ethernet. 

Some vital bit is therefore missing - which would account for the easy wireless availability from Live disks.

No, this is not the problem, it makes no difference. You will only see the wireless options in NetworkManager (and nm-applet, which is the icon in the top right) if there are interfaces with wireless extensions present. All the necessary configuration tools and standard drivers for wireless are installed regardless and you already used one of them in a previous post (iwconfig).

The thing that seems to be missing is the specific driver, but as soon is the card can be identified, the necessary driver can be identified, the package containing the driver can then be identified, then installed...you see we need to know what card you are using as the first step.

---

### Post by daoud7 on 2008-07-06
Perhaps I shouldn't have edited a previous post to insert the information.

The identity of the card is as given above.

lsusb gives:

ubuntu@ubuntu:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. 
Bus 001 Device 001: ID 0000:0000  

But that is only immediately available using a live CD (in order to access the internet). And since the live CD works anyhow....

Also, as I indicated in my first post, the nm applet shows no wireless option.

---

### Post by wdaniels on 2008-07-06
> **daoud7 said:**
> Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. 

But that is only immediately available using a live CD (in order to access the internet). And since the live CD works anyhow....

This is a known issue (including the fact that it often works fine on the live CD), see [LP #139070]("http://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/139070") for details. Actually I came across the same issue myself when upgrading to Gutsy since I have the same wireless card in one of my desktop machines.

If you are lucky, your problem will be only that two different drivers are getting loaded for the same device (rt2500usb and rt73usb) in which case refer to [this specific comment]("http://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/139070/comments/3") in the bug thread about removing rt2500usb.

Otherwise, you may have to build and install manually the "serialmonkey" drivers and the RUtil wireless manager, which is what I did since I didn't notice that bug when I looked at the time.

Since the latter is much more complicated and time-consuming if you're unfamiliar with these things, I would suggest you first try just removing the rt2500usb module as directed in the referenced bug comment (there is a cleaner way using the module blacklist file, but it's probably best to go with what's been said to work already)...

---

### Post by kevdog on 2008-07-06
Ok that helps a lot.  An ra chipset that works with the live CD.  That would mean it was using a built-in linux driver.  Lets see if the ra link module/driver is being loaded?

Can you post the following:

lsmod | grep rt

---

### Post by daoud7 on 2008-07-11
> **kevdog said:**
> Ok that helps a lot.  An ra chipset that works with the live CD.  That would mean it was using a built-in linux driver.  Lets see if the ra link module/driver is being loaded?

Can you post the following:

lsmod | grep rt
Sorry for delay - one of the consequences of having to use internet cafes!  :-(

This is from Live disk

ubuntu@ubuntu:~$ lsmod | grep rt
rt2500usb              24320  0
gameport               16008  1 snd_ens1371
parport_pc             36260  1
parport                37832  3 ppdev,lp,parport_pc
rt73usb                27136  0
rt2x00usb              12800  2 rt2500usb,rt73usb
rt2x00lib              22528  3 rt2500usb,rt73usb,rt2x00usb
rfkill                  8592  1 rt2x00lib
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
mac80211              165652  2 rt2x00usb,rt2x00lib
agpgart                34760  1 intel_agp
iTCO_vendor_support     4868  1 iTCO_wdt
usbcore               146028  5 rt2500usb,rt73usb,rt2x00usb,uhci_hcd

---

### Post by daoud7 on 2008-07-12
> **kevdog said:**
> Ok that helps a lot.  An ra chipset that works with the live CD.  That would mean it was using a built-in linux driver.  Lets see if the ra link module/driver is being loaded?

Can you post the following:

lsmod | grep rt
FWIW the output without a live disk

lsmod | grep rt
gameport	13832  1  snd-ens1371
parpoirt_pc	31524  1
parport		32200  3  ppdev,lp,parport_pc
rtc		11572  0
agpgart		29360  1  intel_agp

lsusb gives the same as live disk

---

