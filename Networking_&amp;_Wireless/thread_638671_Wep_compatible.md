---
title: "Wep compatible"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by tednugent on 2007-12-12
I am having trouble getting my wireless card to work on a dell latitude with any ubuntu distro. works fine without wep sees all available networks but will not connect with wep code. I am able to get my wifes laptop to connect with a belkin cardbus. Is it possible my card is not wep compatible? not sure what card it is just yet. Just thinking since it works great on an unencrypted connection this could be an issue. hoping smarter minds than mine might have an answer.thanks

---

### Post by mozetti on 2007-12-12
FYI - WPA is much preferred over WEP. WEP can be cracked in a manner of minutes.

---

### Post by tednugent on 2007-12-12
It is a intel pro/wireless lan 2100 3b mini pci says it can handle 128 bit encryption I have it on 64 could this make a difference? Or maybe I should use ndiswrapper and use a updated driver. I hate to because it worked so good before I was forced to use a wep because of my new neighbors using too much bandwith on who knows what.

---

### Post by tednugent on 2007-12-12
I just want it to work I think for now wep is good enough would wpa be easier to configure for the card?

---

### Post by mozetti on 2007-12-12
Not sure. 128-bit encryption is better than 64-bit, so if you stick with WEP at least bump it up to 128. 

Since it's not working now under WEP, why not switch to WPA and see how it works?

---

### Post by tednugent on 2007-12-13
problem fixed bought a netgear wg511t cardbus ubuntu 7.1 reconised it all I had to do was plug it in turn on the computor and put in the wep key works great.

---

