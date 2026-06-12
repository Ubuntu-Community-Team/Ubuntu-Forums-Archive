---
title: "NDISWRAPPER causing error/freeze on log in"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by rogval on 2008-07-31
After repeat trial and error, I have determined that ndiswrapper is causing my system to freeze on login with the error of the following...

[B]There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.[/B]

After hours of googling, this apparently has something to do with ndiswrapper and the mrv8k51.inf file for installing the Dlink DWL-G510 Rev.A1 wireless card...which apparently is a big issue that nobody has really come up with a die hard solution.  I did find something about my situation causing the eth lo file getting corrupt when you install this stuff but I can't figure out how to alter the file afterwards cause, like I said...I can't log in cause it freezes and gives me the above error so being a Linux newbie I don't know how to do that kind of stuff via text commands and Konsole and recover my system.

So anyway...when I install the Ndiswrapper via the Synaptics Package Manager and install the windows driver .inf file which I downloaded from Dlink, then voila...I've got wireless, and everything works fine.  But then when I reboot to make sure everything is set...then I get this problem that I am explaining, so I think It has to do with ndiswrapper and the wireless adapter trying to start automatically when I boot the machine.  So then I have to reinstall Ubuntu and start from scratch. 

So to make a long question short...how can I make it where I have to manually start the wireless when the machine boots up.  I know I can disable the wireless adapter before I shut down but that isn't going to work because what happens if the machine restarts automatically after an update, or the power goes out, or whatever kind of restart that wouldn't allow me to disable the wireless and then I'm back to square one!!

By the way...this is Ubuntu Desktop Edition 8.04 which is the latest...just downloaded and started this business the other day.

Sorry for the rambling, but I just wanted to make myself clear and throw out as much info as possible in case somebody sees something I am missing!!

Thanks...any pointers is appreciated!!

Roger

---

### Post by pytheas22 on 2008-07-31
> There was an error starting the GNOME Settings Daemon.

Does the system freeze completely after you get this message?  Normally when it says this, it still allows you to log in to Gnome; it just looks ugly because it doesn't start all of the normal processes.

Also, I'm not positive that ndiswrapper is the source of the problem (although it could be), as issues with Gnome failing to start usually lie elsewhere (like video card problems).  Nonetheless, you could do this to prevent ndiswrapper from loading before you login to Gnome:

After Ubuntu boots and you get to the login screen, press control-alt-F2.  You'll be brought to a command prompt, where you should login with your normal user name.  Then run this command to unload ndiswrapper:
```

sudo rmmod ndiswrapper
```

After that, press control-alt-F7 to get back to the graphical login screen.  Login and see if you still have problems.  If not, then ndiswrapper must have been the issue.  If Gnome does still fail to start, then we'll have to look elsewhere.

Also, this fix for unloading ndiswrapper would have to be manually applied each time you start the machine.  But if it solves the problem, we can write a startup script to do it automatically.  Before doing that, however, I want to make sure that ndiswrapper is indeed the root of the problem.

---

### Post by rogval on 2008-07-31
Ok...I did exactly what you said, and I still got the problem just like before...however, here is what happened when I did your instructions.

When I did the Alt-Ctrl-F2 and I log in ok at the command prompt and then I execute the command "sudo rmmod ndiswrapper" and hit enter and the curser just goes to the next line and sits there flashing...no fail or success indication at all...just sitting there flashing.  So I do the Alt-Ctrl-F7 and it goes back to the log in screen and log in and I still get the same problem...so I let it sit for a couple minutes and then Alt-Ctrl-F2 again and it goes back to the command prompt EXACTLY as I left it to try and log in...just sitting there in the same place, flashing away.

The wierd thing is...I can restart and log in all day until I install the wireless driver via NDISWRAPPER.  I thought it might be related to the issue in this thread below, but I'm too new to Linux to understand the instructions fully.  Here is the thread that I was talking about the lo eth being screwed up...

