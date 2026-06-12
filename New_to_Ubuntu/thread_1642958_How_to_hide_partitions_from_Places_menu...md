---
title: "How to hide partitions from Places menu.."
date: 2010-12-11
forum: New to Ubuntu
---

### Post by karthick87 on 2010-12-11
The drives should be visible only in nautilus..I want to hide the drives from Places Menu..Is it possible..??Any GUI method will be appreciated??

[IMG]http://imgur.com/7Bmfb.png[/IMG]

---

### Post by supererki on 2010-12-11
alacarte - easy GNOME menu editing tool

I think that this is frontend for gconftool

---

### Post by 73ckn797 on 2010-12-11
> **supererki said:**
> alacarte - easy GNOME menu editing tool

I think that this is frontend for gconftool

This is already installed in 10.04 and is the "Main Menu" tool under System/Preferences.

---

### Post by ajgreeny on 2010-12-11
> alacarte - easy GNOME menu editing tool

I think that this is frontend for gconftool 	
I don't think that allows the Places menu to be edited in any way.  You may find a setting in the gconf-editor, but I'm not sure.  The other way to look at, though again I don't know if it works, is to mount the partitions somewhere else than /media.  That will certainly stop them appearing on the desktop as icons, but may not remove them from Places.

Give it a try!

---

### Post by Rubi1200 on 2010-12-11
> **ajgreeny said:**
> I don't think that allows the Places menu to be edited in any way.  You may find a setting in the gconf-editor, but I'm not sure.  The other way to look at, though again I don't know if it works, is to mount the partitions somewhere else than /media.  That will certainly stop them appearing on the desktop as icons, but may not remove them from Places.

Give it a try!
I read something about this recently, but don't recall where now.

In any event, I believe the answer is that it is nigh on impossible to remove the drives from the Places menu (it certainly cannot be done from the current gconf-editor settings if I recall correctly). What you can do is create/delete shortcuts for things like the Downloads folder etc.

If I find the information again I will post it here.

EDIT:
as I said, you can add/remove links for folders in the Places menu.
Open the > ~/.gtk-bookmarks file with your favorite editor and make changes.

The same thing can also be achieved by opening any folder e.g. Home and going to the Bookmarks tab and editing from there.

---

### Post by ajgreeny on 2010-12-11
> **Rubi1200 said:**
> I read something about this recently, but don't recall where now.

In any event, I believe the answer is that it is nigh on impossible to remove the drives from the Places menu (it certainly cannot be done from the current gconf-editor settings if I recall correctly). What you can do is create/delete shortcuts for things like the Downloads folder etc.

If I find the information again I will post it here.

EDIT:
as I said, you can add/remove links for folders in the Places menu.
Open the  file with your favorite editor and make changes.

The same thing can also be achieved by opening any folder e.g. Home and going to the Bookmarks tab and editing from there.
Thanks for that.

I have also looked a bit further and can see no way of removing any partitions on a machine from the Places menu.  I have also found that the mount points made or not for partitions, has nothing to do with it at all, rather as I suspected.

---

### Post by karthick87 on 2010-12-11
Some said mounting in different location other than /media will remove drives from places menu..Is it so???

---

### Post by ajgreeny on 2010-12-11
> **karthick87 said:**
> Some said mounting in different location other than /media will remove drives from places menu..Is it so???
It was me that said it might, but it doesn't remove them, I'm afraid..

Partitions that are not mounted, and have no mount point even available are still showing in my Places menu, so I suspect that without some fundamental rewrite of the code it is impossible to remove any partition on a machine from the Places menu section.

---

### Post by amjjawad on 2010-12-11
So sorry to jump in but ... I'm really curious.
How did you get that listed in Places anyway? I don't have any Partition listed there even if I mount them!

---

### Post by karthick87 on 2010-12-11
> **amjjawad said:**
> I don't have any Partition listed there even if I mount them!

LOL Dont you have partitions listed in your Places Menu??

---

