---
title: "Can't connect to wireless home network [Linksys WRT54G &amp; HP Pavilion]"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by glanne on 2008-07-24
Dear Forum,

I own an **HP Pavilion dv2000 laptop with Windows Vista Ultimate OS**. I  installed Ubuntu via Wubi [[www.wubi-installer.org]](www.wubi-installer.org]) last night and tried it out today. Very impressed with the interface and was mad excited to finally use it until I realized I wasn't connected to the internet, my wireless network.

On my laptop, I have a sort of wireless tab which I can turn on & off by pushing it left-to-right. When it's turned on (the right) and working, it lights up blue. When it's off (and to the left), it lights orange. *In this case, it is on the right, which should indicate it to be on, but the light it still orange, which means wireless capability is disabled internally.* 

I checked the settings on the Internet icon on the top right (the two computer thingies) - it said everything was checked and enabled. I tried figuring things out through the System administrations for Networks and whatnot but still couldn't get through because I'm a complete newb. I probably wasn't doing anything right anyway.

I have a **Linksys WRT54G** for my home wireless network which requires a password.

Please please help me if you can! I apologize in advanced if this has been brought up before - I tried searching through the forums but the related threads I found were a bit too complicated to comprehend for my mediocre tech-capacity. Ubuntu looks like something I would definitely benefit with. That and I'm so ******* tired of Vista and all the ridiculous errors I've had to deal with.

Thank you so so much in advanced!!

Lesleigh Anne 8-[

---

### Post by PinkFloyd102489 on 2008-07-24
Open and terminal, enter these commands, and post the output that they give.


```
lspci
```
```
sudo lshw -C Network
```

---

### Post by ample on 2008-07-29
i also have a wrt54g wireless router which does not work with ubuntu.  my windows machine required that i plug into the router first, and run an exe from linksys to allow my computer to connect wirelessly.  it was NOT a driver for my wireless card since i have a dell card.  it was more like a driver for the router, to be honest i'm not sure what it was because ive never had to do it for any other router ive used.  they only have the exe for windows, no linux support.  has anyone else run into this problem and found a workaround?  

-ample

---

### Post by VyReN on 2008-07-29
I have a dv6000 and the wireless light always shows orange.  The wireless works great, but the light is ALWAYS orange.  Just ignore it, mind over matter. ;)

You will most likely need to install some of the MadWiFi drivers for the wireless to work (as I had to).  Just search your wireless card model and you should get some great instructions.

---

