---
title: "root question"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by audit on 2009-08-21
this is such a stupid question I hate to ask, but...

how do I log on as "root"? I tried 
```
su -
```
but I am told my authentication failed. I am the only one who has ever used this computer, and I have no doubt about the password I would have chosen. I have no reason to see my # sign, I just want to know I can do it.

---

### Post by chriswyatt on 2009-08-21
I think su is disabled in Ubuntu, at least that's the idea I got.

You can do 'sudo' then the command you want.  E.g.

```
sudo apt-get update
```.

Or you can add the root terminal to Applications if you want root access without having to type sudo over and over again, which is basically what 'su' does I think.

---

### Post by Commisar Jimp on 2009-08-21
logging on as root is very dangerous, you should never do it as it can SERIOUSLY screw with your files, and open you up to viruses. Anything you want to do that requires root access can be done in your normal account by temporarily upgrading your privilges. iIn the GUI it will ask for your password, when you give it then you have temporary access and can do things like access synaptic. In the terminal enter "sudo" before a command that requires root access, then give your password

---

### Post by snova on 2009-08-21
You cannot log in as root. Please see [this page]("https://help.ubuntu.com/community/RootSudo").

---

### Post by audit on 2009-08-21
If it is disabled...that is find with me. Actually all I want to know is that I have not done anything stupid. I use sudo all the time. What scared me is when I entered
```
cat /etc/passwd
```
and saw a huge list of users. why so many user If i am the only one on the machine?

---

### Post by snova on 2009-08-21
> **audit said:**
> If it is disabled...that is find with me. Actually all I want to know is that I have not done anything stupid. I use sudo all the time. What scared me is when I entered
```
cat /etc/passwd
```
and saw a huge list of users. why so many user If i am the only one on the machine?

They are all system users.

Note that, if you look at /etc/shadow (where the passwords are stored, you will need sudo to see it), none of the users have passwords (that is, none of them can log in) except your own.

---

### Post by audit on 2009-08-21
one of the reasons I use moved to Linux is so I can learn without fear. I am not worried about screwing up my computer. It I lose everything I reformat and start over smarter than I was before.

---

### Post by sailthesea on 2009-08-21
> **audit said:**
> one of the reasons I use moved to Linux is so I can learn without fear. I am not worried about screwing up my computer. It I lose everything I reformat and start over smarter than I was before.

Fair enough it's a good way to learn
 In Terminal type man sudo for the full picture on sudo's awesome power, it should be all you  all ever need to use  (man  is the prefix that displays the properties of any command , try it out)
 Discussion of logging in at root is actually forbidden in these forums though!:)

---

### Post by chriswyatt on 2009-08-21
> **audit said:**
> one of the reasons I use moved to Linux is so I can learn without fear. I am not worried about screwing up my computer. It I lose everything I reformat and start over smarter than I was before.

Hehe, that's how I learnt how to use DOS / Windows using my parents old PC.

---

### Post by audit on 2009-08-21
I won't ask again...the information I was given was enough to point me in the right direction. Thanks everyone.

---

### Post by sailthesea on 2009-08-21
Cool
Fixing stuff after you broke it is THE best way learn fast!:lolflag:

---

