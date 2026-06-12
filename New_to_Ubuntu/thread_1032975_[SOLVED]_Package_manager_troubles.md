---
title: "[SOLVED] Package manager troubles"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by childofGod on 2009-01-06
I've got no use of add/remove applications, synaptic and update manager ever since I installed k9copy on my system.  They start up, ask for my password and then freeze halfway while building dependencies.  I am using a gnome based (ubuntu); not a kde based system (kubuntu).  Could that have anything to do with it?  I figured I would just uninstall k9copy and be all right, but none of the ways I know how to do it work anymore.  I'm quite the noob and don't know my way around the command line much at all.  Someone please help!:confused:

---

### Post by TCSnyder on 2009-01-06
well the only problems i have had with a package manager is it not installing a package all the way. try running synaptic from the command line and check th output and paste it here.

you can try 
```
dpkg --configure -a

```

this will fix any packages if it stopped during the install.

---

### Post by childofGod on 2009-01-06
Here it is:

dpkg: requested operation requires superuser privilege
paul@bigdaddy:~$ sudo dpkg --configure -a
[sudo] password for paul: 
paul@bigdaddy:~$ 

Does this help?

---

### Post by TCSnyder on 2009-01-06
try running synaptic from the terminal
```
synaptic
```

what is that output?

---

### Post by childofGod on 2009-01-06
Same as when I try to run it from the System/Administration drop down menu-- the dependency tree builds halway and then it doesn't go any further.

---

### Post by bodhi.zazen on 2009-01-06
No, you can run kde apps on gnome without any problem.

try

```
sudo apt-get update
```

and if you get no error messages

```
sudo apt-get dist-upgrade
```

If that works run

```
gksu synaptic
```

Post any error messages.

---

### Post by childofGod on 2009-01-06
Got the following errors after apt-get update:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

What next?  Also, what does the gksu command do if I get that far?

---

### Post by TCSnyder on 2009-01-06
apt-get has to be run as root. use sudo

it could also be that another package manager is open. you can try 
```
killall synaptic
``` 
that will end any synaptic processes

---

### Post by childofGod on 2009-01-06
I did.

---

### Post by TCSnyder on 2009-01-06
you can always try restarting your computer. ( sometimes you will be surprised what that fixes)

---

### Post by childofGod on 2009-01-06
I did that about ten times before posting

---

### Post by TCSnyder on 2009-01-06
i am sorry it out of my league.

---

### Post by childofGod on 2009-01-06
Tyhanks for trying anyhow, TC.

---

### Post by 2hot6ft2 on 2009-01-06
> **TCSnyder said:**
> well the only problems i have had with a package manager is it not installing a package all the way. try running synaptic from the command line and check th output and paste it here.

you can try 
```
dpkg --configure -a

```

this will fix any packages if it stopped during the install.
Well this should have been run with sudo so
```
sudo dpkg --configure -a
```

But first is update manager showing in the top right on the taskbar it will either be a round orange icon, a red triangle or a red down arrow?
If it is single left click on it and it will start. Get the updates and it will go away.

---

### Post by childofGod on 2009-01-06
Hey 2hot, how you doing?  I knew to use sudo with dpkg so that was no issue.  As for the update icons in the top right corner, no they aren't there even when they should be.

---

### Post by 2hot6ft2 on 2009-01-06
> **childofGod said:**
> Hey 2hot, how you doing?  I knew to use sudo with dpkg so that was no issue.  As for the update icons in the top right corner, no they aren't there even when they should be.
Pretty good. I would ask but I see you're having a time of it.

So I take it you've already tried all the usual.
```
sudo apt-get update
sudo apt-get autoremove
sudo apt-get upgrade
```
And the problem is that something has a lock on the installer right?
How about
```
sudo apt-get reinstall update-manager
```
I don't suppose that would work either if it's locked.
So how about
```
sudo killall update-manager
``` first?

---

### Post by childofGod on 2009-01-07
"Curiouser and curiouser", said Alice.

paul@bigdaddy:~$ sudo killall update-manager
[sudo] password for paul: 
Sorry, try again.
[sudo] password for paul: 
update-manager: no process killed

What next?

---

### Post by 2hot6ft2 on 2009-01-07
Have you tried
```
top
```
and look to see if you can figure out what package manager is running?

---

### Post by 2hot6ft2 on 2009-01-07
You already said that you've rebooted several times. Restart, Ctrl+Alt+Backspace, or shut down and started from a cold boot?

If you haven't already tried I would do a full shut down and restart, If you have then nevermind.

---

### Post by childofGod on 2009-01-07
I'm not sure how to read the table generated by running "top", but it appears that the majority of my cpu's time is being used by synaptic even though I am not actually controlling it.  Is this possible?

---

### Post by 2hot6ft2 on 2009-01-07
Apparently it is. So maybe
```
sudo killall synaptic
```
Thought I already saw that though. Back at post 8 I think it was.

---

### Post by childofGod on 2009-01-07
OK, I did what you said and here's what I got:

paul@bigdaddy:~$ sudo killall synaptic
[sudo] password for paul: 
paul@bigdaddy:~$ 

Did it work?

---

### Post by 2hot6ft2 on 2009-01-07
Looks like it did.
Now try
```
sudo dpkg --configure -a
```

---

### Post by childofGod on 2009-01-07
Here's what I get:

paul@bigdaddy:~$ sudo dpkg --configure -a
paul@bigdaddy:~$ 

