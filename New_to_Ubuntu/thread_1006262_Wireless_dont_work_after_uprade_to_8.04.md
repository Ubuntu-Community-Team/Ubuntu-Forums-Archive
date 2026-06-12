---
title: "Wireless dont work after uprade to 8.04"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by Dan Z on 2008-12-09
Hello- I have a Gateway MX3225 laptop. Under Ubuntu 6 wireless worked.  After upgrade to 8.04, no wireless.

It seems the card is recognized, but there is no driver. Assuming I am correct---how do I install the correct driver?

Sudo lshw==>

=sdhci

        *-network:0 UNCLAIMED

             description: Ethernet controller

             product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller

             vendor: Realtek Semiconductor Co., Ltd.

             physical id: e

             bus info: pci@0000:00:0e.0

             version: 20

             width: 32 bits

             clock: 33MHz

             capabilities: pm cap_list

             configuration: latency=0 maxlatency=64 mingnt=32


No driver??

Then I ran

lspci -v | less===>

00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

        Subsystem: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller

        Flags: medium devsel

        I/O ports at 2800 [disabled] [size=256]

        Memory at 58002000 (32-bit, non-prefetchable) [disabled] [size=512]

        Capabilities: <access denied>


Any help appreciated!!! Thanks Dan

---

### Post by stevoo on 2008-12-09
it has been a long time, but i believe you need to re enable the hardware or something like that.

youll need to have an ethernet connection go to System->administration-> hardware drivers and click and enable it, it will download the driver and that will be it ... hopefully that is the problem

---

### Post by Dan Z on 2008-12-09
> **stevoo said:**
> it has been a long time, but i believe you need to re enable the hardware or something like that.

youll need to have an ethernet connection go to System->administration-> hardware drivers and click and enable it, it will download the driver and that will be it ... hopefully that is the problem
Thanks for the response. When I do as stated, the Hardware drivers window opens and says "no proprietary drivers are in use on this system". So no go on that one. 

I think I need to reload the normal driver, don't know how. 
Thanks dan

---

### Post by jedi-penguin on 2008-12-09
Try ndiswrapper, it loads wireless driver for windows into linux. There are lots article on this even on ubuntu's help page. So go to the office website of your wireless card provider and download the driver. Then install ndiswrapper and load up the driver.

---

### Post by Dan Z on 2008-12-11
Thanks I got it working. Installed ndiswrapper through add/remove applications. 
Downloaded driver from Realtek site.

When I ran ndsiwrapper I had to choose which WIndows version driver to use. XP was not accepted as a valid driver, Vista 32 bit did not work. Tried win98 and it worked!

I now have a fully functioning laptop. 

Next to figure out how to network to my Ubuntu desptop.

Thanks again, Dan

---

### Post by CoCoKnots on 2008-12-11
I ran into the same problem after the last upgrade for Hardy 8.04.1 and found that quite a few others were having the same issues. I was certain the problems were connected with my computer from the previous download.
I still believe they stem from the download. However it appears they may have effected the 'soft' switches in my router. I found the problem by accident. You may want to check out my thread... [http://ubuntuforums.org/showthread.php?t=1000871&highlight=CoCoKnots&page=3](http://ubuntuforums.org/showthread.php?t=1000871&highlight=CoCoKnots&page=3) ... Hope this helps. It was driving me a little crazy.

---

