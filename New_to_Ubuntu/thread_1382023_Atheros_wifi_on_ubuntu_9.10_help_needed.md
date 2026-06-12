---
title: "Atheros wifi on ubuntu 9.10 help needed"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by RighteousRob on 2010-01-15
I am trying to get my wireless card in working order but I haven't had any luck yet.  I downloaded a madwifi package for my atheros card but I am unsure how to compile the drivers and load the modules.  Any help with this would be greatly appreciated.  Please be as detailed as possible as I am fairly new to linux.

---

### Post by redbook4574 on 2010-01-15
> **RighteousRob said:**
> I am trying to get my wireless card in working order but I haven't had any luck yet.  I downloaded a madwifi package for my atheros card but I am unsure how to compile the drivers and load the modules.  Any help with this would be greatly appreciated.  Please be as detailed as possible as I am fairly new to linux.

Most atheros cards should work with the native ath5k driver,

---

### Post by bkratz on 2010-01-15
> **RighteousRob said:**
> I am trying to get my wireless card in working order but I haven't had any luck yet.  I downloaded a madwifi package for my atheros card but I am unsure how to compile the drivers and load the modules.  Any help with this would be greatly appreciated.  Please be as detailed as possible as I am fairly new to linux.

You might want to go through this thread, but you will need to know which card you have.

Applications>>Accessories>>Terminal
and type in 

lspci -nn

(that is LSPCI in lowercase)
it should tell you what your card is.


[http://ubuntuforums.org/showthread.php?t=1309072&highlight=atheros](http://ubuntuforums.org/showthread.php?t=1309072&highlight=atheros)

---

### Post by RighteousRob on 2010-01-15
thanks that link looks promising.  I'll give it a shot.

---

### Post by warfacegod on 2010-01-15
I have an Atheros 5211 a/b card in my laptop. It works fine with 9.10. Did you activate the recommended wireless driver in Hardware Drivers?

---

### Post by walt.smith1960 on 2010-01-16
If the above don't help, you might consider using the backports. Here is a post that while not specific to your problem does talk about how to enable backports:
[http://art.ubuntuforums.org/showthread.php?t=1378485&highlight=AR928X+backports](http://art.ubuntuforums.org/showthread.php?t=1378485&highlight=AR928X+backports)

---

### Post by RighteousRob on 2010-01-16
well I got the madwifi drivers installed, I ran the backports command, still nothing.  Am I missing something?  Do I need to run an application to access the internet through my wireless?  Will the light come on once ubuntu recognizes it's there?  I have tried every online tutorial I could get my hands on and nothing has worked.

---

### Post by warfacegod on 2010-01-16
When you installed your OS did your wireless work in the LiveCD environment?

---

### Post by RighteousRob on 2010-01-16
I never tested it on my laptop, I originally ran it on my school computer and it worked fine, so I decided to run it dual boot with my win 7 setup on my laptop.  Give me some details on how to test it in the livecd environment and I'll give it a shot

---

### Post by warfacegod on 2010-01-16
Put the disc in the drive, reboot, tell the computer to boot from disc, select "Try ubuntu without making any changes", try to go online.

---

### Post by RighteousRob on 2010-01-16
nope, it doesn't work.  Would installing it within windows help?  Or does this mean its just not compatible at all

---

### Post by warfacegod on 2010-01-16
> **RighteousRob said:**
> nope, it doesn't work.  Would installing it within windows help?  Or does this mean its just not compatible at all

No. If anything doing a Wubi (Ubuntu inside Windows) install will make it harder and might give you more driver issues like your video driver for example.

Use this command in Terminal:

```
lspci
```

Your chipset will be listed next to Ethernet controller. Use that info and go here to see if your chipset is supported.

[http://linux-wless.passys.nl/]("http://linux-wless.passys.nl/")

If it's there then I suggest going here because I'm out of ideas.

[http://ubuntuforums.org/showthread.php?t=1309072&highlight=wireless+wiki]("http://ubuntuforums.org/showthread.php?t=1309072&highlight=wireless+wiki")

---

### Post by RighteousRob on 2010-01-16
**Vaio Vgn-nr220e**[COLOR=Black]
description: Ethernet controller
product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
vendor: Atheros Communications, Inc.


I didn't see it on the list, I guess it's just not supported, well that really sucks.  Thanks though
[/COLOR]

---

### Post by warfacegod on 2010-01-16
> **RighteousRob said:**
> **Vaio Vgn-nr220e**[COLOR=Black]
description: Ethernet controller
product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
vendor: Atheros Communications, Inc.


I didn't see it on the list, I guess it's just not supported, well that really sucks.  Thanks though
[/COLOR]

You may still wish to read the thread about Atheros chipsets. It may work any way. Glad to help.

---

### Post by RighteousRob on 2010-01-16
Actually I managed to get it working, I am not entirely sure how, I guess I should have been documenting my steps but I'm just relieved it worked.  Thanks for all the help though

---

### Post by warfacegod on 2010-01-16
You have no idea how many times I've been utterly baffled by something just starting to work. Or, even better, doing something I know I shouldn't and having it work anyway. Ghost in the machine is what I say. Enjoy.

P.S. Don't forget to mark this as Solved.

---

### Post by MarkC502 on 2010-01-16
The best support I have found for my Atheros based Wifi device is to compile and install the latest compat-wireless package from [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

You will need to know how to compile things and have some dependencies in place but it was well worth it as I got a newer driver.  

Madwifi is the old way of Atheros drivers the newer Linux kernels can use ath5k and ath9k and you should find that they are superior to older drivers for most devices. So go to the link above and read about the linuxwireless.org's packages as they have install instructions there as well.

Good Luck

---

### Post by Easy Limits on 2010-01-16
I have an Atheros AR5008 in my Toshiba laptop with Ubuntu 9.10 and it works great.  I did have problems getting the wireless to work in earlier versions of Ubuntu though.

---

### Post by RighteousRob on 2010-01-16
thanks again, I'm sure being rather new to linux i'll be back for more help, seeya

---

### Post by tweener on 2010-01-17
righteousBob>>> after you got your wireless to work, does the wireless light come on?  i am have a time getting my to work and still have no luck what so ever..... it hates me.

---

