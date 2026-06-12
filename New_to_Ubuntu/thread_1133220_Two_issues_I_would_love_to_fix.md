---
title: "Two issues I would love to fix"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by Periswell on 2009-04-22
Hello everyone

I absolutely love Mythbuntu but I have got some issues with it. 

Firstly, when I am watching TV, I have a blue boarder around the screen. I know how to fix this using a program called Xvattr but the command to fix it has to be applied every time I load my computer. I cannot add it to the rc.local file as the program has not loaded yet so it does not work and I have tried making it into a executable and putting it into ~/.config/autostart/ folder but this does not work either (note I am using the Xfce window manager). How do I make it load after logging in but before Mythtv loads?

Secondly, I have an external hard drive, 500gb Iomega harddrive to be precise, where I keep all of my films and music. Being made for Windows, it was partitioned as a NTSC partition so I formatted it but something went wrong in the process. I am now left with a 499gb EXT3 partition and a 100mb EXT2 partition on this single harddrive. All my files are on the 499gb partition. When they mount, they show up in /media as disk and disk-1, thats alright but half the time the 499gb partition will be disk and half the time it will be disk-1. This completely confuses Mythtv. I don't want to reformat it as I have already used up 300gb and I don't have another hard drive large enough to store the files as it is being formated. What I would like to know is how do I make Mythbuntu not mount the 100mb partition or how do I get them to always show up as the same name in /media every time I boot up?

Much appreciation and thanks in advance.

-Joshua

PS: Sorry for such a long post.

---

### Post by cariboo on 2009-04-22
I'm not sure about the problem with your TV, but you can give the partitions on your external drive volume labels, and then they will mount to the label instead of the generic disk id. For example if you named partition one films, it would mount as /media/films. The easiest way to change the partition volume label is to use gparted. You can install gparted using Add/Remove Programs or Synaptic Package Manager. Then make sure your external drive is unmount, Next open System-->Administration-->Partition Editor, highlight the partition, right click and select label. Add the new label and follow the prompts.

---

### Post by llamabr on 2009-04-22
I'm not that good with external drives, but I would think that with an entry in your /etc/fstab, you can mount it whereever you want.

To the first question, would it mess up anything to run the command over and over?  You could just put it in your .bashrc file, then it'll run every time you log in.

---

### Post by Periswell on 2009-04-23
thanks for the quick responce, i will try them later after school and tell you how they go.

-joshua

---

### Post by Periswell on 2009-04-24
I am sad to report that neither worked the way i would have liked it.

When i add the Xvattr command to the bashrc file, it only loads it when i go into the terminal, before that it does not work. Also i cannot change my partition name in gparted as the whole partition on the external hard drive comes up as 'unallocated' even though i have got files on it. also fstab does not have sdb1 (my external hard drive). Thank you but doesanyone else know what to do?

-joshua

---