[http://arunpc.com/2008/06/01/ubuntu-there-was-an-error-starting-the-gnome-settings-daemon/](http://arunpc.com/2008/06/01/ubuntu-there-was-an-error-starting-the-gnome-settings-daemon/)

---

### Post by pytheas22 on 2008-07-31
> When I did the Alt-Ctrl-F2 and I log in ok at the command prompt and then I execute the command "sudo rmmod ndiswrapper" and hit enter and the curser just goes to the next line and sits there flashing...no fail or success indication at all...just sitting there flashing. So I do the Alt-Ctrl-F7 and it goes back to the log in screen and log in and I still get the same problem...so I let it sit for a couple minutes and then Alt-Ctrl-F2 again and it goes back to the command prompt EXACTLY as I left it to try and log in...just sitting there in the same place, flashing away.

That's alright; this is the way it's supposed to behave.  You weren't supposed to get any feedback from the "sudo rmmod ndiswrapper" command unless there was an error.

I can see from some of the things mentioned on that page that you linked to how ndiswrapper could be causing problems for Gnome.  You mentioned that you are unable to ping localhost, correct (when you type "ping localhost," you get no reply)?

Do you know what your /etc/network/interfaces file looks like?  You could try changing it to just:
```

auto lo
iface lo inet loopback
```

(if there are any other lines in that file, comment them out by putting a # in front of them; that way you can reenable them again easily if needed)

To edit that file, if you can't log in to Gnome, you can log in on the control-alt-F2 terminal and type:
```

sudo nano /etc/network/interfaces
```

and a simple text editor will open.  It's not pretty, but it works.  After you make the changes, press control-O (the letter, not zero) to save the changes, and control-X to exit.  Then reboot your computer and see if the problems still occur.

Editing /etc/network/interfaces might break ndiswrapper, but really it shouldn't (at one time ndiswrapper may have relied on that file to work, but in modern Linux it should not be necessary, as far as I know).  If it does break ndiswrapper, we can figure out another way around the issue.

Try editing the file as described above and see if it helps (remember to reboot after editing).  If not, we'll keep looking.

---

### Post by rogval on 2008-08-01
> That's alright; this is the way it's supposed to behave. You weren't supposed to get any feedback from the "sudo rmmod ndiswrapper" command unless there was an error.


I understand that, but shouldn't it go back to the current user command prompt, as in [email]MediaCenter@roger>...or[/email] whatever it looks like.  Because like I said before...the curser just jumps down to the next line and sits there flashing...it never goes back to the command prompt where you could type another command.

> I can see from some of the things mentioned on that page that you linked to how ndiswrapper could be causing problems for Gnome. You mentioned that you are unable to ping localhost, correct (when you type "ping localhost," you get no reply)?

Do you know what your /etc/network/interfaces file looks like? You could try changing it to just:

That link that I posted was what I THOUGHT might be my problem, but like I said...being a total newbie, I'm not really sure I'm understanding everything it is saying.  However...my /etc/network/interfaces file does look like the one you showed...just the two lines, just like the lines you quoted.

So anyway...I did what you said... 

> To edit that file, if you can't log in to Gnome, you can log in on the control-alt-F2 terminal and type:
Code:

sudo nano /etc/network/interfaces

and a simple text editor will open. It's not pretty, but it works. After you make the changes, press control-O (the letter, not zero) to save the changes, and control-X to exit. Then reboot your computer and see if the problems still occur.

And being that I couldn't log in ofcourse...I did Alt-Ctrl-F2, and put in the command, and once again...the cursor jumped to the next line and sat there flashing...forever...no new command prompt or anything.

Here is a pic of the screen...

[IMG]http://img.photobucket.com/albums/v611/rogval/0801080850.jpg[/IMG]

In the meantime, while I wait to see what you have to say...I am going to try another video card just for the sake of argument.  The one I have in now is a Radeon 9250 128mb...I've got a spare that is the same but only 64mb...so you never know...we shall see!!  I'll let you know what happens.

Roger

---

### Post by pytheas22 on 2008-08-01
> I understand that, but shouldn't it go back to the current user command prompt, as in [email]MediaCenter@roger>...or[/email] whatever it looks like. Because like I said before...the curser just jumps down to the next line and sits there flashing...it never goes back to the command prompt where you could type another command.


Sorry, I didn't realize that it wasn't returning back to the prompt.  There is indeed something bad going on here if it hangs like that, both when you try to unload ndiswrapper and run nano.  Can you type anything with success at the command line...do commands like:
```

ls
cd /
echo 'hey'
```

hang as well?  If so, then you may be best off reinstalling the whole system, because it's going to be hard to fix the problem if you can't run any commands successfully.

If you can run stuff successfully, you could try:
```

sudo apt-get remove --purge ndiswrapper*
```

This would clear out ndiswrapper completely.  Your wireless would break, obviously, but maybe it would solve the issue with logging in.  After that we could try getting your wireless working again in a way that won't cause the hanging (actually I notice that you have a marvell chipset, which should have good Linux support, so it may not be necessary to use ndiswrapper at all).

Also, just in case it matters, were you using the proprietary ATI video driver or the open-source one?  If you didn't deliberately install the proprietary one, then you must be using the open-source version.

---

### Post by rogval on 2008-08-01
Ok...here is my latest adventure...

1) Completely new install of Ubuntu Desktop Edition 8.04 after putting in a different video card...now running on a Radeon 9250 64mb.

2) Rebooted several time just fine.

