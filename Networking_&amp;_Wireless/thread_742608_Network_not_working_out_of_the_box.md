---
title: "Network not working out of the box"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by Threecorners on 2008-04-01
Hi, I've been trying out the latest Ubuntu live CD to see if it would be a viable option for me to install Ubuntu.  Anyway, I have a very standard generic ethernet card through which I get internet.  Under Windows i just set up DHCP and it works.  Ubuntu, however, is being odd.  It detects the card correctly, but whether I set up DHCP or I manually give it IP settings, it can't seem to receive (or possibly send out?) data.  If I try and set up DHCP it gets given some bogus IP that I know won't work, and running sudo /sbin/dhclient fails because, once again, it doesn't recieve any data.  The documentation provided is sparse and claims that a wired connection should just work.  Any ideas at all? =/

---

### Post by Iowan on 2008-04-01
Under the "Manual network configuration" icon (ie right click it), verify "Enable networking" is checked. You can also open it up and verify "wired connection" is checked.

OOPS!!! May/not work on Live CD... What card?  IIRC, I had problems with my favorite (3Com 3C509B)

---

### Post by Threecorners on 2008-04-01
Yep, everything's checked.  My card is a IC Plus IP100 10/100 Fast Ethernet Adapter, it's integrated into my motherboard.  That thought had occured to me, that it won't work under the Live version, but Ubuntu does recognize it, so I think it has drivers for it.  Also, when you go to manually configure, what does "roaming" refer to?  Does that also mean DHCP?  Thank you!

---

### Post by Threecorners on 2008-04-02
Bumping for tonight, in case anybody else reads this.

---

### Post by I||usion on 2008-04-02
same thing happening to me worked fine with windows but with ebuntu its not a fan at all and its very annoying got it all checked and yea the help stuff doesnt even specify it. im using a d-link wireless router but have it atm through the ethernet and turn wirless on and get the same thing doesnt work so whats up with it? thanks by the way   :confused:

---

### Post by Iowan on 2008-04-02
@Threecorners
Try unchecking the "roaming" option.  Highlight the "Wired Connection", then check "Properties".  Verify that DHCP is selected - it kinda sounds like another (non-manual) selection - I'm away from Ubuntu, and don't remember exact wording. You might post results of **ifconfig -a** and contents of **/etc/network/interfaces**.

---

