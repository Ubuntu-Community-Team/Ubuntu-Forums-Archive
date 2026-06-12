---
title: "Citrix Client v10 - black screen with Ubuntu Hardy and no connect??"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by isrd1 on 2008-04-26
Hello,

I've installed the Citrix Client version 10.6 on Hardy and, after initial problems with certificates it now 'connects' to my work server.  In fact though the connect appears not to actually succeed since once the initial Citrix splash screen had disappeared the Citrix client window appears but remains black, then, after a minute or so, disappears without trace.

Please, I'm a bit of a newby, can anyone either suggest what the problem might be, or where on earth I find the logs for Citrix to get more of a clue of what is causing the failure?  I'm completely stuck and don't know how to move forward.

I think I've read all the relevant posts here and I do have the libmotif3 libraries installed.

Thanks, Rob

---

### Post by MarlowH on 2008-06-07
I'm running Hardy amd64. This worked well for me. Start with the posting in this forum [http://ubuntuforums.org/showthread.php?t=771185&highlight=citrix](http://ubuntuforums.org/showthread.php?t=771185&highlight=citrix) which references [http://wass.homelinux.net/howtos/Citrix_ICA_How-To.shtml](http://wass.homelinux.net/howtos/Citrix_ICA_How-To.shtml) 

As the ubuntu forum writer says, be careful to get the English version.

And follow the directions in the homelinux posting. I did find two differences

Instructions say you'll find the firefox plugins at /opt/firefox/plugins/ but I found them at /usr/lib/firefox/plugins 

Instructions predicted the wfica app would be at /usr/lib/ICAClient/wfica but I found it at /home/<my_id>/ICAClient/linuxx86/wfica

---

