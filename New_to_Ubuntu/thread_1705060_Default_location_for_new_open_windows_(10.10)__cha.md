---
title: "Default location for new open windows (10.10) / changing xorg.conf settings?"
date: 2011-03-11
forum: New to Ubuntu
---

### Post by elsea on 2011-03-11
Hi, 

I am using Ubuntu 10.10.  I changed my /etc/X11/xorg.conf file by accident I think.  (*See details below, but I'm not sure they're relevant to my question.)

Before this change, when my application programs launch new windows, they seemed to be placed automatically in "clear" areas.  E.g. a program opened 4 windows, and they would be spread out to the 4 corners of the screen or sometimes 3 corners and another space in the middle.

Now, when I run the same application or when I open new terminal windows, it seems they always launch in the left-hand corner of the screen, layered on top of each other.  

How can I regain the original window behavior? 

Thanks for any suggestions.

-------------------

*[Details on how xorg.conf was changed:  I tried to install the Nvidia drivers  but that led to terminal only login after reboot.  I did sudo rm  /etc/X11/xorg.conf, then I went to into recovery mode to generate a new  xorg.conf.  I have gui login now but I'm not sure that the regenerated file was the same as the old one.   I'm not even sure if there existed an xorg.conf before I tried installing the Nvidia drivers.  Thus if there are any suggestions on how to check that or related settings that might have changed, I'd appreciate those too.]

---

### Post by turtle153 on 2011-03-11
First check that you;re using compiz. Then install **compizconfig-settings-manager **and look under **Place Windows**. If the Placement Mode is set to smart then Compiz fills up empty spaces first.

---

### Post by elsea on 2011-03-11
Thanks very much!  I don't know how to check that I was using compiz, but it was installed and I installed the settings manager.  PlaceWindows was already set to Smart, and after re-running my application, the windows are distributed instead of layered.

---

