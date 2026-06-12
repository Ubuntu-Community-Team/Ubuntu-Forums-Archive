---
title: "Please, please help me...10.10 version"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by Artone on 2011-06-27
Ok, I installed 10.10 on hp desktop maybe three months ago, I am now having issues with it.
It loads to the user login screen, but when I login to user account, it does show custom wallpaper (that gives me hope) and acts to be loading with the little circle. Mouse does move but cannot operate toolbars. Also, toolbars are usually gray but are now white. What can I do to get user account to fully load user settings. I have important files that I didn't get a chance to backup. Any help with this, will be greatly appreciated. (I just need to get the files) Thanks in advance for help/advice.

In school cannot afford a comp tech to fix it.

---

### Post by entropy1 on 2011-06-27
If you just want to access your files, you can try booting from a Live CD (or Live CD installed on USB stick).  Choose "Try Ubuntu".  Then you can access any files on the harddrive.  If you also have another usb flashdrive (or external harddrive), you can then copy from your harddisk to the flashdrive.

---

### Post by jtarin on 2011-06-27
At the login screen switch to another display by using the keys Alt+F1-F6. Anyone of those should give you a display. Then login as root and use the terminal to access your files.

---

### Post by maizuddin35 on 2011-06-27
yes, use a live cd, or just ALT+F1 - F6, by doing this you still can access the file in you pc.

---

### Post by Artone on 2011-06-28
Tried to boot from cd, using try ubuntu it does but shows the same non working white toolbars. Also, tried alt+f1 -f6 I get nothing.
It shows message "GNU GRUB version 1. 98+20100804-5ubuntu3
Ubuntu, with linux 2.6.35-22-generic
(Under that it reads recovery mode)
Memory test (twice the lower reads serial console 115200) 
What are my options now? Thanks for advice.

---

### Post by nzjethro on 2011-06-28
> **Artone said:**
> 
It shows message "GNU GRUB version 1. 98+20100804-5ubuntu3
Ubuntu, with linux 2.6.35-22-generic
(Under that it reads recovery mode)


That sounds like the Grub menu. Are you not able to select Ubuntu, with Linux 2.6.35-22-generic from the list?

---

### Post by Artone on 2011-06-28
> **nzjethro said:**
> That sounds like the Grub menu. Are you not able to select Ubuntu, with Linux 2.6.35-22-generic from the list?

Yes, but it brings me back to my original issue. Is this fixable? Thanks.

---

### Post by jtarin on 2011-06-28
> **Artone said:**
>  Also, tried alt+f1 -f6 I get nothing.

What do you mean you got nothing??? That's a little improbable. 

At the GUI login dialog use the Alt+F1 (key combination) Alt+F2, Alt+F3, Alt+F4, Alt+F5 one of those key combinations should have given you a login prompt.

---

### Post by Artone on 2011-06-28
Ok, keyboard isn't working, (bad luck) recharged batteries to see if that  was the prob. It wasn't. 
Your probably right, most likely I did it wrong. I know close to nothing about computers, what I know is basic computing, internet documents. Absolutely no trouble shooting skills, so the lingo is over my head. 
Think I will post a video on youtube to show exactly what it does, or doesn't do. If I can get keyboard to work again. Any help with that? Thanks everyone, but starting to feel like it is a lost cause.

---

### Post by Artone on 2011-06-28
Called a tech he says $75 to recover data, and $75 to install xp this seems pricey to me. Is there nothing else I can do/try here?

---

### Post by pjd99 on 2011-06-28
> **Artone said:**
> Ok, I installed 10.10 on hp desktop maybe three months ago, I am now having issues with it.
It loads to the user login screen, but when I login to user account, it does show custom wallpaper (that gives me hope) and acts to be loading with the little circle. Mouse does move but cannot operate toolbars. Also, toolbars are usually gray but are now white. What can I do to get user account to fully load user settings. I have important files that I didn't get a chance to backup. Any help with this, will be greatly appreciated. (I just need to get the files) Thanks in advance for help/advice.

In school cannot afford a comp tech to fix it.

Log in as above (so you have the white toolbars and all), then press CTRL+ALT+F1 (most F-keys should work, and CTRL+ALT+F7 should get you back to the GUI). This will drop you into a terminal so you can access your files. You might need to learn a few terminal commands to back up your data. Plugging in a flash drive should auto mount it somewhere in the /media directory.
Didn't know ALT+F1 was a valid combo at the login screen (is it? Will have to test)... Then again I log in automatically.

Maybe after that try running:
```

sudo apt-get update
sudo apt-get upgrade

```then restart and see if your Gnome session comes back.

This command should pretty much restore gnome to defaults (in case some customisation has caused problems). 
NOTE: This should be attempted AFTER you backup important data (mainly in case you mistype the command, as rm -rf can be dangerous if used incorrectly - i.e. it can completely hose your system). This command is safe enough, it just saves having to clean out each directory and then rmdir them...
These directories contain a lot of gnome configuration files, but no critical data should be there.
```

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

```

---

### Post by jtarin on 2011-06-28
> **pjd99 said:**
> 
Didn't know ALT+F1 was a valid combo at the login screen (is it? Will have to test)... Then again I log in automatically.
Your probably right...my error as I sometimes forget, not everyone mods keys.It's an old habit.:P

Another alternative if needed. is to create a newuser and attempt login and try recovery, by sudo, once logged in.

---

### Post by josephmills on 2011-06-28
have you tried ctrl+alt+f2 ?(that is what it is for me) to drop the gui? after you drop the gui try a ```
fsck -y /dev/sdawhatevernumber your harddrive is
``` then try a ```
sudo /ect/init.d/gdm restart 
``` did it work?

---

