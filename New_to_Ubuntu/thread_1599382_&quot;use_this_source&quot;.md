---
title: "&quot;use this source&quot;"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by jengurule on 2010-10-17
I am 'bout ready to pull my hair out!  I am new to Ubuntu, and so far I have not found it to be user friendly.  However, I am willing to give it a chance.  With that said, I am trying to install software, and all I can get is a button that states "use this source".  I click on it, the authenticate window appears, and I place my password in, click authenticate button, and to the left it says "in process" and then it reverts back to the same thing with the "use this source" button.
 
Also, how do you make your own wireless connection a priority?  I keep getting disconnected.
 
Thank for your time!

---

### Post by greyfox1 on 2010-10-17
Hello, could you explain what program you are trying to install as well as exactly how you are attempting to do it? For example, did you download the software from the internet someplace, or are you using the Ubuntu Software Center (which can be found under the Applications menu)?

---

### Post by jengurule on 2010-10-17
I am just trying to install anything at the moment just to figure it out. As a test of how to use the function, 
 
I go to "applications", 
 
proceed to "Ubuntu Software Center", 
 
then click on "games", 
 
then choose "card games", 
 
I choose "Hearts", by clicking on it, 
 
a button appears that says "more info", so I click on that, 
 
then there is another button that appears that says "use this source", 
 
an authenticate box appears, I enter my password and click the "authenticate" button, 
 
then it says "Available from the 'universe' source and the same button "use this source appears"  It is a never ending battle.
 
This happens to anything I attempt!

---

### Post by jengurule on 2010-10-17
Also, I can't seem to get online...I have clicked the "work offline" button under "file" in Mozilla FIrefox.  Can't even get Google.  Tells me "Server not found"    The wirless icon on the upper right area shows I am connected.

---

### Post by greyfox1 on 2010-10-17
EDIT: Just saw your update about not being able to get online. That must be why everything is failing. If you can get online successfully, you probably won't even need my original instructions (below).

Unfortunately, I'm not the most up to date on how to troubleshoot wireless issues. However, if you could start by posting what brand/model your laptop is, we can try to get the ball rolling.

------

Thank you for the additional information. The Software Center is trying to enable some additional software sources so that you can install Hearts and apparently, it's failing. [Here is a guide]("http://www.psychocats.net/ubuntu/sources") on how to do it manually (it's a one-time process).

What it boils down to is bringing up the Software Center, choosing Edit-Software Sources, and pasting in the line

```
deb http://packages.medibuntu.org/ maverick free non-free
```

This is assuming you just installed the latest version of Ubuntu which is 10.10, the "Maverick Meerkat". Step-by-step instructions are in the link I posted. Good luck!

---

### Post by Quackers on 2010-10-17
Can you plug in an ethernet cable between your pc and your router then go to System > Admin > Hardware drivers (or Additional Drivers) and see if any drivers are advised.

---

### Post by jengurule on 2010-10-17
I rebooted and when it restarted, I was instantly able to get online.  Okay, now that I can get online, I am now trying to figure out the applications and installing software part.  Am I still needing to relocate my computer next to the router to get an ethernet connected, or was that advice only for the availability in getting online itself?

---

### Post by Quackers on 2010-10-17
That was just to get you online and to download any drivers that may or may not be needed by your system.

---

### Post by jengurule on 2010-10-17
So Quakers, you have any advice in regards to installing the software via applications, as I am still having the orignal problem.

---

### Post by Quackers on 2010-10-17
When you are in the Card games part of Ubuntu Software Centre go to full screen display. Is there a box on the right hand side that says Install? If so click on it.
That box can be out of screen if the screen is not large enough.

---

### Post by jengurule on 2010-10-17
Okay, so please advise as how to keep online!  I keep getting disconnected!

---

### Post by Quackers on 2010-10-17
That could be a driver issue or a hardware issue.
If you go to System > Admin > Hardware drivers or it may be called Additional drivers depending on which Ubuntu you are running. It will check whether any new drivers are available for your hardware. Please report back the outcome of that.
Can you please inform us of your wireless card name and model please?