3) Installed ndiswrapper-utils 1.9 off the Ubuntu cd via Synaptics and rebooted...everything still fine.

4) Now following steps from "Configuration" on, in this link...[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper...starting](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper...starting) with "Disable free drivers"...Rebooted, and everything still fine.

5)Proceeded with the next step in the above link...Identifying your adapter...done all the necessary steps up to and including (BUT NO FURTHER) and rebooted, and we're back...no problems yet.

6)No proceeding with steps 3.5...Loading Module...now rebooting again before trying step 3.6...and we're back.

7)Now on to the next step of configuring/connecting to the wireless network. Ok...that worked fine and rebooted just fine however...It dropped my connection and wouldn't reconnect, so I am going to turn off the WPA encryption on the router and see what happens. But I rebooted just fine

8)And I've rebooted with disabling the WPA on the router and seems to be staying connected.  So it looks like Wireless MAC addy filtering is the only security I'm going to have here.  I honestly don't think there is anybody in this neighborhood trying to snoop. 

In the meantime for the next couple of days I am going to stop at this point.  I honestly don't mind to reload ndiswrapper on restart, cause I'm hoping to keep this machine up pretty much 24/7, aside from blowing it's nose occasionally. 

So that is where I stand now.

---

### Post by pytheas22 on 2008-08-01
I'm glad you have it working better now, even if it's unclear what exactly the problem was before.
> 
And I've rebooted with disabling the WPA on the router and seems to be staying connected. So it looks like Wireless MAC addy filtering is the only security I'm going to have here. I honestly don't think there is anybody in this neighborhood trying to snoop.

I bet WEP would work if you want to add a little extra security--usually it's only WPA that causes major problems.  But anyone running Linux who knows what she's doing can [crack a WEP key]("http://aircrack-ng.org") in five minutes these days, and MAC-address filtering won't stop an intruder for more than however long it takes to type "sudo ifconfig hw ether [your MAC address]."  So if you want to try to trouble-shoot the WPA stuff, we can give it a shot.  On the other hand, the vast majority of people are not geeks and have no idea how to defeat wireless privacy schemes, so maybe it doesn't matter that much.
> 
I honestly don't mind to reload ndiswrapper on restart

You could always [write a startup script]("http://strabes.wordpress.com/2006/10/16/how-to-create-a-startup-script-in-ubuntu-dapper/") to this automatically in case the manual loading ever becomes boring.

But I'm glad you can at least get online now without worrying about Gnome crashing; have fun with Ubuntu!

---

### Post by rogval on 2008-08-02
Well...figured what the heck...been playing a little today again, and I thought I would edit in Ndiswrapper in /etc/modules by adding ndiswrapper to the end of the file and low and behold if it didn't recreate the original log in error/freeze problem.

---

### Post by rogval on 2008-08-02
> **pytheas22 said:**
> Sorry, I didn't realize that it wasn't returning back to the prompt.  There is indeed something bad going on here if it hangs like that, both when you try to unload ndiswrapper and run nano.  Can you type anything with success at the command line...do commands like:
```

ls
cd /
echo 'hey'
```

hang as well?  If so, then you may be best off reinstalling the whole system, because it's going to be hard to fix the problem if you can't run any commands successfully.

If you can run stuff successfully, you could try:
```

sudo apt-get remove --purge ndiswrapper*
```

This would clear out ndiswrapper completely.  Your wireless would break, obviously, but maybe it would solve the issue with logging in.  After that we could try getting your wireless working again in a way that won't cause the hanging (actually I notice that you have a marvell chipset, which should have good Linux support, so it may not be necessary to use ndiswrapper at all).

Also, just in case it matters, were you using the proprietary ATI video driver or the open-source one?  If you didn't deliberately install the proprietary one, then you must be using the open-source version.

ls
cd /
echo...all produce results, but when I do the sudo apt-get remove command then I get the frozen flashing cursor...it won't go back to the prompt.

---

