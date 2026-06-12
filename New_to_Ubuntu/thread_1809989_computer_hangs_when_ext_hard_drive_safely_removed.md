---
title: "computer hangs when ext hard drive safely removed"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by PurpleF on 2011-07-22
Recently, whenever I remove my Seagate 1Tb external hard drive, using the "safely remove" command, my computer hangs/freezes.  I've used this external drive with no problems for several years, so any ideas please on either what the problem is, and how I can solve it.  Non techie speak much appreciated :)

---

### Post by relay_man on 2011-07-23
I think I recall having this problem before when using the "remove safely" command from the menu.

Now when I have a problem device that will not unmount from the menu, 
I go to the terminal and enter the command "mount". (See example below
removable drive shown in red)


```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/michael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=michael)
[COLOR="Red"]/dev/sdb1 [/COLOR] on /media/New Volume type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
```

In this case, the system recognized my drive and says that it is mounted to the file system @ /dev/sdb1

So, to safely unmount the device I enter the command:

umount /dev/sdb1

(NOTE: the command to unmount a device is "umount" NOT unmount)

This may be a little more trouble than just using the command from the menu, but I've not had it fail me yet and it is much better than having to restart my system and worrying about damage.

Hope this helps  :)

---

### Post by PurpleF on 2011-07-23
Many thanks Relay-Man, I'll give it a try once I'm sure what I'm doing.  Much appreciated.

---

### Post by PurpleF on 2011-07-25
I checked regarding the "mount" command, (you learn something new every day) and my external hard drive showed as  /dev/sdb1 so did the umount /dev/sdb1 and got the following message 

umount:  /dev/sdb1 is not in the fstab (and you are not root)

all of which means nothing to me!

Any more info please relay-man or anyone, gratefully received please.

---

### Post by relay_man on 2011-07-25
Hi Purple

Rest assured that there are others here who are MUCH better at explaining these things than I am, so maybe someone else will jump in here to help. But I will give it a try.

How you enter text when in terminal is critical.
I noticed in your post that the command to unmount your drive appeared to be given as:

umount:/dev/sdb1

I know you may not have entered it exactly like that, but let's break that down some.  The command should look like:

umount /dev/sdb1

Note that there is no colon after the command umount.
There must be a single space between the "t" in umount and the 
forward slash that precedes "dev"

Most commands that are invoked in terminal will use the same structure.
The command name, then a single space, then the file name or device location etc.


Next, the file fstab is located in the etc directory. ( /etc/fstab )
The fstab file is read by the system and it contains i.d. information about devices that should be mounted at each boot and mounted automatically when connected otherwise. (like your portable disc)

I've include mine as an example below.

```
 # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=93dd0f74-8818-4ba1-a228-8336a7048e59 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=830f2b11-71a1-4155-8c40-33cfab830d1f none            swap    sw              0       0
```



Much useful info about fstab can be learned by reading the manpage.

(At the terminal, enter:   man fstab )

If you have persistent trouble connecting and removing your drive, the man page can help you construct a statement that you can add to your
fstab file which will help the system identify and mount your drive automatically when attached/removed.


