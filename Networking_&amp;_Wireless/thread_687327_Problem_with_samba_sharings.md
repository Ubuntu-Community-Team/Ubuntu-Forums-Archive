---
title: "Problem with samba sharings"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by pikitsan on 2008-02-04
Hi i have a prob with the sharing folders of my pc's.I run ubuntu 7.04 in my dekstop and the other pc has windows.
The problem is that i can't access to the sharing folders of windows cause ask me for a password and username that i don't know.Btw the pc with windows has access to my files cause  a made a samba account for it ...Can anyone help me and tell what to do ???


ps:This happens when i set a sharing folder from the win pc and not copying the files i want to smb://other pc/SharedDocs.Also all firewalls are turned down...

---

### Post by ruy_lopez on 2008-02-04
The username is the account name you chose when Windows was installed. The password is empty (since you don't use one to boot into windows).

If you cannot remember the Windows account name, you can find it by looking within "C:\Documents and Settings\"

---

### Post by pikitsan on 2008-02-04
No nothing happened.When the other pc installed windows didn't create any account so i think he log in with the admin's account....cause no log in screen appears.:sad::shock: .I must create another account user in win ??? If i use the guest account ???

---

### Post by pikitsan on 2008-02-05
Anyone else ????

---

### Post by ruy_lopez on 2008-02-05
When Windows is installed it asks for your name, and then creates an account using that name. You are right about it being an admin account. Windows XP creates an admin account by default. But it still uses the users name FOR the admin account. Explore C:\Documents and Settings\ and look for a subfolder that begins with a persons name. 


It will look like this:


C:\Documents and Settings\JohnDoe\


In this case you would use "JohnDoe" to login using samba.


You can also find your username, by looking in "Control Panel" --> "User Accounts"

---

### Post by pikitsan on 2008-02-05
Thank you for your anwser but should i make a smb account and for this name ???

---

### Post by ruy_lopez on 2008-02-05
No, you shouldn't have to. You are only accessing Windows files from Ubuntu.

All you should have to do, is enable sharing for the files on Windows. Just make sure when you connect to Windows you supply the correct Workgroup name. Usually it is MSHOME.

---

