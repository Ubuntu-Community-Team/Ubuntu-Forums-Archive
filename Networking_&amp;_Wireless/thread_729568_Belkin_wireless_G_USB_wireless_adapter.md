---
title: "Belkin wireless G USB wireless adapter"
date: 2008-03-20
forum: Networking &amp; Wireless
---

### Post by whirley on 2008-03-20
Hi i'm a noob.

I do a full installation using ubuntu 7.10 with my Belkin wireless G USB Network adapter.

Everything works fine for a few hours then i just lose network connection. 

I then reboot and the problem seems to disappear but after a few hours i get the same problem.

I do know i have the Belkin wireless v3000 with ID 050d:705a

Any ideas?

---

### Post by deltaprime on 2008-03-20
well there could be a few possibilities
did you just install ubuntu and not change any settings on your router?
did you change settings after installing ubuntu?
try using a different wireless utility like "wireless assistant" installable through system/administration and then synaptics where you can search for it.
you can try to move closer to the router and see if the problems continue.
reply and ill give you more detail if you can tell me more

---

### Post by whirley on 2008-03-20
1. I have not changed any settings on the router as settings are limited.
2. No settings were changed after installation, i only installed the update, nvidia driver using envy, a LAMP server and mldonkey-server.
3. Network assistant gives me an error i think it's because of gnome
4. Proximity to the hub has never been a problem i'm at 80% connection if the other problem does not occur.

except for that i don't know what to tell you...

need any more info?

---

### Post by whirley on 2008-03-20
it just happened after my new clean install,
i did iwconfig and ifdown and this is what i got.

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifdown

ifdown: interface wlan0 not configured


+++++++++++++++++++++++++
Even if i restart now it does not help but in windows it works fine..

Thank you

---

### Post by whirley on 2008-03-21
Anyone?

---

### Post by rustybronco on 2008-03-21
RT73 Chipset...
[http://ubuntuforums.org/showpost.php?p=2395871&postcount=1](http://ubuntuforums.org/showpost.php?p=2395871&postcount=1)

---

### Post by whirley on 2008-03-21
Thank you very much rustybronco

it took a bit of restarting but problem seems to be solved.

---

### Post by deltaprime on 2008-03-22
> **whirley said:**
> Thank you very much rustybronco

it took a bit of restarting but problem seems to be solved.

nice:)

---

