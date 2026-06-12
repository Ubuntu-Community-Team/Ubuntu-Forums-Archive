---
title: "Can you create a debootStrapChroot version of ubuntu 32bit 10.10"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by TheManno1 on 2011-02-02
I have a ubuntu 64 10.10 and want to use a DebootStrap version of ubuntu 10.10 32bit or the latest 32 bit version to run certain applications that are not compatible with ubuntu 64 bit.

I need a noob friendly version of [https://help.ubuntu.com/community/DebootstrapChroot](https://help.ubuntu.com/community/DebootstrapChroot) with pictures.

Especially Step 2 
**Step 2: Create a configuration file for schroot. I need pictures for that one can't understand how you save a file in a terminal **
 sudo editor /etc/schroot/chroot.d/hardy_i386.conf

How do save in the terminal word editor need pictures and noob friendly instructions.

---

### Post by TheManno1 on 2011-02-02
[LIST=1]
[*]Also How do I create a chroot version of any version of ubuntu in case there comes a new version of 32 bit ubuntu comes then how do I do it .
[/LIST]

[LIST=1]
[*]Infact what is the method that makes it possible to make a chroot of any debian.
[/LIST]

Please include pictures and be noob friendly.

---

### Post by TheManno1 on 2011-02-02
Please Help.

---

### Post by TheManno1 on 2011-02-03
Some help please

---

### Post by wojox on 2011-02-03
If you want to run 32 bit applications under 64 bit Ubuntu install the libs:

```
sudo apt-get install ia32-libs
```

---

### Post by TheManno1 on 2011-02-05
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot) can some one show me these steps with pictures especially the file part 


[LIST=1]
[*]Add the following lines into schroot.conf and then save and close the file. Replace *your_username* with your username. 

