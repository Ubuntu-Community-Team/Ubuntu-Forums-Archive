---
title: "New to Linux, go easy on me! (Wireless adapter)"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by RobbieStew on 2010-02-11
Hello!

I am currently a system administrator, (in a windows environment) and I am really trying to get my knowledge of Linux rolling.

I recently installed the latest version of Ubuntu and I am trying to get my wireless working.

I was impressed that when I plugged in my network adapter (Network Anywhere - NWU11B) and it picked it up and let me view the networks in the area, although it wont let me connect.

It just constantly keeps asking me for the password after trying to connect for 1-2 minutes.

I know the password is correct, and I am assuming I am having the problem due to the fact I do not have a driver installed for this device.

Now, when I say I am new, I really am. Hah.  I have some experience in Unix and working at the command line in Linux, but drivers, installing them etc is totally foreign to me, so take it easy on me.

What are the steps I need to take to get this working?

Any help is much appreciated.

Thanks for your time!

---

### Post by 3rdalbum on 2010-02-11
> **RobbieStew said:**
> Hello!

I am currently a system administrator, (in a windows environment) and I am really trying to get my knowledge of Linux rolling.

I recently installed the latest version of Ubuntu and I am trying to get my wireless working.

I was impressed that when I plugged in my network adapter (Network Anywhere - NUP11B) and it picked it up and let me view the networks in the area, although it wont let me connect.

It just constantly keeps asking me for the password after trying to connect for 1-2 minutes.

I know the password is correct, and I am assuming I am having the problem due to the fact I do not have a driver installed for this device.

If you didn't have a driver for the device, it would not be able to be used to detect wireless networks. Linux contains a large number of drivers for various devices that will be activated if needed.

It's possible that the wrong driver is being used - one that's designed for a slightly different card. Your best shot would be to find out the chipset of your device, which may be quite easy, and then search Google for any workarounds. Open a terminal and copy and paste one of the following commands in:

For a PCI device
```
lspci
```

For a USB device:

```
lsusb
```

If you don't know, try both. One of the entries will show your wireless card, and probably give a model number for the actual chipset*. If you don't get a chipset model number, you can try this command:

```
lshw -C network
```

Search Google for "<chipset model number> ubuntu 9.10" or "<chipset model number> ubuntu karmic".

Hopefully there will be a workaround involving "blacklisting" the incorrect driver, so that the correct driver can be loaded. If there isn't, you might need to compile a driver, but we can cross that bridge if we come to it. Feel free to PM me if this is what Google's search results suggest.

*My 'lsusb' output includes the line:

```
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
```

RTL8187 is the chipset number for my wifi adapter; so if I was having your problem with my wifi, I'd go to Google and type in "rtl8187 ubuntu 9.10".

---

### Post by RobbieStew on 2010-02-11
Thank you sir! I will try this shortly!

---

### Post by RobbieStew on 2010-02-11
The result I got was:  Bus 003 device 003 077b:2227 linksys

I know this USB adapter is a rebranded linksys adapter.  Now, I have drivers on a thumb drive that I use on windows machines, it has XP drivers and a generic driver.

Now in the documentation I see ndisgtk package that says it will allow me to use windows drivers.

When I click on the link to install it, it comes up saying it can't be found.  If I can find this package, would this allow me to use the windows driver?

---

### Post by RobbieStew on 2010-02-11
I have tried getting it from the package manager, but I am assuming I need an internet connection to download this package, so that is no dice either.  Is there a place I can manually install this package?

---

### Post by philinux on 2010-02-11
> **RobbieStew said:**
> I have tried getting it from the package manager, but I am assuming I need an internet connection to download this package, so that is no dice either.  Is there a place I can manually install this package?

If this is a brand new install I would do this.

Connect wired to the router. Then do this. Open a terminal.

```
sudo apt-get update && sudo apt-get upgrade
```

Then try sorting wireless out.

---

### Post by RobbieStew on 2010-02-11
haha, crap its on the other end of the house, I would have to take apart everything.  Only option I have?

---

### Post by philinux on 2010-02-11
> **RobbieStew said:**
> haha, crap its on the other end of the house, I would have to take apart everything.  Only option I have?

Ah me thinks it was a laptop.

My experience with GF's lappy was to connect wired and do the updates. Also with it connected wired you can download what you might need directly and ask any further questions here. Then disconnect wired and with the machine next to the router sort out any problems.

---

### Post by RobbieStew on 2010-02-11
Ok, ill make the move later on today, and give it a go then heh.

---

