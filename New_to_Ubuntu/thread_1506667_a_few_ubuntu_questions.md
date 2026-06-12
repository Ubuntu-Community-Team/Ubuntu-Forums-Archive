---
title: "a few ubuntu questions"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by 29732 on 2010-06-10
Please see last post

---

### Post by TheForumTroll on 2010-06-10
I haven't tested it but [this]("http://email.about.com/od/yahoomailtips/qt/Access_Your_Yahoo_Mail_Account_with_Your_Email_Program.htm") might help.

As for number two: It is just a way to boot with an older kernel should the new one not work with your setup. As more are added the older ones will be removed.

If you want to learn more theres lots of guides. Is it something specific you want to learn? Maybe a specific area like the commandline or something else?

---

### Post by 29732 on 2010-06-12
please read the update (first message)

and how can you open up the equivalent of task manager on ubuntu?

---

### Post by Darkness Des on 2010-06-13
Alt+F2 to open the run dialog, then type in gnome-system-monitor and that'll pull up that task manager, and I find everything runs better with more RAM, a larger SWAP file, and fewer programs running. To remove a program completely, I suggest using aptitude (command line) to install them and then purge them. It recognizes orphaned packages and will remove them. Converting an RPM file is real easy. 
```
sudo aptitude install alien
alien -k name_of.rpm
```
The -k option has it keep the version number, otherwise it appends a 1 to the end of it.

---

### Post by xsinsx on 2010-06-13
Far as the task manager goes -- go to the terminal and you can list all the process with this 
```
 ps -A 
```

that will list all the processes that are running and from there you can use the process id the number associated with the process to kill it with the kill command
NOTE: THIS IS NOT A FULL PROCESS LIST I CUT ALOT OUT TO SAVE SPACE.
```
  

[steve@Fedora-box ~]$ ps -A
  PID TTY          TIME CMD
9442 ?        00:00:00 httpd
 9635 ?        00:00:00 file-roller
10135 ?        00:00:00 sshd
11109 ?        00:00:00 flush-253:0
11114 ?        00:00:00 sshd
11118 ?        00:00:00 sshd
11119 pts/0    00:00:00 bash
11139 pts/0    00:00:00 ps

```

lets say i wanted to stop the httpd process which is a Web server. i would simply. 
```

[steve@fedora-box~]$ kill 9442 

[steve@Fedora-box ~]$ ps -A
  PID TTY          TIME CMD
 9635 ?        00:00:00 file-roller
10135 ?        00:00:00 sshd
11109 ?        00:00:00 flush-253:0
11114 ?        00:00:00 sshd
11118 ?        00:00:00 sshd
11119 pts/0    00:00:00 bash
11139 pts/0    00:00:00 ps

``` 

This would be the same thing far as what the task manager does. 
At least I think this is what your looking for.

---

### Post by 29732 on 2010-06-13
okay, a bit of a problem..

i've used alien and it kept showing me error messages when i converted .i386.rpm files

