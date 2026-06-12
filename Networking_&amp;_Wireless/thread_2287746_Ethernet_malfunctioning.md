---
title: "Ethernet malfunctioning"
date: 2015-07-22
forum: Networking &amp; Wireless
---

### Post by jack152 on 2015-07-22
Hi, I have had my connection suddenly stop working. I haven't installed or done anything different recently. I'm a noob so I don't know how to go about diagnosing the issue. The odd thing is that the connection still shows up as connected, but no pages will load.

---

### Post by Vladlenin5000 on 2015-07-22
Hi and welcome.

Have you reboot the router already? Re-seated cables, confirmed the internet connection is working in other devices, ...?

---

### Post by jack152 on 2015-07-22
Yes I am using the same cable right now with the same ports, same everything, on my laptop.

---

### Post by Vladlenin5000 on 2015-07-22
> **jack152 said:**
> Yes I am using the same cable right now with the same ports, same everything, on my laptop.

OK, but the question was... [I]Have you reboot the router already? Re-seated cables, confirmed the internet connection is working in other devices, ...?
[/I]Can you ping your router from that laptop? Can you connect other devices?

---

### Post by lisati on 2015-07-22
> **jack152 said:**
> Yes I am using the same cable right now with the same ports, same everything, on my laptop.

I have a question as well. *What are you doing now that lets your connection work when it didn't work before?*

If pages are not loading, it could be anything from a malfunctioning connection, through network congestion, to a website that's down.

---

### Post by jack152 on 2015-07-22
I'm not doing anything differently, that's what I mean, I didn't change  anything on the desktop computer, it just stopped working. I just  unplugged the cable from my desktop, and plugged it into my laptop, and  it works fine. I plugged it back into the desktop, and now it does not  even register that the cable has been plugged in anymore.

---

### Post by jack152 on 2015-07-22
And the answers are yes yes and yes.

---

### Post by SeijiSensei on 2015-07-22
When the cable is plugged in, are the LEDs lit up on the card?

Did you try rebooting with the cable connected?

---

### Post by jack152 on 2015-07-22
I' dual-booting on an imac, so there isn't a card, it's just a monitor with an ethernet jack, no light. I was hoping to avoid a reboot because ubuntu is not installed, so I would lose all my configurations and add ons and everything else. In particular, I had a hell of a time getting audio to work recently, rebooting wasn't fixing it, so I'd have to go through that all again if I reboot, and possibly have this problem on top of it. Is there really no simple approach to diagnosing what is wrong, or any kind of built in troubleshooter in ubuntu maybe?

---

### Post by jack152 on 2015-07-23
I tried rebooting since replies here were so slow anyway. Internet connection worked fine for about 15 minutes, then stopped again.

---

### Post by jack152 on 2015-07-24
Well I must say I am very surprised, I thought Ubuntu was supposed to be a powerful platform, I've heard such good things, i'm shocked the only means of troubleshooting a malfunctioning ethernet connection is to unplug it, plug it in, reset it and reboot it. : P

---

### Post by jack152 on 2015-07-24
I finally was able to track down the problem, it had to do with the dns server selection conflicting with the openVPN settings. Thanks for the help.

---

