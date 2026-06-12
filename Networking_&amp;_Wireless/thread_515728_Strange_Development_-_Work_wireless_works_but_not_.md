---
title: "Strange Development - Work wireless works but not home"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by mrtaylor on 2007-08-02
For a while I thought that my wireless card just wouldn't work - its a Dynex DX-WGPNBC.  I installed NDISWRAPPER and the necessary drivers.  The card would power up, but wouldn't connect to my wireless network at home

I have verizon online dsl with the modem/router combo.

I took my computer to work and booted into Feisty (I dual-boot with xp) and put in the necessary info for my work's wireless network - AND IT WORKED!

So...any ideas on why I'm able to connect to the wireless network at my work but not my home, where do I start?

---

### Post by arist0tle on 2007-08-02
wow!!!! that's a new one. lol!!! What kind of security do have at home on your router? Your work situation might have been a freak occurence similar to one I had on my University network using LEAP. Hate to be a downer...but having to keep windows around...laaame!!!!

---

### Post by noob12 on 2007-08-02
While at home do ```
iwlist scan
``` and ```
iwconfig
``` and post the results.  Also, it would be helpful if you post the result of ```
lshw -C network
```

---

