---
title: "Trying to manually install ATI driver, &quot;extraction failed&quot;?"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by BigWoop on 2009-08-31
I'm following this guide, [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually)

I'm only at step 2 and I get this,

user@MesaLinux:/media/Temp/stuff$ sh ati-driver-installer-9-8-x86.x86_64.run --buildpkg Ubuntu/jaunty 
Created directory fglrx-install.ClUZVd
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.64......................................................
.............................................Extraction failed.
Signal caught, cleaning up


What do I do? I'm clueless.

---

### Post by jbrown96 on 2009-08-31
It looks like your download is corrupt. Try downloading again.

Don't follow that procedure either. It's really bad. There's only two steps to installing it.
1) download it
2) run it. ```
sudo sh /media/Temp/stuff/ati-driver-installer-9-8-x86.x86_64.run
``` You don't need to build any .debs first, and the xorg.conf file is configured automatically.

---

### Post by BigWoop on 2009-09-01
I tried moving the file to my home directory and then it seemed OK (It stopped 'cos I forgot to use sudo but it never said anything about the extraction failing i.e. it got past that point), before I was running it from a separate NTFS partition, why would that stop it from working?

What exactly is wrong with that other process that I posted? I'm not dead set on using it I just presumed it would be easier to remove if I have problems if it was installed from a .deb?

---

### Post by BigWoop on 2009-09-02
OK well I tried the install and it all seemed to work fine, but the driver doesn't appear to be working properly.

After I rebooted I could definitely see a difference, but it's performing dismally (dragging windows is very jerky), won't let me enable visual effects, and the control center won't open at all.

What should I do?

---

### Post by Mark Phelps on 2009-09-02
Do you know for sure the driver installed? Open a terminal and enter "fglrxinfo" to confirm the driver got installed and is being used.

What make/model video card are you using?

---

### Post by automaton26 on 2009-09-02
Your first attempt probably failed because you don't have write permission to NTFS partitions by default.

I'm not at my ubuntu machine at the moment, but (from memory) you might try:

```
sudo apt-get install ntfs-config
```

I think (?) that's a graphical front end for NTFS-3G which will let you configure your NTFS partition for read/write. Anyway, as you found out, you can move it to your home folder, which you have write permission for, and run it from there.

As for the ATI driver, ATI stopped supporting certain cards after version 9.3. Try researching your card model and if it's not supported any more, you'll have to stick with the default open source drivers. Or install an older ubuntu that will work with version 9.3 of the drivers.

You can easily check if your proprietary drivers are working at any time by doing:

```
glxinfo | grep direct
```

If it says "Direct rendering: Yes" then it's working.

---

### Post by BigWoop on 2009-09-02
I guess not because all I get from that command is this (Also from glxinfo),

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14

I presumed that it had installed as when I restarted my resolution was higher, and I also noticed a slightly different feel to the picture, performance dropped a lot too and not just due to the resolution.

When I did the install I got an error about the DKMS part of the installation failing but the way it worded it sounded like it didn't really matter, I was wrong maybe.

I read that it (DKMS) has something to do with the driver being able to recompile automatically if you install a new kernel, so it would be cool to fix that too if it's not the main problem anyway.

Another thought, I have installed both the rt kernel and the generic kernel, how will the driver function correctly with both if it has to be specially compiled for each?

My card is an HD4670.

---

### Post by automaton26 on 2009-09-03
Sorry, I had a proper look at the guide you were following and I didn't do any of that.

From a clean install of Jaunty, all I did to get it my ATI card working was:
[INDENT][http://ubuntuforums.org/showthread.php?t=1205418#7]("http://ubuntuforums.org/showthread.php?t=1205418#7")[/INDENT]

The next poster down says they got it working with their HD 4670.

---

