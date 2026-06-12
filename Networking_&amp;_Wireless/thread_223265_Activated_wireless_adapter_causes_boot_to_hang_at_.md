---
title: "Activated wireless adapter causes boot to hang at 'Configuring Network Interfaces'"
date: 2006-07-26
forum: Networking &amp; Wireless
---

### Post by Trizik on 2006-07-26
OK, here's the deal...

Ubuntu 6.06 LTS (Dapper Drake)
AMD Athlon 64
Linksys Wireless Adapter WMP54GR

Initial install was smooth and booting into Ubuntu after install was smooth. Then I "activated" the wireless adapter via the GUI and all hell broke loose. I am no longer able to boot into Ubuntu (safe mode or not) because it hangs at "Configuring Network Devices."

If I Ctrl+C to skip Configuring Network Devices, the login prompt appears, but after logging in, a dark orange/red background appears (part of the desktop theme, I think) along with the mouse pointer. I am able to move the mouse pointer, but that's all I can do because nothing else is visible. If I wait at least 5 minutes as suggested (I have waited for more than an hour just to be sure), nothing ever happens; the orange/red screen and mouse pointer are still the only visuals. At that point I can Ctrl+Alt+F1, which takes me to the command prompt, but when I type any command (such as "sudo gedit /etc/rc.local") and press Enter, the cursor appears on a new line without the preceding "root@ubuntu:~$" and nothing ever happens.

The same thing happens to the cursor in the command prompt when I boot into safe mode.

I can boot off the LiveCD.

For now I would just like to disable the wireless adapter or disable networking altogether so I can at least access Ubuntu. Please advise the easiest way to do this, whether it's using a boot option or the LiveCD or some other way. Thanks in advance.

---

### Post by wieman01 on 2006-07-26
First of all the system hangs because the network configuration is wrong (I think you have figured THAT out) and the system is trying to sychronize the system clock via Internet, and of course gets stuck there. I disabled the "synchronize" function by the way.

Ok, crtl+c helps. You need to boot in recovery mode and do exactly that. Then you log on to the system with your normal user account and password (still in recovery and hence text mode).

Then type in the following command... We are now disabling your network settings:

> sudo vi /etc/networking/interfaces

Key in your user password.

Then:

