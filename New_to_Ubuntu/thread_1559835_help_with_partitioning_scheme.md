---
title: "help with partitioning scheme"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by disastrophe on 2010-08-24
Hi, I am a noob lol. I am planning to change my partitioning scheme to make upgrades and distro changes a lot more painless.
I have a reasonable sized hard drive that I would like to set up for 4 distros, giving each one a 12GB root partition and a 40GB Home partition with a single 2GB swap partition for all. In addition I want to make the balance of my hard drive a large shared data partition to store all my music and videos. I spend way too much time recopying stuff whenever I add or change distros and this would make the process almost trivial.
Anyway, I was starting to slice and dice with the partitioner in the Ubuntu installer but when it came time to assign a mount point to the large data partition at the end of the disk I was at a loss as to how to proceed. So I decided I'd better abort and ask those who have more experience with such things. I hope to get this right the first time. It could potentially save a lot of time and a lot of wear and tear on my hard drive as well as making recovery much easier should something break.
I would sure appreciate some help on this. I do have a Parted Magic Live CD on hand if that would simplify things. Thanks all.

---

### Post by LiquidMeson on 2010-08-24
Should be able to get this all done with the ub-disk just fine.

should look somethin like this.

12g     mount /         ext4 (file system type)
40g     mount /home     ext4   | all your music and data is shared here
2g      mount swap
free space.
Install 1st distro

when you go to install the second distro use the free space to assign 12g to another / and reassign the old 40g partition as /home (Don't format)

Proceed until you have no more free space. Plan accordingly.

noob i think not.

---

### Post by garvinrick4 on 2010-08-24
> **disastrophe said:**
> Hi, I am a noob lol. I am planning to change my partitioning scheme to make upgrades and distro changes a lot more painless.
I have a reasonable sized hard drive that I would like to set up for 4 distros, giving each one a 12GB root partition and a 40GB Home partition with a single 2GB swap partition for all. In addition I want to make the balance of my hard drive a large shared data partition to store all my music and videos. I spend way too much time recopying stuff whenever I add or change distros and this would make the process almost trivial.
Anyway, I was starting to slice and dice with the partitioner in the Ubuntu installer but when it came time to assign a mount point to the large data partition at the end of the disk I was at a loss as to how to proceed. So I decided I'd better abort and ask those who have more experience with such things. I hope to get this right the first time. It could potentially save a lot of time and a lot of wear and tear on my hard drive as well as making recovery much easier should something break.
I would sure appreciate some help on this. I do have a Parted Magic Live CD on hand if that would simplify things. Thanks all. Just make a partition and format it. It does not need a / because it does not have a file system, no O.S.
 It will come up under Places drop down menu.  Give it a label of "data" when you format it. Or music or whatever you want to call it.

---

### Post by Elfy on 2010-08-24
If you want to install 4 seperate distros I would not bother having such large /home for each. Nor would I share /home between distros. In fact I would just go for a 12Gb / and let /home be part of that - if all your 'data' is in seperate partitions then /home is likely to just have each distros config files in.

You can set up symlinks in each home to seperate data partitions.

Choice is of course your's.

---

### Post by indytim on 2010-08-24
As usual in Linux-Land when you ask a generic question, you get 1.5 tons of varied responses.  So here goes with my take ):P

I would recommed:
1.  Using either a LiveCD or a GParted LIveCD, boot and do your patitioning beforehand.
2.  Leave you Windows partition alone unless you need to shrink it down.  If that be the case, do so from within Windows vs GParted.
3.  For your ops (/) 10-12 G should be adequate for most cases.
4.  I recommend a separate /home for each ops you're going to install.  If you not going to store a lot of multi-media etc in there, then 5-10G should be adequate.
5.  You may want to consider breaking up your data into more manageable chunks.  For example, if you have a lot of video, put that in it's own partition.  Same applies for audio as well as your work-in-process epic novel you're writing:p.  Also, if you're going to share your data contents between Lx & Windows, consider formatting your data partitions as ntfs as opposed to ext3-4.
6.  Allow real estate (like a dedicated partition) to store your backups.  My recommendation is partition level image backups.

I'm making these recommendations based on the 6 ops systems (including Windows 7 Pro) and 15 mounted data partitions at bootup on >2TB of storage spanning 3 H/Ds (yikes that sounds like it's a bit over-the-top...:D).

Hope this helps and doesn't just add to the traffic jam of information.

