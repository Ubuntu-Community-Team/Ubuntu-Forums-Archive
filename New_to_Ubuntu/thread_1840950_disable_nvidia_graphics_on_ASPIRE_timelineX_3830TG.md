---
title: "disable nvidia graphics on ASPIRE timelineX 3830TG"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by justldd on 2011-09-08
Hey, I have been able to solve most of the problems I had with this laptop, but I am unable to get a decent amount of battery life.
I think the reason for this is that the nvidia optimus graphic card is on. How can I turn it off so that I only use the integrated i3 graphics?

I could post/upload any files, as needed. (lspci output, etc)

ps: i tried looking into similar threads, but older/other aspirex computers have ATI graphics.

---

### Post by TeoBigusGeekus on 2011-09-08
I think it should be done through bios.

---

### Post by snip3r8 on 2011-09-08
You could instead of disabling ,change your power mizer settings in the nvidia settings manager.

---

### Post by justldd on 2011-09-09
snip3r8, I think that would mean installing the proprietary drivers and then using the 'battery efficient' profile for nvidia cards but... my intuition tells me that doing so is not as efficient as completely turning off the nvidia card and using the one from the i3.

one possible solution I found online was..
"
sudo su
echo "OFF" > /sys/kernel/debug/vgaswitcheroo/switch"

but it doesn't work since I dont have 'vgaswitcheroo' in the debug folder...

---

### Post by justldd on 2011-09-12
broken screen...
I think I might change this into a headless server /media server for media playback and stuff...(...)

*sighs

---

### Post by anewguy on 2011-09-12
> **justldd said:**
> broken screen...

*sighs

Remember - when frustrated, use a foam rubber hammer!!  ;)

Dave ;)

---

### Post by wadd92 on 2011-09-12
I would either disable it though the BIOS or blacklist it by hitting /etc/modprobe.d/blacklist.conf in terminal and appending the correct driver which is most likely either nvidia or nouveau. BUT disabling the driver as far as I see it wont affect its power consumption, to do that either use the NVIDIA controll panel or completly remove the graohics card completly

---

### Post by madjr on 2011-09-12
> **wadd92 said:**
> I would either disable it though the BIOS or blacklist it by hitting /etc/modprobe.d/blacklist.conf in terminal and appending the correct driver which is most likely either nvidia or nouveau. BUT disabling the driver as far as I see it wont affect its power consumption, to do that either use the NVIDIA controll panel or completly remove the graohics card completly

its a laptop so it cant be removed

---

