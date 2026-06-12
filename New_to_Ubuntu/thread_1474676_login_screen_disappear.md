---
title: "login screen disappear"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by endroix on 2010-05-06
Hi,
I upgraded to ubuntu 9.10 from 9.4 and then everything was fine.
But, when I restart my computer,I dont see the login screen to type my password.
I thought it was because of upgrade problem, but I downloaded ubuntu 9.10 iso and installed it again. But, again, when I restart my computer, login screen doesnt show up at all.

When I do ctrl+alt+F2, I can see tty2 login but doing ctrl+alt+F7, I dont see the login screen only brown background, and I also can see the mouse pointer.

I have no clue at all whats wrong and cant access my computer at all graphically. I can access it through tty2 only.

I have installed freeglut and have Intel card.

Is there any solution for this ?
Thanks a lot.

If any further information is needed such as log message, I will post them.

---

### Post by aktiwers on 2010-05-06
When you login in at tty or fullscreen terminal, have you tried typing:
```
startx
```or

```
sudo /etc/init.d/gdm restart
```

---

### Post by endroix on 2010-05-06
After I login through ctrl+alt+F2 ie tty2, 
I tried startx, and it gives me fatal server error.
When I tried second option ie sudo /etc/...., it display same brown screen without login menu.
I have double boot in my system, does this has anything to do with this ?

Is this because of drivers problem or opengl/freeglut/compiz combination error ?

It seems my linux is not locked, since I can login it through tty2.

---

### Post by aktiwers on 2010-05-06
What if you run:
```
 sudo dpkg-reconfigure -phigh xserver-xorg 
```And reconfigure your xserver.

Then try restart it again.

What error does startx give you?

Edit:
Dualboot should not have anything to do with this. :)

---

### Post by endroix on 2010-05-06
When I first tried aktiwers method, it didnt work.
But doing this
```

sudo /etc/init.d/gdm/ stop

```

and then
```
start
``` 
I can go to graphical Linux. yay !!

But, unfortunately I get lots of errors like this 
The Panel encountered a problem while loading "OAFID:GNOME_FastUderSwitchApplet".
Do you want to delete the applet from configuration menu ?

I dont know what is going wrong, and funny thing is when I go to System -> Shutdown, then Restart 
and shutdown is not available at all...

---

### Post by endroix on 2010-05-06
> **endroix said:**
> When I first tried aktiwers method, it didnt work.
But doing this
```

sudo /etc/init.d/gdm/ stop

```and then
```
starts
```I can go to graphical Linux. yay !!

But, unfortunately I get lots of errors like this 
The Panel encountered a problem while loading "OAFID:GNOME_FastUderSwitchApplet".
Do you want to delete the applet from configuration menu ?

I dont know what is going wrong, and funny thing is when I go to System -> Shutdown, then Restart 
and shutdown is not available at all...

And when I do hard shutdown/restart pressing power key, same thing happens ie no login screen, go to tty2, login there, stop gdm and startx and again same OAFID error.... what is going on here ??

---

### Post by aktiwers on 2010-05-06
Hmm im not sure whats wrong here, could be something with your xserver settings.

Did you try to reconfigure it, like I wrote in my last post?
And what video card do you have?

---

### Post by gocoder on 2010-05-06
> **endroix said:**
> Hi,
I upgraded to ubuntu 9.10 from 9.4 and then everything was fine.
But, when I restart my computer,I dont see the login screen to type my password.
I thought it was because of upgrade problem, but I downloaded ubuntu 9.10 iso and installed it again. But, again, when I restart my computer, login screen doesnt show up at all.

When I do ctrl+alt+F2, I can see tty2 login but doing ctrl+alt+F7, I dont see the login screen only brown background, and I also can see the mouse pointer.

I have no clue at all whats wrong and cant access my computer at all graphically. I can access it through tty2 only.

I have installed freeglut and have Intel card.

Is there any solution for this ?
Thanks a lot.

If any further information is needed such as log message, I will post them.
From the desktop, select System/Administration/Login Screen.  Click the Unlock button and enter in your password.  Then select the "Show screen ..." radio button.  Probably, the next button is selected ("Log in as ... automatically").
Click "Close" and "Close" and then restart.

---

### Post by endroix on 2010-05-06
> **gocoder said:**
> From the desktop, select System/Administration/Login Screen.  Click the Unlock button and enter in your password.  Then select the "Show screen ..." radio button.  Probably, the next button is selected ("Log in as ... automatically").
Click "Close" and "Close" and then restart.
When I go to System/Adminstration/Login Screen...I cant even press the Unlock button...i can see that screen but somehow that screen is shaded/greyed and I cant change anything there.

---

### Post by endroix on 2010-05-06
> **aktiwers said:**
> Hmm im not sure whats wrong here, could be something with your xserver settings.

Did you try to reconfigure it, like I wrote in my last post?
And what video card do you have?

~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

And  I did
 sudo dpkg-reconfigure -phigh xserver-xorg 
as you said but do I have to do anything after this as well. I am sorry, since I dont know much about this.

Do you get any options/choices during above reconfiguration process, since I didnt get any at all.

---

### Post by gocoder on 2010-05-06
Hmmm.
Go to System / Administration / Users and Groups.  All users on the system _may_ be displayed.  (I administer my own machine and I always run from my account.)  Click on your userID and if it's marked "Desktop User" you probably don't have admin privileges.
I did a clean install of Lucid on my custom PC and it runs like a champ.
Find the admin userID and log on using that ID.
Another thought...
Can you open a terminal window (under Apps / Accessories)?
Once opened, type "sudo ls -la /root <CR>" and enter your password.  If you see a listing of the /root directory, you have admin access.  On my system, only root can see its own files.

