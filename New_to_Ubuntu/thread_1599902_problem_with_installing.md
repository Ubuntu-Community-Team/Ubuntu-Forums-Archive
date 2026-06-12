---
title: "problem with installing"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by M3-n50 on 2010-10-18
Hello I'm having a little problem with installing software on Ubuntu 10.04. I'm not so experienced so I don't know what I might do wrong. 

I always get this error when trying to install new software 
'The following packages have unresolved dependencies. Make sure that all required repositories are added and enabled in the preferences.'

I got this the first time when trying to install monodevelop and after some research I found that I had to add badgerports to the software sources, but I can't really find anything for the other softwares... I've tried to install them in the terminal with 'sudo apt-get install ...', with the Ubuntu software center and with the Synaptic Package Manager but none of them succeed to install the software.

The other things I'm trying to install are Wine, Kile and Gimp.

Anyone knows what I can do to fix this please?

---

### Post by Sealbhach on 2010-10-18
Go to System/Administration/Software Sources and make sure you have universe and restricted and multiverse repositories enabled. Just tick all of them, really, except the CD source. Then refresh the list - this opens up extra channels from which you can get more software.

If you're using Maverick then I think you will find Software Sources is now part of the Ubuntu Software Centre.

.

---

### Post by M3-n50 on 2010-10-18
Thanks for the reply!

I have them all ticked except for source code, it seems I cannot tick that one. What do you mean by refreshing the list? I reloaded the thing after pressing close if that's what you meant. 

It seems it is downloading Kile now, so I think it's working. It's downloading slow though so I'll edit my post or reply to tell if it worked.

Thanks again for the useful information, I hope it will work! :)

EDIT: It worked! Thank you so much! :)

---

### Post by Sealbhach on 2010-10-18
> **M3-n50 said:**
> 
Thanks again for the useful information, I hope it will work! :)

EDIT: It worked! Thank you so much! :)

Thanks for the feedback, it's good to know that stuff worked, so that when other people Google for this in a few months time, they know it will fix it.

.

---

