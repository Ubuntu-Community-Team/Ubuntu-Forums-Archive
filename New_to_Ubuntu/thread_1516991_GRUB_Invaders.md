---
title: "GRUB Invaders"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by fslezak on 2010-06-24
Hello. I recently installed a copy of GRUB Invaders on my machine. Whenever I select it, the machine always restarts itself. Here is the menu entry:

```
### BEGIN /etc/grub.d/22_invaders ###
menuentry "GRUB Invaders" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set c2b6c098-9ef2-4ffd-9748-1a1080c2d885
    multiboot    /boot/invaders.exec
}
### END /etc/grub.d/22_invaders ###
```The data in /etc/grub.d/22_invaders:

```
#!/bin/bash -e

if test -e /boot/invaders.exec ; then
  source /usr/lib/grub/grub-mkconfig_lib
  INVADERSPATH=$( make_system_path_relative_to_its_root "/boot/invaders.exec" )
  echo "Found GRUB Invaders image: /boot/invaders.exec" >&2
  cat << EOF
menuentry "GRUB Invaders" {
EOF
  prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/g"
  cat << EOF
    multiboot    ${INVADERSPATH}
}
EOF
fi
```The GRUB version is 1.98 . Thanks for your help!

---

### Post by anewguy on 2010-06-24
Not sure what you are doing, as I've never tried installing this space invaders clone.  I noticed it does claim to be multi-platform.  However, I noticed that one of the things it does is try to insert the ext2 file system module.  I also noticed you are running 10.04.  I don't know if it makes any difference or not in this case, but I think be default 10.04 is ext3 or ext4.  I know the libs I've seen say ext2,ext3 and ext4 all together.

I would check to be sure invaders.exec actually exist in /boot first.  Also, I don't know if there are different versions for say Linux versus Windows.  If there is, be sure you have installed the correct one.

I'm also assuming you ran update-grub, since you seem to be able to select the option at boot, it just doesn't do anything.

Dave ;)

---

### Post by anewguy on 2010-06-25
Found something I think you'll need to do - there is a work around and patch on this link:

[http://www.coreboot.org/GRUB_invaders]("http://www.coreboot.org/GRUB_invaders")

Dave ;)

---

### Post by fslezak on 2010-06-27
Invaders.exec is there!

---

### Post by warfacegod on 2010-06-27
> **anewguy said:**
> Not sure what you are doing, as I've never tried installing this space invaders clone.  I noticed it does claim to be multi-platform.  However, I noticed that one of the things it does is try to insert the ext2 file system module.  I also noticed you are running 10.04.  I don't know if it makes any difference or not in this case, but I think be default 10.04 is ext3 or ext4.  I know the libs I've seen say ext2,ext3 and ext4 all together.

I would check to be sure invaders.exec actually exist in /boot first.  Also, I don't know if there are different versions for say Linux versus Windows.  If there is, be sure you have installed the correct one.

I'm also assuming you ran update-grub, since you seem to be able to select the option at boot, it just doesn't do anything.

Dave ;)

10.04 defaults as ext4.

---

### Post by fslezak on 2010-06-27
So... change insomd to say ext4 ?

---

### Post by fslezak on 2010-06-27
So, change insmod to say ext4?

---

### Post by chriswyatt on 2010-06-27
The only issue I have with GRUB invaders is that it uses my laptop's internal speaker, which is really really loud / harsh and as far as I can tell there isn't a way to turn it off.

---

### Post by fslezak on 2010-06-29
Again... HOW DO I GET IT WORKING?????

---

### Post by fslezak on 2010-06-30
(bump thread)

---

### Post by fslezak on 2010-07-14
<thread bumped>

---

### Post by anewguy on 2010-07-14
I tried this so I could duplicate the error and try to find a way to fix it.  I installed right from Synaptic Package Manager, and grub invaders worked the very first time.  Although I liked Space Invaders back in the day, I found this rather annoying as there are no graphics to it (I supposed so it can run on multiple platforms).

At any rate, I was not able to duplicate your error.  I would suggest the following:

- completely remove grub invaders (use Synpatic Package Manager and mark as "for complete removal" and click "apply")

- in a terminal:

sudo apt-get update

- in Synaptic Package Manager:

mark grub invaders for installation an click "apply"

- test again

If your problems continue, follow everything in the link I posted earlier very closely.

Dave

---

### Post by MooPi on 2010-07-14
I can see how you would want this, but the Open Invaders seems a better game under Linux.You can try this clone for Windows systems, [http://www.netadelica.com/coding/inv78/inv78-02.zip](http://www.netadelica.com/coding/inv78/inv78-02.zip)

---