---

### Post by endroix on 2010-05-06
> **gocoder said:**
> Hmmm.
Go to System / Administration / Users and Groups.  All users on the system _may_ be displayed.  (I administer my own machine and I always run from my account.)  Click on your userID and if it's marked "Desktop User" you probably don't have admin privileges.
I did a clean install of Lucid on my custom PC and it runs like a champ.
Find the admin userID and log on using that ID.
Another thought...
Can you open a terminal window (under Apps / Accessories)?
Once opened, type "sudo ls -la /root <CR>" and enter your password.  If you see a listing of the /root directory, you have admin access.  On my system, only root can see its own files.

Since, I am the only user, I can run my system as root ie doing sudo... and I login as first username/password which is by default same as root one...

Random : And what does X server mean ? How is it related to Linux, gnome ?

---

### Post by eclee25 on 2010-05-20
I am having the same problem as the original post on LinuxMint 8. My GRUB screen boots fine but when I choose Mint and wait for the login screen to load it doesn't appear. I tried the suggestions on this thread.

1. When I try startx, it gives me this error:

Fatal server error:
Server is already active for display 0
[INDENT]If this server is no longer running, remove /tmp/.X)-lock and start again.[/INDENT]
Please consult the The X.Org Foundation support at [http://wiki.x.org](http://wiki.x.org) for help.

ddxSigGiveUp: Closing log

Invalid MIT-MAGIC-COOKIE-1 keygiving up
xinit: Resource temporarily unavailable (errno 11): unable to connect to X server
xinit: No such process (errno 3): Server error

I don't know what startx is so I'm not sure what this error means.

2. When I try sudo /etc/init.d/gdm restart the login screen again does not appear

3. When I try sudo dpkg-reconfigure -phigh xserver-xorg
and restart, the login screen does not appear

4. And when I try sudo /etc/init.d/gdm/ stop and then start again (as this is the code that seemed to have worked for endroix, the login screen doesn't appear again.


Does anyone have any suggestions about what I should do? I will post this on the Mint forum as well, but I thought since there was already a thread on it here, this is where I would start.

Thanks in advance for any suggestions!

---

### Post by bwallum on 2010-05-20
Any reason why you can't do a fresh install of Lucid?

That may be a good way to start afresh. Otherwise delete the tmp X lock file mentioned above. It appears that X thinks its already running when you try to start it.

Lucid runs very nicely and much quicker to boot than Karmic (which was no slouch).

---

### Post by eclee25 on 2010-05-20
I was planning on doing a fresh install but there are some files on there that I hadn't backed up yet (one in particular which is due tomorrow) so I think I will hold off until I get this issue sorted out.

How would I go about deleting the tmp X lock file from terminal? Sorry if this a really simple task, but I guess this is why the newbie forum. ;)

Edit: Actually I think the real question is, how do I determine where the tmp X lock file is located so that I can delete it. (I'm sure I could figure out how to delete it looking at other posts)

---

### Post by bwallum on 2010-05-21
> **eclee25 said:**
> ... how do I determine where the tmp X lock file is located so that I can delete it.

It's a hidden file in Places>Computer>File System/tmp

To show hidden files hold down the ctrl key and press the h key (ctrl h)

It will not let a user delete it (need to be root) so open a terminal Applications>Accessories>Terminal and type in ```
gksu nautilus
```This opens file navigation as root and you can delete anything (so please be careful).

If you can't get to see anything then try loading Ubuntu in recovery mode. Select a command line and enter ```
sudo rm /tmp/.X0-lock
``` (the 0 is the numeric zero)

---

### Post by -humanaut- on 2010-05-21
My Login screen in Lucid as been dead since the Alpha's thanks to plymouth I just log in VIA tty console and startx I've completely given up on plymouth since a login screens not important to me and I wasting alot of time trying to fix something upstream should have fixed before releasing Lucid.

---

### Post by eclee25 on 2010-05-22
I tried doing sudo rm /tmp/.X0-lock but then startx said that there were no listening sockets and to check to see if a server wasn't already running.

I ended up retrieving my files by mounting my partition with a live boot disk anyways so I may just do the fresh install of lucid as you suggested bwallum. It just seems strange that this error appeared after months of normal usage.

humanaut: what does it mean to login via tty console?

Thanks for your help!

---

### Post by bwallum on 2010-05-22
> **eclee25 said:**
> I tried doing sudo rm /tmp/.X0-lock but then startx said that there were no listening sockets and to check to see if a server wasn't already running. ...


I do hope that I haven't been the cause of any further pain, could you check to see if there is any other X?-lock in tmp. If so delete it (them) and try again.

Good luck, I still think that a fresh install of Lucid is the best course so maybe that has been brought forward a bit for you.

---

### Post by eclee25 on 2010-05-22
There are no other .X#-lock files in the tmp folder although there is a .X11-unix directory. The .X0-lock file is always there after I reboot after deleting it. I'm not sure what the problem is, but no permanent damage was done. I managed to get all the files that weren't backed up off so the worst of it will just be resetting all the settings once I reinstall.

---

### Post by cordite on 2010-09-23
I have this prob also, but I can only see the cursor on black background. Tried ctrl+alt+f2 etc.-method without success. What can we do ;(

---

### Post by teil3 on 2011-10-07
this seem to be a very old thread but i didnt' found much help after googleing for an hour.
i have the same problem, running maverick. it suddenly appeared. did not do an update recently. 
what's very strange is, i can do startx -- :1 and i get the ubuntu desktop. but if i restart, the problem still remains.

---

