---
title: "Extremely Weak Wireless Signal"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by MrTripi on 2008-08-12
Trying to figure out why my signal is so weak when the router is only 1 room away.  Down/Up speed is great, roughly 13000kbps/2000kbps.  Unfortunately I only have an average connection signal of 40%.  I have a  Linksys WRT54G/GS router with the hacked DD-WRT bios.  I've boosted the XMIT to 78mW-still no good.  

Another feature I've noticed in this bios is that it displays the Signal/Noise/SNR ratio.  Not entirely sure what this indicates, however I'm gonna go out on a limb and assume noise might cause the signal to weaken.  


signal/noise/snr         Signal Quality
-66,  -98   32             32%            

man, what's the deal with this :/

---

### Post by MrTripi on 2008-08-12
:/

---

### Post by finer recliner on 2008-08-12
make sure your router is not within a few feet of any other radio devices such as a cordless telephone or baby monitor.

---

### Post by Onesimus on 2008-08-12
> **MrTripi said:**
> 

signal/noise/snr         Signal Quality
-66,  -98   32             32%            

man, what's the deal with this :/

The SNR (or Signal to Noise Ratio) is a measure of how strong the signal is compared to the noise level.  The numbers you have provided would indicate that the noise is -98dBm, the signal is -66dBm, and the SNR is 32dB (= -66 - -98 ).  A SNR of 32dB seems quite a strong signal.  However, SNR is only one measure of the quality of the signal.  The wireless modem will be receiving multiples copies of the same signal from the router because there will be a large number of possible paths that the signal may take to arrive at your PC (e.g. bouncing off floors, walls, etc.).  It can be that moving the router slightly may improve performance - also try to remove mirrors at either ends (these serve to reflect the signal and hence increase the number of dominant signals).

Hope this helps

---

### Post by Method of Rhythm on 2008-08-12
I am also having a similar issue but only when I boot into Linux.  While on Mac OSX I will have a full 5 bars of reception with maximum connection speed while Ubuntu/Linux is only giving me 1-2 bars with 10% reading.  Could someone help me out on this?

---

### Post by MrTripi on 2008-08-26
I know it's nothing near the monitor. I  can actually walk upstairs(which is farther away) and end up with a signal strength of 90%

---

