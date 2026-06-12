---
title: "My Add/Remove Program is Missing!"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by iocustheoda on 2009-03-07
Hello there,

   I am still new about these things. My recent report was about "Open Source OS". Since its free, I decided to try one myself. Both me and my little sister were excited when we finished install it. However, recently , when I went a way for a while and came back, a number of things occur. The accounts on User and Groups are unable to be unlocked, the add/remove program option is gone,if I try to install anything-I can't now, and I can't remove the trash in the Trash, even when using sudo.

It turns out my account can't do those things because I'm not allow to administer. I only had one account here! How come it wasn't the administrator!:mad::confused::(](*,):cry::-#


I'm using Ubuntu 8.04 LTS

---

### Post by iamkrazee on 2009-03-07
This is a security feature of linux family. Anything that causes system-change is protected. And to perform such tasks, you must run the appropriate command with sudo/gksu/kdesudo prefix. 

Please tell us what exactly you are trying to do, as in add/remove what programs etc. We will help you out.

---

### Post by bailbath on 2009-03-07
> **iamkrazee said:**
> This is a security feature of linux family. Anything that causes system-change is protected. And to perform such tasks, you must run the appropriate command with sudo/gksu/kdesudo prefix. 

He said he used sudo.

---

### Post by bailbath on 2009-03-07
> **iocustheoda said:**
> Hello there,

   I am still new about these things. My recent report was about "Open Source OS". Since its free, I decided to try one myself. Both me and my little sister were excited when we finished install it. However, recently , when I went a way for a while and came back, a number of things occur. The accounts on User and Groups are unable to be unlocked, the add/remove program option is gone,if I try to install anything-I can't now, and I can't remove the trash in the Trash, even when using sudo.

It turns out my account can't do those things because I'm not allow to administer. I only had one account here! How come it wasn't the administrator!:mad::confused::(](*,):cry::-#


I'm using Ubuntu 8.04 LTS

You should be asked your password when you try to change anything administration on the computer. Until you put that in you can't do nothing. Go to the menu system - admin - user and groups can you see what users are listed?
Ian

---

### Post by iamkrazee on 2009-03-07
> **bailbath said:**
> He said he used sudo.

If he´s a first timer, we´re not sure how exactly he used his sudo. I´ve seen people type sudo<enter> and then behaving like root :P.

---

### Post by bailbath on 2009-03-07
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

If sudo is broken follow this guide
Ian

---

### Post by iocustheoda on 2009-03-07
To iamkrazee:

  That's it: Nothing. I came back, I boot the computer on, I check the Applications tab, the Add/Remove button is missing.

The only time I used sudo is:

sudo apt-get install imagemagick. 

After I enter password, it says:
iocustheoda is not in the sudoers file.  This incident will be reported.

I know I used the right password, or I won't be able to write this reply.





To bailbath/Ian:

I found put there are 3 accounts.  

1. Iocus Theoda login name: iocustheoda Home dir: /home/iocustheoda

2. root login name: root home dir.: /root

3. Iona login name:  iona home dir.: /root


no. 2 and 3 are unable to unlock. I noticed the home directory are the same.

no. 1 is the one I'm using, I noticed at User Privileges the "Administer the System" is unchecked and unable to get checked.



To all:


My sister admitted she created her own account there, and make herself as Administer. but she swore she didn't touch any other accounts settings. I've enough of scolding her, I'm more worried on getting this fix. There' a lot of files in here, and it's more work to reinstall the codecs and plugins if I had to reinstall Ubuntu.


By the way, I'm a she. A healthy, suburb, new to computer 17 years old she. I don't mind the misunderstanding, just clearing it out.

---

### Post by Xiong Chiamiov on 2009-03-07
In a terminal, open gedit as root to edit the sudoers file:
```

gksudo gedit /etc/sudoers

```
and add this line:
```

iocustheoda ALL=(ALL) ALL

```

> **iocustheoda said:**
> 
By the way, I'm a she. A healthy, suburb, new to computer 17 years old she. I don't mind the misunderstanding, just clearing it out.
We all know that females don't exist on the internet, especially in Linux forums.

---

### Post by iocustheoda on 2009-03-07
> **Xiong Chiamiov said:**
> In a terminal, open gedit as root to edit the sudoers file:
```

gksudo gedit /etc/sudoers

```
and add this line:
```

iocustheoda ALL=(ALL) ALL

```

[COLOR="Red"]Failed to run gedit 'etc/sudoers' as user root.

The underlying authorization machanism (sudo) does not allow you to run this program. Contact the system administrator.[/COLOR]


> **Xiong Chiamiov said:**
> We all know that females don't exist on the internet, especially in Linux forums.

Surprise. It's the 21st Century. Don't be **stereotypical**. Didn't I say I'm trying? That's because we have are having Information and Communication Technology this year, that is why I'm learning about this. And who says Linux can't be used by girls?

If you don't want to believe me, doesn't matter, as long as my problem is solved. Heck, I only remember being taught not to lie, not to preach.

---

### Post by iamkrazee on 2009-03-07
Sorry for the he/she mix up. I´m not used to talking to a ¨she¨ in a forum.

Anyway, you need to do what Xiong said.. just in a different manner.

