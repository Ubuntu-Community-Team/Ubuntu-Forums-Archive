---
title: "can I move /usr/src files?"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by ayu on 2009-10-06
My /usr/src folder occupies almost 10% of my 10GB harddrive, containing useless(?) files from kernel 2.6.20 etc. Can I move them to an external drive, and if necessary, copy them back when needed? Can I do this with just the file explorer, or is there some apt command I should run instead? Or is there a zip/deb archive of these files somewhere else that I can save instead, and delete everything in the src folder?

Thanks,
Ayu

---

### Post by CatKiller on 2009-10-06
Crikey, how many kernels have you got installed? My /usr/src comes in at 54.5 MB.

If you've got loads of old kernels that you aren't using any more, you can remove them in Synaptic. This will also automatically remove them from GRUB's menu.lst. If everything's currently working OK, you only need to keep the latest kernel. It should go without mentioning that you shouldn't remove all the kernels but I'll mention it anyway, just in case.

Deleting system files willy-nilly is a Bad Plan. Use the package manager for minimal breakage.

---

### Post by Cypher on 2009-10-06
First run this on the command line
```

uname -a

```
which will tell you what version of the Kernel you are currently running. Now in your /usr/src directory you should only keep the "linux-headers" directory for the Kernel you are currently running.

On my Jaunty installation, I'm at 2.6.28-15 and so in my /usr/src directory I have "linux-headers-2.6.28-15" and "linux-headers-2.6.28-15-generic". 

I can see the amount of space being taken from these two directories with
```

cd /usr/src
du -sch

```
I have
> 
64M	linux-headers-2.6.28-15
7.7M	linux-headers-2.6.28-15-generic


You will want to keep this directory around if some application wants to build something specific to your Kernel, everything else is probably extraneous and can be removed.

Just to be on the safe side though, you should list what's in that directory so that we can tell you it's safe to remove it and there's likely a APT/DBKG command to remove it properly..

Regards

---

### Post by itsbrad212 on 2009-10-06
try:

```
[FONT=monospace]sudo [/FONT][FONT=monospace]nautalis[/FONT]
```[FONT=monospace]

then navigate to the directory using the GUI (be careful, you'll be root!):P
[/FONT]

---

### Post by ayu on 2009-10-06
> **CatKiller said:**
> 
If you've got loads of old kernels that you aren't using any more, you can remove them in Synaptic. This will also automatically remove them from GRUB's menu.lst.

So if in Synaptic I just choose to remove linux-headers*, this will both clear the header files in /usr/src and clean up menu.lst?

> **CatKiller said:**
> 
Deleting system files willy-nilly is a Bad Plan. Use the package manager for minimal breakage.

Are these files actively being used or are the src files only needed when installing something?

I have no clue how it works. I would have thought 1) Download zip 2) Unzip into /usr/src 3) Compile and install exe somewhere else

But I guess I still need the newest source file lying around?

> **Cypher said:**
> 
You will want to keep this directory around if some application wants to build something specific to your Kernel, everything else is probably extraneous and can be removed.

Just to be on the safe side though, you should list what's in that directory so that we can tell you it's safe to remove it and there's likely a APT/DBKG command to remove it properly..



```

du -sh /usr/src/*
75M	/usr/src/alsa
56M	/usr/src/linux-headers-2.6.20-15
56M	/usr/src/linux-headers-2.6.20-16
56M	/usr/src/linux-headers-2.6.22-10
56M	/usr/src/linux-headers-2.6.22-9
58M	/usr/src/linux-headers-2.6.24-18
43M	/usr/src/linux-headers-2.6.27-7
43M	/usr/src/linux-headers-2.6.27-9
64M	/usr/src/linux-headers-2.6.28-11
7.6M	/usr/src/linux-headers-2.6.28-11-generic
305M	/usr/src/linux-source-2.6.20
55M	/usr/src/linux-source-2.6.28.tar.bz2
8.0M	/usr/src/nvidia-180.44
52K	/usr/src/rpm
0	/usr/src/vboxdrv-3.0.6
0	/usr/src/vboxnetadp-3.0.6
0	/usr/src/vboxnetflt-3.0.6

```


Thanks for all your help! :)

Ayu

---

### Post by Diabolis on 2009-10-06
This will remove all the uneeded packages, including old kernels.
```
sudo apt-get autoremove
```

