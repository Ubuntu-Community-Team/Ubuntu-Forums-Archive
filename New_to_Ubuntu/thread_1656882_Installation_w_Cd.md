---
title: "Installation w/ Cd"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by gibber on 2010-12-31
Hey everyone,
Nice forum here.  
I'm a little bit of a noob, so bear with me.  

I am having problems installing Ubuntu.  

I have obtained a CD and have the dual-boot option (in fact, I'm using Linux right now).  However, I'd really like to just have Ubuntu (ie. get rid of windows entirely).  I have no idea how to do this.  

I was going to watch a YouTube video to help me out, but I don't have flash.  I am having troubles with the installation of Flash, but I guess I should just try to fix the first problem above first.  

Thanks for the help,

---

### Post by Autodave on 2010-12-31
> **gibber said:**
> Hey everyone,
Nice forum here.  
I'm a little bit of a noob, so bear with me.  

I am having problems installing Ubuntu.  

I have obtained a CD and have the dual-boot option (in fact, I'm using Linux right now).  However, I'd really like to just have Ubuntu (ie. get rid of windows entirely).  I have no idea how to do this.  

I was going to watch a YouTube video to help me out, but I don't have flash.  I am having troubles with the installation of Flash, but I guess I should just try to fix the first problem above first.  

Thanks for the help,

Well, let's get flash working.  In a terminal window type: sudo apt-get install ubuntu-restricted-extras

That should get your flash working.  

If you really do want to get rid on Windose, if you haven't installed a lot of extras yet, perhaps the easiest way for you would be to put the ubuntu boot disk back in and then choose to use "entire disc".

---

### Post by azertyh on 2010-12-31
hello,
use your live cd to format the windows partition. be cautious to select the partition.
after that, start ubuntu and in a terminal, type
```
sudo update-grub
```

---

### Post by sandyd on 2010-12-31
nvm

---

### Post by gibber on 2010-12-31
> **Autodave said:**
> Well, let's get flash working.  In a terminal window type: sudo apt-get install ubuntu-restricted-extras

That should get your flash working.  

If you really do want to get rid on Windose, if you haven't installed a lot of extras yet, perhaps the easiest way for you would be to put the ubuntu boot disk back in and then choose to use "entire disc".

I tried, and I got a weird confirmation/disclaimer message.  I wanted to press "ok" at the bottom, but it wasn't a real button.  So I just exited the terminal and tried again.  When I tried again, I got this message 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

