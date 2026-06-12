---
title: "Automounting EXT4 partition"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by thameera on 2011-02-20
I have a separate ext4 partition in my hard disk which I want to automount at login. So I added the following line in /etc/fstab:

/dev/sda4 /media/sda4 ext4 defaults 0 0

But now the device mounts in read-only mode. Need root access to change its contents. How can I mount the drive so that it does not need root privileges?

---

### Post by coffeecat on 2011-02-20
It's not actually being mounted read only, but owned by root, which is why you can't write to it.

Let it be mounted to /media/sda4, and then from a terminal:

```
sudo chown yourusername: /media/sda4
```Substitute your login name for *yourusername* and don't forget the trailing colon.This has the interesting effect of changing the ownership of the ext4 filesystem rather than the mountpoint. You will now be able to write to it.

If you want other accounts to be able to write to it, you can also:

```
sudo chmod 777 /media/sda4
```

---

### Post by Morbius1 on 2011-02-20
2 options:

(1) Take possession of the mount point:
```
sudo chown thameera /media/sda4
```(2) Change permissions so everyone can access it:
```
sudo chmod 0777 /media/sda4
```There are many variations of the two depending on your requirements.

---

### Post by Morbius1 on 2011-02-20
coffeecat, You'll have to admit that was just plain spooky  :)

---

### Post by thameera on 2011-02-20
@Morbius1, @coffeecat
Thanks a lot for the quick answers. I entered both commands in a terminal but still the contents are read-only :S
Any idea? Do I have to restart the system or something?

---

### Post by coffeecat on 2011-02-20
> **thameera said:**
> 
Thanks a lot for the quick answers. I entered both commands in a terminal but still the contents are read-only :S

Was sda4 mounted to /media/sda4? It won't work if the partition wasn't mounted. If the partition wasn't mounted you only modify the mountpoint and then those modifications get overridden when you mount it.

If you've already included that line in your /etc/fstab, then either reboot, or run:

```
sudo mount -a
```Then run the chown and chmod commands again.

If you haven't yet edited your fstab with that line then:

```
sudo mount /dev/sda4 /media/sda4
```... and run the chown and chmod commands.

---

### Post by thameera on 2011-02-20
No, I have already mounted the partition. Doesn't work though :S

---

### Post by coffeecat on 2011-02-20
> **Morbius1 said:**
> coffeecat, You'll have to admit that was just plain spooky  :)

No. Just great minds thinking alike. :wink:

To pick up your "take possession of the mount point", the interesting thing is that if the partition is mounted you actually take possession of the root of the filesystem, not the mountpoint (which I think is where the OP is going wrong atm). Which can be demonstrated if you do a 'ls -l' on /media before mounting the partition, after chown-ing it, and then again after unmounting it. It's a subtle but little-appreciated distinction. See my posts #7 and #12 in this thread for a little more:

[http://ubuntuforums.org/showthread.php?t=1658937](http://ubuntuforums.org/showthread.php?t=1658937)

Would you be so kind as to pass the word around on this? It deserves to be better known and understood. :)

---

### Post by coffeecat on 2011-02-20
> **thameera said:**
> No, I have already mounted the partition. Doesn't work though :S

OK. It should work. Let's get some more information. Post the contents of your whole /etc/fstab and the output of these commands:

```
sudo fdisk -lu
sudo blkid
ls -l /media
mount
```

---

### Post by thameera on 2011-02-20
Here are the results of the commands:


thameera@thameera-laptop:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x80028002

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    41015295    20506624   83  Linux
/dev/sda2        41017342    44920831     1951745    5  Extended
/dev/sda3        44920832   240232447    97655808   83  Linux
/dev/sda4       240232448   312580095    36173824   83  Linux
/dev/sda5        41017344    44920831     1951744   82  Linux swap / Solaris
thameera@thameera-laptop:~$ sudo blkid
/dev/sda5: UUID="0cad0cfe-d05f-401a-a101-802eff380e8b" TYPE="swap" 
/dev/sda1: UUID="4f9d9f0f-aabd-4e4e-bb2b-bab26341fcae" TYPE="ext4" 
/dev/sda3: UUID="cdfdf285-d3df-4978-b783-b908544fb41e" TYPE="ext4" 
/dev/sda4: UUID="3b41917c-7475-46c1-9942-ba28a706bcd5" TYPE="ext4" 
thameera@thameera-laptop:~$ ls -l /media
total 4
thameera@thameera-laptop:~$ 

Any ideas?

---

### Post by coffeecat on 2011-02-20
You missed out some of the things to post, particularly the output of mount and the contents of /etc/fstab. Also:

> **thameera said:**
> thameera@thameera-laptop:~$ ls -l /media
total 4


With "total=4", there should be two lines after that. Please do the 'ls -l /media command again and post all the output.

---

### Post by thameera on 2011-02-20
Sorry I had missed that, here's the output:

thameera@thameera-laptop:~$ ls -l /media
total 4
drwxrwxrwx 8 thameera root 4096 2011-02-19 05:28 sda4

---

### Post by coffeecat on 2011-02-20
> **thameera said:**
> Sorry I had missed that, here's the output:

thameera@thameera-laptop:~$ ls -l /media
total 4
drwxrwxrwx 8 thameera [COLOR=Red]root[/COLOR] 4096 2011-02-19 05:28 sda4

