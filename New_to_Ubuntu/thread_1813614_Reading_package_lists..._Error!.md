---
title: "Reading package lists... Error!"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by kent69 on 2011-07-28
Reading package lists... Error!

E: Encountered a section with no Package: header

E: Problem with MergeList /var/lib/apt/lists/AZ.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en

E: The package lists or status file could not be parsed or opened.

anyone can help with this issue? I got it before but when i run the VPN I could download the updates, but today even with VPN couldnt got the package because I believe and I know many sites are blocked by admin server

Cheers

---

### Post by wildmanne39 on 2011-07-28
Hi, run these two commands and it should get you fixed up.
```
sudo rm /var/lib/apt/lists/* -vf
```
The first command will remove the damaged list and when you run the second command it will replace it with a new list.

```
sudo apt-get update
```

---

### Post by kent69 on 2011-07-28
I found the above answer by googling the issue no dosent work 

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/Az.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

also the same issue with ubuntu !!! backtrack no issues
thanks

---

### Post by wildmanne39 on 2011-07-28
Hi,ok but did you fix it or did you try the commands I gave you? I have never seen those commands not fix that error.

---

### Post by kent69 on 2011-07-28
> **wildmanne39 said:**
> Hi,ok but did you fix it or did you try the commands I gave you? I have never seen those commands not fix that error.

No I did not fix it, yes I try again the commands you gave and I show in previous message the results after downloading the packages!

really thos issues just bothering I start wondering if because I run kubutu from VM box under windows XP!

while waiting, cheers

---

### Post by kent69 on 2011-07-28
More over the update manager stops working, what Im wondering I didnt do any thing wrong with the OS I was just discovering it open and close windows, !!!

---

### Post by thefasterblueone on 2011-07-28
Be sure your VM has an internet connection.

---

### Post by kent69 on 2011-07-28
Cheers mate I do have connection , this issue on both ubuntu11 and kubuntu11 the backtrack4 works perfect ,,,

---

### Post by wildmanne39 on 2011-07-28
Hi, that is strange that it did not work that ppa must be broken, I would open synaptic and click settings,repositories, other software and uncheck that ppa and then click to reload the list.

I hope you do not need that ppa it is for language translation.

---

### Post by Hubunntu on 2011-08-03
Yea it works . I was facing the same problem. Now its fixed. :guitar:

---

### Post by wildmanne39 on 2011-08-03
Hi, I am glad I could help.

---

### Post by Jouke S on 2011-08-03
Here's a method to copy a status file: 
```
sudo mv /usr/local/var/lib/dpkg/status /home/username/Documents 
```
you now have a status file in a folder that isn't write protected (Documents). Copy it and paste it in a different folder (Downloads)
Now paste these two commands in the terminal(change username of course)
```
sudo mv /home/username/Documents/status /usr/local/var/lib/dpkg/
```
```
sudo mv /home/username/Downloads/status /var/lib/dpkg/
```

---

### Post by evebug on 2012-04-01
Thnx wildmanne39
I was facing same problem, tried few things.
This worked as charm:p

---