[LIST]
[*][lucid]
description=Ubuntu Lucid
location=/var/chroot
priority=3
users=your_username
groups=sbuild
root-groups=root
[/LIST]
[*]Open a terminal and type: 
[LIST]
[*]sudo debootstrap --variant=buildd --arch i386 lucid /var/chroot/ [http://mirror.url.com/ubuntu/](http://mirror.url.com/ubuntu/)
[/LIST]
This will create a basic 'installation' of Ubuntu 10.04 (Lucid Lynx) in the chroot. It may take a while for the packages to be downloaded. 
[/LIST]
I want to create a chroot of ubuntu 10.10 32 bit Am I suppose todelete everything in the file and add this line please include pictures with the file process.

---

### Post by TheManno1 on 2011-02-05
**Re: Can you create a debootStrapChroot version of ubuntu 32bit 10.10** 			
 			 			 		   		 		 		[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot) can some one show me these steps with pictures especially the file part 


[LIST=1]
[*]Add the following lines into schroot.conf and then save and close the file. Replace *your_username* with your username.
[LIST]
[*][lucid]
description=Ubuntu Lucid
location=/var/chroot
priority=3
users=your_username
groups=sbuild
root-groups=root
[/LIST]
[*]Open a terminal and type:
[LIST]
[*]sudo debootstrap --variant=buildd --arch i386 lucid /var/chroot/ [http://mirror.url.com/ubuntu/](http://mirror.url.com/ubuntu/)
[/LIST]
This will create a basic 'installation' of Ubuntu 10.04 (Lucid Lynx) in the chroot. It may take a while for the packages to be downloaded. 
[/LIST]
I want to create a chroot of ubuntu 10.10 32 bit Am I suppose todelete everything in the file and add this line please include pictures with the file process.

---

### Post by TheManno1 on 2011-02-05
**Re: Can you create a debootStrapChroot version of ubuntu 32bit 10.10** 			
 			 			 		   		 		 		[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot) can some one show me these steps with pictures especially the file part 


[LIST=1]
[*]Add the following lines into schroot.conf and then save and close the file. Replace *your_username* with your username.
[LIST]
[*][lucid]
description=Ubuntu Lucid
location=/var/chroot
priority=3
users=your_username
groups=sbuild
root-groups=root
[/LIST]
[*]Open a terminal and type:
[LIST]
[*]sudo debootstrap --variant=buildd --arch i386 lucid /var/chroot/ [http://mirror.url.com/ubuntu/](http://mirror.url.com/ubuntu/)
[/LIST]
This will create a basic 'installation' of Ubuntu 10.04 (Lucid Lynx) in the chroot. It may take a while for the packages to be downloaded. 
[/LIST]
I want to create a chroot of ubuntu 10.10 32 bit Am I suppose todelete everything in the file and add this line please include pictures with the file process.

---

### Post by TheManno1 on 2011-02-18
Need this to run pcsx**2 the playstation 2 emulatorRe: Can you create a debootStrapChroot version of ubuntu 32bit 10.10** 			
 			 			 		   		 		 		[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot) can some one show me these steps with pictures especially the file part 


[LIST=1]
[*]Add the following lines into schroot.conf and then save and close the file. Replace *your_username* with your username.
[LIST]
[*][lucid]
description=Ubuntu Lucid
location=/var/chroot
priority=3
users=your_username
groups=sbuild
root-groups=root
[/LIST]
[*]Open a terminal and type:
[LIST]
[*]sudo debootstrap --variant=buildd --arch i386 lucid /var/chroot/ [http://mirror.url.com/ubuntu/](http://mirror.url.com/ubuntu/)
[/LIST]
This will create a basic 'installation' of Ubuntu 10.04 (Lucid Lynx) in the chroot. It may take a while for the packages to be downloaded. 
[/LIST]
I want to create a chroot of ubuntu 10.10 32 bit Am I suppose to delete everything in the file and add this line please include pictures with the file process.2 the playstation 2 emulator in ubuntu 64 bit.

Also how do i create a chroot of any ubuntu especially if there is a new one.

---

### Post by TheManno1 on 2011-02-21
Need this to run pcsx**2 the playstation 2 emulatorRe: Can you create a debootStrapChroot version of ubuntu 32bit 10.10** 			
 			 			 		   		 		 		[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot) can some one show me these steps with pictures especially the file part 


[LIST=1]
[*]Add the following lines into schroot.conf and then save and close the file. Replace *your_username* with your username.
[LIST]
[*][lucid]
description=Ubuntu Lucid
location=/var/chroot
priority=3
users=your_username
groups=sbuild
root-groups=root
[/LIST]
[*]Open a terminal and type:
[LIST]
[*]sudo debootstrap --variant=buildd --arch i386 lucid /var/chroot/ [http://mirror.url.com/ubuntu/](http://mirror.url.com/ubuntu/)
[/LIST]
This will create a basic 'installation' of Ubuntu 10.04 (Lucid Lynx) in the chroot. It may take a while for the packages to be downloaded. 
[/LIST]
I want to create a chroot of ubuntu 10.10 32 bit Am I suppose to delete everything in the file and add this line please include pictures with the file process.2 the playstation 2 emulator in ubuntu 64 bit.

Also how do i create a chroot of any ubuntu especially if there is a new one.
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=10471466") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=10471466")

---

### Post by TheManno1 on 2011-03-16
Need this to run pcsx2 the playstation 2 emulatorRe: Can you create a debootStrapChroot version of ubuntu 32bit 10.10 [https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot) can some one show me these steps with pictures especially the file part     1. Add the following lines into schroot.conf and then save and close the file. Replace your_username with your username.           * [lucid]             description=Ubuntu Lucid             location=/var/chroot             priority=3             users=your_username             groups=sbuild             root-groups=root    2. Open a terminal and type:           * sudo debootstrap --variant=buildd --arch i386 lucid /var/chroot/ [http://mirror.url.com/ubuntu/](http://mirror.url.com/ubuntu/)       This will create a basic 'installation' of Ubuntu 10.04 (Lucid Lynx) in the chroot. It may take a while for the packages to be downloaded.  I want to create a chroot of ubuntu 10.10 32 bit Am I suppose to delete everything in the file and add this line please include pictures with the file process.2 the playstation 2 emulator in ubuntu 64 bit.

---

### Post by TheManno1 on 2011-03-16
It has been 3 weeks somebody answer all ready

---

### Post by TheManno1 on 2011-03-18
Help please

---

### Post by wep940 on 2011-03-19
> **TheManno1 said:**
> It has been 3 weeks somebody answer all ready
 
(a) this won't get you any help
 
(b) chances are by now that anyone who could help either has not seen the post or nobody is able to help you. 
 
(c) If you're running 64-bit Ubuntu and require 32-bit Ubuntu, why don't you try installing the libs, etc., as already mentioned or just install 32-bit Ubuntu instead on your PC?
 
(d) if you still insist on using dechroot, and your question is about using a command line editor, and you have 64-bit Ubuntu installed, why don't use just open a terminal window and gksudo gedit the file in question?

---

### Post by TheManno1 on 2011-03-19
# schroot chroot definitions. # See schroot.conf(5) for complete documentation of the file format. # # Please take note that you should not add untrusted users to # root-groups, because they will essentially have full root access # to your system.  They will only have root access inside the chroot, # but that's enough to cause malicious damage. # # The following lines are examples only.  Uncomment and alter them to # customise schroot for your needs, or create a new entry from scratch. # # #[sid] #description=Debian sid (unstable) #directory=/srv/chroot/sid #priority=3 #users=rleigh #groups=sbuild #root-groups=root #aliases=unstable,default # #[sid-snap] #type=lvm-snapshot #description=Debian sid LVM snapshot #priority=3 #groups=sbuild,root #root-users=rleigh #root-groups=root,sbuild #source-root-users=rleigh #device=/dev/hda_vg/sid_chroot #mount-options=-o atime,sync,user_xattr #lvm-snapshot-options=--size 2G # #[sid-bsnap] #type=btrfs-snapshot #description=Debian sid btrfs snapshot #btrfs-source-subvolume=/srv/chroot/btrsnap/sid-snap #btrfs-snapshot-directory=/srv/chroot/btrsnap/snapshots #priority=3 #groups=root,sbuild #root-groups=root,sbuild # #[squeeze] #description=Debian squeeze (stable) 32-bit #directory=/srv/chroot/squeeze #priority=3 #groups=sbuild-security #aliases=stable #personality=linux32 # #[lenny] #description=Debian lenny (oldstable) #directory=/srv/chroot/lenny #priority=2 #groups=sbuild #aliases=oldstable # #[lenny-file] #description=Debian lenny (oldstable) #file=/srv/chroot/lenny.tar.gz #location=/lenny #priority=2 #groups=sbuild # #[lenny-secure] #description=Debian lenny (oldstable) #directory=/srv/chroot/lenny #priority=2 #groups=sbuild-security #aliases=stable-security # #[experimental] #type=block-device #description=Debian experimental #priority=4 #groups=sbuild,root #root-groups=root,sbuild #device=/dev/hda_vg/experimental_chroot #mount-options=-o atime,sync,user_xattr #location=/experimental #[lucid] #description=Ubuntu 10.10 #location=/var/chroot #priority=3 #users=family #groups=sbuild #root-groups=root # #[Maverick] #description=Ubuntu Maverick #location=/var/chroot #priority=3 #users=your_username #groups=sbuild #root-groups=root

---

### Post by TheManno1 on 2011-03-19
This is the file in ge edit with this file where do I add this  Add the following lines into schroot.conf and then save and close the file. Replace your_username with your username.      *        [lucid]       description=Ubuntu Lucid       location=/var/chroot       priority=3       users=your_username       groups=sbuild       root-groups=root      Need Maverick 32-bit chroot.

---

### Post by wep940 on 2011-03-20
> **TheManno1 said:**
> This is the file in ge edit with this file where do I add this Add the following lines into schroot.conf and then save and close the file. Replace your_username with your username. * [lucid] description=Ubuntu Lucid location=/var/chroot priority=3 users=your_username groups=sbuild root-groups=root Need Maverick 32-bit chroot.
 
Did you actually put your Ubuntu userid in the statement, or did you leave it as your_username?  It wants you to replace "your_username" with your actual Ubuntu userid.

---

### Post by TheManno1 on 2011-03-20
This is mine  # schroot chroot definitions. # See schroot.conf(5) for complete documentation of the file format. # # Please take note that you should not add untrusted users to # root-groups, because they will essentially have full root access # to your system. They will only have root access inside the chroot, # but that's enough to cause malicious damage. # # The following lines are examples only. Uncomment and alter them to # customise schroot for your needs, or create a new entry from scratch. # # #[sid] #description=Debian sid (unstable) #directory=/srv/chroot/sid #priority=3 #users=rleigh #groups=sbuild #root-groups=root #aliases=unstable,default # #[sid-snap] #type=lvm-snapshot #description=Debian sid LVM snapshot #priority=3 #groups=sbuild,root #root-users=rleigh #root-groups=root,sbuild #source-root-users=rleigh #device=/dev/hda_vg/sid_chroot #mount-options=-o atime,sync,user_xattr #lvm-snapshot-options=--size 2G # #[sid-bsnap] #type=btrfs-snapshot #description=Debian sid btrfs snapshot #btrfs-source-subvolume=/srv/chroot/btrsnap/sid-snap #btrfs-snapshot-directory=/srv/chroot/btrsnap/snapshots #priority=3 #groups=root,sbuild #root-groups=root,sbuild # #[squeeze] #description=Debian squeeze (stable) 32-bit #directory=/srv/chroot/squeeze #priority=3 #groups=sbuild-security #aliases=stable #personality=linux32 # #[lenny] #description=Debian lenny (oldstable) #directory=/srv/chroot/lenny #priority=2 #groups=sbuild #aliases=oldstable # #[lenny-file] #description=Debian lenny (oldstable) #file=/srv/chroot/lenny.tar.gz #location=/lenny #priority=2 #groups=sbuild # #[lenny-secure] #description=Debian lenny (oldstable) #directory=/srv/chroot/lenny #priority=2 #groups=sbuild-security #aliases=stable-security # #[experimental] #type=block-device #description=Debian experimental #priority=4 #groups=sbuild,root #root-groups=root,sbuild #device=/dev/hda_vg/experimental_chroot #mount-options=-o atime,sync,user_xattr #location=/experimental #[lucid] #description=Ubuntu 10.10 #location=/var/chroot #priority=3 #users=family #groups=sbuild #root-groups=root # #[Maverick] #description=Ubuntu Maverick #location=/var/chroot #priority=3 #users=your_username #groups=sbuild #root-groups=root

---

### Post by TheManno1 on 2011-03-20
Where am I suppose to put this in the document above you and do I have a # for it.  Add the following lines into schroot.conf and then save and close the file. Replace your_username with your username. * [lucid] description=Ubuntu Lucid location=/var/chroot priority=3 users=your_username groups=sbuild root-groups=root Need Maverick 32-bit chroot.

---

### Post by wep940 on 2011-03-21
Notice one of the lines towards the end of what you say is yours:
 
Maverick #location=/var/chroot #priority=3 #users=your_username #groups=sbuild #root-groups=root 
 
Put your actual Ubuntu userid in place of the "your_username" above.  So if your userid is joebob, the line would look like:
 
Maverick #location=/var/chroot #priority=3 #users=joebob #groups=sbuild #root-groups=root

---

### Post by Chronon on 2011-03-22
I followed the instructions here:
[https://help.ubuntu.com/community/DebootstrapChroot](https://help.ubuntu.com/community/DebootstrapChroot)

My schroot.conf is quite simple:
```
[jaunty_i386]
description=Ubuntu 9.04 Jaunty for i386
directory=/srv/chroot/jaunty_i386
personality=linux32
root-users=myusername
type=directory
users=myusername,otherusernames

```

---

### Post by wep940 on 2011-03-22
Do you have your actual userid in that file or does it really say "myusername" and "myusername,otherusernames"?   Please, be SURE you substitute your actual userid where ever it says "myusername", and don't leave ",otherusernames" in there either.  If you have other users on your PC who will be using this app, add their actual userid's.
 
So, 2 examples:
 
(1) Let's say your userid is "jimbob" and you are the only user on  your PC:
 
[jaunty_i386]
description=Ubuntu 9.04 Jaunty for i386
directory=/srv/chroot/jaunty_i386
personality=linux32
root-users=jimbob
type=directory
users=jimbob
 
(2) Let's say your userid is "jimbob" and you have 1 other user who might use this and their userid is "billybob":
 
[jaunty_i386]
description=Ubuntu 9.04 Jaunty for i386
directory=/srv/chroot/jaunty_i386
personality=linux32
root-users=jimbob
type=directory
users=jimbob,billybob
 
You can't just leave "myusername" and "otherusernames" in that file - you *MUST* put in actual Ubuntu userid's from your PC.
 
This is as far as I can go with this.  Make the changes and try it.  If you still need additional help, I hope someone who knows about this can help.

---

### Post by Chronon on 2011-03-22
Obviously, I substituted dummy usernames.  I didn't wish to share specific usernames on this forum.

Just to be clear, I'm not asking for help.  My 32-bit chroot system is working just fine.

---

### Post by wep940 on 2011-03-23
I mistook you, I guess, for the Original Poster. I didn't realize you already had this working - perhaps saying something like "I have mine working fine - here is what my file looks like" may have been more clear for me, but I often don't remember what I should.
 
So, thanks for posting what works for you - hopefully the original poster already has their problem solved, in which case this thread should be closed.
 
TO TheMann01 - HAVE YOU SOLVED YOUR PROBLEM YET?  IF SO, PLEASE MARK THE THREAD SOLVED.  IF NOT, PLEASE POST BACK WHAT YOUR CURRENT PROBLEM IS.   THANKS!

---

### Post by Chronon on 2011-03-23
Yeah, looking back I can see how my post was a bit ambiguous.  I'll try to be clearer in the future.  :)

---

### Post by TheManno1 on 2011-03-23
**Step 2: Create a configuration file for schroot.**

 Choose a short name for the *chroot*, we use **hardy_i386** in this example, and create a configuration file for it like this: 

  sudo editor /etc/schroot/chroot.d/hardy_i386.confNote: In lucid the filename must not contain '.' , it should be lucid_i386_conf. 
Put this in the new file: 

  [hardy_i386]
  description=Ubuntu 8.04 Hardy for i386
  location=/srv/chroot/hardy_i386
  #personality=linux32
  root-users=bob
  run-setup-scripts=true
  run-exec-scripts=true
  type=directory
  users=alice,bob,charlieNote:  if you copy this example to your clipboard, be careful to start each  line in column 1 before you save the new file! If you forget, the  command **schroot -l** will fail with an error, e.g. E: /etc/schroot/chroot.d/hardy_i386.conf: line 0: Invalid line: “  [hardy_i386]”. 
Note: for lucid use **directory** instead of **location**, e.g. **directory=/srv/chroot/hardy_i386** . 
Change these things in the example configuration file to fit your system: 

[LIST]
[*]**location**:  This should be a directory that is outside of the /home tree.  The latest schroot documentation recommends /srv/chroot. 
[*]**personality**:   Enable this line if the host system is 64-bit running on an amd64/x64  computer and the chroot is 32-bit for i386.  Otherwise, leave it  disabled. 
[*]**users**: These are users on the host system that can invoke the schroot program and get access to the *chroot* system.  Your username on the host system should be here. 
[*]**root-users**: These are users on the host system that can invoke the schroot program and get direct access to the chroot system as the root user. 
[/LIST]
Note: Do not put whitespace around the '=' character, and do not quote strings after the '=' character. 
 
[B]
What is a clipboard? My version
[Maverick_i386]
  description=Ubuntu 10.10 Maverick for i386
  location=/srv/chroot/maverick_i386
  #personality=linux32 (How do you enable this?)
  root-users=Family
  run-setup-scripts=true
  run-exec-scripts=true
  type=directory
  users=Family           

[/B]

---

### Post by TheManno1 on 2011-03-24
[LIST]
[*]Re: Can you create a debootStrapChroot version of ubuntu 32bit 10.10 Step 2: Create a configuration file for schroot.  Choose a short name for the chroot, we use hardy_i386 in this example, and create a configuration file for it like this:  sudo editor /etc/schroot/chroot.d/hardy_i386.confNote: In lucid the filename must not contain '.' , it should be lucid_i386_conf. Put this in the new file:  [hardy_i386] description=Ubuntu 8.04 Hardy for i386 location=/srv/chroot/hardy_i386 #personality=linux32 root-users=bob run-setup-scripts=true run-exec-scripts=true type=directory users=alice,bob,charlieNote: if you copy this example to your clipboard, be careful to start each line in column 1 before you save the new file! If you forget, the command schroot -l will fail with an error, e.g. E: /etc/schroot/chroot.d/hardy_i386.conf: line 0: Invalid line: &#8220; [hardy_i386]&#8221;. Note: for lucid use directory instead of location, e.g. directory=/srv/chroot/hardy_i386 . Change these things in the example configuration file to fit your system:      * location: This should be a directory that is outside of the /home tree. The latest schroot documentation recommends /srv/chroot.     * personality: Enable this line if the host system is 64-bit running on an amd64/x64 computer and the chroot is 32-bit for i386. Otherwise, leave it disabled.     * users: These are users on the host system that can invoke the schroot program and get access to the chroot system. Your username on the host system should be here.     * root-users: These are users on the host system that can invoke the schroot program and get direct access to the chroot system as the root user.  Note: Do not put whitespace around the '=' character, and do not quote strings after the '=' character.   What is a clipboard?
[*]My version [Maverick_i386] description=Ubuntu 10.10 Maverick for i386 location=/srv/chroot/maverick_i386 #personality=linux32 (How do you enable this?) root-users=Family run-setup-scripts=true run-exec-scripts=true type=directory users=Family
[/LIST]

[LIST=1]
[*]See previous post [http://ubuntuforums.org/images/smilies/star.png](http://ubuntuforums.org/images/smilies/star.png)
[/LIST]

---

### Post by Chronon on 2011-03-24
> **TheManno1 said:**
>  
[B]
What is a clipboard? My version
[Maverick_i386]
  description=Ubuntu 10.10 Maverick for i386
  location=/srv/chroot/maverick_i386
  #personality=linux32 (How do you enable this?)
  root-users=Family
  run-setup-scripts=true
  run-exec-scripts=true
  type=directory
  users=Family           

[/B]
Enable that option by uncommenting the line:
```
[Maverick_i386]
description=Ubuntu 10.10 Maverick for i386
location=/srv/chroot/maverick_i386
personality=linux32
root-users=Family
run-setup-scripts=true
run-exec-scripts=true
type=directory
users=Family       
```

Also, I think the run-setup-scripts and run-exec-scripts options are deprecated and will throw warnings (but the chroot should still run).

---

### Post by TheManno1 on 2011-03-24
base installed successfully but W: No chroots are defined in ‘/etc/schroot/schroot.conf’

---

### Post by TheManno1 on 2011-03-25
base installed successfully but W: No chroots are defined in ‘/etc/schroot/schroot.conf’

---

### Post by TheManno1 on 2011-03-25
base installed successfully but W: No chroots are defined in ‘/etc/schroot/schroot.conf’

---

### Post by wep940 on 2011-03-25
You  are bumping your thread up with the same exact post.  Read the forum rules - don't bump before 24 hours AFTER your last post.  Do you think your problem is important?  Sure!  But so do the thousands of others looking for help here as well.  Remember, this is not paid support - everything here is volunteers.  Keep in mind they might have other things going on, like work, a family life, etc..
 
So please, bump once, wait 24 hours.  If no response THEN bump again.

---

### Post by TheManno1 on 2011-03-25
**Re: Can you create a debootStrapChroot version of ubuntu 32bit 10.10** 			
 			 			 		   		 		 		You  are  bumping your thread up with the same exact post.  Read the forum rules -  don't bump before 24 hours AFTER your last post.  Do you think your  problem is important?  Sure!  But so do the thousands of others looking  for help here as well.  Remember, this is not paid support - everything  here is volunteers.  Keep in mind they might have other things going on,  like work, a family life, etc..
 
So please, bump once, wait 24 hours.  If no response THEN bump again.

okay also how do I compile the latest version of dolphin(Wii) is there a repository

---

### Post by TheManno1 on 2011-03-26
base installed successfully but W: No chroots are defined in ‘/etc/schroot/schroot.conf’ and 
dolphin compile WII.

---

### Post by TheManno1 on 2011-03-27
base installed successfully but W: No chroots are defined in ‘/etc/schroot/schroot.conf’   Does anyone know a dolphin wii repository.

---

### Post by Chronon on 2011-03-28
Depending on what version of Ubuntu you are running, "location" might be deprecated.  Lucid and Maverick need "directory" instead of "location".

---

### Post by TheManno1 on 2011-03-28
What am I suppose to do have 10.10

---

### Post by wep940 on 2011-03-29
10.10 *is* Maverick, so try what Chronon posted last.

---

### Post by TheManno1 on 2011-03-30
Depending on what version of Ubuntu you are running, "location" might be deprecated. Lucid and Maverick need "directory" instead of "location".  I don't understand

---

### Post by bodhi.zazen on 2011-03-30
This is a very long thread, but I suspect you are going about this the hard way.

What application are you trying to run ? What makes you think you need to run it in a chroot (a 32 bit chroot is very outdated and it is rare you would need to do this).

---

### Post by Chronon on 2011-03-31
If you look at the configuration file I posted earlier:
```
[jaunty_i386]
description=Ubuntu 9.04 Jaunty for i386
directory=/srv/chroot/jaunty_i386
personality=linux32
root-users=myusername
type=directory
users=myusername,otherusernames
```

Notice that it says "**directory**=/srv/chroot/jaunty_i386" instead of "**location**=/srv/chroot/jaunty_i386"

I am not claiming this is necessary to accomplish whatever you may be trying to accomplish.  I am only telling you what has worked for me.

---

### Post by TheManno1 on 2011-04-07
How do you run pcsx2 in ubuntu 64 and how do you save 
the file in sudo edito

---

### Post by TheManno1 on 2011-04-08
Hello

---

### Post by wep940 on 2011-04-09
You are obviously trying to do something for which you lack some of the more basic skills and understandings of Linux or Ubuntu.  People have posted answers for you - you post back like their reply meant nothing.
 
do yourself a favor, close this thread, research more on your own until you understand things, then post for help if needed.  Everyone I think just feels you've carried this too far without understanding.

---

### Post by TheManno1 on 2011-04-10
This is what happens when I extrac pcsx2
You don't have the right permissions to extract archives in the folder "file:///srv/chroot/maverick_i386/usr/games"
sOME HOW I MADE A CHROOT AND STILL HAVE NO IDEA HOW YOU SAVE IN SUDO EDITOR how did it make a chroot what am I suppose to do once I have written a chroot sudo editor that is probably my last problem.  I need to know how to save the file in sudo editor.

---

### Post by Chronon on 2011-04-10
I have to agree that you probably need to do some reading on your own to try to figure out some of the basics of Ubuntu.  The program "sudo" allows you to execute the subsequent command as another user.  In Ubuntu we use it to temporarily gain root privileges.  It doesn't have any specific connection with saving or editing.  Saving a file behaves uniformly for different users, so if you know how to save to a location normally then it should be the same if the program is running as root.

---

### Post by TheManno1 on 2011-04-10
Which site do you suggest still I somehow created a chroot and all I have to left to do is to extract pcsx2 now. but
You don't have the right permissions to extract archives in the folder "file:///srv/chroot/maverick_i386/usr/games"

Is it possible I can delete the chroot and create a new one. Also why do i go into the editor if you can't save there. Is linux for dummies going to help learn how to master chroot creating.

---

### Post by Chronon on 2011-04-11
Of course you can delete the chroot but I don't see a reason to do this.  Programs can save to a given location if the user that started the program has write access there.  If your user doesn't have write access to a certain location then you might need to use sudo to launch the program as the superuser.

---

### Post by TheManno1 on 2011-04-11
how

---

### Post by wep940 on 2011-04-11
Please, please, PLEASE - if you don't know how to use sudo as recommended, you really need to get a more basic understanding of things Linux and Ubuntu in particular.  We understand your desire to get these gaming emulators working, but without the basic understandings being presented here you are going to go nowhere.  I think you'll find people are getting tired of trying to answer your questions when you seem to lack the basics.

---

### Post by TheManno1 on 2011-04-11
Which books/site you suggest okay fine I will close this thread If i knew how for a month.

---

### Post by Chronon on 2011-04-11
There are some useful pages in the community help pages:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I have found that these very forums are also useful.  You can search them via the site's search or using google.  Reading topics here has helped me to learn a lot about Ubuntu.  Simply googling for the terms that you don't understand can be useful too.

---

### Post by TheManno1 on 2011-04-24
will a chroot jail work for pcsx2 [https://wiki.archlinux.org/index.php/Install_bundled_32-bit_system_in_Arch64](https://wiki.archlinux.org/index.php/Install_bundled_32-bit_system_in_Arch64) it seems easier

---

### Post by TheManno1 on 2011-04-29
I did some more work and now this is the problem. Base is installed 

I used this command 
 $ schroot -lE: /etc/schroot/chroot.d/maverick_i386.conf.save: [maverick_i386]: Required key ‘directory’ is missing

---

### Post by petran79 on 2011-04-30
I face the same problem here. 

Though if you want it for the pcsx2 emulator, they are preparing a version that does not require chroot. plus it has still many problems with games.  better use Windows version. 

Chroot of Lucid in Maverik works ok. Problem is setting Nvidia's graphic drivers in chroot. 

This chroot situation is one of the many problems Ubuntu has, hence why many people avoid it. I give up. One has to be an expert and compile Nvidia drivers and the kernel to make it work since you can not install 32 bit drivers in 64 bit kernel

---

