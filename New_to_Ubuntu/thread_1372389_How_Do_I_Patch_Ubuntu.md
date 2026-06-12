---
title: "How Do I Patch Ubuntu?"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by NeverMind785 on 2010-01-04
I posted this in general help but I didn't get any answers. Could beginner talk help me out?

I found a patch for a problem I've been having with ubuntu. The sound comes out of my headphones but not out of my speakers. It's really getting on my nerves. 

The thing is, I don't know how to use the patch. I would really appreciate it if someone could tell me how to install it or whatever.

I found the patch here: [http://patchwork.kernel.org/patch/49477/](http://patchwork.kernel.org/patch/49477/)

Thanks

---

### Post by USB_NL on 2010-01-04
hi have you richt clicked the speaker icon and opened sound preferences before?

look at OUTPUT tab
Connector

have you seen thoose option there before?

---

### Post by NeverMind785 on 2010-01-04
Yeah I have. It says: 
Connector: Analog Output

---

### Post by USB_NL on 2010-01-04
> **NeverMind785 said:**
> Yeah I have. It says: 
Connector: Analog Output

ok that's not the problem

---

### Post by bacardiandwatermelon on 2010-01-04
This isn't really my thing, but normally you download the source code for a driver, patch it, then compile it and install it. It has been ages since I have done any patching but I think it goes something like..
```
sudo patch -p0 < patch.diff
```

---

### Post by bacardiandwatermelon on 2010-01-04
I just found these.. They may help..
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205)

---

### Post by NeverMind785 on 2010-01-05
> **bacardiandwatermelon said:**
> I just found these.. They may help..
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205)

The thing is, I don't use netbook remix. Also, I can't find my computer on the list of computers in the first link. I don't know what I'd put in for my computer if mine isn't on there.

---

### Post by spiderbatdad on 2010-01-05
> **bacardiandwatermelon said:**
> This isn't really my thing, but normally you download the source code for a driver, patch it, then compile it and install it. It has been ages since I have done any patching but I think it goes something like..
```
sudo patch -p0 < patch.diff
```

Ditto, but I'll try to help. This presumes you have saved the patch in a file called patch.diff
This patch appears to assume you are already  in /usr/src/linux-headers-generic...or which ever you boot. That is the patch file start in sound/pci/hda/ note without a leading / before sound. I think that Ubuntu does not use a trailing / on directories therefore the -p0 option seems correct instead of -p1.
So if you cd into /usr/src/linux-headers-<your kernel> you should be able to apply the patch with the above command. For this command to execute you would need patch.diff in the same directory...a full path to the file might work also.

There is a good example of applying patches here: [http://www.linuxforums.org/articles/using-diff-and-patch_80.html](http://www.linuxforums.org/articles/using-diff-and-patch_80.html)

Note: I do not know what will happen when you apply the patch, but I'm never afraid to break my system to try something new. There is a -b option to create a backup of the original makefile for you, explained in man patch.

---