Did that do what it was supposed to do?

---

### Post by 2hot6ft2 on 2009-01-07
Yes, anytime it doesn't give any info to say there was an error in trying to complete the command means it succeeded.
Now
```
sudo apt-get update
sudo apt-get autoremove
sudo apt-get update
```
And yes the update twice both before and after the autoremove

---

### Post by 2hot6ft2 on 2009-01-07
I think this is why synaptic was running in the background.
> **TCSnyder said:**
> try running synaptic from the terminal
```
synaptic
```

what is that output?
For one synaptic is a gui app so it should have been ```
gksudo synaptic
```
and that's why it didn't show up. Sometimes you can get away with it but not always.

---

### Post by childofGod on 2009-01-07
Before I go forward, what will autoremove do?  Sorry to have to be so tedious but I have no unix or even dos background.  Command line is an alien world to me.

---

### Post by 2hot6ft2 on 2009-01-07
All that does is remove packages that were downloaded and stored on your computer in order to be installed. Once they have been installed all those do is take up space so it's safe to remove them. It doesn't uninstall anything or remove anything else.

It also removes packages that are no longer needed. Like if you uninstall an app that had 5 dependencies but nothing else needs them then they are just taking up space for nothing.

---

### Post by childofGod on 2009-01-07
Anything look out of order here?

paul@bigdaddy:~$ sudo apt-get update...

Reading package lists... Done                            
paul@bigdaddy:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

paul@bigdaddy:~$ sudo apt-get update...

Reading package lists... Done                            
paul@bigdaddy:~$ 

I'm mostly curious about the results of autoremove.  The results of both updates were 100%, so I'm sure they worked properly.

---

### Post by 2hot6ft2 on 2009-01-07
> **childofGod said:**
> 
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

Looks great. You have 4 updates available which you can either get in synaptic or wait for the update manager to tell you about them. No biggie.

So now I can safely ask...how are you?:P

---

### Post by childofGod on 2009-01-07
Much better now thanks to you.  What's the best way to become adept at using the command line?  I use it so infrequently that its almost like I'm learning everything from scratch each time I use it instead of building knowledge over time.

---

### Post by 2hot6ft2 on 2009-01-07
And as far as k9copy goes. It will work fine in ubuntu. It can be either installed or un-installed either thru synaptic or Applications>Add/Remove

Best to not be trying un-installing via the terminal until you get a little more comfortable with how it's used and the command structure since it's a very powerful tool. Don't let that scare you though.

---

### Post by 2hot6ft2 on 2009-01-07
You'll learn a whole lot here in the forums and if you have any questions just ask. Someone will explain what you don't know.

Here is a whole lot of info you can look thru on just about everything including the terminal.

Bash is the terminal so here it is first.
[http://www.gnu.org/software/bash/manual/bashref.html#Copying-This-Manual](http://www.gnu.org/software/bash/manual/bashref.html#Copying-This-Manual)

Linux is Not Windows
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Ubuntu Linux Resources
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Linux alternatives to windows apps
[http://www.osalt.com/](http://www.osalt.com/)
[http://www.linux.org/apps/](http://www.linux.org/apps/)
[http://www.gimpshop.com/](http://www.gimpshop.com/)
[http://www.linuxappfinder.com/](http://www.linuxappfinder.com/)

Everyone asks coming from windows
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

Customizing and apps
[http://ubuntuforums.org/showthread.php?t=856190](http://ubuntuforums.org/showthread.php?t=856190)
[http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11)

Learning Linux
[http://ubuntuforums.org/showthread.php?t=790485](http://ubuntuforums.org/showthread.php?t=790485)
[http://ubuntuguide.org/wiki/Ubuntu:Intrepid](http://ubuntuguide.org/wiki/Ubuntu:Intrepid)
[http://ubuntuforums.org/showthread.php?t=655207](http://ubuntuforums.org/showthread.php?t=655207)

Troubleshooting, multimedia and misc help
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)
[http://tazbuntu.blogspot.com/2008/07/remove-old-kernels-in-ubuntu.html](http://tazbuntu.blogspot.com/2008/07/remove-old-kernels-in-ubuntu.html)

---

### Post by TCSnyder on 2009-01-07
> **2hot6ft2 said:**
> I think this is why synaptic was running in the background.

For one synaptic is a gui app so it should have been ```
gksudo synaptic
```
and that's why it didn't show up. Sometimes you can get away with it but not always.

you can run synaptic by
```
synaptic
``` 
you cant make changes without making being root, but it still runs graphically. ( i always try my code before i put it in to make sure i dont post something stupid)

---

### Post by 2hot6ft2 on 2009-01-07
If that's got you fixed up you can mark your thread as solved. Have a great Evening. Time for me to hit the sack.

---

### Post by 2hot6ft2 on 2009-01-07
> **TCSnyder said:**
> you can run synaptic by
```
synaptic
``` 
you cant make changes without making being root, but it still runs graphically. ( i always try my code before i put it in to make sure i dont post something stupid)
That's a possibility. In any case it's straightened out now. I suspect just running synaptic is why it was running in the background and didn't open as it should. I may be wrong, I'll admit it.

---

### Post by 2hot6ft2 on 2009-01-07
The actual command that is run when you click on synaptic in the menu is
```
gksu /usr/sbin/synaptic
```
I'm tired and going to bed now. Goodnight.

---

