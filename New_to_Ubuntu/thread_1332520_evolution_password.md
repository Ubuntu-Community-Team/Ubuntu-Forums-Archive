---
title: "evolution password"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by iRounak on 2009-11-20
I have to enter my password every time in Evolution when i want to check emails for the first time after i boot ubuntu. It says something like "Evolution cannot access the default keyring because it is locked. Please enter the password."

---

### Post by cloyd on 2009-11-20
I am a total novice, but I have an answer.  If you think back on all you did as you installed your system, you were asked  to create _two_ passwords.  One was your administrator password.  The other was the key ring password. That is what Evolution is asking for. You will have to supply it every time you try to send and receive mail (or at least I do at present). 

It is part of what makes Ubuntu and Linux systems relatively free of spyware and viruses. 

If you don't remember setting a second password, I'm sure there is a way to reset it, though I do not have the answer.  I would search the formum for it . . . I'm sure it can be done .

---

### Post by adaucourt on 2009-11-20
@[iRounak]("http://ubuntuforums.org/member.php?u=942898")

I suggest you use the "Forget Passwords" option under the File menu in Evolution.  If you still continue to have problems you can delete the default keyring in /home/your username/.gnome2/keyrings and reboot.  This will cause Ubuntu to prompt to re-enter new passwords.  Remember to mark the Show hidden files check box under the view menu in Nautilus in order to see the .gnome2 folder.

---

### Post by iRounak on 2009-11-20
Hi,
Thanks for the reply.
> You will have to supply it every time you try to send and receive mail (or at least I do at present). 

I dont want to do this. I know which password I have to enter. I want Evolution to stop nagging me for the password.

---

### Post by iRounak on 2009-11-29
Please help......the system password prompt really bugs me.

---

### Post by CorruptDNA on 2009-11-29
well the system prompt password is a really important feature of ubuntu.
just keep that password copied and paste it whenever the prompt appears or so..

---

### Post by dnairb on 2009-11-29
I would assume that the OP has the system set up to automatically log in. Therefore, the keyring remains locked.

To avoid having to enter a password each time Evolution starts, change the log in settings to prompt you for your password at system log on:

System -> Administration -> Login Window -> Security tab

---

### Post by iRounak on 2009-11-29
Thanks for the reply.
> **dnairb said:**
> I would assume that the OP has the system set up to automatically log in. Therefore, the keyring remains locked.

To avoid having to enter a password each time Evolution starts, change the log in settings to prompt you for your password at system log on:

System -> Administration -> Login Window -> Security tab
If this is how it works, then
1. its quite strange--the autologin should unlock keyring as well
2. there must be an alternate way to always keep the keyring unlocked.

---

### Post by dnairb on 2009-11-29
> **iRounak said:**
> Thanks for the reply.

If this is how it works, then
1. **its quite strange--the autologin should unlock keyring as well**
2. there must be an alternate way to always keep the keyring unlocked.

Not necessarily - imagine if someone else *other than you* boots up your system, is logged-in automatically (as you) then has access to *your* emails because the system assumes *you* have turned your computer on.

---

### Post by jrrader on 2009-12-03
[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

seahorse stores all the passwords you save in an encrypted file. When it asks for you password it is asking so it can unlock that encrypted file. By not using a password you are storing all your passwords in an unencrypted file.  By not using a login password and unencrypting  the password file you are giving anyone who comes into your house all your passwords.  I would really suggest turning on the login password and adding the lock screen applet to your desktop if you are going to disable the keyring.

---

### Post by iRounak on 2009-12-03
thanks. It will work for me.

---

