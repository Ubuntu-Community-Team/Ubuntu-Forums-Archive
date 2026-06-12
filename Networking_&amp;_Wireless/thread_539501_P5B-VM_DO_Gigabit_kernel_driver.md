---
title: "P5B-VM DO Gigabit kernel driver"
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by ^KrS^ on 2007-08-31
Hi all i'm hopeing someone can shed some light on an issue i've got.  Our server is using Asus P5B-VM DO motherboard with ain intel (82665 i believe) gigabit nic onboard.  We've recently upgraded our main switches to gigabit and would like to use the onboard controller (we've been using a 3com 905c which worked fine).

The problem i'm having, we're running 7.04 release and it's never gotten the intel nic to detect correctly, i've tried downloading the drivers from intel website, which compiled fine, but still couldn't get an ethx out of it.  Best it does is try to load the module and it "half" detects it:

[  357.169672] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:1a:92:77:7e:9f
[  357.263162] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection

That's as far as it gets.  I've tried rmmod and modprobing the iTCO_wdt and iTCO_vendor_support modules as well and no change in progress.

Ok now the fun part heh, i grabbed the tribe5 live image and booted the server from that.  Wouldn't ya know intel nic came right up no problems.  So i figured i could grab the kernel and modules from tribe repo and run 2.6.22-10 on my 7.04 install, everythign installed fine, booted fine, but.. again, no intel nic.

So this is where i'm stumped, why would the e1000 kernel module work in tribe 5 but not if installed in 7.04.

I'm pretty sure i've seen ppl get this exact motherboard to work with the intel nic in ubuntu before, but i'm having a REAL fun time trying to get it to go :)

Any suggestions are welcome! i should have time today to try em out and reply back with results.

Thanx so much!!

Kev

---

### Post by noob12 on 2007-08-31
What do

```

sudo ethtool eth0

ifconfig -a

```

show when booted in 7.04?

---

### Post by ^KrS^ on 2007-08-31
Thanks so much :) i found when runnin ifconfig -a it was assigning eth2 to it instead of eth0 (weird it says eth0 when modprobing)

everything is good now that i know it's eth2 lol

Thanx again!

Kev

---

### Post by noob12 on 2007-08-31
Check the mac addr of your device and you can map that to eth0 in **/etc/iftab**.  It's getting reaassigned to eth2 because you have some other mac addr listed in that file.

**man iftab** for more info.

---

### Post by ^KrS^ on 2007-08-31
Ahhhh ok i get it now, ya i had a different mobo running this install of 7.04 a while ago.. that's where the eth0 came from... the clouds are clearing lol

Thanx again so much for your insight, to remedy my shortcomings ;)

Kev

---

