---
title: "Configurinh MN-710 without Internet connection"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by ganiba on 2007-05-25
Hi,
i'm trying to install MN-710 with ubuntu 7.04 and all the time i can't get it work.
The probolem is that i don't have access to internet by a cable only by wireless. So, i can't really download online the needed packages.
What i've done is burn the Ubuntu DVD. I found on it ndiswrapper with utils. But, when i tried to install an other application"Wireless Windows Drivers, ndiswrapper graphical tool" i can't find it in DVD.

So, nothing worked in this way. So, i made a new installation and download the last ndiswrapper from their website (not dvd), and follow some procedure such as the one used to install Broadcom Card.
Finally, i make the light on my USB card flashing and i can now see different wireless networks, BUT, i can't connect to any one of them. I don't know why.
The network i'm intereseted into uses WEP, so i don't know if this is the problem.

So, my question is if there is someone who could install the same card MN-710 on ubuntu 7.04 without having internet connection?

Thanks.

---

### Post by wrongopinions on 2007-05-29
I am having similar trouble. I would classify myself as a real beginner... as in this is the first thing I have attempted with xubuntu or any linux other than installation. 
After figuring out I need build-essential installed just to use a make command (remember I am a noob) I managed to get ndiswrapper working. I too cannot do this with an internet connect seeing as I need the mn710 to get the internet. 
My snag is I downloaded the driver for the mn710. It has an .inf and a .sys file. I am not sure how to install those into ndiswrapper. 

Maybe I am approaching this incorrectly... how did you (or anyone) get and install the mn710 driver?

Also, my best advice on why an internet page is not showing up (remember I am new... dont laugh too hard at me): since you are seeing wireless signals, couldnt it be as simple as you just do not have the network setup yet? try configuring a network then connecting to it........that would be my first guess, seeing as I will probably have to face this issue once I get the driver working

thanks for anyones help

---

### Post by wrongopinions on 2007-05-29
sorry for the double post... after much headache, and remarkable luck... I am stuck at the same point you are...

I see the networks, and I see my own. I try to configure to it, but its just not bringing up webpages. I am also using WEP. 

So anyone have advice for both of us?!!?!?

---

### Post by ganiba on 2007-06-04
I Give up from trying Wireless connection with Ubuntu.
I'm using windows now and i'll wait until Ubuntu becomes mature to handle wireless cards correctly.

---

### Post by netvip3r on 2007-07-09
MN-710 does work with ndiswrapper on Feisty

files you'll need are [ mn710.inf, mn710-50.sys, mn710-51.sys ]

when you run [ sudo ndiswrapper -i mn710.inf ], this installs the .inf file to /etc/ndiswrapper/mn710 but **does not** move the .sys files. Copy both .sys files to this location manually. ndiswrapper should be moving all files into /etc/ndiswrapper/mn710 but it is not sometimes.

---

