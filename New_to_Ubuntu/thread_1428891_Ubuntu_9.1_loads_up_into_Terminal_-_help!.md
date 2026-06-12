---
title: "Ubuntu 9.1 loads up into Terminal - help!"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by kendankendan on 2010-03-13
Hi,

My Ubuntu 9.1 OS loads into terminal.  It used to open up in a GUI environment.

I am a knowledgeable windows user eager to move completely to Linux.  That makes me a newbie in the Linux/Ubuntu world.

I have tried:
startx
sudo/etc/init.d/gdm start
inti 5

I really don't know what they do but I've tried them.

Can you help me?

---

### Post by souleke on 2010-03-13
try Ctrl+alt+F7 to switch at tty7 where the desktop shoud be

---

### Post by EMR on 2010-03-13
Is this after you log in?  If so, there is an option before you log in to switch to and from a command line session, and it may have somehow switched to that.

---

### Post by kendankendan on 2010-03-13
I've tried Ctrl+alt+F7 - didn't work

I was never brought to the point where I log in.

Interestingly, I tried this:

I typed exit and hit return
The Ubuntu logo came up.  This looks good
The login screen appeared.  This is better.
Everything looked like it would work at this point and then....

I'm back to where I was.  Let me describe it to you:
It is a white rectangle on the top left hand corner with the following:
kendan@ubuntu:~$

Outside the white rectangle is all black

---

### Post by shabs on 2010-03-13
Do you get any errors when you try 'startx' or 'sudo/etc/init.d/gdm start'?

Shabs.

---

### Post by kendankendan on 2010-03-13
Using startx I got:
X:user not authorized to run the X server, aborting

Using sudo/etc/init.d/gdm start I got:
Dash: sudo/etc/init.d/gdm: No such file or directory

---

### Post by shabs on 2010-03-13
Not sure if that helps but try 'sudo startx'.
If that fails an option would be (re)installing gdm. 'sudo apt-get install gdm' and then 'sudo /etc/init.d/gdm start'
If you get any errors be sure to post them ;)

Shabs.

---

### Post by kendankendan on 2010-03-13
Tried sudo startx
>>>Fatal server error.  server is already active for display0.  if the server is no longer running, remove ./tmp/.X0-lock and start again

Tried sudo apt-get install gdm
>>>.... already installed - no changes

Tried sudo /etc/init.d/gdm start
>>>since the script you are attempting to invoke has been converted to an upstart job, you may also use the start(8) utility eg. start gdm

Tried sudo start gdm
>>> Rejected start message, matches rules...................

---

### Post by sandyd on 2010-03-13
> **kendankendan said:**
> Tried sudo startx
>>>Fatal server error.  server is already active for display0.  if the server is no longer running, remove ./tmp/.X0-lock and start again

Tried sudo apt-get install gdm
>>>.... already installed - no changes

Tried sudo /etc/init.d/gdm start
>>>since the script you are attempting to invoke has been converted to an upstart job, you may also use the start(8) utility eg. start gdm

Tried sudo start gdm
>>> Rejected start message, matches rules...................
```

sudo killall gdm
sudo rm tmp/.X0-lock
sudo gdm
```
how about that?

---

### Post by kendankendan on 2010-03-13
> **carlee said:**
> ```

sudo killall gdm
sudo rm tmp/.X0-lock
sudo gdm
```how about that?

sudo killall gdm
>>>No process found

sudo rm tmp/.X0-lock
>>>I didn't write it down, but there was nothing to delete

sudo gdm
>>> *** /gdm-binary;1694:warning ***:Failed to acquire org.gnome.Displaymanager......
bailing out


My Ubunto is on a partition beside another partition containing windows vista.  Unfortunately I can't cut and paste from one to another.    I feel inadequate.  I usually help people out in the windows world.  Go figure.

---

### Post by flipper9 on 2010-03-13
I have the same exact problem and the proposed fixes gave the same errors. Just stuck and can't login. Guess time to reinstall! :(

---

### Post by kendankendan on 2010-03-13
I'd be happy to reinstall ubuntu if I knew how without erasing my files.  Is that possible?

---

### Post by shabs on 2010-03-13
Try 'sudo apt-get remove gdm --reinstall'
and then try 'startx'
Also try 'sudo apt-get install ubuntu-desktop' or 'sudo apt-get install ubuntu-desktop --reinstall' if it says that its already installed.

Have you tried going into the recovery mode? Do you see the GUI then?

Do you remember making any changes as you said you were seeing the GUI before. Something could have affected the X11.

Also please post the contents of /etc/X11/xorg.conf. Specially the sections under 'Section "Monitor"' and 'Section "Display"'

Shabs.

---

### Post by kendankendan on 2010-03-13
When I choose the recovery mode,  I am not able to cursor up/down to select options.  It seems to be frozen.

I tried the last set of instructions and out of desperation, tried a few other things.  At this point, I am giving up.  I don't have the experience to tackle this.

I'd like to change gears....
My hard drive is partitioned.  One partion is ntfs and the other is ext6 (??The latest Linux filesystem format whatever it is.).  I have a grub boot loader to select which os to run.
I'd like to reinstall Ubuntu on the same partition.  I'd like to keep my home director if I could but that is not necessary.

I had made an attempt using the ubunto 9.1 cd.  Having restarted it with the cd in the drive, I felt confident that I was doing the right thing up to a certain point when I was not sure if it was going to place another ubuntu9.1 instance on my hard drive or if it would overwrite the existing ubuntu (which is what I want).  I was afraid to continue.

Any help would be appreciated.  I really want to drop MS mostly because I believe in the philosophy of Ubuntu just as much as I am opposed of what Bill Gate's philanthropist views and where the money is being spent.

Thanks all for the help you've given me so far.

---

### Post by shabs on 2010-03-13
:)
I was under the impression that ext4 is the latest, neither did a google search lead me to ext6.
That aside, if you want to save your home partition you can always back it up, reinstall and move it back.
"dd if=/folder/to/backup of=/destination/folder".
However if you're not worried about your data a fresh install would be an alternative.
Unless you create a new partition, you would be overwriting an existing one. Feel free to ask more questions if you have any.

Shabs.

---

