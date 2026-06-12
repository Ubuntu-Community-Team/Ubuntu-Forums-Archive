---
title: "wireless Hardware block on HP Envy after going to 18.04 from dual boot"
date: 2018-08-16
forum: Networking &amp; Wireless
---

### Post by michael-tod on 2018-08-16
Had a working Win 10 / Linux Mint system on a HP ENVY dv7-7223cl Notebook, but decided to delete all partitions, wipe drive and "upgrade" to just Ubuntu 18.04.1 LTS.
After reboot got a perpetual wireless hardware switch block (i.e. light stays amber, airplane mode always on) 
     All [suggested "tricks" from HP's forums]("https://support.hp.com/us-en/document/c01891123") were tried (that can be done without windows) 
Spent a few days trying several solutions described in this forum without success... so wiped drive, installed Ubuntu fresh and updated/upgraded all via Ethernet...
still no change.  Stumped.  Any insights appreciated.  -Mike

current:  [https://paste.ubuntu.com/p/MYGyzTG23d/](https://paste.ubuntu.com/p/MYGyzTG23d/)

    Network controller [0280]: **Qualcomm Atheros AR9485** Wireless Network Adapter [168c:0032] (rev 01)
     Subsystem: Hewlett-Packard Company AR9485/HB125 802.11bgn 1×1 Wi-Fi Adapter [103c:1838]
     Kernel driver in use: ath9k
 
 0: phy0: Wireless LAN
     Soft blocked: no
     Hard blocked: yes

---

### Post by chili555 on 2018-08-16
The issue of HP wireless being inoperable because of a hard block and therefore the usual wireless key not toggling wireless on and off is long-standing. There are only a few things you can try.

First, try removing the helper module hp_wmi and then try to switch the wireless on with the key combination. 

You could also try:

```
sudo modprobe -r hp_wmi
sudo rfkill unblock all
rfkill list all

```
Second, check the user guide for your HP laptop and be certain that the wireless key combination you are using is correct. Be certain that you are not using Fn+F12, for example, if the user guide says it is simply F12. On the other hand, if you are certain you are using the correct sequence, try the *wrong *sequence as an experiment; i.e., use Fn+F12 (or whatever your sequence is) if the user guide says it’s F12 and vice versa.

Next, you can remove the card, tape off pin 20 and re-insert it: [https://ubuntuforums.org/showthread.php?t=2150597](https://ubuntuforums.org/showthread.php?t=2150597)

You can, if all these steps fail, file a bug report against the module hp_wmi: [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

Finally, in many, but not every case, a USB wireless will also be hard blocked for the same reasons. If you want to try one, be certain to try it within a return period.

I regret that there isn’t a better answer for HP laptops.

---

### Post by michael-tod on 2018-08-16
no joy from the  -r hp_wmi  

I thought it might be just a driver (kernel update) issue, since it previously worked (temporarily) until the first update happened.  but after the first reboot is when the hardware switch stayed amber (blocked).  e.g.  the HP fix was a driver issue:  "download and install the wireless hot key driver" (if all other options failed).

I'll try the tape on pin 20 trick next.  (btw, [the pic]("http://s24.postimg.org/6zlq6obmp/33athxe.jpg") didn't load, so can't tell if its same pin layout)
> remove the card, tape off pin 20 and re-insert it: [URL="https://ubuntuforums.org/showthread.php?t=2150597"]https://ubuntuforums.org/showthread.php?t=2150597
[/URL]in the article found this: 
 "had a gateway laptop that only worked intermittently with a broken  switch, even though everything was set to on in the BIOS. This fixed it!  My card had a few extra weird pins, but it was still second from the  right on the left side, facing upside down.  The diagram above seems a  little bit backwards - the left side will be big and the right small  when the card is upside down. But, pin-wise, it was correct for me.  Realtek card."


found [pic here]("https://web.archive.org/web/20150507095522/http://www.mp3car.com/attachments/wireless-communications/56148d1249724286-hacking-mini-pci-e-hsdpa-into-aopen-i45gmt-hd-board-sim_to_mini_pci_express.jpg").  so question is: would the Realtek & Qualcomm Atheros Mini-PCIcards have same pin layout?

---

### Post by chili555 on 2018-08-16
If it is identical in layout to all mini-PCIe cards, like this: 

[IMG]http://www.jarzebski.pl/files/images/mask-pin-20-2.jpg[/IMG]...then I suspect so. If you can easily remove it and try it, you will soon find out.

---

### Post by michael-tod on 2018-08-17
thanks again.  I tried it.

and found out the answer is yes!  that worked.  forced harware block disabled.
but...
I'd still prefer a "kernal driver" fix, instead of this hardware bypass. 

 call it  1/2 solved.  :wink:

thanks for the suggestion.

---

### Post by chili555 on 2018-08-17
I suggest that you proceed with filing a bug report against *hp-wmi *as I outlined above.

Even if not ideal, I'm glad that the wireless is working.

---

