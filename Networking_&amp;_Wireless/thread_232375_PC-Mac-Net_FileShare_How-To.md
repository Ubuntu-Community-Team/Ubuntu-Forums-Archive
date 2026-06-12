---
title: "PC-Mac-Net FileShare How-To"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by amh221 on 2006-08-08
:confused: :( 
I'm trying to use PC-Mac-Net FileShare to share files between my PC that's running Ubuntu and my Macintosh that's running Mac OS X v. 10.4.7. Every time 
I try to install PC-Mac-Net FileShare, I get an error that says:

../Common/plugin.cpp: 6490
Failure Condition: 0
The application cannot continue because a needed file cannot be
installed. libssl.so.0.9.7: cannot open shared object file: No such file
or directory

PC-Mac-Net FileShare says that it requires Ubuntu users to run the command line:

sudo apt-get install libstdc++5

in order to install the correct library. I ran the command line, and I got back that I already had the most recent version (libstdc++5).

I even got that error after I ran the command line, so I know that libstdc++5 can't have anything to do with the error I keep receiving.

Does anyone have any ideas of what might be causing this problem? Does anyone have any ideas of how to solve this problem?

---

### Post by ohgod on 2006-08-08
This is just a guess (I've never used PC-Mac-NEt FileShare), but it seems like you're missing libssl-dev and/or libssl.  

Might want to give this a shot:  sudo apt-get install libssl libssl-dev

---

### Post by amh221 on 2006-08-08
That didn't work. I typed sudo apt-get install libssl libssl-dev, but I got this back:

Package libssl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package libssl has no installation candidate

---

### Post by ohgod on 2006-08-09
Ooops, I should've tried this before recommending it...

I got the same error running that command (libssl not found), but libssl-dev is a valid package name.  Try 'sudo apt-get libssl-dev'.  Hope that helps.

---

### Post by amh221 on 2006-08-09
I tried 'sudo apt-get libssl-dev', but I got this in return:

E: Invalid operation libssl-dev

---

### Post by ohgod on 2006-08-10
oh geez, that's my fault.  forgot part of the command.  sorry.

sudo apt-get install libssl-dev

---

### Post by amh221 on 2006-08-10
:confused: :mad:
Okay, the installation of libssl worked, but pc-mac-net fileshare is still giving me the same error.

../Common/plugin.cpp: 6490
Failure Condition: 0
The application cannot continue because a needed file cannot be
installed. libssl.so.0.9.7: cannot open shared object file: No such file
or directory

I am now completely baffled and confused.

---

