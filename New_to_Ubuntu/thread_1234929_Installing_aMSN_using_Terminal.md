---
title: "Installing aMSN using Terminal?"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by StrychnineTwitch on 2009-08-08
I'm actually really new to Ubuntu, and literally I know nothing about it. 
I have tried using Pidgin messenger and I didn't like it, so I wanted to go to aMsn, and on another thread I saw something about using Terminal and writing in the code: [ sudo apt-get install amsn]
So I did so, and now it is asking
[sudo] password for ____:

 I tried typing in my password for login, but it wont allow me to type anything.
Can anyone help me on this?
Please use the simplest talk you can, as I completely suck at understanding anything more :P
Thank you so much! :)

---

### Post by halitech on 2009-08-08
it won't show you typing anything, just type it in and hit enter. Its a security feature to prevent people from seeing how many characters you typed in and guessing your password

---

### Post by pedro3005 on 2009-08-08
Oh, and remember to type the administrator (root) password, not your user one.

---

### Post by StrychnineTwitch on 2009-08-08
Alright, thanks so much :)
I cant wait to learn more about Ubuntu so I dont have to ask questions like this anymore, hahaha.

---

### Post by harry2006 on 2009-08-08
i guess sudo requires your user password and not the root password, that defeats the basic purpose of having sudo in the first place!

---

### Post by halitech on 2009-08-08
> **pedro3005 said:**
> Oh, and remember to type the administrator (root) password, not your user one.

what are you talking about? there is no root password, they would user their login password as long as they are the first user created which has sudo rights.

---

### Post by StrychnineTwitch on 2009-08-08
> **halitech said:**
> what are you talking about? there is no root password, they would user their login password as long as they are the first user created which has sudo rights.

I'm actually not the first user created. My dad had to set everything up for me first, and hasn't given my account administrative privileges yet.

edit: And I've tried typing in my user password, and it told me I wasn't in the sudoers file.

---

### Post by atomizer on 2009-08-08
Then I think the only solution is to ask your dad to install amsn.

---

### Post by halitech on 2009-08-08
> **StrychnineTwitch said:**
> I'm actually not the first user created. My dad had to set everything up for me first, and hasn't given my account administrative privileges yet.

edit: And I've tried typing in my user password, and it told me I wasn't in the sudoers file.

if you aren't the first user created then you don't have sudo rights. You will need to get your dad (or someone who knows the first user info) to log into their account and add amsn for you. Then it will be available for you as well.

---

### Post by StrychnineTwitch on 2009-08-08
Yeah, I'll probably do that. 
I just wanted to know for future reference, when the computer is under my administration.

---

### Post by StrychnineTwitch on 2009-08-08
> **halitech said:**
> if you aren't the first user created then you don't have sudo rights. You will need to get your dad (or someone who knows the first user info) to log into their account and add amsn for you. Then it will be available for you as well.
Ok, thanks a lot!

---

### Post by halitech on 2009-08-08
> **harry2006 said:**
> i guess sudo requires your user password and not the root password, that defeats the basic purpose of having sudo in the first place!

Actually, using SUDO is more secure then having a Root user and using that password because with using SUDO, the root account is disabled so if someone wants to hack into your system, they not only need to guess the password but the username as well. Also, the first user created has no extra rights unless invoked using sudo on a command so you don't need to have an admin account and a user account to keep your regular user safe.

---

### Post by nhasian on 2009-08-16
amsn is pretty.  it looks a lot like MSN Messenger.  unfortunately it only supports the msn protocol.  

what didnt you like about pidgin?

In the upcoming Ubuntu Karmic Koala the default messenger will be empathy instead of pidgin.  You can try it out now instead of waiting till october:

[https://launchpad.net/~telepathy/+archive/ppa](https://launchpad.net/~telepathy/+archive/ppa)

---

