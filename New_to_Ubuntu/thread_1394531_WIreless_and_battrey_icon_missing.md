---
title: "WIreless and battrey icon missing"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by gerryex on 2010-01-30
Hi ALL,
 
I am very new to Ubuntu but am familier with OS's in general. I loaded the latest version (9.10, I believe) onto an Acer laptop and its been wroking fine. Just today I had to change out my router to the standard one used by Verizon FiOS, which includes wireless. After some stumbles got everything to work pertty well, but then I had a problem.
 
When I booted up in the panel at the top, which used to show an icon for the battery and for the wireless connection now showed two icons for the speaker level next to the wireless icon. One of the speaker icons worked as expected but the other one didn't do anything. So I right clicked on it and deleted it and it went away along with the wireless icon. Now I can't seem to get either one back.
 
I did go into the power management app in the main menu and did specify that the icon show all the time but that didn't help. I also right clicked on the panel and looked at the available things to add but neither the battery nor the wireless icons were listed.
 
The other thing is where can you go to make changes to the wireless setup if the icon is missing. Shouldn't there be some other way to get to the wireless setup?
 
Anyway, any help would be appreciated.
 
Thanks,
Gerry

---

### Post by NightwishFan on 2010-01-30
Press alt+f2 and type:
```
killall gnome-panel
```

Is your panel still incorrect? If so, open a Terminal under Application -> Accessories and type:
```
killall nm-applet && nm-applet
```

Did the network applet show up? Please print any error messages in the terminal.

---

### Post by gerryex on 2010-01-30
> **NightwishFan said:**
> Press alt+f2 and type:
```
killall gnome-panel
```
 
Is your panel still incorrect? If so, open a Terminal under Application -> Accessories and type:
```
killall nm-applet && nm-applet
```
 
Did the network applet show up? Please print any error messages in the terminal.
 
 
Hi NightwishFan,
 
Thanks for the suggestion, but isn't "killall" going to remove the panel? I don't want to do something that I won't be able to get back to.
 
Thanks,
Gerry

---

### Post by NightwishFan on 2010-01-30
It should restart automatically. If you are unsure, then use:
```
killall gnome-panel && gnome-panel
```

---

### Post by migi on 2010-01-30
You might have removed the notification area when you tried to remove the speaker. Try right clicking the gnome-panel/add to panel/Notification area. That might at least bring back the missing icons again, but might not solve the problem with two speaker icons.

---

### Post by gerryex on 2010-01-30
> **NightwishFan said:**
> It should restart automatically. If you are unsure, then use:
```
killall gnome-panel && gnome-panel
```
 
Hi NightwishFan,
 
Yes, you were right, the panel restarted almost instantly. Unfortunately the network and battery icons were still not there.
 
If I remember my old Unix the "&&" tells the shell to execute the stuff following it as a new command, so I assume that should restart the applet, but all I got were a bunch of messages and the command does not seem to finish. Here are some of the messages:
 
** (nm-apples:4397): DEBUG: foo_client_state_changed_cb
... DEBUG: old state indicates that this was not a disconnect 9
... DEBUG: going for offline with icon: notification-network-wireless-disconnected
 
 
I got several of these messages but the comman promt never comes back. When I go to close the terminal it tells me that the command has not finished but it let it sit for several minutes and it still has not finished! So I just closed it.
 
So for now I still don't have the battery nor wireless icon. Is there some way I can get to the wireless setup without the icon. Also if there is anything else you can suggest I would appreciate it!
 
Thanks,
Gerry

---