### Post by rogval on 2008-08-02
Ok...booted into recovery mode option at the very beginning of the boot process and did the ***sudo apt-get remove --purge ndiswrapper**** and let it do it's thing and it went back to the prompt after a whole list of processes it did and then I rebooted and was able to log in just fine...so that tells me it is ndiswrapper that is doing it!!  don't know why, but at least we now know what it is!!

Guess I will try the whole script thingy and see what happens.

---

### Post by rogval on 2008-08-04
Can anybody tell me step by step, how to write this startup script and how to integrate it?  Googling has all kinds of intstuctions on what to do with the script once you write it, but nothing otherwise.  Aside from the fact that most of the instructions that I found seem to contradict one another.

Again...we're talking about a newb here!!:)
Roger

---

### Post by pytheas22 on 2008-08-04
Different Linux distributions deal with startup scripts in different ways, and it doesn't help that Ubuntu is in the process of replacing init (which is traditionally responsible for booting the system on most Unix systems) with [upstart]("http://upstart.ubuntu.com/").  So don't feel bad if you're confused.

But basically this is what you need:

1. write your script to modprobe ndiswrapper and save it into the /etc/init.d directory (these commands will do it all automatically):
```

sudo gedit /etc/init.d/modprobe-ndiswrapper.sh
```

A file will open.  Add the commands you need to run (one command per line), save the file and close it.

2. make sure the new script is executable:
```

sudo chmod +x /etc/init.d/modprobe-ndiswrapper.sh
```

3. tell the system to add the new script to the bootup queue:
```

sudo -s
cd /etc/init.d
update-rc.d modprobe-ndiswrapper.sh defaults
```

This should work; if not let me know.

---

### Post by rogval on 2008-08-04
Unfortunately the script has made it do the exact same as if I put ndiswrapper in the modules file for startup.

So I guess I will stick with manually starting it...unless you have another idea?

---

### Post by pytheas22 on 2008-08-04
Unfortunately I don't have any other ideas, but the script should work.  Are you sure it's being run?  To check, add a line to it like:
```

touch /home/file.txt
```

If the script runs, a blank text file named "file.txt" will appear in /home.

Otherwise, what did you put in the script exactly?

---

### Post by rogval on 2008-08-04
I did verbatim, just like your steps said in post #13.

In the file I put 

[B]sudo depmod -a
sudo modprobe ndiswrapper[/B]

since that is what I do in termninal whenever I login/startup to get the wireless going.

I did notice in some googlingthey say to begin a startup script with **#!/bin/bash** but you didn't mention anything like that, so, I don't know.

---

### Post by pytheas22 on 2008-08-04
> I did notice in some googlingthey say to begin a startup script with #!/bin/bash but you didn't mention anything like that, so, I don't know.

Yes, that's the proper way to write a bash script, and you could try adding #!/bin/bash at the top of the script to see if it helps.  But on Ubuntu it should run even without that line.

Also, try adding:

```
rmmod ndiswrapper
```

to the beginning of the script, so that the finished product looks like:

```
#!/bin/bash

rmmod ndiswrapper
depmod -a
modprobe ndiswrapper
touch /home/file.txt
```

(the sudos are not necessary since the script is being run by root to begin with, although they shouldn't hurt anything).

---

### Post by rogval on 2008-08-04
How about a script that I can put on the desktop and doubleclick it once I get fully started up, and it will execute those command in terminal automatically.

---

### Post by pytheas22 on 2008-08-04
> How about a script that I can put on the desktop and doubleclick it once I get fully started up, and it will execute those command in terminal automatically.

That's a good idea and works too.  Just write a script with the commands you need and place it on your desktop or wherever, and make sure it's executable.

Actually if you want, you can run the script automatically when you log into Gnome.  If you go to System>Preferences>Sessions, you can set that up.

An important point is that the script needs to be run as root, so you should prefix your commands with a command like:
```

gksudo sudo -s
```

That way you'll be prompted to enter your password graphically, and after you do it, you will be logged in permanently as root (in the shell where the script is being run, at least) for the duration of the script.

If you run the script automatically using the Gnome Sessions thing, you could get around the root-user issue simplying by calling the script with gksudo; that is, the command that you enter into Sessions would be something like:
```

gksudo /home/you/Desktop/yourscript.sh
```

You may also want to end the script with the command "exit" so that your root privileges get dropped when the script is finished.  I don't think this matters--I think the script will run in its own shell, which will close when the script is done--but it wouldn't hurt just to be safe.

---

