---
title: "fake virus scanner"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by dzon65 on 2009-11-27
You know this fake message popping up "your system is in danger,there are many threads......scanning now...50 dangerous blabla.detected."Do you want to install this executive file now?"I thought this was a thing from the (windows)past.And yet,it popped up and is very persistent.I know from the past this is a fake thing but it made me think.Might be a stupid question but since I dualboot on vista,if vista would be infected,can this affect ubuntu as well?

---

### Post by Grenage on 2009-11-27
> if vista would be infected,can this affect ubuntu as well?

No, it won't affect it.

---

### Post by NickJones on 2009-11-27
And this is why I like Ubuntu!

---

### Post by MelDJ on 2009-11-27
no. windows viruses wont affect ubuntu.

---

### Post by H4F on 2009-11-27
> **Grenage said:**
> No, it won't affect it.

Hm well. I wouldn't say that.
1) If you have access from vista to your /boot /home /root (yes you can do that!!) 
2) If some one write a virus with targeting those systems like yours

It is possible that I virus will make some changes to your linux partitions or file/folders.

The problem is that no one yet have a reason to create such a beast :D

---

### Post by MelDJ on 2009-11-27
> **H4F said:**
> Hm well. I wouldn't say that.
1) If you have access from vista to your /boot /home /root (yes you can do that!!) 
2) If some one write a virus with targeting those systems like yours

It is possible that I virus will make some changes to your linux partitions or file/folders.

The problem is that no one yet have a reason to create such a beast :D

actually there are linux viruses but they are mainly in labs and are dealt with quickly. 
any proof to back up your first claim? (just curious) ;)

---

### Post by wilee-nilee on 2009-11-27
If your running Firefox in vista or Ubuntu you should have noscript and adblock plus installed from addons and you will never see these popups
With adblock plus I add the easy privacy+easylist 

better privacy is a good lso cookie remover as well

---

### Post by H4F on 2009-11-27
> **MelDJ said:**
> actually there are linux viruses but they are mainly in labs and are dealt with quickly. 
any proof to back up your first claim? (just curious) ;)

there are ways to access ext3 partitions trough installing third party drivers.
[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

---

### Post by MelDJ on 2009-11-27
i dont think explore2fs or any such files can be used to configure /root files as they are protected

---

### Post by H4F on 2009-11-27
> **MelDJ said:**
> i dont think explore2fs or any such files can be used to configure /root files as they are protected

some sources says explore2fs currently is not supporting write access because its unstable.
google says still you can have read write access trough other ways

---

### Post by whoop on 2009-11-27
> **H4F said:**
> some sources says explore2fs currently is not supporting write access because its unstable.
google says still you can have read write access trough other ways

Well, in the end there just bits on the disk platter, there not encrypted by default. The protection scheme is not really active when the operating system itself is not running. So there's nothing really stopping you from changing stuff. True protection could only be achieved via hardware protection; encryption would get you some security, although you would still be able to corrupt/format the file system.

---

