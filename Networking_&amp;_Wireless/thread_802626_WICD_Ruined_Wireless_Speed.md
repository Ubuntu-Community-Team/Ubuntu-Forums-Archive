---
title: "WICD Ruined Wireless Speed"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by markder on 2008-05-21
I just upgraded to hard from gutsy a few hours ago. This also happened to be the first time in a long time that I've used the wireless card (I have a WMP54G v4.0) in my desktop because of a recent move. 

After completing the upgrade, my wireless was working great. I had around 70 to 85% signal strength. And my download speed at speakeasy.net/speedtest was around 15000kbps. However, my 'connection information' said my speed was only 1 Mb/s. I thought this might have been a small problem with Network Manager.

I decided to switch to WICD because I heard good things about it and that it allowed me to better control my wireless connections. After I did this, I started to have problems. Upon starting WICD up, my signal strength never went above 50%. My download speed became abysmal, only reaching 300kbps. 

So I went back to Network Manager. For some reason, I now can't achieve a signal strength of more than 65%. My download speed test only reaches 1000kbps. What can I do to solve this problem?

---

### Post by imdano on 2008-05-21
Wicd and NM don't really affect the quality of your connections.  They just associate with access points.  Once you're connected the speeds are dependent on your wireless card, wireless driver, and the access point you're connected to.  The only thing I can think of is maybe your rate got capped somehow, but wicd doesn't touch that, and I think it would only affect download/upload speeds, not signal strength.

What's the output of iwconfig?  Particularly pay attention to what your Bit Rate is set to.

---

### Post by markder on 2008-05-21
[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

I actually just tried the instructions in that thread and have no wireless connections even available when I'm logged into Ubuntu. My options under Network Manager just say 'Enable Networking' with no mention of 'Enable Wireless' I'm gonna try WICD again from a USB

Why do you think the speed stayed so low even after I reinstalled Network Manager?

---

