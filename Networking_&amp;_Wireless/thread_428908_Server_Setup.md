---
title: "Server Setup"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by Uranium235 on 2007-04-30
Is Ubuntu feisty Server Edition compatible with the following network switches?

Dell Power Connect 2216
3com Super Stack II Switch 3300

---

### Post by madmetal on 2007-04-30
> **Uranium235 said:**
> Is Ubuntu feisty Server Edition compatible with the following network switches?

Dell Power Connect 2216
3com Super Stack II Switch 3300

i dont see them here 
[https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards)
but you might search the forums for users feedback..
i think what matters most is the chipset they have and the brandname..(eg 3COM should work fine..)

---

### Post by Uranium235 on 2007-04-30
Man those aren't network cards.  They're something like the switches your ISP uses for routing incoming signals. :)

---

### Post by madmetal on 2007-04-30
> **Uranium235 said:**
> Man those aren't network cards.  They're something like the switches your ISP uses for routing incoming signals. :)

yeap mea culpa! :) 
just didnt notice..

---

### Post by dmizer on 2007-04-30
i guess the real question here is ... define compatible?

or in other words, how are you planning to deploy these switches such that you are concerned about compatibility?

---

### Post by Uranium235 on 2007-04-30
Ok the "plan" is this guy wants to set up a full blown ISP, and he's got no knowledge of how to do so, just money and hardware.  I live in the middle of nowhere and I'm the only one with any (although it is little) knowledge of linux.  So I guess what I'm getting at is how do I make this stuff he's got work with the Ubuntu server edition? :)

---

### Post by dmizer on 2007-05-01
well ... a switch like you've quoted is just a switch.  it will opperate independant of which os you use as your main server.  these are not backbone switches for an isp, they are backbone switches for a large client, and as such, they simply opperate on firmware (possibly) with some minimal programing that can be done via a tellnet link or via a browser.

i certainly wouldn't want to roll out an isp on them, but they won't have any problem routing traffic to/from your linux server.

---

### Post by Uranium235 on 2007-05-01
Well if I can get the traffic routed for him properly that's the main thing at this point.  He can then worry about buying better hardware to do what he's wanting to do.

---

