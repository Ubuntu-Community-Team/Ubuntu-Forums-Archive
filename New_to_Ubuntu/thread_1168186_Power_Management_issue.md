---
title: "Power Management issue"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by don_diego on 2009-05-23
I installed Ubuntu 9.40 on an older laptop as its only OS about 3 weeks ago. In the beginning it displayed the battery on the top panel. It worked perfectly, showing the battery's status or if it was running off AC. Unfortunatley later,  probably when I was setting up the Wi-Fi PCMIA card, it disappeared. But now after adding it back to the panel it always shows that the battery is 0% charged, regardless whether the laptop is on battery or AC power. 

I noticed that under System > Preferences > Power Management there are only two tabs (AC powoer and General), none for Battery. 
 
In another thread it was suggested that perhaps my power management had been messed up and somebody might be able to help me restore it. (Sorry, being a total newbie I haven't figured out to provide a link to this thread.) 

I would very much appreciate it if somebody could help me to restore power management and the battery status monitor to proper working order. 

TIA

---

### Post by JGD on 2009-05-23
Since you mention that your laptop has only been setup with 9.04 Jaunty Jackalope for 3 weeks it may be easier to just do a reinstall.  If you want to keep the installation that you have you might try going into: 

System > 
Administration  > 
Synaptic Package Manager >

Then mark for reinstallation: 

acpi
acpid
apmd
gkrellm-ibam
gnome-power-manager
guidance-power-manager
ibam
kde-guidance-powermanager
laptop-mode-tools
libapm1
libplasma3


Reinstalling these may resolve your problem.  Report back with how you made out.  I have 4 systems setup and running 9.04, I like it a lot!


jgd

---

### Post by don_diego on 2009-05-23
> **JGD said:**
> Since you mention that your laptop has only been setup with 9.04 Jaunty Jackalope for 3 weeks it may be easier to just do a reinstall.  If you want to keep the installation that you have you might try going into: 

  You are right, I'll take the eay way out - reinstall since I have done nothing with it other than trying to familiarize myself with Ubuntu and will report back afterwards.

Thanks.

---

### Post by don_diego on 2009-05-24
OK, it's been reinstalled and I've run Update Manager, so it is up to date.

Surprise: the Battery Charge Monitor icon did NOT show up on the top panel as it had previously after the original (first-time) installation. When I added it, instead of giving the battery's status it just says "System is running on battery power - 0 minutes (0%) remaining" even though the laptop ts actually running on AC power. 

Another weird thing: System > Preferences > Power Management shows 2 tabs - AC Power and General, there is no tab for Battery Power. 

I don't know if it has any bearing on this but I will mention that in order to make my LIve CD work I have to use the F6 options acpi=off, edd=on and Free software only. If I don't check those the Live CD does not work on this old Dell Inspiron 2650.

TIA for any help to get this working as it should.

---

### Post by zubin71 on 2009-05-24
do make sure you submit a big report wen you hav time!

---

### Post by JGD on 2009-05-24
Hi Don,

Have you made any changes to your BIOS setup between your first and second install?  Power manager will not work without ACPI (Advanced Configuration and Power Interface).  Look in your BIOS setup screens and enable ACPI before you boot into system startup.  Once you are able to enable ACPI you may need to reinstall 9.04.  The ACPI specification was first released in December 1996.  If your Dell is older than that your BIOS may not include functionality for it.  If this is the case you will need to pursue a BIOS update.  Good luck and report back, I'm following the thread!

jgd

---

### Post by don_diego on 2009-05-24
Hi JGD,

I believe you have discovered the reason - there is no reference to ACPI in the BIOS! I bought this laptop used and heaven knows how old it may be. 

I am going to try my best to see if it can be updated. I may not be able to accomplish much due to the long holiday weekend but please keep following this thread. I will post again ASAP with any results or the lack thereof. 

Thanks for staying with me.

---

### Post by JGD on 2009-05-24
Hi Don,

Glad to try and help out.  What I can't understand is why it worked on your 1st install but not on your second.  Did you have the PCMCIA WLAN card installed the first time you installed?  How about the second time?   

First, find out which BIOS and version you have, it says on bootup.  Then go to the Dell Support area on their websites and search for updates.  You may end up having to try the website of the maker of the BIOS:  Award, AMI, Phoenix, etc. to see if there may be updates lurking there.  Good luck!  I'll stay tuned...


jgd

---

### Post by don_diego on 2009-05-24
> **JGD said:**
> Glad to try and help out.  What I can't understand is why it worked on your 1st install but not on your second.  Did you have the PCMCIA WLAN card installed the first time you installed?  How about the second time?   

Well JGD, as to whether that card was inserted during the first install is a good question but you are asking a 78-year old guy whose memory isn't what it used to be. However, most likely it was in place because that's where it was when I picked up up this "bargain". I can say with certainty that it was not inserted during the 2nd install because in the meantime I had discovered that it was probably as old as the laptop (it is an 801.11.b) and by that time I had connected via cable. 

> First, find out which BIOS and version you have, it says on bootup.  Then go to the Dell Support area on their websites and search for updates.  You may end up having to try the website of the maker of the BIOS:  Award, AMI, Phoenix, etc. to see if there may be updates lurking there.  Good luck!  I'll stay tuned...I had no problem finding a BIOS update (they had only 1 available) on the Dell website and successfully updated the BIOS. Of course, this was only possible via Windows which I had to reinstall it so that took a while.

The result of my labors was disappointing to say the least: while the BIOS version, which had been A05, was upgraded to A13 but (and it is a BIG BUT) it still does not include any way to control power management. 

Guess the only thing to do is to forget about this Dell and switch to my Toshiba which is a current model.

Thanks for your patience listening to my sad tale and trying yo help. I very much appreciate it.

---

### Post by don_diego on 2009-05-25
JGD, I hope you are still reading this thread because I made a big mistake. It wasn't when I first installed 9.04  - it was a few days before when I first installed 8.10 that the battery monitor was displayed. Sorry about misleading you. 

Switched back to 8.10 and  - voila - there it is again! Guess I'll stick with Intrepid Ibex as I don't think it's absolutely necessary to have the latest version for learning.

---

### Post by JGD on 2009-05-26
Hi Don,

Thanks for the update.  I'm glad to hear that Intrepid made your system work for you.  Now one of us should file a bug report about Jaunty not supporting your hardware as Intrepid does.  I really can't understand why that would be.  Enjoy Ubuntu, I'm sure you'll love it.  


jgd

---

### Post by don_diego on 2009-05-26
> **JGD said:**
> Hi Don,

Thanks for the update.  I'm glad to hear that Intrepid made your system work for you.  Now one of us should file a bug report about Jaunty not supporting your hardware as Intrepid does.  I really can't understand why that would be.  Enjoy Ubuntu, I'm sure you'll love it.  


jgd
Hi JGD, 

Needless to say I am enjoying Ubuntu very much but I do have some questions in regard to filing a bug report. After reading the sticky on this subject it would appear that it would be most meaningful if I were able to include the info gathered by Apport. Correct? Alas, since Jaunty is no longer installed this is not an option unless I were to reeinstall it. 

Which brings me to question 2: Is it possible to do that without removing Intrepid, in other words have 2 versions in this old laptop simultaneously? (CPU 1.2 GHz, 512 RAM, 20 Gb HD) 

And question 3: Is it worth filing a bug report since I may be the only one who has ever tried running Jaunty on such an ancient Dell Inspiron 2650? 

Looking forward to your thoughts on this matter. Thanks.

---

### Post by Miljet on 2009-05-26
The only limitation to how many distributions you can install is available disk space. 20 gb should be plenty for two distributions/versions.

Additional distributions have no effect on CPU or RAM usage since only one operating system runs at the time.

---

### Post by don_diego on 2009-05-26
> **Miljet said:**
> The only limitation to how many distributions you can install is available disk space. 20 gb should be plenty for two distributions/versions.

Additional distributions have no effect on CPU or RAM usage since only one operating system runs at the time.
Thank you Miljet. I take this to mean that you agree a bug report using *Apport *would be more meaningful than just a verbal description of the problem I encountered?

---

