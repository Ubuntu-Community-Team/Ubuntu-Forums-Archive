---
title: "K(Ubuntu) and modem Octal A360"
date: 2005-10-24
forum: Networking &amp; Wireless
---

### Post by flamarro on 2005-10-24
Hi there, 
As you can see, with this modem i'm from Portugal. My ISP is SAPO and i have a ADSL connection to the internet with this modem.
Well, I always have problems to make this modem work, but, with more or less trouble i could get my objectives done.
I use to have ubuntu hoary working, with the **amedyn drivers** that worked really good. only have to install linux-atm rr-ppoe e libusb-dev. work great.
make dist-upgrade to breezy, restarted, then amedyn doesn't work anymore. Upgrade cap, sudo make amedyn again amstart.sh and there you go again.
Now the problem, always had ubuntu, wanted a fresh install of breezy, and would like to try kubuntu as well, so that i could write the so many tweaks i've done in ubuntu. I am a litle lost, i think i don't know how can i make this all thing work at all, sometimes i think this :-).
So, new partition, dowwnloaded Kubuntu breezy and give it a shoot.Well, i can't make amedyn drivers work in kubuntu breezy. It gives me a error when i do **make**. I have installed libusb, linux atm, rp-pppoe, nothing, i can't understand what is missing, what is the tiny litle thing that i am doing wrong.
Does anyone here is from Portugal and have this modem working in a fresh install of 5.10?

---

### Post by flamarro on 2005-10-27
ok. Now i can do the compile thing. Amedyn drivers, as i can understand need gcc 3.4 and breezy comes with 4.0.....
installed and it works. Now when i do **sudo amstart.sh**, in the end it start with strange letters.....

---

### Post by aka_zedweb on 2006-11-22
Could you please post a detailed explanation of how to install the necessary packages, where to get them without net, and the downgrade compiling option? Please  :-D   My Sapo Octal is killing me!

-------

EDIT: Problem solved
Got a generic .deb package for my 2.6.17-10-generic Kernel and everything works fine. I'm already typing this from Ubuntu's Firefox :-)

---

