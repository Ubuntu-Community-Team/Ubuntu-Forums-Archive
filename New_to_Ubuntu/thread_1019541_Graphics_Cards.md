---
title: "Graphics Cards"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by gridd on 2008-12-23
hi I'm considering getting a tv dvd graphics card which ones would you recommend. I'm using this.

 00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

At the moment  and i think it s on an nec intel  M board. 
using Ubuntu 8.04, but considering moving up to 8.10.
cpu Intel(R) Pentium(R) 4 CPU 2.80GHz
 
But 8.10 will not run on my system, It just hangs after booting up and logging in. To either a black or beige  screen with live cursor.
 screen resolution is 1680 x 1050  60 hz 20"
  
Any advice would be appreciated thanks.ps 8.10 has been md5 checked.

---

### Post by Titan8990 on 2008-12-23
> hi I'm considering getting a tv dvd graphics card which ones would you recommend. I'm using this.


This would completely depend on two things:


Does your motherboard have a PCI-e x16 or AGP port?


What is the max output of your power supply?

---

### Post by gridd on 2008-12-23
> **Titan8990 said:**
> This would completely depend on two things:


Does your motherboard have a PCI-e x16 or AGP port?


What is the max output of your power supply?hi. how do i find these things out aside of sys info?

I have just used sys info which gave me this. intel corp. 82801 PCI Bridge (rev82)(prog-if OO [Normal decode])

I dont know if that is any help at all.

---

### Post by Titan8990 on 2008-12-23
There is a couple ways to find out if what kind of expansion slots your motherboard has:


A) Physically look at the board

B) Look up your motherboard's documentation

C) Look up the documentation for your PC's model number


To find the power supply info:


A) Look on the side of the power supply, its the only way

---

### Post by gridd on 2008-12-23
I've taken side of box off it says 400w dc output.IN RED
+3.3V   +5V   +12V   -5V   -12V   +5VSB
20 A   30 A   20A    0.5A  0.8A   2.5A

---

### Post by Titan8990 on 2008-12-23
That should be fine since you it doesn't sound like you need a hefty gaming card.

How about expansions slots on the board?

---

### Post by gridd on 2008-12-23
One Expansion slot free for 1000 mb memory 

Three, white ones 49pin plus 11 pin (sorry Ive forgotten the name for these)two occupied one dial up which i can lose. 
one firewire.and a small brown one free.
 So a possible max of Two free + 1mg mem.

---

### Post by Titan8990 on 2008-12-23
The small brown one is an AGP port. AGP is a dead technology but there are still graphics cards available for it but you will be paying more than its worth since it is "legacy" equipment.


Something like this: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814133176](http://www.newegg.com/Product/Product.aspx?Item=N82E16814133176)

---

### Post by gridd on 2008-12-23
[QUOTE=Titan8990;6423384]The small brown one is an AGP port. AGP is a dead technology but there are still graphics cards available for it but you will be paying more than its worth since it is "legacy" equipment.


Something like this: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814133176](http://www.newegg.com/Product/Product.aspx?Item=N82E16814133176)[/QUOT

hi,that looks good does Ubuntu already have drivers for this or will i have to download them.thanks.

---

### Post by Titan8990 on 2008-12-23
Both, there are the open-source nvidia drivers that come with Ubuntu as well as the closed-source that work better but need to be downloaded via the Restricted Drivers Manager.

---

### Post by gridd on 2008-12-23
Cheers have given thanks.

---

