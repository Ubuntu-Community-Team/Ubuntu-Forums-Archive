---
title: "I get &quot;terry@terry-oem:~$&quot; whe I boot up, What happened to the desktop?"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by gillie4762 on 2011-02-10
I am a very newbee to all of this. I had issues when I installed UBUNTU but finally got it to run. Now when I boot into UBUNTU 10.10 I get "terry@terry-oem:~$ instead of a desktop. I have no idea where to go next. I have XP and 2 installs of UBUNTU on the drive. I had the desktop at one time.

---

### Post by searchfgold6789 on 2011-02-10
Try typing: ```
sudo /etc/init.d/gdm start
```
PS - It is probably not a good idea to put your FB link in your signature. Just saying ;)

---

### Post by gillie4762 on 2011-02-10
Facebook gone.  I entered the line and get a message about running scripts can use utilities(8) start.
I entered almost every combinations of utilities, start, upstart ane ended up with job is already running.

---

### Post by tarps87 on 2011-02-10
Try
```
startx
```

Also please can you post the exact message that you see, I believe the usage of start has changed in later Ubuntus

---

### Post by gillie4762 on 2011-02-10
What I got:
(WW) warning, (EE) error, (NI) not implementated, (??) unknown
(--) log file: "/var/log.Xorg.0.log, time Thri Feb 10 10:39
      using config file "/etc/xii/xorg.conf
NVIDIA could not open device file/dev/NVIDIA0/I/O error
NVIDIA0 failed to initialize NVIDIV Graphice Device
NVIDIA0 please see common problems in README
NVIDIA0 for additional information
NVIDIA0 failed to initialize NVIDIA Graphice Device
Screens found, but none have a usable cofiguration
Fatel Server error
   No screens found
Please consult the X.org foundation support group for help
Please check log file at "/varlog/X.org.0.log
ddxSigGibeUp: closing log
giving up
x init no such file or directory unable to connect to server
xinit no such procesds server error
 
Thats all of it also the first time I saw a message like that

---

### Post by searchfgold6789 on 2011-02-10
Maybe the drivers for your video card are not installed correctly. Try typing:```
sudo aptitude install nvidia
```

---

### Post by tarps87 on 2011-02-10
> **searchfgold6789 said:**
> Maybe the drivers for your video card are not installed correctly. Try typing:```
sudo aptitude install nvidia
```

If this does not work you have probably installed the restricted/closed source version on the driver in which case I would suggest trying
```
sudo dpkg-reconfigure xserver-xorg
```
This should get you using the default driver

---

### Post by gillie4762 on 2011-02-10
with "sudo aptitude: command not found is the error message

---

### Post by gillie4762 on 2011-02-10
with "sudo aptitude install nvidia" error message sudo aptitude: command not found

---

### Post by gillie4762 on 2011-02-10
After i tried the suggestions, I got a fast look at the purple screen. i don't know how to shut down from the prompt so I have to use the power button to reboot. I also see the purple screen briefly has it shuts down

---

### Post by uRock on 2011-02-10
> **gillie4762 said:**
> After i tried the suggestions, I got a fast look at the purple screen. i don't know how to shut down from the prompt so I have to use the power button to reboot. I also see the purple screen briefly has it shuts down
Please use apt-get in place of aptitude. Aptitude is a thing of the past in Ubuntu.
```
sudo apt-get install nvidia
```

---

### Post by gillie4762 on 2011-02-10
E: unable to locate package nvidia

---

### Post by uRock on 2011-02-10
Try```
sudo apt-get install nvidia-common nvidia-current
```

---

### Post by gillie4762 on 2011-02-10
E: unable to locate nivida
E: unable to locate package current

---

### Post by howefield on 2011-02-10
> **gillie4762 said:**
> E: unable to locate nivida
E: unable to locate package current

Are you spelling it correctly ?

Try copy/pasting from uRocks post.

---

### Post by gillie4762 on 2011-02-10
nvidia-common is already the newest version
nvidia-current is already the newest version

---

### Post by gillie4762 on 2011-02-10
Forgot a line
0 upgraded, 0newly installed, 0 to remove and 9 not upgraded

---

### Post by searchfgold6789 on 2011-02-10
Try```
sudo apt-get update
``` beforehand.

---

### Post by uRock on 2011-02-10
> **searchfgold6789 said:**
> Try```
sudo apt-get update [COLOR=Red]&& sudo apt-get dist-upgrade[/COLOR]
``` beforehand.
Added to it. This may very well fix the problem.

---

### Post by gillie4762 on 2011-02-10
nothing changed. the screen fluttered as if it was going to start then reverted to the prompt

---

### Post by gillie4762 on 2011-02-10
E: could not open lock file /var/lib/dpkg/lock - open (13: permission denied)
E: unable to lock the administration directory (/var/lib/dpkg/),  are you root?

---

### Post by dargaud on 2011-02-10
Maybe you have another install going on at the same time. Reboot and try again? Also "sudo aptitude full-upgrade".

And for uRock about aptitude being a thing of the past, what replaces it? How do you do a "aptitude search" then ?

---

### Post by gillie4762 on 2011-02-10
I get the message sudo: aptitude: command not found.
there are two installs on this drive and both are acting the same way, I have no idea how to end either. I am getting ready to clean it all out and start over with only one install. To reboot I use the power off button on the computer.

---

### Post by uRock on 2011-02-10
> **dargaud said:**
> Maybe you have another install going on at the same time. Reboot and try again? Also "sudo aptitude full-upgrade".

And for uRock about aptitude being a thing of the past, what replaces it? How do you do a "aptitude search" then ?
Aptitude is not installed in Ubuntu by default. I have been using Ubuntu for two years now and have had no need for aptitude. Directing users to use a command that is not installed while they are trying to fix their system just creates more frustration when the command does not exist on the system. Yet you are telling the OP to use aptitude when previous posts makes it obvious that aptitude is not installed.

If you prefer aptitude, then by all means use it, but please keep in mind that it is not installed by default.

---

### Post by uRock on 2011-02-10
> **gillie4762 said:**
> I get the message sudo: aptitude: command not found.
there are two installs on this drive and both are acting the same way, I have no idea how to end either. I am getting ready to clean it all out and start over with only one install. To reboot I use the power off button on the computer.
**sudo poweroff** will shut the system down and **sudo reboot** will restart the system.

Have you tried using the restore kernel and selecting to repair the system?

---

### Post by gillie4762 on 2011-02-10
I did once, that was long ago I will try again. Thanks for the commands. Part of my problems is I am way to new with UBUNTU to be fighting thid battle. I did remember that after i did the update is when this all started. it was the same with both installs. I did the install update and lost the graphic presentation.

---

### Post by uRock on 2011-02-10
If you select the second newest kernel does the problem still happen? This happens sometimes, so hopefully the older kernel will work and if it does, then you easily uninstall the newest kernel or just alter grub to boot the older kernel when you boot the system.

---

### Post by gillie4762 on 2011-02-10
I completed the repair and rebooted everything is the same.

---

### Post by gillie4762 on 2011-02-10
I did the samw with the second install and the results were the same. I'm taking abreak for dinner and erands.

---

