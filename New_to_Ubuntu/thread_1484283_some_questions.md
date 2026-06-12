---
title: "some questions"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by tekno62 on 2010-05-15
My parents computer was owned by a malware attack and I have given up on supporting windows. 

I use Wubi as for some reason both CD and DVD drive would not burn the ISO. 

Now I have what seems to be 2 grub boot sessions one is for windows and Ubuntu and then the next one is for what version of Ubuntu. is there away to just get it to boot Ubuntu ( made it the default till I can get some files off that system ) 

Next thing is my parents play alot of games on King.com. right now King.com hates anything lunix - there away to make king think my parents are using windows xp.

also would like to know how to make it so when they kick on the firefox address bar the all the litters are high lighted.

---

### Post by Ozymandias_117 on 2010-05-15
> Now I have what seems to be 2 grub boot sessions one is for windows and Ubuntu and then the next one is for what version of Ubuntu. is there away to just get it to boot Ubuntu ( made it the default till I can get some files off that system ) 

No. The first one is Windows' Boot loader, then when you select Ubuntu, you have to go through Grub (A popular GNU/Linux Boot Loader).

---

### Post by Paddy Landau on 2010-05-15
If you are going to stop using Windows, then I would also stop using Wubi and instead do a proper native installation of Ubuntu. Your Wubi is vulnerable to faults in Windows.

If you need to use Windows, you'll have to either reinstall or get a professional (or yourself) to clean it.

Either way, remember to back up your data first.

There exists a thing called *Wine* to run Windows programs on Linux. Unfortunately, it works for only a small portion of Windows programs.

Luckily, there exists a thing called [PlayOnLinux]("http://www.playonlinux.com/"), which makes using Wine far easier. PlayOnLinux will install Internet Explorer 7 for you on Linux. I'd try that with your King.com.

Remember to check that Wine is installed on your system (it's in the repositories) before you install PlayOnLinux.

EDIT: I see that king.com doesn't dislike only Linux, but anything that's not Windows. Funny!

---

