---
title: "[SOLVED] How do I reset all my passwords?"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by scotttie on 2009-01-11
Hi eveyone,
I reset my password in user groups but this doesn't seem to have a global effect, I now find myself using two passwords for different sections of Ubuntu, how can I changs this so all password entry prompts are one password?
thanks 
Scottie:confused:

---

### Post by DGortze380 on 2009-01-11
> **scotttie said:**
> Hi eveyone,
I reset my password in user groups but this doesn't seem to have a global effect, I now find myself using two passwords for different sections of Ubuntu, how can I changs this so all password entry prompts are one password?
thanks 
Scottie:confused:

Open a terminal and use the command:

passwd <username>

replace <> with your username.

---

### Post by theozzlives on 2009-01-11
you should use your password, what are you trying to do?

---

### Post by Michael.Godawski on 2009-01-11
hi,

have a look at this guide to reset your sudo password.


[LIST]
[*][http://godawski.oxyhost.com/resetpassword.html](http://godawski.oxyhost.com/resetpassword.html)
[/LIST]

---

### Post by DGortze380 on 2009-01-11
> **theozzlives said:**
> you should use your password, what are you trying to do?

he's trying to change his password...

---

### Post by scotttie on 2009-01-11
Hi theozzlives, 
> you should use your password, what are you trying to do? 
Um I need to change the Password because I am not the only one who knows what it is, and to stop changes being made without me knowing I thought it best to have a password nobody else knows (initially ubuntu was put on as a trial with family password, but I am so pleased with it I intend to keep it on) so Thats the reason for the change.
Thanks for your interest.
Scottie

---

### Post by theozzlives on 2009-01-11
> **scotttie said:**
> Hi theozzlives, 

Um I need to change the Password because I am not the only one who knows what it is, and to stop changes being made without me knowing I thought it best to have a password nobody else knows (initially ubunto was put on as a trial with family password, but I am so pleased with it I intend to keep it on) so Thats the reason for the change.
Thanks for your interest.
Scottie

go to system>administration>users/groups. Click on unlock, highlight your username and click properties. Chang your password at the bottom.

---

### Post by scotttie on 2009-01-11
thanks all,
That worked for the main part of Ubuntu but now evolution still seems to be holding the old password? wont let me in with the new one tried rebooting etc any ideas please,
thanks 
Scottie

---

### Post by ciborium on 2009-01-11
You probably used your username's password as your keyring password.  

See [http://ubuntuforums.org/showthread.php?p=2302037](http://ubuntuforums.org/showthread.php?p=2302037)

I did the same thing when I first tried out Ubuntu.  I used user/user1 as the username/password, then decided it wasn't such a good idea.  Every time I would log into my FTP server I had to use my old password to unlock the keyring.

---

