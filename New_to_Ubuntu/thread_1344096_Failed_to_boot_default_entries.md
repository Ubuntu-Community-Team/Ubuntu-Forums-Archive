---
title: "Failed to boot default entries"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by Tycoon timbo on 2009-12-02
I installed ubuntu, removed disc and pressed enter.  When it reboored, I entered setup and set the hard drive as first boot device and got the above error message with:

error: no such device: f56c5f4f-3a33-4f28-aa4a-3430a4c9dff9

Anyone familiar with hexadecimal who can tell me what to do?

tried booting it up again and got grub up, offering a choice of ubuntu generic or ubuntu generic recovery.  Either result in the same error message above.

---

### Post by Locke_99GS on 2009-12-02
That is a UUID; you got this when GRUB tried to load, I reckon?

If so, if you could boot back into the LiveCD and issue this command from a terminal: 

```

sudo blkid

```

and post the output. 

Also, if you know which partition you installed Ubuntu to, if you could do this:
(assuming Ubuntu 9.10 [Karmic]) - Replace sd?? with the actual device, "sda2" for example.

```

sudo mkdir /mnt/ubuntu
sudo mount /dev/sd?? /mnt/ubuntu
cat /mnt/ubuntu/boot/grub/grub.cfg

```

and post the output.


If you do not know where you installed Ubuntu, trying this may help make it apparent:

```

sudo fdisk -l

```

If you don't understand it's output and don't know where you installed Ubuntu, post it's output and we'll try to help.

---

### Post by Tycoon timbo on 2009-12-02
First of all, thankyou for helping.
You are right, I got the error message when grub tried to load.
I have got ubuntu installed using the cd and entered your code into the terminal.  This is what I got:

/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID+"f56c5f4f-3a33-4f28-aa4a-3430a4c9dff9" TYPE="ext4"
/dev/sda5: UUID="da7b9339-alf3-4749-80b9-asbb2e53c871" TYPE="swap"
/dev/sdb1: UUID="40B8D90DB8D901F8" TYPE="ntfs"

I did a full install of ubuntu.  Not too sure what the rest of your message entails.  I am swimming in deep water and need step by step instructions.

---

### Post by Locke_99GS on 2009-12-02
Try this:

```

sudo mkdir /mnt/ubuntu
sudo mount /dev/sda1 /mnt/ubuntu
sudo grub-mkconfig -o /mnt/ubuntu/boot/grub/grub.cfg

```

and see if that helps.

---

### Post by Tycoon timbo on 2009-12-02
first line of code has no effect.
second line gets:
  mount: can't find /dev/sda1/mnt/ubuntu in /etc/fstab or /etc/mtab
last line gets:
  grub-probe: error: cannot find a device for /.

:(

---

### Post by Locke_99GS on 2009-12-02
> **Tycoon timbo said:**
> first line of code has no effect.
second line gets:
  mount: can't find /dev/sda1/mnt/ubuntu in /etc/fstab or /etc/mtab
last line gets:
  grub-probe: error: cannot find a device for /.

:(

Make sure there is a space before "/dev/sda1" and "/mnt/ubuntu". Just copy and paste into the terminal.

The first command had no output because it was successful. If it didn't work, it would give you an error.

---

### Post by Tycoon timbo on 2009-12-02
I can't copy and paste as I am on my writing to you on my laptop while the pc is poorly.  Only way I could get on line.
Okay, second line went in with no hitch this time but the last line still gets the same error:
  grub-probe: error: cannot find a device for /.
Paid careful attention to the detail in the line of code, got the same result twice.
2 out of three aint bad?

---

### Post by Locke_99GS on 2009-12-02
Ok, lets try this. I haven't tried anything like this with grub2, but we'll see how it goes.

```

sudo su
mkdir /mnt/ubuntu
mount /dev/sda1 /mnt/ubuntu
mount -o bind /dev /mnt/ubuntu/dev
mount -t proc /mnt/ubuntu/proc
cd /mnt/ubuntu
chroot /mnt/ubuntu
grub-mkdevicemap
grub-mkconfig -o /boot/grub/grub.cfg

```

---

### Post by Tycoon timbo on 2009-12-02
first line got me to:    root@ubuntu:/home/ubuntu#
entering second line after that got me:   mkdir: cannot create directory '/mnt/ubuntu': File exists.
As the file exists, I ploughed ahead and entered the third line and got:
  mount: mount point mnt/ubuntu does not exist

I stopped there as this does not seem to be working.

Is it possible to format the drives and then re-install ubuntu on blank drives?

---

### Post by Locke_99GS on 2009-12-02
You can just try to install all over again, which should work. :) Before you do so, it looks like you forgot the preceeding forward-slash in "/mnt/ubuntu" on the line that got you stopped up.

---

### Post by Tycoon timbo on 2009-12-02
hands up, you are quite right.  this time I got as far as entering the mount -t line, and got lots of info about what types of mount can be done and their usage. not sure if it worked or not so went for the chroot line and got:

cannot change root directory to /mnt/ubuntu: No such file or directory

Have tried re-installing ubuntu 3 times tonight.  Each time the install runs fine but re-boot after install lands me in this particular creek.  ukripper has been helping and I changed the jumpers on the hard drives to cable select, but he has gone to bed now.  I have a gut feeling that it is somehow linked to the hard drives and having ubuntu installed on both.  Only other bug I can think of is possibly somewhere on the motherboard but have no clue as to what or where.  I wish I could be more help............

---

### Post by Locke_99GS on 2009-12-02
I'll boot to a LiveCD a bit later and try myself to see what issues I'm running into.

---

### Post by Tycoon timbo on 2009-12-02
Great.  I will try removing a hard drive and re-installing ubuntu again.  Curious how it worked perfectly on my laptop, but the world of binary can be a trifle mysterious at times eh?

---

### Post by rg_stephens on 2009-12-11
I had the same problem after I replaced the hard drive in an old Dell desktop. Strangely enough, Windows XP didn't work either. I was about to throw the old thing out. I found that the problem is a bug in Ubuntu 9.10. After doing the workaround, everything was OK. YEAAAA!

See:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/403408](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/403408)

---

