---
title: "username and password"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by aebaa on 2009-01-09
Hi all
This might sound daft to all you computer people but, I have just downloaded ubunta and installed it on my pc but it is asking for a username and password before I can get to the desktop? How do I get a username and password I have looked on these threads but have found nothing about this.

Thanks

---

### Post by Zack McCool on 2009-01-09
> **aebaa said:**
> Hi all
This might sound daft to all you computer people but, I have just downloaded ubunta and installed it on my pc but it is asking for a username and password before I can get to the desktop? How do I get a username and password I have looked on these threads but have found nothing about this.

Thanks

When you installed it, it asked you to create a user.  It asked for a username, and a password.  You entered this information as a part of the install.  Now, it will want that information at every bootup.

---

### Post by kestrel1 on 2009-01-09
This should have been set up during the installation.

---

### Post by aebaa on 2009-01-09
Hi
I have just done what I did when I downloaded the 699 mb and it has not asked for me to input a username and password so I don’t know what it does.

Thanks for very quick replies 
p.s. I’m not too hot with pc’s so I might of missed something

---

### Post by kestrel1 on 2009-01-09
You shouldn't be able to carry on installing unless you put a username & password in.
You may need to re-install & be a bit more careful during the install.
This is not a criticism, just a pointer.

---

### Post by aebaa on 2009-01-09
Ok i will try to install again.

thank tou for your help

---

### Post by Zack McCool on 2009-01-09
I don't have the time now to do a VM install to get you a screenshot of the screen that you enter the information in, but the way it works (from memory) is this:  You use the LiveCD to install the OS.  At the end, it reboots, and on this first boot (from the Hard Drive), a screen will come up to ask you for your Full Name, a user name, and a password.  Once you enter this information, and perhaps a couple of other prompts, you have a fully operational Ubuntu system.  And from that point on, it will ask you for the username and password you entered during firstboot.

---

### Post by Elfy on 2009-01-09
You should be able to find out the username from recovery mode, reboot - pick recovery - when you get to the small recovery menu choose root prompt

```
grep 1000 /etc/passwd
```

should give you the username -eg

[noparse]kevin:x:1000:1000:kevin,,,:/home/kevin:/bin/bash[/noparse]

Then do
```
passwd *yourname*
```

exit and resume, then you can use your username and new password

---

### Post by aebaa on 2009-01-09
I have only installed ubunta without uninstalling windows just to see what it is like so I have them both on my hard drive do you thing I should format my hard drive and then install ubunta by its self to see if I get the screen you are talking about.
Thanks

---

### Post by Elfy on 2009-01-09
try to find username and reset password before you reinstall

---

### Post by aebaa on 2009-01-09
ok will do that now 

thanks

---

### Post by nothingspecial on 2009-01-09
I may be off the mark here but I`m sure I`ve seen this before.

Are you sure you`ve installed ubuntu or are you just running the live cd.

Like I said I`m sure I`ve heard of live cds that do this.

I think the default user name and password are ubuntu

---

### Post by jmszr on 2009-01-09
aebaa,
        I suggest you go here:[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)  and on the left hand side of the page click on "Installing A Dual Boot Without Partitioning" -this should explain installing Wubi to you. It is also a very good beginner's resource. Because you're installing Ubuntu "just to see what it is like", wiping your hard drive at this point would probably not be a good idea.

---

### Post by aebaa on 2009-01-09
Hi all

I have just installed it again and I’m an idiot it appears that I have hit the wrong key on my username with which I use all the time, old age makes you do funny things as I remember the screen that I put the username and password in now (I only did it yesterday ay) so thank you all very much and I’m sorry to have wasted your time over this.

Thanks all again and sorry

---

### Post by kestrel1 on 2009-01-09
It is never a waste of time if we are helping a fellow ubuntu'n
But you are welcome anyway.

---

