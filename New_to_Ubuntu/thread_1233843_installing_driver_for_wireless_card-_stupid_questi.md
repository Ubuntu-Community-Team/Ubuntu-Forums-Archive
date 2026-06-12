---
title: "installing driver for wireless card- stupid question"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by mimicoco on 2009-08-07
Hello!

I've spent the last two days trawling the forums to find the answer to this, and its there, I can see it, but i just don't speak enough geek to get it working :(

I have a D-link g630 wireless card, ubuntu jaunty installed and no internet connection on that computer. I managed to download on another computer the driver LINUX_DWL-G630_v1.0.3.0.tar.gz (from a spanish site no less) and get it to my jaunty desktop still compressed. 
  
so sorry for the really dumb question-- but how do i istall the driver from the TAR file? I've read the pocket guide, and am thinking that this is something so simple that there are no instructions?

---

### Post by 3rdalbum on 2009-08-07
Sorry to say this, but it's not "so simple that there are no instructions". I guess they think that anyone who wants to manually install a driver, will already know what to do.

Can you plug the computer straight into a free Ethernet port on your router? You will need to use Synaptic Package Manager to install the "build-essential" and "linux-headers" packages.

Once they are installed, you decompress the .tar.gz file using File Roller. Open a terminal and navigate to the decompressed directory (type "cd" and a space, and then drag the folder icon to the terminal, and run that as a command).

Now generally you'd type:

```
make
sudo make install

```

And then reboot.

---

### Post by mimicoco on 2009-08-07
Thankyou 3rdalbum!

Actually, it seems that my level of comprehension is so low that up near the date on my desktop i clicked on a radio button and the card started working all by itself! 

Im online hooray! Thanks for your help anyway!:D:D:D

---

### Post by 3rdalbum on 2009-08-07
Oh okay, sorry I assumed you had already checked the Network Manager.

---

### Post by tarps87 on 2009-08-07
> **3rdalbum said:**
> Sorry to say this, but it's not "so simple that there are no instructions". I guess they think that anyone who wants to manually install a driver, will already know what to do.

Can you plug the computer straight into a free Ethernet port on your router? You will need to use Synaptic Package Manager to install the "build-essential" and "linux-headers" packages.

Once they are installed, you decompress the .tar.gz file using File Roller. Open a terminal and navigate to the decompressed directory (type "cd" and a space, and then drag the folder icon to the terminal, and run that as a command).

Now generally you'd type:

```
make
sudo make install

```

And then reboot.

**@3rdalbum** I don't know if you will find this useful but build-essential and I'm sure the linux-headers package for the kernel installed using the cd are on the cd. All you need to do is apt-cdrom add *cdrom* and update and install.
Just thought I'd share it.

---