now, it may not be so in simply .rpm (although i've never tried that) but i didn't use the program since

and for the task manager....

i'm currently running 2 mozilla firefoxes and all it shows me is this:

ivan@oldmanriver-laptop:~$ ps -a
  PID TTY          TIME CMD
 1975 pts/0    00:00:00 ps
 
is that normal?

---

### Post by 29732 on 2010-06-13
> **Darkness Des said:**
> Alt+F2 to open the run dialog, then type in gnome-system-monitor and that'll pull up that task manager

yeah, i've just tried that  and it does do what i want it to but this process:

vino-server

hogged up all my cpu and that caused my firefox to crash
i could not end the process strangely enough 
i've had the remote access thingy disabled, but it still was running
i had to restart the computer to kill it and now it isn't running
any suggestions?

---

### Post by xsinsx on 2010-06-13
> **29732 said:**
> 

and for the task manager....

i'm currently running 2 mozilla firefoxes and all it shows me is this:

ivan@oldmanriver-laptop:~$ ps -a
  PID TTY          TIME CMD
 1975 pts/0    00:00:00 ps
 
is that normal?

Make sure the Flag on the command is a capital A.

According to the manual for ps command:
```


   -A      Display information about other users' processes, including those
             without controlling terminals.

     -a      Display information about other users' processes as well as your
             own.  This will skip any processes which do not have a control-
             ling terminal, unless the -x option is also specified.
```

so change the lowercase -a to -A or add the -x option. so

```
 ps -ax
```

or 

```
 ps -A
```

to learn more about the process command read its manual by typing

```
 man ps 
```

---

### Post by 29732 on 2010-06-13
okay, i see 

this is my result:

 1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 cpuset
   12 ?        00:00:00 khelper
   13 ?        00:00:00 netns
   14 ?        00:00:00 async/mgr
   15 ?        00:00:00 pm
   17 ?        00:00:00 sync_supers
   18 ?        00:00:00 bdi-default
   19 ?        00:00:00 kintegrityd/0
   20 ?        00:00:00 kintegrityd/1
   21 ?        00:00:00 kblockd/0
   22 ?        00:00:00 kblockd/1
   23 ?        00:00:00 kacpid
   24 ?        00:00:00 kacpi_notify
   25 ?        00:00:00 kacpi_hotplug
   26 ?        00:00:00 ata/0
   27 ?        00:00:00 ata/1
   28 ?        00:00:00 ata_aux
   29 ?        00:00:00 ksuspend_usbd
   30 ?        00:00:00 khubd
   31 ?        00:00:00 kseriod
   32 ?        00:00:00 kmmcd
   35 ?        00:00:00 khungtaskd
   36 ?        00:00:00 kswapd0
   37 ?        00:00:00 ksmd
   38 ?        00:00:00 aio/0
   39 ?        00:00:00 aio/1
   40 ?        00:00:00 ecryptfs-kthrea
   41 ?        00:00:00 crypto/0
   42 ?        00:00:00 crypto/1
   55 ?        00:00:00 kstriped
   56 ?        00:00:00 kmpathd/0
   57 ?        00:00:00 kmpathd/1
   58 ?        00:00:00 kmpath_handlerd
   59 ?        00:00:00 ksnapd
   60 ?        00:00:00 kondemand/0
   61 ?        00:00:00 kondemand/1
   62 ?        00:00:00 kconservative/0
   63 ?        00:00:00 kconservative/1
  293 ?        00:00:00 khpsbpkt
  294 ?        00:00:00 scsi_eh_0
  295 ?        00:00:02 scsi_eh_1
  296 ?        00:00:00 scsi_eh_2
  297 ?        00:00:00 scsi_eh_3
  298 ?        00:00:00 scsi_eh_4
  299 ?        00:00:00 scsi_eh_5
  304 ?        00:00:00 knodemgrd_0
  334 ?        00:00:00 jbd2/sda5-8
  335 ?        00:00:00 ext4-dio-unwrit
  336 ?        00:00:00 ext4-dio-unwrit
  370 ?        00:00:00 flush-8:0
  397 ?        00:00:00 upstart-udev-br
  399 ?        00:00:00 udevd
  700 ?        00:00:00 kpsmoused
  701 ?        00:00:00 kmemstick
  702 ?        00:00:00 bluetooth
  734 ?        00:00:00 mmcqd
  748 ?        00:00:02 iwlagn
  750 ?        00:00:01 phy0
  825 ?        00:00:00 hd-audio0
  869 ?        00:00:00 rsyslogd
  875 ?        00:00:01 dbus-daemon
  891 ?        00:00:00 NetworkManager
  892 ?        00:00:26 gdm-binary
  904 ?        00:00:00 modem-manager
  905 ?        00:00:00 avahi-daemon
  907 ?        00:00:00 avahi-daemon
  936 ?        00:00:00 console-kit-dae
 1010 ?        00:00:00 gdm-simple-slav
 1033 tty4     00:00:00 getty
 1056 tty5     00:00:00 getty
 1061 tty2     00:00:00 getty
 1062 tty3     00:00:00 getty
 1065 ?        00:00:00 wpa_supplicant
 1066 tty6     00:00:00 getty
 1072 ?        00:00:00 acpid
 1080 ?        00:00:00 cron
 1081 ?        00:00:00 atd
 1086 ?        00:00:00 winbindd
 1099 ?        00:00:00 bluetoothd
 1111 ?        00:00:00 winbindd
 1141 ?        00:00:00 cupsd
 1156 ?        00:00:00 krfcommd
 1228 tty7     00:34:03 Xorg
 1251 tty1     00:00:00 getty
 1258 ?        00:00:00 gdm-session-wor
 1267 ?        00:00:00 gnome-session
 1301 ?        00:00:00 ssh-agent
 1304 ?        00:00:00 dbus-launch
 1305 ?        00:00:00 dbus-daemon
 1308 ?        00:00:03 gconfd-2
 1313 ?        00:00:00 gnome-keyring-d
 1317 ?        00:00:44 gnome-settings-
 1319 ?        00:00:00 gvfsd
 1324 ?        00:00:00 gvfs-fuse-daemo
 1334 ?        00:00:00 polkit-gnome-au
 1336 ?        00:03:37 pulseaudio
 1337 ?        00:00:01 nm-applet
 1340 ?        00:00:58 gnome-panel
 1341 ?        00:00:00 rtkit-daemon
 1342 ?        00:06:40 compiz
 1345 ?        00:00:59 nautilus
 1350 ?        00:00:00 gnome-power-man
 1351 ?        00:00:00 bluetooth-apple
 1352 ?        00:00:00 polkitd
 1366 ?        00:00:00 upowerd
 1369 ?        00:00:00 gvfsd-trash
 1373 ?        00:00:00 bonobo-activati
 1393 ?        00:00:00 gvfs-gdu-volume
 1404 ?        00:00:04 wnck-applet
 1408 ?        00:00:00 trashapplet
 1412 ?        00:00:00 udisks-daemon
 1415 ?        00:00:00 udisks-daemon
 1422 ?        00:00:00 hald
 1423 ?        00:00:00 hald-runner
 1457 ?        00:00:00 sh
 1458 ?        00:00:02 gtk-window-deco
 1461 ?        00:00:00 gvfs-gphoto2-vo
 1464 ?        00:00:00 gvfs-afc-volume
 1466 ?        00:00:00 hald-addon-inpu
 1467 ?        00:00:00 gconf-helper
 1474 ?        00:00:00 hald-addon-rfki
 1475 ?        00:00:00 hald-addon-leds
 1485 ?        00:00:00 hald-addon-gene
 1488 ?        00:00:00 hald-addon-cpuf
 1489 ?        00:00:00 hald-addon-acpi
 1496 ?        00:00:00 hald-addon-stor
 1501 ?        00:00:00 indicator-apple
 1502 ?        00:00:00 notification-ar
 1503 ?        00:00:00 clock-applet
 1504 ?        00:00:00 indicator-apple
 1510 ?        00:00:02 syndaemon
 1512 ?        00:00:00 gvfsd-burn
 1518 ?        00:00:00 gvfsd-metadata
 1520 ?        00:00:00 indicator-appli
 1522 ?        00:00:00 indicator-messa
 1532 ?        00:00:00 indicator-sound
 1537 ?        00:00:00 indicator-sessi
 1539 ?        00:00:32 indicator-me-se
 1547 ?        00:00:01 notify-osd
 1550 ?        00:00:00 dhclient
 1554 ?        00:00:00 gnome-screensav
 1631 ?        00:00:00 gdu-notificatio
 1672 ?        00:00:00 python
 1692 ?        00:00:00 update-notifier
 1697 ?        00:00:00 system-service-
 2026 ?        00:00:00 udevd
 2027 ?        00:00:00 udevd
 2360 ?        00:00:00 gvfsd-computer
 2465 ?        00:00:09 skype
 2823 ?        00:00:00 firefox
 2828 ?        00:00:00 run-mozilla.sh
 2832 ?        00:20:14 firefox-bin
 3186 ?        00:00:00 gnome-terminal
 3187 ?        00:00:00 gnome-pty-helpe
 3188 pts/0    00:00:00 bash
 3207 pts/0    00:00:00 ps
 can you read that?:lolflag:
because i cant

---

### Post by 29732 on 2010-06-13
i think ill just stick with system monitor

---

### Post by cap10Ibraim on 2010-06-13
another similar thing to task manager processes try 
```
top
```then use kill PID_number 
to kill a process,PID_number from the PID column using top
q to quit

---

### Post by 29732 on 2010-06-13
Hmm, interesting, thanks

I'll use that 
and now what about those other questions?

---

### Post by cap10Ibraim on 2010-06-13
4-)...well do you check the computer janitor in the system->Administration ?