You still haven't give us the output of the mount command or the contents of /etc/fstab, so I can't tell from that whether the mountpoint or filesystem on sda4 is owned by you. And the root group ownership (highlighted in red) isn't going to help.

:sigh: I'm running blind here without necessary information, but try this:

```
sudo mount /dev/sda4 /media/sda4
```Ignore any error message. Now:

```
sudo chown thameera: /media/sda4
sudo chmod 777 /media/sda4
```[B]
Do not omit the trailing colon after thameera in the chown command.[/B]

Does that work?

---

### Post by thameera on 2011-02-20
When I try to mount, it says that /dev/sda4 is already mounted on /media/sda4.
When I enter the chmod and chown commands, no output comes. But still the problem exists.

Sorry about my lack of knowledge and common sense about the required data. Here's the contents of the /etc/fstab:


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=4f9d9f0f-aabd-4e4e-bb2b-bab26341fcae /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
# Commented out by Dropbox
# UUID=cdfdf285-d3df-4978-b783-b908544fb41e /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=0cad0cfe-d05f-401a-a101-802eff380e8b none            swap    sw              0       0
UUID=cdfdf285-d3df-4978-b783-b908544fb41e /home ext4 defaults,user_xattr 0 2
/dev/sda4 /media/sda4 ext4 defaults 0 0

---

### Post by Morbius1 on 2011-02-20
> But now the device mounts in read-only mode. Need root access to change its contents.Perhaps I'm reading too much into that statement but the "change it's contents" needs some clarification.

Are you talking about the ability to add or remove a file from there?

Or are you talking about the ability to edit a specific file in that partition?

The chmod command does not extend to the contents of the partition. You can make it extend to every folder and file but you need to be careful. If the partition holds another OS for example you don't want to extend permissions on the contents. 

coffecat, point taken - it was a sloppy use of the word mountpoint. I'll be careful  in the future.

---

### Post by thameera on 2011-02-20
> **Morbius1 said:**
> Perhaps I'm reading too much into that statement but the "change it's contents" needs some clarification.

Are you talking about the ability to add or remove a file from there?

Or are you talking about the ability to edit a specific file in that partition?

I cannot even open the contents of that drive. Here's a screenshot: [http://imgur.com/tOBEx](http://imgur.com/tOBEx)

---

### Post by coffeecat on 2011-02-20
> **thameera said:**
> When I try to mount, it says that /dev/sda4 is already mounted on /media/sda4.
When I enter the chmod and chown commands, no output comes. But still the problem exists.

If sda4 is mounted on /media/sda4 and you entered the chown and chmod commands exactly as I posted them, then I cannot understand why it is not working. What exactly are you trying to do? What happens when you do it?

Go to the Places menu and open 'Computer'. Now open 'File System'. Now media; now sda4. Drag and drop a file from your home folder. What happens?

Now open a terminal, and:

```
touch /media/sda4/testfile
```

Don't use sudo. What happens? Do you get an error or does a file called testfile appear in /media/sda4?

---

### Post by coffeecat on 2011-02-20
> **thameera said:**
> I cannot even open the contents of that drive. Here's a screenshot: [http://imgur.com/tOBEx](http://imgur.com/tOBEx)

That's because you are trying to access files that you wrote with root privileges before you ran the chown and chmod commands. What you have already done has enabled you write to that partition as an ordinary user, but we need to do something about those pre-existing files. That's simple:

```
sudo chown -R thameera: /media/sda4
```

---

### Post by thameera on 2011-02-20
> **coffeecat said:**
> If sda4 is mounted on /media/sda4 and you entered the chown and chmod commands exactly as I posted them, then I cannot understand why it is not working. What exactly are you trying to do? What happens when you do it?

Go to the Places menu and open 'Computer'. Now open 'File System'. Now media; now sda4. Drag and drop a file from your home folder. What happens?

Now open a terminal, and:

```
touch /media/sda4/testfile
```

Don't use sudo. What happens? Do you get an error or does a file called testfile appear in /media/sda4?

I didn't notice it before, but apparently I can copy or create files in that drive with the methods you mentioned. The newly created files don't need any permissions. However the old files are still locked.

---

### Post by Morbius1 on 2011-02-20
The line in fstab is not being mounted it's being ignored. It's showing up as "37GB ....."

Perhaps the line was added to fstab but never executed. Mount the new line in fstab:
```
sudo mount -a
```That's my best guess anyway.

---

### Post by coffeecat on 2011-02-20
> **thameera said:**
> However the old files are still locked.

Yup. I missed the bit about existing files in your first post. See my post #18 for the fix. We posted simultaneously.

---

### Post by thameera on 2011-02-20
> **coffeecat said:**
> Yup. I missed the bit about existing files in your first post. See my post #18 for the fix. We posted simultaneously.

sudo chown -R thameera: /media/sda4

The above command worked! Thanks a lot, both of you! Sorry for being such a nuisance. Thanks, again, for your time!

---

### Post by coffeecat on 2011-02-20
> **thameera said:**
> sudo chown -R thameera: /media/sda4

The above command worked! Thanks a lot, both of you! Sorry for being such a nuisance. Thanks, again, for your time!

Not a nuisance at all. :) It's good that it's sorted. Good luck!

---

