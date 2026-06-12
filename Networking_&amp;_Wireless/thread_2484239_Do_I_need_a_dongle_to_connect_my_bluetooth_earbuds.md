---
title: "Do I need a dongle to connect my bluetooth earbuds to wifi??"
date: 2023-02-20
forum: Networking &amp; Wireless
---

### Post by david503 on 2023-02-20
I have bluetooth earbuds.   The article I read says I need a dongle to connect them to my ubuntu pc.  Is that really true?  I mean the pc already has built in wifi.  I really need more hardware for bluetooth than just wifi??

This just hangs:

$ sudo bluetoothctl scan on
Waiting to connect to bluetoothd...

And this: 

sudo blueman-manager

gives a popup "Bluez daemon is not running, blueman-managager cannot continue. This probably means no Bluetooth adapters detected...." etc etc.

They  connect to my phone just fine.

I thought this would be easy!

---

### Post by Hakunka-Matata on 2023-02-21
Yes, you do need more than wifi hardware to use bluetooth.  Go to your computer settings and see if settings has a bluetooth section.

---

### Post by david503 on 2023-02-21
> **Hakunka-Matata said:**
> Yes, you do need more than wifi hardware to use bluetooth.  Go to your computer settings and see if settings has a bluetooth section.

Nah damnit you're correct. "No bluetooth found. Plug in a dongle to use bluetooth." 

Christ- I really thought the two would be easily compatible.  What idiots invented this and made it incompatible with wifi?

Painful thanks, [COLOR=#000000]Hakunka-Matata,[/COLOR]

Sigh,

d

---

### Post by TheFu on 2023-02-21
Bluetooth is a completely different protocol than wifi.  Sure, they both use unlicensed 2.4Ghz bands, but that's about the end of the similarities. BT is meant for low power, limited range - though people have connected from over 2 miles away over bluetooth.

Both are not exactly secure, so be very careful using either, but bluetooth has been proven to be about 10x less secure than wifi, which is saying much.  In the last 20 yrs, I've been hacked once.  They use bluetooth to break in.  Be very careful.

I disable both wifi and bluetooth in my laptop BIOS. No need to risk the security problems. If I do need 1, it is worth the hassle of having to reboot, change the bios, and enable whichever I need to be certain it isn't enabled by accident.

---

### Post by david503 on 2023-02-21
Oh that's very good information in my case- I live in Manhattan.  I'm swimming in wifi here.  I didn't know bluetooth was so naked.

But as for wifi- WPA-PSK isn't good enough?

m

---

### Post by chili555 on 2023-02-21
> But as for wifi- WPA-PSK isn't good enough?It surely isn't. I recommend WPA2-PSK and also WPA2-AES (sometimes called CCMP) is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. If you have access to the newer WPA3 devices, use that.

I recommend, especially in Manhattan, the best security that's available. Two padlocks are better than one and three padlocks and a mean dog are even better!

---

### Post by TheFu on 2023-02-21
Manhattan? Had lots of friends go to school there. I couldn't take Kansas for long periods.

The best wireless security is to treat it like it is open internet and use a good VPN whenever using it. I do, even inside my house. Wifi is treated like it is the open internet. Never trusted.

All wifi protocols, including wifi-5 were found to have flaws that were in existence since the 1990s just a few years ago. While, they've probably fixed that issue in the supported devices, older devices aren't fixed and that's no use when the wifi consortium refuses to follow the best practices of security designers around the world.  Usually, when there is 1 bug found, there are at least 2 others in software.  When the architecture has a design flaw that's found, chances are there are 5 others that haven't been found ... at least by the public.  

All we can do is to take the steps that we can related to security. Everyone has a different level of effort they can or are willing to accomplish.
How paranoid you should be depends on what is at risk and who may be attacking.  The level of security needed to prevent a nosy neighbor is very different than the level needed to protect $5M in the bank or corporate secrets/assets worth $1B+.  Only you and your corporate security guys can decide what is appropriate.

---