---

### Post by pythonscript on 2010-06-13
Open the Synaptic Package Manager, and under status, select the option that says (among other things) "Residual Config", select all, right click and select "Mark for Complete Removal." This should be done *after* you've already used the purge option (which does a decent job but needs this too) and once you apply, that should do what you're looking for in terms of totally removing a package.

---

### Post by 29732 on 2010-06-13
I do use computer janitor but it isn't really helpful for me....
And as for that program removal, thanks, I'll keep that in mind

Now what about that process "vino-server"

Is it a bug?

---

### Post by cap10Ibraim on 2010-06-13
> **29732 said:**
> I do use computer janitor but it isn't really helpful for me....
And as for that program removal, thanks, I'll keep that in mind

Now what about that process "vino-server"

Is it a bug?
how much is taking from the CPU ?
[http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html#more-15](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html#more-15)

---

### Post by 29732 on 2010-06-13
the time when it did, (but now it is not working anymore) it took around 95% of my cpu

---

### Post by xsinsx on 2010-06-13
well I can read it but I also am frequently checking things on my laptop... i understand whats going on... But yes if its not your cup of tea then go ahead and use what makes you happy :).

---

### Post by 29732 on 2010-06-13
lol

---

### Post by -kg- on 2010-06-13
> **29732 said:**
> I do use computer janitor but it isn't really helpful for me....
And as for that program removal, thanks, I'll keep that in mind

