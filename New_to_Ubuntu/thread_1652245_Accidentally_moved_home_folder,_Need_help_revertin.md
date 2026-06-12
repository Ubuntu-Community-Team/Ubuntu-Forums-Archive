---
title: "Accidentally moved home folder, Need help reverting."
date: 2010-12-24
forum: New to Ubuntu
---

### Post by poisonpixel on 2010-12-24
I was using an application that gave me a view of folders on my computer and accidentally dragged my /home folder into the /lib folder. I am not sure how to put it back in its original place.  When I try use sudo nautilus in the terminal there is now an error and the program doesnt start. The computer was also shut off and when I rebooted it is now a blank wallpaper type screen but I can still start terminal. How should I go about moving this folder to the original place?

Why would it allow me to move the folder but not give me permission to move it back. :/

---

### Post by Dark_Stang on 2010-12-24
Your home folder stores a lot of user specific settings and configuration files. You should be able to boot from a Live CD and move it back, or login to recovery console (hold shift while it's starting up and you should see the GRUB menu to choose this). Recovery console will let you login as root to terminal and move it back. Assuming it is in /lib the command to move it back is...
```
mv /lib/home /home
```

---

### Post by wolfgangmcq on 2010-12-24
Probably permissions problems on the /lib folder. If you're not worried about security, try
```
<snip>
```However, note that this gives everyone permission to wreak havoc on /lib/!

---

### Post by Dark_Stang on 2010-12-24
Do NOT do this.

> **wolfgangmcq said:**
> Probably permissions problems on the /lib folder. If you're not worried about security, try
```
<snip>
```However, note that this gives everyone permission to wreak havoc on /lib/!

---

### Post by nothingspecial on 2010-12-24
> **wolfgangmcq said:**
> Probably permissions problems on the /lib folder. If you're not worried about security, try
```
<snip>
```However, note that this gives everyone permission to wreak havoc on /lib/!


[SIZE=4][COLOR=Red]Yes do not do this, whatever you do, you will toast your system[/COLOR][/SIZE]

---

### Post by owiknowi on 2010-12-24
1. when you accidentally moved your home folder, were you logged in as root?
2. if so log in again as root and just move them back.

as far as my knowledge goes, there's nothing changed in the default user/folder rights settings, it's not possible to move anything as a normal user to an other folder than your home folder.

3. did someone else had (remote)access to your computer?

! this is perhaps an interesting thread if you could do this without changing anything to the default user/folder rights !

---

### Post by poisonpixel on 2010-12-24
> **Dark_Stang said:**
> Your home folder stores a lot of user specific settings and configuration files. You should be able to boot from a Live CD and move it back, or login to recovery console (hold shift while it's starting up and you should see the GRUB menu to choose this). Recovery console will let you login as root to terminal and move it back. Assuming it is in /lib the command to move it back is...
```
mv /lib/home /home
```

I tried this and it seemed to work since there was no error-like response after entering it into the terminal. However, when I restarted the computer it still came up with the weird errors because the /home folder being in an incorrect spot. I guess I will have to make a live cd but the question is how. I was in the process of making a live cd when I accidentally dragged the damn home folder into some strange place. I am not to certain of which part of /home which folder was dragged into /lib so I may be doing this wrong. 
i suck
Any reccomendations?

---

### Post by poisonpixel on 2010-12-24
> **owiknowi said:**
> 1. when you accidentally moved your home folder, were you logged in as root?
2. if so log in again as root and just move them back.

as far as my knowledge goes, there's nothing changed in the default user/folder rights settings, it's not possible to move anything as a normal user to an other folder than your home folder.

3. did someone else had (remote)access to your computer?

! this is perhaps an interesting thread if you could do this without changing anything to the default user/folder rights !

When I dragged the folder I was using unetboot and only searching for my flash drive location to make a live usb. I was browsing around in the application's menu thing and accidentally clicked, dragged, and dropped the home folder into the one above which was /lib . I didnt even start it with sudo.

When I start the computer normally it gives the errors:

>could not update ICEauthority file /home/judith/.ICEautority
&
>Problem with configuration server
>(/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)

---

### Post by nothingspecial on 2010-12-24
I`m not sure if you move your personal /home/user folder or the whole /home directory.

From root recovery shell.

If it was your /home/user directory
```

sudo mv /lib/user /home
sudo chown -R user:user /home/user
```Change each instance of [COLOR=Red]user[/COLOR] to your username

If it was the entire /home directory

```
sudo mv /lib/home /
```Then you will have to chown each users home directory as above, using the specific usernames in each case.

---

### Post by Dark_Stang on 2010-12-24
Do you have another machine you can burn the LiveCD with? You're obviously able to post in this forum. If you've only got access to Windows you can download some software to burn the .iso with. (Windows 7 may come with software to do this on it's own, I can't remember).

---

### Post by poisonpixel on 2010-12-24
I guess I will work on your solutions when I have the time. Thanks for your quick replies and help!
You guys are ****ing awesome. Hopefully I will be able to fix this. ; ~ ;

---

### Post by Verbeck on 2010-12-24
and if that didn't work, could you post the output of
*ls -la /lib*

---

### Post by poisonpixel on 2010-12-24
> **Verbeck said:**
> and if that didn't work, could you post the output of
*ls -la /lib*
I wouldnt know how to paste the output of that since I am using a different computer to post on the forums. 

I have tried all the options others posted, other then live cd,  and when I start ubuntu I still get the errors previously mentioned. 

I am still stuck and have no idea what to do. I never expected this **** from an accidental click, super saddening. ;<

---

### Post by poisonpixel on 2010-12-24
In the terminal I wrote:
cd
And it responded:
bash: cd: .home/judith: no such file or directory

; A ; 
What happened to the /home/judith?

I know the entire contents of /home were moved into /lib because before the computer was shut down a nautilus window I opened before accidentally moving the folder allowed me to look at it.

---

### Post by poisonpixel on 2010-12-24
> **Dark_Stang said:**
> Your home folder stores a lot of user specific settings and configuration files. You should be able to boot from a Live CD and move it back, or login to recovery console (hold shift while it's starting up and you should see the GRUB menu to choose this). Recovery console will let you login as root to terminal and move it back. Assuming it is in /lib the command to move it back is...
```
mv /lib/home /home
```

Currently creating a live usb. 
How am I supposed to move it using a live usb?

---

### Post by |Eric| on 2010-12-24
can you do a ls -l /lib 
and a ls -l /home

and post result ?


Edit : sorry can you just type the line for /home or /lib/home ?


one thing you can do is this as your user : 
mkdir /home                                      #this creates a /home folder
mkdir /home/`whoami`                             #this creates  your user folder  (whoami should give your username) 
sudo chown -R YourUsername:YourUsername /home/YourUsername                 #this gives you super powers invisibility amongs other things .... j/k

then just reboot

---

### Post by cgroza on 2010-12-24
> **poisonpixel said:**
> Currently creating a live usb. 
How am I supposed to move it using a live usb?
Mount the partition where you home folder is and then cd to it and follow your instructions.

---

### Post by poisonpixel on 2010-12-24
> **|Eric| said:**
> can you do a ls -l /lib 
and a ls -l /home

and post result ?


Edit : sorry can you just type the line for /home or /lib/home ?


one thing you can do is this as your user : 
mkdir /home                                      #this creates a /home folder
mkdir /home/`whoami`                             #this creates  your user folder  (whoami should give your username) 
sudo chown -R YourUsername:YourUsername /home/YourUsername                 #this gives you super powers invisibility amongs other things .... j/k

then just reboot
FUUUCK I did the last thing you did which allowed me access the computer after logging in. I guess somehow the code someone gave earlier in this thread made me copy it so it ended up like
~/home/home/judith. So much aggravation. ;c

---

### Post by poisonpixel on 2010-12-24
> **Dark_Stang said:**
> Your home folder stores a lot of user specific settings and configuration files. You should be able to boot from a Live CD and move it back, or login to recovery console (hold shift while it's starting up and you should see the GRUB menu to choose this). Recovery console will let you login as root to terminal and move it back. Assuming it is in /lib the command to move it back is...
```
mv /lib/home /home
```
I think this may have been what created the problem. ;/

---

### Post by |Eric| on 2010-12-24
i would guess as much 
glad it solved your thing y

you can move your stuff to the newly created folder to recover all your settings and all that 

ie mv /home/home/judith/* /home/yourusername/*  or somthing like that ( you may need to modify this for *.* and .* )

---

### Post by owiknowi on 2010-12-24
would like to know how the move to /lib was even possible in the first place.
anyone an idea or did i miss something (also am watching lee mack :) )?

---

