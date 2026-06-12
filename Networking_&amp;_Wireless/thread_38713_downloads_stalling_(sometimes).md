---
title: "downloads stalling (sometimes)"
date: 2005-06-01
forum: Networking &amp; Wireless
---

### Post by eferrari on 2005-06-01
I am having a problem with certain large ( > 500K) downloads stalling all the time.
I have tryed many things to debug the issue but now I need some help. Here are some points to consider: (I am running an up to date install of 5.04 on a Shuttle SN41G2)

1) It appears to be application independent. It happens using firefox, synaptic, wget, whatever.

2) Downloads that do stall will always stall. For Example, attempting to download flash player will always stall but attempting to download eclipse never fails.
Always Fails: [http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash) 
Never Fails: [http://www.eclipse.org/downloads/download.php?file=/eclipse/downloads/drops/R-3.0.2-200503110845/eclipse-SDK-3.0.2-linux-gtk.zip&url=http://gulus.USherbrooke.ca/pub/appl/eclipse/eclipse/downloads/drops/R-3.0.2-200503110845/eclipse-SDK-3.0.2-linux-gtk.zip&mirror_id=114](http://www.eclipse.org/downloads/download.php?file=/eclipse/downloads/drops/R-3.0.2-200503110845/eclipse-SDK-3.0.2-linux-gtk.zip&url=http://gulus.USherbrooke.ca/pub/appl/eclipse/eclipse/downloads/drops/R-3.0.2-200503110845/eclipse-SDK-3.0.2-linux-gtk.zip&mirror_id=114)  

3) When downloads do stall they seem to usually stall somewhere between 500 - 600KB.

4) I have an NForce2 chipset. 

5) $ uname -a
Linux shuttle 2.6.10-5-386 #1 Fri May 20 13:52:48 UTC 2005 i686 GNU/Linux

6) I don't think it is the driver: I was originally running forcedeth. Suspecting the driver, 
- I compiled nvnet. 
- modprobe -r forcedeth
- modprobe nvnet
- used lsmod to confirm forcedeth NOT running and nvnet IS.
- tested a download and STILL saw the problem.
I then switched from using the onboard ethernet to using a USB-Ethernet adapter and STILL saw the problem.

I don't think forcedeth or nvnet are the problem, but I don't understand enough about networking to debug any further. 

Does anyone have any idea what I should be looking into? (or what might be wrong)
(Thanks for reading a long post and thanks in advance for any help)

---

### Post by thrift on 2005-06-01
I would suggest trying to transfer a large group of file between this machine and another local machine.  

If it doesn't fail with that I'd look to your ISP/Internet gateway as to what's up with their connection.  

If it does fail I'd look towards possibly the cable(if it's the same one you've been using for internet access) or the driver.

---

### Post by mwprice on 2005-12-30
I also was seeing large downloads stall.  I found that wget was able to retrive a large file.  I set -T10 (timeouts to 10 seconds) and -t0 (keep retrying).  It seems that the stalls occur when a byte is in error.  Wget took 19 tries to get a 23MByte file.  I wonder why that is happening.  Windows downloads the same file just fine.

M Price

---

