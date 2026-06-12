---
title: "Install Jaunty next to Hardy with separate /home partition"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-08-22
I have:

[LIST]
[*]sda3 - Hardy, mounted as root
[*]sda5 - ext3 data, mounted as /home
[*]sda7 - unused partition
[*]sda6 - swap
[/LIST]
There is no other partition or unused space on the drive.

I wish to install Jaunty into sda7, and keep sda5 as my /home -- without deleting the data.

When I boot off the Jaunty Live CD, I choose the manual option for the partitions.

I choose:

[LIST]
[*]sda7 - as ext4, format the partition, mount as root.
[*]sda5 - as ext3, don't format the partition, mount as /home.
[*]sda6 - as swap.
[/LIST]
Question:

[LIST]
[*]Bearing mind that I want to keep my data on sda5 (/home), have I chosen the correct options for sda5? Or should I leave sda5 alone, and manually set fstab on Jaunty after the installation?
[/LIST]
(I have made a full backup just in case.)

TIA

---

### Post by earthpigg on 2009-08-22
i'm about 80% sure that will work.

have never done it myself, though.

do not be surprised, however, if 9.04 software makes changes to the config files in your /home/ur-username that 8.04 software cannot understand.

you will be, for example, having 8.04's old version of pidgin trying to read 9.04's newer version of pidgin's configuration files.

work around for that - and im about 65% sure of this - would be to not have any of the same user names on 8.04 as on 9.04.

---

### Post by Paddy Landau on 2009-08-22
Thank you for those warnings.

Well, I have a full backup, so I guess I'll take the plunge!

---

### Post by earthpigg on 2009-08-22
> **Paddy Landau said:**
> I have a full backup

a good backup, and being able to afford downtime, is all you really need to experiment with whatever crazy schemes you wish.

let us know how it turns out -- i'd like to learn from this myself.

---

### Post by ajgreeny on 2009-08-22
The biggest potential problem you will face is the shared (I assume) /home partition that both hardy and jaunty will be using, as different versions of software can cause configuration incompatibilities between the two.

The sensible way would be to not have a separate /home partition shared between each OS, but to keep the /home in root and then make sure all your data files are in the shared partition.  That way all configuration files and folders will be separate for each OS and there will be no configuration conflicts, but the data files, which take most disk space, will be shared and should work with no problem.

The difficulty will be working out how you can carry on using hardy, which at the moment does have a separate /home partition, but which I am suggesting should now have home and all its config files and folders in /home in root.  I imagine it is possible to do this somehow, but it is beyond me, I'm afraid, and if it were me, I would just start again, and install hardy first with no separate home, make the shared partition for data, then install jaunty in exactly the same way.

---

### Post by earthpigg on 2009-08-22
ajgreeny: you may/may not know more about this than me. does what i suggested above make sense?

make his 8.04 username is eightohfour.
make his 9.04 username is nineohfour.

config files for 8.04 will be in /home/eightohfour.
config files for 9.04 will be in /home/nineohfour.

while logged in as nineohfour in 9.04, config changes and whatnot will be saved to a different home folder - one that will never be looked at while logged in as eightohfour in 8.04.

this should/maybe/will allow him to have 8.04 and 9.04 share a /home partition *_but not specific user /home folders_* without issue. and he will be able to copy specific config folders/files from /home/eightohfour to /home/nineohfour if he wishes, but not the other way.

example: delete /home/nineohfour/.purple. copy /home/eightohfour/.purple to /home/nineohfour and BAM, pidgin account stuff in 9.04 will be the same as it was 8.04. same with firefox, his .torrent client of choice, etc.

but he will not be able to move config stuff from 9.04 to 8.04 without probably creating problems.

any flaws in my logic that you see?

i've been known to look at things to simplistically and miss things before...

---

### Post by fela on 2009-08-22
Just go for it. If you have a backup of your data, and doing this cannot possibly cause a hardware failure, what have you got to lose? Only don't do it if you can't afford any downtime at all!

BTW, good job on the data backup. To everyone else: your data should be backed up whatever the circumstances. You might think your harddrive will last forever, well trust me I thought that and guess what I got for it? A catastrophic head crash. Lucky I had my music and photos backed up on my NAS, huh?

---

### Post by JC Cheloven on 2009-08-22
> **earthpigg said:**
> ajgreeny: you may/may not know more about this than me. does what i suggested above make sense?

make his 8.04 username is eightohfour.
make his 9.04 username is nineohfour.

config files for 8.04 will be in /home/eightohfour.
config files for 9.04 will be in /home/nineohfour.

while logged in as nineohfour in 9.04, config changes and whatnot will be saved to a different home folder - one that will never be looked at while logged in as eightohfour in 8.04.

this should/maybe/will allow him to have 8.04 and 9.04 share a /home partition *_but not specific user /home folders_* without issue. and he will be able to copy specific config folders/files from /home/eightohfour to /home/nineohfour if he wishes, but not the other way.

