---
title: "Password will not work"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by Amockineuropa on 2010-11-17
I have been using Ubuntu for some now and just yesterday when I went to log in with the same password I have used for 2 years it will not recognize my password. I also get this message which is new:

INSTALL PROBLEMS: The configuration defaults for GNOME power manager have not been installed correctly. Please contact your Computer administrator.

I have not had any issues up until just now. My password has not change. My computer has been off for past 2 weeks but otherwise that is it. What do I do to get back into my account?

frustrated

---

### Post by sikander3786 on 2010-11-17
Press Ctrl + Alt + F1 at you login screen. Do you see the virtual terminal? If yes, use your credentials to login. Does it accept?

If yes, from that command prompt, try

```
sudo dpkg --configure -a
```

If tty doesn't accept the password, try booting into recovery mode by pressing and holding down Shift key on Bios screen until you see the Grub menu. Recovery would be 2nd option on the list. Then drop to root shell and try the same command there.

For resetting password,

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

However power manager problem need to be fixed.

---

### Post by Amockineuropa on 2010-11-17
It seemed to. Meaning I get amockineuropa-laptop login:
I type in my username then get asked password after I enter it I get Last login data
I then typed in the sudo dpkg --configure -a and i get sudo password for amockineuropa:
I entered my password and got amockineuropa@amockineuropa-laptop: $ 

Now what?

---

### Post by sikander3786 on 2010-11-17
Press Ctrl + Alt + F7 and try to login your desktop.

Or if it doesn't bring up the login screen, reboot and try logging in. For reboot,

```
sudo shutdown -r now
```

---

### Post by Amockineuropa on 2010-11-17
I tried that and it appeared to cycle for a few seconds then went back to log on screen.

---

### Post by sikander3786 on 2010-11-17
> **Amockineuropa said:**
> I tried that and it appeared to cycle for a few seconds then went back to log on screen.
Which version of Ubuntu is it?

Which graphics card? Are the proprietary drivers installed?

Is compiz enabled?

---

### Post by Amockineuropa on 2010-11-17
Ubuntu 10.10. Not sure what the rest is but like I said everything was fine 2 weeks ago when I shut my pc off.

---

### Post by sikander3786 on 2010-11-17
Go to the terminal again by Ctrl + Alt + F1 and see if you have a home directory.

```
ls /home
```

The output should match your username.

---

### Post by Amockineuropa on 2010-11-17
What then? I dont mean to be so dumb but everything was fine until I turned off PC 2 weeks ago last night it worked fine then I rebooted and all these problems started. WHY? Will I loser ALL my data? I just need to get around my password or atleast put in a new one.

---

### Post by Amockineuropa on 2010-11-17
About ready to go back to WINDOWS.

---

### Post by sikander3786 on 2010-11-17
> everything was fine until I turned off PC 2 weeks ago last night it worked fine then I rebooted and all these problems started. WHY? Will I loser ALL my data? 

No one would be able to come up with a definite answer to that.

Might be some updates borked your install... Only assumptions.

You shouldn't lose data. But you might need to figure out what happened and how to solve it.

Choose the Operating System that better suits your needs and satisfies you. If it is Windows, you have the right to choose any :-)

Good Luck!

---

### Post by TheAnachron on 2010-11-17
In linux you are able to reset the root password, so there is no way to loose all data of linux if the file system is fine.

---

### Post by Amockineuropa on 2010-11-17
Question is HOW to do that. I believe the devil is in the 10.10 upgrade. I use to run 9.04 and life was good. Then upgrade to 10.04 then 10.10 changed that for me. Everything was running just dandy after the upgrades then just today - PEROBLEMS. I know my password. The PC might have forgot it but I did not. I need this data on this HD. HOW did I get back into my old account w/out having to Re-install the entire OS and wiping my HD clean. HOW do I reset master password and then HOW did I get back into my old account?

---

### Post by sikander3786 on 2010-11-17
Until you don't get an error like "authentication error" or "wrong password", it might not be a password problem. As you said, you type your password and hit Enter, screen changes for a moment but reverts back to login screen again. That is not caused by wrong password.

It might be caused by a missing home directory, compiz problems etc. You can confirm presence of your home directory using the command that I posted earlier.

And for resetting password, instructions are present in the link in my first post.

---

### Post by Amockineuropa on 2010-11-17
I will try that when I get off work.

---

### Post by Amockineuropa on 2010-11-17
what is compiz?

---

### Post by sikander3786 on 2010-11-17
> **Amockineuropa said:**
> what is compiz?
If you don't know about that, you probably might not have enabled it :)