### Post by NightwishFan on 2010-01-30
The app running in the terminal will not close, as it is a GUI app. That was the correct behavior. Perhaps you have some packages missing (though I doubt it, try this in a terminal:
```
sudo apt-get install ubuntu-desktop && sudo apt-get -f install
```

After this command runs, log out and then back in.

---

### Post by gerryex on 2010-01-30
> **migi said:**
> You might have removed the notification area when you tried to remove the speaker. Try right clicking the gnome-panel/add to panel/Notification area. That might at least bring back the missing icons again, but might not solve the problem with two speaker icons.
 
Hi migi,
 
Yes! That got me back the battery and speaker icon, but I still don't have the wireless icon. And without that the system keeps trying to tie into my neighbor's wireless rather than my own and I know when the wireless icon was there before I was able to tell it to tie into my wireless and it worked. So without the wireless icon I can't seem to tie into my own wireless network.
 
Thanks,
Gerry

---

### Post by gerryex on 2010-01-30
> **NightwishFan said:**
> The app running in the terminal will not close, as it is a GUI app. That was the correct behavior. Perhaps you have some packages missing (though I doubt it, try this in a terminal:
```
sudo apt-get install ubuntu-desktop && sudo apt-get -f install
```
 
After this command runs, log out and then back in.
 
Hi NightwishFan,
 
That looks rather intimidating!!! Before I try that I just want to say that the wireless icon WAS there and functioning properly so what ever software needed was there. All I did was right click on it and remove it. If you still think I should try it I'll do that first thing tomorrow as I have to shut down now.
 
(Is there some thing simpler I could try?) Also, is there some other way to get to the wirless setup so I can tie into the proper network.
 
Thanks for all your help,
Gerry

---

### Post by migi on 2010-01-30
I'm not sure but it could be that you killed the network-applet while executing killall before. You could try to just write nm-applet& in the console. But then it will disappear again if you close the console window. Luckily if that is the case a simple logout and login should autostart the applet for you again.

---

### Post by NightwishFan on 2010-01-30
Migi is correct. I assumed above that the problem was more sinister, related to GDM somehow. Once I had the icons at the bottom of the login screen appear in my gnome panel along with two speaker icons.

Sorry to lead you along. #-o

---

### Post by gerryex on 2010-01-30
Hi ALL,,

Well its back!!  The last thing I did before I shut down was to add the notification area back in and I got the speaker and battery back but still didn't have the wireless icon.  I wanted to try migi's suggestion, but I had to shut down.

Of course my technical curiosity got the best of me and I turned it back on and low and behold the wireless icon was back again!  So are all three icons part of the notification area?  I still would like to know how one would make changes to the wireless setup without the icon.

Anyway, thanks to all for all your help!!!

Gerry

---

### Post by NightwishFan on 2010-01-30
You could likely use the command line or an alternate network managing program. The notifications in the panel (in Karmic) include the sound, power, and network. It is like a nesting ground for programs that want their status shown at a glance, or easy access.

---

### Post by Tony.B on 2010-02-03
Hello.
I have exactly the same problem, also on my Acer laptop.
I've managed to get the speaker and the wireless icons back, but my battery icon is still missing. Can someone please tell me, in VERY simple language, how to get the battery icon back?
Many thanks,
Tony

---

### Post by gerryex on 2010-02-03
> **Tony.B said:**
> Hello.
I have exactly the same problem, also on my Acer laptop.
I've managed to get the speaker and the wireless icons back, but my battery icon is still missing. Can someone please tell me, in VERY simple language, how to get the battery icon back?
Many thanks,
Tony
 
Hi Tony,
 
If you have the speaker and the wireless icons back, then I think all you need to do is go to (I'm doing this from memory as I don't have the Acer on and have to leave shortly) something like Power Management which is in the main menu either under Preferences or Administration. One of the options is to display the battery icon all the time.
 
Good luck,
Gerry

---

### Post by Tony.B on 2010-02-04
Thanks for trying to help, Gerry, but that doesn't work on my computer.

System -> Preferences -> Power Management  gives me a screen that says
[INDENT]Installation Problem
The configuration defaults for GNOME Power Manager have not been installed correctly[/INDENT].

Also, when I switched on, the Update Manager asked me to update & I immediately got another error message:
[INDENT]E:dpkg was interrupted. You must manually run 'sudo dpkg --configure -a' to correct the problem[/INDENT]

I have no idea what either message means.  I presume that, at some stage, I have inadvertently clicked on something I shouldn't have.

Any help would be gratefully received.

Thanks & regards,
Tony

---

### Post by Tony.B on 2010-02-04
OK I found out how to fix it.

I went back on earlier threads and found that I needed to go to
[INDENT]Applications -> Accessories -> Terminal[/INDENT]
to enter the sudo code.

When I'd done this, I went to
[INDENT]System -> Administration -> Update Manager[/INDENT]
and updated my system.

The Battery Icon came back by magic, and the Wireless Icon is still there.  All ok.

Cheers,
Tony

---

### Post by gerryex on 2010-02-04
> **Tony.B said:**
> OK I found out how to fix it.

 
Hi Tony,
 
Glad you got it fixed!
 
Many years ago I worked with Unix, which was the precursor to Linix. In those days there was no GUI to work with - only the command prompt (which is now called the Terminal). The command language of Unix, and now Linix, is VERY hard to get right and although I have worked with many software systems I had to go to our Unix expert to help me with some commands.
 
With Linix, there is now a GUI, but unfortunately when things go wrong most often you have to fall back to the Terminal and commands. This is one of the reasons, in my opinion, Linix or any variant of Unix will never become mainstream.
 
But its something to play with!!!
 
Gerry
 
P. S. I started another thread as although I now have a wireless icon that does not disappear, I am getting a low strength reading and dropouts with the wireless. I know its Ubuntu because when I boot back to Win 7, the wireless strength never drops under 90% and I have not yet lost the signal. So far I haven't received too much help on that issue!

---

### Post by Tony.B on 2010-02-05
Thanks, Gerry. I hope you get some help from the forum. It won't be me, I'm afraid: I didn't grow up with this technology. When I was at school, calculators hadn't been invented. I'm trying to learn all about it, and finding it fascinating, but I'm a long way from being able to offer advice. I wish you good luck.
Cheers, Tony

---

