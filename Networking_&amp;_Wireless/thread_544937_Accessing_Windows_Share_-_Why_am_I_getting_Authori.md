---
title: "Accessing Windows Share - Why am I getting Authorization Dialog?"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by CMoneyDollaBillz on 2007-09-06
I just finished setting up a Windows share on my Ubuntu Feisty Fawn Machine. On the Windows Vista machine, I shared this folder accessible to EVERYONE with no user authentication security. Furthermore, when accessing the Windows share from another Windows box, I could simply open the folder with no authentication dialogs. However, I set up the share in Ubuntu using the "Connect to Server" option leaving the user name blank. I am able to load the shared folder, see the contents, and even play music files. But for some reason, as soon as the folder loads I get an Authorization Dialog box asking for the user name and password on the Windows Box for the specific shared folder. I could just ignore it and play my music files, but was wondering why I am getting this dialog box and how I can get rid of it. Thanks everyone!

---

### Post by CMoneyDollaBillz on 2007-09-09
bump... anyone?

---

### Post by Megatog615 on 2007-09-09
This is actually a security feature. You can set different share modes to change how to access the shares from other computers. By default, Samba uses "User" mode, which means you have to type in your username and password(like what's happening right now). Share mode makes Samba behave like how Windows serves shares.

1. Open up /etc/samba/smb.conf(with sudo).
2. Take out the ; in front of "security = user".
3. Change "user" with "share".
4. Save and close.
5. Reboot and your shares will behave just like a real Windows share.

---

### Post by GaMeFaNaTiC on 2007-09-11
hi, this happens to me aswell, i changed the settings to share but i still cant click inside a folder shared on a windows os because that authorization dialog pops up and i dont know why because the folders arnt protected with a password. i dont know what the user and pw is either i tried my root one but that didnt work. is there a way to fix this or another way to share files/folders printers and view them using something else other than samba which wont give me this authorization dialog.

---

