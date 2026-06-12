---
title: "Is ndiswrapper-utils contained on Ubuntu 7.04 CD"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by ray.farmer on 2007-05-24
I have been trying to find ndiswrapper-utils but it doesn't appear to be on my CD of Ubuntu 7.04. I obtained this version from Ubuntu download page. I have followed the instructions to burn the ubuntu 7.04 CD. Then used that CD to install on my DELL Inspiron 7500.

Following various instruction to get my netgear WG111 recognised, the first thing seems to be be get ndiswrapper installed. I been using the Package application but it doesn't find ndiswrapper.

So is ndiswrapper on the CD?

Any help would be grateful.
Regards
Ray Farmer

---

### Post by aysiu on 2007-05-24
It was included in the 6.06 and 6.10 CDs. For some strange reason, they removed it from 7.04.

---

### Post by tarynth on 2007-05-24
I can confirm as already stated, that ndiswrapper and ndiswrapper -util is not on the Feisty 7.04 CD.  Instead, I had to connect to the internet with a network card, install ndiswrapper from the Add/Remove software, and then disconnected from the internet, and proceeded to work on the netgear wg111.

---

### Post by ray.farmer on 2007-05-24
Hi,

Thanks for the responses,

Tarynth,

was that via ubuntu website?  
I assume you were able to access the internet via a different network card, unfortunately I cannot do this.

Regards
Ray Farmer

---

### Post by tarynth on 2007-05-24
Well, I am very new to Ubuntu and Linux in general.  I used the Add/Remove applications feature of Ubuntu which gathers software from many places.  Some are Ubuntu "approved" software but Ndiswrapper was not in the approved list. Ndiswrapper was listed when i chose, Show : ALL AVAILABLE APPLICATIONS

I know its possilbe to download source code and compile ndiswrapper yourself but I am so new to linux I found this to be difficult and used the above step instead.
And you are right, I was able to download and install Ndiswrapper because I had a regular pci network card in the computer.  Hopefully that answers your question(s)....

tt

---

