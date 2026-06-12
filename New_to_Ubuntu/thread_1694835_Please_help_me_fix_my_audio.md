---
title: "Please help me fix my audio?"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by hey-you on 2011-02-24
Hello,

I'm starting a new thread because I can't find anyone else with the same problem that I have. It seems that while trying to fix choppy sound in my Virtual Box Windows  7 guest I have messed up my computer. I guess I followed someone's  advice that didn't really apply to my situation and now I have no sound at all, and Sound is gone from my Preferences menu.

When I type aplay -l in terminal under 00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High  Definition Audio Controller (rev 01) there are no Kernel drivers or  kernel modules listed.

I'm using Ubuntu 10.10.

Can someone please tell me what to do to fix it? I'm not very experienced in this and would appreciate detailed instructions.

Thank you!

---

### Post by oldos2er on 2011-02-25
What exactly was the advice you followed? Not easy to advise you without knowing what you did.

---

### Post by corncob on 2011-02-25
> **oldos2er said:**
> What exactly was the advice you followed? Not easy to advise you without knowing what you did.

Is the tutorial at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) of any help?

---

### Post by hey-you on 2011-02-25
> **corncob said:**
> Is the tutorial at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) of any help?
I followed this tutorial through the ALSA driver Compilation step which failed. Here is the log.

for i in control postinst postrm ; do \                                     
 &#9474;         if [ -f debian/$i.orig ]; then \                                    
 &#9474;         mv -f debian/$i.orig debian/$i ; \                                  
 &#9474;         fi ; \                                                              
 &#9474;         done                                                                
 &#9474; rm -f control-munge                                                         
 &#9474; make mrproper                                                               
 &#9474; make[1]: Entering directory `/usr/src/modules/alsa-driver'                  
 &#9474; rm -f .depend *.o snd.map*                                                  
 &#9474; rm -f modules/*.o modules/*.ko                                              
 &#9474; make[2]: Entering directory `/usr/src/modules/alsa-driver/include'          
 &#9474; rm -f .depend core *.o sndversions.h modules/*.ver modules/*.stamp          
 &#9474; make -C sound clean                                                         
 &#9474; make[3]: Entering directory `/usr/src/modules/alsa-driver/include/sound'    
 &#9474; rm -f *.h               


I had selected the hda-intel for the alsa-source step because the lspci -v command used to show hda-intel although it doesn't now. This is what it says now:

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: Dell Device 01bd
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at efffc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

What should I do next?

---

### Post by corncob on 2011-02-26
> **corncob said:**
> Is the tutorial at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) of any help?

Well, I guess it wasn't of any help.  It was just a thought since you weren't getting any other advice except for post #2 which you seem to have skipped.

---

### Post by hey-you on 2011-02-26
Thanks for the tutorial, it looked like it might help for a while, but then failed. I don't mean to skip post #2, but I can't find the pages from which I followed the directions, so I just can't answer that one. I guess I will have to install Ubuntu again.

Thanks for the replies.

---

### Post by lkjoel on 2011-02-26
> **hey-you said:**
> Thanks for the tutorial, it looked like it might help for a while, but then failed. I don't mean to skip post #2, but I can't find the pages from which I followed the directions, so I just can't answer that one. I guess I will have to install Ubuntu again.
 
Thanks for the replies.
Before you re-install, just give this a shot.
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.
See if it helps.

---

### Post by hey-you on 2011-02-26
> **lkjoel said:**
> Before you re-install, just give this a shot.
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.
See if it helps.


I followed the instructions in the Fix your sound! link and it worked! Thanks A LOT!

---

### Post by lkjoel on 2011-02-26
> **hey-you said:**
> I followed the instructions in the Fix your sound! link and it worked! Thanks A LOT!
No problem! ;)

---

