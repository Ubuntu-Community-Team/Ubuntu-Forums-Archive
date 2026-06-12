---
title: "Samba and windows"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by maddot on 2006-11-12
I've followed the guide and installed samba into ubuntu. I want the pc i installed ubuntu to become a file server on my lan which is made up of 2 linux pcs and 2 windows pcs. after setting it up, i have 3 partitions made. /dataA, /dataB, /dataC, now, for some reason, i can't write to them from any of my pcs on the lan. Later i found out, i can't even write to it in the ubuntu box itself. Are they connected or something must be done? The read only checkbox is already unticked and this problem still persists.

---

### Post by DavidTangye on 2006-11-12
I presume you mean that on the server box you cannot write to partitions mounted at /dataA, /dataB, /dataC.

OK so forget the samba issues, just get those partitions writable locally first.

What is the contents of /etc/fstab? I am guessing the partitions are formatted as ntfs maybe, and not writeable by your kernel? (Although I understand that the kernel can or soon will be able to write to ntfs.

Anyway, the partitions should be ext3 or maybe you prefer reiser format, so the kernel can read/write.

Then your samba server stuff should just work, given what you have said about your samba setup.

---

### Post by cloakable on 2006-11-12
A few questions:

Do you have the samba server allowing guest logins?
 If so, what user are you mapping guest logins to?

And, what are the permissions on the folders you have the partitions mounted in? It has to be writable too - I encountered this problem on my box - I had the share set to writeable, but the folder was set so only I could write to it, with guest set to 'nobody'.

---

### Post by maddot on 2006-11-12
the partitions are formatted as ext3. Yes it allows guest login. The thing is, everything i try to do in the gui mode, it gives me a big access denied, even if i want to access other directories within the root. It'm thinking they are connected. I also checked the permissions given to the partitions, apparently they belong to root and i have no access to write on it. How do i fix that. The boxes are greayed out and i can't change it from that gui, guess the only way is through the terminal. Can i create a root account or something that has complete access to everything in the gui for the directories?

---

### Post by cloakable on 2006-11-12
In the terminal:
```
sudo chmod ugo+rwx /path/to/partition1 /path/to/partition2 /path/to/partition3
```
After that, you should be able to write to the partitions.

---

### Post by maddot on 2006-11-12
ok, i tried that, now i can write on the box itself, but i still can't write from the windows pcs.

---

### Post by cloakable on 2006-11-12
Odd. Do you mind posting the contents of your /etc/samba/smb.conf file?

---

