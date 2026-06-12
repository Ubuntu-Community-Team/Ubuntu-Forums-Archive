---
title: "Cannot Reinitialize Orinoco PCMCIA After Eject"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by elcasey on 2007-01-07
I'm having a very strange problem with my Orinoco PCMCIA card not being recognized if it is ejected and reinserted.

The usual situation consists of my running Kismet for a wardriving session or just out of curiosity at home and, because I have a pigtail antenna for it, I usually ejected the card when I was done, rather than simply removing the antenna (which I've started doing).

My usual "shutdown" procedure for the card consists of a [FONT="Courier New"]sudo ifconfig eth2 down[/FONT]. After reading some FAQs and howtos re: PCMCIA issues in Linux, I began adding [FONT="Courier New"]cardctl eject[/FONT] before physically ejecting the card.

Here's the problem: Once I physically eject the card, it refuses to be recognized again until I reboot (with the card *out* of the PCMCIA slot). After reboot I simply insert the card, type [FONT="Courier New"]sudo ifconfig eth2 up[/FONT] and *et voila!* I have a working Orinoco card again.

Here's a reading of its *iwconfig* entry when it's working: ```
eth2      IEEE 802.11-DS  ESSID:""  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:0
```

The error message I get when it won't reinitialize the card is something along the lines of "Error: eth2 does not exist." It's not an exact error message, but I don't really feel like ejecting the card at the moment.

After some advice from inhabitants of #ubuntuforums and dragorn of #kismet (both on Freenode) I messed around with *modprobe* a lot (I was never able to remove a pcmcia module because I always got an error that they were in use) to no avail. I also tried adding eth2 to my /etc/network/interfaces file, but upon [FONT="Courier New"]sudo /etc/init.d/networking restart[/FONT] I was informed, once again, that eth2 did not exist.

I have no idea why this happens but it's **extremely** annoying to have to reboot at least once per day to get this card working again after having ejected it.

HELP! ](*,)

---

### Post by elcasey on 2007-01-07
No one knows anything about this? I'll give it another day and then try cross-posting to a hardware subforum.

---

### Post by tturrisi on 2007-01-07
If I'm not rebooting I always deactivate my orinoco using net-admin in gnome, then remove the card.  Kismet will also sometimes leave the card in an unworking state when it closes, which is a known issue w/ kismet.  Kismet fails to bring the card out of monitor mode and then the card cannot be used for anything at all at that point unless one reboots.  Kismet never seems to do that w/ my atheros cards though, only my agere orinoco.

---

### Post by elcasey on 2007-01-07
Thanks for the feedback. I haven't tried using net-admin, which I will try now. If it's simply an issue with the Orinoco/Hermes I chipset, then I'll just have to accept that (or reformat and dual-boot with XP for wardriving, which I'm seriously tempted to do).

Hopefully net-admin will "cut me some slack" and alleviate the problem. I just found it rather inconceivable, honestly, to find a problem that needed constant rebooting in an OS that prides itself on insane uptime.

Thanks again! :)

---

