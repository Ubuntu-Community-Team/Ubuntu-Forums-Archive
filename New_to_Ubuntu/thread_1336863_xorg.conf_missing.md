---
title: "xorg.conf missing?"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by csq on 2009-11-24
Hi,

I am pretty new to Linux. I just installed Ubuntu 9.10 but I can' find xorg.conf in /etc/X11. Am I missing something?

Thanks

---

### Post by amingv on 2009-11-24
There is no xorg.conf by default in 9.10, giving space to autodetection.
Some drivers may generate a xorg.conf later on, though.

What would you like to do with it? Are you having any problems?

---

### Post by csq on 2009-11-24
I am using Intel 4500 graphics card which has many known problems. I want to take a look at the xorg.conf to see the configuration and other options.

---

### Post by Sealbhach on 2009-11-25
> **csq said:**
> I am using Intel 4500 graphics card which has many known problems. I want to take a look at the xorg.conf to see the configuration and other options.

There is no xorg.conf in Ubuntu 9.10, see here for reasons why: [http://ubuntuforums.org/showthread.php?t=1325212](http://ubuntuforums.org/showthread.php?t=1325212)

However, you can generate one if you need to, by dropping to the shell

Drop to the terminal by doing **ctrl+alt+F1**

Login.

Type 

**sudo service gdm stop**

Then type:

**sudo Xorg -configure**

then to restart X

**sudo service gdm start**

This will generate an xorg.conf. 

.

---

### Post by csq on 2009-11-25
[I]Hi, Sealbhach

Thank you. it works.
[/I]

---

### Post by seijling on 2009-12-17
Fantastic post!

However, how does one assert that it should use the file.  Does its presence in /etc/X11 ensure this?

The file is there and the issue remains.

---

### Post by mikewhatever on 2009-12-17
> **seijling said:**
> Fantastic post!

However, how does one assert that it should use the file.  Does its presence in /etc/X11 ensure this?

The file is there and the issue remains.

What issue? Are you the original poster under a different username?

---

### Post by 3rdalbum on 2009-12-17
Xorg uses xorg.conf if present.

---

### Post by ligaa9mm on 2010-11-04
Thank you Sealbhach!!! I followed your commands, and it worked.

It now says...
> (++) Using config file: "/home/__myusername__/xorg.conf.new"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"

Now I can get around my broken touchpad and finally left click again!

---

### Post by griffineyes on 2012-08-29
> **Sealbhach said:**
> There is no xorg.conf in Ubuntu 9.10, see here for reasons why: [http://ubuntuforums.org/showthread.php?t=1325212](http://ubuntuforums.org/showthread.php?t=1325212)

However, you can generate one if you need to, by dropping to the shell

Drop to the terminal by doing **ctrl+alt+F1**

Login.

Type 

**sudo service gdm stop**

Then type:

**sudo Xorg -configure**

then to restart X

**sudo service gdm start**

This will generate an xorg.conf. 

.
Hi Sealbhach, 

I followed the steps you suggested but I received an error:

"Number of created screens does not match number of detected devices. Configuration failed."

What does this mean? How can I fix it?

Thank you

---

### Post by sandyd on 2012-08-29
***Necromancing - thread closed.***

From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

