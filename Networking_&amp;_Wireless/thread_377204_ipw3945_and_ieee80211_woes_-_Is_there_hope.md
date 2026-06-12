---
title: "ipw3945 and ieee80211 woes - Is there hope?"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by Deguello on 2007-03-05
I am at wits end. I have tried to get my wireless working and have run up against dead ends, I hope someone can help.

I have an Acer Aspire 5601 AWLMi with the Intel/Pro 3945 wireless setup. I have a Win XP/Feisty Herd that I upgraded to 4.06 this afternoon as a dual boot system.

I used Synaptic to install the wireless network manager, but could not a .inf file to load.

I tried ndiswrapper setup, ieee80211 setup, and ipw3945 setup. With all of these I am not able to get past the 'make install' stage, as I get an error messages about not having permission to modify a file. 

I have a funny feeling that this may be due to the fact that I am in effect running a live cd install, but for me to make the leap entirely into Unbutu, I have to make sure that I can get my wireless working. Of course I could be wrong.

Is there anyone that can point me in the right direction?

Thank you!

---

### Post by andreas64 on 2007-03-06
Hi,

the ipw3945 is supported out-of-the-box. Just install linux-restricted-modules-generic, boot your machine and everything should work.
Andreas

---

### Post by drefined on 2007-03-06
I am having problems as well with the ipw3945ABG, I have a toshiba satellite a105-s4094 and everything installed fine and worked. I was able to connect to the net through hardwire but tried everything to get my wireless to connect but it wouldn't.

Everything seems like its working, the inboard card is picking up signals from my router and i was able to see my router but I was not able to connect using... sudo dhclient <eth1> At the end of it all, it says it's sleeping.. *SIGH* I'm tired and hopefully some legendary expert will be online to help us with this problem.

/end cry

---

### Post by Deguello on 2007-03-06
> **andreas64 said:**
> Hi,

the ipw3945 is supported out-of-the-box. Just install linux-restricted-modules-generic, boot your machine and everything should work.
Andreas

I hope it is that easy.

I will try this. Thanks for your response.

---

