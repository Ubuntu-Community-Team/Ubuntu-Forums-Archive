---
title: "How to make Ubuntu Stop trying to connect to a wifi network?"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by kramer65 on 2010-11-18
Hello,


I've got one build-in wireless card in my pc, and one USB-wireless thingy. Since the build-in wireless card was always unable to connect to my (or any) wifi network I plugged in the USB-dongle which works like a charm. 

The annyoing thing is however, that the build-in wireless card continues to search for the wifi network which it can't connect to. This results in constantly repeating error messages that it couldn't connect to the network and that I need to re-insert the WPA-key.. #-o

How can I make ubuntu _stop_ trying to connect to the wifi network with the build-in wireless card?

Any tips are welcome!

---

### Post by gary0 on 2010-11-18
If it's a laptop, there will be a switch somewhere, probably along the front that will physically turn the internal wireless card off. Or it might be a fn-F* combination to do the same.

---

### Post by Hippytaff on 2010-11-18
You need to find out the name of the wlan
```

iwconfig

```
then once you know which ine you want to disable do
```

wlan0 down

```
where wlan0 is the correct wireless device you want to switch off :-)
 
If this doesn't work, I've got the syntax or something wrong, but can't check it right now (not at home) so when I get home I'll double check, but it should work :-)

---

### Post by fallenshadow on 2010-11-18
Something like this happened to me recently. :)

Try this:

1. Right click on your network manager icon.

2. Click on Edit Connections.

3. Click on the Wireless tab.

4. Delete any wireless network entries.

Hope that helps! ;)

---

### Post by HDave on 2010-11-18
Super Easy:

Click right on the network manager icon in your top panel (upper right) and uncheck the box "Enable Wireless".

Done.

---

### Post by Hippytaff on 2010-11-18
> **HDave said:**
> Super Easy:
 
Click right on the network manager icon in your top panel (upper right) and uncheck the box "Enable Wireless".
 
Done.
 
Won't that disable all wirelss devices?

---

### Post by Hippytaff on 2010-11-18
Is this a duplicate thread? :-)

---

### Post by HDave on 2010-11-18
> **Hippytaff said:**
> Won't that disable all wirelss devices?

Yes it will!  I guess it pays to read more slowly...sorry!  :oops:

---

