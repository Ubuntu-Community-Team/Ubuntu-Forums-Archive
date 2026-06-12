---
title: "wlan0 disappears after reboot"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by natille on 2007-11-05
I recently installed Gutsy Gibbon on a desktop that resides very far from my router, but has a USR5416 wireless PCI card in it. I managed to install the Windows driver and ndiswrapper and almost got connected to my router when the system froze and caused me to need to reboot.

Upon reboot ifconfig and iwconfig would not show me wlan0, but ndiswrapper -l would tell me that the driver was installed and the device was found. So I searched around for a bit to no avail and since I had just installed, I reinstalled the entire OS to try to resolve the problem quickly.

I started the process over and once it looked like I'd finished installing the driver, I intentionally restarted the computer (via menus, not by kicking the reset button) to try to cement the changes. Upon reboot, I had the same problem I'd come across the first time with the frozen system reboot.

ndiswrapper knows the card is there but I can't get it to work.

Please help!

---

### Post by luisromangz on 2007-11-05
You have to make ndiswrapper driver load at boot. There are problably better ways to do so, but last time I added an entry in the /etc/rc.local, before the exit 0:

modprobe ndiswrapper

---

### Post by natille on 2007-11-05
Shouldn't wlan0 come back when I "sudo modprobe ndiswrapper"? It doesn't currently. 

Is there anything else I can try to get it to come back before I start trying to make something load that I can't even load outside of boot up?

Thanks!

---

### Post by AstarothCY on 2007-11-06
Add ndiswrapper to /etc/modules.

---

### Post by natille on 2007-11-06
> Add ndiswrapper to /etc/modules.

Done. But no help to getting wlan0 to come back... Any other ideas?

---

### Post by kubel on 2007-11-06
Adding *modprobe ndiswrapper* to /etc/rc.local as luisromangz suggested worked for me. It should work if you run that command manually. Not sure what's happening in your case.

A simple solution I had before asking ndiswrapper to load at startup was to use ndisgtk to remove and then re-install the driver (very quick and easy to do). After about 15 seconds, Ubuntu connected to my default AP just as it should. 

There is a confirmed bug in Gutsy that occurs when your wireless switch is off at boot that can cause wlan0 to disappear regardless of whether or not you have it on or off after it boots. So make sure your wireless is switched on before booting. Bug is #121415 at launchpad.

---

### Post by natille on 2007-11-07
So, here's my latest status.

If I run "sudo modprobe ndiswrapper" I just get returned to the prompt and nothing has changed. I've tried repeating this several times, with much hope, so one question about this: should I see anything returned to me when I modprobe ndiswrapper? The fact that it sends me back to a prompt with no "congratulations, you've started ndiswrapper" (or something to that effect) seems a little odd.

I also was searching around and found "lspci -nn | grep Network" which tells me that my card is unclaimed, which I'm not sure how to claim it now.

The first time I installed it and had this problem, I had installed using ndisgtk, and so I tried to uninstall using ndisgtk, but it refused to allow me to uninstall that way. I could click the button, but it would not go away.

My card doesn't come up under System > Administrator > Network either, which probably has something to do with the unclaimed deal.

Also, I'm not sure what is meant by 'turning on my wireless before boot', I have no switches on my PCI card and my wireless network is up and running all day and all night, so I'm not sure what I'm intended to switch.

Thanks for all the suggestions so far!

---

### Post by dented59 on 2007-11-07
I've had similar problems with my USB Netgear WPN111.

try running ps aux | grep ndis to see if ndiswrapper is loaded. If it is and you still can't see your card you could try sudo rmmod ndiswrapper to unload ndiswrapper, and then run sudo modprobe ndiswrapper again. If your luck is anything like mine though it's about a 50-50 chance that you'll get a systemwide hang and be forced to reboot.

So far I've had no luck figuring out what is causing the crashes. Also sometimes I will lose connection and be completely unable to reconnect without rebooting. I suspect that when that happens something has caused ndiswrapper to lock up. Trying to unload it or reboot results in a systemcrash.

Also, if you have Network manager installed, try disabling it. Worked a lot better for me when I did.

---

### Post by natille on 2007-11-07
> **dented59 said:**
> 
try running ps aux | grep ndis to see if ndiswrapper is loaded. If it is and you still can't see your card you could try sudo rmmod ndiswrapper to unload ndiswrapper, and then run sudo modprobe ndiswrapper again. If your luck is anything like mine though it's about a 50-50 chance that you'll get a systemwide hang and be forced to reboot.


"ps aux | grep ndis" returned:
```

root     5527  0.0   0.0            0            0 ?         S<    20:37     0:00 [ndis_wq]
root     5528  0.0   0.0            0            0 ?         S<    20:37     0:00 [wrapndis_wq/0]
natille  5559  0.0   0.0            2972        748 pts/0    R+    20:40     0:00 grep ndis

```

I'm not really sure what that's telling me.

As for rmmod ndiswrapper -> modprobe ndiswrapper, no crash, but also no positive results. Again doing either gives me no feedback, which I'm not even sure if I should be getting feedback, but it would be nice...

Also, I misremembered the command that told me that the card was unclaimed when I mentioned that earlier; I used "lshw -C network", not "lspci -nn | grep Network", sorry. I figure clarifying might help something.

Thanks again for all the suggestions!

---

### Post by natille on 2007-11-12
No more suggestions, it would seem...
I may just steal my beau's Gigabyte wireless card and give it a go.
I might be back.

---

### Post by natille on 2007-11-21
So, my wireless woes are slightly resolved. I figured out only once I installed the Gigabyte (Ralink) card that both cards are recognized by the system without ndiswrapper.

Ever since, I've had both cards in, but sometimes they both have difficulties connecting to my router, and other times everything works fine. It usually has difficulty after booting up, but after being on a while it seems better.

Sometimes the computer will switch which card it is using and to an AP where it is getting no signal.

I still have no idea why ndiswrapper was basically eating wlan0...

---

