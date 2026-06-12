---
title: "Ubuntu boots up in terminal instead of gnome desktop"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by jlsm on 2010-10-23
Hello guys.

I'm a beginner with Ubuntu and linux.

I've installed 10.10 Maverick on my Lenovo 3000 G430 and so far I had almost everything configured except the brightness adjustment setting for the LCD. I followed some instructions I found on the forums and restarted. Now selecting default from Grub2, ubuntu doesn't boot to gnome desktop, instead it boots in text mode (asking for login and password and showing tty1). I tried startx as I found on another thread, but it returned a few errors.

(Following is not the actual error screen returned, but error messages are exactly as shown)

open /dev/fb0: No such file or directory
intel(0): No kernel modesetting driver detected
Screen(s) found, but none have a usable configuration

Fatal server error:
no screens found

ddxSigGiveUp: Closing log
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): Server error


When I boot in failsafe mode (recovery mode), I can get to GUI mode and when I select Restart X in the options, I can get to the desktop.

Hope someone could help me to put my Ubuntu back in order. I can re-install Ubuntu, since I still don't have that much files on it, but I really want to learn Ubuntu, and I believe that fixing this problem is a good start to learning it.

Thanks much in advance.


jlsm

---

### Post by flxdms on 2010-10-23
Have you tried switching manually to the GUI by pressing alt + ctrl + F7 (or F8 ) when you see the console?

---

### Post by nzadLithium on 2010-10-23
Which instructions did you follow?

---

### Post by noorez on 2010-10-23
Try running 'startx' at the terminal to try and start the x server manually. What is the result?

---

### Post by garvinrick4 on 2010-10-24
Make sure these two say state installed:If not install it and reboot.
```
aptitude show gdm
``````
aptitude show xorg
``````
 sudo apt-get install (package name)
```

---

### Post by Crusty Old Fart on 2010-10-24
[FONT=sans-serif]Howdy jlsm:
        
        Let's look at the following line of your error screen:
        
        intel(0): No kernel modesetting driver detected
        
        It suggests to me that your operating system doesn't contain a         driver for your graphics adapter card for which kernel         modesetting (KMS) can be used. KMS is enabled by default in your         OS but only works for certain drivers. For drivers that are not         yet compatible with kernel modesetting you will need to use X.         Fortunately, if the system finds an X configuration file where         it is supposed to be, it will attempt to use it instead of KMS.
        
        I see two problems that you're running into:
[/FONT]
[LIST=1]
[*][FONT=sans-serif] You're missing an X configuration file. That's because it         doesn't exist by default anymore. You have to make it.[/FONT]
[*][FONT=sans-serif] You're issuing old commands, like: startx, which are no longer         valid X commands for your OS.[/FONT]
[/LIST]
[FONT=sans-serif]         
        So, let's start from the tty1 screen that is available to you         immediately after boot.
        
        Log in with your username and password at the prompts.
        
        For the next steps, we need to make sure that X and gnome aren't         running. If they are running, then the following command will         stop them. If they are not running, then the following command will         tell you it can't stop them because they aren't running anyway         and no harm will be done. So, issue the following command:
        ```
[FONT=sans-serif]sudo service gdm stop[/FONT]
```        Now we are sure that X isn't running.
        
        You can now have the system automatically generate a         configuration file for X using the following command:
        ```
[FONT=sans-serif]sudo X -configure[/FONT]
```        This will create a file in your home directory (~) named:         xorg.conf.new
        
        This file needs to be copied into /etc/X11 as: xorg.conf
        You do this with the following command:
        ```
[FONT=sans-serif]sudo cp ~/xorg.conf.new /etc/X11/xorg.conf[/FONT]
```        That should take care of the first problem.
        
        Now, to start X/gdm you need to issue the following command:
        ```
[FONT=sans-serif]sudo service gdm start[/FONT]
```        You should now be presented with a GUI login screen. This screen         should also be served up on every subsequent boot now that you         have an xorg.conf file in: /etc/X11
        
        You also still have the file xorg.conf.new file in your home (~)         directory. If you need to make changes to your x configuration,         you can edit that file, copy it to /etc/X11/xorg.conf and then reboot.
  
