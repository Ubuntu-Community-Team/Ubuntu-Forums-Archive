---
title: "no gui ubuntu 9.04"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by badtazz72 on 2009-05-27
i installed ubuntu 9.04 and it worked well and then i whent to advanced desk top effects it downloaded driver i rebooted and all i have now is a .no resume image,doing normal boot.
i searched google for a fix and im starting to get discouraged.
i have nvidia 8600 gt and a 3.16 gb intell dual core.

---

### Post by overdrank on 2009-05-27
> **badtazz72 said:**
> i installed ubuntu 9.04 and it worked well and then i whent to advanced desk top effects it downloaded driver i rebooted and all i have now is a .no resume image,doing normal boot.
i searched google for a fix and im starting to get discouraged.
i have nvidia 8600 gt and a 3.16 gb intell dual core.

Hi and welcome, have you tried to boot into recovery mode and use xfix to correct the graphical issues?
Recovery mode is usually the second choice from the grub when booting.
Move to  Absolute Beginner Talk

---

### Post by badtazz72 on 2009-05-27
> **overdrank said:**
> Hi and welcome, have you tried to boot into recovery mode and use xfix to correct the graphical issues?
Recovery mode is usually the second choice from the grub when booting.
Move to  Absolute Beginner Talk






yes and still no fix

---

### Post by Paul41 on 2009-05-27
Try running the following from the command line and then answer the questions it takes you through to see if it fixes it (if you are unsure of the answer you can usually pick the default).

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by badtazz72 on 2009-05-27
> **Paul41 said:**
> Try running the following from the command line and then answer the questions it takes you through to see if it fixes it (if you are unsure of the answer you can usually pick the default).

```
sudo dpkg-reconfigure xserver-xorg
```