It is a Window Manager with lots of eye-candy features like wobbly windows, desktop cube, custom animations etc.

---

### Post by Amockineuropa on 2010-11-17
U R right I dont know that so I probably did not do it

---

### Post by Amockineuropa on 2010-11-17
How or WHAT do I need to do about that Message I get at start up?

---

### Post by Amockineuropa on 2010-11-17
INSTALL PROBLEMS: The configuration defaults for GNOME power manager have not been installed correctly. Please contact your Computer administrator.

Would this have something to do with my problem interms of not being able to lodge in?

---

### Post by sikander3786 on 2010-11-17
> Would this have something to do with my problem interms of not being able to lodge in?

Yes. We first need to find your home directory. It stores most of the related configuration.

---

### Post by Amockineuropa on 2010-11-17
I will have to wait for that until tomorrow when off work. I will try then

---

### Post by Amockineuropa on 2010-11-19
Indeed I ran my home directory is there I then ran file and all of my stuff is there. But how do I fix the password issue

---

### Post by sikander3786 on 2010-11-19
Ok. Please make sure you are not running out of space on your root partition.

Post the output of

```
df -h
```

---

### Post by Hippytaff on 2010-11-19
try
```

passwd

```
 
Edit -> Actually I'll butt out...sorry Sikander, your sorting it :-)

---

### Post by sikander3786 on 2010-11-19
> Actually I'll butt out...sorry Sikander, your sorting it

No problem :-)

Actually the problem is not the password itself but this,

> INSTALL PROBLEMS: The configuration defaults for GNOME power manager have not been installed correctly. Please contact your Computer administrator.

And it is often related to disk space ;-)

---

### Post by Hippytaff on 2010-11-19
Cool...You've got it in hand :-)

---

### Post by Amockineuropa on 2010-11-19
OK I will try this

---

### Post by Amockineuropa on 2010-11-20
I have the data but cannot copy/paste it

I can give U the available data if U ask me what you need

---

### Post by Amockineuropa on 2010-11-20
filesystem        size       used     avail     use%       mounted on
/dev/sda5       63g          60g       1.1m    100%       /
none               1.4g         320k     1.4g     1%           /dev
none               1.4g         0           1.4g      0%         /dev/shm
none               1.4g         216k     1.4g      1%        /var/run
none               1.4g         0           1.4g      0%        /var/lock
none               1.4g         0           1.4g      0%        /lib/init/rw
root@amockineuropa-laptop: /home/amockineuropa#

---

### Post by Elfy on 2010-11-20
Try to clean some space on the root drive - could be causing your issue as / is full. I f you run these from the recovery root prompt you'll not need sudo

```
sudo apt-get autoclean
``` removes out of date packages

```
sudo apt-get clean
``` removes all packages


If that allows you in - I suggest that you look at what you have in / as the problem will return.

This line shows how full / is 

/dev/sda5 63g 60g 1.1m 100% /

---

### Post by sikander3786 on 2010-11-20
You can try to clean your apt-get cache as **forestpiskie** suggested above.

60 GB is used on that space so that is not Ubuntu alone and you have got some personal files on that drive as well. If cleaning the cache doesn't help, you can boot into a Live CD and move some of your data away from / partition to some other place.

---

### Post by Amockineuropa on 2010-11-20
So I run these commands from the terminal? It should clean out some of the packages that have accumulated. 
 
Otherwise not SURE what the Recovery Root drive is. So by removing these packages this will free up space on the HD? These packages I take it are no longer needed?

---

### Post by sikander3786 on 2010-11-20
> **Amockineuropa said:**
> So I run these commands from the terminal? It should clean out some of the packages that have accumulated. 
 
Otherwise not SURE what the Recovery Root drive is. So by removing these packages this will free up space on the HD? These packages I take it are no longer needed?
Yes those commands will clean up some space.

And those packages are already installed. They are saved so in case, at some point when re-installing any of those applications, they don't need to be fetched from the internet again.

No harm in deleting them.

---

### Post by Amockineuropa on 2010-11-20
Again I am at work and wll have to try these suggestions in the AM when I get off. I do appreciate your efforts and I hope that this will work for me.

---

### Post by Amockineuropa on 2010-11-21
Thank you your suggestions worked like a charm. I am grateful.

---

### Post by sikander3786 on 2010-11-21
> **Amockineuropa said:**
> Thank you your suggestions worked like a charm. I am grateful.
Glad to know it worked :-)

You can mark the thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

