---
title: "x window: session error in one account"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by rhb on 2009-02-15
*** problem resolved ***

I'm not really a newbie anymore, but not sure where best to post this.

 I recently pulled the graphics card (S3 Savage 2000) out of the AGP slot because I suspect it's related to random reboots.  I managed to experiment and reconfigured the xserver-(forgot name) with dpkg-reconfig.

  First I chose vesa.  It came up in 1024 x 768.  I tried to change screen resolution to 800 x 600, but it showed gibberish.  Next I choxe VGA, but it failed because it couldn't use 24 bit depth.

   I finally reset it to vesa and left resolution alone.  Now it works in single-user mode and for all users but the one in which I changed the screen resolution.  I'm guessing there is a configuration file which I need to edit or delete from the command line before I can use x for that user.

   I am still running Ubuntu 6.06. kernel 2.6.15-53-686.

   The VGA controller is: ler: VIA Technologies, Inc.: Unknown device 3344 (rev 01) 
(note: all my sysinfo lines are left-truncated like that for unknown reasons)

   I can't remember exactly how to see the error messages now.  It says something about no screen :0 or can't connect to it.

   Any suggestions about how to reconfigure or how to get more debug info would be appreciated.

Update:

I learned about dpkg-reconfigure, so this episode was helpful to me.  I had the PCI adapter working on most accounts, but at one point I switched to a console via ctrl-F2, and the display messed up.  I decided that the PCI adapter is probably flaky, so I put the AGP board back in.  I had trouble with the reconfigure command at that point -- the conf file was missing a required entry.  Because I had saved the original xorg.conf file, I restored it, and now it works again.  Apparently only a new motherboard can prevent the random reboots, which I believe are related to the PCI adapter.

---

