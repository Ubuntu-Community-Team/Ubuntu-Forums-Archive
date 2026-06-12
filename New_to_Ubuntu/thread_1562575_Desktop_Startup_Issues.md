---
title: "Desktop Startup Issues"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by throese on 2010-08-27
While in Ubuntu:

I clicked "Safely Remove Device" on my external hard drive then restarted my computer. I also removed LAMP by doing:

```
tasksel remove lamp-server
```

While in Windows 7:

I went on added some videos from my Windows partition to my external hard drive then restarted (without clicking "Safely Remove Device" on my external hard drive).

Here's when all my problems started

After restarting my computer and getting the GRUB Bootloader, I selected Ubuntu so it would load. I got this as a result:

[http://i36.tinypic.com/2le6z34.jpg](http://i36.tinypic.com/2le6z34.jpg)

Then after I hit the "Escape" key, I got to this:

[http://i37.tinypic.com/2zi6drp.jpg](http://i37.tinypic.com/2zi6drp.jpg)

So, is there ANYTHING I can do from the CLI (Command Line Interface) to restore the GUI or will I have to (for the THIRD EFFING TIME) make a full re-install and download all 200+ MB of stuff from the update manager?

I don't know how to back up my stuff and I don't know what to do. I don't mean to keep bugging you all all of the time about minor problems that I somehow manage to cause, yet can't fix because I'm still learning.

---

### Post by zeroseven0183 on 2010-08-27
Quick question: Have you tried logging in to that command line?

---

### Post by throese on 2010-08-27
Yes, but it still stays in the command line, any ideas as to what I could do once I've logged in through the command line?

Nano:

[http://i204.photobucket.com/albums/bb125/throese/nano.jpg](http://i204.photobucket.com/albums/bb125/throese/nano.jpg)

It asks (cause I typed while in nano) what can I do from the CLI to restore the desktop.

Low Graphics Options:

When I hit "Enter" on Ubuntu it gave me a prompt that asked if I wanted to run Ubuntu in low graphics mode, I hit yes then it gave me this little box:

1) Run Ubuntu in low graphics mode for just one session

2) Reconfigure Graphics

3) Troubleshoot The Error

4) Exit to console login

5) Restart X

Those are the 5 options it shows.

[http://i204.photobucket.com/albums/bb125/throese/options.jpg](http://i204.photobucket.com/albums/bb125/throese/options.jpg)

Recover Mode Options:

[http://i204.photobucket.com/albums/bb125/throese/recoverymode.jpg](http://i204.photobucket.com/albums/bb125/throese/recoverymode.jpg)

So, with all the new information and pictures, does anyone have any new ideas as to how I can restore the desktop and how it became messed up in the first place?

---

### Post by theDaveTheRave on 2010-08-28
OK, seems as though you have a few strange issues??

I assume you are posting from your windows partition.

from what I understand you seem to be able to get into a CLI prompt from a login? (sorry your pictures aren't that great so I just need to confirm...)

so if you have your CLI you can try the following...

```
startx
```

to start a basic graphical session, I half expect that it will say that you don't have X installed (or similar).

In which case you can simply perform the following...

```
sudo apt-get install ubuntu-desktop
```

and you will get an installed Gnome desktop, I assume this is what you want? if you want to load a 'light weight' desktop look into how to install either LX11DE (my current choice) or something like fluxbox or openbox.

regarding your external HDD problem, you may need to log into windows, access the drive from there, then 'disconnect' it in the 'correct' manner.

Otherwise, as you say you have 'installed' from scratch 3 times already I guess you have a live CD somewhere nearby, check you are able to access the disk from this.

quickly regarding backups...

The best would be to create a cron job to copy over all of your '/home' on a periodic basis, to another disk or similar. I don't know what the 'official' suggested basis of backups is for linux, so you will need to do a quick search.

good luck...

David

---

### Post by skatinjj on 2010-08-28
> **throese said:**
> Yes, but it still stays in the command line, any ideas as to what I could do once I've logged in through the command line?

Nano:

[http://i204.photobucket.com/albums/bb125/throese/nano.jpg](http://i204.photobucket.com/albums/bb125/throese/nano.jpg)

It asks (cause I typed while in nano) what can I do from the CLI to restore the desktop.

Low Graphics Options:

When I hit "Enter" on Ubuntu it gave me a prompt that asked if I wanted to run Ubuntu in low graphics mode, I hit yes then it gave me this little box:

1) Run Ubuntu in low graphics mode for just one session

2) Reconfigure Graphics

3) Troubleshoot The Error

4) Exit to console login

5) Restart X

Those are the 5 options it shows.

[http://i204.photobucket.com/albums/bb125/throese/options.jpg](http://i204.photobucket.com/albums/bb125/throese/options.jpg)

Recover Mode Options:

[http://i204.photobucket.com/albums/bb125/throese/recoverymode.jpg](http://i204.photobucket.com/albums/bb125/throese/recoverymode.jpg)

So, with all the new information and pictures, does anyone have any new ideas as to how I can restore the desktop and how it became messed up in the first place?

Try to reconfigure your xorg:

```
sudo dpkg-reconfigure xserver-xorg
```

Just follow onscreen instructions

Also, have you tried press ctrl-alt-F7 to see if that dumped you back into the gui?

---

### Post by throese on 2010-08-29
None of them fixed my problem so I just re-installed it again and downloaded everything from the update manager and Ubuntu Software Center again.

---

