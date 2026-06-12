---
title: "[SOLVED] question about su/root"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by cerealtx on 2009-01-12
i can get into root using sudo su and my password works, but using su to become the super user my password does not work, and i read somewhere that the pw should default as root, which it is not, ive tried numerous other logical password with no luck, does anyone know what the pw could be?

---

### Post by hyper_ch on 2009-01-12
why do you need to be root anyway?

---

### Post by stevoo on 2009-01-12
You cannot do 

su 

alone as it will not work

Try 

sudo su 

This will get you in as root .... and dont mess too much around like this,

---

### Post by cerealtx on 2009-01-12
> **hyper_ch said:**
> why do you need to be root anyway?

i have millions of reasons to be root, im the system admin, i should be able to access anything i want and mv what i want where, im aware of sudo commands, this is more just for my own peice of mind, there is no point having that command in the terminal if it does not work

---

### Post by hyper_ch on 2009-01-12
yet you give no real reason as to why you *need* su.

Edit: I think you should have a look at this: [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by cerealtx on 2009-01-12
> **hyper_ch said:**
> yet you give no real reason as to why you *need* su.

Edit: I think you should have a look at this: [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

you might wanna read it "Tutorials explaining how to enable the root account for a graphical login or autologin" which is not what im wanting at all im a cli user, this is mostly for my peice of mind, i can accomplish anything i want with sudo su which is root, and if u really wanna know what i use it for lets go through them all, wireshark, updates, backups, filepermission, formating the normal stuff u use root for

---

### Post by overdrank on 2009-01-12
> **cerealtx said:**
> you might wanna read it "Tutorials explaining how to enable the root account for a graphical login or autologin" which is not what im wanting at all im a cli user, this is mostly for my peice of mind, i can accomplish anything i want with sudo su which is root, and if u really wanna know what i use it for lets go through them all, wireshark, updates, backups, filepermission, formating the normal stuff u use root for

Hi and that is what you are asking is to enable root.

---

### Post by hyper_ch on 2009-01-12
> **cerealtx said:**
> you might wanna read it "Tutorials explaining how to enable the root account for a graphical login or autologin" which is not what im wanting at all im a cli user
Well, you just read the first paragraph. Congratulations. Have a goo at the rest also ;)

---

### Post by cerealtx on 2009-01-12
k so i acctually read throuhg it all, and all i can see is Ubuntu made the decission based on security not to allow su and only allows temp access through sudo su? am i catching on :)

---

### Post by LowSky on 2009-01-12
yes you are catching on. Ubuntu's development team and many of the users here believe that root is way to powerful for the normal user to need.
It is the oposite mentality that Microsoft Developers used in Windows.

The lack of root allows most user to maintain stabiltiy with the occasionally ability to access the system only when needed.
Sudo command acomplish this easily.

If you need root access for a multiple of cammands use 
sudo -i
it will grant you access to root for an extended time, so you dont have to keep entering sudo to commands, and so you dont have login as a super user

---

### Post by tarps87 on 2009-01-12
The simple answer is there is no root password as there in 'no' root user to try and increase the security. If a user logs on a root and type a malicious command who knows what will happen, if they have to use sudo for the command it acts as a warning. This is not to say that you are not capable of using a root account it is the settings for the default install. I hope this answers you question

Edit:

> **cerealtx said:**
> k so i acctually read throuhg it all, and all i can see is Ubuntu made the decission based on security not to allow su and only allows temp access through sudo su? am i catching on :)

You caught on too quick or I type too slow

---

### Post by hyper_ch on 2009-01-12
root exists, it's just not enabled - so nobody can actually login as root.

---

### Post by tarps87 on 2009-01-14
> **hyper_ch said:**
> root exists, it's just not enabled - so nobody can actually login as root.

If you are referring to my post that was what I meant my 'no', just wasn't very clear #-o

---

