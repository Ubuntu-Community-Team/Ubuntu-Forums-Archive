---
title: "after 10.10 install and reboot login issue"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by rs87424 on 2010-10-11
I recently installed 10.10 and after I rebooted it comes to a screen that asks for <name of my computer> login: and then it goes to password... I have no idea how to put in the login credentials but I know my password... is there anyway to get into 10.10?

---

### Post by throntax on 2010-10-11
Is it your username, then password?

---

### Post by rs87424 on 2010-10-11
yes, actually I found out what to put for my username.  But here is the root of the problem I think.  Basically, instead of a normal looking log in screen its just a black screen with letters everywhere like the terminal and I log into 10.10 and nothing happens it just says welcome to ubuntu and then its exactly like the terminal.. very strange... not sure what I need to do to get back to normal ubuntu

---

### Post by throntax on 2010-10-11
you may need to install 'gdm'
```
sudo apt-get install gdm
```

but then maybe gnome hasn't installed either? try typing ```
startx
``` and see what happens.

---

### Post by rs87424 on 2010-10-11
well... with the startx... it just says fatal error no such file? or something and the other option says that nothing is updated or upgraded or removed...

---

### Post by throntax on 2010-10-11
ok. When you installed, did you have internet access? It sounds like you need to install some stuff, but if you only have a disc it might be easier to retry installing from that. 

Sometimes an installation just stuffs up halfway through, and I've re-installed and it's been fine. But that hasn't been with 10.10.

---

### Post by celticbhoy on 2010-10-11
Can you boot into recovery
 Is so try the reconfigure packages option

---

### Post by throntax on 2010-10-11
or actually, if you could me more specific with the error output from 'startx,' it may turn out to be a video card driver issue.
When you type startx and the error appears, pay attention to any line that has 'EE' in it. there may be another clue in there.

---

### Post by rs87424 on 2010-10-11
well I found that if I go into recovery mode and put in startx it will take me to a ubuntu screen... otherwise when I looked at the error message for startx it said that no modesetting kernel was found and one screen was found but wasn't applicable

---

### Post by rs87424 on 2010-10-11
and also I tried to reconfigure packages.. but I couldn't find that option as everything was worded differently

---

### Post by throntax on 2010-10-11
do you know what kind of video hardware you have?

Take a look at this link and see if it looks familiar:
[http://ubuntuforums.org/showthread.php?t=1286968]("http://ubuntuforums.org/showthread.php?t=1286968")

---

### Post by rs87424 on 2010-10-11
well its definitely an intel video for sure

---

### Post by throntax on 2010-10-11
That post linked to [https://wiki.ubuntu.com/X/KernelModeSetting]("https://wiki.ubuntu.com/X/KernelModeSetting")

Which hurts my brain at the moment, but you could also try: 

[http://superuser.com/questions/192121/how-to-install-intel-82852-855gm-driver-on-ubuntu-10-10-maverick-meerkat]("http://superuser.com/questions/192121/how-to-install-intel-82852-855gm-driver-on-ubuntu-10-10-maverick-meerkat")
if you're sure it's an intel card.

Just create an xorg.conf in /etc/X11/ using the details in the second link, the four lines should do it. It's a bit of a temporary fix I think, but then maybe it will be easier to research how to downgrade the video driver.

---

### Post by rs87424 on 2010-10-11
sorry for asking... but how do you get into the file... such as etc/default/grub and so on and so forth... using the terminal

---

### Post by throntax on 2010-10-11
there are a few different text editors for doing that. I use vim (or vim.tiny, as it's sometimes called).

To do that, just 'vim.tiny "filename"' (you will need to use 'sudo' for most files outside your home directory)

You should really look it up to find out how to use it, as it's pretty useful. But to get you started, here are a few tips:

to insert text, you first have to press 'i'

once you have inserted text, to get back to 'command mode' (which is where you were before pressing 'i'), press 'escape'

to write and quit, press ':wq' from command mode.

to quit without saving press ':q!' from command mode.

It's a great application with heaps of features, but experiment with a few files getting the hang of just writing, editing, saving and reopening etc. If the 'filename' doesn't exist it will try to create it for you, so try making a new one like that and then move on to the important system files.

---

### Post by rs87424 on 2010-10-12
yeah i just made a cd with ubuntu 10.10 and installed ubuntu again.  Apparently too much was missing from the upgrade and nothing was going to work anyways because for some reason the upgrade didn't work properly

---