IndyTim / DataMan

---

### Post by julio_cortez on 2010-08-24
Just one question (sorry for kinda hijacking the thread but maybe it comes useful): can a single swap partition be shared between all the distros with no risk (e.g. when hibernating), or would it be better to assign separate swap partitions for each distro?

---

### Post by indytim on 2010-08-24
One swap is all that is required across multiple Lx ops.

-IndyTim / DataMan

---

### Post by julio_cortez on 2010-08-24
Thanks for clearing it out :)

---

### Post by QLee on 2010-08-24
> **indytim said:**
> One swap is all that is required across multiple Lx ops.

-IndyTim / DataMan
Really, DataMan? What happens when one wants to hibernate one system and boot up into another? Of course, you did state "required" and I can't argue with that.

---

### Post by srs5694 on 2010-08-24
First, you didn't mention Windows at all, so I'll assume you're not using it.

Personally, I'd use one /home partition for all the distributions and forego a separate data partition. For best safety, don't try to share users' home directories between distributions -- that is, in distribution A, the main user's home directory might be /home/userA, in distribution B, it would be /home/userB, and so on. You can do this by using different usernames in the different distributions or, with a little juggling, by using the same username but specifying different home directories. You could then store your multimedia files in one user's home directory (/home/userA, say) or in some other directory (/home/multimedia, say). In either case, you can use symbolic links to provide slightly easier access to these files -- /home/userB/music could be a symbolic link to /home/userA/music, for instance.

This approach keeps user files in a standard location: the /home directory. It also minimizes partition clutter and therefore makes it less likely that you'll run out of room on any given partition. Putting /home on a separate partition makes it possible to completely wipe an installation and re-install it fresh without affecting user data -- you've just got to be careful not to put a new filesystem on /home when you re-install!

If the computer does dual-boot to Windows, then storing your multimedia files in a Linux partition may not be the best approach -- although there are Windows drivers for some Linux filesystems, so you could do it this way if you want to install such a driver. Check on drivers for whatever filesystem you want to use first, though. An NTFS partition is probably the best bet if you want to create a separate multi-OS partition for storing multimedia data.

---

### Post by disastrophe on 2010-08-24
Thanks everybody. You're all great, I really appreciate all the advice and goodness knows I need it;) 

I have the following setup now with 3 of the four distros installed, I haven't decided what the fourth is going to be yet.

/dev/sda1   *           1        1459    11717632   83  Linux
/dev/sda2            1460       43778   339920897    5  Extended
/dev/sda5            1460        2675     9764864   83  Linux
/dev/sda6            2675        4134    11717632   83  Linux
/dev/sda7            4134        5350     9764864   83  Linux
/dev/sda8            5350        5593     1951744   82  Linux swap / Solaris
/dev/sda9            5593        7052    11717632   83  Linux
/dev/sda10           7052        8268     9764864   83  Linux
/dev/sda11           8268        9727    11717632   83  Linux
/dev/sda12           9727       10942     9764864   83  Linux
/dev/sda13          10943       21884    87889920   83  Linux
/dev/sda14          21884       32826    87889920   83  Linux
/dev/sda15          32826       43778    87966720   83  Linux

or...
 
sda1 is Ubuntu /  12GB  -ext4
sda5 is Ubuntu /Home  10GB  -ext4
sda6 is Isadora KDE /  12GB  -ext4
sda7 is Isadora KDE /Home  10GB  -ext4
sda8 is swap 2GB
sda9 is pclinuxos gnome /  12GB  -ext2  <  really nice gnome distro, I like it better than Mandriva even
sda10 is pclinuxos gnome /Home  10GB  -ext2
sda11 unused  to be used as / 12GB  <  probably PCLOS KDE
sda12 unused to be used as  /Home 10GB 
sda13 data  -ext3  87GB
sda14 data  -ext3  87GB
sda15 data  -ext3  88GB

I  am writing from sda1 right now, Mint set itself up almost automatically  since it's mainly just Kubuntu repackaging, PCLinuxOS - legacy grub took  about 5-10 min to get it chain loading from grub2. The three distros  installed are fully updated and booting very happily now.

Now, I  intend to share sda13 - 15 with all distros. Which brings me to my next  question - permissions. When I formatted the three I did not take  ownership, that didn't seem like a good idea since I was working from  removable media. I can access them all from Ubuntu and Mint but cannot  write to them unless I open them as admin. I obviously need to work with  ownership and permissions but am unsure exactly what I need to do to  make access to them seamless. I think I still need some help here lol.

