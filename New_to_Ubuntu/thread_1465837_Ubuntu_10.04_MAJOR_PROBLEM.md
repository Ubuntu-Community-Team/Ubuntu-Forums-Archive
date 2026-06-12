---
title: "Ubuntu 10.04 MAJOR PROBLEM"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by ryandavis33 on 2010-04-29
i just installed Ubuntu LTS and every time i login it takes me back to the login screen. i can never see the desktop.

What can i do???:confused::(

---

### Post by Warthaug on 2010-04-29
I too am having the exact same issue.  I tried following this advice:
[http://art.ubuntuforums.org/showpost.php?p=9189840&postcount=8](http://art.ubuntuforums.org/showpost.php?p=9189840&postcount=8)

The first command did not work as the folder/file do not exist:
```
chmod 700 /tmp/gconfd-$USER/
```

The second command did work, but I'm still stuck in an infinate loop of log-in screens:
```
cp -r ~/.dbus/session-bus ~/.dbus/session-bus.bak
rm -rf ~/.dbus/session-bus
```

Please help!!!!!!

Bryan

---

### Post by Geoff918 on 2010-04-29
I had an odd experience with this several test versions ago.

I found a potential work-around?

1) Ctl-Alt-F1
2) Input userid
3) Input password
4) Ctl-Alt-F7

Should let you in, might have you log-in once more. But, this always worked for me.

Thanks,

Geoff

---

