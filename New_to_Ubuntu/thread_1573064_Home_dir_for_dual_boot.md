---
title: "Home dir for dual boot"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by nnjond on 2010-09-12
Home dir for dual boot

Hi,

I'm thinking of installing a dual boot:

sda1			010 Gib		openSuse
sda2			005 Gib		Meercat	
sda3			48x Gib		Partition serving as Home dir for both oses

sda5			004 Gib		swap


I imagine there is the no more intergrated scheme where by i can access my files from either os; Is that correct?

Thanks for your time.

---

### Post by jtarin on 2010-09-12
> I imagine there is the no more intergrated scheme where by i can access my files from either os;Is that correct?

I don't really know.
I'm not familiar enough with your imagination to make a judgement to the correctness of it.

---

### Post by surfer on 2010-09-12
i'd be careful with all your [FONT="Courier New"]/home/user/.*[/FONT] files...

what if you made a very small [FONT="Courier New"]/home[/FONT] partition for all the OSes you are going to use and one common partition (which you'd mount on [FONT="Courier New"]/home/user/common[/FONT] or sth)?

---

### Post by Lateralis on 2010-09-12
My knowledge of this is limited... Maybe one potential problem I can think of though... User IDs in Ubuntu start from 1000, whilst user groups start from 0 (as far as I can tell; happy to be corrected).  I don't know what the corresponding values are in OpenSuSE but I could envisage OpenSuSE thinking that files written from Ubuntu don't belong to "you" and vice versa because the group and User IDs don't match across distros.  

And perhaps that won't even be an issue.  Let me know how you get on. :P

---

### Post by nnjond on 2010-09-12
Thanks for your advice surfer. A common home dir is what i would like and i  thought the solution was to ignore the designated home/user dirs and place all my files on  a 3rd partition called home. You have revealed it is a little more complicated than that.If you think you understand my goal, Please would you say a little more about your solution.

---

### Post by nnjond on 2010-09-12
perhaps i should thank you jtarin for the most memorable post i have read. Princibly because it was intentionally worthless. Let me make my contribution to the community by telling you it doesn't take much imagination to see how this plays out in your other attempts at socilising. are you at your pc now because you are bored and lonely?

---

### Post by jtarin on 2010-09-12
> **nnjond said:**
> perhaps i should thank you jtarin for the most memorable post i have read. Princibly because it was intentionally worthless. Let me make my contribution to the community by telling you it doesn't take much imagination to see how this plays out in your other attempts at socilising. are you at your pc now because you are bored and lonely?I see you have a very thin skin. Well we will certainly keep that in mind for our little friend next time we see him.;)

---

### Post by srs5694 on 2010-09-12
Sharing a /home partition between distributions is perfectly workable; however, sharing *users' home directories* between distributions is more problematic, for two reasons. First, user ID (UID) numbers can vary from one distribution to another, so that a file you create in one distribution may appear to be owned by somebody else (or by an unmapped UID value) in the other. This problem can be overcome by using the usermod command or similar GUI tools to synchronize the UID values across distributions.

Another problem is that the user configuration files for one distribution can require different contents. For instance, they may include references to programs, icons, and so on, and these files may be located in different places in the two distributions. The result is that if you set up the account using Distribution A, when you boot into Distribution B you'll get ugly icons and some menu items may not work. Similar problems can occur in programs other than the file manager, too.

Overall, therefore, it's best to keep user home directories separate. An easy way to do this is to give yourself different usernames in the different distributions. If you like, you can subsequently change a username, without changing its home directory, to give yourself the same username but different home directories in each OS.

If you want to share files across the distributions, you should synchronize your UID numbers, and change UID numbers on all the files in one home directory to match these changes. You can then access files by changing from one home directory to another or by setting up suitable symbolic links between home directories.

---

### Post by oldfred on 2010-09-12
Rather than sharing /home which can be a problem, many of us share a /data partition. You then can mount or mount and link folders into /home.

Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments by Morgan Hall
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions (post #5) of data linking from above blog, based on more from comments 
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by nnjond on 2010-09-13
Thanks for your help. I see a data partition is what i really wanted.

---

