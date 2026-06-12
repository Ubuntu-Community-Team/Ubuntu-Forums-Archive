---
title: "Totally new to Ubuntu - Problems on start up"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by Toronto11 on 2010-11-14
Good evening,

I'm totally new to Ubuntu and have just installed 10.04.  I can't get to the login screen, but have tried the recovery option.  I know from someone showing me on their computer what the terminal is etc., and that's all I can access, but I don't know the codes associated with taking the next step.

Please help.

---

### Post by Rave Gloves on 2010-11-14
When it boots up what is actually happening? is it a black screen with code? if so what dose the code say?

---

### Post by Paqman on 2010-11-14
What hardware are you installing it on? Have you definitely installed the desktop version and not the server version by mistake? What happens when you type this:
```
startx
```

---

### Post by drs305 on 2010-11-14
As Rave Gloves states, we need more information.

Four of the possibilities you might see are: grub, grub rescue, initramfs or just a black screen with a blinking cursor.

Did you see the Grub menu before it booted?

---

### Post by Toronto11 on 2010-11-14
I can't get to the login screen, there was just a big Ubuntu Logo so I restarted and when prompted I selected the recovery option and it lets me choose from options like free up disk space, etc. and then it lets me enter terminal commands, but I don't know which command to enter to get going.  My friend thinks it's the configuration files.

---

### Post by drs305 on 2010-11-14
You might want to try the recovery mode option dealing with video. In Maverick it's called failsafex, but whichever one references video.

If it boots properly, open a terminal (Applications, Accessories, Terminal) and run the following command. You will be asked for your password. Type your normal password and press ENTER. You won't see what you type.

```
sudo apt-get update && sudo apt-get upgrade
```

Try rebooting the same way (with the fail safe video if it still doesn't work). From the Desktop, look at System, Administration, Additional Drivers or Hardware Drivers. See if a driver for your video card is listed. If it is, install it.

---

### Post by Toronto11 on 2010-11-14
I tried the startx commend and it asks me for a password and then says my password is not valid.

Upon getting to the recovery mode I get the following message:
ClamAV Daemon clamd

and then 

Ubuntu 10.04.1 LTS Connell-desktop tty1

---

### Post by Toronto11 on 2010-11-14
I tried the recovery option mode for video and I got two error messages saying the config files could not be parsed.

---

### Post by Toronto11 on 2010-11-14
I'm in the tty kernel if I'm not mistaken, but ctrl + alt + f7 doesn't bring me to the proper GUI.  Is this an issue with config files or the xinput configuration?

Please help, I really want to stop using Windows.

---

### Post by drs305 on 2010-11-14
> **Toronto11 said:**
> I tried the startx commend and it asks me for a password and then says my password is not valid.

Upon getting to the recovery mode I get the following message:
ClamAV Daemon clamd

and then 

Ubuntu 10.04.1 LTS Connell-desktop tty1

Did you try entering your username and password at the "Connell-desktop tty1" prompt?

If you can't log in, it's often faster to reinstall than to continue troubleshooting. If the LiveCD boots to Desktop without any problems then your system should be compatible. 

You can wait for more responses but as thread responses grow the number of new responders generally decreases. If getting your system working in the shortest amount of time is your primary objective I would probably reinstall. 

If you have time and want to wait, add some new information to the thread in eight hours when a new group of 'helpers' will probably be online.

---

