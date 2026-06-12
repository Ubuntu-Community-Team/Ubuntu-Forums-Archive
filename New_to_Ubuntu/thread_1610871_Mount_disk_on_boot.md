---
title: "Mount disk on boot"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by Brasil on 2010-11-01
Hi there, I have a LaCie external disk attached to my mythbuntu box. The issue I have is that when I reboot the drive is not accessible to mythtv unless I cycle the power to it or access it  manually (eg via thunar or the desktop icon). When correctly mounted it shows up as /media/LaCie/ Now as I understand it it isn't mounting correctly. I have worked out how to unmount it manually by sudo umount /dev/sdc1 . I tried manually mounting it by sudo mount /dev/sdc1/ /media but that doesn't appear to work. Am I heading down the right track? Is there more information required in my mount command? How do I modify fstab to fix this issue?

Grateful for any advice !

Thanks,
-Travis

---

### Post by Crusty Old Fart on 2010-11-02
Howdy Travis:

Make sure you have the "auto" option in your /etc/fstab file on the line that specifies your LaCie drive. The "defaults" option should include the auto option within it, but there's no harm in forcing automatic mounting at boot by explicitly declaring the "auto" option.
Access your fstab file with an editor of your choice (e.g.: vi, nano, etc.). I prefer vi, so...
```
sudo vi /etc/fstab
```Now add a line of code for your drive. I'll assume it's formatted as ntfs but if it isn't, you'll need to make some changes to the following example:
```

/dev/sdc1  /media/LaCie  ntfs  [COLOR=Red]**auto**[/COLOR],defaults  0  0

```This addition to your /etc/fstab should mount the drive during boot providing you have already created the directory: /media/LaCie

The man page for fstab (at least in Ubuntu) is pretty good:
```

man fstab

```If you wanted to un-mount it after boot:
```

sudo umount /media/LaCie
***...or...***
sudo umount /dev/sdc1

```Conversely, if you wanted to re-mount it after you had un-mounted it:
```

sudo mount /media/LaCie
***...or...***
sudo mount /dev/sdc1

```Get it?

---

### Post by Brasil on 2010-11-02
Hi there, thanks for your reply. OK, I've tried that. I note that you say "providing you've already created the directory /media/LaCie/". Where do I create this directory in boot, in fstab or somewhere else?

---

### Post by Crusty Old Fart on 2010-11-02
/media is a root level directory. You don't create it inside the /boot directory nor do you create it inside the fstab file.

[COLOR=DarkGreen]**STEP 1**[/COLOR]
Do this:
```

cd /
ls -al | grep media

```If you don't get any output, go to [COLOR=Red]**STEP 2**[/COLOR] below.
If you get output that looks similar to this:
drwxr-xr-x   5 root root  4096 2010-10-31 01:12 media
Then do this:
```

sudo mkdir /media/LaCie

```That should do it.

If you needed STEP 2, here it is:
[COLOR=Red]**STEP 2**[/COLOR]
Do this:
```

sudo mkdir /media
sudo mkdir /media/LaCie

```Now you should have the /LaCie directory under the /media directory, which is at root level.

More better?

Crusty

---

### Post by amitpokhrel on 2010-11-02
> **Brasil said:**
> Hi there, I have a LaCie external disk attached to my mythbuntu box. The issue I have is that when I reboot the drive is not accessible to mythtv unless I cycle the power to it or access it  manually (eg via thunar or the desktop icon). When correctly mounted it shows up as /media/LaCie/ Now as I understand it it isn't mounting correctly. I have worked out how to unmount it manually by sudo umount /dev/sdc1 . I tried manually mounting it by sudo mount /dev/sdc1/ /media but that doesn't appear to work. Am I heading down the right track? Is there more information required in my mount command? How do I modify fstab to fix this issue?

Grateful for any advice !

Thanks,
-Travis
hi..I am posting here coz i have no idea where to make a new post.
I have ubuntu 10.10 on my system.Recently I have found that I cannot open any of the folders or drives form places. when I click at any folder or drives office loading page loads but nothing opens.. please suggest me some solutions..

