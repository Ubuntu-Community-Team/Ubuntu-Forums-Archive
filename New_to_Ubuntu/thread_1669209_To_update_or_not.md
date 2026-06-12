---
title: "To update or not?"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by OldLes on 2011-01-17
Hi there. New here. I have been thinking of using Linux for about 10 years, but it would never do everything I wanted. (eg, canon scanner), and even now, I shall have to replace that scanner. This time I intend to succeed, so  I have just built myself a new computer. This is based on the Shuttle SN78SH7 which usesAMD has the GeForce 8200 chipset. I tried loading the recent Ubuntu, and Kubuntu, but the cmputer hung partway through. I later heard this was common, but that the Mandriva 2009 - 1 was OK, which loaded OK for me. Since I also had the Ubuntu 9.04, I tried that as well, and that loaded, so here I am.
I have now done the "critical updates", but avoided the "Update to Ubuntu 10.x" button.
Is this correct, would it crash me out, or would it be OK since I now have a working install.
I understand from what I read previously that the Geforce 8200 grphics was the problem.
I am also stuck with my Edimax wireless PCI, but I have seen the fixes on this forum, and a Unix expert pal is calling round tonight, so I hope that can be solved.
OldLes.

---

### Post by hansolo4949 on 2011-01-17
"if it ain't broke, don't fix it".

If everything is working just fine, I see no reason to upgrade unless you want some more eye candy (which I even think is in 9).

Quite honestly, as long as there aren't any features in 10.04/10.10 that you need, you should just stick with 9. After all, who wants to spend an afternoon fixing a computer just because you wanted some more eye-candy? (believe me, i've been bitten with something like that several times before because I wanted the "best" version of something;)).

---

### Post by rburkartjo on 2011-01-17
i agree old if it aint broken dont fix it. dont know how many times i have not followed that advise and spent a day or two fixing my system

---

### Post by Rex Bouwense on 2011-01-17
I too am a believer in if it ain't broke don't fix it (unless it seems like fun), but Jaunty (9.04) has reached its end of life.  There will be no more updates coming out for it.  Since you just installed I would recommend that you install 10.04 Lucid over your Jaunty install.  Lucid is a Long Term Support version and will be supported for three years.  So download 10.04, do the MD5Sum, burn the ISO to a CD or a flash drive, and install it in the same space that Jaunty now occupies.  Enjoy.

---

### Post by OldLes on 2011-01-18
OK, stupid me as usual, I decided to do an update. Incidentally, I am a Linux virgin, and struggle with terminal. 
I made the decision to update when I got the message "No more critical updates", to be issued. The update option was V 9.10, which is only supported to April 2011. After the restart, the graphics only allowed low resolution graphics. I assume I need a new NVidia GeForce 8200 graphics driver. Correct? If so, where do I get it, and what do I do with it?
OldLes.

---

### Post by hansolo4949 on 2011-01-18
try going to system>administration>hardware drivers. There may be a driver for your card in there. if there is, click on "activate", and you should be good to go!

You should also google your problem and see if anyone has found a solution.

---

### Post by OldLes on 2011-01-18
Many thanks Hansolo.
It worked a treat. Now to try to get the PCI Edimax WiFi card.
Les.[SIZE=3]
[/SIZE]

---

### Post by hansolo4949 on 2011-01-18
Sure! i'm happy you're computer is working properly now, with the exception of your wireless. I'm assuming there wasn't a driver for it in hardware drivers. I don't know anything about that problem, so i'll have to let someone else help you with that. What is the problem, exactly? is it slow? not working? I'll se what I can do from a general standpoint...

---

### Post by hansolo4949 on 2011-01-18
Sure! i'm happy you're computer is working properly now, with the exception of your wireless. I'm assuming there wasn't a driver for it in hardware drivers. I don't know anything about that problem, so i'll have to let someone else help you with that. What is the problem, exactly? is it slow? not working? I'll se what I can do from a general standpoint...

---

### Post by hansolo4949 on 2011-01-18
OOPSIE, triple post:(

---

### Post by OldLes on 2011-01-19
This Edimax card seems fraught with problems. There is a driver, and it seems possible to get it working, but not easy (possible?) for a newbie. I have found a few promising links, including on this forum, but even after 2 sessions of more than 2 hrs each, a pal who is an experianced (services trained)  unix and ubuntu worker / user, it still does not work. When I get details of a "Guarannteed working out of the box" alternative card, I will solve the problem that way, hopefully.
Old Les

---

### Post by darklord on 2011-02-02
For wireless support why not try the window driver thro Ndiswrapper [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper).

The above is the most simplest method to make NIC cards to work under ubuntu and has worked for me in the past.

Sometimes you get extra benfit if you stick to linux modules and do the correct way but this can be confussing.

Also to make life simpler to update to a newer version of ubuntu to the next release seperate your root partion and your home folders into two seperate partions. This should allow the end user to install a new distro or a newer version without loosing your data - even if the root drive becomes corrupt in some way.

For this i sugest that you start with a new hard drive.
1. Remove old hard drive
2. Install new hard drive
3. set up ubuntu with two or more partions - one for root "/" and one for home (the installer allows the end user to suggest his/her own disk layout) 
4. turn off pc, reinstall old hard drive 
5. Copy the required data from the old drive /home/username to the /home/username on the new driver. If you copy all of home to the new driver you will potentialy overwrite configuration files, these files are usualy hidden ie.. /home/username/.configure

---

