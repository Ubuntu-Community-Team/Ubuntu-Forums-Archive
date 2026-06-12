---
title: "Ndiswrapper install problems"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by JSpencer87 on 2007-04-20
Ok i am not quite sure where to post this but since the main thing i am trying to install is Ndiswrapper i figure this was a good one.   I just installed Fiesty on an old machine that i am using a Netgear WG311v3 wireless card and i need to install the driver for it.  But when i tried installing it using apt-get i get an error message saying 
"E: Couldn't find package ndiswrapper-utils-1.8"
after further investigation it can't find any packages for anything.  What do i need to do?

Justin

---

### Post by tl3000 on 2007-04-20
While working on my wireless problem after upgrading to Fiesty as described in the following thread:

[http://ubuntuforums.org/showthread.php?t=415458](http://ubuntuforums.org/showthread.php?t=415458)

I found that 1.8 has been replaced by 1.9 in the repository.  I too tried to install 1.8 as instructed and got the same error message.  You can install NDISwrapper 1.9 from the repository--which I was able to do successfully but I'm not sure how this new version differs though.  I know that with Edgy my wireless adapter driver had problems with which particular version of NDISwrapper is used.  FYI...

---

### Post by JSpencer87 on 2007-04-20
I have tried using the newer version of NdisWrapper with no luck. I still get the no package found error.  I also don't see anything in the Synaptic Package Manager besides what is already installed.

---

