---
title: "Problems with /home and ubuntu starting"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by oGuDrEv on 2010-05-02
Hello everybody,

I am completely new in Ubuntu, so I apologize for my mistakes. 

First time I had installed Ubuntu following and Internet guide. They showed how to make the partitions and I did as they showed. So, I did three partitions of my hard drive: one for file system (an ext4 partition), other for swap and other for my personal files that used to be in folder /home (this one is an ext4 partition too).

Last Friday I was updating my Ubuntu to the new version 10.04. I left the computer updating with a small command line instruction in order to after three hours the computer turn off alone.

On Saturday I tried to turn on the PC but it does not start. My action was to reinstall Ubuntu and I did it on Sunday. I must say it worked perfectly and now i am a new user of Ubuntu last version. But here the problem comes: When I tried to restore /home folder (in accordance with some tutorials I found on Internet) I could mount the partition where was originally /home but after i restart my PC it does not work anymore. Ubuntu says something like it is not able to found /home directory and it is completely true because of i delete it. Now I need to make Ubuntu loads automatically my partition sda6 in folder /home. Could you give some advices for that, please? I really appreciate your help

Thanks,

**[oGuDrEv]("http://ubuntuforums.org/member.php?u=1065498").**

---

### Post by 4Orbs on 2010-05-02
Just to be sure I understand the situation:
1. You have Ubuntu installed on only one partition plus a swap partition?
2. You deleted the /home folder as an administrator?
3. You want to have partition sda6 mounted as your /home folder?
4. You had previously installed Ubuntu and used sda6 as the /home mounting point, but it didn't work? So you reinstalled Ubuntu to only one partition?

If this is correct, then I suggest not using sda6 as the /home mount point, but rather as an additional /mnt/storage partition. Then you could copy your important files from the /mnt/storage partition over to your new /home folder. Would this be a satisfactory solution for you?

EDIT: I am assuming that sda6 already has some important files on it. If it is empty then that's ok also.

---

### Post by srs5694 on 2010-05-02
I disagree with 4Orbs. Using a separate /home partition is a far more standard practice in Linux than is keeping /home on the root (/) partition and symlinking to some other random location. A symlink configuration just adds complexity with absolutely no benefit in terms of functionality or reliability.

Here's how you can fix your problem:


[list=1]
[*]Boot to some sort of Linux system (Ubuntu install CD/DVD, emergency disc, your current installation if you can get in as root, or whatever).
[*]If necessary, mount the root (/) of your installed system someplace convenient. I'll assume it's at /, but this assumption won't be valid for certain types of emergency discs; in that case, you should add your true mount point to the below references (for instance, if you've mounted it at /mnt and I write about /home, you'd use /mnt/home instead).
[*]If the /home directory doesn't exist, create it. (Type "sudo mkdir /home" at a shell prompt.)
[*]Edit /etc/fstab and add the below entry to it, or a variant as described below.
[*]Type "sudo mount /dev/sda6 /home".
[*]Check /home for your home directory (for instance, /home/oGuDrEv, if oGuDrEv is your username). If it's not present, create it and then type "chown -R 1000 /home/oGuDrEv". This assumes that the user ID (UID) for your main user is 1000, as is the default for the first user on an Ubuntu system. If you're using a full install, you can substitute your username for 1000.
[*]Reboot. Everything should work.
[/list]


The /etc/fstab entry can look like this:

```

/dev/sda6     /home    ext4           noatime        0 2

```

Instead of /dev/sda6, you can refer to the partition by its UUID number, as in:

```

UUID=580d3322-2ff8-4692-a964-be996c2e9929     /home    ext4           noatime        0 2

```

You can obtain the UUID number by typing "sudo blkid /dev/sda6". The advantage of using the UUID number is that it will be resistant to changes should you add or delete partitions. Some Ubuntu utilities may also rely on it (but I'm not sure of that). The device filename (/dev/sda6) is more direct and easier for a human to parse, though, and it's more resistant to some problems that can damage or alter the UUID value. Take your pick about which to use.

---

### Post by 4Orbs on 2010-05-03
I was suggesting mounting sda6 as a storage partition rather than /home because he had already tried it as /home and it didn't work. That leads me to believe there are existing configuration files present that are not compatible with Ubuntu 10.04, so the separate storage partition would allow him to recover his important files and copy them to his new /home partition. No symlinking at all.

---

### Post by srs5694 on 2010-05-03
His previous installation was an Ubuntu installation, and it's obvious from his description that something about his upgrade attempt fubared his OS upgrade. Chances are this left his /home partition unaffected, so there's no need to recover anything. I could be wrong, of course, but if that were the case, an easy solution would be to move the original user home directory on /dev/sda6 to another name and create an empty home directory in its place. That's one of the advantages of a separate /home partition, in fact -- a messed-up system update is very unlikely to damage user files in /home, thus simplifying the recovery process. The problem in this case is that oGuDrEv apparently didn't specify that /dev/sda6 was /home when doing the re-installation. If s/he had done that, the system would be working now.

(FWIW, I fault Ubuntu's design for this. IMHO, a separate /home partition should be standard. It's easy enough to give partitions labels, such as "home" or "Ubuntu-home," and then have an installer search for these labels and suggest using the correct partition when doing a re-install. For whatever reason, Ubuntu's designers have chosen not to use a separate /home partition by default, which causes endless problems.)

---

### Post by 4Orbs on 2010-05-03
> but if that were the case, an easy solution would be to move the original user home directory on /dev/sda6 to another name and create an empty home directory in its place

And that's where I was going with my suggestion.

---

### Post by srs5694 on 2010-05-03
> **4Orbs said:**
> > but if that were the case, an easy solution would be to move the original user home directory on /dev/sda6 to another name and create an empty home directory in its placeAnd that's where I was going with my suggestion.

One of us is misunderstanding the other. You originally wrote:

> I suggest not using sda6 as the /home mount point, but rather as an  additional /mnt/storage partition. Then you could copy your important  files from the /mnt/storage partition over to your new /home folder.I read this as meaning mounting /dev/sda6 at /mnt/storage, using cp or some other tool to copy files from /mnt/storage to /home (on the root filesystem), and then abandoning or repurposing /dev/sda6. This would do away with all the advantages of putting /home on a separate filesystem.

My own suggestion is to keep using /dev/sda6 as a separate /home partition. It probably won't need any work, and certainly not *copying* many files, to get it working again. (In the above, I wrote "move the original user home directory," but in this context, "move" is synonymous with "rename" -- in fact, on the command line the same command, mv, is used for both operations because they're identical.)

One key point for understanding: There's a difference between the /home directory and individual users' home directories. The /home directory is precisely that: a directory called "/home". This directory normally holds one or more subdirectories, such as /home/fred or /home/sally. These subdirectories are individual users' home directories. Some people on this forum either don't understand this distinction or are imprecise in how they describe each case, which can lead to problems.

To sum up my position: Remounting /dev/sda6 as /home is fairly simple and will preserve the benefits of using a separate /home partition. Mounting /home elsewhere and copying files adds complexity and is almost certain to reduce flexibility in the long run. (An exception might be if a bigger hard disk were being added as a way to expand space in /home, but oGuDrEv didn't mention such a need.)

---

### Post by 4Orbs on 2010-05-03
You are correct. I withdraw my suggestions.

---

