---
title: "Wine"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by farglum on 2009-04-01
I recently installed Wine. But when I tried to install a exe to it it said "install anywhere". And there isnt enough disk space to install anywhere. So i went out and bought a 1TB external hard drive. But i cant find it when it says "install anywhere". im wondering if i need to format the hard drive or something else. If anyone could help i would appreciate it.

-farglum

---

### Post by bruno9779 on 2009-04-01
What are you trying to install?

---

### Post by farglum on 2009-04-01
A program called plazmic.

---

### Post by farglum on 2009-04-01
Does it matter what program? It says i need 200mb of space. And i have 1000gb. But i browse my computer and stuff and i cant find it. I just Installed Gparted to format it so im ready for help.

---

### Post by skymera on 2009-04-01
> **farglum said:**
> Does it matter what program? It says i need 200mb of space. And i have 1000gb. But i browse my computer and stuff and i cant find it. I just Installed Gparted to format it so im ready for help.

Yes. It does matter.
Wine is not perfect and runs programs poorly at best.

What does Plazmic do?

---

### Post by pg-13(prostitute) on 2009-04-01
lol dual-boot

---

### Post by farglum on 2009-04-01
Basically it lets you edit themes for BlackBerry's using photoshop. Or Gimp in this case.

---

### Post by stchman on 2009-04-01
> **farglum said:**
> Basically it lets you edit themes for BlackBerry's using photoshop. Or Gimp in this case.

A drop dead application if ever there was one.

---

### Post by farglum on 2009-04-01
> **stchman said:**
> A drop dead application if ever there was one.

What do you mean? Does it suck?

---

### Post by stchman on 2009-04-01
> **farglum said:**
> What do you mean? Does it suck?

I was meaning fairly useless.

---

### Post by farglum on 2009-04-01
> **stchman said:**
> I was meaning fairly useless.

Well, i have a blackberry so i was wanting to make my own theme. So your saying its pretty much pointless?

---

### Post by farglum on 2009-04-01
So any help?

---

### Post by llamabr on 2009-04-01
The question was 'what does it do?' and you asked 'does it matter?' and the answer is 'yes', because running wine is always really the last resort.

Whatever it is that thing thing does, there's likely a native application that does it better, without having to debug wine every time it breaks.

It just edits jpg's for you to use as a background for your blackberry?  Why can't you do that in gimp?

---

### Post by farglum on 2009-04-02
I have no idea lol.

---

### Post by farglum on 2009-04-02
> **farglum said:**
> I have no idea lol.

In the end it turns into a zip file i think. Then an alx file.

---

### Post by farglum on 2009-04-02
So any help?

---

### Post by mikechant on 2009-04-02
> But when I tried to install a exe to it it said "install anywhere". And there isnt enough disk space to install anywhere.

Perhaps you could give some more details. This "install anywhere" thing is confusing - explain step by step exactly what you did and what happened.

---

### Post by farglum on 2009-04-02
Ok. I have the exe file on my desktop. So I right click and click 'run in wine'. Then it says 'Choose a temporary file to install to'. But when I click on any file it does the same thing. I could take a screen shot if that would help. But when I browse through my computer I cant find my external hard drive.

---

### Post by tarps87 on 2009-04-02
A few things that may help you.

The 'c:' drive in wine is in you home directory as a hidden folder, this will open it in nautilus
```
nautilus ~/.wine
```

You can configure more drives using wine config which is under applications -> wine or
```
winecfg
```
There is a drive tab which will allow you to set a folder as a new drive.

The format of the drive does not matter, I would suggest ext3.

Check here to see how well programs work on wine and if any additional steps are needed
[http://appdb.winehq.org/](http://appdb.winehq.org/)
plazmic does not appear in the data base which means no one has tested it or updated the data base with it

Hope this helps

---

### Post by tarps87 on 2009-04-02
> **farglum said:**
> But when I browse through my computer I cant find my external hard drive.

Can Ubuntu see and use the additional drive?

---

### Post by farglum on 2009-04-02
> **tarps87 said:**
> Can Ubuntu see and use the additional drive?

Yes. But when I browse Wine i cant find it

---

### Post by farglum on 2009-04-02
Im wondering if i need to reinstall Wine into the hard drive. If i can even do that. Im having some trouble configuring the drives. I can probably do it manually but i forgot the whole fdisk thing.

---

### Post by farglum on 2009-04-02
These are the two windows I click 'run in Wine'

[[IMG]http://img7.imageshack.us/img7/7908/screenshotinstallanywhe.png[/IMG]](http://img7.imageshack.us/my.php?image=screenshotinstallanywhe.png)
[[IMG]http://img7.imageshack.us/img7/screenshotinstallanywhe.png/1/w440.png[/IMG]](http://g.imageshack.us/img7/screenshotinstallanywhe.png/1/)    

[[IMG]http://img5.imageshack.us/img5/7908/screenshotinstallanywhe.png[/IMG]](http://img5.imageshack.us/my.php?image=screenshotinstallanywhe.png)
[[IMG]http://img5.imageshack.us/img5/screenshotinstallanywhe.png/1/w440.png[/IMG]](http://g.imageshack.us/img5/screenshotinstallanywhe.png/1/)

---

### Post by tarps87 on 2009-04-02
> **farglum said:**
> Yes. But when I browse Wine i cant find it

Have you added it as a drive in the wine config? You should be able to find it under /media/*drive_name*/ when browsing from a program running on wine

---

### Post by farglum on 2009-04-02
I just manually added the drive when i was configuring wine. But i still cant find it when that window comes up

---

### Post by mister_pink on 2009-04-02
If you configure it on the drive tab of the wine configuration then it will come up as a windows like drive, for example E:\, as allocated in the wine configuration.

---

### Post by Jonathan2 on 2009-04-02
I Think U Can't Install Any Programs On Any Removable Media or External I Think So Not Sure 
But If The External Hard Disk Doesn't Exist In Computer This Another Problem Make Sure It Is Probably Mount .
Not Sure And I Don't Understand Ur Question .

---

### Post by farglum on 2009-04-02
oh well

---

### Post by tarps87 on 2009-04-03
Can you post a screen shot of when you choose the location, it is usaly a tree view

---

