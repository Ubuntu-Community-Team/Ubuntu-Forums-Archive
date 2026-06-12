---
title: "Installing 9.10 version - Partitioning issues"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by guadaatenea on 2010-01-06
Hi everyone,

   I've searched through the forums and official site, and found a great deal of information regarding Ubuntu 8.x, but I still have trouble finding a way through the installation process. The thing is I can't find any instructions regarding how to create a partition to keep dual booting (not interested in Wubi), due to huge differences between the options I'm supposed to find according to tutorials and the ones I actually come across during installation process (never found a "resize" option or bar anywhere, I swear I've searched)

   Thanks to whoever takes the time,

                      G.

---

### Post by bodhi.zazen on 2010-01-06
Personally I resize partitions with gparted, then install, makes it easier.

Also if you look here: 

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

They have pictures for what you want, see the second Step 8 =)

---

### Post by mkoehler on 2010-01-06
Does selecting "Boot up side-by-side" in the installation menu not work for you?

Also, don't forget to defrag your windows installation before installing linux to not lose any data.

---

### Post by guadaatenea on 2010-01-06
I've already made a defrag, and also left nearly 50gb of free space in an 80gb disk. I've made backups for every important file I have.

I get the options

- Erase and use entire disk --->(right now, no way)
- Use the largest continuous free space ---->(doesn't work, of course)
- Specify partitions manually ---->(the one I'm trying to use, and which leads us

=> To a screen with a long green bar (can't move it) with the options "Change" (lonnng list of arcane options for a poor philologist with no particular computing knowledge), "Reverse" and the third one meant "Delete", although it wasn't exactly put that way. There's also a gray "Add" option, and another one that is meant to create a new partition, but which seems to erase everything and begin from zero when I try to use it.

(do I need to say I feel frustrated an a tiny bit stupid?)

---

### Post by guadaatenea on 2010-01-06
I've checked the Graphic Install. It's meant for 8.x.

What's gparted?

---

### Post by -kg- on 2010-01-06
[LIST]
[/LIST]

[GPartEd]("http://gparted.sourceforge.net/") is the partition editor used by Ubuntu (and others) to manage and edit hard drive partitions.  You have GPartEd on your Ubuntu Live CD (System/Administration/Partition Editor) or you can use the GPartEd Live CD which you can download from the webpage I provided the link to above.

As far as partitioning operations, you might like to read at the link in my signature block below.  After that, you can choose the "Manual" method, select the partitions you create, and mark the mount points for each partition you want to use.  That, or you can resize your Windows (?) partition and choose to "- Use the largest continuous free space" which will work since you will have created the free space by resizing your other partition.

---

### Post by Slayer. on 2010-01-06
[http://sourceforge.net/projects/gparted/files/gparted-live-stable/](http://sourceforge.net/projects/gparted/files/gparted-live-stable/)

---

### Post by tom.swartz07 on 2010-01-06
> **guadaatenea said:**
> Hi everyone,

   I've searched through the forums and official site, and found a great deal of information regarding Ubuntu 8.x, but I still have trouble finding a way through the installation process. The thing is I can't find any instructions regarding how to create a partition to keep dual booting (not interested in Wubi), due to huge differences between the options I'm supposed to find according to tutorials and the ones I actually come across during installation process (never found a "resize" option or bar anywhere, I swear I've searched)

   Thanks to whoever takes the time,

                      G.

Okay, I would definitely avoid partitioning before you actually install. Its useful for users that know what to do, and these are only in cases where users want to split their installs into separate partitions.

Perhaps you are using the Alternate Install disc? I remember I accidentally used the alternate disc once and it didnt work too well also.

Try re-downloading the normal Desktop install cd and burn it again. There is an option to install Ubuntu side-by-side for the regular desktop. You could then take it from there.

---

### Post by Bartender on 2010-01-06
How many primary partitions do you have?

The reason why you're seeing different options in tutorials is because they've changed the wording of the auto-partitioning choices in almost every distro.  So a tutorial that was written for anything other than the exact distro you're using may not look familiar.

Did you burn the install CD yourself?  Did you burn it slowly?  Did you use a good quality CD-R, not a -RW?  I'm just wondering if the CD is good.  Did you use the "Check CD for errors" option when it first boots up?

---

### Post by guadaatenea on 2010-01-07
My HD is all in one piece, I'd chosen not to make partitions back when I bought my PC and had Windows XP installed.

As for my CD, I didn't check it for errors, I was planning to do so the next time I boot from it, but there's no good reason to think it might have any defects, I used a good quality cd and my drive has never burned cds with errors yet.

I didn't know there's an alternate one, but as I downloaded from here [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) I don't think there are big chances I may have gotten it wrong, are there?

Anyhow, the plan for the moment is to try to follow the instructions in this [http://bit.ly/7gwBdM](http://bit.ly/7gwBdM) tutorial, which actually describes the screens I have. If that doesn't work, I'll see if Gparted looks too advanced for me (well, Tom's warnings do seem a bit discouraging). If it does look tricky, I'll try to resize the area Windows is using with Partition Magic, with a little help from a friend of mine who should get an award for patience, and then try installing Ubuntu using the "largest free space" option. If I feel like walking in a minefield and I don't dare to do that (my friend can help me on the phone but he lives a good many miles away), well, then I'll see.

---

### Post by dmaxel on 2010-01-07
Since I haven't seen it mentioned anywhere, I thought it might help. For Windows Vista and Windows 7, there is a tool where you can shrink your Windows partition so that you have enough space for Ubuntu as you wish and be certain that you won't lose any of your data.

Computer --> Manage --> Continue for UAC --> Disk Management (on left side).

From there you can shrink your own system partition. If for any reason it doesn't let you shrink as much as you want, yet you know you have enough free space, there may be some "unmovable items" in the way. You'll have to find alternative defragging programs to move them for you.

---

### Post by -kg- on 2010-01-07
[LIST]
[/LIST]

And one more option...you might want to consider getting a second hard drive and installing it.  That way, no partitioning operations on your Windows partition, or drive, for that matter.

Just point the installer to that second HD and let 'er rip. :D

---

### Post by viper3ez on 2010-01-07
i just installed 9.10 a dozen times the last 2 days. i do not know how to use operating system from separate partitions so i installed side by side.

if that disc does not givve you an option to install side by side, that means its not seeing your windows OS  so i'ld stop and use a new disc.

if you are trying to have 2 OS, you want the liveCD to see your windoows disc and if it does, it should give you the side b side option. i'm a novice so without the side by side option, i wont go any further.

---

