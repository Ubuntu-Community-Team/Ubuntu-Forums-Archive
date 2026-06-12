---
title: "Kylix"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by Panekoek on 2011-03-06
Hi Guys

I am in school and we do delphi. I have got Ubuntu on my computer and i have heard that kylix is delphi on linux. If anyone could tell me where i could get or buy kylix that would be great.

Thanks a lot.

Pane

---

### Post by ikt on 2011-03-06
> **Panekoek said:**
> Hi Guys

I am in school and we do delphi. I have got Ubuntu on my computer and i have heard that kylix is delphi on linux. If anyone could tell me where i could get or buy kylix that would be great.

Thanks a lot.

Pane

Looks like kylix has been dead for a while now, are you able to run the compiler they use with wine?

---

### Post by kellemes on 2011-03-06
Kylix is dead indeed..
Even better: [Lazarus]("http://www.lazarus.freepascal.org/")

---

### Post by Panekoek on 2011-03-06
But is lazarus like delphi? Like does it have the same components and layout?

---

### Post by jmszr on 2011-03-06
Panekoek,

This may be of help: [http://wiki.lazarus.freepascal.org/Lazarus_For_Delphi_Users](http://wiki.lazarus.freepascal.org/Lazarus_For_Delphi_Users) and: [https://secure.wikimedia.org/wikipedia/en/wiki/Lazarus_%28IDE%29#Differences_from_Delphi](https://secure.wikimedia.org/wikipedia/en/wiki/Lazarus_%28IDE%29#Differences_from_Delphi) .

---

### Post by JKyleOKC on 2011-03-06
> **Panekoek said:**
> But is lazarus like delphi? Like does it have the same components and layout?It's similar, but not identical since the underlying operating systems are different.

My solution to the problem was to install VirtualBox, then in VirtualBox install a copy of WinXP, and finally in that copy install Delphi. To do it this way it's best to have at least 2 GB of RAM and a dual-core processor, though.

If you create programs with either Kylix or Lazarus they may not run at all on Windows, which might be a problem for your school assignments...

---

### Post by kellemes on 2011-03-07
> **Panekoek said:**
> But is lazarus like delphi? Like does it have the same components and layout?

It strives to be as compatible as possible, I have actually converted some Delphi-projects to Lazarus without issues.
[Lazarus for Delphi users.]("http://wiki.lazarus.freepascal.org/Lazarus_For_Delphi_Users")

But if you really need Delphi you indeed could go VirtualBox, but (as said) you need a lot of resources since you're running 2 os's and Delphi at the same time.

---

### Post by Panekoek on 2011-03-07
I have got a core i7 and 4gb DDr3? Good enough ? ::P

---

### Post by JKyleOKC on 2011-03-07
More than good enough. I gave my Delphi VM a 16-GB hard disk and just 512 MB of RAM, and it's quite happy. The o/s is WinXP Pro with SP3 and all updates installed. The "hard disk" is actually a file, of course, but the VM treats it as a drive. This box has a much less capable CPU and only 3 GB of RAM.

I actually have seven VMs installed on this box, including the one for Delphi (Delphi 5, FWIW) but usually run no more than two of them at the same time. The rest are in "saved" state, similar to "suspend" or "hibernate" and can be restored without having to boot up.

---

### Post by Panekoek on 2011-03-08
Would Delphi not work with WINE?

---

### Post by Panekoek on 2011-03-09
bump

---

### Post by kellemes on 2011-03-09
> **Panekoek said:**
> bump

Well, why not give it a try..
Guess it largely depends on the version..
See [WineHQ]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=42")

---

