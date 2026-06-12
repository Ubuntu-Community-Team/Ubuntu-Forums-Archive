---
title: "New Plan - Netgear"
date: 2007-06-27
forum: Networking &amp; Wireless
---

### Post by Esqulax on 2007-06-27
Right... ive made a few posts.. but stuff has now changed!

I have a Netgear WG511 ver2
Ok, i have installed Fiesty Fawn... im pretty sure ive installed ndiswrapper-utils (its actually sudo apt-get ndiswrapper-utils-1.9)

which is cool...
looked up what driver i may need for the card i have... and lo and behold, its "Atheros madwifi" which is listed under "linux-restricted-modules"
So... how do i get it to do its magic?

When i pop the card in its slot (laptop PCMCIA card) nothing happens to indicated its in there (no lights on the card, no moves from the computer)

any ideas where to go from here?

---

### Post by spd106 on 2007-06-28
It depends on how new the card is. If it's a few months old the restricted drivers application should help you get it installed and working. If the card is newer and that fails then you can either download an svn snapshot of madwifi and build it yourself or fall back to ndiswrapper.

There might also be a message in the /var/log/syslog or dmesg complaining about the card being unrecognised when ath_hal and ath_pci are trying to load.

---

### Post by Antonio44 on 2007-06-28
Believe it or not I did this yesterday in Linux MInt for my mother on her laptop. I am pretty sure I used the following link:

[http://elehmann.wordpress.com/2006/12/23/netgear-wg511v2-wlan-card-on-ubuntu-edgy/](http://elehmann.wordpress.com/2006/12/23/netgear-wg511v2-wlan-card-on-ubuntu-edgy/)

I don't know if it will work or not but I spent days with this and got it to work yesterday using this.


Best of luck!


A.

---

