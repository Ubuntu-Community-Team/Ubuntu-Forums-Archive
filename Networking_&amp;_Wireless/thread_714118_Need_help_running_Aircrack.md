---
title: "Need help running Aircrack"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by OldNewb on 2008-03-03
I have a an atheros AR5BXB63 chipset and the only way I have found to get it to work is using ndiswrapper.  When I go to use Aircrack I get this error

me@computer:~/aircrack$ sudo aireplay-ng -9 wlan0
Ndiswrapper doesn't support monitor mode.

Is there a way to get this to run?

---

### Post by OldNewb on 2008-03-03
... Bump ...

---

### Post by dynamethod on 2008-03-03
You cant use the ndiswrapper driver with aircrack, period.

ndiswrapper does not support monitor mode

---

### Post by azhtar on 2008-03-06
yes it does, i run with ndiswrapper and bcm43xx firmware and i can put it into listening mode, I don't know what's the problem with him, but it does work.

---

### Post by wieman01 on 2008-03-06
Listening mode, yes, perhaps. But reinjection won't work.

---

### Post by OldNewb on 2008-03-06
> **azhtar said:**
> yes it does, i run with ndiswrapper and bcm43xx firmware and i can put it into listening mode, I don't know what's the problem with him, but it does work.

How do you put it into listening mode?

---

### Post by wieman01 on 2008-03-06
You could follow my WEP tutorial (signature) for instance.

---

### Post by azhtar on 2008-03-09
> **wieman01 said:**
> Listening mode, yes, perhaps. But reinjection won't work.

It does works with packet reinjection, have a look at [[COLOR="Blue"]this link[/COLOR]]("http://www.aircrack-ng.org/doku.php?id=broadcom"), as you can see, there's a patched driver wich I use with my HP Pavilion DV9074cl, but if you want to get it the easy way, download backtrack3 beta linux distro, it already has the patched drivers and all ready to run.

> As of 2.6.17, a driver for the Broadcom bcm43xx wireless chipset has been included in the kernel. Older kernels can sometimes be made to work, check out resources available here While this driver natively supports monitor mode, **it requires patching before packet injection can be done**. After testing aireplay-ng with the patches, please contribute to the forum thread by reporting any successes or failures there.

I want to remember everybody a thing, As Mr. wieman01 says in his nice tutorial ;) (BTW thanks for it dude), do not attempt to crack any wifi network without propper permission, it is illegal, so better to spend some bucks getting your own friggin Internet connection than to pay some time in Jail

---

### Post by wieman01 on 2008-03-09
> **azhtar said:**
> It does works with packet reinjection, have a look at [[COLOR="Blue"]this link[/COLOR]]("http://www.aircrack-ng.org/doku.php?id=broadcom"), as you can see, there's a patched driver wich I use with my HP Pavilion DV9074cl, but if you want to get it the easy way, download backtrack3 beta linux distro, it already has the patched drivers and all ready to run.
I was talking about 'ndiswrapper", not the native Linux driver. The native one is capable of it of course...
> **azhtar said:**
> I want to remember everybody a thing, As Mr. wieman01 says in his nice tutorial ;) (BTW thanks for it dude), do not attempt to crack any wifi network without propper permission, it is illegal, so better to spend some bucks getting your own friggin Internet connection than to pay some time in Jail
Very true.

---

### Post by azhtar on 2008-03-09
:lolflag: so it is a Native linux driver? :lolflag: thanks for the info, I didn't knew, since I'm still a noob i thought it was a ndiswrapper driver :P

---

### Post by wieman01 on 2008-03-09
No issue... Lol.

"ndiswrapper" is a wrapper module for Windows drivers. It basically lets you load Windows drivers and it works extremely well. Check out this site for more:

[http://ndiswrapper.sourceforge.net/joomla/]("http://ndiswrapper.sourceforge.net/joomla/")

---

