---
title: "Clean install of Karmic, having problems."
date: 2010-01-07
forum: New to Ubuntu
---

### Post by gshockxc on 2010-01-07
I just finished the clean install of Karmic, and I'm already having issues.  First, only one of my dual monitors is working.  I tried to turn on the second monitor, and save the settings to the config file, but I get this error message: 

```

Failed to parse existing X config file '/etc/X11/xorg.conf'!

```

Then I click 'OK' and it closes the Nvidia server settings window.  

There are 130+ bug fixes, so I'm installing those now, and we'll see if that helps.

---

### Post by Soulcage on 2010-01-07
I believe I had the same problem not on kubuntu though. (can't really remember the error) The solution was to delete the xorg.conf file with: sudo rm /etc/X11/xorg.conf then save the settings with sudo nvidia-settings.

---

### Post by gshockxc on 2010-01-07
I'm also missing the Synaptic Package manager...

---

### Post by howefield on 2010-01-07
Remove the existing xorg.conf (or rename so you still have a copy in case of issues, however, given that Karmic doesn't need the file...)

After a clean install of Ubuntu, I do the following to get dual monitors working.

Install nvidia/proprietary driver.

Then in a terminal, execute the following command.

```
sudo rm /etc/X11/xorg.conf
```

Then start nvidia-settings

```
gksudo nvidia-settings
```

Configure as appropriate and when saving the file, save to

```
/etc/X11/xorg.conf
```

---

### Post by gshockxc on 2010-01-07
> **Soulcage said:**
> I believe I had the same problem not on kubuntu though. (can't really remember the error) The solution was to delete the xorg.conf file with: sudo rm /etc/X11/xorg.conf then save the settings with sudo nvidia-settings.

Tried that, same error.

---

### Post by Salpta on 2010-01-07
Try again but use:

sudo nvidia-xconfig

after deleting xorg.conf and before running nvidia-settings.
[http://ubuntuforums.org/showthread.php?t=1312435](http://ubuntuforums.org/showthread.php?t=1312435) (undoIT's post)

---

### Post by gshockxc on 2010-01-07
> **howefield said:**
> Remove the existing xorg.conf (or rename so you still have a copy in case of issues, however, given that Karmic doesn't need the file...)

After a clean install of Ubuntu, I do the following to get dual monitors working.

Install nvidia/proprietary driver.

Then in a terminal, execute the following command.

```
sudo rm /etc/X11/xorg.conf
```

Then start nvidia-settings

```
gksudo nvidia-settings
```

Configure as appropriate and when saving the file, save to

```
/etc/X11/xorg.conf
```

This is really pissing me off.  I'll get over it, but when I ran the gksudo command, here's what I got: 

```

The program 'gksudo' is currently not installed.  You can install it by typing:
sudo apt-get install gksu
gksudo: command not found

```

WTF, do I have to reinstall EVERYTHING?!!!

---

### Post by Salpta on 2010-01-07
gksudo is the proper way to run gui's from the command line.  You can install gksu, or just use sudo.  It will work just as well.

Source: [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by gshockxc on 2010-01-07
OK, I got gksudo installed, and I get the same error.  It won't let me save to the xorg.config file.

```

gksudo nvidia-settings

```

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".

---

### Post by sadaruwan12 on 2010-01-07
Yo, BRO don't blow your top off k just relax 'cos some people have the luxury of having flawlessly working PC's with Ubuntu karmic in them. And I'm one of them. for your problem try doing this,

open X11.conf file ;
```
sudo gedit /etc/X11/X11.conf
```

then open your NVIDIA setting manager and do all the needed configuring on that.

When you're going to save the X11 settings you could see a button labeled as preview click on that and that'll open up a preview of your new X11 settings select all of them and copy it then go to your already opened X11 delete all the content there.

Paste your nvidia settings on to that empty X11 file and click save. Now close it restart your system.

Did you do a full system upgrade after your fresh install and before trying to get your VGA setup ?

---

### Post by Salpta on 2010-01-07
Step-by-step:

1. Remove old xorg.conf:    $sudo rm /etc/X11/xorg.conf
2. Reconfigure x:           $sudo nvidia-xconfig
3. Restart x:   Press Ctrl + Alt + Backspace keys all at once.
4. Rerun nvidia-settings:   $gksudo nvidia-settings
5. Make your changes & apply them.
6. Click Preview (this is just in case)
7. Make a new file in your home directory named xorg.conf
8. Copy all the text from the preview into the new file & save.
9. Save the nvidia-settings.  If it borks again run: $sudo cp ~/xorg.conf /etc/X11.xorg.conf

---

### Post by gshockxc on 2010-01-07
> **Salpta said:**
> Step-by-step:
7. Make a new file in your home directory named xorg.conf


Sorry, I know I'm an idiot, but how do you make a file?  I can't seem to recall.  I thought it was 

```

mk xorg.conf.backup

```

But that doesn't work.
I'm with you on everything else.

---

### Post by gshockxc on 2010-01-07
> **sadaruwan12 said:**
> Yo, BRO don't blow your top off k just relax 'cos some people have the luxury of having flawlessly working PC's with Ubuntu karmic in them. And I'm one of them. for your problem try doing this,

open X11.conf file ;
```
sudo gedit /etc/X11/X11.conf
```

then open your NVIDIA setting manager and do all the needed configuring on that.

When you're going to save the X11 settings you could see a button labeled as preview click on that and that'll open up a preview of your new X11 settings select all of them and copy it then go to your already opened X11 delete all the content there.

Paste your nvidia settings on to that empty X11 file and click save. Now close it restart your system.

Did you do a full system upgrade after your fresh install and before trying to get your VGA setup ?

I know, I'm not trying to get too upset.  It's just annoying because I have no idea what I'm doing.

I know what you're saying, I'm just not having much luck getting it to do that.  I finally got it to recognize my second display, but I mistakenly checked the box for a separate X Screen, so now it's like I have two different desktops, instead of an extended one on dual monitors.

What do you mean by a full system upgrade?  I thought that's what I did when I installed from the .iso image I burned.

When I first tried setting up the dual monitors - after the CD install, I got several notifications for bug fixes and updates.  When things didn't work with the Nvidia settings, I went back and installed those, but I'm still having trouble.

Thanks.  Trying to stay calm.

---

### Post by gshockxc on 2010-01-07
OK, I'm not even sure what changed, or why it worked this time, and not before.  For some reason, it wouldn't let me modify the xorg.conf.backup file, so I removed it.

Then it wouldn't let me create a new one.  I was trying to make one, but I couldn't remember the command to make a file.  I was trying to configure the dispalys like I wanted while hoping for a new post to this thread, and for whatever reason, it would let me save the file xorg.conf file

When I pressed Ctrl+Alt+Backspace, nothing happened.  At least, I didn't 'SEE' anything happen.  I don't know if I was able to save the file right after that, but I restarted my machine, and now I've got both displays working properly.  Thanks for the help guys.  I know what you were trying to help me do, but I'm still not sure what I was doing wrong.  

I guess I'm getting closer.  Thanks.

---

### Post by GameManK on 2010-01-10
> **Salpta said:**
> gksudo is the proper way to run gui's from the command line.  You can install gksu, or just use sudo.  It will work just as well.

Source: [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)
On Kubuntu, use kdesudo instead.  No need to install gksudo, though it'll get pulled in if you install something like synaptic anyway.

---

### Post by gshockxc on 2010-01-10
> **GameManK said:**
> On Kubuntu, use kdesudo instead.  No need to install gksudo, though it'll get pulled in if you install something like synaptic anyway.

That makes sense.  gksudo didn't work, and I had to install it.  Of course, that's because I didn't know to use kde sudo.

How do you become a Kubuntu Member?  Is that just from signing up on the forums, or registering as a Kubuntu user?

---