example: delete /home/nineohfour/.purple. copy /home/eightohfour/.purple to /home/nineohfour and BAM, pidgin account stuff in 9.04 will be the same as it was 8.04. same with firefox, his .torrent client of choice, etc.

but he will not be able to move config stuff from 9.04 to 8.04 without probably creating problems.

any flaws in my logic that you see?

i've been known to look at things to simplistically and miss things before...

... If I understand you -may I don't-, this is quite a weird thing, and unnecessary anyway. Having two different users from two different OSs accesing the same files on a separate partiton is comon practice, and there is not need -nor advantage- in calling that a home partition. Also I'm unsure wheter it can lead to permission problems with the files or not (who's the owner, which has owner rights over a given file?), or a mess with users (both would lie in that /home, they could login from both OSs...right?). 

Just in case: The intended usefulness of a separate /home partition is when reinstalling your OS. Your files will remain, and the old configuration files (dot-whatever) will be overwritten as needed when installing or updating the apps in the new system.
Even so, I don't see the point in a separate /home partition. But being the default setup in Arch linux, there should be a point :). I find cleaner the separate data partition scheme suggested by ajgreeny.

---

### Post by ajgreeny on 2009-08-22
Your suggestion of different usernames  for each OS is certainly possible, and with a separate partition for data will still allow the sharing of all data files by both OSs, so, it's really up to the OP to decide which he uses.  I still prefer the home for each OS in its own root partition and a simple shared partition for all the data; seems simpler to me, and without the added chance of using an incorrect username.

As a side issue to this you could also keep all the data in one of the /home partition, separate or within root, and then just link to that from the other OS for all your data folders.  You can then keep the same usernames for simplicity, and save on data space. I don't know why I didn't suggest this before as it's what I do with my 3 linux OSs on one machine.  Stupid me!

---

### Post by Paddy Landau on 2009-08-23
Thank you all for your excellent advice.

In the end, I decided to copy my entire /home partition to my Hardy partition. Thus, I now have Hardy and Jaunty that do not look at each other at all.

My intention is to install Jaunty and get rid of Hardy, but as I can't afford to lose too much to downtime, I wanted to keep Hardy "just in case" until Jaunty has proven itself on my machine.

Incidentally, regarding my first question, Jaunty did not overwrite my /home partition but intelligently kept it. Yay!

---

### Post by HiImTye on 2009-08-23
you could resize your /home partition and make it two partitions. less headache, your /home data will still be seperate and you can opt out of mounting the 'other' /home partition

---

### Post by Paddy Landau on 2009-08-23
> **earthpigg said:**
> let us know how it turns out -- i'd like to learn from this myself.
I'm finding it a bit tedious.

When I first booted with Jaunty, it certainly attempted to keep all my settings, and did quite a good job.

But I found too many bits-and-pieces missing (specifically programs that I hadn't installed) or inconsistent (menu entries that were valid under Hardy but not under Jaunty), so I decided to reinstall it with a fresh (empty) /home partition. I'll copy across all my data after getting my Jaunty programs and settings set up.

I'm in the process of setting all my settings again, but I'm having a little difficulty. For example:

[LIST]
[*]I see that Compiz is installed; but where do I find it in the menu?
[*]My extra keyboard keys (to load Firefox or the calculator, for example) worked automatically first time with Hardy, but not at all with Jaunty.
[/LIST]
 I'm half-decided to give up on Jaunty and wait until Karmic, which is LTS. Having said that, there's not much more for me to do to finish with all my settings and program installations. And I can work on Hardy in the meantime.

---

### Post by theozzlives on 2009-08-23
I'm unclear why someone would do this?

---

### Post by Paddy Landau on 2009-08-23
> **theozzlives said:**
> I'm unclear why someone would do this?
My intention was to upgrade my Hardy to Jaunty, but I needed Hardy available in case the Jaunty upgrade gave problems (which it has).

I already had a separate /home partition.

---

### Post by theozzlives on 2009-08-23
> **Paddy Landau said:**
> My intention was to upgrade my Hardy to Jaunty, but I needed Hardy available in case the Jaunty upgrade gave problems (which it has).

I already had a separate /home partition.

If you already backed up your Hardy and Jaunty throws up on itself, you still got your backups to fall back on.

---

### Post by Paddy Landau on 2009-08-23
> **theozzlives said:**
> If you already backed up your Hardy and Jaunty throwes up on itself, you still got your backups to fall back on.
Yup, and how inconvenient would that be to restore, do more work, try again, perhaps restore again...

This way, I can jump between them with ease and speed.

---

### Post by theozzlives on 2009-08-23
> **Paddy Landau said:**
> Yup, and how inconvenient would that be to restore, do more work, try again, perhaps restore again...

This way, I can jump between them with ease and speed.

Guess I just have to much time on my hands, with a home based business. The only computer I can't afford downtime on is my web server.

---