### Post by BugBuster on 2010-12-11
Hi karthick87, I just tried this out and can surely say that if you mount you partitions in /mnt with an entry in fstab like say;
```
/dev/sda1 /mnt/windows   ntfs-3g  defaults 0 0
```
then that partition is not listed in Places menu, but its there until its not mounted. However the partition does not appear on the desktop either.

And by the way..I suggested you try this yesterday on IRC #debian..remember bonjoyee?

---

### Post by karthick87 on 2010-12-11
Tried it,but still it's listed there in Places Menu..

---

### Post by amjjawad on 2010-12-12
> **karthick87 said:**
> LOL Dont you have partitions listed in your Places Menu??

No, I don't.
However, I have "Removal Media" right after Computer (underneath) and when I point my mouse, I got a list of partitions. So not the way you have them.

---

### Post by tajiknomi on 2010-12-12
> **amjjawad said:**
> No, I don't.
However, I have "Removal Media" right after Computer (underneath) and when I point my mouse, I got a list of partitions. So not the way you have them.

[SIZE=2]Its ***Strange*** that the partitions are not listed in your ***places***, can you plz Attach a screen-shot of your Places....?[/SIZE]

---

### Post by amjjawad on 2010-12-12
> **tajiknomi said:**
> [SIZE=2]Its ***Strange*** that the partitions are not listed in your ***places***, can you plz Attach a screen-shot of your Places....?[/SIZE]

Thank you so much, I just learned a new command ;)
I was unable to take a screenshot to any menu. I searched on google and found this:
```
gnome-screenshot --delay <time>
```There you go

I don't want to change the topic. I was just curios and wondering, that's all :)

---

### Post by karthick87 on 2010-12-12
What version of ubuntu you are using???

---

### Post by amjjawad on 2010-12-12
> **karthick87 said:**
> What version of ubuntu you are using???
Just as shown under my avatar, it's 10.04 Desktop Edition 32-bit.

---

### Post by karthick87 on 2010-12-12
I am also using the same.But for me it is displayed..Did you made any changes??

---

### Post by amjjawad on 2010-12-12
> **karthick87 said:**
> I am also using the same.But for me it is displayed..Did you made any changes??

Never.
All changes I do is either to change the background or change the theme. So everything should be on the default settings.

---

### Post by karthick87 on 2010-12-12
How many partitions do you have??

---

### Post by BugBuster on 2010-12-12
How many disks/partitions do you have? Could it be collapsing the list make the menu not grow too much? Because I have seen that happen sometimes!

---

### Post by amjjawad on 2010-12-12
> **karthick87 said:**
> How many partitions do you have??

Around 16 ;)
Check my signature and you'll understand why. I'm talking about PC1.

---

### Post by amjjawad on 2010-12-12
> **BugBuster said:**
> Could it be collapsing the list make the menu not grow too much? Because I have seen that happen sometimes!

Check the screenshot I posted. I don't think so because it's been like that since day1, even before I had 16 partitions.

---

### Post by BugBuster on 2010-12-12
So that could be the reason its collapsing them into a sub-menu. Could try unmounting some partitions for a while and keep only a few mounted? The result will seal the deal!!

---

### Post by QLee on 2010-12-12
[QUOTE=amjjawad]Check the screenshot I posted. I don't think so because it's been like that since day1, even before I had 16 partitions.[/QUOTE]
How many of the 16 are on removeable media and how many of them are mounted in the filesystem tree at boot through an entry in fstab?

---

### Post by amjjawad on 2010-12-12
> **BugBuster said:**
> So that could be the reason its collapsing them into a sub-menu. Could try unmounting some partitions for a while and keep only a few mounted? The result will seal the deal!!

> **amjjawad said:**
> No, I don't.
However, I have "Removal Media" right after Computer (underneath) and  when I point my mouse, I got a list of partitions. So not the way you  have them.

Mounting and unmounting has nothing to do with that as the number of partitions there remain the same.

---

