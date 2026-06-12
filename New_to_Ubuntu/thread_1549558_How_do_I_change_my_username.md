---
title: "How do I change my username?"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by Hi-Ho-Silver! on 2010-08-09
Hi, how do I change my username on ubuntu? 
Thanks :D

Edit: *SOLVED* ty all!

---

### Post by Nesaskewatch on 2010-08-10
System/Administration/Users and Groups.  You'll see the option there.

Welcome aboard!

---

### Post by inameiname on 2010-08-10
Now, if you are truly trying to change your username, as in change it all, including your home folder's name and location, it's not as easy. Doing that, you must do the following:

To Change User Login Name:

    sudo gedit /etc/passwd
    sudo gedit /etc/shadow
    sudo gedit /etc/group
    sudo gedit /etc/gshadow

    Change the following in all four and reboot. 

So if the current username is 'me', you must change all instances of 'me' with 'your username'. And be sure that if you do change your username like this, you have to also change the instances of '/home/me' to '/home/(your username)' as well as move all the contents to the appropriate directory.

---

### Post by baddnady23 on 2010-08-10
Wouldn't it also be possible to create a new user account, then using root privileges move all the the documents and files in the old user /home to the new new user /home then delete the old account?

---

### Post by inameiname on 2010-08-10
Maybe. I'm not enough of an expert to know for sure. It'd be grande if that was possible, as the method that I mentioned can be a tad difficult. I only found out it was even possible a few days back when I ran across the method above to change the username. 

Personally, I just redo the computer from a fresh install of Ubuntu with a desired username as it always seems more complicated and risky doing things such as changing a username. :P

---

### Post by khelben1979 on 2010-08-10
> **baddnady23 said:**
> Wouldn't it also be possible to create a new user account, then using root privileges move all the the documents and files in the old user /home to the new new user /home then delete the old account?

Yes, but it's important to change the owner of the files to the new user. Easily done with the [chown]("http://en.wikipedia.org/wiki/Chown") command.

---

