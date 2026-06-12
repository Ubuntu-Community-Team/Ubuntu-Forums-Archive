---
title: "apt-get broken"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by JonoEPD on 2011-03-24
Hey all, 

-I'm New to Ubuntu [been using for about 6 months]
-reinstalled via Wubi a few weeks ago

I get the following when I attempt to install something via apt-get:
jono@ubuntu:/$ sudo apt-get install lynx
<usual stuff>
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)

----------------------------------------------------

Also, it appears that dpkg is not installed (though it's already the newest version?) and I need dpkg to install dpkg. 

jono@ubuntu:/$ dpkg
The program 'dpkg' is currently not installed.  You can install it by typing:
sudo apt-get install dpkg
jono@ubuntu:/$ sudo apt-get install dpkg
<stuff>
dpkg is already the newest version.
<stuff>
Do you want to continue [Y/n]? Y
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)

I've been trying to fix this for a few days and have not found a solution. I hit the same problem last time I installed Ubuntu as well; I ended up reinstalling after a similarly futile attempt.  

Help! :)

EDIT: If it matters, I'm pretty sure that this happens after I install adobe

Jon

---

### Post by sikander3786 on 2011-03-24
Welcome to the forums :-)

Please post the complete outputs of these commands.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

While posting, click the # icon in post menu and paste your text in between the generated [code] tags for readability purposes.

---

### Post by JonoEPD on 2011-03-24
```
jono@ubuntu:~$ sudo apt-get install -f
[sudo] password for jono: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)

```

```

jono@ubuntu:~$ sudo dpkg --configure -a
sudo: dpkg: command not found
```

---

### Post by sikander3786 on 2011-03-24
Thanks for the outputs. So what is the output of this one?

```
ls -l /usr/bin/dpkg
```

---

### Post by JonoEPD on 2011-03-24
```

jono@ubuntu:~$ ls -l /usr/bin/dpkg
ls: cannot access /usr/bin/dpkg: No such file or directory

```

---

### Post by sikander3786 on 2011-03-24
Ok. Please follow post # 2 or post # 6 here.

[http://ubuntuforums.org/showthread.php?t=197819](http://ubuntuforums.org/showthread.php?t=197819)

If you follow post # 2, instead of extracting the package, install the package using package manager by double clicking the package.

---

### Post by JonoEPD on 2011-03-24
Using the ubuntu software center: 

Using i386 version: [I'm pretty sure I am i386, since I used 32-bit recommended Wubi install][INDENT]Wrong architecture 'i386' 
[/INDENT]Using amd64:[INDENT]Breaks existing package 'grub-common' dependency dpkg (<= 1.14.25) 
[/INDENT]I then tried extracting both manually and cp to /usr/bin/dpkg, which also didn't work.

---

### Post by sikander3786 on 2011-03-24
We need to see the output of this command then.

```
uname -a
```

And when trying to cp the extracted dpkg files, did you use 'sudo'? You need to...

Or execute nautilus with root privileges and then copy the files to respective directories.

```
gksudo nautilus
```

---

### Post by JonoEPD on 2011-03-24
```
jono@ubuntu:~$ uname -a
Linux ubuntu 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:46 UTC 2011 x86_64 GNU/Linux

```

This is what I get when I try to manually install:

```

jono@ubuntu:~/Downloads$ mv dpkg_1.15.8.4ubuntu3.1_i386 dpkg
jono@ubuntu:~/Downloads$ sudo mv dpkg /usr/bin
[sudo] password for jono: 
jono@ubuntu:~/Downloads$ sudo apt-get install skype
<stuff>
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)
jono@ubuntu:~/Downloads$ sudo rm -r /usr/bin/dpkg
jono@ubuntu:~/Downloads$ ls
chessgames.pgn  dpkg_1.15.8.4ubuntu3.1_amd64  jin-2.14.1
jono@ubuntu:~/Downloads$ mv dpkg_1.15.8.4ubuntu3.1_amd64 dpkg
jono@ubuntu:~/Downloads$ sudo mv dpkg /usr/bin
jono@ubuntu:~/Downloads$ sudo apt-get install skype
<stuff>
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)
```

```

gksudo nautilus
Initializing nautilus-gdu extension

** (nautilus:26402): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '26402'

(nautilus:26402): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
```

---

### Post by JonoEPD on 2011-03-24
Update: I copied /usr/bin/dpkg_/usr/bin/dpkg to /usr/bin. I ran sudo apt-get skype again, which froze the terminal, so I quit and then typed sudo rm -r /var/lib/dpkg to kill the lock. Now I get this:

```
jono@ubuntu:~$ sudo apt-get install skype
E: Could not open lock file /var/lib/dpkg/lock - open (20: Not a directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

Looking around it seems that that was a pretty fatal error, so I'm gonna reinstall. The original problem, however, was solved. Thanks a lot for your time sikander :)

Jon

---

### Post by sikander3786 on 2011-03-25
You were running 64-bit :-)

> Linux ubuntu 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:46 UTC 2011 [COLOR="Red"]x86_64[/COLOR] GNU/Linux

And what you did wrong while removing the dpkg lock was using the '-r' recursive switch. It might have remove the directories as well. The correct command should be,

```
sudo rm /var/lib/dpkg/lock
```

Or a simple reboot solves the lock problems most of the time.

Anyhow, good luck for the re-install.

---

