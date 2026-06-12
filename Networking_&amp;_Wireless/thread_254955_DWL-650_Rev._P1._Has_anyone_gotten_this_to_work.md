---
title: "DWL-650 Rev. P1. Has anyone gotten this to work?"
date: 2006-09-10
forum: Networking &amp; Wireless
---

### Post by Shane N on 2006-09-10
I've searched and searched and searched the forum for signs of anyone getting this card to work, and from what I found, I didn't see any signs of success. So, for a "end of discussion" topic question, has anyone gotten this card to work at all? And if so, share the secret... how did you do it?

---

### Post by einstein on 2006-09-11
I tried but gave up on a DWL-650+.  Got a Linksys 802.11b notebook adapter and had it up and running in a flash.  D-Link + Linux has been nightmarish for me... ended up re-installing Breezy on a desktop after (foolishly) plugging a DLink DWL-G122 into it.

---

### Post by ymeng on 2006-10-17
I have the same problem. I found this link that might hold the solution: [http://kernel.org/pub/linux/utils/kernel/pcmcia/howto.html](http://kernel.org/pub/linux/utils/kernel/pcmcia/howto.html). However, I don't know how to do this. 

Can someone pick up from here, re-interpret this howto into step by step instructions?

Here is my theory why this might be the solution: I noticed DWL 650 RevP appears in the source file: linux-wlan-ng-0.2.3/src/prism2/driver/pcmcia_cs.c. However, when I tried "apt-get install linux-wlan-ng". I see this msg at the end: "* Linux >= 2.6.13-rc1 requires pcmciautils instead of pcmcia-cs"
 (I had to run "apt-get remove linux-wlan-ng" first so I can see this msg). Does this msg imply that very pcmcia_cs.c is left out in my build?

If so, then the link may be the answer to the problem? I'm a newbie, some expert may tell if I am barking on the wrong tree.

Any help is greatly appreciated!

---

### Post by audiophyl on 2007-04-04
> **Shane N said:**
> I've searched and searched and searched the forum for signs of anyone getting this card to work, and from what I found, I didn't see any signs of success. So, for a "end of discussion" topic question, has anyone gotten this card to work at all? And if so, share the secret... how did you do it?
I've gotten the DWL-650 Rev P1 to work in Ubuntu.  The problem is that the device ID isn't correct in the source.  This has been reported to several parties that have access to the source, and will be fixed in (some) future kernel release.  The simplest solution is to use a hex editor and fix the hostap_cs.ko module (much faster and cleaner than recompiling).  My instructions are here, and all of the problems noted on the second page have been resolved by Ubuntu updates:

[Page 1]("http://sin613.blogspot.com/2007/02/i-win.html")
[Page 2]("http://sin613.blogspot.com/2007/02/i-win-again.html")

Update: To be precise, a patch has already been committed and this will be fixed in kernel 2.6.22 according to the maintainer that closed the bug report on kernel.org.

---

