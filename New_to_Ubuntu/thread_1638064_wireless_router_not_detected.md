---
title: "wireless router not detected"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by big_fact_hunt on 2010-12-05
i'm an it pro, mostly ibm host, although have worked on multi platform systems, which included unix/dec systems, between the host and pc based systems, but the last time I used it in anger was 11 years ago.
my linux/unix skills are pretty rusty, and i'm hoping to find a couple of people who would perhaps mentor me whilst i find my feet. Indeed, I am on a big fact hunt!

i've just installed ubuntu on an acer aspire 9304wsmi laptop and immediately hit my first problem. the network is being recognised, but is disabled. It works OK in Windows, and I have temporarily disabled security on my router.

Do you need me to past any logs?

bfh

---

### Post by dacanadianbomb on 2010-12-05
Hi,

I am a newbie to Linux myself but I have one question : 
Your post is called "Wireless router not detected" and you say that "the network" is being recognised but is disabled. ¨
Do you mean your local wireless network card on the laptop is recognised but disabled, or that the router you are attempting to connect to is visible but you cannot connect  ?

I have had issues connecting to a wireless router that had broadcasting its SSID disabled in the past.Though this may be unrelated to your problem.

---

### Post by big_fact_hunt on 2010-12-06
Well, the network icon is telling me "device not ready. (firmware missing).

iwconfig is telling me :-

lo       no wireless extensions
eth0     no wireless extensions 

and using lshw .c network, it recognises my Broadcom BCM4311 802.11b/g WLAN device, but i get

*-network DISABLED

My routers  SSID is visible, and I tried it with a buddy's laptop and a fresh ubuntu installation, and his connected immediately.
NB. Mine is an Acer Aspire 9304WSMi

Also, people mention the System>Administration>Networking and Restricted Drivers Manager options, which are not there.

---

### Post by The Real Dave on 2010-12-06
Can you see the network using Network Manager? (The panel icon in the top right hand side). If not then perhaps there is a driver issue with your specific wireless card.

I presume you're using Ubuntu 10.10, the standard install?

---

### Post by Hippytaff on 2010-12-06
It is probably a driver thing 'no firmware detected'
 
Are you using a usb dongle?
the outputs of
```

lsusb

```
or
```

lspci

```
will provide the chipset so you can find out whether the driver needs to be installed
```

lsmod | grep [COLOR=red]drivername[/COLOR]

```
will return a result if the driver is loaded, or nothing if not.
 
My guess is that if it's not usb wireless dongle then your device is ralink or broadcom :-)
 
Edit -> welcome by the way - like your nick

---

### Post by nothingspecial on 2010-12-06
You need to install one of these

firmware-b43-installer or firmware-b43-lpphy-installer

get a wired connection and search for them in system - administation > synaptic package manager.

You will need to restart.

The drivers thing is now at system > administration > additional drivers


(I hate it when they change stuff like that)

---

### Post by big_fact_hunt on 2010-12-06
cracked it via [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

was a bit temperamental, but was ultimately able to go through

---

