---
title: "pptpd security update 1.2.3-1ubuntu1 broke pptpd"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by Vermyndax on 2007-05-17
Ubuntu folks:

pptpd security update 1.2.3-1ubuntu1 released on May 14th, 2007 broke pptpd for connecting Mac clients.

Downgrading to the previously released version 1.2.3-1 resolved the issue immediately.

Is there something that needs to be done to the options of pptpd to resolve the issue?

---

### Post by lonetree on 2007-05-17
Hi Vermyndax,

I posted the same issue a few hours ago too.  ref : [http://ubuntuforums.org/showthread.php?t=446626](http://ubuntuforums.org/showthread.php?t=446626)

My problem lies with windows clients. Now at least I know that I am some how right about the new pptpd updates is the culprit.

By the way, how do you do the downgrade? And which version of ubuntu are you using now? I'm still on 6.06LTS.

Hope you can reply soon. Cheers

---

### Post by Vermyndax on 2007-05-17
I am also on Dapper LTS.

To downgrade:

apt-get install pptpd=1.2.3-1

---

### Post by lonetree on 2007-05-17
Hi Vermyndax,

thanks a lot, I'll do that now. 

Let's just hope the real patch will be ready soon, and no more break.

Cheer mate.

Keep in contact.

regards

-------------------------------

Ok. Downgrade successful, seems fine now. By the way, how do you know which is the previous version? Any tips? :-)

---

### Post by Vermyndax on 2007-05-17
I looked it up in the Ubuntu package repository... packages.ubuntu.com

Has anyone reported this bug?  Nice to know it was tested before the patch was released :)

---

### Post by Chappy7777 on 2007-05-17
I too am still using 6.06  My knowledge of Ubuntu is limited at best, but of the 4 versions I've messed around with, 6.06LTS is the "sweetspot" of Ubuntu Distroes. 
I just installed 7.04 on 2nd HDD, (the 1st HDD has 6.06) and as I type this I am removing 7.04. I had Xandros on it before, and it will be going back on later.
I don't understand why 6.06 has, in the Networking app, an Autodetect for the modem, but neither 6.10 or 7.04 do. I assume the distro is supposed to do it on it's own. (?) But I can't get the dang thing to see my modem.6.06's autodetect picks it up right away. My first, and last for awhile, experience w/Feisty was not good. Sigh. 
Chappy

---

