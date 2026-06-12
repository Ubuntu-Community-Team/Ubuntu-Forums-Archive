---
title: "Got everything configed as root. How to move settings to safe user account?"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by Razmear on 2009-02-19
The title just about sums it up.

When I first installed I was having issues with the video card, so I just logged in as root to make the setup easier. 
Unfortunately once I got the card replaced I stayed root and setup all the apps, mail, firewall, printer sharing, and appearance settings to my liking without realizing that it might be a big security issue being root all the time.

Can I just copy the contents of my /root folder (including hidden files) over to my /home/NEWUSER directory and expect everything to work, or will I be starting from scratch to recreate my profile? 

Also, how risky is it to be logged in as root as the standard user account? This is a home PC so I'm not worried about someone sitting in front of it doing something, just internet related security issues.  

Thanks,
eb

---

### Post by Razmear on 2009-02-19
Well it didn't work....
Got an error that the users home directory must be owned by the user right after the log in screen, then got a black screen and had to reboot. 

So I went back in as root, killed off the user account and deleted the home directory, but now when I log in as root I get the same error message, so I guess I screwed something up. Oh well, guess I'll just create a new user and start from scratch. Posting these results just so someone else doesn't try the same thing :)

eb

---

### Post by egalvan on 2009-02-19
> **Razmear said:**
> The title just about sums it up.

When I first installed I was having issues with the video card, so **I just logged in as root** to make the setup easier.


By default, Ubuntu has no "root" account enabled.
How did you "log in as root"?
If you just prefaced commands with sudo, you should have no problems.
If you truly enabled the root account, then you might.

> Unfortunately once I got the card replaced I stayed root and setup all the apps, mail, firewall, printer sharing, and appearance settings to my liking without realizing that it might be a big security issue being root all the time.


Being root all the time is not "A Good Idea"

> Can I just copy the contents of my /root folder (including hidden files) over to my /home/NEWUSER directory and expect everything to work, or will I be starting from scratch to recreate my profile? 

Others will have to answer this.

>  how risky is it to be logged in as root as the standard user account? 
This is a home PC so I'm not worried about someone sitting in front of it doing something, just internet related security issues.  
Thanks,
eb

Again, being root all the time is not a good idea.
Not just from a security view-point, but also from a usability view-point.
Root can do far more damage to your system than a regular, non-root-enabled, user can.
For instance, a mis-typed command can erase far more than you wanted.
Including the entire contents of your Linux installation.

---

### Post by Razmear on 2009-02-19
> How did you "log in as root"?
From another thread here I guess I'm not supposed to say how I enabled the GUI login for root, but that is what I did. I got tired of dealing with the package manager errors saying I didn't have permission so I enabled the root GUI account. 

I'm in a new user profile now and getting things fixed up. I had to CHOWN a copy of my thunderbird data and after that it copied into place and is working fine. I used to use Unix on the job about 10 years ago, so I know enough to be dangerous, but not enough to really know what I'm doing. Yes I know rm -r is bad :) 
Most of my problem is remembering everything I forgot on the admin side and also learning what all the gui app names are called. 

This thread was a great help:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
so I can sudo the package manager and file manager, makes life a lot easier. 

If anyone can detail the risks (other than user command errors) of being logged in as root, it would be appreciated. Might even make a good FAQ cuz I'm sure I'm not the only one who enabled root GUI access to get an install done, and if I didn't see a warning about running firefox as root in another thread I might still be root right now. 

Thanks,
eb

---

### Post by egalvan on 2009-02-19
> **Razmear said:**
> From another thread here I guess I'm not supposed to say how I enabled the GUI login for root, but that is what I did. I got tired of dealing with the **package manager errors saying I didn't have permission** so I enabled the root GUI account. 

I've been installing for over a year, and never received these types of errors. More than two dozen installs.
I use Synaptic, and occasionally apt-get.

I have a launcher that runs Nautilus as root,
and another to edit grub and fstab (I like to experiment)

> I'm in a new user profile now and getting things fixed up. I had to CHOWN a copy of my thunderbird data and after that it copied into place and is working fine. I used to use Unix on the job about 10 years ago, so **I know enough to be dangerous, but not enough to really know what I'm doing**. Yes I know rm -r is bad :) 
Most of my problem is remembering everything I forgot on the admin side and also learning what all the gui app names are called. 


One reason to use regular, non-root accounts.

> 
This thread was a great help:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
so I can sudo the package manager and file manager, makes life a lot easier. 

If anyone can detail the risks (other than user command errors) of being logged in as root, it would be appreciated. Might even make a good FAQ cuz I'm sure I'm not the only one who enabled root GUI access to get an install done, and if I didn't see a warning about running firefox as root in another thread I might still be root right now. 

Thanks,
eb

aysiu has an excellent post.

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

if you haven't read it, do so. Highly recommended.

Part way down is this link...

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

it may help answer some questions.

---

### Post by Razmear on 2009-02-19
My install issues were mainly due to an older Nvidia MX440 video card that is no longer supported by Ubuntu and dealing with their crap v96 driver package. My new video card just arrived Tuesday, so life is good now. 

I'll check out those threads now,
eb

---

### Post by egalvan on 2009-02-19
> **Razmear said:**
> My install issues were mainly due to an older Nvidia MX440 video card that is no longer supported by Ubuntu and dealing with their crap v96 driver package. 

Well, I've been installing Ubuntu Hardy on several older Dell Optiplex.

I installed nVidia MX400 32Mb cards on them, 'cause they were cheap.
($20 for 4, new, 6-month warranty, shipped; how could I refuse?)

No video issues, no update issues.

And they are running very well, thank you.
Quite sprightly.

Also, for fun, installed Puppy 4.2 on one,
it flies!

Customer wanted Vista, not Linux, so the original deal fell through
(I *refuse* to support Vista. And no, I'm not sorry)

I sold them to other students, so no big loss.
(the students could not afford what I originally wanted to charge, so I did have a slight loss.
But the world is a better place, because four deserving students now have working computers in their homes.
I'm happy)

Now I'm rambling.
Better end this.
ErnestG

---

