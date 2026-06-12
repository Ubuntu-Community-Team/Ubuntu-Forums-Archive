---
title: "net usershare add: share name is already a valid system user name"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by SaturnusDJ on 2008-09-20
While sharing folder 'Games' I got this error:

```
'net usershare' returned error 255: net usershare add: share name games is already a valid system user name
```

The last thing I want is renaming the folder.

(8.04 + Samba)

---

### Post by SaturnusDJ on 2008-09-21
Someone please?:|

---

### Post by SaturnusDJ on 2008-09-22
Complicated problem or what?

---

### Post by superprash2003 on 2008-09-22
do you have a username called games?? well the "rule" is username and sharename cannot be same.. you dont have to rename folder.. you just have to rename share name.. or you could just remove the games username from system->admin->users and groups

---

### Post by SaturnusDJ on 2008-09-25
Thank you for your reply.:)

I meant that I don't want to use another sharename then 'Games' cause that doesn't make sense.


To the point:
I have 2 users on the system:
- root
- myname

And of course my name is not Games haha.

---

### Post by superprash2003 on 2008-09-25
to confirm check under system->admin->users and groups.. also in your terminal type cat /etc/samba/smbusers and post output

---

### Post by SaturnusDJ on 2008-09-25
No users or groups containing the word 'Games.'

The ```
cat /etc/samba/smbusers
``` command doesn't work. Output is:
```
cat: /etc/samba/smbusers: No such file or directory
```

---

### Post by SaturnusDJ on 2008-09-27
Does someone knows a solution? Or could it be a bug?

---

### Post by SaturnusDJ on 2008-10-05
Someone, please?

---

### Post by Iowan on 2008-10-05
If I check **sudo less /etc/passwd** on my system, there *IS* a user named **games**... although I did not put it there. Probably one of the default system users (like mail, news, man, and dhcp). If your share is named **games**, try **Games**, otherwise, maybe **mygames** or **MyGames**

BTW, **cat /etc/samba/smbusers** doesn't work here, either...

---

### Post by SaturnusDJ on 2008-10-06
Thank you.
I only want to share the dir as 'Games,' nothing else.
Is it save to try deleting that user?

---

### Post by Iowan on 2008-10-06
Looks like my system already has backups of **passwd** and **shadow**, but before I deleted the **games **user, I'd want a current backup/copy to use if something went very wrong. Then, depending on your courage, you could either **sudo deluser**, or just edit the username in the two files (change it to something like **gamer**. Either way might break something.

---

### Post by SaturnusDJ on 2008-10-07
So it actually is possible to permanently fck up Ubuntu when renaming/deleting the user?

---

### Post by Iowan on 2008-10-07
> ...removing the home directory as option or [COLOR="Red"]even all files on the system  owned  by  the  user[/COLOR]  to  be removed, running a custom script, and other features.  From **man deluser** - _with the right options_, everything owned by the user could be deleted.  If you decide that wasn't the thing to do... 
 The default action by **deluser** may not be quite so drastic. Renaming may make the files difficult to get to - but it's reversible.

---

### Post by SaturnusDJ on 2008-10-08
What do you suggest?

Priority:
1. System MUST continue working without things messed up.
2. Sharename should be nothing else then: Games.

---

### Post by Iowan on 2008-10-08
I'd probably use **sudo nano /etc/passwd** and **sudo nano /etc/shadow** to rename the user **games** to **gamer** and try the Samba share again.

---

### Post by SaturnusDJ on 2008-10-08
Can you please give the exact commands? (I'm new to Linux.)
Google search 'sudo nano' didn't had any usefull outputs.

---

### Post by Iowan on 2008-10-08
**man nano** lists options, but here are the steps:
[LIST=1]
[*]CTRL-ALT-F1 (This opens a terminal - actually selects tty1)
[*] Login with your username and password.
[*] Type **sudo nano /etc/passwd** <ENTER>
[*] [sudo] password for <yourusername>: (enter your password)
[*] Arrow down to **games** (line #6 on my system)
[*] Arrow right to "s" - use <DELETE> or <BACKSPACE> to delete "s", type "r".
[*] Type CTRL-O  (filename will appear above command list)
[*] Press ENTER  (this will cause file to be written)
[*]Type CTRL-X  ( exits **nano**).
[*]Type **sudo nano /etc/shadow** <ENTER>
[*]Repeat step 4, if necessary (System might not ask for password)
[*]Repeat steps 5-9.
[/LIST]CTRL-ALT-F7 gets back to desktop.  Instead of CTRL-ALT-F1, you can also use a terminal from Applications>Accessories>Terminal.

If you'd prefer to make a backup first, before step 3:
Type **sudo cp /etc/passwd /etc/passwd~**
Type **sudo cp /etc/shadow /etc/shadow~**

---

### Post by SaturnusDJ on 2008-10-12
It's been a busy week but I followed your instructions some minutes ago. ;)

The backups are saved and the username 'games' is changed to 'gamer.'
Since then it was possible to share the map 'Games.'

Thank you very much for you effort and time.:grin:

---

### Post by albinootje on 2009-01-19
.. [missed page 2 :(]

---

