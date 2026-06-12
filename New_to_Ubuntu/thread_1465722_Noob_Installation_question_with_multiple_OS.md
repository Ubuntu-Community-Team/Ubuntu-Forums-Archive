---
title: "Noob Installation question with multiple OS"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by maldonw on 2010-04-29
OK so I was having an issue with having vista fedora and ubuntu on one drive where grub would not see fedora just the other 2 (had a post on this earlier). Now as luck would have it I had to replace my hard drive so a ghosted an earlier image that has vista and fedora. Now i want to install ubuntu without the hassle of what happened before. What do I need to do so that when i install ubuntu grub will see all 3 OS's?

---

### Post by arrrghhh on 2010-04-29
GRUB is supposed to pickup any and all OSes installed.  Are they all on the same drive?  If not, make sure all drives are plugged in.

---

### Post by maldonw on 2010-04-29
> **arrrghhh said:**
> GRUB is supposed to pickup any and all OSes installed.  Are they all on the same drive?  If not, make sure all drives are plugged in.
yes they are all in the same drive. what I plan on doing is going on windows vista and shrinking that partition by lets say 10 gigs and use that free space to install ubuntu. does that sound like the proper thing to do?

---

### Post by arrrghhh on 2010-04-29
> **maldonw said:**
> yes they are all in the same drive. what I plan on doing is going on windows vista and shrinking that partition by lets say 10 gigs and use that free space to install ubuntu. does that sound like the proper thing to do?

That works.  Proper, whatever you determine is best... there's tons of ways to install Ubuntu.  Just pick the one that suits *your* needs best.

---

### Post by maldonw on 2010-04-29
I started a fresh install of ubuntu in an  newly created partition. This created a bit of a different problem. grub  now sees all 3 OS's however when i try to boot fedora I get the  following error : [COLOR=Red]you must load kernel first[/COLOR] [COLOR=Black]it then kicks me back to the grub page to choose another  OS[/COLOR].  I loaded ubuntu and did a sudo blkid and got this 

[COLOR=Red]wilfredo@wilfredo-laptop:~$ sudo blkid
[sudo] password for wilfredo: 
/dev/sda1: UUID="20378F114179A3DD" TYPE="ntfs" 
/dev/sda2: UUID="b8ebdef5-19a0-4a0e-b37c-d87928281842" TYPE="ext4" 
/dev/sda3: LABEL="Fedora-12-i686-L"  UUID="c89d7967-25aa-44e0-8ecd-6d21e57d6797" TYPE="ext4" 
/dev/sda5: UUID="a91f19e1-b82c-4a9e-b49b-9cced833c1cf" TYPE="ext4" 
/dev/sda6: UUID="1db22484-abdd-440c-912b-b859ef12ea87" TYPE="swap" 
wilfredo@wilfredo-laptop:~$ 
[/COLOR]
any ideas??
 		                   		  		  		  		  		  	   	 		 
	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG][]("http://ubuntuforums.org/editpost.php?do=editpost&p=9197238")

---

