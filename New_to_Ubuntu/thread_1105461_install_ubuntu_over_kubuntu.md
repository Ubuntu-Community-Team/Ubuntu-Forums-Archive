---
title: "install ubuntu over kubuntu"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by error919 on 2009-03-24
I decided I no longer want kubuntu but would rather have ubuntu.
(it is simpler)
No I can't use internet on kubuntu so apt-get will not do anything.
I do not want to just add gnome. I want to completly get rid of
kubuntu and install ubuntu.
Anyone know how?

---

### Post by KCG102282 on 2009-03-24
You can't without the internet and how are you posting without the internet?

---

### Post by t0p on 2009-03-24
> **KCG102282 said:**
> You can't without the internet and how are you posting without the internet?

Maybe he's using a different machine to post here.

Unfortunately, KCG102282 is half right.  It *is* possible to do it without your ubuntu machine having internet access.  But you will need to use a computer that is online.

You can use [APTonCD]("http://aptoncd.sourceforge.net/").  Make the CD, then run this command:

```
sudo apt-get install ubuntu-desktop
```

**ubuntu-desktop** is a *meta-package* - installing it will also install a heap of Gnome-based applications.

As for removing Kubuntu... I don't know an easy way to do this.  As far as I know, running

```
sudo apt-get remove kubuntu-desktop
```

 will not remove the KDE-based apps.  It may be easier to just download the ubuntu live cd .iso and install ubuntu over your kubuntu installation.

---

### Post by error919 on 2009-03-24
can I just format or repartition the linux part of the hard drive
and Install ubuntu?
Also about the internet thing.
Internet doesn't work for me on kubuntu, but it works fine on
windows.

---

### Post by KCG102282 on 2009-03-24
Yes if you have a ubuntu disk you can do that. Sorry I was under the impression you had no connection at all.

---

### Post by t0p on 2009-03-24
> **error919 said:**
> can I just format or repartition the linux part of the hard drive
and Install ubuntu?


Sure you can.  Download the ubuntu live cd .iso, or get an ubuntu cd sent to you by [shipit.ubuntu.com]("http://shipit.ubuntu.com"), then install it on the partition that is currently occupied by kubuntu.  You'll need to reformat the partition first, but the cd will help you deal with that.

**EDIT:** I suggested APTonCD and ubuntu-desktop because for some reason I'd assumed you had config files and other stuff you wanted to keep.  But if you don't mind doing a clean installation, that's certainly the way to go.

When you've got ubuntu working, come back and post the details of your non-working internet.  I'm sure someone here will be able to help you get that sorted.

---

### Post by error919 on 2009-03-24
Thanks for the help.
Ill try the format thing with the cd.

---

### Post by error919 on 2009-03-24
ok I used sudo apt-get install ubuntu-desktop.
But now I can't access it at the log in screen.
How do i go about using it?

---

