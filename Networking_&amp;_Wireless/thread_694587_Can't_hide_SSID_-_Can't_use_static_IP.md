---
title: "Can't hide SSID - Can't use static IP"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by DizMan on 2008-02-12
Hi there!

I'm new in Ubuntu town! I've only been "here" for a week, so please answer in details for "dummies" (yup, that's me)...

I've had a lot of trouble getting my wifi to work (Zyxel USB G-260), but after following one of the "howto"'s it works. I've installed a new version of Ndiswrapper from sourceforge.net and followed the guide point for point.

1. problem: It only works when I broadcast my SSID. When I hide it, Ubuntu won't connect to the net and sometimes the item "wireless network" is not shown in the network manager. When broadcasting the SSID everything is ok. I use WPA encryption. But I'd like to hide the SSID. Any idea to make that work? I've tried to enter the appropirate data in manual configuration. But it doesn't connect.

2. problem: When connected via broadcast mode my router assigns the IP address, for example: 10.0.0.33. But I would like so fix the IP address to let's say 10.0.0.20 so I always know, which pc has which IP address. Again I've tride the manual configuration, but then I cannot connect. Any idea to solve this.

Hope to hear from you. I'm pretty impressed with Ubuntu and think it rocks. My problems until now has almost only been with wireless networking. 

Thanks again...

/ Diz.

---

### Post by aeiah on 2008-02-12
you dont really need to hide your ssid. it is VERY easy someone to find out your SSID even if you have it hidden. the secure part of your set up is your WPA encryption. use a strong password and you will be safe. a long one, with random numbers, characters and symbols.

---

### Post by aeiah on 2008-02-12
as for assigning the same IP each time, this seems like something you'd set up in your router rather than on the client side. have you tried searching for such a setting with your router? what router are you using?

---

### Post by wieman01 on 2008-02-12
For 2 reasons:

**A.** The networking applet (called Network Manager) has issues with networks that hide their SSID.
**B.** It cannot handle static IP addresses at this stage.

In both cases you will have to wait until Ubuntu Hardy comes out.

---

### Post by DizMan on 2008-02-12
> **aeiah said:**
> as for assigning the same IP each time, this seems like something you'd set up in your router rather than on the client side. have you tried searching for such a setting with your router? what router are you using?

Hi, thanks!

I'm using a Zyxel P-2602HW-D1A dsl and sip router. Hmmm... It might have a possibility of linking a specific MAC-address to a specific IP-address. May be that was your thought as well?

Thanks again!

/Diz

---