Now what about that process "vino-server"

Is it a bug?

Did you read at the link provided in cap10Ibraim's post?  Vino-server allows other computer users to view and/or control your desktop remotely.

I checked mine and everything is disabled.  Did you ever knowingly enable this feature?  Is it presently disabled (you ought to check now..."System/Preferences/Remote Desktop")?  Could someone else in your household have enabled it?

If the answer to most or all of the above is no, you might want to check out your installation.  Someone *might* have hacked in to your computer and gained access to your desktop (and thereby, your hard drives).

---

### Post by 29732 on 2010-06-13
yeah, i've disabled it and (almost) never used it 

so I think it is a bug or something

---

### Post by -kg- on 2010-06-13
> **29732 said:**
> the time when it did, (but now it is not working anymore) it took around 95% of my cpu 

> **29732 said:**
> yeah, i've disabled it and (almost) never used it 

so I think it is a bug or something

So are you still having problems with it, or did disabling it stop the problem?  If it stopped the problem, then it likely isn't a bug.

I don't know how much the process is supposed to use (95% processor usage sounds a bit excessive to me, but it might be normal), but if disabling the feature cured the problem, then it probably isn't a bug, as such.  At least, being disabled, it's not a bug that will have any effect on you in this aspect.

Vino and vinegre are listed in Synaptic and show in my installation as being installed.  I'm not sure whether you can safely uninstall them or not.  I know that uninstalling some packages (such as Evolution) can damage the installation.

---

### Post by 29732 on 2010-06-13
yeah, but i don't use them THAT often, but it isnt a problem anyway, so im not gonna bother uninstalling the package (or whatever) 

i still have a few more unanswered questions, ill list them in my next reply

---

### Post by 29732 on 2010-06-13
Is there a program or feature or tweak that can put different wallpapers on different workspaces?


A few more questions coming soon

---

### Post by TheForumTroll on 2010-06-14
Have [a look here]("http://lmgtfy.com/?q=ubuntu+different+wallpaper+on+each+desktop") ):P

Ask away if you get stuck or have more questions :)

---

### Post by 29732 on 2010-06-15
lol

i hate those things that do that

and btw, that was reeeeeeeeeeeaaaaaaaaaaaalllllllllyyyyyyyyyyyy helpful *sarcastically said*

---

### Post by 29732 on 2010-06-15
And, by the way, how can you change the amount of workspaces on ubuntu 

P.S I've googled it and i didn't get very good awnsers
P.S.S I've got the desktop wallpaper thingy to work (yay!)

---

