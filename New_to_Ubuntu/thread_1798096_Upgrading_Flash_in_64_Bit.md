---
title: "Upgrading Flash in 64 Bit"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by maembe on 2011-07-05
Since Adobe released an update a couple months ago, I haven't been able to use Flash to player videos or anything.  It just says "you need to update Flash".  Unfortunately, since I'm using 64 bit linux, there don't have an updated version available.  Is there any way to get it to work or do I just have to wait until they release an update?

---

### Post by haqking on 2011-07-05
if you are using firefox etc then i recommend the flash-aid plug in.

Worked fine for me for most sites, and i am using 64 bit 10.10.

I recently switched to chromium as my browser however and flash works alot better in it than in firefox in my opinion

---

### Post by phaditama on 2011-07-05
I agree with haqking. i recently switch to chromium and I also notice that flash works better in it.

---

### Post by PapaGary on 2011-07-05
FlashAid worked for me.

Natty 64 bit.

---

### Post by rosencrantz on 2011-07-05
I had that too after an automatic flash upgrade. I downgraded by hand which made it work again:

apt-cache policy flashplugin-installer
sudo apt-get install flashplugin-installer=10.2.159.1ubuntu1

---

### Post by oldos2er on 2011-07-05
> **rosencrantz said:**
> I had that too after an automatic flash upgrade. I downgraded by hand which made it work again:

apt-cache policy flashplugin-installer
sudo apt-get install flashplugin-installer=10.2.159.1ubuntu1

But if you want 64-bit flash, the easiest way to get it is with FlashAid.

---

### Post by the.phantom on 2011-07-06
flash-aid   !

it makes it easy to upgrade and downgrade as needed and has a few tweaks you can try !
works 32 and 64 bit
solved my 64 bit trouble
but on a a older1.7 gig processor with 1.5 gig it didn't help much

---

### Post by wildmanne39 on 2011-07-06
Hi, +1 for flashaid just open firefox click on tools,addons, the install flashaid and you have to follow the directions it will run a script that will install the best flash for your system. Created by LovingLinux.

---

### Post by maembe on 2011-07-08
I added flashaid but I don't know how to use it.

---

### Post by oldos2er on 2011-07-08
[http://www.webgapps.org/add-ons/flash-aid](http://www.webgapps.org/add-ons/flash-aid)

FlashAid puts an icon on your navigation bar, just click it.

---

### Post by SeijiSensei on 2011-07-08
Does FlashAid install the "[Square]("http://labs.adobe.com/technologies/flashplayer10/square/")" version of FlashPlayer on 64-bit systems?  That's the only one I've ever used.  I do have a problem sometimes going to full-screen, but otherwise it seems pretty flawless and not especially demanding of resources either.

---

### Post by grahammechanical on 2011-07-08
I am using 64bit and I watch TV in Firefox using the BBC iplayer. This needs Flash 10. I remember when the switch from 9 to 10 was made. But there is now a 64bit Flash 10 available. I am using it Firefox says I have 10.3 r181 installed.

Here is a link

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Note this comment

> **64-bit users**:  [Download a preview release of Flash Player with native support for 64-bit Linux]("http://labs.adobe.com/technologies/flashplayer10/square/") from Adobe Labs.
It also mentions something about Square.

You may even find the Software Centre will download the 64bit version.

Regards.

---

### Post by Muskegman on 2011-07-08
The FlashAid icon will appear at the top right of the web browsers panel, just click it it will do the rest.

I can also confirm FlashAid corrected my 64bit Flash and all is working

---