### Post by QLee on 2010-12-12
[QUOTE=amjjawad]Mounting and unmounting has nothing to do with that as the number of partitions there remain the same.[/QUOTE]

True, however, you did not answer my question. Please answer it.

---

### Post by amjjawad on 2010-12-12
> **QLee said:**
> How many of the 16 are on removeable media and how many of them are mounted in the filesystem tree at boot through an entry in fstab?

My bad, I was in hurry and didn't count them, I just looked at the last number, sorry.

I have 11 used partitions (all in Removable Media - I already mentioned that before.) + 2 unformatted + swap = 14.

Only two are mounted in fstab.

Oh, I noticed something. There is duplicate in my "Removable Media" for one of my auto-mounted partition. So, total is 12 in that list "Removable Media".

---

### Post by amjjawad on 2010-12-12
> **QLee said:**
> True, however, you did not answer my question. Please answer it.

Hahaha, easy on me, I was replying the other poster beside my internet is so slow... it takes 10 seconds or more to refresh the page after posting.

---

### Post by QLee on 2010-12-12
Mine is slow too, I'm on dialup.

So, are you telling me that the partitions you have mounted at boot time by having entries in fstab do not show up in the "Places" menu? 

Might that have any significance in regard to the original posters question?

---

### Post by amjjawad on 2010-12-12
> **QLee said:**
> Mine is slow too, I'm on dialup.

So, are you telling me that the partitions you have mounted at boot time by having entries in fstab do not show up in the "Places" menu? 

Might that have any significance in regard to the original posters question?

Forget the duplicate I was mentioning as it happened with me before.

I have ALL my partitions (mounted and unmounted) in the Removable Media. All the formatted partitions of course.

I have another PC with less partitions. Shall I check it and report back? however, that might take some time as I'm trying to fix something in there. Yes, the other PC has also Ubuntu 10.04.

The two partitions I have mounted at boot time are there.

The difference between me and the OP's case is that mine are in a sub-menu while his are not.

---

### Post by QLee on 2010-12-12
All removable media will be in that removable media "sub menu".

Partitions mounted in the filesystem tree at boot time with entries in fstab will show up in computer, filesystem, not in the places menu. Unmounted, internal (non removable) partitions will show up in the places menu.

Apologies to Socrates.

---

### Post by karthick87 on 2010-12-12
So it is not possible to hide or remove partitions from Places menu.Right???

---

### Post by QLee on 2010-12-12
[QUOTE=karthick87]So it is not possible to hide or remove partitions from Places menu.Right???[/QUOTE]

Well, on my system, a partition that I mount at boot time in fstab (in my case sda7, mounted at /mnt/sda7) does not show up in Places, it shows up in Places-->Computer-->Filesystem-->mnt-->sda7. Only the internal hard drive partitions that are not mounted through fstab show up in Places (ready to be mounted by click)

---

### Post by amjjawad on 2010-12-12
> **QLee said:**
> All removable media will be in that removable media "sub menu".

Partitions mounted in the filesystem tree at boot time with entries in fstab will show up in computer, filesystem, not in the places menu. Unmounted, internal (non removable) partitions will show up in the places menu.

Apologies to Socrates.

Just to be extra clear, all the partitions in "Removable Media" sub-menu are for two internal HDDs. I'm not using External HDDs on this PC.

Partitions mounted at boot time with entires in fstab + Partitions are not mounted at boot time with no entires in fstab which will be mounted with one click >>> ALL in that sub-menu (Removable Media).

I don't know why. It's been like that since I installed Ubuntu 10.04.

---

### Post by QLee on 2010-12-12
[QUOTE=amjjawad]...
I don't know why. It's been like that since I installed Ubuntu 10.04.[/QUOTE]

I have no idea how your system got messed up like that, but think about it, only removable media should show up in removable media, eh.

---

### Post by amjjawad on 2010-12-12
> **QLee said:**
> I have no idea how your system got messed up like that, but think about it, only removable media should show up in removable media, eh.

Yeah, I know but again, it's been like that since the first install and I have no problem with it this way ;)

