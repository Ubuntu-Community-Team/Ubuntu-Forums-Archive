---
title: "Basic quick question from someone very stupid indeed (me)"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by Kernel Sanders on 2009-01-26
I have a Virtual Server with the CentOS 5 Linux operating system with GoDaddy (Oi, no laughing at the back! :D ) 

The problem is, that phpmyadmin displays the error about mcrypt not being installed. Will this cause slowness or other problems?

Just in case, I want to install it anyway just in case it does cause slowness or problems (although I might be wrong about that?)

The good news is that i've found the instructions to do this:

> 
   1. SSH into your VDS with your favorite SSH client or the SSH Java applet offered by GoDaddy.
   2. Login with your credentials.
   3. Su to the root user.
   4. Type "yum install mcrypt*". Say yes to the prompts.
   5. Type "yum install mhash*". Say yes to the prompts.
   6. Type "yum install php-mcrypt*". Say yes to the prompts.
   7. Type "yum install php-mhash*". Say yes to the prompts.
   8. Restart the server.


My basic stupid question is to do with step 3. How do I "su to the root user"? :o 

I'm asking here btw as this isn't just a server question, it also goes to my understanding of Linux overall, which will come in very useful when I install Ubuntu on my Notebook later on, and I will no doubt add to this thread later with more basic stupid questions :o 

Any help appreciated, and "LOL FAIL" is also an acceptable response ;)

---

### Post by sp0nge on 2009-01-26
The root user is setup by default when you install the OS. You can elevate to root like this:

```
me@home:~$ sudo su
```

---

