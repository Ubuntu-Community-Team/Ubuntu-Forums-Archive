---
title: "genuine ubuntu"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by carthee29 on 2011-01-03
how can find it is an genuine software........
my ubuntu gives warning about "it is not a genuine ubuntu"
and there is missing many package in my snaptic package manager...

---

### Post by Megaptera on 2011-01-03
Where did you get your copy from? Here's the legal/legit link [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by Jay Car on 2011-01-03
> **carthee29 said:**
> how can find it is an genuine software........
my ubuntu gives warning about "it is not a genuine ubuntu"
and there is missing many package in my snaptic package manager...

You'll have to make your own decision, of course.  But, if you're truly worried about the authenticity of your software, my own advice would be to download Ubuntu from [here]("http://www.ubuntu.com/desktop/get-ubuntu/download"), and then reinstall it. Be sure to backup your personal files first.

---

### Post by howefield on 2011-01-03
> **carthee29 said:**
> my ubuntu gives warning about "it is not a genuine ubuntu"


Screenshot ?

---

### Post by ruegore on 2011-01-03
I'm not quite sure I understand. As far as I know, there is no notion of "genuine" akin to Microsofts' "genuine".

If you want to be sure you have an unmodified distro, just head over to ubuntu.com and click on Downloads, and select whichever one you want. Download, burn to disc (or USB key), install, and be happy. You can also find MD5Sums for all the iso files so you can be sure the file wasn't modified between ubuntu.com and you, or whichever mirror location you get it from.

Use this to generate checksum of files using md5:
```
$ md5sum *filename*
```

"filename" would be the actual filename of the file you want to check.

Compare to provided md5sum files for your download. If you have a mismatch, delete the iso and download and check again. If you still have a mismatch, try another mirror.

I hope that helps.

---

### Post by audiomick on 2011-01-03
Hallo.
Here is some stuff to read
[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)
[https://help.ubuntu.com/8.04/serverguide/C/extra-repositories.html](https://help.ubuntu.com/8.04/serverguide/C/extra-repositories.html)

You should at least have a look at this, even if it seems to be a lot to read.

In short, the sofware centre, or synaptic package manager, goes and gets software from various servers on the internet. On a freshly installed Ubuntu system, only the Ubuntu servers are enabled. It is possible to add other ones to the lists. 

Also, even from the Ubuntu lists, it is possible to get software that is not maintained by Ubuntu directly. That is explained here:
[http://www.ubuntu.com/project/about-ubuntu/components](http://www.ubuntu.com/project/about-ubuntu/components)

This means that if you want to install something and get a message that it is not "genuine Ubuntu", this is not necessarily a problem.

If stuff is "missing" from Synaptic, it most likely means you don't have the package source for it enabled,  or it is software that Ubuntu does not supply at all.

---

### Post by Frogs Hair on 2011-01-03
Hi and Welcome

It may be helpful to post the exact message and a link to where you downloaded the software from. One way to check is to go to update manager > settings tab > authentication and check for the automatic signing key.

---

### Post by Verbeck on 2011-01-03
is it the error 'software source not authenticated' ? (or something like that)

you didn't give much detail in the first post

---

### Post by perspectoff on 2011-01-03
I can sell you a sticker for $199, if you want.

---

### Post by matt_symes on 2011-01-03
Hi

Please supply a screen shot as per howefield's suggestion. I think you might be getting a bit confused as to what is genuine. With a screen shot we would be able to tell you exactly what is going on.

Applications->Accessories->Take a screenshot. (Put grab after a delay of greater than 0 when taking it).

Kind regards

---

