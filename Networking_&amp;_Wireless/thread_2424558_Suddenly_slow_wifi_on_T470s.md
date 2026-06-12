---
title: "Suddenly slow wifi on T470s"
date: 2019-08-10
forum: Networking &amp; Wireless
---

### Post by Cinemarxism on 2019-08-10
I have a Thinkpad T470s with some wifi issues on Ubuntu (18.04).

What usually happens is that the wifi connection suddenly becomes  really slow. I have not been able to find any constant pattern as  regards when this kicks in. Sometimes it's slow immediately after  startup. Other times the problem kicks in after an hour or so of usage.  On a few (rare) blessed days there will be no problems whatsoever.

No issues with Windows 10 on the same computer. Also no issues with my android phone or my wife's macbook and iphone.

I haven't really done any tweaking of my settings, besides setting the region (under "iw reg get") to "NO" (where I am located).

I know there are many threads on similar issues, but haven't found any  threads where the OP has the same laptop as I do. A bit wary of messing  things up if I just copy suggested commands from other threads, not all  that savvy when it comes to network issues.

I've ran the wireless info script from the stickied post, [here's the output]("https://paste.ubuntu.com/p/Ysw2d24jD6/").

---

### Post by chili555 on 2019-08-10
Is it slowing down because your router is set to auto channel select and the router just decided for whatever reason to change channels? Your paste shows that you are connected on channel 5. That's a pretty unusual channel to choose; usually, 1,6 or 11 are preferred due to overlap: [https://www.metageek.com/training/resources/why-channels-1-6-11.html](https://www.metageek.com/training/resources/why-channels-1-6-11.html)

---

### Post by Cinemarxism on 2019-08-10
Thanks for the suggestion. The router was indeed set to automatically select channel. I've now changed it manually to channel 6, will report back to see if the problem persists.

---

### Post by Cinemarxism on 2019-08-11
Okay, so that didn't really seem to fix the problem.

Still experiencing sudden, significant drops in speed, upload speed in particular, although I am not on channel six ([new paste here]("https://paste.ubuntu.com/p/WZVfdtYm4b/"))

Any suggestions for what else I might try?

---

### Post by chili555 on 2019-08-12
> although I am not on channel six Your paste disagrees:> Cell 01 - Address: <MAC 'Telenor4472ise' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Telenor4472ise"
<snip>

Let's try a few more tweaks. If your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

You might also try a driver parameter:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=8
```Any improvement? 

You might also try =1 or =2 or =4. Once you find a setting that helps, if any, make it persistent with:

```
sudo -i
echo "options iwlwifi 11n_disable=X"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```...where X is the driver parameter you found that fixes the issue.

---

### Post by Cinemarxism on 2019-08-12
A typo, the "not" should have been a "now".

Thanks again for the suggestions! I'll test it out any report back if the problem persists.

---