### Post by Warthaug on 2010-04-29
Geoff, I tried your advice.  I can log in with my username/pasaword in the text mode, but when I ctrl-alt-F7 I am stuck at the text that appears immediately before the login screen (seems to be stuck on "Checking battery state..., other text reads things like "Setting sensor limits").

Still stuck in infinite-login-loop hell!

Bryan

---

### Post by taino205 on 2010-04-29
Same here, I just did the upgrade and after restarting the system I got into the infinite loop. I also tried the steps above but did not help. I was upgrading from 9.10. This really sucks, I will probably just install from scratch after I can get some stuff out of the system.

---

### Post by ryandavis33 on 2010-04-29
i dont know why but i cant see anything when i press ctl alt whatever...is there anyother fix for this??

---

### Post by Geoff918 on 2010-04-29
You should be able to see *something*. Perhaps there's a major issue with the graphics card?

I mean, I can think about booting into failsafe command line and then running

startx

(which will start the x.org graphics server)

---

### Post by Sealbhach on 2010-04-29
Some people had this problem with Ubuntu 9.10 as well

[http://ubuntuforums.org/showthread.php?t=1338879](http://ubuntuforums.org/showthread.php?t=1338879)

Seems to be a problem with the screen resolution, I haven't looked through the entire discussion there, but it should point you in the right direction.

.

---

### Post by HalfEmptyHero on 2010-04-29
Did you try clicking and making sure gnome is selected as the session.

---

### Post by markoturso on 2010-04-30
I have this problem too. Ubuntu logon screen appears (Ubuntu logo with dots that represents loading), then disappears, everything's black, actually monitor is put in a stand by mode. I even reinstalled it, same thing. To be worse, I've done clean install, erased my 9.10...now, this SUCKS totally. I really can't describe how I'm pissed off. I use Ubuntu since 6th version, but this problem is ridiculous. I tried safe mode, demo mode and all other options, same thing, monitor goes to stand by, end of story, I guess it's when logon screen should show. 
I tried what Geoff918 said with no result. I don't see point testing solutions for problems that users had with 9.10, because I didn't had that problems with 9.10, it's obvious that this problem is something new.
I hope someone could help, I don't have any idea what to do.

---

### Post by Peter09 on 2010-04-30
try going into command line in safe mode and type
 
```
startx
```

---

### Post by MadMikeyB on 2010-04-30
> **Warthaug said:**
> Geoff, I tried your advice.  I can log in with my username/pasaword in the text mode, but when I ctrl-alt-F7 I am stuck at the text that appears immediately before the login screen (seems to be stuck on "Checking battery state..., other text reads things like "Setting sensor limits").

Still stuck in infinite-login-loop hell!

Bryan

This seemed to be a problem with dpkg for me, I had to go to the root shell and manually sudo dpkg --configure -a

It then continued installing the packages and booted into lucid. To be safe I ran sudo apt-get update && sudo apt-get upgrade upon the reccommendation of a friend.

---

### Post by Warthaug on 2010-04-30
I have "solved" the problem by reinstalling 10.04 and setting it to auto-login.  Sucks loosing the security, but it'll do until a confirmed fix is available.

Bryan

---

### Post by Bodsda on 2010-04-30
> **Warthaug said:**
> I have "solved" the problem by reinstalling 10.04 and setting it to auto-login. Sucks loosing the security, but it'll do until a confirmed fix is available.
 
Bryan
 
I would follow Peter09's advice about running the startx command. This way you may be able to see output from GDM as to why it is looping (you may need to pipe output to a text file)
 
Bodsda

---

### Post by Sealbhach on 2010-04-30
> **Warthaug said:**
> I have "solved" the problem by reinstalling 10.04 and setting it to auto-login.  Sucks loosing the security, but it'll do until a confirmed fix is available.

Bryan

if someone has physical access to your machine, it's game over anyway. I just use my computer at home so I always have it on auto login. They still need a password to open the keyring and access the internet.

.

---

### Post by Eycks on 2010-05-01
I upgrade from 9.10 to 10.04. When I get to the logon screen I enter my password for my user name.  After a few screen changes I get the logon screen again.  I tried what was recommended above but nothing works.  I am able to get to the text the recovery screen.  When I ran startx I got a lavender screen but nothing else.

---

### Post by Peter09 on 2010-05-01
What graphics card have you got.
Do
```
lshw -C video
```
and post the output.

---

### Post by Warthaug on 2010-05-02
The output of lshw is:
```
  *-display:0
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:29 memory:f6e00000-f6efffff memory:e0000000-efffffff(prefetchable) ioport:eff8(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f6f00000-f6ffffff
```

I'm on a laptop, so the second output is the VGA/HDMI connector.  It all runs through the same video card.

Thanx

Bryan

---

### Post by Peter09 on 2010-05-02
When in recovery mode can you use the option for using the low res graphics mode. Then check if you can select a third party driver in System->Admin->Hardware

---

### Post by bentrider1957 on 2010-05-02
I had the same issue.  It is a GFX error in Grub2.  See if this helps:

1. Boot from Install CD and when the icons of the man and keyboard come up, press the spacebar.

2. When you do this, a menu will come up to select your language.  In this case, I selected English.  I imagine you would too.  After you select the language, your menu will pop up.

3.  Select the FIRST option on the menu to Use Ubuntu without install.    At this point press the F6 key.

4.  A command-line will come  up.  You will see at the end of that command line -quiet spash.

5.  Delete everything from the word "quiet"

6.  Type the words:     1915.modeset=0 xforcevesa 

7.  Hit return and it should boot.

Once booted, load the proper video drivers.  In my case, I went directly to AMD/ATI.  However, I have read that Nvidia cards do the same thing.

Post back if this works for you or not.





> **markoturso said:**
> I have this problem too. Ubuntu logon screen appears (Ubuntu logo with dots that represents loading), then disappears, everything's black, actually monitor is put in a stand by mode. I even reinstalled it, same thing. To be worse, I've done clean install, erased my 9.10...now, this SUCKS totally. I really can't describe how I'm pissed off. I use Ubuntu since 6th version, but this problem is ridiculous. I tried safe mode, demo mode and all other options, same thing, monitor goes to stand by, end of story, I guess it's when logon screen should show. 
I tried what Geoff918 said with no result. I don't see point testing solutions for problems that users had with 9.10, because I didn't had that problems with 9.10, it's obvious that this problem is something new.
I hope someone could help, I don't have any idea what to do.

---

### Post by KirbySmith on 2010-05-02
I can concur that in 9.10 my nVidia card was not friendly to the unsophisticated Ubuntu installer - me.  My 10.4 beta live cd wouldn't show me the safe graphics mode, so I couldn't test the following process out.  But anyway...

To install 9.10, I had to install from the live CD desktop after starting the live CD in safe graphics mode.  For me, this would generate an install that booted in safe graphics mode, from which I could function and then download the nVidia drivers I needed.  And my configuration is 4 years old, so it isn't yesterday's hot card that is the problem.

I sense from the many versions of this topic that I see here that Ubuntu's installer needs to detect configurations that are problematic and install in some failsafe mode.  Once the desktop is up, a message would inform the user of the steps needed to upgrade the video.  These issues affect the reputation of Ubuntu and Linux for those who are just starting.

kirby
___________
with a little hacking, it just works

---

### Post by Macchi on 2010-05-02
> **KirbySmith said:**
> 
with a little hacking, it just works

I am not that lucky, despite reasonable hacking my Intel graphics on one of the laptops are still failing on Lucid final.  This is frustrating for a final Long Term Support release! It only works with an earlier kernel from Beta 2.

---

### Post by bitter_mike on 2010-05-06
I figured this out last night. I posted my solution here: 

[http://ubuntuforums.org/showthread.php?t=1473152&highlight=login+loop](http://ubuntuforums.org/showthread.php?t=1473152&highlight=login+loop)

Had to reinstall GDM, and gnome-session and that pretty much fixed everything.

Hope this helps.

---

### Post by Woonjas on 2010-05-09
I ran into the same problem after upgrading from Karmic to Lucid (64 bit).

Initially screen resolution was set wrong, which was fixed easily enough, but the problem remained.

Through TTY login I can get into X:
CTRL-ALT-F1
login with my account
sudo service gdm stop
startx

I then need to use Compiz-Fusion to Reload Window Manager before windows show the title bar and controls

I noticed that creating a new user account, and then trying to login using this new account works fine from the GDM login screen, without having to perform the window manager reload, so it must be something to do with the prefs stored in my home dir, just not sure which .xxxx files/directories I need to remove/modify

---

### Post by Peter09 on 2010-05-09
copy .profile to profile_saved and logout and log in again.

```
mv .profile profile_saved
```

---

