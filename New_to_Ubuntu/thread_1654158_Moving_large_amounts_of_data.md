---
title: "Moving large amounts of data"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by Nagle75 on 2010-12-27
I'm running Ubuntu 10.10 Maverick Meerkat (64 bit). I've used linux off & on for a few years, but I would still consider myself a novice. I would like to move a single directory thats about 250 gigs. This directory contains a lot of important, irreplaceable data & I'm looking for a safe way to move it to my new RAID array. I've already moved small files to it, so I know it works. However I've read that nautilus chokes when moving large files. I didn't want to use cp because I wanted to see what was happening, as the files transferred.
On windows I used to use md5sum to verify file integrity of things I downloaded. Can I generate an md5sum of that large directory, before I move it, so I have something to compare it to after the directory is finished being moved? If so, how would I do that? If not, what would be a better way to move that much data? I saw in another thread someone mentioned "Gnome-Commander". This looks good, but I don't fully understand it, or know if it would work for my intended purpose. When giving directions please be very specific. Thanks in advance for your help.:)

---

### Post by mikewhatever on 2010-12-27
You could use 'rsync -a --progress'. It's kind of similar to cp but shows progress.

---

### Post by idi0tf0wl on 2010-12-27
> **mikewhatever said:**
> You could use 'rsync -a --progress'. It's kind of similar to cp but shows progress.

Or you could opt for the -v flag with cp (verbose mode will explain what is being done). Man pages are your best friend.;)

---

### Post by oldfred on 2010-12-28
I have used this rsync command that was part of a backup script.

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)


# backup script
# a - archive, retain file settings
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress
echo "starting..."
rsync -aruvP /mnt/data_DT/Documents /usr/local/fred/data/

---

### Post by Nagle75 on 2010-12-28
Is rsync in the Synaptic package handler? I also like the idea of the -v flag Yes... I remember the man pages, I used Mandriva ages ago, but it's much different then Ubuntu & I have to say I like Ubuntu better so far.:)When I want to get the directions for a package I simply type "man" & then the name of the package & then it gives me a list of directions? Thanks for the help.:)

---

### Post by Sukarn on 2010-12-28
> **Nagle75 said:**
> Is rsync in the Synaptic package handler? I also like the idea of the -v flag Yes... I remember the man pages, I used Mandriva ages ago, but it's much different then Ubuntu & I have to say I like Ubuntu better so far.:)When I want to get the directions for a package I simply type "man" & then the name of the package & then it gives me a list of directions? Thanks for the help.:)

rsync comes installed by default in Ubuntu and most other Linux distributions. You do not need to install it from Synaptic package manager.

Yes, that is how man pages work. They are the same everywhere.

---

### Post by bikodog on 2010-12-28
simple rsync explanation:

[http://www.psychocats.net/ubuntu/backup]("http://www.psychocats.net/ubuntu/backup")

---

### Post by Nagle75 on 2010-12-28
> **bikodog said:**
> simple rsync explanation:

[http://www.psychocats.net/ubuntu/backup]("http://www.psychocats.net/ubuntu/backup")


This is a good straight forward explanation... Thank you! I'll try this when I get home later:)

---

### Post by seawolf167 on 2010-12-28
+1 for rsync

Read through the man pages, it has a ton of options you can use

---

### Post by Nagle75 on 2010-12-28
Thank you everyone for the info & help! I opted to use the rsync w/ the front end & it worked well. After moving over 400 gigs of data in less then 2 hours, I'm convinced that this is the correct tool for such enormously important chores. I liked using the gui (grsync) because it showed me each directory it was copying as it worked. It was really straight forward & simple... even if you aren't savvy, you can figure this program out quickly. I now feel confident about working with large files. Thanks again:D

---

