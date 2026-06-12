---
title: "Cron stops work when logged out"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by estipois on 2011-05-08
Hi!
I'm using ubuntu server 10.04.2 LTS.
I have set up the crontab what runs a php script every fifth minute.
I'm logging in over SSH and while i'm logged in, it runs the script. While I'm not logged in, the script is not executed. 
Could somebody success where to start looking for problem. 

Thanks!

---

### Post by yetiman64 on 2011-05-08
> **estipois said:**
> Hi!
I'm using ubuntu server 10.04.2 LTS.
I have set up the crontab what runs a php script every fifth minute.
I'm logging in over SSH and while i'm logged in, it runs the script. While I'm not logged in, the script is not executed. 
Could somebody success where to start looking for problem. 

Thanks!
Each user on the system has a crontab. One for your user and one for root, if the install only has your user account.

<removed wrong info, thanks DaithiF,>

Did you use "crontab -e" or "sudo crontab -e" to insert the script entry?

---

### Post by DaithiF on 2011-05-09
> **yetiman64 said:**
> If you log out your crontab will not do anything

No, no, no.  Cron will run regardless of whether a user is logged in or not.  Thats actually the whole point, to be able to run jobs unattended.

@OP, is your home directory encrypted by any chance?  That is one reason why cron jobs may fail when your user is not logged in, because your directory is only decrypted while you are logged in.

---

### Post by estipois on 2011-05-09
Thanks for replies!

I do not think that the home folder would be encrypte. At least by myself i have not choosed such a option neither installed / configure somewhere. 

I will try to put it run under root. Will see how then will be. 
But should Cron write somewhere the log also, lets say when it will be called out ?

---

### Post by DaithiF on 2011-05-09
Just to make sure on the encrypted home directory, does this directory exist?

/home/.ecryptfs/<yourusername>

if so then you have an encrypted home directory.

---

### Post by estipois on 2011-05-09
DaithiF,
I checked over and Yes, I do have there the encrypted home folder.
So what should I do now? How can I still run the cron? or maybe I should move the files, what i'm using with cron, to not crypted folder?

---

### Post by DaithiF on 2011-05-09
> **estipois said:**
> DaithiF,
I checked over and Yes, I do have there the encrypted home folder.
So what should I do now? How can I still run the cron? or maybe I should move the files, what i'm using with cron, to not crypted folder?
if moving the files is an option then yes.  personally i would start over with an unencrypted home, as i don't think it adds much value on a server and complicates system admin.

---

### Post by estipois on 2011-05-10
It is not a big system what i'm runing here. 
but yeah, it helped when i moved the file to not crypted folder. 

Thanks for help.

---

