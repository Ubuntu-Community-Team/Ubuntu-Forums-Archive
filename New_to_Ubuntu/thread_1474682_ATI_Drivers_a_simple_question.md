---
title: "ATI Drivers: a simple question"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by TechDragon on 2010-05-06
I have an ati video card in my IBM t60 laptop.  When I click on the "hardware drivers" built in ubuntu management piece it shows no proprietary drivers are installed and does not give me any options to install a proprietary driver.

Do I need to add a repo? Or do this manually? I am so used to Ubuntu just doing things for me :)

The reason I ask is when I utilize wine to play games that require directx i am receiving an error stating that the dxdllreg.dll cant find a video card.  I have tried reinstalling ubuntu but get the same error.

I am thinking I need to add the ati driver.

---

### Post by LowSky on 2010-05-06
Older ATI cards, like the one in your T60 are no longer supported by AMD/ATI. All that is available is the community driver which is used by default.

---

### Post by TechDragon on 2010-05-06
hmm that sounds like that sucks. Is there anyway to install one of the old proprietary drivers

or possibly even know of a distro that still adds the old drivers?

---

### Post by Mark Phelps on 2010-05-06
> **TechDragon said:**
> ...Is there anyway to install one of the old proprietary drivers
Not really ... 

The main problem is a combination of the following:
1) ATI quit producing fglrx drivers for some Legacy cards over a year ago
2) The current fglrx drivers from ATI website will NOT work with the older cards
3) The older ATI fglrx drivers that will work with the legacy cards will not work with X-server versions newer than Ubuntu 8.10

So, in theory, if you regress your X-server back to the version that was in Ubuntu 8.10, you should be able to then use the Catalyst 9.3 drivers (latest ones that will work with the legacy cards) ... but that is a LOT of work, runs the risk of trashing your graphics display capability, and prevents you from using any of the improvements to the X-server since Ubuntu 8.10.

> or possibly even know of a distro that still adds the old drivers?

As mentioned above, it's not just the old drivers, it's also the old X-server, and no, not aware of any Linux distro that is still using the X-server from the Ubuntu 8.10 days.

---

### Post by sandyd on 2010-05-06
Theirs legacy ATI drivers avalible for those cards.

take a look @ [http://www.google.com/search?client=ubuntu&channel=fs&q=legacy+ATI+linux+drivers&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=legacy+ATI+linux+drivers&ie=utf-8&oe=utf-8)

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)

---

### Post by shebaw on 2010-05-06
What version of Ubuntu are you running, lucid supported my ati graphics card out of the box for the first time in any ubuntu distribution. The open source driver is way better than the Catalyst 10.04 driver on my machine.

---

### Post by Mark Phelps on 2010-05-06
Shebaw:

The OP is asking specifically about proprietary drivers -- the fglrx drivers. The open source driver is not installed through the Hardware drivers option; only the fglrx driver is installed that way.

The open source drivers are installed by default.

Carlee:

Those legacy drivers will NOT work with recent versions of the X-server.  To use them in anything recent, the OP would have to regress their X-server version -- which I already mentioned.

---

### Post by TechDragon on 2010-05-06
hmm well .... i dont mind utilizing wine for the two games I like but it appears that the open source drivers don't work with directx atleast in my experience does any one else have any luck?

WineHQ says:
Runes of Magic and DDO should work with a little tweaking, I have done the tweaking just not getting any love.

---

