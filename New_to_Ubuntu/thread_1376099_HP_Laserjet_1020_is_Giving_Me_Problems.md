---
title: "HP Laserjet 1020 is Giving Me Problems"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by SPazzo on 2010-01-08
So I installed Ubuntu 9.10 on my parents computer.  It used to have XP.  They have a HP Lasterjet 1020 printer.  I have used this printer on my laptop which has Jaunty on it and it worked fine.  It just asked to install a driver, I installed it, and it worked fine.

Now, I did the same exact thing I did with my parents desktop as I did with my laptop.  The printer wouldn't print.  I did some Googling and found this page:  [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)  I followed the instructions and it *STILL* wouldn't work.  By this time I'm a little annoyed.  So I tried [THIS PAGE]("http://blog.dipinkrishna.info/2009/07/install-hp-printers-in-linux-ubuntu.html").  It worked fine.  Problem solved right?

Nope.  About four or five hours (and one reboot) later it stopped printing.  I tried typing this into terminal:
```
firefox http://localhost:631
```
and installing the printer from there.  Still doesn't work.

I'm guessing my problem might be that I tried and installed too many things to try to get it to work.  Does anyone have any advice on what the heck to do?  Also, if I have the printer plugged into the computer (via usb) while the computer is booting up, it freezes and won't boot.  Neither the mouse nor the keyboard respond and I have to do a hard reset, unplug the printer, and boot up again.

Please help. :(

---

### Post by Methuselah on 2010-01-08
AFAIK, the most you should have to do is **sudo apt-get install hplip**.
I honestly don't know about the other stuff and I can't give firsthand advice having an Epson myself.

---

### Post by scrooge_74 on 2010-01-08
is not commong for it to give problems, check the config file in /etc/cups sometimes it is not broadcasting the printer to the network

---

### Post by SPazzo on 2010-01-08
> **scrooge_74 said:**
> is not commong for it to give problems, check the config file in /etc/cups sometimes it is not broadcasting the printer to the network

It's not a wireless printer though.

---

### Post by Methuselah on 2010-01-08
Is the printer present in CUPS but won't print or is it not being recognized at all?

---

### Post by SPazzo on 2010-01-08
> **Methuselah said:**
> Is the printer present in CUPS but won't print or is it not being recognized at all?

It's recognized.  It just won't print.

---

### Post by Methuselah on 2010-01-08
Are you using an unfamiliar user account?
Verify that it is not something as simple as a permissions issue.
Check the privileges assigned to the user you're trying to print with.

---

### Post by SPazzo on 2010-01-08
> **Methuselah said:**
> Are you using an unfamiliar user account?
Verify that it is not something as simple as a permissions issue.
Check the privileges assigned to the user you're trying to print with.

This computer has three accounts on it.  (Not counting root.)  They all have the same permissions, which is everything.  Including Configuring Printers.

---

### Post by Methuselah on 2010-01-08
What is the output of **ls -l /dev/lp0**?
(ell)

---

### Post by SPazzo on 2010-01-08
> **Methuselah said:**
> What is the output of **ls -l /dev/lp0**?
(ell)

It's ```
crw-rw---- 1 root lp 6, 0 2010-01-08 15:29 /dev/lp0
```

---

### Post by Methuselah on 2010-01-08
> **SPazzo said:**
> It's ```
crw-rw---- 1 root lp 6, 0 2010-01-08 15:29 /dev/lp0
```

Thanks.
Are your users members of lp group?

---

### Post by SPazzo on 2010-01-08
> **Methuselah said:**
> Thanks.
Are your users members of lp group?

No.  I just looked into the Manage Groups window and it seems that they are all part of the Adm group.  I honestly haven't done any sort of work with the *Groups* type of stuff.

---

### Post by Methuselah on 2010-01-08
> **SPazzo said:**
> No.  I just looked into the Manage Groups window and it seems that they are all part of the Adm group.  I honestly haven't done any sort of work with the *Groups* type of stuff.

I'm not 100% sure if it is an issue in Ubuntu but in the distro I'm currently using users that want to print have to be a member of lp as only lp (and root) have rw access to the printer's device node.
The permissions seem to be the same in Ubuntu but I do not remember lp group membership being necessary.
Maybe there is some other mechanism at play.

What does the terminal spit out when you're logged in as one of the users in question and enter **groups**?
Afterwards, as an experiment, try **gksu gedit**, type something and attempt to print it.

The most I can suggest after that is that you poke around in /var/log/cups to see if there is any error that could shed light on what is happening.

---

### Post by SPazzo on 2010-01-08
It says ```
peter adm dialout fax cdrom tape audio dip video plugdev fuse lpadmin netdev admin sambashare
```

Peter is the name of the user I'm on.

---

### Post by SPazzo on 2010-01-08
> **Methuselah said:**
> I'm not 100% sure if it is an issue in Ubuntu but in the distro 
Afterwards, as an experiment, try **gksu gedit**, type something and attempt to print it.


Wow!  It worked!  What does this **gksu gedit **do?  I mean I know it opens up gedit.  But what does gksu mean?  I assume it's some sort of open with root or something.

---

### Post by SPazzo on 2010-01-08
Ah ha!  I took a chance and added all the users on the computer to the lp group.  Now it prints fine!

I hope what I did was okay...

---

### Post by Methuselah on 2010-01-08
> **SPazzo said:**
> Wow!  It worked!  What does this **gksu gedit **do?  I mean I know it opens up gedit.  But what does gksu mean?  I assume it's some sort of open with root or something.

Well, you just confirmed that it is definitely a permissions issue.
**gksu** is just like **sudo** except that it is preferred for graphical applications that open in their own window.
[Generally graphical applications shouldn't be run as root but that is another matter!]
So basically, you ran gedit as root and it printed.

What I would do now is add everyone who you want to print to lp

eg.
```

gpasswd -a peter lp

```

Anyway who is a member of lp shoudl also be able to print then.
So open gedit normally as peter and try to print after running the above.

---

### Post by Methuselah on 2010-01-08
> **SPazzo said:**
> Ah ha!  I took a chance and added all the users on the computer to the lp group.  Now it prints fine!

I hope what I did was okay...

I see you did the lp group add before I posted.
I just thought that if the printer was in Cups it should print.
So it seemed likely to be a permissions problem.
Not sure why the default config is as it is but glad you got it to work.

Please mark the thread solved using thread tools.

---

### Post by SPazzo on 2010-01-08
Well, I seem to have got it working.  Thanks so much Methuselah!

---

### Post by scrooge_74 on 2010-01-08
> **SPazzo said:**
> It's not a wireless printer though.

what wireless had to do with setting the cups server right? 

/etc/cups is where the config files of the print server are stored, you could have a couple of printers in your network or attach to the server in question and they will all show up there.

---

