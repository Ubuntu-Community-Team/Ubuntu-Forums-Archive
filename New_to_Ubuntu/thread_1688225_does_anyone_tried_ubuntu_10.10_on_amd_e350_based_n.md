---
title: "does anyone tried ubuntu 10.10 on amd e350 based netbook?"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by pft0 on 2011-02-15
i installed ubuntu on a usb flash drive, which can boot my core2duo notebook with ati 3470 display, and phenomIIx4 with ati 5770 display, also could boot my atom netbook, it it cannot boot into my hp dm1 with amd e350 apu.

---

### Post by Paqman on 2011-02-15
There seem to be other people on the internet who've been able to install Ubuntu onto that netbook. Have you checked in the BIOS to make sure it's set to boot from USB? I found one page that says booting from USB is very unreliable, you may want to give it a couple of tries.

---

### Post by pft0 on 2011-02-15
booting from usb is not a problem for me, and i forgot to metion mine netbook is hp pavilion dm1 with amd e350 apu.
my problem is that it will hang just before loading the login scrren, i saw some crap dotted line on sceen but i can't alt+f1 to the terminal, so i think it is hanged.
sorry for my bad english

---

### Post by jerry6185 on 2011-03-03
Installation went smoothly for me. On an Acer Aspire 5253-BZ480 the only problem it has its that their is water mark that says "AMD unsupported hardware" after i installed the AMD driver.
By the way that laptop is on sale at staples for 379.00
[http://www.staples.com/Acer-Aspire-AS5253-BZ480-15.6-Laptop/product_918744](http://www.staples.com/Acer-Aspire-AS5253-BZ480-15.6-Laptop/product_918744)

---

### Post by uRock on 2011-03-03
> **pft0 said:**
> booting from usb is not a problem for me, and i forgot to metion mine netbook is hp pavilion dm1 with amd e350 apu.
my problem is that it will hang just before loading the login scrren, i saw some crap dotted line on sceen but i can't alt+f1 to the terminal, so i think it is hanged.
sorry for my bad english
Have you tested the iso image to make sure it is good?

---

### Post by jchiso on 2011-03-03
> **jerry6185 said:**
> Installation went smoothly for me. On an Acer Aspire 5253-BZ480 the only problem it has its that their is water mark that says "AMD unsupported hardware" after i installed the AMD driver.
By the way that laptop is on sale at staples for 379.00
[http://www.staples.com/Acer-Aspire-AS5253-BZ480-15.6-Laptop/product_918744](http://www.staples.com/Acer-Aspire-AS5253-BZ480-15.6-Laptop/product_918744)

I had the same experience.  You have to install the newer 11-2-x86.x86_64 Catalyst driver.

---

### Post by T0OL on 2011-04-07
I have dm1-300 with e350, I was able to install 10.10 via usb no problem. I too had graphics driver issue, but fixed it by getting the catalyst version from amd website for the e350 processor.

initially ubuntu did not detect the wireless card, found solution else where on forum. required download of the ralink drivers and adding a line to some data file.

Problem now.. unable to join hidden ssid networks. it actually joins, but i cant get out. unable to ping anything except lo. anyone else have same problem?

---

### Post by ehpikay on 2011-04-07
I'm trying to install Ubuntu 10.10 on my HP dm1 via a USB flash drive. I followed the instructions to create it from Ubuntu's website. I changed the boot order in BIOS (put USB key/drive at the top), but it would boot into Windows anyway. When I do an F9 to see the boot options I have, I only see Notebook Hard drive, and do not see an option for USB. Strange! Has any one come across this before?

@T0OL, how did you go about installing ubuntu on a dm1?

---

### Post by T0OL on 2011-04-08
> **ehpikay said:**
> @T0OL, how did you go about installing ubuntu on a dm1?

created the usb live disk using a windows machine following online instructions. 
1) put in laptop
2) power on
3) hit esc
4) chose f9
5) mine says note book harddrive and cbm flash disk, chose flash disk
6) follow install

with the exception to finding and installing proper e350 drivers and ralink 539f, everything was pretty simple. still am unable navigate the network.

I can connect to a hidden ssid
I can get an ip address
I cannot load a web-page
I cannot ping either

---

### Post by walt.smith1960 on 2011-04-08
Not an amd e350 but I have a desktop with an AMD785 chipset that won't boot from a USB key. BIOS is set properly.  A ThinkPad R61 & AMD desktop with a 740 chipset that boot fine from the same USB key.  I wonder if there's something in newer AMD chipsets that causes problems booting from USB drives?

---

### Post by ehpikay on 2011-04-09
> **T0OL said:**
> created the usb live disk using a windows machine following online instructions. 


@T0OL Which instructions did you follow. I have tried following 3 different sets of instructions, and none of them seem to work. Can you please give me the link to those instructions?

Thanks

---

### Post by antikyte on 2011-05-03
@ehpikay - I managed to get wireless networking operational on my e-machines e350 ( 32-bit version of Ubuntu 10.04). 
The instructions are at [http://wp.me/pweWl-fj](http://wp.me/pweWl-fj) and include creation of a live disk using the Ubuntu Startup Disk Creator utility.

Hope you find them useful.

Mike

---

### Post by ndak on 2011-05-06
I bought an Acer 15.6 inch laptop with the e350.  I could not get lucid installed but managed to install desktop edition of v.10.10.  The alternate installation of v.10.10 would not install, giving an unsupported kernel error.  I ran out of disk space after installation of the desktop version because of huge logging of multiple errors (90 GB accumulated during installation and updating.)  I decided the kernel does not yet support the e350 and I returned the Acer laptop.

Dennis

---

### Post by Fraoch on 2011-05-06
> **ndak said:**
> I decided the kernel does not yet support the e350 and I returned the Acer laptop.

Obviously it's too late now, but you should have tried 11.04 (Unity issues notwithstanding) as it has a newer kernel - actually just about cutting edge right now - 2.6.38.  kernel.org shows that 2.6.38.5 is the very newest stable.

This may have had a big influence - the AMD E350 is still very new.

---

### Post by T0OL on 2011-05-16
i have 11.04 installed on and everything works great, it was updated from 10.10 by ubuntu update manager.

I am still unable to surf the network, when connected to a hidden ssid. otherthan that networking works great.

anybody have a fix?

---

