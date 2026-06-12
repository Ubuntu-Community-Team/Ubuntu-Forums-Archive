---
title: "Linux-Windows Networking"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by essex on 2007-01-16
I am new to Ubuntu Linux, I am able to see my Windows network on the Linux box and I have samba setup with a folder shared that I am trying to test with.  Every thing seems to work ok on the Linux side but when I try access my Linux share from the Windows machine it asks for a userneme and password. The only user and password that I have assigned on the Linux box is what I try, this does not work.  Was there something that I missed when I set the share on Linux.  If so where do I find this setting or config file.

Thanks

---

### Post by dmizer on 2007-01-16
in /etc/samba/smb.conf, change:
```
security = user
```
to 
```
security = share
```

also, under your share listing in smb.conf, you'll need to add this option:
```
guest ok = yes
```

if you still have trouble, post the contents of your /etc/samba/smb.conf file, or try the first link in my sig.

edit:
before this will work, you'll have to restart samba:
```
sudo /etc/init.d/samba restart
```

---

### Post by sermat on 2007-01-17
Sorry to intrude, but I have the identical problem.  Is there an answer through the 6.06 GUI?
(Sorry for further question, but most Linux problems, even in distros apparently aimed at refugee users from Windows like me, seem to have to be solved at code level.  Is this so?)
Thanks
Sermat

---

### Post by essex on 2007-01-17
Thanks, that did it for me.  :cool:  I can see from looking at the Samba.cfg file that there is a lot options in there.  Will look at your HowTo & try to learn a little more about. I had looked at the Samba docs but it was overwhelming for a noob.  :confused:

---

### Post by dmizer on 2007-01-17
@essex
no worries on that, the samba docs are overwhelming for me too, and i've been pouring over them for about a year now.  glad we got you working though.

@sermat
regarding your gui ... i've never used it before so i haven't the slightest idea of how to tell you to configure the above settings via your gui.  from another thread i've been watching, i'm not sure it's even possible.  if you like, you can keep an eye on it too.  it's located here: [http://ubuntuforums.org/showthread.php?p=2024040#post2024040](http://ubuntuforums.org/showthread.php?p=2024040#post2024040)

most howto's are written in code edits for the following reasons:
1) there are too many gui environments to be able to write good howto's to cover them all.  gnome, kde, xfce, icewm, fluxbox ... just to name a few.  and they all have different programs and utilities and clicks to perform the same function.  some have a gui for samba editing, some do not.
2) command line directions work for all environments supported in ubuntu, so it doesn't matter if you use xfce or gnome or some other obscure gui we've never heard of, we can help you fix your problem as long as you're willing to work in the command line.
3) command line directions are far less prone to mistakes.  in most cases, all you have to do is simply copy and paste the commands.
4) in many cases, there is NO good gui way of addressing the problem.  you must fix the problem in the command line.
5) linux is FULLY customizable.  you can make your gnome environment look and function like a mac.  while mine functions more like a standard gnome environment.  so when i write directions for places for you to click, you won't necessarily be looking at the same thing i am.  this can happen even though we are using the SAME gui.

the above are just a few of the main reasons you're not likely to see many gui howto's listed here.

so, as long as you're willing to copy and paste commands like i've given above, i can help you.  otherwise, i'd have to partition off a piece of this computer's hard drive and install dapper (i'm running edgy), then have to figure out what gui you're referencing, and figure out if there's a way to do it.  this process could take me a week or more to figure everything out.

the above directions took me all of 10 minutes to write up, and probably took essex about the same amount of time to implement.  what's more, the above directions will work in edgy and dapper.

---

### Post by sermat on 2007-01-18
DMIZER
Thanks for your explanation - it helps a lot for newcomer to have a broader understanding than I had.  I will try to follow in Essex's footsteps. Thanks again
Over and out!   Sermat.

---

