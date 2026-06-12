---
title: "Desktop environment freeze after login  (me too)"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by hopefulkayaker on 2011-04-11
I am having the same problem as in [this thread]("http://ubuntuforums.org/showthread.php?t=1709949"), except I can't get the fix to work. I was watching a youtube video last night, in which the video froze but the audio kept playing. Upon attempting to rectify the situation by reloading the page, I discovered that the system was frozen.

After rebooting, I saw my GMOME-do, which I had just installed earlier in the day, and the 'unlock login keyring' window, which I'd never seen before.

The fix in the linked thread above is to enter a few commands in recovery mode, which worked for that person. However, I've never even heard of recovery mode, as I've only been running Maverick Meerkat for a week. 

I found [this thread]("http://ubuntuforums.org/showthread.php?t=34473") which explains how to do it. But at no time in my bootup do I see a message prompting me to hit ESC. So I hit ESC all through the boot process, but it just booted normally. I read on another site that you can get to recovery mode using a live CD as well, but that didn't work either.

:-(

---

### Post by Hippytaff on 2011-04-11
If you are not dual booting (which it seems you are not) you should be able to get the grub menu, which will give the option to boot into recovery mode by pressing SHIFT at boot.

---

### Post by hopefulkayaker on 2011-04-11
That's right, I'm not dual booting. I managed to hit ESC at the right time, and am at the root shell prompt.

The other thread says to type:

rm /home/USERNAME/.config/gnome-session/saved-session/*
But when I do, it says "cannot remove [PATH ABOVE]: No such file or directory".

My username is either 'Brian' or 'brian', but neither of them work.

I tried a few commands to figure out what the eff is going on, but to no avail:

```

cd home
bash: cd: home: No such file or directory
ls
[no output]
ls -l
total 0

```

What's going on?

---

### Post by Hippytaff on 2011-04-11
Your username shouldn't have any CAPS. Linux doesn't like it.
 
What does doing```
pwd
``` and ```
whoami
``` return?

---

### Post by hopefulkayaker on 2011-04-11
Let's see...

```

pwd
/root
whoami
root

```

---

### Post by Hippytaff on 2011-04-11
sorry about this...what does ```
df -h
``` return

---

### Post by hopefulkayaker on 2011-04-11
> **Hippytaff said:**
> sorry about this...what does ```
df -h
``` return

No problem! :-) I really appreciate your help.

```

df -h
Filesystem Size Used Avail Use% Mounted on
/dev/sda2 43G 7.3G 34G 18% /
none 1.5G 248K 1% /dev
none 1.5G 0 1.5G 0% /dev/shm
none 1.5G 52K 1.5G 1% /var/run
none 1.5G 0 1.5G 0% /var/lock

```

---

### Post by Hippytaff on 2011-04-11
I was looking to see if you had a /home partition, but I forgot that ubuntu does'nt offer a spereate home partition at installation.
 
try ```
cd /home
``` with the forward slash
 
Also does ```
 ls -a
``` return anthing?

---

### Post by hopefulkayaker on 2011-04-11
I think it was the forward slash I was missing before that was causing cd to fail.

Now I've navigated to /home/brian/.config/gnome-session/saved-session

and I get

```

ls -a
. ..

```

So...it sounds to me that the problem I'm having is different than the problem the guy in the other thread was having. Not sure where that leaves me.

---

### Post by Hippytaff on 2011-04-11
now you've got the path correct try the rm command again (as in the post you link to in your first post.
 
what graphics card do you have? you might need to download and run the bootinfo script from [here]("http://sourceforge.net/projects/bootinfoscript/") and post the results.txt just to rule out anything more serious.
 
Unfortunately, I'm going to have to go for a bit (lunch break is over)....no doubt someone will jump in to help...I'll check on your progress as soon as I can.

---

### Post by hopefulkayaker on 2011-04-11
I did run that rm command. There are no saved sessions to remove, it would appear.

I'm not sure what graphics card I have. I'm not much of a gamer, so the card is the one which came with my desktop (a 2yr old budget Dell pavilion).

How would I be able to run the script since it's freezing on the desktop?

Enjoy your lunch, and thanks again. Hopefully another clever mind will think of something. ^_^

---

### Post by Hippytaff on 2011-04-11
You will need to boot from liveCD to run the script (sorry I should have mentioned that.
 Also you can find out your graphics card by doing ```
lspci
```

---

### Post by hopefulkayaker on 2011-04-11
OK, I apparently have an **nVidia GeForce 8300 GS** video card.

---

### Post by Hippytaff on 2011-04-11
in that case you probably need to install the driver. Can you get to the grub menu by pressing SHIFT at boot. If so highlight ubuntu (the top one) and press e. then change 'quiet splash' to 'nomodeset'. Then press CRTL+X to boot. You should get into the graphical user interface. Then you need to go to system -> Administration - > additional drivers, and install the Nvidia one if it is offered to you (which it should be)

---

### Post by hopefulkayaker on 2011-04-11
> **Hippytaff said:**
> in that case you probably need to install the driver. Can you get to the grub menu by pressing SHIFT at boot. If so highlight ubuntu (the top one) and press e. then change 'quiet splash' to 'nomodeset'. Then press CRTL+X to boot. You should get into the graphical user interface. Then you need to go to system -> Administration - > additional drivers, and install the Nvidia one if it is offered to you (which it should be)

I am able to get to grub (using ESC, actually), and I followed your instructions, but when I got to the desktop...it's still frozen. I can't screenshot it, but I see GNOME-do on the screen, and then the "unlock login keyring" window in front of it, just like in the OP.

boo

---

### Post by el_koraco on 2011-04-11
I had the same problem with the damned keyring a couple of times. What did it for me was to go to the console (crtl alt F1), list 

```
ps -ef | grep keyring
```and just start killing processes with the associated PID's. I was so angry I don't even know which process was responsible for the keyring lockup, but somehow managed to get the keyring screen to unlock. Then i entered my user password a few times, went to System - Preferences - Passwords and Encryption Keys and changed the default keyring to blank. I'm just waiting for it to happen again. 

The keyring is an program that stores all your passwords behind an encryption. When you're logging in automatically, it has a tendency to show up at unexpected times, and sometimes goes on a rampage. 

I wouldn't necessarily recommend you try the method I employed, it is perhaps better to listen to a wiser forum member. Mine was done out of sheer frustration.

---

### Post by hopefulkayaker on 2011-04-11
I don't know much about hardware, but it strikes me as odd that this could have anything to do with my video card.

If I can manage to kill the process, I think I'll try just disabling the autologin. I'd rather have to log in that risk this happening again.

---

### Post by hopefulkayaker on 2011-04-11
It seems like those processes are getting re-started, since after killing all processes with 'keyring' in the name, there are still the same number of 'keyring' processes.

---

### Post by Hippytaff on 2011-04-11
if you do htop, it will list processes and PID's. you can then do```
 kill PID (process number)
```. I was thinking you might possibly need to reinstall x.org

---

### Post by hopefulkayaker on 2011-04-11
> **Hippytaff said:**
> if you do htop, it will list processes and PID's. you can then do```
 kill PID (process number)
```. I was thinking you might possibly need to reinstall x.org

Yeah, I tried killing the keyring process again, but it's not working. I try killing it, and then when I check to see if it's running...it still is. I presume is was killed and then restarted.

---

### Post by Hippytaff on 2011-04-11
It might be worth looking into stopping the daemon from starting...then rebooting

[http://manpages.ubuntu.com/manpages/maverick/man8/start-stop-daemon.8.html](http://manpages.ubuntu.com/manpages/maverick/man8/start-stop-daemon.8.html)

---

### Post by hopefulkayaker on 2011-04-11
Two questions, what would a well-formed command using start-stop-daemon look like? I see the option to stop a daemon, but how do you prevent it from starting on boot?

Second, how can I get the name of the daemon I need to stop? htop doesn't scroll, and ps doesn't even give names.

---

### Post by el_koraco on 2011-04-11
Try killing it with kill -9 PID. Again, i can't tell you the name of the particular process I've killed to get things working, but I do know i had to kill three or four of them.

---

### Post by el_koraco on 2011-04-11
> **hopefulkayaker said:**
> 
Second, how can I get the name of the daemon I need to stop? 

The daemon's name is gnome-keyring-daemon, but i can't tell you about the script, because i haven't tried the option. I think it's best if you wait for input from somebody else.

---

### Post by Hippytaff on 2011-04-11
It explains how to prevent daemons starting up at boot [here]("http://ask.debian.net/questions/how-to-prevent-daemons-from-starting-at-installation-time"). I guess it'll take some googling to find out the name of the daemon that you need to stop, or someone here who knows...I'm not sure

Edit -> now we know the name ;-)

---

### Post by el_koraco on 2011-04-11
Mmmmkay, how 'bout you try this, it might be easier, but it might be worth to note exactly the steps you've taken in order to recreate everything. You might also wanna wait for a second opinion.  
Go to /etc/gdm. List the files. You should see a custom.conf file. Open it with nano. 

```
sudo nano custom.conf
```

the second line should say automatic login enable=true. change it to false and save the text. Save with CRTL O (not zero, the letter), and exit with CTRL X. 

Type ```
sudo shutdown -r now

```

to restart. Let's see what happens.

---

### Post by hopefulkayaker on 2011-04-11
> **el_koraco said:**
> The daemon's name is gnome-keyring-daemon, but  i can't tell you about the script, because i haven't tried the option. I  think it's best if you wait for input from somebody else.

Thank you for the name of the daemon! That should be quite helpful.


> **Hippytaff said:**
> It explains how to prevent daemons starting up at boot [here]("http://ask.debian.net/questions/how-to-prevent-daemons-from-starting-at-installation-time"). I guess it'll take some googling to find out the name of the daemon that you need to stop, or someone here who knows...I'm not sure

Edit -> now we know the name ;-)

I googled 'preventing gnome-keyring-daemon from starting', found [this post]("http://ubuntuforums.org/showpost.php?p=10552905&postcount=12"), and followed the instructions. 

After rebooting, the keyring window appeared saying "Choose password for new keying", but the window, along, with the rest of the desktop, is still totally unresponsive.

:-( This is getting pretty frustrating..if the keyring is so buggy, why has it not been disabled on the development side? I can't use my computer at all until this crap gets sorted out.

---

### Post by hopefulkayaker on 2011-04-11
> **el_koraco said:**
> Mmmmkay, how 'bout you try this, it might be easier, but it might be worth to note exactly the steps you've taken in order to recreate everything. You might also wanna wait for a second opinion.  
Go to /etc/gdm. List the files. You should see a custom.conf file. Open it with nano. 

```
sudo nano custom.conf
```the second line should say automatic login enable=true. change it to false and save the text. Save with CRTL O (not zero, the letter), and exit with CTRL X. 

Type ```
sudo shutdown -r now

```to restart. Let's see what happens.

IT WORKED! :-D

Thank you both for your help!

---

### Post by Hippytaff on 2011-04-11
Good thinking el_koraco

hopefulkayaker - Glad you got it sorted, and well done for not giving up :-)

perserverance will succed

---

### Post by el_koraco on 2011-04-11
Glad to see it worked out. don't forget to mark the thread as solved.

---

