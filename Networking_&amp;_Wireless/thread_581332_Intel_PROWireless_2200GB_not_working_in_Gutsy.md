---
title: "Intel PRO/Wireless 2200GB not working in Gutsy"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by FredDC on 2007-10-19
I have an Intel PRO/Wireless 2200GB wireless in my ACER laptop. I have just installed Gutsy Gibbon on it, but I cannot seem to get the wireless working. I have installed the 2 previous versions of Ubuntu and it has always worked out-of-the-box.

Anyone have an idea about what is going wrong?

---

### Post by noob12 on 2007-10-19
What model of Acer laptop do you have?

---

### Post by codedmin on 2007-10-19
Same problem here with asus W6A...

I can put wireless work with wicd... but if gutsy is final this sould have been fixed before release...

---

### Post by FredDC on 2007-10-19
> **noob12 said:**
> What model of Acer laptop do you have?

I have an ACER TravelMate 8000.

---

### Post by A L G A on 2007-10-19
> **codedmin said:**
> Same problem here with asus W6A...

I can put wireless work with wicd... but if gutsy is final this sould have been fixed before release...

Hi at all!
I've the same problem but I experienced a strange thing ... i tried to configure the ipw 2200bg manually by setting static ip and some times it works but strangely it "opens" only 1 site at time.
for example one time it worked only wit "www.google.com", mail.google.com didn't work ....

I tried wicd, it says that i'm connected to my AP but it doesn't load the webpages again.

---

### Post by MegaJim on 2007-10-19
I've got an Acer Aspire 1360 with an i2220 [Airconn Inprocomm IPN 2220] Running the XP Driver through NDISwrapper.

In 7.04 network manager scanned for networks properly and no major issues.

After updating to Gutsy I reinstalled NDISwrapper and reinstalled the i2220 XP driver.  After this, the network manager applet no longer seems able to pickup any networks in roaming mode where previously there were 4-5 in my area.

I can connect manually through the wireless, however, but I think this indicates some problems.

---

### Post by FredDC on 2007-10-19
Is there any official word on these problems yet? It seems alot of people are having similar difficulties with their wireless they didn't have in older versions of Ubuntu. Something broke, but what?

---

### Post by noob12 on 2007-10-20
FredDC: can you post the output of 
```

sudo lshw -C network

```

---

### Post by Qu4k3R on 2007-10-22
> **noob12 said:**
> FredDC: can you post the output of 
```

sudo lshw -C network

```

What should I do if I get some message saying my wireless board is 'unclaimed' ?

> 
PCI (sysfs)  
  *-network:0 UNCLAIMED   
       description: Network controller
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=64 maxlatency=24 mingnt=3


---

### Post by noob12 on 2007-10-22
It should be claimed by the ipw2200 driver which is distributed as part of the kernel image.

Can you post the output of **lspci -nn** ?

Do you see any errors from the ipw2200 driver  in your **dmesg** output soon after your boot ?

---

### Post by pasipasi on 2007-10-23
Copy all the files from /lib/firmware/2.6.22-14-generic to /lib/firmware/2.6.22-14-386 and re-modprobe ipw2200. It should then work. I found this solution from a bug report at launchpad.

```
sudo mkdir /lib/firmware/2.6.22-14-386
sudo cp /lib/firmware/2.6.22-14-generic/ipw2200* /lib/firmware/2.6.22-14-386/
sudo modprobe ipw2200
```

---

### Post by fj401971 on 2007-10-27
I believe this helped.  

I also noticed that my hardware switch works even though the light does not.  This is on an Acer TravelMate 8000.

---

### Post by hantabaru on 2007-11-02
Hi

Just thought I would add something to this thread. I have an acer travelmate 8000 as well and the same problem exist. However if I switch the wifi off and on again with the wifi button on the laptop, it connects no problem to my network. I didn't have problems with previous installations either. I haven't had a chance to try this fix this yet (I'm at work), but seeing as I can get it working it's not a big problem.

---

