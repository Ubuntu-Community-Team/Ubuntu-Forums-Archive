---
title: "metacity, gnome-pannel, wireless not starting up"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by Julian Lewis on 2009-06-19
Hi,
   I have a ACER one with a hard-drive, it works out of the box. My daughter has an ACER one 16Gb flash memory version, with linpus, which I have replaced by 9.04 Remix Netbook.
On my ACER with hard drive it works perfectly, however with the one with 16-GBytes flash there are some startup problems. I think the flash version is a bit slower...

On a reboot the window manager metacity is not running, and obviously gnom-pannel, consequently I suspect that is why wlan isn't available.

I start a terminal and type ....

metacity &
gnome-pannel &

and I have a nice Ubuntu classic desktop with workspaces enabled. I have no fancy compiz features switched on. And no error messages.

When I do a dmesg I don't see anything special that might be the reason for a crash, I think the startup is corrupt some how.

What command do I need to start the wireless lan manager ? As a last resort I can just start it by hand...

By the way all latest Ubuntu updates are applied, its running 2.6.28-13-generic 

Can some one tell me what to do to repaire the startup sequence, I guess I could install a shell script but that's not very pretty. And most importantly how is the wlan manager restarted.

In addition when this happened to me the first time, I just re-installed from my USB key a second time.... still thae same problem. It looks like an error due to the slower startup may be the cause.. perhaps a slack handful of sleeps in the startup may help.

Thanks for any advice.

---

### Post by Julian Lewis on 2009-06-19
more information ....

well I switched on remember application settings, and that fixed the window manager .... why who knows , but now I got gnome-pannel and metacity running. .....
Still no wlan.
Then I remembered that the wlan worked just fine from the USB image... so I booted from the key again. Sure enough wlan worked just fine.

Then I rebooted from the installed system... guess what wlan works now.

Looks like the hardware was not recognised, but booting from the key puts it in a good sate after which it gets recognised.

How can I make sure this won't reocur.

---

