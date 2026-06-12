---
title: "Boots to GRUB Menu instead of splash screen"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by steve7777777 on 2011-01-16
I have Ubuntu 10.10 64 bit standard installation. Not dual boot and no other OS booting.

As of yesterday the PC boots to the GRUB boot menu. I select the first option and it boots into the splash screen.


My  /etc/default/grub file:
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

What can I do to boot directly into Ubuntu?  Not sure what caused this  but I was playing around with GPARTED boot CD and made no changes.

Thanks!

---

### Post by steve7777777 on 2011-01-16
Shot of the GRUB menu:

[IMG]http://img171.imageshack.us/img171/213/img20110116113149.jpg[/IMG]

---

### Post by sudo_0 on 2011-01-16
> made no changes

i don't believe you... lol

actually i have same issue on my macbook5.1 solo booting 10.10
bios not blessing ubuntu install maybe?

---

### Post by steve7777777 on 2011-01-16
I did press "reset" button on the PC when booting off of the GPARTED CD. Maybe Ubuntu made a change to the GRUB for recovery purposes? Other than that I made no changes. I use Virtual box to mess with things I don't fully understand :)

---

### Post by CharlesA on 2011-01-16
So the menu shows up, and asks you to make a selection, and you have to hit enter for it to boot Ubuntu. Is that correct?

---

### Post by steve7777777 on 2011-01-16
> **CharlesA said:**
> So the menu shows up, and asks you to make a selection, and you have to hit enter for it to boot Ubuntu. Is that correct?

Yes. Exactly.

---

