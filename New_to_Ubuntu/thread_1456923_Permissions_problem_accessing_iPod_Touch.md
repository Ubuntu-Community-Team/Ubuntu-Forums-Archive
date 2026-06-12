---
title: "Permissions problem accessing iPod Touch"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by stuartcox on 2010-04-17
Using NBR and ipod touch 32g 2nd gen jailbroken

I have been trying to connect my ipod and i keep getting permissions problems. I am not fully conversant with chmod and chown so need advice.

I have added fuse via instructions here: [http://fatbuttlarry.blogspot.com/2010/01/ipod-touch-iphone-3g-ubuntu-910-in-5.html](http://fatbuttlarry.blogspot.com/2010/01/ipod-touch-iphone-3g-ubuntu-910-in-5.html)

I know i have changing permissions on the ipod via Terminal but have forgotten what i did. Unforgiveable i know. I was following advice on the net without understanding. Anyway.

When I connect my ipod it is recognised via the .gvfs method.

If I
sudo ifuse /media/ipod I am asked for password and then my ipod shows as mounted  in the file browser. If i try to access it i get

Could not display "/media/ipod". Access denied.

If I
 ls -l /media
ls: cannot access /media/ipod: Permission denied
total 4
lrwxrwxrwx 1 root root    6 2010-04-13 00:38 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2010-04-13 00:38 cdrom0
d????????? ? ?    ?       ?                ? ipod

If I try to SSH via USB i get access denied.

I really do not understand permissions. I am sure i have done something on the ipod side of things but what can i do and how can i check.

One week into trying to solve this.

Thank you.

Stuart

---

### Post by stuartcox on 2010-04-19
Have i posted this to the right forum? please advise. 
 
Now i am coming across more problems. 

My terminal emulator will not open and anything which seems to need a permission says basically cannot do.

Plus i just came across this when trying to dismount from fuse.

umount: /media/ipod is not in the fstab (and you are not root)

I think my main question is that i really do not know what i have done to my permissions or understand groups and owners etc and what do i do to alter it.

Stuart

---

### Post by tom.swartz07 on 2010-04-19
Hi Stuart


This link should take care of your immediate needs with setting up iPhone and iPod sync. Once you use this method, you should be able to sync music via Rhythmbox.
[http://www.webupd8.org/2010/01/easy-way-to-sync-your-iphone-with.html](http://www.webupd8.org/2010/01/easy-way-to-sync-your-iphone-with.html)

It might be advisable for you to restart your computer, adding things to Fuse and the like usually dont take effect until the program is restarted.

Here is an interesting guide to user permissions: [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
What happens on your computer, in short, system files are owned by a user called root. Your specific files, music, pictures, etc, are all owned by you. When you use chown, it is a command to change who 'owns' the file, root or yourself. chmod, on the other hand, changes file permissions. This allows a text file with commands or something run as a program, or in your case, allows the ipod to be read and written to.


Also, If youre willing to wait until April 29th, the newest version of Ubuntu (10.04) will have full support for the iPod and iPhone right as soon as you install it.

---

### Post by stuartcox on 2010-04-20
Thankyou.

re

"This link should take care of your immediate needs with setting up iPhone and iPod sync. Once you use this method, you should be able to sync music via Rhythmbox.
[http://www.webupd8.org/2010/01/easy-...hone-with.html]("http://www.webupd8.org/2010/01/easy-way-to-sync-your-iphone-with.html")

It might be advisable for you to restart your computer, adding things to Fuse and the like usually dont take effect until the program is restarted."

I have followed this link beforeand i believe i do not have a problem with this set up. Rather it is my ipod touch that might have a corrupted Music DB. for instance when i open Rhythmmbox 2 instances ask me to to enter model (the option however does not open) and enter name to initialize. I try but nothing. Rhythmbox does not recognize my ipod.

via fuse sudo fuse /media/ipod when i try to accessmy ipod it says Could not display /media/ipod Access denied.

i cannot access my virtual terminal anymore. it throws me out and if i try to reinstall via Cydia it errors. Looks like permissions again.

I read you article and understand a little what you said but do you have a walkthrough how to right my permissions and ownerships to so i can reaccess my ipod. 

sorry for the long post

Stuart

---

### Post by funfrank on 2010-06-28
I am having the same exact issue.  Were you able to solve this problem?  Please post the solution if you have.

---

### Post by funfrank on 2010-06-30
bump.

---

