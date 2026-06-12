---
title: "problem finding the root password"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by Imesmi on 2011-05-01
So I have created two users in linux (owner how can i call that )
But I don't know which is the password of the root su. I have tried each of the passwords of the two users but it doesn't work. I really need to find the root password because I also have problem connecting with the internet :confused:  a adsl connection with the modem my pc is dell inspiron 1420 and I tried the pppoeconf but it asks the password of the root and I don't know it. pleaaaaaaaaaaase help me out coz i have tried a lot by myself and i couldn't do anything. thank you in advance

---

### Post by Quackers on 2011-05-01
Welcome to UF.
When using sudo the password is your user's password. 
sudo su is the same.

---

### Post by Imesmi on 2011-05-01
> **Quackers said:**
> Welcome to UF.
When using sudo the password is your user's password. 
sudo su is the same.

But i tried the password of the user i was logged in and when i typed the password it replied authentication failed

---

### Post by hakermania on 2011-05-01
You are maybe asking of the password prompt on login when asking for internet connection.
If this is your problem, yes, you have to type the su passwd and not the current user's password!

If you've never been su you can try the following in a terminal:
1)```

sudo su

```
Press Enter. You'll be asked for password, type your user's password (the one who's logged in). You won't see anything echoed (not even ****) instead of your password, but this is for security reasons, it will be written normally. Once finished typing your password, press Enter again. By doing so, you'll gain su power. After this, type
```
passwd
```
If the su has already got a password, I cannot find a possible solution, but if not, this will prompt instantly for new su password (which you have to type twice). After this, this password which you typed will be used in the prompt dialog when you boot your system.
Also, in order to avoid future prompts of this dialog, you can do the following:
1) Click on the Signal icon on the top right corner
2) Select 'Edit Connections' and go to the 'Wireless' tab
3) Select your current modem in which you're connected or you are usually connected in and Select 'Edit'
4)  Check the Checkbox at the bottom left corner of the window 'Available to all users'
5) Press save and type the su password which you created previously

Hope I helped you or anyone else following this thread

---

### Post by CharlesA on 2011-05-01
The root account is locked by default in Ubuntu. You use sudo to run commands as root.

See here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Imesmi on 2011-05-01
i did as you said hakermania but when i typed the password of the user i was logged in and pressed enter it promted that the user account i was logged in is not in the sudoers file and this action will be report. :((

---

