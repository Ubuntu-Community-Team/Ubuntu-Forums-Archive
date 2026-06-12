---
title: "Problems with D-Link DWL-520+"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-08-29
Hi everyone,
 
I just installed a PCI wireless card from an older computer into my machine. I'm running ubuntu 9.04. 

The card is a D-Link DWL-520+. Network manager shows no wireless devices. Whenever I go to System -> Administration -> Hardware Manager, it hangs at "Searching for available drivers" for about 10 minutes, and then tells me that "No proprietary drivers are in use on this system." 

```
iwlist scan
``` takes about 10 minutes as well, thereafter showing wlan0 in the list, but it says "no scan results" 

My computer also seems to freeze up a lot with this card installed. I'll be playing music and after about 5 minutes the whole system locks up. (Music starts stuttering, can't move mouse.)

This card works fine on my XP partition, so I know this is not a hardware issue. The green light on the back of the card blinks on and off.

Any help would really be appreciated. :)
Thanks in advance.

---

### Post by k3lt01 on 2009-08-29
Does the card work if you are using a LiveCD? if not are you using it with ndiswrapper?

---

### Post by sandyd on 2009-08-29
ok. im pretty sure your card works in ubuntu... or rather, the wiki claims that it works..

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)

from
[http://www.google.ca/search?q=D-Link+DWL-520%2B+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=D-Link+DWL-520%2B+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

it looks like theirs no WPA support out of the box, but that will be fine.
Which driver are you using for the card?
should be [acx111]("https://help.ubuntu.com/community/WifiDocs/Driver/acx111")

---

### Post by asuastrophysics on 2009-08-29
I just tested it on the LiveCD, but it still didn't work. 

I'm not using ndiswrapper or any other driver software that doesn't come with ubuntu out of the box. I know that my wifi card uses the acx-111 drivers. 

I thought it would be wise to ask for suggestions before i installed madwifi or ndiswrapper.

---

### Post by k3lt01 on 2009-08-30
Unless you can confirm the card will work with madwifi I'd use ndiswrapper. Having said that if you use choose ndiswrapper be sure you can get the drivers needed before you try it.

Have you had the internet using a wired connection?

---

### Post by LewRockwell on 2009-08-30
other D-link experience

[http://ubuntuforums.org/showthread.php?t=1252042](http://ubuntuforums.org/showthread.php?t=1252042)

.

---

### Post by asuastrophysics on 2009-09-30
> **k3lt01 said:**
> Unless you can confirm the card will work with madwifi I'd use ndiswrapper. Having said that if you use choose ndiswrapper be sure you can get the drivers needed before you try it.

Have you had the internet using a wired connection?

Yeah, back when I was in my other apartment, I had an ethernet port and internet worked flawlessly.

---

### Post by asuastrophysics on 2009-09-30
I think the card is toast. Every time I try to connect to a network in Vista, I get:

"wireless association failed due to an unknown reason"

lol this is why windows sucks. it doesnt think you're intelligent enough to handle the real reason ;)

the card seems unable to handle newer wifi passwords in the WPA format. Unassociated networks and unprotected ones work fine...:confused:

---

### Post by oldsoundguy on 2009-09-30
I use D-Link DWL 520+ cards exclusively.  Have one working in a Mythbuntu box, One in a Linux Mint box .. two working in 9.4 boxes and   one working in a Windows XP box .. all through a D-Link DWL-7100 AP and a D-Link DI-624 router.

I also have wireless cards that I use when I am repairing computers and need to get on line and they do some downloading or scanning.

Suspect as stated .. the card is toast.

---

