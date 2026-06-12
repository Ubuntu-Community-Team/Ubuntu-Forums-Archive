---
title: "how to install kubuntu onto an existing ubuntu install?"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by aimpau on 2009-05-30
I know i just need to type in

```

sudo apt-get install kubuntu-desktop

```

but that would take a long time getting the files online. How do I do it using a kubuntu live cd?

---

### Post by drs305 on 2009-05-30
You could probably add the kubuntu cd to the repositories (Software Sources or Synaptic, Settings, Repositories, Third Party, Add CD-ROM). 

Then select kubuntu-desktop. You may have to disable the other repositories to force it to go to the CD instead of online.

---

### Post by aimpau on 2009-05-30
now why I didn't think of that. Thanks!

---

### Post by aimpau on 2009-05-30
oopss...sorry, doesn't work. anyone have any more ideas?

---

### Post by halitech on 2009-05-30
do you currently have ubuntu 9.04 installed or another version?

can you post the output of
```
cat /etc/apt/sources.list
```

---

### Post by aimpau on 2009-05-30
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security universe main multiverse restricted
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty-updates universe main multiverse restricted


edit

I have xubuntu 9.04 installed. I have live CD for k/ubuntu 9.04.

---

### Post by halitech on 2009-05-30
I don't see the cdrom listed at all? did you enable it and then disable it?

Use mousepad to put a # in front of the current repos, then use synaptic to add the cd then make sure you click the reload button before searching for the kubuntu-desktop package.

---

### Post by aimpau on 2009-05-30
I tried adding it using synaptic and sudo apt-cdrom but this is what it shows:

Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
E: Failed to mount the cdrom.

---

### Post by halitech on 2009-05-30
if you put the cd in can you mount it and view the files on it? Also, do you have more then 1 cdrom/dvd?

---

### Post by aimpau on 2009-05-30
1 cd/dvd rom. I can view it but FYI, it's a live CD.

---

### Post by halitech on 2009-05-30
ok, is it a cd or a dvd?

the live cd *might* be the issue, I know you can only do updates (ie 8.04 to 8.10, 8.10 to 9.04) using the alt cd so it might be the same with this but I'm not sure

---

### Post by aysiu on 2009-05-30
The Desktop CD won't work for *adding* Kubuntu.

You'll need the Alternate CD to do that.

So here are your options: [list][*]Use *apt-get* or Synaptic to add Kubuntu to Ubuntu using your internet connection[*]Download the Alternate CD and add Kubuntu by using the CD as a source instead of the internet[*]Use the Desktop CD (or "live CD") to resize the Ubuntu partition and install Kubuntu to its own partition[/list] If you have a relatively fast internet connection, go for the first option.

If you have a slow internet connection on your Ubuntu computer but a faster connection on another computer, go for the second option.

If you just want to try something else and feel like messing about with partitions and having two completely separate installations of Ubuntu, then go with the third option.

---

### Post by halitech on 2009-05-30
glad to see you around aysiu :) would it make a difference if he has a dvd drive and is using the apt-cdrom option?

---

### Post by aimpau on 2009-05-30
> **aysiu said:**
> The Desktop CD won't work for *adding* Kubuntu.

You'll need the Alternate CD to do that.

So here are your options: [list][*]Use *apt-get* or Synaptic to add Kubuntu to Ubuntu using your internet connection[*]Download the Alternate CD and add Kubuntu by using the CD as a source instead of the internet[*]Use the Desktop CD (or "live CD") to resize the Ubuntu partition and install Kubuntu to its own partition[/list] If you have a relatively fast internet connection, go for the first option.

If you have a slow internet connection on your Ubuntu computer but a faster connection on another computer, go for the second option.

If you just want to try something else and feel like messing about with partitions and having two completely separate installations of Ubuntu, then go with the third option.

I was afraid of that...:) I already knew my options even before I posted here, but since this is "The" Ubuntu forums, I thought I can walk on water. :) I'll go ahead with sudo apt-get install kubuntu-desktop then.:)

Thanks!

---

### Post by aimpau on 2009-05-30
how do I tag this thread solve again?

---

### Post by halitech on 2009-05-30
they removed that option and the thanks option awhile ago. I *think* you can edit your very first post and change the title but not sure

---