PCLinuxOS  will need some fstab editing --no prob, my fingers aren't broken. I'll  cross that bridge later in the appropiate forums. But I'm totally open  to any insights.

> **forestpiskie said:**
> If you want to install 4 seperate distros I  would not bother having such large /home for each. Nor would I share  /home between distros.
Choice is of course your's.

Thanks, I agree. I am going  to keep some goodies unique to each distro in there too so I opted for a  much smaller but more than sufficient /home. I'm kind of OCD about  containers too.=P~

> **indytim said:**
> 
I would recommed:
1.  Using either a LiveCD or a GParted LIveCD, boot and do your patitioning beforehand.
2.  Leave you Windows partition alone unless you need to shrink it down.   If that be the case, do so from within Windows vs GParted.
3.  For your ops (/) 10-12 G should be adequate for most cases.
4.  I recommend a separate /home for each ops you're going to install.   If you not going to store a lot of multi-media etc in there, then 5-10G  should be adequate.
5.  You may want to consider breaking up your data into more manageable  chunks.  For example, if you have a lot of video, put that in it's own  partition.  Same applies for audio as well as your work-in-process epic  novel you're writing:p.   Also, if you're going to share your data contents between Lx &  Windows, consider formatting your data partitions as ntfs as opposed to  ext3-4.
6.  Allow real estate (like a dedicated partition) to store your backups.  My recommendation is partition level image backups.

I'm making these recommendations based on the 6 ops systems (including  Windows 7 Pro) and 15 mounted data partitions at bootup on >2TB of  storage spanning 3 H/Ds (yikes that sounds like it's a bit  over-the-top...:D).

Hope this helps and doesn't just add to the traffic jam of information.

IndyTim / DataMan

Thanks, I used much of your advice. Well, minus the windoze stuff. 20 years of m$ was enough.:-&  I divorced Redmond less than a week after I tried Ubuntu - about 4 months ago. It was like Go Mohave, just go. lol 

> **srs5694 said:**
> First, you didn't mention Windows at all, so I'll assume you're not using it.
That's for sure. I supported the anti malware industry plenty long enough.;)

Anyway,  does anyone know how I can make accessing my data partitions a little  more seamless? I do not need any network shares, remote access or  anything. Only for the four Linux installs. Thanks again for all the help  everybody!

---

### Post by srs5694 on 2010-08-24
> **disastrophe said:**
> Anyway,  does anyone know how I can make accessing my data partitions a little  more seamless? I do not need any network shares, remote access or  anything. Only for the four Linux installs. Thanks again for all the help  everybody!

Add them to /etc/fstab and, as root, set permissions and ownership such that you can access the files using the user ID number(s) associated with all your installations. Type "man chown" and "man chmod" to learn about using the chown and chmod commands, if necessary. You might want to find a tutorial on chmod, such as [this one](http://catcode.com/teachmod/) (I've not read it carefully; it just turned up in a Google search), since chmod syntax can be odd and confusing sometimes.

---

### Post by disastrophe on 2010-08-24
> **srs5694 said:**
> Add them to /etc/fstab and, as root, set permissions and ownership such that you can access the files using the user ID number(s) associated with all your installations. Type "man chown" and "man chmod" to learn about using the chown and chmod commands, if necessary. You might want to find a tutorial on chmod, such as [this one]("http://catcode.com/teachmod/") (I've not read it carefully; it just turned up in a Google search), since chmod syntax can be odd and confusing sometimes.

Thank you.  I found a number of UIDs associated with this installation in /etc/passwd. Are these what I am after and which one(s) - Me, Debian -exim, sys, root, and so forth?  
I can see I need to learn a bit more here to make this happen. Some examples of a similar operation would certainly help. Another common question, for data partitions shared within this computer what would a good set of suggested permissions be so basic security isn't undermined? i.e. 750, etc?

---

### Post by disastrophe on 2010-08-25
Just to get things rolling along I decided to go for the quick and dirty. I use the same username and domain across my installs.  I am owner and I went with chmod -R 777 /media/data1, etc. Setting up my fstab now.
Maybe not the most secure setup but I'm firewalled through my router and iptables and I don't do any p2p, other shares or remotes. It should be okay.
I'll refine it more as I have time to study. Thank you very much again everybody. Marking this as solved.

---

### Post by srs5694 on 2010-08-25
You can use usernames with chown, as in "sudo chown -R fred /home/somedir" to give ownership of everything in /home/somedir to the user whose username is fred. If you need to use a UID number, you can get it from /etc/passwd. You'd need the UID number associated with the username you want to use -- so you might have something like this:

```

jennie:x:1000:1010::/home/jennie:/bin/bash

```

This shows that the UID for the user jennie is 1000, so you'd use 1000 if you need to use a UID number. (You might do this if you're changing ownership in an emergency boot or for a second OS installed on the computer.)

Ideally, you should synchronize the UIDs across systems, so that the same real-world user has the same UID on all the OSes installed on a computer. This will simplify file access across installations. You can use the usermod command to change a UID, as in "sudo usermod -u 1234 fred" to change fred's UID to 1234. This will *not* change ownership of the user's files, though; you'll need to use chown to do that.

---

### Post by disastrophe on 2010-08-26
> **srs5694 said:**
> You can use usernames with chown, as in "sudo chown -R fred /home/somedir" to give ownership of everything in /home/somedir to the user whose username is fred. If you need to use a UID number, you can get it from /etc/passwd. You'd need the UID number associated with the username you want to use -- so you might have something like this:

```

jennie:x:1000:1010::/home/jennie:/bin/bash

```This shows that the UID for the user jennie is 1000, so you'd use 1000 if you need to use a UID number. (You might do this if you're changing ownership in an emergency boot or for a second OS installed on the computer.)

