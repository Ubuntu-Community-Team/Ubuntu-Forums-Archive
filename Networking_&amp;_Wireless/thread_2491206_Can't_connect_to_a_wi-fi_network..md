---
title: "Can't connect to a wi-fi network."
date: 2023-09-29
forum: Networking &amp; Wireless
---

### Post by marsbar23 on 2023-09-29
Hello. I have a old computer, a hp dv5000, I was hoping to setup to donate to charity. However there's no easy way to connect to the net. I'm used to Windows, bearing this in mind, can you help?

---

### Post by SeijiSensei on 2023-09-29
Can you wire it directly to your router with an Ethernet cable? That should be all you need.

---

### Post by marsbar23 on 2023-09-29
Hi. Yes I thought of that, but don't have access to the router as it's shared accommodation. Only wi-fi, but I can't get the list of networks to show.

---

### Post by SeijiSensei on 2023-09-29
It's likely a driver problem then. 

If you're donating the computer, I'd just wipe the drive and let the donation agency decide what to do about an OS. 

I have a Win10 installation ISO that I used to create a clean installation on the last PC I donated. Went through all the steps up until it wanted me to sign into Microsoft. Left it there for the agency to handle.

---

### Post by marsbar23 on 2023-09-29
I've managed to install a broadcom from a driver package, transferred from my other laptop. Now I don't know what to do.

I want to setup the device myself, not leave it to the shop.

I'm downloading some .deb files for the old laptop I'm trying to install, however, 90 per cent of them state "Could not open, The package might be corrupted...". Can anyone shed light on this?

---

### Post by SeijiSensei on 2023-09-30
Try "sudo modprobe name_of_driver_module".

---

### Post by marsbar23 on 2023-09-30
Due to problems with Linux, because of my inexperience, I'm going to try XP now, and hope windows update downloads the WiFi drivers I need. I discovered I could tether my phone and old laptop, so I'm giving it a bash. XP is the original OS, so it should be possible.

It's so old it only goes up to 1280 or so, horizontal resolution, no HD resolution here! 1GB RAM, 120GB HD. Dinosaur.

Update : couldn't tether my phone with Windows. At this rate, it looks like another landfill item.
Update : tried a different Linux distro and found that it supported my Broadcom out of the box. No hacking needed.

---

### Post by readableauthor on 2023-10-01
Do you know what Wi-Fi adapter is installed in there? On Linux you can find it out this way in the terminal:
```

lspci -nnk -d ::0280

```

---

### Post by marsbar23 on 2023-10-02
@ readable Thanks for the help! I solved it last night though, I was looking for a very light distro, and tried Linux Lite. To my surprise it supported my Broadcom 4318 WiFi board, no hacking with the command line needed. 

I must have tried at least 20 different distros, and discovered more problems just in trying to solve the wi-fi connection one.  It snowballed and I discovered that the laptop had a completely dead battery, and even L.L. was quite sluggish, so I bought a 1GB stick of RAM, from a Chinese seller on eBay, and found a battery from Amazon.

Other problems I had was in trying to understand the Linux CLI, and it's architecture. I was at one point determined to add the driver to a distro, and had a number of very technical documents at the ready to try it, before I got lucky. &#128515;

So I'm finished until the parts turn up! (which will be literally on the slow boat to China).

---

