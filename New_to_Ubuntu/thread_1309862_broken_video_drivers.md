---
title: "broken video drivers"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by jcats on 2009-11-01
this morning I tried to upgrade 8.10 to 9.04 through the update manager. The update went well, except that the best video resolution I could get was 1280X1024. I have a Dell E228wfpc (native resolution is 1680X1050). So as I have done with every other upgrade, I fired up Envy, let it pick the divers (ATI) and installed. It rebooted, and when it came back up, the desktop is all messed. The screen is divided in half, horizontally. The bottom half is all snow. The top half  shows 2 small Ubuntu's (just like the one that shows on boot up.)
The system is dual boot, and the Windows side works fine.
Also, I have lost mouse/keyboard function.
I'm thinking that the video drivers is causing this. But I don't have a clue as to how to remove it.
Please, any help would be appreciated.

jcats

---

### Post by Zoot7 on 2009-11-01
I'd say the best thing for you to do is to boot into recovery mode and select "Xfix" to reset xorg.conf to use the default vesa drivers.
Then use envy to remove the driver and then remove envy as directed here:
[http://albertomilone.com/envyngfaq.html#A]("http://albertomilone.com/envyngfaq.html#A")

After that install the ATi drivers manually using the following guide:
**[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide")**

What kind of card have you? Bear in mind that some of the ATi cards require you to downgrade X under Jaunty to let you use the fglrx driver.
[http://ubuntuforums.org/showthread.php?t=1171445]("http://ubuntuforums.org/showthread.php?t=1171445")

---

### Post by jcats on 2009-11-01
First off, I apologize for the double post. I posted, but it never showed for several minutes, so I posted again. sorry :oops:

I'm going to respond to both posts here. Thanks Zoot7 and Turtle.net for writing. I'm afraid my newbie-ness is showing.
Zoot- in recovery, I went to "drop to root shell" and put in Xfix, but got no command found. Am I doing this in the right place?

Turtle-I followed your commands and now the screen flashes a couple of times and then goes in "no signal". I think I screwed something up there.

As a new development-Ubuntu went into forced chk disc and it faied for some corrupt files. I only showed for a couple of seconds, so I couldn't read it all.

How do I reboot from the recovery screens?
Sorry to add to this. thanks again for the help

---

### Post by Zoot7 on 2009-11-02
Select the recovery mode option from the boot menu, that should bring you to another menu, there should be an option there "Xfix", select that; there's no need to drop to a shell prompt.
That option was there in Ubuntu since I started using it with Feitsy and right up to Jaunty, I'm not sure whether it's in Karmic or not.
Failing that, drop to the shell and run:
```
sudo dpkg-reconfigure xserver-xorg
```

---