1. Press "insert".
2. Comment out **_all_** lines **_except_** for these ones (by adding a # in front of each):
> auto lo
iface lo inet loopback
3. Press "escape".
4. Press "Shift ZZ".

The "interfaces" files should now have been saved and you need to reboot: 
> sudo reboot

You should be able to access your system as you are used to.

---

### Post by Trizik on 2006-07-30
> **wieman01 said:**
> Ok, crtl+c helps. You need to boot in recovery mode and do exactly that. Then you log on to the system with your normal user account and password (still in recovery and hence text mode).

Then type in the following command... We are now disabling your network settings:

sudo vi /etc/networking/interfaces

Key in your user password.When I boot into recovery mode and hit Ctrl+C to bypass "Configuring Network Interfaces," root@computername:~# precedes the blinking cursor. When I type "sudo vi /etc/networking/interfaces" the cusor jumps to the beginning of the next line (no more root@computername:~#) and nothing happens. Other commands do nothing. Backspace prints a few characters of text rather than deleting text.

What's going on?

---

### Post by a.estrada.111680 on 2006-08-08
I have exactly the same problem you have/had. Did you get to resolve it? I am still stuck on the command line with the cursor just blinking after I pressed enter. 

Thanks

---

### Post by niko7865 on 2006-08-17
I've got the same problem and would really like a fix for the unresponsive command line. Any help is appreciated, I hate haveing to use my windows partition.

---

### Post by wieman01 on 2006-08-17
What happens if you press "crtl + alt + F1"? Can you log on to another terminal this way?

---

### Post by niko7865 on 2006-08-18
I don't have any other logins that I know of. I reinstalled and commented out the lines in /etc/network/interfaces. Everything worked fine for 2 or 3 reboots. I installed mplayer and a few chemistry applications and now it will boot to the login screen without problems but upon logging in i will only get the default brown background and a mouse pointer which remain indefinitly. After logging into the terminal and typing a command it will fail to execute, pressing enter will only create a new blank line. I have access to the partition so i can copy over any files that will help. Thanks :)

---

### Post by stricevics on 2006-08-18
> **niko7865 said:**
> After logging into the terminal and typing a command it will fail to execute, pressing enter will only create a new blank line.

If the command execution fails, does CTRL+C do anything?

Also, when logged in as root, there is no need to type "sudo". Sudo gives option to execute a command as root. (someone else wrote that earlier)

---

### Post by niko7865 on 2006-08-19
turns out i was getting this error when trying to start xserver

Option "Device" "/dev/wacom"
(EE) xf860OpenSerial:cannot open /dev/wacom
no such file or directory
Error opening /dev/wacom No such file of directory

I was abe to fix it by booting into the rescue mode and doing dpkg-reconfigure xserver-xorg, there are still several sections containing relations to wacom and tablet PC devices of which I have none. If/when I find a pemanent solution I'll post here how I was able o solve it, if no one beats me to it.

---

### Post by wieman01 on 2006-08-20
"wacom" will give you error messages in the log file, but won't cause a system error that you notice. Surprised to hear it.

---

### Post by niko7865 on 2006-08-20
Ya it definatly wasn't that, must have just been a coincidence that it worked after reconfiging xserver. I think it's haning at something like "Loading Startup Scripts (etc/rc.local)" Wrong wording but it's something to that extent. Thats the last thing that shows up when i try logging in, let it hang for awhile at the brown screen and mouse pointer, and then hit Control + Alt + Backspace.

Going to post this in general help since it isn't a networking problem anymore.

---

### Post by usererror on 2006-08-21
Did anyone find a resolution to this?  I posted about this too, but no solution yet.  Same exact equipment I'm having is also here.

CTRL + C does not work either after any command I type hangs. :mad:

---

### Post by usererror on 2006-08-21
I found a solution!

My whole goal was to get a standalone internet workstation to be wireless, with just firefox so we don't ever have to maintain it.

here is what i did to make it connect to the wifi network and NOT cause hang ups on boot.

Reloaded, again, from scratch.

went into terminal.

ran the following:

```
iwconfig ra0 essid "Internet"
```

```
sudo vi /etc/network/interfaces
```

added the following line:
```

auto ra0
iface ra0 inet dhcp

```

```
/etc/init.d/networking restart
```

the restart was successful, so i rebooted and it came up perfectly.  i did NOT use the GUI network config tool at all this time.

---

### Post by dragonlor20 on 2006-08-24
> **a.estrada.111680 said:**
> I have exactly the same problem you have/had. Did you get to resolve it? I am still stuck on the command line with the cursor just blinking after I pressed enter. 

Thanks

Hey guys... All of you with the hangup after the command line... The reason it is doing this is because of a problem in the original solution's code. There is no file called /etc/networking/interfaces so the computer creates one. That blank line after the command prompt is a new document, just like when you use gedit and type the wrong location for a file, instead of an error you get a new file. Simple.

Solution: change /etc/networking/interfaces ----> /etc/network/interfaces that will get you the file you want.

---

### Post by leggot on 2007-06-24
I'm a newbie to Linux/Ubuntu and appear to have the same symptoms:

1. ubuntu boot hangs at configuring network
2. hit ctl-c
3. login to ubuntu as a regular user
4. get red-orange screen and hangs
5. ctl-alt-f1 to get to a command line
6. issue  "sudo vi /etc/network/interfaces" and get a hang.  Repeating ctl-alt-FX, login, etc. and still get hang at this sudo vi command.

Any ideas to try to get interfaces updated  would be much appreciated

---

