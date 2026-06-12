---
title: "Ubuntu share folder cannot be accessed in Windows."
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by rocketero on 2007-04-19
Hello ubuntu communtiy

I just installed ubuntu 6.10 in a vmware virtual machine and all works fine except for the share folders with samba.

in ubuntu I can see the windows machines and access files, but from windows even that I see the ubuntu box in windows network , I cannot access files in the ubuntu machine.

I have checked that the shares are done with SMB and that permissions are allowed for everyone but I still don't undertand why when i try to input a username and password to access the ubuntu share in windows it tells me that the login information is not correct.

Any help with this would be appreciated in advance.

---

### Post by FriscoZR on 2007-04-24
Getting the same thing in 7.04.

If I try to logon via windows-xp pro with username & pw, windows brings up another dialog box with hostname/username (with the 1st char capped - when it's not on the ubuntu box) and it still doesn't logon with that capped or not with the correct pw. Have tried multiple accts with admin privalages - nothing seems to work.

I'm guessing it's a Samba cfg issue, but I've not been able to figure out what it is. :( 

If anyone can shed some light on this - it would be greatly appreciated.

---

### Post by SXR on 2007-04-25
not only canI not access ubuntu 7.04 from windows but from ubuntu windows will not allow me to access the files I can only see that the XPbox is connected to the network .

---

### Post by jacom on 2007-04-25
I have the same issue. I can browse windows fine from linux, but when I want to browse from windows it asks me for a login and nothing works!

---

### Post by FriscoZR on 2007-04-25
Ok,
I've gone through the tutorial on peer 2 peer found here [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) a couple of times.
1st time through I just modded my file (smb.conf) instead of renaming and copying the stuff from the window and then modifying.
Actually that worked much better doing that, the rename copy thingy.
Anyway, I still have problems with the step of:

             sudo chmod 0777 /media/samba         when setting permissions

             sudo chmod 0777 /media/disk            actual 1 that works

It occasionally works, but I'm not sure why, and when I restart - it definately doesn't work.

From the Windows side it says I don't have permissions when this doesn't work.
The first time around, it wouldnt logon until I used the file in the tutorial. I'll need to closely examine the diffs to see why it worked better.

1) Anyone got an idea of why when I restart I don't get my volume set as 'disk' for the above permissions thing to work?  Did I forget to put a mount somewhere - and if so where - or something else stupid like that?

2) Can the permissions statement be put into the samba  (smb.conf) file to make that automatic?

3) I also must be totally daft, I don't seem to be able to find the mapper stuff they talk about. Can someone point me in the right direction there?

Thanks for the assist everyone,
MP

---

