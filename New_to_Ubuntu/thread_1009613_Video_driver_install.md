---
title: "Video driver install"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by timp4jc on 2008-12-12
Can someone help me find a step by step guide on how I can install the ATI 8.28.8 graphics drivers on my 8.10 install of Ubuntu.  This is for an ATI Mobility Radeon 9200 (this is the last that is supposed to support this card).  I really appreciate the help.  Thanks.

---

### Post by phidia on 2008-12-12
You can look through the Ubuntu video wiki [here]("https://help.ubuntu.com/community/Video"), but perhaps you will find better driver installation using [envy or envyng]("https://launchpad.net/envy") depending on which is best for your card.

---

### Post by w4ett on 2008-12-12
The correct drivers for your card are included by default in Ubuntu. (xorg-driver-ati)

your card is not supported by the proprietary driver fglrx. Only the 9500 cards and above are supported by the restricted drivers See:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by timp4jc on 2008-12-12
What I do to get the screen to resolve correctly then?  When I boot it in live mode, I get streaked colors on the top third of the screen, black in the middle third, and black and white bars on the bottom third.  As soon as I boot safe graphics mode it is fine if you can stand 800x600. I am using a widescreen sony viao vgn-s150.

---

### Post by w4ett on 2008-12-12
I know that using the 8.10 release might be preferable, but have you tried the 8.04 LTS release (Hardy Heron)?  It might be be worth a try to see if the previous version of the xserver might be a little more compatible with your chipset....not to mention that is has 3 years of support as opposed to 18 months for Intrepid.

---

### Post by timp4jc on 2008-12-12
I tried it.  Same problem.  This thing is really kicking my tail.

---

### Post by overdrank on 2008-12-12
> **timp4jc said:**
> I tried it.  Same problem.  This thing is really kicking my tail.

Hi and I tend to agree with w4ett as I am using Hardy 8.04 with a ATI 7000. Could you tell us some specs on the system like is the ati graphics integrated and share the system memory?

---

### Post by w4ett on 2008-12-12
Agreed:  Give us some system specs and also copy and paste the results of the following commands so we can see what we're dealing with:
```

lspci
```

```
cat /etc/X11/xorg.conf
```

```
glxinfo
```

---

### Post by phidia on 2008-12-13
According to the wiki [here]("http://wiki.cchtml.com/index.php/Hardware") the legacy driver is still available for that card.
Main page of that resource is [here]("http://wiki.cchtml.com/index.php/Main_Page")

---

### Post by w4ett on 2008-12-13
From the AMD/ATI Wiki Page:
> RADEON Legacy

    These cards are no longer actively supported by AMD as of the 8.28.8 fglrx driver. The installer is still available on AMD's website. ati-driver-installer-8.28.8.run 
    [COLOR="Red"]If you own one of these cards, it is highly recommended that you use the "radeon" Open source drivers.[/COLOR] 

    * Radeon 8500
    * Radeon 9000
    * Radeon 9200
    * Radeon 9250 

In other words, development of the legacy fglrx driver has stopped, and it has not been compatible with the xserver in Ubuntu since 6.06.  This is not Canonical's fault, but rather AMD/ATI's, since it has chosen not to support their legacy cards any longer.

---

