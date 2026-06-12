---
title: "modprobe ndiswrapper: FATAL Error"
date: 2005-11-15
forum: Networking &amp; Wireless
---

### Post by tomlondon on 2005-11-15
Hi folks. All advice would be appreciated!

**Short description of problem:**

**ndiswrapper -l** gives "driver present, hardware present" but **modprobe ndiswrapper** gives a "FATAL Error: Operation not permitted" error and **iwconfig** gives "no wireless extensions"


**Long description of problem:**

I'm using a Cardbus card identified by Windows as an Am1772. I'm using the same driver that I'm currently using in Windows. I don't have any other means of connecting to the internet, other than downloading files on my PC and transferring them accross on a USB drive. Ubuntu didn't pick up the card on install.

Following the instructions on the [wiki]("https://wiki.ubuntu.com/SetupNdiswrapperHowto") I downloaded ndiswrapper 1.5 and compiled it from source. Only one package appeared in /usr/src/ : ndiswrapper-utils. I installed -utils, assuming that ndiswrapper was already installed.

**ndiswrapper -i ~/windows_drivers/oem11.inf** worked fine
**ndiswrapper -m** worked fine

When I run **modprobe ndiswrapper** I get the following message:

```

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

```

**ndiswrapper -l** gives me:
```

Installed ndis drivers:
oem11     driver present, hardware present

```

I've also added ndiswrapper to the end of /etc/modules and rebooted. No difference.

**iwconfig** doesn't show any wireless extensions, just:
```

lo     no wireless extensions
sit0   no wireless extensions

```

If I open System > Administration > Networking, no networks show up under "Connections"; only a modem.

Where did I go wrong? All help would be appreciated. Thanks.

---

### Post by Lambert on 2005-11-15
try

```
sudo modprobe ndiswrapper
```

When ever you get that permission denied try adding sudo to the front of the command.

---

### Post by tomlondon on 2005-11-15
Sorry, should have mentioned that I was running all of that as root. Have just tried again and same message.

---

### Post by Lambert on 2005-11-15
What do you get when you run

```
lsmod | grep ndis
``` 
What's the model/manufacture of the device?

Also post the output of the following here.

```
lspci -v
and 
lsusb -v
```

---

### Post by tomlondon on 2005-11-15
Lambert, thanks for your help so far.

The results of lsmod contain no reference to "ndis" - I have attached the full output.

Results of **lspci -v** and **lsusb -v** are also attached.

The card is a cheapo 802.11b PCMCIA (cardbus?) card, manufactured by "Origo". I think it may use the the RTL8180 chipset but can't confirm that. Realtek apparently have a set of Linux drivers for the 8180 [here]("http://www.realtek.com.tw/downloads/downloads1-3.aspx?keyword=8180") but since their Windows driver didn't work with the card, I thought it best to stick to a driver which I know works (in Windows)

Thanks again

---

### Post by Lambert on 2005-11-15
1. Did you try the version that's in the repositories/on the cd first before compiling? If so did you uninstall first before compiling?
2. Look in /lib/modules/2.6.12-9-386/misc and see if there is a ndiswrapper.ko file there (or even a misc directory with anything ndiswrapper in it)

You can go to google and type [COLOR=DarkRed]ndiswrapper.ko ubuntu[/COLOR] as keywords and search through as I see there are a few posts out there with this same problem. Maybe you'll find your answer in one of those.

One other thing if you could attach to a post. that is the output of 

lshw -C network (add sudo if not logged in as root)

---

### Post by taurus on 2005-11-16
Or try to remove it and re-install it again,

sudo apt-get remove ndiswrapper-utils
sudo apt-get update
sudo apt-get install ndiswrapper-utils

---

