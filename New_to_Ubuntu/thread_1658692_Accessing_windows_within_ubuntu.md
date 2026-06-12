---
title: "Accessing windows within ubuntu"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by rkakkar on 2011-01-03
I have a laptop with windows installed in it currently. I want to install ubuntu but still be able to access windows from within in (without rebooting). is this possible? and can i do it without having to remove windows first?

---

### Post by nevius on 2011-01-03
> **rkakkar said:**
> I have a laptop with windows installed in it currently. I want to install ubuntu but still be able to access windows from within in (without rebooting). is this possible? and can i do it without having to remove windows first?

You can access the files in your windows partition without rebooting (if you have windows and ubuntu installed on separate partitions). You will not be able to run programs installed in Windows from the linux partition. If you want to run windows programs in Ubuntu you need to look into WINE or running windows in a virtual machine (ie virtualbox).

---

### Post by jink2002 on 2011-01-03
If you are dual booting Windows and Linux:

While in Ubuntu, open up Disk Usage Analyzer (it's in accessories) and click "Scan Home". Your windows partition will come up. You can browse through files and access them, as long as there is an application that can open them (such as word documents, certain applications, etc..)

Hope that helps ^_^

---

### Post by rkakkar on 2011-01-03
Oh I need to run windows applications ... basically this one main app at office works properly only in IE .. i know :( .. so i need to keep windows access for it. so i guess virtualbox would solve my problems?

---

### Post by I'mGeorge on 2011-01-03
> **rkakkar said:**
> I have a laptop with windows installed in it currently. I want to install ubuntu but still be able to access windows from within in (without rebooting). is this possible? and can i do it without having to remove windows first?

Ubuntu recognizes windows partitions so you can mount them.

---

### Post by Spencer Caplan on 2011-01-03
> **rkakkar said:**
> Oh I need to run windows applications ... basically this one main app at office works properly only in IE .. i know :( .. so i need to keep windows access for it. so i guess virtualbox would solve my problems?

That is the kind of issue that Virtualbox works perfectly for (I find WINE to be rather buggy on many applications)

Just let me know if you have any issues moving to Virtualbox.

---

### Post by Miter_J on 2011-01-03
I remember when you install Ubuntu, you'll get the options of mounting the Windows partitions in Ubuntu. That's easy to do. You can visit windows files whenever you want since the NTFS are recognizable in Ubuntu.
But accessing Ubuntu in Windows will take you a lot of effort. That's really difficult.
Using VirtualBox will make it slower cuz it use only part of your RAM and you're actually running many Windows progresses at the same time.
Btw, according to your statements, I don't know why you wanna use Ubuntu.

---

### Post by rkakkar on 2011-01-03
> **Miter_J said:**
> I remember when you install Ubuntu, you'll get the options of mounting the Windows partitions in Ubuntu. That's easy to do. You can visit windows files whenever you want since the NTFS are recognizable in Ubuntu.
But accessing Ubuntu in Windows will take you a lot of effort. That's really difficult.
Using VirtualBox will make it slower cuz it use only part of your RAM and you're actually running many Windows progresses at the same time.
Btw, according to your statements, I don't know why you wanna use Ubuntu.

Why I wanna use UBuntu?! I LOVE IT. I wanna use it for everything except for that application which needs IE. Like my email, videos, music, etc.

---

### Post by rkakkar on 2011-01-03
I'll try VB and see how it works out. Will post again in case I face issues.

---

### Post by Miter_J on 2011-01-03
Aha~ So good luck~
PS. I hate IE as well...

---

