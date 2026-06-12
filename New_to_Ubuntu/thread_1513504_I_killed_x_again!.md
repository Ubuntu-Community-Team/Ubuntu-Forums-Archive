---
title: "I killed x again!"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by pottzie on 2010-06-19
This is a new post since I just marked the old one solved. I mucked around trying to get an updated nvidia driver, and somehow hosed my (mom's!) computer so that all I have is the splash screen and mouse pointer. I ran "dpkg fix broken packages" and after rebooting everything worked. I shut down her computer to swap out monitors, and when I rebooted...just the splash screen and mouse pointer!
 Any suggestions?

---

### Post by pottzie on 2010-06-19
I'm getting antsy, and while I'm waiting, I'm going through some thoughts.
 The title says that I've screwed up X. Have I? I have an image, and a blinking mouse cursor. Is X working, and I have another problem? 
 One thing that comes to mind is that everytime I've installed Ubuntu, there's a box asking for my password before the system starts. It's almost as if that box was missing, and the system won't load until I somehow log in...maybe.
 Other thoughts come from installing Arch a few weeks back. Stuff like HAL, daemons for gnome, and editing files with nano.

---

### Post by Windows Nerd on 2010-06-19
You have probably gotten no replies because I think most everyone is not sure what you did to mess it up, and what your problem is. Myself included. Maybe you could clarify these two things, then we could help you out?

Scott

---

### Post by pottzie on 2010-06-19
By now it's kind of a chicken/egg problem! I don't know either! Having said that, here's what I remember.
 I thought I had a problem because on the computer this is on, the image on screen was horrible; it skewed in at the sides and top and bottom, and no matter what I did using the buttons on the monitor, the best I could get was an image that bowed in on three sides and went off screen completely on one side making web pages unreadable.
 I saw a tutorial about installing nvidia drivers, and downloaded a driver but (pardon the all caps) DID NOT INSTALL. The instructions didn't say to yet and I thought that would happen later during the process. The instructions did have a line about blacklisting earlier drivers and I did that. All of this just copying what was on screen to the terminal and hitting enter. The last thing that I did was to reboot, per the guide. If I remember correctly, it was "just in case." When I rebooted, the reddish screen (Ubuntu 10.04) and mouse cursor, but no gnome and no more icons or system for all practical purposes. 
 I was able to run "dpkg fix broken packages" from safe mode during boot, and after doing that the system worked. I had to reboot to start it, and it worked OK. Now after changing to another monitor, I'm back to the reddish screen and mouse arrow.
 I was just reading Wikipedia about X:
[http://en.wikipedia.org/wiki/Xorg.conf](http://en.wikipedia.org/wiki/Xorg.conf)
 In it it says "The file xorg.conf is a file used for configuring the X.Org Server. While typically located in /etc/X11/xorg.conf, its location may vary across operating systems.
For a long time, editing xorg.conf was necessary for advanced input devices and multiple monitor output to work correctly. This was regarded to be a major usability obstacle. In modern systems this is seldom necessary, thanks to input hotplugging and the XRandR extension integrated into new X.org releases. It is still needed for devices from some manufacturers, notably NVIDIA and Wacom, whose drivers fail to provide support for those technologies. This also cause confusion or even problems when changing an option that is no longer explicitly entered is required."

 Great. I've run xorg.conf before doing the "fix broken packages," and it said that there was a file that replaced the x-11 with another file..I assume. And I'm stuck wondering if anything I said in the second post is what I'm really up against. Seems that there should be something I can run in the terminal to show what the system itself sees. List-something, file system check (isn't that what fix broken packages was?)
 I'm at my house now, and I'm going to attempt going at it with another live cd that I have here to see if that can boot, as one I tried earlier couldn't.

---

### Post by J V on 2010-06-19
If there is a compatible driver for your video card, you can install it through system > administer > hardware drivers, now I'm not sure what you've done, but if you can undo it, undo it.

If you can't, you'll have to reinstall (No biggie, will take a lot less time this time)

---

### Post by pottzie on 2010-06-19
Reinstall did the trick. I was hesitant because there's "stuff" on the Windows partition. Deleted the ext 4 and swap partitions and all is well.
 Now if I can just leave well enough alone....

---