_Here are some notes for you regarding the new ways of restarting X:_
        
        You can restart X by dropping back down into a virtual shell by         pressing: Ctrl+Alt+F1 logging in again and issuing the following commands:
```
[FONT=sans-serif]sudo service gdm stop
sudo service gdm start[/FONT]
```If you do that you'll need to login again to the GUI that is presented, as you did earlier.
  
But...There is another way to restart X without having to drop back into  a virtual shell. It can be done by pressing Ctrl+Alt+Backspace. But  that key combination is disabled by default in your OS. You'll need to  enable it before you can use it.
  
_Here's how to enable Ctrl+Alt+Backspace:_
[/FONT]
[LIST=1]
[*][FONT=sans-serif]On your main menu in the upper left corner of your screen, click: System-->Preferences-->Keyboard[/FONT]
[*][FONT=sans-serif]Click on the "Layouts" tab, and then on the "Options..." button.[/FONT]
[*][FONT=sans-serif]Click on the list item: Key sequence to kill the X server[/FONT]
[*][FONT=sans-serif]Check the box to the left of: Control + Alt + Backspace[/FONT]
[*][FONT=sans-serif]Click the Close button on this window and then again on the one behind it.[/FONT]
[/LIST]
[FONT=sans-serif]That's it. Now you can use Ctrl+Alt+Backspace from your desktop GUI to restart X.
  
If you have problems with this, you may need to disable KMS for your driver. I'll wait for you to post back before writing up those instructions as they may not be needed.
[/FONT]

---

### Post by pmurk on 2010-10-25
With the above line I was able to create a xorg.conf which looks fine according to my knowledge.

I still kept geting "intel(0): no kernel modesetting driver detected" and 
checked /etc/default/grub and found
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"
deletion of nomodeset (which came from experiments for screen brightness, 
ran sudo update-grub and things are fine.

---

### Post by anewguy on 2010-10-25
EDIT:  Removed previous info I had here as it was incorrect and I don't want another reader to be mislead in this instance.  Please ignore this.  Just saw your post right above this one - I guess I miss read it.  I see that the process you went through put nomodeset on your boot line, and that was causing the problems.  Sorry I didn't read that correctly.

Dave ;)

---

### Post by jlsm on 2010-10-25
Thanks to everyone who took the time to read on my problem and give their inputs. I'll have to restart again to test all your suggestions, then I'll post back what I find.

jlsm

---

### Post by jlsm on 2010-10-25
Back...

-> flxdms, no go on the alt-ctrl-F7 (F8), still in text mode when I press those key combos.

-> nzadLithium, the last suggestion I followed before I experienced this problem was to install the xserver-xorg-video-intel-dbg in the synaptic package manager. Please note that when I installed that package, Ubuntu some other software updates as well. Not sure if there were some kind of conflict, or if it was just coincidence.

-> noorez, the error messages I listed in my first post were errors returned by launching startx from the prompt.

-> garvinrick4, upon typing the commands you suggested, the screen returned was

The program 'aptitude' can be found in the following packages:
  * aptitude
  * aptitude-gtk

Shall I try to install these packages also?

-> Crusty, I followed your suggestions up to 'sudo service gdm start' and restarted, it still dropped me onto text terminal. I did 'sudo service gdm stop' and then 'sudo X -configure', then tried to test the new config by using

sudo X -config /home/jlsm/xorg.conf.new

and it showed the exact same errors as when I ran 'startx'


I'm very grateful for the time you all are putting to help me with this problem. I will be waiting for your additional suggestions to fix this.

Thanks all.


jlsm

---

### Post by jlsm on 2010-10-26
Hiya all,

Problem solved. Thanks goes to pmurk for the solution he provided. I am now able to boot directly to gnome desktop. Well, my apologies to him also because I tried his solution last. I didn't think much of it because I put the nomodeset entry in that line for about 2 weeks now, and I didn't experience any problems until three days ago.

Well, I'm happy that my Ubuntu is working again (except for that brightness adjustment thorn).

Again, thanks so much to all who pitched in and gave their suggestions.


jlsm

---

