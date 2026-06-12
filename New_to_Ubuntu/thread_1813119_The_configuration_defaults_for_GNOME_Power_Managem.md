---
title: "The configuration defaults for GNOME Power Management have not been installed"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by prodriguez on 2011-07-27
Hi all,

I am new at Ubuntu, I have been ussing it for 6 months and no problem. Currently I have ver 11.04 and after a recent update I got the following message "The configuration defaults for GNOME Power Management have not been installed correctly. Please contact you computer Administrator" and could not longer log in any longer.

Reading similar issues from other users looks like it is a low space issue but not very sure how to fix it. From Terminal I ran this command df -h and I got the following:

/dev/sda1       73G         71G                 0%            100%         /
none            462M       700K            462M             1%        /dev
none            469M              0k            469M             0%        /dev/shm
none            469M        348k            469M             1%        /var/run
none            469M              0k                     0k            0%         /var/lock

Thanks in advance for your help.

---

### Post by jerrrys on 2011-07-27
run these three commands.  this will hopefully free up some space.

is this a wubi (ubuntu inside windows) install?

**Remove all the packages** 	from /var/cache/apt/archives and /var/cache/apt/archives/partial 	folders:  	  
[LIST]
[*]sudo apt-get clean
[/LIST]
 
[LIST]
[*]**Remove 	all expired packages** from /var/cache/apt/archives and 	/var/cache/apt/archives/partial that are no longer available for 	download:  	
[/LIST]
 
[LIST]
[*]sudo apt-get autoclean
[/LIST]
 "*Not available for download*" does not mean the user should save them - normally these files have been replaced or are no longer needed.  
 
[LIST]
[*]**Remove unneeded dependencies** 	which are no longer needed:  	
[/LIST]
 
[LIST]
[*]sudo apt-get autoremove
[/LIST]

---

### Post by prodriguez on 2011-07-27
Thank you jerrys

Prior to getting your response I have removed some unused files from /home with rm. This has created some free space and was I has able to log in again.

This is not a Wubi it has its own partition. I have a dual OS on running on this desktop and I can boot Windows or Linux.

Regardless this do you still recommend to execute these three commands or they are only applicable for Wubi?

Thanks
Pablo

---

### Post by jerrrys on 2011-07-27
no, you can use those commands to hopefully clear some space.

---

### Post by prodriguez on 2011-07-27
Thanks again.

It worked wonderful.

I can consider this issue [SOLVED].

---

### Post by jerrrys on 2011-07-27
also

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

[http://www.dedoimedo.com/computers/gparted.html#mozTocId335513](http://www.dedoimedo.com/computers/gparted.html#mozTocId335513)

EDIT:  "Solved" is located under thread tools

---

