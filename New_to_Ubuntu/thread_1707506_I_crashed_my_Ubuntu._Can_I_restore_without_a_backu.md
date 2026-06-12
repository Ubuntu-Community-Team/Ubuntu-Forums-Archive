---
title: "I crashed my Ubuntu. Can I restore without a backup?"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by NationUpNorth on 2011-03-15
I once installed an Nvidia driver for my fresh installed Ubuntu, and also got help with it from in here.

[http://ubuntuforums.org/showthread.php?t=1697036](http://ubuntuforums.org/showthread.php?t=1697036)

However installing that driver makes the OS unable to boot at all. I'm trying to execute a backup file from the shell prompt as instructed but it gives me a "cp: missing destination file operand after... "

I learned to do a backup and execute the backup in case it didn't work by writing following:

```
sudo cp /etc/X11/xorg.conf.backup
```As stated above it doesn't seem to work. It gives me "cp: missing destination file operand after... "

My question is if there's an easy way to restore Ubuntu completely, or do I have to format the whole drive? Please make notice I have no important data on the Ubuntu drive. I did not store any important data at all as I loved to try out the Nvidia driver first.

---

### Post by Sickpuppy87 on 2011-03-15
Try sudo cp /etc/X11/xorg.conf.backup /etc/X11/conf.conf

The second part is the destination

Edit: actually I read that wrong. Do you have a .backup file?

---

### Post by oldos2er on 2011-03-15
Try ```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

### Post by NationUpNorth on 2011-03-15
Ah I can't even read my own notes. I was supposed to write:

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```I entered that and nothing happened. It didn't say anything. Thinking it had probably restored I booted up normally. Not much of a change though. Only difference is the screen now turns black after the loading screen with the dots. Before that it was just loading with the dots...

Like dot.... dot.... dot..... dot.... dot....

And then now it's dot....dot.....dot.... black

I'm not actually sure I ever backup'ed the file succesfully, I'm afraid.

EDIT// Oh wait, now it actually boots up in the shell prompt.. Mmh, what can I do? I can't see the desktop.

---

### Post by oldos2er on 2011-03-15
Try ```
startx
```

---

### Post by NationUpNorth on 2011-03-15
No startx didn't help. Said something about file not found I think. I can take a picture and upload if you want?

Or is it just easier to format?

---

### Post by Sickpuppy87 on 2011-03-15
Did it happen to say what file was not found ?

---

### Post by NationUpNorth on 2011-03-15
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): server error.

Those are the last two lines.

---

### Post by crispy_420 on 2011-03-15
Could you boot into single user mode and reconfigure xserver even if to a default driver (sudo dpkg --reconfigure xserver-xorg) just to get past this initial hump? Just a suggestion for now. Or if it is gone completely, install a fresh xorg from command line?

---

### Post by NationUpNorth on 2011-03-16
I'm afraid what you're suggesting is too advanced for me. I do however thank you for trying to help. Once I get time I think a complete format would do better.

---

### Post by RJ12 on 2011-03-16
> **crispy_420 said:**
> Could you boot into single user mode and reconfigure xserver even if to a default driver (sudo dpkg --reconfigure xserver-xorg) just to get past this initial hump? Just a suggestion for now. Or if it is gone completely, install a fresh xorg from command line?

> **NationUpNorth said:**
> I'm afraid what you're suggesting is too advanced for me. I do however thank you for trying to help. Once I get time I think a complete format would do better.


What crispy_420 means is to boot into recovery mode (do you get a boot menu asking you to select an OS to boot into? if not hold the Shift key when turning on the computer until you get a list of OSs to choose then use the arrow keys to highlight the Recovery mode entry and hit enter) then there should be an option to go to a root terminal. Then you should be able to type the command he gave you.

Although, if you want to reinstall, that is your choice.

---

### Post by crispy_420 on 2011-03-16
Reinstall might be the easier choice and depending on your comfort level, the quicker choice too. And that is 100% your choice. Make sure you get your files first to prevent data loss.

There are plenty of guides on what I described, I know cause I have hosed my xorg too many times over the years and been backed into a corner like you. So if you have an extra PC near by you can read these fixes and try. At this point you have nothing to loose but some time. And if you get frustrated, this and many other resources are there to help you.

And sorry about being too technical. Think of single user mode (recovery mode) as the safe mode option just no GUI.

Either path you choose, good luck.

---

