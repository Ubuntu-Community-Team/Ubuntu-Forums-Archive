---
title: "need new password, required by root, for new user issue."
date: 2010-11-16
forum: New to Ubuntu
---

### Post by yt_l9 on 2010-11-16
:confused:

I just installed Kubuntu when I upgraded to 10.10 mostly to experience KDE.  I had been using Ubuntu for a couple years now and have always been able to fix everything just by simply searching the forums here but I've run into an issue I can't figure out.  

I set up Kubuntu for myself and then I went to add an account for my girl friend, which I did semi-successfully.  Now when I try to log into her account with the password I created for the account it states that root requires that a new password be made.  This wouldn't be an issue but I can't input anything into the dialog box.  I tried to allow her account to log on without a password but that's not working either.  I can't get into her account at all.  I even tried to make her account without a password but the same prompt pops up and I can't type anything at all.  I've tried multiple keyboards to no avail (my main one is a dinovo edge and I've had issues connecting before so I went to my old usb one).  

I'll try going through command line tonight but I don't foresee that making a difference.  Should I just reinstall the log-in section of the OS?  I'm sure I can find how to do that on here somewhere, I hope.

Any suggestions will be greatly appreciated.  If you need more information then I can run home at lunch and try to repost as required.


My hardware, though I didnt have any issues w/ 10.4 Ubuntu so I don't think that is an issue either
2.83 ghz quad core Intel cpu
8 gb ram ddr2 800
64 gb OCZ ssd
p-45a motherboard (Foxconn)

---

### Post by Hippytaff on 2010-11-16
From the terminal, whilst logged into her account you should be able to change the password with
```

passwd

```
though you might need to ad her to the sudoers file.

---

### Post by yetiman64 on 2010-11-16
From man passwd,
> The passwd command changes passwords for user accounts. A normal user may only change the password for his/her own account, _*while the superuser may change the password for any account*_.From my reading of this OP you should be able to change the 2nd account from your account with the command Hippytaff quoted without adding the 2nd account to the sudoers file (gives that user root access). It would look like.
```
passwd <user>
``` replacing <user> with the 2nd account name. You will be prompted to input the password twice though it won't appear to be inputting anything (a security measure for the terminal). If the 2 password entries match in terminal it will inform you when successful.

---

### Post by yt_l9 on 2010-11-16
Hippytaf, the issue is that I can't log into her account at all to change her password.  Well the issue is that root is demanding a new password from the user when logging into her account but I'm unable to create one.

Yetiman,
Will theis yield different results than when I do it from system settings tool-bar?  I'll likely still run home and try it though.  I did check up on how to create an account via commant line and that was my next attempt.  Is there anything I should be doin in terms of groups or should I just create a new one for her?  I was going to just do:

sudo useradd -d /home/lynn -m lynn

or should I not worry about making a directory for her?  Could that be part of the issue?

---

### Post by Hippytaff on 2010-11-16
> 
Hippytaf, the issue is that I can't log into her account at all to change her password. Well the issue is that root is demanding a new password from the user when logging into her account but I'm unable to create one.

 
Sorry, missed that vital bit of info :-s

---

### Post by mcduck on 2010-11-16
Simply running this command (as your own user, assuming you are an admin) should allow you to set the password for a user:

```
sudo passwd username
```

(you don't need to be able to log in as that user, since you run the command with *sudo* it runs as root, and root has the power to change any user's password.)

---

### Post by yetiman64 on 2010-11-16
> **yt_l9 said:**
> Hippytaf, the issue is that I can't log into her account at all to change her password.  Well the issue is that root is demanding a new password from the user when logging into her account but I'm unable to create one.

Yetiman,
Will theis yield different results than when I do it from system settings tool-bar?  I'll likely still run home and try it though.  I did check up on how to create an account via commant line and that was my next attempt.  Is there anything I should be doin in terms of groups or should I just create a new one for her?  I was going to just do:

sudo useradd -d /home/lynn -m lynn

or should I not worry about making a directory for her?  Could that be part of the issue?
Main reason for terminal is I'm unsure of the graphical tools layout in KDE as I'm on Gnome, and as far as I'm aware they both use the same underlying tools via terminal.

As I understand it, useradd  should automatically add the necessary group for the account. Just checked man useradd and the above command looks Ok.

Have a good read of "man useradd" and "man passwd" in the terminal in case I've missed anything though (I'm NOT an expert by any means at this !).

You should probably use the graphical tools from your account to remove the first attempt though **if** you try to add the account in terminal with useradd.

I would suggest you try to set the password _*on the existing account from your account*_ via the terminal command *_first_* though to see if you can successfully repair the first attempt, it sounds from your first post like it has a chance at working in that the main block in getting into the 2nd account is the system complaining it needs a password.

Good luck.

---

### Post by yt_l9 on 2010-11-16
> **Hippytaff said:**
> Sorry, missed that vital bit of info :-s
No worries.

McDuck,
I'll try this at home in about 15 minutes but I've found the issue is not setting the password but when I try to log into her account I get a prompt.
It goes like this:
-sign into account 'lynn' w/ password (tried it without a password as well)
-prompt shows up saying root requires me to create a new password
-I can't input any text into prompt box so I have to cancel.


Thank you all for the help thus far.  Hopefully the terminal works!

Yetiman,
You have it mostly correct on the issue, and hopefully completely on the solution.  It still requires a password to logon to her account but after putting in the correct password I get the second prompt before even loading the system.  I just don't know how to circumnavigate the second prompt where 'root requires a password change'.

---

### Post by yetiman64 on 2010-11-16
> I just don't know how to circumnavigate the second prompt where 'root requires a password change'.Hopefully resetting the password from terminal will alleviate that problem (fingers crossed for you :))

---

### Post by d3v1150m471c on 2010-11-16
```

userdel -r <username> # will remove the entire account
useradd -m <username> # adds a new account

```

do that and see if the account works.

---

### Post by yt_l9 on 2010-11-16
Thank you everyone!
deleting the old profile and just adding it from the terminal (with password) worked!  I guess there is some issue with the graphical front end of either the kde user management system or more likely just me.

---