In the error message you were given, the statement was made that you were not "root".
When you start and log in to your system normally, your ability to install, edit, or move important/critical files is prohibited.  This is good because it protects you from having one those "oh no" moments.
Conversely, root is the owner or "super user" of your system.   
Root has NO power limitations.  When you become root, you can change, copy, move, remove, alter, add, invert, cover with chocolate (not really)
any file, directory, or device in any way you like.
So, if you log in as root or use sudo to become root, you can literally destroy anything and completely disable your system.
More than ninety nine percent of the time you do NOT need to be root.
Nor should you be.  You also do not normally need to be root to unmount
your usb disc.
(you will have to be root however, if you decide to edit your fstab file.
Don't log in as root to do this.  Read the manpage about "sudo")


Whew!  

My first question is:  Did you construct the command correctly?

---

### Post by PurpleF on 2011-07-26
You're great relay-man, thanks for all the info.  Sorry about the delay in replying, I'm all ears now!

I had another go and I believe I did it right.  This time I copied what was on the terminal so you can see.

                     p { margin-bottom: 0.21cm; }  fiona@fiona-desktop:~$ mount 
 /dev/sda5 on / type ext4 (rw,errors=remount-ro) 
 proc on /proc type proc (rw,noexec,nosuid,nodev) 
 none on /sys type sysfs (rw,noexec,nosuid,nodev) 
 none on /sys/fs/fuse/connections type fusectl (rw) 
 none on /sys/kernel/debug type debugfs (rw) 
 none on /sys/kernel/security type securityfs (rw) 
 none on /dev type devtmpfs (rw,mode=0755) 
 none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620) 
 none on /dev/shm type tmpfs (rw,nosuid,nodev) 
 none on /var/run type tmpfs (rw,nosuid,mode=0755) 
 none on /var/lock type tmpfs (rw,noexec,nosuid,nodev) 
 none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755) 
 binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev) 
 gvfs-fuse-daemon on /home/fiona/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=fiona) 
 /dev/sdd1 on /media/Expansion Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions) 
 fiona@fiona-desktop:~$ umount /dev/sdd1 
 umount: /dev/sdd1 is not in the fstab (and you are not root) 
 fiona@fiona-desktop:~$  
 
It looks like I left the space OK but got the same result.  The colon is in the response from the terminal.   I'm really scared by what you say about fstab and the man page, especially as whatever I do I can't get anything covered in chocolate. Computer manufacturers need to get onto this, plus doing the ironing!  This would come as standard if it were a woman page! Seriously though, it does all scare me.

I really appreciate how you are "talking me through this" and I've had a couple of strong cups of coffee and a ciggie ready for the next stage.  

What is life if you don't learn something new each day?  Over to you please relay-man.:confused:

---

### Post by skatinjj on 2011-07-26
To umount you need to use sudo command so:

```
sudo umount /dev/sdd1
```

if that does not work then:

```
sudo umount "/media/Expansion Drive"
```

---

### Post by amjjawad on 2011-07-26
> **PurpleF said:**
> Recently, whenever I remove my Seagate 1Tb external hard drive, using the "safely remove" command, my computer hangs/freezes.  I've used this external drive with no problems for several years, so any ideas please on either what the problem is, and how I can solve it.  Non techie speak much appreciated :)

Is it Ubuntu 10.04 or 11.04???

---

### Post by PurpleF on 2011-07-26
Hi Scatinjj and Amjjawad, thanks for your input.  I'll give the sudo unmount a try once I've logged off from the forum and let you know how it goes.  

It's 10.04 Lucid Lynx Amjjawad as I stick with what I'm used to.  

I'll get back shortly.

---

### Post by skatinjj on 2011-07-26
The command is

```
sudo umount /dev/sdd1
```

It is not unmount

---

### Post by amjjawad on 2011-07-26
> **PurpleF said:**
> It's 10.04 Lucid Lynx Amjjawad as I stick with what I'm used to. 

If it was 11.04, I wouldn't be surprised but it's 10.04 so it's a bit weird to me.

Do you have another machine at home? if yes, try that and see if you get the same issue.
Try the commands in the other post and hope that will help you!

Good luck ;)

---

### Post by PurpleF on 2011-07-26
Thanks for that reminder re the umount skatinjj, I DID remember what relay-man said about that.

Well, I gave it a try and the result was as follows

gvfs-fuse-daemon on /home/fiona/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=fiona)
/dev/sdd1 on /media/Expansion Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
fiona@fiona-desktop:~$ sudo umount /dev/sdd1
[sudo] password for fiona: 
fiona@fiona-desktop:~$ sudo umount /dev/sdd1
umount: /dev/sdd1: not mounted
fiona@fiona-desktop:~$ sudo umount "/media/Expansion Drive"
umount: /media/Expansion Drive: not found
fiona@fiona-desktop:~$ sudo umount "media/Expansion Drive"
umount: media/Expansion Drive: not found
fiona@fiona-desktop:~$ 

