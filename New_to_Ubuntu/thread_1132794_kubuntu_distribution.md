---
title: "kubuntu distribution"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by blablaz on 2009-04-22
Hi everybody,

I am trying to figure out what command (on the shell script) should i use to know what distribution of kubuntu i am using. Not the version, the distribution.

$Thanks a lot

PS: I alredy used uname -a, cat /etc/issue, cat /proc/version ...  but i dont think it is what i need.

---

### Post by kpkeerthi on 2009-04-22
> **blablaz said:**
> 
 what distribution of kubuntu i am using
I haven't heard of a distribution of kubuntu. Kubuntu is a distribution by itself.

---

### Post by blablaz on 2009-04-22
Yes of course i meant what command (on the shell script) should i use to know what distribution of Linux i am using and only the distribution but not version

Thanks !

---

### Post by Simian Man on 2009-04-22
I don't think there is a way to do that really.  Also keep in mind that for all intents and purposes, Ubuntu and Kubuntu are the same distribution.  What I use for figuring out what Unix system I'm on is first:
```

uname -a

```

This will tell you if you are on Linux, Solaris, BSD etc and also what kernel if you are on Linux.  Then I find that you can usually get the distro from:
```

gcc -v

```

Which prints gcc's configuration info.  The last line usually includes the distro name that it was built for.

---

### Post by dawynn on 2009-04-22
Now there is one terror of a question.

Here's a basic example.
When Ubuntu first came out, they made it pretty easy to swtich from Debian simply by adding some additional repositories to the sources file, and installing the ubuntu-destop metapackage (or whatever it may have been called at the time).  

So somebody switches and they now have Debian and Ubuntu repositories in their sources list.  Which distribution are they using?

Even more basic -- using just the ubuntu repositories, I can now have installed xubuntu-desktop, kubuntu-desktop, ubuntu-desktop, edubuntu-desktop, or a combination of these.  (Note: there may be some conflict if multiple -desktop's are installed)  I may have installed from a ubuntu CD, but now have parts of several of the desktops -- allowing users to switch as they wish to.  Which *buntu distribution am I now using?

Personally, my computer is triple booted with Windows, Crunchbang, and Linux Mint.  These Linux distributions both make use of the Ubuntu repositories.  So, to a casual observer, it may look like I use Ubuntu, but with a few extra repositories.  But my system isn't even purely Crunchbang or Mint as I've added other repositories to my own liking.

Granted, we're still in the Debian-based world.  But my point is, once someone starts messing with their sources.list (or whatever the distribution uses to provide packages), the distribution stops being pure (in the case of the *buntu's, you don't even need to change repositories to switch distributions), and kind of morphs into its own personal thing.  (Not that that's a bad thing at all)  My point is, if the user has done any kind of tweaking, can the system still be called a representative of a particular distribution?

Really, the distribution is what specifically came on the CD.  But Puppy Linux taught us that even CD-based distributions are easily modifiable.  So, that's even a sticky question.

You can identify the kernel, you can identify the package repository (apt-based, rpm-based, etc.), but trying to nail any particular installation down to a specific distribution seems an effort in futility.

---

### Post by kpkeerthi on 2009-04-22
> **blablaz said:**
> Yes of course i meant what command (on the shell script) should i use to know what distribution of Linux i am using and only the distribution but not version

Thanks !
I can understand your query now.
```

lsb_release -i

```
should get you the distribution name. From what I see from [here]("http://www.unixtutorial.org/commands/lsb_release/") this lsb_release appears to be a standard linux command and not ubuntu-specific.
You can pipe the output of the above command to 'cut' or 'awk' to extract the portion you need.

```

lsb_release -i | awk -F":" '{print $2}'

```
* I have not checked this commandline myself

---

### Post by kpkeerthi on 2009-04-22
Here is what I got running that command in Arch:
```

$  lsb_release -i
Distributor ID: arch


$  lsb_release -i | awk -F":" '{print $2}'
arch

```

---

### Post by dawynn on 2009-04-22
Are you on a computer that *should* be a Kubuntu PC?  Or is this one that you truly do not know what distribution its supposed to be fore?

Note that lsb_release needs an lsb-compliant system in order to work.  For Ubuntu-based (possibly all Debian-based) systems, install the lsb package first.

BTW, there is an Arch Linux distribution.  Perhaps that's what you're using?
[http://www.archlinux.org/](http://www.archlinux.org/)

---

