---
title: "Trying to determine what wireless card this computer has"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by bg1256 on 2007-10-15
I am shopping for a new laptop, and I found one that will meet my needs [here]("http://www.circuitcity.com/ssm/Gateway-MT3423-14-1-Widescreen-Laptop-Computer-MT3423/sem/rpsm/oid/186484/catOid/-12963/rpem/ccd/productDetail.do#availability").

There is one thing that I am struggling to determine, however, and that is what wireless card it has installed.

I looked at Gateway's website and found that model's components [here]("http://support.gateway.com/s/Mobile/2007/Apache/1014654R/1014654Rcl4.shtml").

When I clicked on GemTek, it shows BCM4318E.  Does that mean it's using a Broadcom chipset?  If so, I'm a little disappointed, as my older laptop uses it, and I'm trying to avoid ndiswrapper.

But, the link says Realtek 8115L, which works out of the box according the the supported hardware list stickied in this forum.

If anyone can help me make sense of this, I would appreciate it, because I'd love to have a laptop whose wireless card works out of the box.

---

### Post by openaddict on 2007-10-15
Yep, it looks like a Broadcom chipset from the links you provided.  If you can, find a laptop that has an Intel wireless chipset.  Intel is very good about supporting Linux with their excellent wireless drivers.  I have a high-end laptop with an Intel wireless chipset and it works perfectly out of the box with every distro I've used.

---

### Post by bg1256 on 2007-10-15
Thanks for the very quick reply.

I have heard from other people that Intel is the way to go as far as Linux is concerned.

The appealing part of this particular laptop is that the hardware is about as good as I can get within my budget...

Ah, well.  Maybe I'll do some reading about how well ndiswrapper works with this particular chipset.  

Thanks!

---

### Post by openaddict on 2007-10-15
Have you taken a look at System76?  They offer 2 models of low cost ($699) laptops and officially support Ubuntu Linux.  In fact, they're a Linux-only hardware vendor.  (Disclaimer: I do not work or have any affiliation with System76.)

---

### Post by bg1256 on 2007-10-15
Never, ever heard of it.  I'll check it out.

---

### Post by KCPokes on 2007-10-15
I have a Gateway (MX8738) laptop which has a Realtek wireless card.  I can confirm that it does use a Broadcom chipset and it does work "out of the box" with Feisty.  That said, you'll be unhappy with the wireless "out of the box".  Mine works but it is 1) slow and 2) it drops under any type of load and sometimes with no load at all.  I'm to the point that I'm ready to blacklist the bcmxx module and try ndiswrapper just to see if it provides any sense of stability.  I've used ndiswrapper with my other distros and cards and have been happy with the results compared to with what I'm getting now.

---

### Post by bg1256 on 2007-10-15
Thanks, KCPokes.

I am currently using ndiswrapper with a broadcom chipset, and it is stable and fast. However, I have a strange problem: it seems that whenever I boot up my computer, and there is no wireless network present, the wireless card does not get turned on automatically, and I cannot get it turned on no matter what I do.  The reason this is a problem is that this also happens when a wireless network is using encryption; hence, I am unable to connect to networks with encryption.

I've tried network manager and wicd, and neither seems to help.

---

### Post by KCPokes on 2007-10-15
I may find the time tonight to mess with making the change to ndiswrapper.  If I do, I'll let you know how it goes.  For the most part I've never had a problem with ndiswrapper, so surprised that you are having an issue.  Of course there is another option that you could consider, other then ndiswrapper, which is Linuxant Driverloader ([http://www.linuxant.com/driverloader/](http://www.linuxant.com/driverloader/)).  I used this WAY back when the solutions for wireless were fewer and far between, and it worked flawlessly.  The big downside to it is that you do need to update the package EVERY time you update the kernel, which is a hassle, but right now it might be an option that I'll pursue if I continue to experience issues with this wireless card.

---

### Post by bg1256 on 2007-10-15
I've had to reinstall the ndiswrapper driver with every new version of Ubuntu (from Dapper to Feisty) that I've used so far, and I anticipate doing the same when Gutsy comes out in a few days.

That is a pain as well. 

But, with my limited budget right now (full-time student), the computer to which I linked might be the only one I can afford.  It seems great for what I need, but I may have to deal with some of thes frustrations of ndiswrapper to get what I want.

Oh well, maybe another solution will develop to adapt to this hardware in the not-too-distant future.

---

### Post by bg1256 on 2007-10-15
I went ahead and purchased the computer - it definitely does have broadcom.

Ah well.  Buying the hardware for the price was definitely worth it for me, even if I have to do some tinkering to get Linux to work well.

Anyone ever have their laptop buttons not work to dim their screen?  Didn't work on the live cd... hoping it will work once it's done installing, though.

---

### Post by KCPokes on 2007-10-16
I have the MX8738 and the function buttons do work for dimming and brightening the screen, although they can be a bit flaky.  

In regards to the wireless, went home last night and did some checking (since I didn't have access to my laptop at work) and turns out that my card does NOT have a Broadcom chipset.  For one, it is a USB based (internal) wireless card, and not a PCI card.  It does work out of the box using the rtl8187 driver, which is built in (as far as I know because I don't recall doing anything to make it work...but who knows, I get in a groove sometimes).  That said, the built-in driver is awful.  Speed is slow and stability it non-existent.  I went ahead and blacklisted the driver last night and installed ndiswrapper, using the Windows 98 drivers for the Realtek 8187 wireless card (which in itself is hard to find).  After some fiddling it now connects on startup and hasn't dropped once since I've made the change, as opposed to the 10 times it would drop before (with the only way to reestablish the connection being rebooting the machine).  Additionally, and this is huge, the speed is noticeably faster.  Not sure if this is similar to the bmcxx drivers only running at wireless b or not, but it would appear as such.  I am definitely a much happier camper now as wireless was that one last thing that was just grating on me to get resolved before I could go entirely linux on this machine.  

Now if only I could get VideoReDo to work, via Wine, I'd never have a reason to use Windows.  Was hoping GOPChop would fill that void, but sadly it just doesn't cut it.  

Good luck with your new machine.  I bought my Gateway, as a business write-off, mainly due to it having a 17" display and being cheap, for what I was getting.  I must admit that I've not been disappointed since I made the purchase, other then finding out firsthand how much I truly refuse to use Vista as my next OS.

---

### Post by bg1256 on 2007-10-16
Thanks so much for your detailed response.

I have since determined that I, too, have a Realtek chipset, and I have located all the applicable windows drivers.

Also, there is a Linux driver on realtek's website, which I might try first, although I'm not exactly sure how installing that would work just yet.

One more question for you: did you get sound working out of the box?  I currently don't have it, and I have no idea how to get it.

Thanks again! Knowing that someone made progress on a similar machine is certainly encouraging.

---

### Post by KCPokes on 2007-10-16
Actually my sound did work out of the box, from what I recall.  I would suspect that you have an Intel sound chip as well, as it is all part of the integrated Intel solution (graphics and sound, for one).  What does your laptop show when you do a "lspci"?  

Here is mine:

```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
03:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

The key thing here is the Intel chipset for sound.  If yours is similar, should be able to work through this.  I have to run for now, but I'll check back tomorrow.

---

### Post by bg1256 on 2007-10-17
Thanks again for your help.

I actually do not have Intel integrated audio, which seems to be the problem.  I'm currently running Vista, so I can't run lspci.

And I am blanking on the name of the chip right now from memory... I'll try to post it again here.

And thanks again for your help with wifi.  I am going to wait until Gutsy comes out before I start tinkering, because I don't want to have to reinstall everything again in two days.

---

