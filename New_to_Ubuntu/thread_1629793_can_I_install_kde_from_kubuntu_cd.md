---
title: "can I install kde from kubuntu cd?"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by dhiman33 on 2010-11-24
:guitar:I wonder if I can install kde in my ubuntu 10.10 from the kubuntu 10.10 cd I have. It would save time as I have slow net connection--- is this possible? :rolleyes:

Also, how big is the kde download in mb? How to switch between gnome & kde after I install it? And would it make ubuntu sluggish or buggy? Pls reply soon... Thnks in advance.):P

---

### Post by BugBuster on 2010-11-24
If you have the 'alternate' install cd for Kubuntu then this is possible. If it's a live (desktop)cd then I dont think its possible.

---

### Post by dhiman33 on 2010-11-24
Nooooooo..........:cry:](*,):cry:. Anyone else knows a way?[-o<[-o<

---

### Post by theozzlives on 2010-11-24
Try adding the CD to your repositories. then do:
```
sudo apt-get install kubuntu-desktop
```
after all is said and done, you should be able to switch sessions at the login window.

---

### Post by dhiman33 on 2010-11-24
How to add the kubuntu(live) cd to the rep?:-\"

---

### Post by BugBuster on 2010-11-24
> **theozzlives said:**
> Try adding the CD to your repositories. then do:
```
sudo apt-get install kubuntu-desktop
```
after all is said and done, you should be able to switch sessions at the login windows.

This can be done only with a alternate cd as all the deb packages are available on it and can be added to apt as a repo, while a live cd contains a pre-configured installation that is packed tightly in a squashfs file.

The live cd, unfortunately in the op's case, contains only a few debs and not all that are configured on it.

---

### Post by dhiman33 on 2010-11-24
If u say so, I think it's impossible now. But what abt the other questions?(size of kde,would it make ubuntu slow?)

---

### Post by BugBuster on 2010-11-24
> **dhiman33 said:**
> If u say so, I think it's impossible now. But what abt the other questions?(size of kde,would it make ubuntu slow?)


Cannot comment on this one...GNOME is all I have been using since the day I started using linux. Someone else might surely be able to guide you on this.

---

### Post by theozzlives on 2010-11-24
> **BugBuster said:**
> This can be done only with a alternate cd as all the deb packages are available on it and can be added to apt as a repo, while a live cd contains a pre-configured installation that is packed tightly in a squashfs file.

The live cd, unfortunately in the op's case, contains only a few debs and not all that are configured on it.

I've done the restricted drivers for my wireless off the live CD.

---

### Post by dhiman33 on 2010-11-24
:shock:OMG, now I'm confused----- someone tell me being sure if it is possible to install kde from kubuntu live cd.

---

### Post by BugBuster on 2010-11-24
> **theozzlives said:**
> I've done the restricted drivers for my wireless off the live CD.

Sure you may have..as I said the live cd contains only a few debs and you were lucky to find what you needed were among them.

---

### Post by pawhtiobo on 2010-11-24
To add the CD-Rom to the repository:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[https://help.ubuntu.com/8.04/add-applications/C/offline.html](https://help.ubuntu.com/8.04/add-applications/C/offline.html)

See ya...

---

### Post by dhiman33 on 2010-11-24
Do all people agree with bugbuster? O.k, then pls say how big is the install and if it's gonna make ubuntu sluggish?....pls answer...:neutral:

---

### Post by Verbeck on 2010-11-24
from synaptic :
219mb  have to be downloaded 
729mb of extra space will be used
(might be more, i've got some kde apps installed)

afaik, the speed would depend on your computer's specifications

---

### Post by msjones on 2010-11-24
I think the KDE desktop is very heavyweight. Seems to be sluggish even on high end systems. For me at least.

Gnome & Xfce are, for me, the best windows managers.

---

### Post by brennydoogles on 2010-11-24
> **msjones said:**
> I think the KDE desktop is very heavyweight. Seems to be sluggish even on high end systems. For me at least.

Gnome & Xfce are, for me, the best windows managers.

I'm going to have to agree with msjones, my experience with KDE was this: very pretty, but frustrating to use because of speed and difficulty to configure properly.

---

### Post by dhiman33 on 2010-11-25
Ok, if kde is that big and that sluggish, I'd like to forget it atleast for now:-\". But there are so many good kde softwares... can u tell me one time download of a list of packages that will enable me 2 install most of kde softwares with download size within 5-10 mb:KS?(right now **any** kde software would require me to download abt. 40 mb-50 mb!!:evil:)

---

### Post by masaibana on 2010-11-25
I have kubuntu dvd, so it easier to install. Its true. Kubuntu is a little bit sluggish. I need to install ubuntu first, than upgrade it to kubuntu, to get gnome+kde with low net bandwith. As I see, ubuntu is powerful, but kubuntu is beautiful. So I have to keep both of it. I dont think kubuntu that heavy, it depends on the configuration (maybe).. and ram. On idle it consume my ram memori about 1GB to 1.5GB.

---

