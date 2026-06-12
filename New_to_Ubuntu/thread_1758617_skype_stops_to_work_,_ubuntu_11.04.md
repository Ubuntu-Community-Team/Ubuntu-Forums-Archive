---
title: "skype stops to work , ubuntu 11.04"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by hanah on 2011-05-14
Hi everybody 

I am really beginner with Ubuntu, but 
i have  (managerd to) installed skype after upgrade from 10.10 to Ubuntu 11.04  (toshiba laptop)
using 

[http://compixels.com/6827/install-skype-in-ubuntu-11-04-natty-narwhal-command-line](http://compixels.com/6827/install-skype-in-ubuntu-11-04-natty-narwhal-command-line)
and ubuntu software centre. 

Everything had seemed to be o.k., but after several days the program stopped to work, was not possible to start it at all. 

I have tried terminal, but installation was not completed, (do not remember the error more, but something with download)

therefore reinstalled packages (synaptic package manager) 
libqt4-dbus libqt4-network libqt4-xml libasound2

uninstall, downloaded new from [www.skype.com]("http://www.skype.com") and again reinstalled 

Was working also after restart, but unfortunately today i have the same problem

Dont you have please any idea how I can fix it. Reinstalling before every calling is annoying ;) 

Many thanks 

hanah

---

### Post by kpbenz on 2011-05-26
This is apparently a new issue, simply 

> 
rm ~/Skype/shared.xm


and restart skype.

Maybe you also want to install the skype package, that is in the Ubuntu repository ...

---

### Post by RichardCain on 2011-05-29
Correction:

> rm ~/.Skype/shared.xml

---

### Post by oldsoundguy on 2011-05-29
You think Skype has problems in Linux now, wait until they are completely absorbed by Microsoft! (Microsoft bought them out from eBay!)

---

### Post by RichardCain on 2011-05-29
I think most linux users are dreading that!  Any alternatives you can suggest?

---

### Post by dFlyer on 2011-05-29
> **hanah said:**
> Hi everybody 

I am really beginner with Ubuntu, but 
i have  (managerd to) installed skype after upgrade from 10.10 to Ubuntu 11.04  (toshiba laptop)
using 

[http://compixels.com/6827/install-skype-in-ubuntu-11-04-natty-narwhal-command-line](http://compixels.com/6827/install-skype-in-ubuntu-11-04-natty-narwhal-command-line)
and ubuntu software centre. 

Everything had seemed to be o.k., but after several days the program stopped to work, was not possible to start it at all. 

I have tried terminal, but installation was not completed, (do not remember the error more, but something with download)

therefore reinstalled packages (synaptic package manager) 
libqt4-dbus libqt4-network libqt4-xml libasound2

uninstall, downloaded new from [www.skype.com]("http://www.skype.com") and again reinstalled 

Was working also after restart, but unfortunately today i have the same problem

Dont you have please any idea how I can fix it. Reinstalling before every calling is annoying ;) 

Many thanks 

hanah

This has been reported a lot recently. Not sure what is going on with most having this problem. I'm running 11.04 with skype from archives. I've had no problems at all. Just finished an 1 hour chat with my son-in-law and no problem. Yesterday chatted with my nephew in the philippines, no problem. I don't think it's a microsoft/skype problem yet but may become one in the future.

---

