---
title: "Anonymous Samba Share not working with Gutsy server"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by sanmadjack on 2007-10-18
I have a dedicated file server in my closet that uses samba to share files for all the Windows and Linux computers. I upgraded to Gutsy today and now when I use XP to access the previously working shares they ask for logins. Even weirder the login name is stuck on DARKHOLMEIII\Guest making it impossible to use an actual login. I've already tried apt-get purging samba and reinstalling it, but once I set up a new share and set user=share it does the same thing. Any ideas?

---

### Post by tubasoldier on 2007-10-19
I have the same issue. I even went in and changed all the samba permissions back to anonymous logins and gave access rights to everything I could. I'm interested in the fix as well.

---

### Post by pixatintes on 2007-10-19
I have the same issue too.. :(

Share folders don't work...

---

### Post by ceefour on 2007-10-19
Same here I can't access any of my data using Samba. Damn :-(

```
...
switch message SMBtrans2 (pid 5550) conn 0x84d12a8
setting sec ctx (1000, 1000) - sec_ctx_stack_ndx = 0
vfs_ChDir to /media/data/pub
call_trans2qfilepathinfo: TRANSACT2_QPATHINFO: level = 1004
error packet at smbd/trans2.c(3273) cmd=50 (SMBtrans2) NT_STATUS_OBJECT_PATH_NOT_FOUND
Transaction 86 of length 94
switch message SMBtrans2 (pid 5550) conn 0x84cf6a0
setting sec ctx (65534, 65534) - sec_ctx_stack_ndx = 0
vfs_ChDir to /tmp
get_referred_path: |pub| in dfs path \pawn\pub is not a dfs root.
error packet at smbd/trans2.c(6256) cmd=50 (SMBtrans2) NT_STATUS_NOT_FOUND
Transaction 87 of length 98
switch message SMBtrans2 (pid 5550) conn 0x84d12a8
setting sec ctx (1000, 1000) - sec_ctx_stack_ndx = 0
vfs_ChDir to /media/data/pub
call_trans2qfilepathinfo: TRANSACT2_QPATHINFO: level = 1004
error packet at smbd/trans2.c(3273) cmd=50 (SMBtrans2) NT_STATUS_OBJECT_PATH_NOT_FOUND
Transaction 88 of length 94
switch message SMBtrans2 (pid 5550) conn 0x84cf6a0
setting sec ctx (65534, 65534) - sec_ctx_stack_ndx = 0
vfs_ChDir to /tmp
get_referred_path: |pub| in dfs path \pawn\pub is not a dfs root.
error packet at smbd/trans2.c(6256) cmd=50 (SMBtrans2) NT_STATUS_NOT_FOUND
Transaction 89 of length 98
switch message SMBtrans2 (pid 5550) conn 0x84d12a8
setting sec ctx (1000, 1000) - sec_ctx_stack_ndx = 0
vfs_ChDir to /media/data/pub
call_trans2qfilepathinfo: TRANSACT2_QPATHINFO: level = 1004
error packet at smbd/trans2.c(3273) cmd=50 (SMBtrans2) NT_STATUS_OBJECT_PATH_NOT_FOUND
Transaction 90 of length 39
switch message SMBtdis (pid 5550) conn 0x84cfef0
setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
vfs_ChDir to /home/ceefour
setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
expo (192.168.1.101) closed connection to service ceefour
Yielding connection to ceefour
vfs_ChDir to /
...


```

---

### Post by ceefour on 2007-10-19
From here: [http://lists.samba.org/archive/samba-technical/2007-May/053388.html](http://lists.samba.org/archive/samba-technical/2007-May/053388.html)

> Ah - this explains a lot. The default for the "msdfs root"
parameter changed between 3.0.24 from True to False.

Has this client been restarted since the new Samba
load was added and restarted ?

If not - try rebooting the client. The clients remember
if a server was a dfs root and act accordingly until a
restart.

The decision was made to change "msdfs root = no"
due to problems detecting that the initial name given in
a dfs root path belonged to this server (as I recall).


I'll try rebooting my Windows PC. If it works then problem solved.

If not then I'll scream some more :-P

---

### Post by ceefour on 2007-10-19
Yes it worked!

Simply restarting my Windows solved the problem.

---

### Post by jlombs on 2007-10-19
I am having an issue where I can connect to my Windows Shares, but when I try to listen to music it cuts out after 20 seconds and my divx movies won't even load.  I never had an issue before and I have the same connectivity % (60-80%)

It seems more of a network issue

---

### Post by ceefour on 2007-10-19
> **jlombs said:**
> I am having an issue where I can connect to my Windows Shares, but when I try to listen to music it cuts out after 20 seconds and my divx movies won't even load.  I never had an issue before and I have the same connectivity % (60-80%)

It seems more of a network issue
Connecting to Ubuntu Samba (Feisty) using Vista Basic always got dropped after a few seconds during copying a big file :-(

---

### Post by sanmadjack on 2007-10-19
I feel stupid now. I should have known that whenever Windows gives me guff, the firs thing I should do is reboot. Using Linux so much I get used to not doing that :) Thanks for the help!

---