im reinstalling right now is there any thing special i should do before i let it put driver in?
:(

---

### Post by Paul41 on 2009-05-27
No, it should take care of everything for you.

---

### Post by badtazz72 on 2009-05-27
> **Paul41 said:**
> No, it should take care of everything for you.


do i put 173 or 180 nvdia driver?

---

### Post by badtazz72 on 2009-05-27
> **badtazz72 said:**
> im reinstalling right now is there any thing special i should do before i let it put driver in?
:(

it saysxsever-org not installed and no info is available:confused:

---

### Post by badtazz72 on 2009-05-27
says xsever is not installed

---

### Post by durand on 2009-05-27
> **badtazz72 said:**
> says xsever is not installed

Install the xserver-xorg package.
```
sudo aptitude install xserver-xorg
```

It might just be easier if you reinstalled.

---

### Post by badtazz72 on 2009-05-27
i did and every time it does this

---

### Post by durand on 2009-05-27
Erm, what do you do everytime? Next time, try to install the graphics driver from System > Administration > Hardware Drivers.

---

### Post by badtazz72 on 2009-05-27
i have this is my fourth time and it boots and says no resume image,doing normal boot

---

### Post by badtazz72 on 2009-05-27
did it still not working all i have is my name-dessktop:~$

---

### Post by Jive Turkey on 2009-05-27
"no resume image" seems to suggest that ubuntu is for some reason trying to resume from suspend or hibernate mode.  2 out of my 3 computers will not hibernate or suspend for ubuntu (they go down, but start up to black screen sometimes with cryptic error messages or just a blinking cursor, there is no fix except a hard reset and never to use hibernate or suspend again)

My suggestion:

Do a fresh install(again, sorry), then run these commands in a terminal (menu: Applications>Accessories>Terminal in case you didn't know)
```
sudo apt-get update
sudo apt-get dist-upgrade
```
reboot if prompted (make extra sure you are restarting and not hibernating/suspending)
Then go to System>Administration>Hardware Drivers
and try to install the 180 driver
reboot (again, make sure you are not suspending)
That might be more reliable for you.

---

### Post by Jive Turkey on 2009-05-27
> **badtazz72 said:**
> did it still not working all i have is my name-dessktop:~$

at the $ prompt, what happens if you type "startx" sans quotes, and press enter?

also try the command "sudo /etc/init.d/gdm restart" if startx doesn't get you into a gui environment.  Then try startx agian.

also, maybe first try holding down ctrl+alt and press F7  if that does nothing, do ctrl+alt+F8 and post any error messages that you find there.

---

### Post by badtazz72 on 2009-05-27
still no gui

---

### Post by badtazz72 on 2009-05-27
run ubuntu 8.04 and didnt have this problem

---

### Post by badtazz72 on 2009-05-27
sudo aptitude install xserver-xorg(this aptitude does not have super cow powers)

---

### Post by badtazz72 on 2009-05-27
this is driving me crazy

---

### Post by badtazz72 on 2009-05-27
can some one please help me

---

### Post by durand on 2009-05-27
In order for us to help you, you need to give more information than "still no gui". What error comes up?

---

### Post by sodainmay on 2009-05-27
mabe you can change the source and apt-get install again,or your dispaly drive doen't work

---

### Post by badtazz72 on 2009-05-27
unabel to connect to x sever

---

### Post by badtazz72 on 2009-05-27
no sreens found

---

### Post by xavierp94 on 2009-05-27
Have you tried disabling the problematic drivers? Do that if possible through recovery mode.

---

### Post by badtazz72 on 2009-05-27
all i have is a black sreen with desk top :~$_

---

### Post by xavierp94 on 2009-05-27
> **badtazz72 said:**
> all i have is a black sreen with desk top :~$_
So you are in the terminal right now. Am I right?

---

### Post by badtazz72 on 2009-05-27
i dont now i installed ubuntu 9.04 and let it install driver and now i have no gui
only comand promt

---

### Post by xavierp94 on 2009-05-27
> **badtazz72 said:**
> i dont now i installed ubuntu 9.04 and let it install driver and now i have no gui
only comand promt
Try typing in 
 startx

---

### Post by badtazz72 on 2009-05-27
> **xavierp94 said:**
> Try typing in 
 startx







no screen found 
no device found

---

### Post by badtazz72 on 2009-05-27
no such file or directory

---

### Post by xavierp94 on 2009-05-27
> **badtazz72 said:**
> no such file or directory
Try the following solutions:
> **spcwingo said:**
> Try this command:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```That reconfigures the xserver back to the default settings. After that, enter this command:

```
sudo /etc/init.d/gdm restart
```This restarts the Gnome Display Manager. You should now have your GUI back. At this point you should now go back to system>admin>hardware drivers and disable/uninstall the driver that didn't work. If you want, you can try installing envyng to install the graphics drivers...I had to do this to get my graphics card rolling. To install envyng just enter this command in a terminal:

```
sudo apt-get install envyng-core
```Now press CTRL+ALT+F1 to drop out of X.  Enter this command to run envyng:

```
envyng -t
```After that follow the on-screen instructions to install the driver for your card. Just reboot when prompted. Let us know if this get her going.
Link to thread:[http://ubuntuforums.org/showthread.php?t=1170391](http://ubuntuforums.org/showthread.php?t=1170391)

---

### Post by badtazz72 on 2009-05-27
says checking battery stat and has a blinking crosier

---

### Post by badtazz72 on 2009-05-27
still sitting blinking

---

### Post by badtazz72 on 2009-05-27
looks like it does it when  i install nvidia driver i un in stalled nvidia driver and got gui back

---

### Post by badtazz72 on 2009-05-27
this is crazy wy does it loose the gui when i install driver

---

### Post by badtazz72 on 2009-05-27
atal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log
xinit:  Server error.

---

### Post by badtazz72 on 2009-05-27
any body figure this out?:(

---

### Post by badtazz72 on 2009-05-27
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

---

### Post by badtazz72 on 2009-05-28
has any body got this gui problem figured out

---

### Post by Jive Turkey on 2009-05-29
> **badtazz72 said:**
> You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

I think you should do what it says, boot up to your black screen which hopefully gets you to a '~$' prompt which is where you are supposed to type:
```
sudo nvidia-xconfig
```
you should get prompted for a password and then it will hopefully configure your xorg.conf file correctly to use the driver.  
In the past we used to post our xorg.conf files for others to review and offer suggestions when we had problems like this but that practice has become less useful as the way xserver uses the file seems to change radically as the various packages evolve.  If you resort to that type of troubleshooting you should be sure to stick with jaunty 9.04 versions.

'sudo' is the preferred "as root" method for ubuntu.  
Most other linux OS's generally use another method which we are not allowed to discuss on the forums.

---

### Post by badtazz72 on 2009-05-30
i whent back to windows for now need my pc. i love linux but not they problems with nvidia
well see how it wrks out with next version:(

---

### Post by twocs on 2009-06-17
I think I can summarize the problem:

[LIST]
[*]The GUI works for the Live CD.
[*]The GUI worked when you installed the for the first time.
[*]When you tried to install the advanced desktop effects, it downloaded drivers and didn't work any more.
[*]You tried fixing x-server, but none of your efforts worked.
[/LIST]

So, it seems like you hadn't spent a long time using Ubuntu on that partition, so if it was me, I'd probably just cut my losses and reinstall 9.04.

You could then experiment with the advanced desktop effects using the Live CD first, so that we check the driver that gets downloaded is working for Ubuntu. It's really a good system, with many advantages especially for getting interested in programming. For example, setting up NetBeans is really simple, much better than Windows IMO.

---

### Post by badtazz72 on 2009-07-13
it works in 8.04lts i wold like to use 9.04 but my head is ready to crack

---

