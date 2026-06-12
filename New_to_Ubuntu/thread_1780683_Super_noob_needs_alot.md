---
title: "Super noob needs alot"
date: 2011-06-12
forum: New to Ubuntu
---

### Post by Badluckchuck on 2011-06-12
Hello-

I am about as new as it comes when it comes to understanding linux. So please stay with me.  I decided to try linux cause I honestly just wanted to try something other than M$....

Ok-

So I spend most of my day the other day installing/setting up 10.10 on laptop.  I surfed through these forum pages and google for what seems like the entire day...

- I have a intel SSD that I am using for my main/primary drive.  I have been TRYING to find a place where I can set everything up to be optimized for SSD.  I did find a way to enable the TRIM, however writes cycles, RAM disk, and the rest of what is probably easy- I could NOT comprehend.  Sadly, from what I had found...you kinda had to have had an idea as to what you were doing already. I learned this the hard way since I did brick the OS in this enabling TRIM process....twice lol

Someone Please give a "for morons" idea/breakdown for me here...

-I am very familiar with M$, OSx, and hardware- so please feel free to reference...

---

### Post by VOT Productions on 2011-06-12
Welcome to the Ubuntu Forums!
I'm sure this thread will help you ([http://ubuntuforums.org/showthread.php?t=1463870](http://ubuntuforums.org/showthread.php?t=1463870))

---

### Post by Badluckchuck on 2011-06-12
Hello,

Thank you so much for the quick response....

Sadly though, most of those are the exact pages I have book marked (my fault for lack of details, new the forum life as well) I dont have any issues getting to the editor or anything.  I guess what I dont understand that I need to so is with the placement of everything, for ex.

"Add this line to fstab to mount /tmp (temporary files) as tmpfs (temporary file system):
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0"

where am I adding these lines of code? in the middle, end of the string? or copy/paste after the "ext4 discard,mount..." and stick is somewhere in the middle? Within most of the links I find and such, most are giving you just the code to enter and assuming that you already are a few steps ahead of where my head is.  

Then obviously after I reboot (and home I didnt brick it again) is bring up the gedit again and make sure the command stuck...  

I will def. take another stab at it, for some of the links are written/explained a little clearer (well to me anyway) and will post back later on with results.  Ty again!

---

### Post by cchhrriiss121212 on 2011-06-12
Setting up an SSD is quite simple for newer linux distros (like 10.10) as they have a kernel with TRIM support. There is no other configuration that is necessary, that tmpfs stuff is not something you need to worry about.

For other optimisations you can edit fstab and add mount options. To do that enter this into a terminal:
```
sudo gedit /etc/fstab
```
Then just add "noatime" and "discard" options to any partitions on the drive. Here is what mine looks like for example:
> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=d1b27a1b-f0ea-442b-a921-018064dfb058 /               ext4    noatime,discard,errors=remount-ro 0       1
This should increase performance slightly.

---

