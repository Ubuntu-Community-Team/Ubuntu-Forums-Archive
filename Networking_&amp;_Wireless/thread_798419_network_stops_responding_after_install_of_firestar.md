---
title: "network stops responding after install of firestarter"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by cdmdotnet on 2008-05-18
Since i installed firestart my network access now completely dies, how it's not right away, it doesn't seem to be after a set period of time.

it didn't matter if i had the' firewall' active or not. Infact it hasn't even made a difference now that i've removed the program. 

if i issue a "/etc/init.d/networking restart" it just hangs after stopping and restarting the firewall... for a second time (it seems to stop, then start, then stop then start the firewall). But as i said, it still happens even though i've now removed the software. Only resolution seems to be restarting the whole machine.

i cannot ping any machines in my network, traceroutes don't respond, no DNS resolutions, no internet.

I do seem to notice it after the screensaver has kicked in, it might also be after the monitor is turned off so is it possible that it's a power management issue? if so, how can i tell if power management is trying to shutdown my network cards?

I have the machine not to enter standby (its supposed to be running 24 / 7 - however this makes that irrelevant as it's not accessible now when the networking stop working).

I've running Hardy on a standard dell 73400. Any help would be great with a network (not usb) ADSL router.

---

### Post by cdmdotnet on 2008-05-18
I can now confim this is not a power issue, as this reboot only took 5 minutes after posting the above message for all networking to die.
ifconfig ethx up and down make no difference
/etc/init.d/networking restart also makes no difference with firestarter removed (although it does finish now and doesn't hang)

---

