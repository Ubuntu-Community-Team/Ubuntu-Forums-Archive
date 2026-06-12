---
title: "Accessing Windows apps on a dual-boot"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by kickwin on 2009-05-21
I recently installed the latest version of Ubuntu on my machine and I already have Windows XP running on it. Though I would like to stick to using Ubuntu, I have a few proprietary softwares (my grad research related) installed on my WinXP that I have to use once in a while. I am not sure how I can access these software from within Ubuntu without having to restart the computer and logging into Windows.

I did some research online but found that many posts were either too old or do not explain in a language that a linux newbie like myself can understand. I would really appreciate if you guys could provide suggestions.

---

### Post by Zzl1xndd on 2009-05-21
When I need to use a Windows application I normally use Wine or a Virtual machine. 
 
What kind of applications is it that you need to use?

---

### Post by lovinglinux on 2009-05-21
There was a thread posted a few hours ago about using your current Windows installation on a virtual machine, but I don't remember in which forum it was posted. Anyway, you could do that.

---

### Post by QIII on 2009-05-21
Using Wine is the generally accepted answer.  But not all Microsoft products will run satisfactorily in it.

If you google "Wine Linux" (no quotes), you should be able to find a list of what does and does not work well.  Also, do a forum search here and you will find plenty of help regarding its use.  

Personally, I'd just go with the 90 seconds it takes to go from OS to OS and keep anything from MS from sullying my Linux box.

(Sorry to the MCSE.  I'm a MCSD, and I try to avoid using MS...)

---

### Post by Zzl1xndd on 2009-05-21
> **QIII said:**
> 
(Sorry to the MCSE.  I'm a MCSD, and I try to avoid using MS...)


No worries, I agree with you 100%.

---

### Post by lisati on 2009-05-21
The previously mentioned ["Wine"]("https://help.ubuntu.com/community/Wine") will be good for using *some* applications. Try [here]("https://help.ubuntu.com/9.04/switching/applications-equivalents.html") for a list of Linux-friendly equivalents of some programs.

---

### Post by kickwin on 2009-05-21
I have Origin (scientific graphing) and Endnote (bibliography management) installed on my WinXP. 

Thanks for your suggestions guys. I will give 'Wine' a try.

---

### Post by Apollo87 on 2009-05-21
Looks like Origin and Endnote work well with Wine:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=378](http://appdb.winehq.org/objectManager.php?sClass=application&iId=378)

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=835](http://appdb.winehq.org/objectManager.php?sClass=application&iId=835)

---

### Post by kickwin on 2009-05-25
I was wondering if anyone has seen any simple instructions on the web for configuring Wine to access the applications on existing Windows partition(s). Thanks in advance.

---

### Post by theozzlives on 2009-05-25
You can't access the apps installed on the Windows partition, but you may re-install them on your Ubuntu using WINE.

---

