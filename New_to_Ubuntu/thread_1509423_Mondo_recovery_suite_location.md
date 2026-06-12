---
title: "Mondo recovery suite location?"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by Primus1 on 2010-06-14
I installed the Mondo recovery suite but can't see it listed anywhere under 'applications' or 'system'.
It shows a green tick that it's installed, Mindi too but I can't see them listed.

---

### Post by djackn on 2010-06-14
I noticed the same behavior with P4V. My workaround was to make a link to the app on the desktop, which works for me.

---

### Post by warfacegod on 2010-06-14
Try: Right click you Apps/Places/System menu> select Edit Menus> look through there to find it, put a check next to it.

If it isn't listed, then it's likely that the app doesn't have a GUI and/or you'll need to start it with the Terminal.

---

### Post by Primus1 on 2010-06-14
[LEFT]Thanks warfacegod, unfortunately it's not listed.


[/LEFT]

---

### Post by admiralspark on 2010-06-14
Open a terminal and type in "mondo" without the quotes. It either will open the program (if you're lucky) or it will search for commands like "mondo" and report back the results, which may give you a clue to which is the right command to use.

---

### Post by Primus1 on 2010-06-14
Pity:

No command 'mondo' found, did you mean:
 Command 'mongo' from package 'mongodb' (universe)
 Command 'mono' from package 'mono-runtime' (main)
mondo: command not found

---

### Post by warfacegod on 2010-06-14
It's probably something like:

```
mondo -t
```

---

### Post by Primus1 on 2010-06-14
Same result W  :confused:

---

### Post by warfacegod on 2010-06-14
Get the mondo-doc package from Synaptic. See if that has answer for you. if that isn't listed either, try:

```
mondo-doc
```

---

### Post by warfacegod on 2010-06-14
Another thought: Hit Alt+F2> type gksudo mondo> hit enter

---

### Post by Primus1 on 2010-06-14
> **warfacegod said:**
> Another thought: Hit Alt+F2> type gksudo mondo> hit enter

Oh, I thought that looked promising when it asked for my password, but no it just disappeared.

When I downloaded Mondo I also downloaded the doc and Mindi too, none of which are listed anywhere.

---

### Post by Primus1 on 2010-06-14
Did alt+F2 again, this time I ticked the little box "run in terminal", again it asked for pass, I put it in, and nothing.

---

### Post by warfacegod on 2010-06-14
Just found this: [http://www.mondorescue.org/docs/mondorescue-howto.html#QUICKSTART]("http://www.mondorescue.org/docs/mondorescue-howto.html#QUICKSTART")

I'm going to interpret the command as:

```
sudo su bash# mondoarchive
```

That's a guess.

---

### Post by Primus1 on 2010-06-14
Nope:
Unknown id: bash#

I've just thought, there were a confusing number of choices to download, perhaps I downloaded and installed the wrong one for my machine. It didn't complain at any point but ...

---

### Post by warfacegod on 2010-06-14
At this point I suggest going to the Mondo site for better information.

---

### Post by gandaran on 2010-06-14
run in terminal
```
sudo mondoarchive
```
and
```
sudo mondorestore
```
for the restore function

---

### Post by Primus1 on 2010-06-14
Thanks for the help, it's been interesting, I'll have another look at the problem tomorrow. ):P

---

### Post by Primus1 on 2010-06-14
> **gandaran said:**
> run in terminal
```
sudo mondoarchive
```and
```
sudo mondorestore
```for the restore function

Initializing...
Execution run ended; result=-1
Type 'less /var/log/mondoarchive.log' to see the output log

sudo mondorestore
Execution run ended; result=-1
Type 'less /var/log/mondorestore.log' to see the output log

---

### Post by gandaran on 2010-06-14
> **Primus1 said:**
> Initializing...
Execution run ended; result=-1
Type 'less /var/log/mondoarchive.log' to see the output log

sudo mondorestore
Execution run ended; result=-1
Type 'less /var/log/mondorestore.log' to see the output log
well, these are the right start commands, I installed mondo from synaptic package manager and they do work.

---

### Post by Primus1 on 2010-06-14
I looked at the log for the first one and got this:

[TH=4794] libmondo-tools.c->reset_bkpinfo#858: Hi
root is mounted at /dev/sdb

No, Schlomo, that doesn't mean /dev/sdb is the root partition. It's just a debugging message. Relax. It's part of am_I_in_disaster_recovery_mode().
[TH=4794] libmondo-devices.c->am_I_in_disaster_recovery_mode#147: Is this a ramdisk? result = 0
        [TH=4794] libmondo-tools.c->setup_tmpdir#842: Failed to create global tmp directory /4/mondo.tmp.We4KtI for Mondo.
        [TH=4794] libmondo-files.c->register_pid#815: Unregistering PID
        [TH=4794] libmondo-files.c->register_pid#817: Error unregistering PID
running: umount /mnt/cdrom > /mondo-run-prog-thing.tmp 2> /mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
umount: /mnt/cdrom: not found
--------------------------------end of output------------------------------
...ran with res=256

---

### Post by warfacegod on 2010-06-14
Turn your CD drive on?

---

### Post by Primus1 on 2010-06-15
Not sure I understand W, the Drive appears in 'Computer' and works ok.

---

### Post by warfacegod on 2010-06-15
> --------------------------------start of output-----------------------------
umount: /mnt/***cdrom: not found***
--------------------------------end of output------------------------------
...ran with res=256

Just grasping at straws.

---

### Post by Primus1 on 2010-06-15
I put a blank disk in cd (grasping 2) but no effect.

Did alt+F2 again and clicked on "show list of known applications" and mondo is not listed there.

---

### Post by warfacegod on 2010-06-15
I'd reinstall it.

Another option would be to use remastersys, forgoing Mondo entirely.

---

### Post by Primus1 on 2010-06-15
I will look at that, also clonezilla seems to have good results with members and has a 'beginner' option.
Don't really want to install mondo again, hope it hasn't done some kind of damage to my OS.
Thanks for the help warfacegod.

---

### Post by warfacegod on 2010-06-15
Sure thing.

It's unlikely that it has caused any damage to your system. If anything it may have exposed a preexisting condition but I thinks it's far more likely that Mondo just doesn't like your computer.

---

### Post by Primus1 on 2010-06-15
It's mutual :p 
cheers.

---

### Post by ubuntologist on 2010-06-26
Hi there,

Installing Mondo on a Lucid Server was a bit of an issue for me as well. I managed to get it working though and believe it will be the same for a Lucid Desktop.

Note: The Ubuntu repositories are outdated. Use the latest versions of Mondo and Mindi; i.e. 2.2.9.4-1 & 2.0.7.5-1 respectively.

1) Purge your existing installs:

[INDENT]*apt-get purge mondo*[/INDENT]

2) Add the following repositories to /etc/apt/sources.list: -

[INDENT][I]deb [ftp://ftp.project-builder.org/ubuntu](ftp://ftp.project-builder.org/ubuntu) 10.04 contrib
deb-src [ftp://ftp.project-builder.org/ubuntu](ftp://ftp.project-builder.org/ubuntu) 10.04 contrib[/I][/INDENT]

3) Install the latest versions:

[INDENT]*apt-get install mindi=2.0.7.5-1 mondo=2.2.9.4-1*[/INDENT]

4) LASTLY, place the following in /etc/apt/preferences (create the file if it doesn't already exist). If you don't, when you upgrade (apt-get upgrade), your latest versions will revert back to the older versions.

[INDENT][I]Package: mondo
Pin: 2.2.9.4-1
Pin-Priority: 1001

Package: mindi
Pin: 2.0.7.5-1
Pin-Priority: 1001[/I][/INDENT]

5) Run Mondo and backup: 

[INDENT]*mondoarchive*[/INDENT]

Hope that helps!

---

### Post by robinbillings on 2010-07-20
Thank you for this wonderful solution. I found, however, that the entry you provided for the /etc/apt/preferences file did not work, and my system kept wanting to "update" the mondo and mindi packages to the lucid repository.  I did a little searching and modified the preferences file to read as follows:

Package: mondo
Pin: version 2.2.9.4*
Pin-Priority: 1000

Package: mindi
Pin: version 2.0.7.5*
Pin-Priority: 1000

The asterisk at the end of the Pin line is a wildcard that gives permission to upgrade to any later version, but not earlier.  This configuration was adapted from the following documentation:

[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)

Under the section titled:
3.10 How to keep specific versions of packages installed (complex)

The Pin-Priority of 1000 will NEVER downgrade a package to a previous version.  1001 is utilized more to keep a version from being upgraded.  

Thanks again for the great pointer.

Robin

---

