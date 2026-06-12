---
title: "Flash is not working well at all in Jaunty"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by 11010110 on 2009-05-28
Hello everyone,

I have tried to install flash from firefox (the firefox plugin) from the adobe website, from the repositories and i have even tried the nonfree plugin but still the majority of the videos on the majority of sites will not even appear. any flash on any page that does show up is displayed as a big grey play symbol surrounded by a circle (even ads) and once clicked the video has laggy sound (only when the nonfree audio plugin is used) and just doesnt work satisfactorily under any of the different installations. It worked all but perfectly with Intrepid for me. I have researched and none of the fixes i found worked and most of them were for AMD64 (which i do not have so i disregarded those fixes). If anyone has any ideas on how i could resolve this it would be greatly appreciated. I will continue my research in the meantime. 

thanks to all in advance!

---

### Post by gandaran on 2009-05-28
your mistake is installing a lot of flashy things, go to synaptic type flash in search box, the only package you should have installed in jaunty is flashplugin-installer( adobe flash from the repository), remove the rest, the adobe packages, swfdec and gnash.

---

### Post by 11010110 on 2009-05-28
that was exactly it thank you. i thought i tried it already but way at the bottom of the list there were some plugins still installed i guess. i think it went wrong when i installed the swf reader plugin when firefox prompted me and then installed flash though synaptic. 

Thanks again for the help! It is truly appreciated!

---

### Post by ex-wirecutter on 2009-06-19
> **gandaran said:**
> your mistake is installing a lot of flashy things, go to synaptic type flash in search box, the only package you should have installed in jaunty is flashplugin-installer( adobe flash from the repository), remove the rest, the adobe packages, swfdec and gnash.
May I add my thanks as I was having the same problem and your suggestion solved it .

---