**linux-headers** are the headers files used to compile the kernel and some other applications. You don't need them if you are not going to compile anything from source.

Just remove them with this:
```
sudo apt-get remove linux-headers
```

---

### Post by pedro3005 on 2009-10-06
You can get rid of them, i think the following command will do:
```
sudo apt-get purge linux-headers-2.6.20-15 linux-headers-2.6.20-16 linux-headers-2.6.22-10 linux-headers-2.6.22-9
linux-headers-2.6.27-7 linux-headers-2.6.27-9 linux-headers-2.6.24-18
``` You should wait for someone else to approve it though, as i'm not sure.

---

### Post by fela on 2009-10-06
My /usr/src is just 19MB. That's with kernel headers...no kernel source though as my current kernel is absolutely fine.

---

### Post by Diabolis on 2009-10-06
> **pedro3005 said:**
> You can get rid of them, i think the following command will do:
```
sudo apt-get purge linux-headers-2.6.20-15 linux-headers-2.6.20-16 linux-headers-2.6.22-10 linux-headers-2.6.22-9
linux-headers-2.6.27-7 linux-headers-2.6.27-9 linux-headers-2.6.24-18
``` You should wait for someone else to approve it though, as i'm not sure.

There is no need to specify every single package, since they are not used they will be removed. And it should be --purge not purge, which is not needed either, that argument is used to completely remove a program, this means uninstall and delete configuration files, but a kernel doesn't have that.

---

### Post by CatKiller on 2009-10-06
> **ayu said:**
> So if in Synaptic I just choose to remove linux-headers*, this will both clear the header files in /usr/src and clean up menu.lst?

Yes. But only remove the ones that you definitely don't need. You'll probably also want to remove the corresponding Linux images if you have those installed too.

> 
Are these files actively being used or are the src files only needed when installing something?They're pulled in by the nVidia driver. I have no idea if they're still needed after the install to make the nVidia driver work. You'd have to ask them.

Given that the nvidia-glx package depends on nvidia-kernel-source, which in turn depends on linux-headers, removing the last set of headers will, in all likelihood, also remove your nVidia driver.

Personally, I would use Synaptic to remove them rather than the command line as a new user.

EDIT: Actually, never mind the headers. It's the fact that you've got the whole Linux source in there that's taking up all the room. Why did you install that? Is it something you need to keep?

---

### Post by Chronon on 2009-10-06
> **Diabolis said:**
> There is no need to specify every single package, since they are not used they will be removed. And it should be --purge not purge, which is not needed either, that argument is used to completely remove a program, this means uninstall and delete configuration files, but a kernel doesn't have that.

Actually, there is no "--purge" option, it's "purge".

---

### Post by Diabolis on 2009-10-06
Just checked and you have both.
```
sudo apt-get --purge remove
```
and
```
sudo apt-get purge
```

---

### Post by ayu on 2009-10-07
> **CatKiller said:**
> You'll probably also want to remove the corresponding Linux images if you have those installed too.
How do I remove the image files? Do they take up a lot of space?

> **CatKiller said:**
> It's the fact that you've got the whole Linux source in there that's taking up all the room. Why did you install that? Is it something you need to keep?

Er, yeah, that's kind of what I'm asking :P
It probably got installed when I needed to compile a driver or something a couple of years ago. I'm wondering if I can delete it safely now to free up space.

Thanks!
Ayu

---

### Post by Chronon on 2009-10-07
> **Diabolis said:**
> Just checked and you have both.
```
sudo apt-get --purge remove
```
and
```
sudo apt-get purge
```

So they are. . . the former wasn't mentioned in the brief help but it's in the man page.  Apparently ```
apt-get remove --purge
``` is the same as ```
apt-get purge
```.

---

### Post by CatKiller on 2009-10-07
> **ayu said:**
> How do I remove the image files? Do they take up a lot of space?

Through the package manager.

>  Er, yeah, that's kind of what I'm asking :P
It probably got installed when I needed to compile a driver or something a couple of years ago. I'm wondering if I can delete it safely now to free up space.

If you installed it through the package manager, remove it through the package manager. I guess it bears repeating; deleting system files willy-nilly is a Bad Plan. Use the package manager for minimal breakage.

---

