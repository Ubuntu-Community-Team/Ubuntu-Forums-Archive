---
title: "How do you convert AVI to smaller ISO image???"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by suomalainen on 2010-02-08
Ubunteros,

I have an AVI file that I want DeVeDe do convert into an ISO image.

The AVI file is 2GB. After DeVeDe makes it an ISO it becomes 5.3GB!!! Now it is larger than what will fit to a DVD...

So what should I be doing to make this smaller? Or what other ideas and process are there that I can follow???


Thanks for your help!!!!

---

### Post by sandyd on 2010-02-08
> **suomalainen said:**
> Ubunteros,

I have an AVI file that I want DeVeDe do convert into an ISO image.

The AVI file is 2GB. After DeVeDe makes it an ISO it becomes 5.3GB!!! Now it is larger than what will fit to a DVD...

So what should I be doing to make this smaller? Or what other ideas and process are there that I can follow???


Thanks for your help!!!!

DeVeDe uses mencoder, which uses bitrate calculations to estimate the size of the iso being produced. The bitrate calculations are always off, so the iso actuallly is smaller than a DVD. It will be about 3.7 GB. 

However, I simply believe that your having the same problem - except that mencoder overestimated the bitrate.

Try and use dvdstyler or some other DVD creation tool.

---

### Post by Temposs on 2010-02-08
Have you tried making the image in Brasero?

---

### Post by TenPlus1 on 2010-02-08
First make sure you have the latest version of DeVeDe installed, then add your .avi file as normal and click on the "Adjust Disc Usage" at the side of the percentage bar, it'll recalculate and make it fit without any problem...

---

### Post by halitech on 2010-02-08
> **TenPlus1 said:**
> First make sure you have the latest version of DeVeDe installed, then add your .avi file as normal and click on the "Adjust Disc Usage" at the side of the percentage bar, it'll recalculate and make it fit without any problem...

+1 I do this all the time. Just make sure the time of the video(s) is under 3 hours and when you click the adjust disk usage it should come out at about 3.7gig

---

### Post by switch10 on 2010-02-08
> **TenPlus1 said:**
> First make sure you have the latest version of DeVeDe installed, then add your .avi file as normal and click on the "Adjust Disc Usage" at the side of the percentage bar, it'll recalculate and make it fit without any problem...

+1  Yes this works.  I use it almost every time.  It will decrease quality though obviously.

---

### Post by suomalainen on 2010-02-11
All,

I'm running 8.04LTS 64 bit abd the ""Adjust Disc Usage" " option doesn't exist for me. I even tried uninstalling then installing again but that didn't work.

Is this a feature only available for 32 bit????

Thanks.

---

### Post by halitech on 2010-02-12
I'm using version 3.14 and I have it. Pretty sure I've had it on every version I've used. It should be on the right side about 2/3 of the way down.

---

### Post by suomalainen on 2010-02-12
As You all can See I haven't "adjust disk usage" tool. I even tried using Synaptic to uninstall and then reinstall and that did not work. I even tried "applications --> Add/Remove" and that too failed.....

Maybe it's because I run 64 bit 8.04LTS?????

---

### Post by halitech on 2010-02-12
ummmmmm how can you have version 3.6 when the latest version acording to the authors website is 3.16?

[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

---

### Post by suomalainen on 2010-02-12
I just tried to download from the link you vave using the hyperlink

Click here to download DeVeDe 3.16.0 in DEB format (2003 Kbytes) for Ubuntu, Debian...

But then I got error message.

See attached please.....

---

### Post by halitech on 2010-02-12
use Synaptic to install libgtk2.0-0 and then try to install Devede again

---

### Post by kio_http on 2010-02-12
Convert the video to something else using mencoder then burn.

---

### Post by suomalainen on 2010-02-12
I just tried to install the file via Synaptic and it showed that I already had it. So then I reinstalled it and still nothing happened. Same error message appeared again.

---

### Post by halitech on 2010-02-12
did you install libgtk2.0-0 or is it another version?

---

### Post by suomalainen on 2010-02-13
Hi Halitech,

I really don't know how to answer Your question????

So I attached a screenshot which shows the very exact same file as you noted. It's the same one I said I re-installed....

---

### Post by halitech on 2010-02-14
that makes no sense on why it can't find a dependency like that. I'm not sure what to tell you at this point

---

### Post by Temposs on 2010-02-14
> **halitech said:**
> that makes no sense on why it can't find a dependency like that. I'm not sure what to tell you at this point

The version of DeVeDe that is trying to be installed probably requires a newer version of libgtk than is in the repositories for suomalainen's version of Ubuntu. Thus, it is impossible to satisfy the dependency with the libgtk that is installed.

suomalainen: if you're using Ubuntu 8.04, that's probably why you're getting this error. I guess the DeVeDe devs are not supporting Ubuntu 8.04 anymore. If you want to install the latest version of DeVeDe, you'll likely have to either upgrade your version of Ubuntu or install all the dependencies using the Ubuntu 9.10 repository.

---

### Post by suomalainen on 2010-02-15
Thanks Temposs,

I'm looking to upgrade when the next LTS version is released in April.

I guess I'll get the latest version then.

As mentioned at the outset of this post I have an AVI file that is 2.0 GB and want to turn it into an ISO and burn to DVD. Can you suggest any alternatives?

Thanks

---

