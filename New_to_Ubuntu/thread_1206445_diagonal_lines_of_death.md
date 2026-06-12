---
title: "diagonal lines of death"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by dimitriv on 2009-07-07
When a certain cd is in the cd drive, the screen goes white with beige/black diagonal lines going across the screen, mouse and keyboard are unresponsive. machine appears truly hung as also no response from use of cd eject button.

On ubuntu is there an equivalent of windows ctrl+alt+del to try when a system or app is not responding?

I've never seen a cd render a machine so paralysed. I hadn't chosen to look at the cd or run files from it, it was just from being inserted in the drive.

Thanks

---

### Post by mikechant on 2009-07-07
There are various things you can try if the gui is not responding:

1/ Ctrl-Alt-F1 to get a console login screen, then you could use 'top' or 'ps' and 'kill' to get rid of any looping/stuck processes, or try a command line 'eject'. Ctrl-Alt-F7 gets you back to the gui screen.

2/ Restart the gui with ctrl-alt-backspace (or Altgr + sysrq + K if the first combo is disabled)

3/ Use the 'magic key' combo - hold down the ALT and SYSREQ* keys and type R E I S U B with a few seconds gap in between each letter**. This will perform a clean reboot. See [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key) for more. Note you're typing 'blind' here, but this combo should work in pretty much every case where the (non-gui) OS is still running.

* You may not have a seperate or marked sysreq key - use the print screen key instead if so.

** The few seconds gap between each letter command is very important otherwise you may (e.g.) end up rebooting before the filesystems have synced and get data corruption.

Out of interest, what is this CD you're having trouble with?

---

### Post by wpshooter on 2009-07-07
> **dimitriv said:**
> When a certain cd is in the cd drive, the screen goes white with beige/black diagonal lines going across the screen, mouse and keyboard are unresponsive. machine appears truly hung as also no response from use of cd eject button.

On ubuntu is there an equivalent of windows ctrl+alt+del to try when a system or app is not responding?

I've never seen a cd render a machine so paralysed. I hadn't chosen to look at the cd or run files from it, it was just from being inserted in the drive.

Thanks

Have you tried inserting this CD in another machine to see if you get this same behavior.

One thing that I would contemplate would be to check to see if there is a firmware (not driver) upgrade for your CD drive.

---

