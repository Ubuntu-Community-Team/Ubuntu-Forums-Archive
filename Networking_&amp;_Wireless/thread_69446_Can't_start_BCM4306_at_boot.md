---
title: "Can't start BCM4306 at boot"
date: 2005-09-26
forum: Networking &amp; Wireless
---

### Post by imrazor on 2005-09-26
I've gotten my wireless card to work with Kubuntu 5.04 i386, but can't seem to get it to activate at boot. When attempting to load the Windows driver via ndiswrapper, I received a message that ndiswrapper was forcing RadioState|1. Later I found that I had to manually edit config files in /etc/ndiswrapper and change RadioState to 0 to get the card to work at all. The problem is that whenever ndiswrapper is loaded now, it automatically forces the wireless card off. Thus when the system boots, Ubuntu can't configure a disabled wireless card. So I have to manually activate the card with a keyboard button, run iwconfig then dhclient to set everything up. The wireless card is a Broadcom BCM4306 (aka MaxPerformance 54g) and the laptop is an eMachines M6805.

---

### Post by dgbauer on 2005-12-25
I am running Ubuntu 5.10 and I too have the M6805...  I just got my wireless card working today after much trouble, but it is working absolutely great!

Are you running the 64-bit or the 32-bit version of Ubuntu, and what version is your ndiswrapper?  I just need a little more info to see if I can help at all...

---

### Post by imrazor on 2005-12-25
I found that the problem was a setting in the BIOS. I've since set it to Radio On and upgraded to Kubuntu 5.10. No more problems. BTW, I'm running the 32-bit version. I spend a lot of time watching video, and I wasn't sure if the 64-bit version could load the 32-bit Windows codecs for xine/kaffeine.

I've also had a lot of problems with my M6805 just shutting down for no apparent reason. I found the fix was to set the power profiles to powersave for battery and to max performance for AC. Have you had or heard of similar problems with other M6805's?

---

### Post by dgbauer on 2005-12-26
I have never had mine shut down for no reason...  But I have had it turn off the screen for no reason...  [Fn]+F4 wouldn't touch it either...  

Congrats on the wireless working too!  I almost forgot that I had to fart around in the BIOS before mine was working too.

---

