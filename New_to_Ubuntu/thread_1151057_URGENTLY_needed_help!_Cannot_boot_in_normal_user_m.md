---
title: "URGENTLY needed help! Cannot boot in normal user mode"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by steeny124 on 2009-05-06
I've had ALL sorts of problems since upgrading to 9.04.  
My sound is STILL not working. 

However, I was getting an error message when logging in under normal user mode:

> User's $HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by usuer and have 644 permissions.  User's $HOME directory must be owned by user and not writable by other users.

I was trying to fix that by running some chmod commands that I can't remember. Upon trying to reboot, I got the following error messages:

> Could not update ICEauthority file /home/steeny124/.ICEauthority


> There is a problem with the configuration server 
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

> Nautilus could not create the following required folders:
home/USER/Desktop
/home/USER/.nautilus
Before running Nautilus, please create these folders, or set permission such that Nautilus can create them. 
> 
There was an error starting up the screensaver:
Failed to change to 'home/steeny124' (Permission denied)
Screensaver functionality will not work in this session

I'm currently running as root.  I've looked for other posts that may be able to help, but nothing so far has.  I'm open to try other links that may cover this, but I have trouble because I need specific instructions 'cause I'm stupid, haha. 

PLEASE help!!

---

### Post by steeny124 on 2009-05-06
bump

---

### Post by spiderbatdad on 2009-05-06
check the permissions of /home/user they should be 755. Most likely need to run sudo chmod  755 /home/user
This is usually a last resort. See community documentation here:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by steeny124 on 2009-05-06
Ran the advice pointed in that link.  When I run in root I still get the error message about the .dmrc file. 

When I try to boot in normal user mode, it doesn't give me the long list of error messages it did before, it just sits at a blank background screen not doing anything.

Any advice?

---

### Post by steeny124 on 2009-05-06
bump

---

### Post by MontelEdwards on 2009-05-06
You are bumping way to soon.
Wait a day before bumping.
So you're able to log in as root?
Well if yes the best and easier way is to just open Nautilus and go to uh, /home and then find your home folder, right click and then click properties i think then go to permissions and set owner to your user name, and disable access to other usernames. Then click apply to all folders and files in that folder i think is what it is. Then you should be alllll right ;)

---

### Post by mlentink on 2009-05-06
Take a deep breath

Now, might reinstalling 8.04 or 8.10 be an option? Just to get things going again? 
So you might carefully examine what you need to preserve in an upgrade, and think of a good plan?

Please remember that none of us here gets paid to support you. Chances are, if you're in trouble, it's of your own doing. Nobody here urged you to install 9.04 without thought. 

So, step back, rethink, reformulate your problem. Help us help you. Help us to find causes rather than symptoms.

---

### Post by MontelEdwards on 2009-05-06
> **mlentink said:**
> Take a deep breath

Now, might reinstalling 8.04 or 8.10 be an option? Just to get things going again? 
So you might carefully examine what you need to preserve in an upgrade, and think of a good plan?

Please remember that none of us here gets paid to support you. Chances are, if you're in trouble, it's of your own doing. Nobody here urged you to install 9.04 without thought. 

So, step back, rethink, reformulate your problem. Help us help you. Help us to find causes rather than symptoms.
Finally...
Your correct

---

### Post by mlentink on 2009-05-06
> **m.deonte said:**
> Finally...
Your correct

What do I know?

btw. Cool to be testing Karmic when the first alpha is still 12 days out...
;-)

---

### Post by MontelEdwards on 2009-05-06
> **mlentink said:**
> What do I know?

btw. Cool to be testing Karmic when the first alpha is still 12 days out...
;-)
Yeah, it really has pissed me off, and it broke A LOT of packages.
But, it is worth it i guess.
Nothing is new at all that i can notice. I think just the toolchain was uploaded. But i cant wait alpha1. I it scheduled in my phones calender, well the whole schedule is in my phone,lol.


But the only way to get it now, it to just change your sources.list by replacing jaunty with karmic. SO when i get the alpha1 ill be happy.



Oh, gnome 

2.26 better be in there or im going to have a fit.
And i meant like that i felt like that, and didnt know how to put it in those words, ya know?

---

### Post by steeny124 on 2009-05-06
So, I totally didn't mean to come off as a whiny, needy little newbie. 

I guess I just freak out a little when my computer acts up. 

But I'm sure you're used to annoying little peons like me.  

Sorry about that. 

I may just do a clean install.  Do you know of any good tutorials?

---

### Post by Didius Falco on 2009-05-07
I can give you a quick re-install guide right here.

If you need to backup anything, do it from the Live CD before starting the install.

If you are happy with the layout of your partitions, just boot the Live CD and run install.

When it gets to the Partitioner, choose the **Manual (advanced)** option. Highlight the partition that contains your current installation by selecting it on the screen and click the **Edit Partition** box. Set it to **Use**, **EXT3** and set the type to** /**. Then click the small **Format** box on the screen so the partitioner will wipe out everything on the drive before installing the system anew.

If you have a separate **/Home** partition, repeat the above except, of course, setting the **type** to **Home**. You will want to format it, because otherwise you are going to run into problems like the one that caused you to reinstall.

No need to touch the swap partition - Ubuntu will recognize and use it.

That's pretty much it - let the installer do it's thing and you'll soon be logging into a fresh install.

Learn to use Sudo, and use it only when needed and wisely. Sudo is a powerful, but two-edged weapon.

Good luck!!

Regards,

Didius

---

