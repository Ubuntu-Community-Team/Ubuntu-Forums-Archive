---
title: "remastersys and virtual box"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by cosine352 on 2009-02-06
Hi all,
I am trying to back up the dist. I am using Ubuntu 8.10 and has windows xp in the virtual box. My question is if I do the 
> sudo remastersys dist
does it going to keep the windows xp too ? If not is there anyway to do it? 

Thanks.

---

### Post by rraj.be on 2009-02-06
i cant get why you are asking about windows . . .Remastersys will remaster the ubuntu distro when you select it and there is no doubt regarding tihs.

---

### Post by niteshifter on 2009-02-06
Hi,

He's asking about windows because being a virtual machine it's part of his system.

The answer is no. The dist option does not include any user data. The VM file set would be user data. There are other limitations as well, [see here]("http://www.remastersys.klikit-linux.com/ubuntu.html").

---

### Post by cosine352 on 2009-02-06
> **niteshifter said:**
> Hi,

He's asking about windows because being a virtual machine it's part of his system.

The answer is no. The dist option does not include any user data. The VM file set would be user data. There are other limitations as well, [see here]("http://www.remastersys.klikit-linux.com/ubuntu.html").

That is exactly what I am looking for. So remastersys can not do it. Is there anyway to do it? Like partimage or dd command may be ?? 
If someone know how to do it, please let me know.

---

### Post by thomasr on 2009-02-06
Use remastersys backup - not remastersys distribution. That will save all your data including the Vm - IF it will all fit on a DVD.

---

### Post by cosine352 on 2009-02-06
> **thomasr said:**
> Use remastersys backup - not remastersys distribution. That will save all your data including the Vm - IF it will all fit on a DVD.

is there any way to exclude some folders during this process ?

---

### Post by niteshifter on 2009-02-07
Hi,

> **cosine352 said:**
> That is exactly what I am looking for. So remastersys can not do it. Is there anyway to do it? Like partimage or dd command may be ?? 
If someone know how to do it, please let me know.

partimage is a good choice so long as you can live with not being able to access a particular file or folder from the backup set. partimage is on the Ubuntu Live CD. But a really fine tool kit is the System Rescue CD (available [here]("http://www.sysresccd.org/Main_Page")). Has partimage (and a host of other useful tools), can run in memory (freeing up your optical drive) if you have enough RAM, supports UDF so backup image files can be written directly to DVD by partimage. All in all, a very handy disc to have around. If you have an external USB hard drive the Ubuntu Live CD or System Rescue CD will allow you to image your system.

---

