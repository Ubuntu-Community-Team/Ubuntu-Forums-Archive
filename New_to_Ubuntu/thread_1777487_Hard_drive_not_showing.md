---
title: "Hard drive not showing"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by Super-Dan on 2011-06-07
So I have 11.04 Installed and I am very happy!

Now I am running a 40gb sata HDD to learn more about Ubuntu and to hopefully migrate fully to Ubuntu!

I have plugged an 80GB IDE hard drive now to store documents temporarily, switched the PC off plugged the drive in and restarted.

No sign of the Hard drive in Computer?

So what do I do then? Should it not be there automatically?

---

### Post by Autodave on 2011-06-07
> **Super-Dan said:**
> So I have 11.04 Installed and I am very happy!

Now I am running a 40gb sata HDD to learn more about Ubuntu and to hopefully migrate fully to Ubuntu!

I have plugged an 80GB IDE hard drive now to store documents temporarily, switched the PC off plugged the drive in and restarted.

No sign of the Hard drive in Computer?

So what do I do then? Should it not be there automatically?


If the drive is USB, try booting up to Ubuntu with the drive disconnected.  Then, plug it in after booting and Ubuntu should recognize it.  Let us know what happens.
If the drive is installed in the computer, the leave it connected and boot machine.  Now, go into disk manager and see if the drive is listed there.  Click on the drive and then click "mount drive" and it should now be available.  If you want it recognized everytime you boot, you'll have to get someone with more knowledge than me to help you. :-)

---

### Post by DawieS on 2011-06-07
I recommend that you reboot the computer, and check your Bios settings during boot-time. The drive has to be recognized during boot. It is probably a setting such as "Native IDE" that is currently disabled.

---

### Post by shad0w_walker on 2011-06-07
Edit: Apparently the IDE isn't hotplug warning isn't needed now.

Your best bet is to see if the drive is detected on boot. Usually you can get into the BIOS with a key press such as Del or F2 at bootup. It should say somewhere. When you're in there, it should have a list of drives, etc.

---

### Post by seawolf167 on 2011-06-08
Check BIOS (usually by hitting [F2], [F8] or [del] during POST), for a couple things


[LIST]
[*]ensure the IDE channels are enabled
[*]ensure that the drive itself is enabled (and not switched to "off")
[*]ensure that sata/ide combinations are enabled (depending on your BIOS there is usually an option that controls this)
[/LIST]
On the drive itself, you may need to switch the jumper from "master" to "cable select". Also check basic things like that the drive is getting power, has a solid PATA connection, etc.

---

