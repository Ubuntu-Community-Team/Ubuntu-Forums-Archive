---
title: "Executing a Shells Script on Startup/Boot"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by kevinharper on 2011-05-06
I had [an issue]("http://ubuntuforums.org/showthread.php?t=1747668") that required me to write up a script and execute it when the computer booted up.

Being that I am fairly new to shell scripting and had never created one that would be automatically executed, my first instinct was to create a .sh file and save it in my home folder. I then went to System > Preferences > Startup Applications and added the .sh script to the list (the file was already executable).

To my surprise, it did not execute when I rebooted. Why? I was under the impression that adding it as a startup app, the OS would simply launch it from the location I had specified.

---

### Post by wigout on 2011-05-07
This post seems to address your issue, albeit on an earlier incarnation of Ubuntu:
[http://ubuntuforums.org/showthread.php?t=610476](http://ubuntuforums.org/showthread.php?t=610476)

Here's the highlights:
> Quote:
                                                                      Originally Posted by **avik**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=3754875#post3754875")                 
                 *Go to System->Preferences->Sessions.  Add your script to the startup programs.*
                                 
Do this if you mean to run the script every time you log in.

If you want to make it run once during system startup, and not when you  log out and log in again, call your script from /etc/rc.local. This is a  file that is run during boot time after all requisite initialization is  complete.

---

