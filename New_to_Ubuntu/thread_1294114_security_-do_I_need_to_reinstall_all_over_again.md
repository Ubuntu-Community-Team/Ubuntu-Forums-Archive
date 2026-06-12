---
title: "security -do I need to reinstall all over again?"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by dlteach2 on 2009-10-17
My computer was set up by someone else who used my personal name as the computer name which I am very concerned about for security reasons and would like to change that.  In the meantime, I have already followed directions to access the lost admin password which puts me in as a root user if I am using the terminology correctly. Before I follow the directions that I was given on the forum to upload recent security files which currently will not upload,  I'm wondering if it is best for the overall security of the computer to start all over again and reinstall Ubuntu. But the last time I tried to do that, all the same information showed up on the reinstall.  What is the best way to make my computer secure - update the security files and then  follow the directions I was given to change the computer name or start all over again and create new admin info, computer name, etc.?

If the vote is for starting all over again, how do I reinstall without accessing all the same info?

---

### Post by Kprojekt on 2009-10-17
To change the name of the Computer (The Hostname) you have to edit /etc/hostname, however if you decide to change your /etc/hostname, you better change /etc/hosts to the same name or you won't be able to use sudo and some of the network apps will not work...

Applications -> Accessories -> Terminal

Code:

gkudo gedit  /etc/hostname  /etc/hosts

---

### Post by Kprojekt on 2009-10-17
As to your root password issue, i'm not sure what youa re talking about, but you should not be logging in as root, as it poses a security risk.

---

### Post by dlteach2 on 2009-10-19
Thank you.

---

### Post by dlteach2 on 2009-10-19
The directions from psychocats.net gave instructions as to how to access and old password which apparently ends with user identified as a root user. That is why I am still asking if it is best to just start all over again to avoid the possibility of any more security problems.

---

### Post by running_rabbit07 on 2009-10-19
You can change you passwords and user name in the System>Administration>Users & Groups GUI. Your computer name shouldn't pose a problem.

---

### Post by dlteach2 on 2009-10-19
you mean if I change the computer host name which is what I want to do?

---

### Post by running_rabbit07 on 2009-10-19
I meant that you shouldn't have to, unless you want to. As long as you are in control of the password, all should be fine in the eyes of security.

---

### Post by dlteach2 on 2009-10-19
okay, but I do want to change the computer hostname.

---

### Post by louieb on 2009-10-19
> **dlteach2 said:**
> okay, but I do want to change the computer hostname.

You got the how to do that in post #2 - edit those two files.

---

### Post by barnaclebill18 on 2009-10-19
Hello.

I am not an expert, but I just reinstalled.

If you format the drive when you reinstall, all that stuff should be erased.

If you reinstall without formatting, your settings and things will remain.

The easiest way for you to do it, I think, would be to reinstall and make sure you format, since it sounds like you do not have much on it.

---

### Post by running_rabbit07 on 2009-10-20
If you decide to go the route of reinstalling, you may first want to install and run APTonCD to back up mostly all of the updates you have done. This will save you a great amount of time getting the system up and running after the reinstall. 

If you go about making the changes to the computer name as mentioned in post 2 and you change the passwards, as in my previous post, your system should be back to fully secure.

Good luck in whichever choice you make. Let us know if you need help.

---

### Post by dlteach2 on 2009-10-20
Thank you very much for your help. I'll let you know my success.

---

### Post by dlteach2 on 2009-10-20
Thank you. you're right, i have nothing on it at all.

---

### Post by dlteach2 on 2009-10-20
Thank you!

---

### Post by dlteach2 on 2009-10-20
Thank you. I really appreciate the help. I am such a newbie at all of this. Will see what I can do and will come back on line for help needed.

---

### Post by Wehll on 2009-10-20
I seem to have a problem similar, but a few steps back in the process. I feel like a total idiot, but I just installed Xubuntu, and I must have had a typo in the password I typed in during setup, as it will not accept any password type in. So, I was wondering if there was a way to access/change your password without a complete re-installation. Any help would be great.

---

### Post by louieb on 2009-10-20
> **Wehll said:**
> ...a way to access/change your password without a complete re-installation. Any help would be great.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Welcome to Ubuntu forums.

---

### Post by Wehll on 2009-10-20
Thank you. Now I can actually start using my new OS! Pretty quick on response time, too.

---

### Post by dlteach2 on 2010-01-04
Thank you everyone for helping with this. I ended up with a new reinstall and the computer has been working just fine for the most part.

---

