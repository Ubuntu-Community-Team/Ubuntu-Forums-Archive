---
title: "eth1 instead of wlan0"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by clobberze on 2007-05-18
i just installed ubuntu 7.04 from the cd that just arived, and for some reason my wireless connection apear like eth1 and to make thigs even worst (at least imo).
i am a complete noob in linux. so i took some screenshots to explain better my problem.

in the network tools i get this

[IMG]http://img521.imageshack.us/img521/4987/dammittd4.png[/IMG]


but in the Manual configurations i get this

[IMG]http://img390.imageshack.us/img390/3302/dammi2qd5.png[/IMG]


and the funniest is that the wireless usb can actualy find my router!!!

[IMG]http://img521.imageshack.us/img521/3407/dammit3zn0.png[/IMG]



well... if any soul is willing to help me i apretiate it.

If any other  information is needed please ask and tell me how to get it (noob here)

And  to finish:  it's a laptop Toshiba Satellite 1410-304

And the wireless ubs device is a Sitecom WL-113.


ty :)

---

### Post by dfreer on 2007-05-18
hmmm. depending on the wireless driver, your wireless card can be detected as ethX (most intel), athX (most atheros chipsets), or even wlanX (I think broadcoms or those installed with ndiswrapper?). anyways, the point is as long as it works it doesn't matter what name it has.
It looks like it correctly detected your wireless Access Point, are you having network issues or problems reaching the internet? If not don't mess with it :D

---

### Post by clobberze on 2007-05-18
:) i have no ideia what u just said on the first lines.

but i'm on wired network. if i use wireless and even putting the ips and dns like i did on the wired it still don't work.

any other thoughts?

---

### Post by clobberze on 2007-05-18
any clues?

---

### Post by dfreer on 2007-05-19
basically I was just saying do not worry about the name change.

when you click on your router name in this image:
[IMG]http://img521.imageshack.us/img521/3407/dammit3zn0.png[/IMG]
What happens? does it try to connect and fail? does it ask for a wireless password?


you might want to check and make sure that the correct drivers for your wireless card is installed. Also, wireless USB dongles are notorious for not playing nice with linux.

---