I don't understand it  "not found" as there it is on the list!  The expansion drive is sitting there glaring at me with it's green light!  Any other suggestions would be most welcome please folks. :(

---

### Post by PurpleF on 2011-07-26
Sorry amjjawad, I'm a 1 computer gal, nice try.  Can you imagine what a mess I'd make of multiple computers!!!!!!!!;)

---

### Post by amjjawad on 2011-07-26
Unplug your External HDD, restart your machine, login to Ubuntu and then plug it.

Repeat the previous commands and let's see what will happen.

Please, whenever you post an output for any command, make sure to wrap up the text (output) with "CODE" tags or "#".

:)

---

### Post by skatinjj on 2011-07-26
When you use umount, you get no output to say it worked.  Since there were no errors, it seems it unmounted successfully.

You can verify that with the mount command (no sudo needed).  That will list mounted devices and mount points.

As for the light, if its not blinking then there is no activity, it just has power to it.

---

### Post by amjjawad on 2011-07-26
> **PurpleF said:**
> Sorry amjjawad, I'm a 1 computer gal, nice try.  Can you imagine what a mess I'd make of multiple computers!!!!!!!!;)

If you won't make any mess, you will never learn, trust me :)

I'm doing my best to mess with my computers and produce some errors but ... guess I'm not that lucky :P

---

### Post by PurpleF on 2011-07-26
Hiya skatinjj, what a revelation!  I thought because the light was on it was still "mounted"  Thanks so much for that.

Hiya amjjawad, I reckon skatinjj has put the spolight on the problem, I'm so naive I just assumed it was still "mounted" but thanks for the suggestion.  It seems I've done something wrong regarding out put commands judging by your last sentence.  I'm really sorry.  Please could you explain what wrap up the text etc means so I know what to do another time please?

---

### Post by skatinjj on 2011-07-26
You know after like a million dual boot setups I still managed to wipe my XP partition the other day (installed ubuntu right over-----VROOM!XD).

I now have 300,000+ files that start with the letter F to sort through =(

So like stated, gotta make messes to learn....

And before its said, my back up drives failed....

---

### Post by amjjawad on 2011-07-26
> **PurpleF said:**
> Hiya amjjawad, I reckon skatinjj has put the spolight on the problem, I'm so naive I just assumed it was still "mounted" but thanks for the suggestion.  It seems I've done something wrong regarding out put commands judging by your last sentence.  I'm really sorry.  Please could you explain what wrap up the text etc means so I know what to do another time please?

Sure thing, Fiona :)

When someone asks you to post the output of any command, you need to put "CODE" between [ ] at the beginning and the same "CODE" between [/] at the end.

So, it would look like this:

```
sudo apt-get update

```

OR

You can highlight the text (the output) and click "#". You see that "#" above the text box where you type? there you go :)


If your problem is fixed, please ...

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=7263[/IMG]


Please let us know if you need any more help :)

---

### Post by skatinjj on 2011-07-26
As for the freezing its a kernel bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/811745]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/811745")

Problem fixed by rolling back to an older kernel.

---

### Post by PurpleF on 2011-07-26
Thank you amjjawad, I see what you mean now.  I've made a note of it and will do it properly next time.  So glad you put me right.  Wouldn't want to be a sour cup of Ubuntu would I!

Thanks everyone for your help, much appreciated

---

### Post by skatinjj on 2011-07-26
You can run to display the running kernel:

```
uname -r
```

If you have the kernel in question, you can install an older kernel to use.

---

### Post by amjjawad on 2011-07-26
> **PurpleF said:**
> Thank you amjjawad, I see what you mean now.  I've made a note of it and will do it properly next time.  So glad you put me right.  Wouldn't want to be a sour cup of Ubuntu would I!

Thanks everyone for your help, much appreciated

You welcome at anytime and enjoy Ubuntu ;)

And remember, if you won't break things, you will never learn how to fix them :)
It might be scary at the beginning but by time, it will be so easy :)

Have a great time!

---

### Post by Moonlight_Gambler on 2011-07-29
I'm not really a Terminal person, so what works for me is Disk Utility.

Select the drive from the left, then "Unmount", then "Safely Remove".

---