---

### Post by jengurule on 2010-10-17
Okay, I did the driver search as recommended and I came up with notice that says "No proprietary drivers are in use on this system".  I am not certain as to what you are referring to in your inquiry of the wireless card.  I have an adapter that I insert in the back of the tower.  It is a Cisco Linksys "G"

---

### Post by Quackers on 2010-10-17
Does it plug into a usb port and have a little aerial?

---

### Post by jengurule on 2010-10-17
Yes, it inserts into an USB port and looks similiar to a thumb drive.

---

### Post by Quackers on 2010-10-17
Could you please go to Applications > Accessories > Terminal and when the terminal opens type
lsusb   then press enter key.
Please copy/paste the resulting script in your next post.

---

### Post by jengurule on 2010-10-17
[EMAIL="gurule@gurule-Dimension"]gurule@gurule-Dimension[/EMAIL] - 3000:~S

---

### Post by Quackers on 2010-10-17
after this
gurule@gurule-Dimension - 3000:~S
type in lsusb (that's a lowercase L at the start, not a 1) and hit enter. This should produce a list in the terminal screen of all usb devices in your pc. Please copy/paste that list in your next post.

---

### Post by jengurule on 2010-10-17
Now th %*&#@& Firefox window won't open!!    Am having to reboot; AGAIN, and it says Firefox is not responding.  FYI: I appreciate your time.   This may take some time....as I am working off another computer.

---

### Post by Quackers on 2010-10-17
No problem.

---

### Post by omegamormegil on 2010-10-17
I have also seen the frustrating "use this source" problem.  The issue is a connectivity issue.  I was connected, but apparently the connection wasn't stable enough.  

Running sudo apt-get update gave me errors indicating that the update was failing.  The software center is trying to be a little too user friendly, in my opinion, because when the update fails there is no feedback to let the user know why clicking the "use this source" button did absolutely nothing.  

For the individual having this problem, perhaps you should try plugging directly into your router to see if the problem stems from a weak wireless signal.  Best of luck.

---

### Post by omegamormegil on 2010-10-17
Also, have you installed Ubuntu, or are you booting off of a LiveCD?  I saw a bug report indicating that this may not be working properly when using the LiveCD.

---

### Post by jengurule on 2010-10-17
OKAY!!!!
 
gurule@gurule-Dimension-3000:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1737:0077 Linksys WUSB54GC v3 802.11g Adapter [Ralink RT2870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Quackers on 2010-10-17
Ok, so your wifi adaptor is Linksys WUSB54GC v3 802.11g Adapter [Ralink RT2870]. I suspect the Ralink RT2870 is the chipset. I'll have a mooch around and see if there are any known problems with the driver.
Is the connection still dropping out, needing a reboot?
Also you said that Firefox froze. Is that a common occurrence and does any other programme do that?
Also which version of Ubuntu are you using?

---

### Post by jengurule on 2010-10-17
I have rebooted countless times!  I decided to reset the router, then go in and change the channel.  So far, since that time, it has not disconnected randomly.  *Fingers crossed*  It's been a whole 6 minutes and it is still connected!

---

### Post by jengurule on 2010-10-17
OH CRAP!!!!  That didn't work either!

---

### Post by Quackers on 2010-10-17
I've done some googling and a search in the Networking & Wireless section of the forum and although nobody seems to have had your specific circumstances there is a big thread there regarding the RT2870 drivers. Have a look at the thread and see what you can glean :-) Knowing what version of Ubuntu you are running would be better as the "fix" may be different.
I'm off to bed now, it's 1-30 am :-)  Good luck to you!

[http://ubuntuforums.org/showthread.php?t=1489883&highlight=RT2870](http://ubuntuforums.org/showthread.php?t=1489883&highlight=RT2870)

---

### Post by jengurule on 2010-10-17
Thanks for your help!  Godd night.
 
BTW it is Ubuntu 10.10

---

### Post by jengurule on 2010-10-17
I uploaded a CD and am NOT running live off of the CD

---