When you boot your PC, you see a choice of kernels. You pick the recovery kernel. And from there on, you´ll need to pick the option which drops you to a shell.

There you will need to do :

```
nano /etc/sudoers
```

```
iocustheoda ALL=(ALL) ALL
```


The difference here is that you will be forcibly dropped to a root shell so as to enable you performing super-user tasks.

---

### Post by iocustheoda on 2009-03-07
by booting, meaning the  booting with CD, right?

---

### Post by t0p on 2009-03-07
No one seems to have pointed this out: your account is not a sudoer.  Maybe this happened when your sis created her account.  Anyway, you won't be able to do any of the steps mentioned above from your account.  You need to use your sister's account to do anything involving admin privileges.  So log in as your sister (ie use her account) and make the changes from there.

---

### Post by iamkrazee on 2009-03-07
No.. hard disk. I´m assuming that you have it installed on your harddisk. Have you not?

---

### Post by iamkrazee on 2009-03-07
> **t0p said:**
> No one seems to have pointed this out: your account is not a sudoer.  Maybe this happened when your sis created her account.  Anyway, you won't be able to do any of the steps mentioned above from your account.  You need to use your sister's account to do anything involving admin privileges.  So log in as your sister (ie use her account) and make the changes from there.

She said she swore and everything, but come to think of it.. you don´t intentionally have to mess up things. She swore alright but probably did something inadvertently that took away your rights. Anyway... you can try what xiong said from her account OR do what I said.

---

### Post by iocustheoda on 2009-03-07
To iamkrazee:

   Yes, I install it in hard disk. When it boot, it went straight to the login screen through the splash screen. Where should I find the recovery kernel then?

to T0ps:

 I tried putting username iona and her password. 
> 
User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME director must be owned by user and not writable by other users.

Then;
> 
Your session only last less than 10 second. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskpace. Try logging in with one of the failsafe session to see if you can fix the problem.


It can't be installation problem,as I used this almost three days this week, excluding the two day before when I went camping. It was okay back then.

If I had to go to the failsafe session, what should I do?

---

### Post by iamkrazee on 2009-03-07
failsafe terminal wont help you. You just turn off your PC completely. Then turn it back on and keep pressing up/down keys rapidly until you see a menu. You must see something called GRUB menu. Which would have different lines like Ubuntu 8.10 2.6.27-13 etc. There should ideally be 3 lines, select the 2nd one from that.

---

### Post by iocustheoda on 2009-03-07
I chose recovery mode kernel. I've change in the sudoers  the part as iocustheoda ALL=(ALL) ALL

why there are still no changes? Still no add/remove , still can't unlock other accounts, still can't delete trash as permission is still denied.


I'm getting confused...

---

### Post by iocustheoda on 2009-03-07
That's it. I'm backing up my files, and reinstall. I'll have to reinstall those applications, again....


Thanks guys....

---

### Post by bailbath on 2009-03-07
Good idea. You don't know what else has been done without your permission and at least you will be back in charge!
By the way sorry I assumed you were male :oops:
Ian

---

### Post by darth_indy on 2009-03-07
Good luck, iocustheoda. I've had to dea/ with a similar problem before, also based on someone going places they shouldn't and messing with the wrong settings. It would be possible to fix all those, but time consuming.

Also,

> **Xiong Chiamiov said:**
> 
We all know that females don't exist on the internet, especially in Linux forums.

That was a joke. Poorly worded and not clear, but still a joke. *shrugs* People still like to play off that misconception, and the jokes about it are getting as old as the stereotype itself.

After all, if that were true, I wouldn't be here :) Greetings to a fellow female Ubuntu user, and I hope you get your problems sorted out!

---

### Post by iamkrazee on 2009-03-13
> **iocustheoda said:**
> That's it. I'm backing up my files, and reinstall. I'll have to reinstall those applications, again....


Thanks guys....

Report back if the issue persists. although I guess it´s safe to assume that no such thing has happened since there has been no activity on this thread.

---

### Post by donkE on 2009-03-26
Hello All, 

I've been using Ubuntu for the past year, and have just now run into this problem. I don't consciously remember changing my account settings, but I did change a "guest" account so as to be unable to administer the computer. It seems though that I may have changed my settings as well.

I booted into recovery mode, went into the root shell, and executed:

nano /etc/sudoers

The first time I entered username ALL=(ALL) ALL under

# User privilege specification
root	  ALL=(ALL) ALL
username  All=(All) ALL

Saved and exited, Normal Boot, and still cannot Unlock my account in Users and Groups. Also unable to perform gksudo gedit /etc/sudoers (same error as other person).

Restarted, went back to root shell and added username ALL=(ALL) ALL under

# Members of the admin group may gain root privileges
%admin   ALL=(ALL) ALL
username ALL=(ALL) ALL

Continued Boot; am still unable to Unlock account in Users and Groups, however I can now execute and open the above gksudo gedit command. In full my sudoers file looks like this:

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL
donk-e  All=(All) ALL
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
donk-e ALL=(ALL) ALL

----------------------------------

Your ideas and help will be greatly appreciated!

---

### Post by iamkrazee on 2009-07-17
Your problem isn't quite clear, although it's too late to ask, still. 

Please try out commands like chmod, chown, usermod etc. Make use of man pages too. Mostly you'll be able to fix such problems just with that.

---