Ideally, you should synchronize the UIDs across systems, so that the same real-world user has the same UID on all the OSes installed on a computer. This will simplify file access across installations. You can use the usermod command to change a UID, as in "sudo usermod -u 1234 fred" to change fred's UID to 1234. This will *not* change ownership of the user's files, though; you'll need to use chown to do that.

Thank you srs5694! I think I actually know what I'm doing now lol. My *buntu and Mint installs use 1000 for my UID and group ID, PCLOS uses 500 (I believe for PCLOS it has to be between 0-999.) So I will be changing my UIDs in my *buntu/Mint installs to 500. 
This and in combination with what I learned last night on psychocats - [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) 
This will be ideal and reasonably secure. The entire process is much, much simpler than I supposed!
(thanks, psychocats!)
Doing it now.
Thanks again for all your help everybody!

Oops, one other little question, are there any other "reserved" UID numbers that are NOT listed in /etc/passwd? winders was full of surprises like that lol.

---

### Post by srs5694 on 2010-08-26
I've never used PCLinuxOS, but it's *very* unlikely that it limits UIDs to 0-999. The Linux kernel and modern Linux support utilities support 32-bit UIDs, so they can range from 0 to 4,294,967,295. Older kernels and tools used 16-bit UIDs, creating a range of 0-65,535. On most distributions, UIDs below 100 are reserved for system tools, and those between 100 and either 499 or 999 are intended for server programs. A UID of value corresponds to root (no matter what name it's given).

Given these restrictions, it's probably safer to change all your UIDs to 1000 than to change them all to 500. That said, I've done the latter on Ubuntu systems in the past with no obvious ill effects.

---

### Post by disastrophe on 2010-08-29
You are correct of course, I read something backwards. It actually said most numbers under 999 were reserved for system, duh. Although for some reason it makes your UID and GID 500. 
And speaking of GIDs lol. That was a little something I had to pick up on the fly. In order to assume ownership of those partitions I had to change my group ID number as well, I basically stumbled through it with little trauma but a couple of interesting surprises.
I ran usermod -u 1000 username after logging in as root. No probs there. Then after running "ls -l" I noticed the listing was showing "username 500" and sure 'nuff, username didn't actually own anything.
Okay, then I ran "groupmod -g 1000 username" as well as "usermod -g 1000 username" and they both returned "unable to determine identity of username" or something like that. 
So what I did to fix it was to manually edit the GIDs in /etc/group and /etc/passwd. After which I ran "chown -R username:username /home/username" and as it turned out I also needed to run "chmod -R 755 /home/username". 
This is what happens when you mix certain distros I guess, but it certainly was a learning experience and I actually kind of enjoyed it once I got past some very minor frustration. It went much smoother than changing things under NT. 
The PCLOS installations are happy and fully functional now and sharing data with the *buntu installations with the same permissions.

---