### Post by cap10Ibraim on 2010-06-15
> **29732 said:**
> And, by the way, how can you change the amount of workspaces on ubuntu 

P.S I've googled it and i didn't get very good awnsers
P.S.S I've got the desktop wallpaper thingy to work (yay!)

right click on the workspace area -> preferences
if that's what you are asking for

---

### Post by 29732 on 2010-06-15
](*,)
WOW 
that was not smart of me...
thanks

---

### Post by 29732 on 2010-06-15
a few more questions coming soon!

---

### Post by 29732 on 2010-06-17
and now, my latest problem, 

when I close the laptop lid, it keeps running bu twhen I open it, it shows a blank screen , nothing else 
i pressed random buttons, but nothing worked

any solutions?
not to change the settings on what happens when i close the lid, but solve the "suspend" problem

---

### Post by cap10Ibraim on 2010-06-17
if you press ctrl+alt+f1 do you see a tty1 terminal ?

---

### Post by 29732 on 2010-06-17
yes, and i had ABSOLUTELY NO WAY TO GET OUT OF IT!!!!
WHY DID YOU TELL ME TO DO IT IN THE FIRST PLACE?!
I WAS WATCHING A VIDEO, FOR CRYING OUT LOUD!

---

### Post by cap10Ibraim on 2010-06-17
> **29732 said:**
> yes, and i had ABSOLUTELY NO WAY TO GET OUT OF IT!!!!
WHY DID YOU TELL ME TO DO IT IN THE FIRST PLACE?!
I WAS WATCHING A VIDEO, FOR CRYING OUT LOUD!

:guitar: 
I was asking you when the blank screen shows up by the way press 
ctrl+alt+f8 
to go back

---

### Post by 29732 on 2010-06-17
okay, ill try that

if it doesn't work, im blaming it all on you
:p

---

### Post by cap10Ibraim on 2010-06-17
if f8 didn't work ctrl+alt+f7 
to go back to the gui

---

### Post by 29732 on 2010-06-17
"gui"?

---

### Post by 29732 on 2010-06-17
"guided user interface" maybe?
:lolflag:

---

### Post by cap10Ibraim on 2010-06-17
Yes multitasking you have all these sessions from 1 to 8 
just try them 
ctrl+alt+f1 ... ctrl+alt+f8 
they are terminals except the last one which you are using right now 
so 
when you face the blank screen try 
ctrl+alt+f8 directly 
or ctrl+alt+f1  then ctrl+alt+f8

---

### Post by 29732 on 2010-06-17
lol
but there isnt anything to "guide" me

XD

---

### Post by 29732 on 2010-06-17
and now for my other concern...
what is /dev/null and when i start ubuntu, it occasionally shows an error message showing that it cant open it, no such file or directory?
it boots normally even with the error message, but what does it mean?

---

### Post by 29732 on 2010-06-17
oh, and the suspend problem was fixed, thanks to cap10Ibraim
when I open the lid, it automatically starts, no hotkeys required
thanks

---

### Post by 29732 on 2010-06-18
NOTE: i've googled it and it shows me that is an unfixable bug, so never mind, i dont care about that problem THAT much 

but anyway..
noone thought of a good ubuntu tip?

---

### Post by cap10Ibraim on 2010-06-18
check this out 
[http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html](http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html)
It worked with me

---

### Post by 29732 on 2010-07-03
UPDATE:

More questions for everyone:

1. Is there a program that is as good ( or better ) than Winamp?
2. Is there a way to find out if your fingerprint reader is compatible with Ubuntu
3. Is there a faster .mkv decoder?
and finally:
4. I have already 3 ubuntu generic images on GRUB, and it is becoming annoying. Can I remove them somehow?

---

### Post by 29732 on 2010-07-04
5. how can i install my wireless printer?
6. are there shortcuts for copy and paste?
7. can i make shortcuts?

---

### Post by 29732 on 2010-07-04
8. How can I remove older linux images from BURG
9. How do I remove entries from BURG

And please see post 46 and 45

---

### Post by 29732 on 2010-07-05
10. How can I make Ubuntu easier for me?
11. Are there any useful terminal commands?

And please see post 47

---

### Post by 29732 on 2010-07-05
[size=7]please!!!!!
Someone answer me!!!
[/size]

---

