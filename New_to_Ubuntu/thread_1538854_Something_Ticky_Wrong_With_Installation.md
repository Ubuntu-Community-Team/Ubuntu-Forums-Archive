---
title: "Something Ticky Wrong With Installation"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by Complete on 2010-07-25
This is my first experience with Ubuntu.  First of all, let me say that i am installing Ubuntu on a machine whose hard drive crashed and I have replace the C drive with a new drive and I think my problem might because of the pin settings on the back of the hard drive and the fact that my system might not recognize it as the C drive.

What happens is this.  After I have installed Ubuntu, the Ubuntu system says that the installation is complete and that I need to restart the computer in order to use the new installation.  After I click the button to "Restart Now" the CD drive spits out the installation CD and the computer hangs.

After waiting several hours just to be sure, I manually power down and power up the computer.

A dos-like display goes by the screen (as it always had) showing what hardware I have on the system .  Here is where I see the first thing that is wrong.  It says:

[INDENT]Pri.Master Disk:  0 MB Mode 0[/INDENT]

If I bring up the BIOS settigs it says that the Primary Master is [AUTO]

if I let the power up of my computer continue it says that there is a disk boot faulure.

What do you suggest I do?

---

### Post by marshmallow1304 on 2010-07-25
If you haven't done so already, check the jumpers on the hard drive.  Set it to master or cable select.

Also, boot up the LiveCD, select 'Try without installing' and use System->Administration->Disk Utility to make sure the disk isn't failing.

---

### Post by Complete on 2010-07-26
> **marshmallow1304 said:**
> If you haven't done so already, check the jumpers on the hard drive.  Set it to master or cable select.

Also, boot up the LiveCD, select 'Try without installing' and use System->Administration->Disk Utility to make sure the disk isn't failing.

I will take your advice.  But first, let me tell you what has happened lately and get see what you think.

Sure enough, the jumpers were wrong and I corrected it.  After that, I checked the BIOS and I set the settings for the master drive to automatic.  Before I did that, everything was set to zero, now the system BIOS recognizes the hard drive and displays the hard drive ID in the BIOS settings.  The only thing that concerns me now is that the size it displays for the hard drive ia a bit lower than I think it should be.  The smallest IDE drive I could find was over 300 gigs.  Now I wonder if the motherboard (2001 Sony Vaio Desktop) is not advanced to recognize a hard drive that big.

Now, here is the current block.  I booted from the CD and I am currently installing Ubuntu.  The problem now is that the final stage of the installation (before it asks to restart the computer) where it seems to install while fromating the hard drive is stuck at 36 percent.  I wonder if the installation is broken by some sort of confusion or error about the hard drive size setting.

I guess if the installation display does not change from 36% over night, I will restart and take your advice to see if the hard drive fails.

---

