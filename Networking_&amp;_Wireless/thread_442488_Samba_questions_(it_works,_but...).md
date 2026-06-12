---
title: "Samba questions (it works, but...)"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by Znupi on 2007-05-13
Well, I got samba up and running and am able to see shares from windows, and windows is able to see my shares. Excellent. But:

1) If I go to network:///, I see nothing. I am able to access other computers using smb://<computer_name>, but they don't appear under network:/// until they have accessed my computer.

2) If I access a computer that only has two folders in share, I see what partitions it has :O. Example: that PC (it's using windows) has two partitions: C:\ and E:\. When I go to smb://<computer_name> I get these folders:
C$ , E$ , <Folder1> , <Folder2>
Obviously, I can't access C:\ or E:\, it asks for a password and nothing works. I can access the two folders with no problems, though.

PS: I don't think that is the usual case. It might have something to do with the fact that one folder is on C:\ and the other on E:\. I think that if there was no folder on E:\ for example, E$ would not appear. Anyway I have yet to test thins.

Are these two things normal?

---

### Post by [S|G] on 2007-05-13
Are you in the same workgroup/domain as the other computers? You can specify that if you edit your /etc/samba/smb.conf and setting "WORKGROUP = YOURWORKGROUP".

As for question number 2, that is absolutely normal. C$ and E$ are administrative shares that windows enables by default. If you have the computer's administrator password, you can connect to C$ (using user administrator and its password) and have access to all files on C:\. You can also access that from any windows machine, the only difference is that windows hides the administrative shares.

C$ and E$ would appear as long as there is a disk that correspond to that letter :) So if you had a D:\ then you would be able to access it using D$

---

### Post by Znupi on 2007-05-14
> **'[S|G] said:**
> C$ and E$ are administrative shares that windows enables by default. If you have the computer's administrator password, you can connect to C$ (using user administrator and its password) and have access to all files on C:\. You can also access that from any windows machine, the only difference is that windows hides the administrative shares.

C$ and E$ would appear as long as there is a disk that correspond to that letter :) So if you had a D:\ then you would be able to access it using D$
Lol, cool, I didn't know that...
> **'[S|G] said:**
> Are you in the same workgroup/domain as the other computers? You can specify that if you edit your /etc/samba/smb.conf and setting "WORKGROUP = YOURWORKGROUP".

Yes, we are in the default, 'mshome', and the strange thing is that, if I remember correctly, when we were in different workgroups, they showed up immediately as I opened network:///

---