---

### Post by QLee on 2010-12-12
[QUOTE=amjjawad]Yeah, I know but again, it's been like that since the first install and I have no problem with it this way ;)[/QUOTE]
Aha, maybe it's due to a version difference, I'm currently working on a Karmic system.

[Edit] I've just gone and confirmed it on a 10.04LTS system, when I mount in fstab similar to my reply above, it does not appear except in the filesystem.

I hate pictures, as I mentioned, I'm on dialup.

---

### Post by amjjawad on 2010-12-12
> **QLee said:**
> Aha, maybe it's due to a version difference, I'm currently working on a Karmic system.

I'm on PC2 and it's exactly like the OP's case. Please see attached.

You were right, my system (PC1) is messed up. Guess I found yet another issue with it. But, I don't think it's a big deal.

Both PC1 and PC2 has Ubuntu 10.04.

---

### Post by bodhi.zazen on 2010-12-12
See this post:

[http://ubuntuforums.org/showpost.php?p=7240711&postcount=4](http://ubuntuforums.org/showpost.php?p=7240711&postcount=4)

---

### Post by matt_symes on 2010-12-12
Hi

Mcduck's answer in this thread also solved the OP issue.

[http://ubuntuforums.org/showthread.php?t=1439003](http://ubuntuforums.org/showthread.php?t=1439003)

Also there is also a post on udev rules. I think you might be able to garner a solution there.

EDIT: If you use udev rules and are using Lucid or higher  read the very last post to get the correct identifier

Kind regards

---

### Post by QLee on 2010-12-12
Cool, that is another confirmation of what I wrote in post 34.

---

### Post by amjjawad on 2010-12-12
And I guess I should stop digging and being so much curious :D
Nuh, it's good to know more about Ubuntu.

Good thing it's not a big deal and not affecting anything, at least now. I'm talking about my case. But never mind, sorry if I caused confusion.

---

### Post by QLee on 2010-12-12
[QUOTE=amjjawad]And I guess I should stop digging and being so much curious :D
Nuh, it's good to know more about Ubuntu.
...[/QUOTE]
Well, you did sort of hijack the thread but that happens sometimes. It wasn't a mission critical problem, so we could take some time.

It is really difficult to lead you guys, who are frequent posters, to find the solution by the Socratic method when other posters, want to jump in and give "the" answer, and who may or may not read the whole thread. As Socrates believed, it can be more helpful, in the long run, to help someone learn to think and give them more personal satisfaction to discover the answer for themself through questions. I don't usually try that with inexperienced users but you guys answer a lot of posts.

I expect some may disagree with me, but ... there you have it, YMMV.

---

### Post by amjjawad on 2010-12-12
> **QLee said:**
> Well, you did sort of **hijack** the thread but that happens sometimes. It wasn't a mission critical problem, so we could take some time.

It is really difficult to lead you guys, who are frequent posters, to find the solution by the Socratic method when other posters, want to jump in and give "the" answer, and who may or may not read the whole thread. As Socrates believed, it can be more helpful, in the long run, to help someone learn to think and give them more personal satisfaction to discover the answer for themself through questions. I don't usually try that with inexperienced users but these guys answer a lot of posts.

I expect some may disagree with me, but ... there you have it, YMMV.

Apparently, you misunderstood my **posts**.
If you go back to my first post here, you'll find that I mentioned clearly that I was **curious**. If you read my last post or any other post, I did NOT ask for help, I was just **curious**. If I need help, I know how to get it and I don't need to hijack someone's else thread. Your guess is WRONG this time ;)

---

### Post by matt_symes on 2010-12-12
Hi

Karthick87.

I can confirm that...

```

matthew@matthew-laptop:~$ cat /etc/udev/rules.d/hide--partitions.rules 
ACTION!="add|change", GOTO="hide_partition_end"
SUBSYSTEM!="block", GOTO="hide_partition_end"
KERNEL=="loop*|ram*", GOTO="hide_partition_end"

KERNEL=="sda2", ENV{UDISKS_PRESENTATION_HIDE}="1"

LABEL="hide_partition_end"
matthew@matthew-laptop:~$ 
```...hid my windows boot partition from the Places menu, using this udev rule. I believe the solution should also work for you.

EDIT: I am trying to find out if it is possible to use the UUID instead of the device name. If i have any luck i will repost.

Kind regards

---

### Post by karthick87 on 2010-12-12
```
karthick@Ubuntu-desktop:~$ cat /etc/udev/rules.d/hide--partitions.rules 
cat: /etc/udev/rules.d/hide--partitions.rules: No such file or directory
```

---

### Post by matt_symes on 2010-12-12
Hi

@Karthick87

You have to create it as a new file. You can call it what you want.

It was not there on my machine, i had to create it and as you can see i made a typo in the file name (from the original thread). 

hide**--**par....

Change sda2 to what parition you want to hide.

You can have as many...
[FONT=monospace]
[/FONT]KERNEL=="sdXY", ENV{UDISKS_PRESENTATION_HIDE}="1"

entries as you want. One for each partition you want to hide.

You will need to reboot to see the effect.

Kind regards

---

### Post by karthick87 on 2010-12-12
That's not working for me..Still i can see drives in Places menu..Do you want me to delete the fstab rule for that drive which i wanna hide??

---

### Post by matt_symes on 2010-12-12
Hi

Yes, you could try that (just put a # in front of it to comment it out in fstab).

My fstab is quite minimal. 

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=3d48429c-7361-4ab8-8689-54407673b141 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b1c6171a-075e-4291-af69-64baf751d10e none            swap    sw              0       0
```It tend to mount things manually. Also, i am using 10.04.

You could post the output of your rules file. I can confirm this does work on my setup, so.....

BTW: I have a whole host of partitions on my machine for different distro's. My menu was collapsing to the 'Removable drive' sub menu, and that's where the partitions were displayed. However, after hiding some of the partitions i now have them displayed under places and not under the sub menu under places.

Kind regards

---

### Post by karthick87 on 2010-12-12
```
karthick@Ubuntu-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc        proc      nodev,noexec,nosuid    0  0  
#Entry for /dev/sda7 :
UUID=ea6bb1fd-65fd-42f8-aa64-4a591993fe3b  /            ext4,acl  errors=remount-ro      0  1  
#Entry for /dev/sda2 :
UUID=16b8e005-ba37-4212-986f-0ecd20243003  /media/sda2  ext3      defaults               0  0  
#Entry for /dev/sda5 :
UUID=B630D52430D4EC7D                      /media/sda5  ntfs-3g   defaults,locale=en_IN  0  0  
#Entry for /dev/sda6 :
UUID=D6E8DAE8E8DAC5C1                      /media/sda6  ntfs-3g   defaults,locale=en_IN  0  0  
#Entry for /dev/sda8 :
UUID=94f3a305-5cd8-4f4d-ba07-91c2a63d7498  none         swap      sw                     0  0  
```

For example i wanna hide sda5,wat you want me to do??

---

### Post by matt_symes on 2010-12-12
Hi

Post your rules file in /etc/udev/rules.d.

What partitions are you trying to hide?

EDIT: Sorry missed your last post's comment. Hold on.

Kind regards.

---

### Post by matt_symes on 2010-12-12
Hi

Try this. You are using 10.04 or higher aren't you? Karmic and lower require a different idendifier. I.E. not UDISKS_PRESENTATION_HIDE

```

sudo nano /etc/udev/rules.d/hide-partitions.rules
```

Enter password as per usual and copy and paste the code below into that file.

```
ACTION!="add|change", GOTO="hide_partition_end"
SUBSYSTEM!="block", GOTO="hide_partition_end"
KERNEL=="loop*|ram*", GOTO="hide_partition_end"

KERNEL=="sda5", ENV{UDISKS_PRESENTATION_HIDE}="1"

LABEL="hide_partition_end"
```

Save the file and verify by typing
```

cat /etc/udev/rules.d/hide-partitions.rules
```

Check the flie is correct.

Next edit you fstab file

sudo nano /etc/fstab

Put a # in front of the line

```
UUID=B630D52430D4EC7D                      /media/sda5  ntfs-3g   defaults,locale=en_IN  0  0 
```

so it becomes

```
# UUID=B630D52430D4EC7D                      /media/sda5  ntfs-3g   defaults,locale=en_IN  0  0 
```

and save the file.

Again 
```

cat /etc/fstab
```

to check the file.

Assuming all is well, reboot you PC. Then, hopefully, sda5 will not appear. This is what i did and it worked for me.

Kind regards

---

### Post by matt_symes on 2010-12-12
Hi

On my machine...

sudo blkid

```
/dev/sda1: LABEL="System_restore_win7" UUID="DAA41C49A41C2B11" TYPE="ntfs" 
**/dev/sda2: LABEL="Windows_7_boot" UUID="921C18621C18441F" TYPE="ntfs" **
/dev/sda3: LABEL="Windows_7" UUID="A2984D43984D1767" TYPE="ntfs" 
/dev/sda5: LABEL="Ubuntu_10.04" UUID="3d48429c-7361-4ab8-8689-54407673b141" TYPE="ext4" 
/dev/sda6: UUID="b1c6171a-075e-4291-af69-64baf751d10e" TYPE="swap" 
/dev/sda7: LABEL="OpenSuse" UUID="56a4c951-b189-45cb-91e6-76c83b765044" TYPE="ext4" 
/dev/sda8: LABEL="natty" UUID="fb661c9e-e56a-413b-bef4-dc2e0db8c0b1" TYPE="ext4" 
/dev/sda9: LABEL="Fedora-14" UUID="3d35b416-3b1b-467d-892c-ac2095c0ab18" TYPE="ext4" 
/dev/sda10: LABEL="Arch_Linux" UUID="6aa72302-2b4f-432c-953a-33c7513bfa47" TYPE="ext4" 
/dev/sda11: UUID="926199d8-a8a5-4ae0-9014-e7ae790187a9" TYPE="ext4" 
/dev/sda12: UUID="ef9ae3cc-e084-4664-bf0e-ae9bac39dace" TYPE="ext4" 
/dev/sda13: UUID="f8dc5390-f494-4963-95ee-c27ecbf4fea1" TYPE="ext4"
```My rule

cat /etc/udev/rules.d/hide--partitions.rules

```
ACTION!="add|change", GOTO="hide_partition_end"
SUBSYSTEM!="block", GOTO="hide_partition_end"
KERNEL=="loop*|ram*", GOTO="hide_partition_end"

KERNEL=="**sda2**", ENV{UDISKS_PRESENTATION_HIDE}="1"

LABEL="hide_partition_end"
```sda2 is my windows boot partition, as can be seen from blkid and the partition label.

Below is a screen shot of my menu. As you can see, sda2 or window_7_boot it is not under places. If i remove the rule it is displayed under places

Kind regards

---

### Post by karthick87 on 2010-12-12
That worked like a charm :) Thank you matt_symes.

---

### Post by matt_symes on 2010-12-12
Hi

... and here is a screen shot with the rule removed.

matthew@matthew-laptop:~$ ls -a /etc/udev/rules.d/
.  ..  70-persistent-cd.rules  70-persistent-net.rules  README
matthew@matthew-laptop:~$ 

screen shot below. I hope it answers some of the questions about menu behaviour.

Kind regards

---

### Post by Rubi1200 on 2010-12-12
Excellent stuff matt_symes :) 

But an awfully complicated way to go about editing the Places menu!

Shouldn't this be made easier, especially for new users?

---

### Post by matt_symes on 2010-12-12
> Shouldn't this be made easier, especially for new users?

Definitely!!!! Might make a nice project for someone.

---

### Post by shimoda on 2011-02-28
thanks a lot... I also was searching for this... :)

---

