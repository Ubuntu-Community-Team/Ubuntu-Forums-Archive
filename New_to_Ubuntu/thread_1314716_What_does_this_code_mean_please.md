---
title: "What does this code mean please?"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by listerdl on 2009-11-04
Audacious, the music player, refuses to open or work. I have tried several things. In a previous post a reader suggested that I re-install audacious by doing the below command - (the result is also below)

Thanks in advance for all replies and help!


```
henry@DELL-laptop:~$ sudo apt-get install --reinstall audacious
[sudo] password for henry: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-alsaaudio python-awn-extras libawn0 libawn-extras0 python-awnlib
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/1160kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 127116 files and directories currently installed.)
Preparing to replace audacious 1.5.1-3ubuntu1.1 (using .../audacious_1.5.1-3ubuntu1.1_i386.deb) ...
Unpacking replacement audacious ...
Processing triggers for man-db ...
Setting up audacious (1.5.1-3ubuntu1.1) ...

henry@DELL-laptop:~$ 

```

It seems that command 'worked' - but in reality, it did nothing. Was I meant to do something else in the terminal?

After this 're-isntall' - nothing worked and audacious continues to allude me.

Another suggestion was to remove the .audacious folder in my home folder, but when I go to my home folder and do CTRL + H - lots of folders appear but alas no .audacious...

All help greatly appreciated! I feel lost w/out audacious!

---

### Post by scout4536 on 2009-11-04
Seems like all went well with the installation of the music player, just out of spite, try a reboot, you shouldn't have to reboot after installing software, but give it try and see what happens.

If it doesn't work after that, try sudo apt-get autoremove audacious, then reinstall sudo apt-get install audacious

---

### Post by 5BallJuggler on 2009-11-04
> **listerdl said:**
> Audacious, the music player, refuses to open or work. I have tried several things. In a previous post a reader suggested that I re-install audacious by doing the below command - (the result is also below)

Thanks in advance for all replies and help!


```
henry@DELL-laptop:~$ sudo apt-get install --reinstall audacious
[sudo] password for henry: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-alsaaudio python-awn-extras libawn0 libawn-extras0 python-awnlib
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/1160kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 127116 files and directories currently installed.)
Preparing to replace audacious 1.5.1-3ubuntu1.1 (using .../audacious_1.5.1-3ubuntu1.1_i386.deb) ...
Unpacking replacement audacious ...
Processing triggers for man-db ...
Setting up audacious (1.5.1-3ubuntu1.1) ...

henry@DELL-laptop:~$ 

```

It seems that command 'worked' - but in reality, it did nothing. Was I meant to do something else in the terminal?

After this 're-isntall' - nothing worked and audacious continues to allude me.

Another suggestion was to remove the .audacious folder in my home folder, but when I go to my home folder and do CTRL + H - lots of folders appear but alas no .audacious...

All help greatly appreciated! I feel lost w/out audacious!

What do you get when you type "audacious2 %U" into a terminal?

---

### Post by mbzn on 2009-11-04
The '.' In front makes this folder hidden. You can however still delete it in the command line "rm -r ~/.audacious".

---

### Post by AlphaLexman on 2009-11-04
On my system audacious personal files are stored in:

~/.local/share/audacious

Try looking there / rmdir there and reinstall.

---

### Post by listerdl on 2009-11-06
I have tried all of the above with no success.

When I did 'audacious2 %U' as suggested this happened:

henry@DELL-laptop:~$ audacious2 %U
bash: audacious2: command not found

Nothing is making audacious return - any other ideas?

-- OK -- I found the audacious folder and I want to delete it but I cant...any idea how I am able to authorise the deletion? I am the sole person using this laptop...thanks!

---

### Post by 5BallJuggler on 2009-11-06
> **listerdl said:**
> I have tried all of the above with no success.

When I did 'audacious2 %U' as suggested this happened:

henry@DELL-laptop:~$ audacious2 %U
bash: audacious2: command not found

Nothing is making audacious return - any other ideas?

-- OK -- I found the audacious folder and I want to delete it but I cant...any idea how I am able to authorise the deletion? I am the sole person using this laptop...thanks!

easiest way is to type.

"sudo nautilus" into a terminal
enter you password and away you go.

---

### Post by mc4man on 2009-11-06
You're using audacious, not audacious2, so the terminal launch would simply be
audacious

The audacious config files are probably in ~/.config/audacious (never used jaunty but likely place

---

### Post by Paqman on 2009-11-06
> **5BallJuggler said:**
> 
"sudo nautilus" into a terminal


You should never use sudo with a GUI app like Nautilus. The correct command is:
```
gksu nautilus
```

---

### Post by 5BallJuggler on 2009-11-06
> **Paqman said:**
> You should never use sudo with a GUI app like Nautilus. The correct command is:
```
gksu nautilus
```

I've just learned something, although i'm not sure why, is it becasue you can delete what you like?

---

### Post by listerdl on 2009-11-06
Thanks!

BTW, I did the following: henry@DELL-laptop:~$ audacious %U

amidi-plug(amidi-plug.c:amidiplug_init:97): init, read configuration
amidi-plug(i_backend.c:i_backend_load:107): loading backend '/usr/lib/audacious/Input/amidi-plug/ap-alsa.so'
amidi-plug(i_backend.c:i_backend_load:145): backend /usr/lib/audacious/Input/amidi-plug/ap-alsa.so (name 'alsa') successfully loaded
Segmentation fault

---------

There appears to be a 'segmentation fault...' any idea how to repair that - since that is clearly the problem here right?

Thanks ;)

---

### Post by CJ Master on 2009-11-06
> **5BallJuggler said:**
> I've just learned something, although i'm not sure why, is it becasue you can delete what you like?

It can mess up temporary files, and it's generally considered a good practice anyway.

---

### Post by listerdl on 2009-11-06
THANKS - that has solved that problem but created another.

The volume doesn't work at all. I receive this message:

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plug-ins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

ARGH. Solve one problem and another comes over...any ideas...thanks ;)

---

### Post by Paqman on 2009-11-07
> **5BallJuggler said:**
> I've just learned something, although i'm not sure why, is it becasue you can delete what you like?

There's a good explanation on [Psychocats]("http://www.psychocats.net/ubuntu/graphicalsudo"). In short, it's because you end up using the wrong user profile.

---

