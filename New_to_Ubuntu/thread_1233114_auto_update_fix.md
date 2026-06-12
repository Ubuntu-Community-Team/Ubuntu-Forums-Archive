---
title: "auto update fix???"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by DarinB on 2009-08-06
can some one explain the bug fix so i don't do something wrong?????? 

Automatic Updates not checking automatically
Bug: automatic updates checking not working after upgrade from Intrepid to Jaunty. `apt-get update` or update-manager 'check' works fine, however, but are manual operations.

Launchpad: [https://bugs.launchpad.net/ubuntu/+s...er/+bug/356152](https://bugs.launchpad.net/ubuntu/+s...er/+bug/356152)

Reason: /etc/cron.daily/apt script incorrectly chmod'ed as 644 aka not executable

**Fix: # chmod 755 /etc/cron.daily/apt ... reboot; might help to remove /var/spool/anacron/cron.daily**

---

### Post by drs305 on 2009-08-06
First, realize that updates are handled a bit differently in jaunty. Security updates are made available immediately, but other updates will be installed only weekly by default. If you want to update more frequently, you will have to run the "check" manually or change the settings (System, Administration, Update Manager, Settings).

The link to the bug fix didn't work, so I don't know whether you really need to run it, but to answer your specific question, if you still need it - Open a terminal (Applications, Accessories, Terminal), and copy (preferable) or type the following and press ENTER:
```

sudo chmod 755 /etc/cron.daily/apt

```
Once you hit ENTER, you will be asked for your password. You won't see anything as you type (it's a security feature). Just type it and hit ENTER. The 755 will change the permissions so the file can be executed.

---

### Post by DarinB on 2009-08-06
could this have messed up my auto update when i did the part below and changed mirrors or was it coincidence it used to work when i first installed jaunty. i messed up [I][SIZE="4"]my system by rm a list.d
lost my medibuntu reinstalled it,,,,
i was also recommended to use best mirror for my area
since then..... i get no error messages but no auto updates,,,,,,, it is set to receive them?
1. when is update day i remember it used to be thursday or does that only apply to the canonical site updates, and not to ie ....mirror.cc.columbia.edu....????????[/SIZE][/I]
Or could it be in one of the kernel upgrades i have three jaunty kernels on my boot menu???????

---

### Post by drs305 on 2009-08-06
You can check to see if your system is set to receive updates by going to System, Administration, Software Sources (or Synaptic). Check the Updates tab and the Ubuntu Updates and Automatic Updates settings. 

If you think it may be a problem with your server, in Software Sources, Ubuntu Software tab, change the "download from" to another server and then Reload.

The kernels should not have stopped the updates, no matter which of the three you select.

---

### Post by DarinB on 2009-08-12
I did what drs305 suggested i get the auto updates now but they automatically go to my part of my panel that show apps are open, no more little orange triangle up top notification bar. i do have to click it to choose what i want to add, which is great, any ideas maybe its my settings for the auto update, i really just want it the way it was the little icon that i can click if i have time. or when i have time.

---

### Post by kansasnoob on 2009-08-12
Look at post #18 here:

[http://ubuntuforums.org/showthread.php?t=1095928&page=2](http://ubuntuforums.org/showthread.php?t=1095928&page=2)

I followed that and got back the "old" update icon. 

Because I'm visually impaired I later installed 'notification-daemon (0.4.0-0ubuntu3)' and removed 'notify-osd' which requires the removal of 'ubuntu-desktop'. **Now, that's OK, but 'ubuntu-desktop' must be reinstalled to perform a dist-upgrade or I'll end up with a broken OS.**

For me the new notifications simply needed to be in a better location and remain displayed longer so I could focus in on them. I expect they'll become more 'user configurable' in the ongoing development process.

---

### Post by Tibuda on 2009-08-12
> **DarinB said:**
> I did what drs305 suggested i get the auto updates now but they automatically go to my part of my panel that show apps are open, no more little orange triangle up top notification bar. i do have to click it to choose what i want to add, which is great, any ideas maybe its my settings for the auto update, i really just want it the way it was the little icon that i can click if i have time. or when i have time.

You can have your icon back. Press Alt+F2. Type **gconf-editor** and press Enter/OK.  Browse to /apps/update-notifier. Uncheck the auto_launch item.

Or you can use a terminal:
```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```

---

### Post by DarinB on 2009-08-12
I did what danielrmt suggested......now i have to wait to see if the icon comes up and doesn't launch automatically i like the control of ignoring it if i don't have time. thanks

---

### Post by DarinB on 2009-08-13
Ok the auto update icon is back, but i have another problem it wont go away now. after updates in installed.
The problem may be Aeskulap, a medical xray viewer. The repos have a beta version of it that does not work with Jaunty, i have the previous version running fine. but the distribution upgrade asks to be added. i can't do that.... i only want to keep the old version. I think that is what may be keeping the icon up, is there any way to stop that from asking to update the version of aeskulap that i have???????????????????????
or is it something else?????? it is a pain to have to uncheck the aeskulap version update every time.

---

### Post by drs305 on 2009-08-13
> **DarinB said:**
>  The repos have a beta version of it that does not work with Jaunty, i have the previous version running fine. but the distribution upgrade asks to be added. i can't do that.... i only want to keep the old version. I think that is what may be keeping the icon up, is there any way to stop that from asking to update the version of aeskulap that i have???????????????????????
or is it something else?????? it is a pain to have to uncheck the aeskulap version update every time.

DarinB,

You can 'lock' the version you have by going to Synaptic, highlight the package, then in the main menu: Package, Lock Version.

Then in the command line:
```
sudo aptitude hold <packagename>
```
Example: sudo aptitude hold gimp

Accomplishing these two items will hold the current version of the app in both Synaptic and command-line updates until you change the values and remove the lock.

---

### Post by DarinB on 2009-08-13
do i need to do the command line one and if i do how do i change it back one day or some day?????
the gui method seems to work but i guess if i do a sudo apt-get upgrade or update ????? is that what you mean????

---

### Post by drs305 on 2009-08-13
> **DarinB said:**
> do i need to do the command line one and if i do how do i change it back one day or some day?????
the gui method seems to work but i guess if i do a sudo apt-get upgrade or update ????? is that what you mean????

Yes, if you run an update command from the terminal the Synaptic lock won't block an update. To prevent a terminal update, place a 'hold' on the package as described earlier.

Refer to the following for instructions on how to place and remove holds:
[https://help.ubuntu.com/community/PinningHowto]("https://help.ubuntu.com/community/PinningHowto")  

Look at the section on "removing a hold"

---

### Post by DarinB on 2009-08-14
Thanks drs305

---