---

### Post by Crusty Old Fart on 2010-11-02
To amitpokhrel:

To make your own new post in this forum, [Click Here]("http://ubuntuforums.org/forumdisplay.php?f=326")

Then, near the upper left of your screen, click on the New Thread button...or...you can just [Click Here]("http://ubuntuforums.org/newthread.php?do=newthread&f=326") and you'll be taken straight to a new thread entry.

Now...with regard to your other question, I don't understand what you mean when you say:
> ...when I click at any folder or drives office loading page loads but nothing opens...But, if you open a new thread, you'll have much better luck finding someone who does understand.

Welcome to the crowd,

Crusty

---

### Post by Brasil on 2010-11-02
> **Crusty Old Fart said:**
> /media is a root level directory. You don't create it inside the /boot directory nor do you create it inside the fstab file.

[COLOR=DarkGreen]**STEP 1**[/COLOR]
Do this:
```

cd /
ls -al | grep media

```If you don't get any output, go to [COLOR=Red]**STEP 2**[/COLOR] below.
If you get output that looks similar to this:
drwxr-xr-x   5 root root  4096 2010-10-31 01:12 media
Then do this:
```

sudo mkdir /media/LaCie

```That should do it.

If you needed STEP 2, here it is:
[COLOR=Red]**STEP 2**[/COLOR]
Do this:
```

sudo mkdir /media
sudo mkdir /media/LaCie

```Now you should have the /LaCie directory under the /media directory, which is at root level.

More better?

Crusty

Thanks for that: I wasn't very clear, though, as to what I was asking. The /media/LaCie directory exists when access the drive from the GUI (ie when the drive becomes available). But it seems to disappear when I reboot. What I was asking was do I need to create this directory manually as part of the boot process?

Anyway, I created the directory, then did a sudo mount /dev/sdc1/ and it seems to be there. :) So thanks :)

---

### Post by Crusty Old Fart on 2010-11-02
Howdy Travis:

You're mighty welcome.

Now that you have created /media/LaCie manually, it should remain on your system until you delete it...and with any luck, it will always be used by your LaCie drive

If you made the entry into your fstab as described earlier, and your external drive is connected and turned on before you boot, it should mount automatically. That's what the [COLOR=Red]**auto**[COLOR=Black] option is supposed to do.[/COLOR][/COLOR]

You can always check to see what is mounted with this:
```

cat /etc/mtab

```

Even amidst a bit of confusion, it seems like you're good to go now.

Hopefully, the next time you boot up, the drive will mount by itself during boot.

Buenos Nachos,

Crusty

---

### Post by Brasil on 2010-11-02
> **Crusty Old Fart said:**
> Howdy Travis:

You're mighty welcome.

Now that you have created /media/LaCie manually, it should remain on your system until you delete it...and with any luck, it will always be used by your LaCie drive

If you made the entry into your fstab as described earlier, and your external drive is connected and turned on before you boot, it should mount automatically. That's what the [COLOR=Red]**auto**[COLOR=Black] option is supposed to do.[/COLOR][/COLOR]

You can always check to see what is mounted with this:
```

cat /etc/mtab

```

Even amidst a bit of confusion, it seems like you're good to go now.

Hopefully, the next time you boot up, the drive will mount by itself during boot.

Buenos Nachos,

Crusty

Works like a charm :) Thanks Crusty!

---

### Post by Guisphilar on 2013-03-07
Hey, I'm using Ubuntu 12.04 LTS. When I try to do sudo mkdir media/SAMSUNG is says mkdir: cannot create directory `media/SAMSUNG': Input/output error. I then tried sudo vi /etc/fstab which opens just fine but then I dont know how to write inside of it because I tried just typing and it did nothing.

---

### Post by sandyd on 2013-03-07
**Necromancing - Thread Closed**
Please do not post in threads more than one year old.

Thanks!

---

