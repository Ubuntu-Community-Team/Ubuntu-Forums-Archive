---
title: "Video Driver no longer loads"
date: 2011-07-13
forum: New to Ubuntu
---

### Post by chipslinger on 2011-07-13
I have a Ubuntu 8.04 system that I use as a fileserver. It works fine except it doesn't load the windows system. When I look in the syslog it shows an error CRITICAL: gdm_config_value_get_bool: assertion 'value->type == GDM_CONFIG_VALUE_BOOL" failed.
 
About a year or so ago, I had loaded a third party video driver, which worked great, until I did a package update and the video card stopped working. I've decided that I don't need this to work and just want to get back to a standard SVGA resolution without any of the fancy stuff working. However, I have no memory of how I got the video driver installed.
 
I searched the forum and found one reference to a similar problem, but don't understand enough to do a bare bones boot or what file to edit to remove the driver. Any help would be greatly appreciated. Thank you
 
btw: I did recently log in remotely and do a package update, but the problem is still there.

---

### Post by Mark Phelps on 2011-07-13
Part of solving your problem is that 8.04 is no longer supported.  So, it may be difficult to find packages for it now.

To help us out, we need to know the make and model video card you're using.  So, open a terminal, do an "lspci", find the line containing "VGA" -- and post the results back here.

---

### Post by chipslinger on 2011-07-14
Thanks in advance for your assistance.
 
The response is VGA compatible controller: ATI Technologies Inc unknown device 9498. I can power off the system if having the exact card type would be helpful. Again, I'm not necessarily trying to make this card work in all its wonder and glory; just get it working again at a standard SVGA resolution.
 
This may be beyond what I can reasonably ask to have explained to me in an email, but is there a reliable way to update a system to a newer Ubuntu version "in situ" without installing from scratch? I have installed a four disk RAID plus SAMBA, but otherwise it is a stock 8.04 installation. I haven't searched the forum for further information, but I suspect that doing an upgrade is not necessarily a slam dunk.

---