### Post by CharlesA on 2011-01-16
Ok. It sounds like you need to change something in the grub config. See here: [https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

Check the GRUB_TIMEOUT setting.

---

### Post by steve7777777 on 2011-01-16
> **CharlesA said:**
> Ok. It sounds like you need to change something in the grub config. See here: [https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

Check the GRUB_TIMEOUT setting.

Here's the  /etc/default/grub:

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
[COLOR=Red]# GRUB_TIMEOUT=10[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

I just commented out the above, and no change. The Grub menu stays there until choose an option and hit enter. 




--
***GRUB_TIMEOUT=10*** 

[LIST]
[*][IMG]https://help.ubuntu.com/community/Grub2?action=AttachFile&do=get&target=info.png[/IMG] This instruction defers to the **GRUB_HIDDEN_TIMEOUT** unless **GRUB_HIDDEN_TIMEOUT** is commented (#). If **GRUB_HIDDEN_TIMEOUT** is active, the **GRUB_TIMEOUT** only operates once, and if, the menu is displayed. 
[*]Setting this value to -1 will cause the menu to display until the user makes a selection. 
[*]The  GRUB 2 menu is hidden by default unless another OS is detected by the  system. If there is no other OS, this line may be commented out unless  the user changes it. To display the menu on each boot, uncomment the  line and use a value of 1 or higher.
[/LIST]

---

### Post by CharlesA on 2011-01-16
Strange.

Mine looks exactly the same. Uncomment GRUB_TIMEOUT=10 and then run this:

```
sudo update-grub
```

Reboot and see what happens.

---

### Post by steve7777777 on 2011-01-17
I uncommented **GRUB_TIMEOUT=10**, and ran the command, and the GRUB menu is still there on booting up.

---

### Post by CharlesA on 2011-01-17
That doesn't make sense. It's like grub thinks there is a second OS installed.

---

### Post by DougieFresh4U on 2011-01-17
> **steve7777777 said:**
> Shot of the GRUB menu:

[IMG]http://img171.imageshack.us/img171/213/img20110116113149.jpg[/IMG]

Well I see 2 kernels installed so maybe it's giving him the option of which kernel he chooses to boot.
But then I am no GURU
Just a thought  :p

---

### Post by Elfy on 2011-01-17
> #GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="3"
Gives me 3 seconds - you could change the 3 to less than that.

---

### Post by Elfy on 2011-01-17
Hang on - you changed the entries - what you have done should work.

Did you update grub?

```
sudo update-grub
```

---

### Post by steve7777777 on 2011-01-17
> **forestpiskie said:**
> Hang on - you changed the entries - what you have done should work.

Did you update grub?

```
sudo update-grub
```

Yes. This is what the config file looks like now:

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="

Still getting the GRUB menu.

One more bit of information. About a week ago the SDA1 drive had reallocated sectors, so I switched it out with a new - and larger drive, using Clonezilla to backup and restore the image. The boot up was fine for over a week and I used NX many times to access and boot remotely. During that time I installed the updates that Ubuntu suggested. 

I doubt it's the /etc/default/grub but I'm new to Linux.

Only a single OS:

[IMG]http://img248.imageshack.us/img248/1585/gparted1.jpg[/IMG]

---

### Post by Elfy on 2011-01-17
> GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
[COLOR="Red"]#GRUB_TIMEOUT=3[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="

Try commenting the grub timeout line.

Edit and update grub

---

### Post by Elfy on 2011-01-17
> GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
[COLOR="Red"]#GRUB_TIMEOUT=3[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="

Try commenting the grub timeout line.

Edit and update grub

PS - thanks for the pic - but unfortunately I can't see that too well ;)

---

### Post by steve7777777 on 2011-01-17
> **forestpiskie said:**
> Try commenting the grub timeout line.

Edit and update grub

PS - thanks for the pic - but unfortunately I can't see that too well ;)

I commented out the grub timeout line. No success :(

Thanks for the suggestions and let me know if more info would help.

---

### Post by Elfy on 2011-01-17
Can you post the whole of the grub file please.

---

### Post by steve7777777 on 2011-01-17
> **forestpiskie said:**
> Can you post the whole of the grub file please.

Here it is:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
#GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by Elfy on 2011-01-17
mmm - I can never remember with grub2 

try commenting GRUB_HIDDEN_TIMEOUT_QUIET=true

I'd guess someone else will see and post.

---

### Post by Elfy on 2011-01-17
mmm - I can never remember with grub2 

try commenting GRUB_HIDDEN_TIMEOUT_QUIET=true

I'd guess someone else will see and post.

---

### Post by CharlesA on 2011-01-17
Here's what mine looks like for reference.

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by drs305 on 2011-01-18
Remove the # symbol from the Grub timeout line. 

If you aren't seeing any kind of countdown, and your GRUB_TIMEOUT is not set to -1, the most likely cause is that GRUB is finding a 'recordfail' event. 

If G2 doesn't boot properly, it marks the system so that the next time the system will wait for user input the next time. It does this so that the same failed boot selection isn't automatically selected again.

Unfortunately, on some systems this recordfail event is marked even when everything is working properly. In fact, it just started happening on my system yesterday.

You can try to clear the marker with:
```
sudo grub-editenv create
```
to make sure it isn't recorded in that file, but this seldom fixes the problem.

There are many reasons a recordfail event can be generated and I haven't come up with a way of troubleshooting them all. I have found workarounds, which set the *recordfail* value to one that will resume the countdown. To do this, you can modify the /etc/grub.d/00_header file.

To test this, edit /boot/grub/grub.cfg  This file isn't meant to be edited, but this will check to see if it's a recordfail problem. If it isn't, running "sudo update-grub" will remove the change. Open the file for editing:
```
gksu gedit /boot/grub/grub.cfg
```

Find this section and make the change (remove [COLOR="Red"]red[/COLOR], add **bold**). Save the file but do NOT update grub.

> 
if [ "${recordfail}" = 1 ]; then
[COLOR="Red"]  set timeout=-1[/COLOR]
  set timeout=10
else
  set timeout=10
fi

Reboot and see if the menu counts down and then boots automatically.

If it does we can make the change more permanent.

---

### Post by drs305 on 2011-01-18
Remove the # symbol from the Grub timeout line and update grub. 

If you aren't seeing any kind of countdown, and your GRUB_TIMEOUT is not set to -1, the most likely cause is that GRUB is finding a 'recordfail' event. 

If G2 doesn't boot properly, it marks the system so that the next time the system will wait for user input the next time. It does this so that the same failed boot selection isn't automatically selected again.

Unfortunately, on some systems this recordfail event is marked even when everything is working properly. In fact, it just started happening on my system yesterday.

You can try to clear the marker with:
```
sudo grub-editenv create
```
to make sure it isn't recorded in that file, but this seldom fixes the problem.

There are many reasons a recordfail event can be generated and I haven't come up with a way of troubleshooting them all. I have found workarounds, which set the *recordfail* value to one that will resume the countdown. To do this, you can modify the /etc/grub.d/00_header file.

To test this, edit /boot/grub/grub.cfg  This file isn't meant to be edited, but this will check to see if it's a recordfail problem. If it isn't, running "sudo update-grub" will remove the change. Open the file for editing:
```
gksu gedit /boot/grub/grub.cfg
```

Find this section and make the change (remove [COLOR="Red"]red[/COLOR], add **bold**). Save the file but do NOT update grub.

> 
if [ "${recordfail}" = 1 ]; then
[COLOR="Red"]  set timeout=-1[/COLOR]
  **set timeout=10**
else
  set timeout=10
fi

Reboot and see if the menu counts down and then boots automatically.

If it does we can make the change more permanent.

---

### Post by steve7777777 on 2011-01-18
> **drs305 said:**
> Remove the # symbol from the Grub timeout line and update grub. 

If you aren't seeing any kind of countdown, and your GRUB_TIMEOUT is not set to -1, the most likely cause is that GRUB is finding a 'recordfail' event. 

If G2 doesn't boot properly, it marks the system so that the next time the system will wait for user input the next time. It does this so that the same failed boot selection isn't automatically selected again.

Unfortunately, on some systems this recordfail event is marked even when everything is working properly. In fact, it just started happening on my system yesterday.

You can try to clear the marker with:
```
sudo grub-editenv create
```to make sure it isn't recorded in that file, but this seldom fixes the problem.

There are many reasons a recordfail event can be generated and I haven't come up with a way of troubleshooting them all. I have found workarounds, which set the *recordfail* value to one that will resume the countdown. To do this, you can modify the /etc/grub.d/00_header file.

To test this, edit /boot/grub/grub.cfg  This file isn't meant to be edited, but this will check to see if it's a recordfail problem. If it isn't, running "sudo update-grub" will remove the change. Open the file for editing:
```
gksu gedit /boot/grub/grub.cfg
```Find this section and make the change (remove [COLOR=Red]red[/COLOR], add **bold**). Save the file but do NOT update grub.


Reboot and see if the menu counts down and then boots automatically.

If it does we can make the change more permanent.

Thanks! I'll try that tonight. I'm also going to use [Webmin]("http://www.webmin.com") to view the logs - noting the time when the system is booting. Hopefully this can help others as well!

---

### Post by steve7777777 on 2011-01-18
After running

**sudo grub-editenv create**

the system booted directly into the splash screen. When I rebooted a second time it got stuck at the GRUB panel.

I then edited grub.cfg as instructed and the system boots directly to the splash screen. After the second re-boot it also booted to the splash screen :)

A few questions.

How do I make the change more permanent? 
I take it there's still a problem somewhere and I need to check out the logs?

Thanks for the help!!!

---

### Post by drs305 on 2011-01-19
@ steve7777777,

Early on with the Grub2 introduction I tried with numerous users to find the cause of the recordfail marker and don't recall having much success.

Understand that what you are doing is preventing Grub 2 from stopping a repeated booting of a selection which it had problems with on the previous attempt. If it was set to autoboot and failed back to the G2 menu, it would continue attempting to boot the same menuentry. For most users, disabling this feature is not a problem, but I thought you should know just in case you have some unique requirement for unattended operation...

The quick fix: edit /etc/grub.d/00_header:
```
gksu gedit +238 /etc/grub.d/00_header
```
The line to edit is around line 240. Change "1" to "0"
> make_timeout ()
{
    cat << EOF
if [ "\${recordfail}" = **[COLOR="DarkRed"]0[/COLOR]** ]; then
  set timeout=-1
else
  set timeout=${2}
fi
Save the file, update grub, and you should be able to auto boot.


If you want to try, you could completely purge and reinstall Grub 2. This does a much more thorough job than a straight reinstall does. The only caveat is that you won't have a bootloader for a minute or so. We check the Internet connection before removing it just to make sure you can reinstall it.

```
sudo apt-get udpate # To ensure Internet connection works.
sudo apt-get purge grub-common  # Remove Grub 2
sudo apt-get install grub-pc  # Add Grub 2 back.

```While reinstalling, it will display a line for you to add kernel options. Normally none are required. Tab to OK and continue.
When you get to the partitioning page, use the space bar and ONLY select the drive (example sda); do NOT select the partition (example sda5). Tab to OK and ENTER.

This will completely remove all the grub files and reinstall them. If the recordfail event is being caused by a problem within G2, this should fix it.

---

### Post by steve7777777 on 2011-01-19
I applied the "quick fix" and it now boots correctly!  Thanks for the assistance and I hope someone finds a solution to the GRUB 2 bug.

---

### Post by NerdWermz on 2011-01-19
Good thread, glad I found it.

I have three different machines on 10.10 (one is 64bit) that all started doing this 2 weeks ago. They all use to boot fine.  I was wondering if it was one of the updates or something. And they are all single boot machines.

---

### Post by NerdWermz on 2011-01-19
Good thread, glad I found it.

I have three different machines on 10.10 (one is 64bit) that all started  doing this 2 weeks ago. They all use to boot fine.  I was wondering if  it was one of the updates or something. And they are all single boot  machines.

---

### Post by steve7777777 on 2011-01-19
> **NerdWermz said:**
> Good thread, glad I found it.

I have three different machines on 10.10 (one is 64bit) that all started doing this 2 weeks ago. They all use to boot fine.  I was wondering if it was one of the updates or something. And they are all single boot machines.

Interesting. As I mentioned my machine is single boot, Ubuntu 10.10 Maverick 64bit. 

Have you done image restores with Clonezilla recently?

---

### Post by NerdWermz on 2011-01-20
> **steve7777777 said:**
> Interesting. As I mentioned my machine is single boot, Ubuntu 10.10 Maverick 64bit. 

Have you done image restores with Clonezilla recently?

Nope, I've never done any of that.

---

### Post by NerdWermz on 2011-01-21
Just curious, does it seem slower to you now?   just seems to hang at the empty black screen with the blinking cursor longer now.   I did everything but reinstall grub2.

---

### Post by steve7777777 on 2011-01-21
> **NerdWermz said:**
> Just curious, does it seem slower to you now?   just seems to hang at the empty black screen with the blinking cursor longer now.   I did everything but reinstall grub2.

Yes, it takes several seconds longer to boot, but I have a fast machine. I haven't reinstalled GRUB 2 yet.

---

