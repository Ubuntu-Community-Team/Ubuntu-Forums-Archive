---
title: "help needed for  forgotten password"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by Kaleyla on 2010-05-16
I recently purchased an HP Mini 1120NR Newtbook from a friend. It has Nautilus installed as the OS and she is the only user /owner on the system. I had her password and username, but here's all of the weird things about this system.
 
A) Upon logging in to the desktop, a message pops up stating: "$home directory for this user is being ignored"
 
B) I managed to get into some menu and change waht I thought was her personal password, however the system doesn't recognize her old password OR the new one I set. I am able to only boot up but not log into the desktop at all. The only options I get is a drop down menu under the username/password log in screen which says Remote Login via XDMCP and "Select Session"-- that offers the following:
 
Last session
Failsafe Terminal
GNOME
Falsafe GNOME
Run XClient script
Secure remote connection
None of these sessions are accessible without me knowing..the PASSWORD! I am VERY NEW to Linux, and I need this netbook to be up and running. I ultimately would like to be able to add myself as a user and not have to keep accessing anything through her username. But as it stands, I an't even get in that way anymore. Please help me get started.
 
Kaydee

---

### Post by ibuclaw on 2010-05-16
Which version of Ubuntu are you using?

When turning on the computer, hold down SHIFT or ESC (one or the other will work), and you should see a boot menu. Select "**Recovery Mode**" from it.

Then you will be brought to a console menu, select "**Root Console**", if I recall correctly, and then type in:

```
passwd **username**
```
Replace "username" with the user of the system, and that will prompt you to enter a new password for the user.

Once finished, press Ctrl+Alt+Del to reboot.

Regards

---

### Post by Kaleyla on 2010-05-16
I recently purchased an HP Mini 1120NR Netbook from a friend. It has Nautilus installed as the OS and she is the only user /owner on the system. I had her password and username, but here's all of the weird things about this system.
 
A) Upon logging in to the desktop, a message pops up stating: "$home directory for this user is being ignored"
 
B) I managed to get into some menu and change waht I thought was her personal password, however the system doesn't recognize her old password OR the new one I set. I am able to only boot up but not log into the desktop at all. The only options I get is a drop down menu under the username/password log in screen which says Remote Login via XDMCP, (for which my system cannot detect any networks to connect to), and "Select Session"-- that offers the following:
 
Last session
Failsafe Terminal
GNOME
Falsafe GNOME
Run XClient script
Secure remote connection
 
I cannot access ANY of these, or the BIOS, or anything because ALL of these require the password. I am looking to be able to add myself in as a new user and stop using her to navigate through the system. I really need this netbook to be up and running as soon as possible. PLEASE HELP!

---

### Post by Kaleyla on 2010-05-16
Thank you for replying so quickly.
 
I am using Nautilus. I am not sure which kernel version. I tried using the shift key, the esc key, and the Shift + Esc keys, and I am unable to see the recovery console. I just get a black screen with a blinking dash cursor. I tried the F10 key for the BIOS, but they, too ask for a current password which is not any of the passwords entered. I am really frustrated, because I find this really crazy that the only user on the system has no administrative rights. Please help. Again, my system is the HP Mini 1120NR Mi Edition. thank you in advance for any efforts.
 
Kaydee

---

### Post by mikewhatever on 2010-05-16
This is odd. Nautilus is just a file browser in Gnome, I don't think there is an operating system by that name. You should be able to reset the current password, create new users, etc if and once you get to the recovery mode, regardless of whether or not you are the only user. If the operating system is Ubuntu, can you find out which version? Can you ask your friend?

---

### Post by ajgreeny on 2010-05-16
Nautilus is not an operating system, just the file manager of systems using gnome as the desktop environment, so I will assume you mean it is running ubuntu as the OS.

Which version of ubuntu will affect what is needed next, however, as you need to get into recovery mode from the grub menu.  If the system is running 9.04 or earlier that requires you to press Esc at or just after pressing the power button.  If the OS is 9.10 or 10.04 you will need to press shift at that point instead.

Choose recovery mode at the menu, and boot into a command line when asked.  This will be a root command line system so be careful or you could completely bork the system.  Now follow this page [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) to make sure you have a good password for the user you have and you should be OK to go again.  If that is what you already did, then I am baffled and don't know how to help any further.

Good luck.

PS: Don't forget linux is case sensitive, so make sure you get that right every time you type anything.

PPS:  You really need to contact your friend again and find out for certain what the password was, both for the operating system and for the BIOS, or you could just be in for a big problem getting this machine to work, or even to get a new OS on to it if you can't get into the BIOS.

---

### Post by Kaleyla on 2010-05-16
Thank you all for your responses. Ibuclaw, your solution was the problem solver. I hit the ESC key and HP gave me two options: HP IE mobile experience, and System recovery. System Recovery was the closest thing to what you mentioned, but it involves erasing the data and formatting the hard drive. Since the few items I added to my friend's desktop was previously backed up to a portable USB flash drive, this option worked the best for me. I hope this helps someone else who may come across this rare and odd issue. I managed to remove her and instate myself as the only user in the Netbook. I haven't checked to see if I actually have admin rights yet, so look for me to be posting for help about THAT issue! LOL. Thank you, Ibuclaw, and to all of you who cared enough to reply so supportively.
 
 
Sincerely,
Kaydee

---

### Post by mikewhatever on 2010-05-16
Thanks for the update, Kaleyla. How about the repeatedly posed question about the version of Ubuntu you run (I assume it is Ubuntu since you posted at the Ubuntu forums)? The following commands either from the recovery mode or from a Terminal window should provide helpful info on the subject:

uname -r

cat /etc/lsb-release

---

### Post by ibuclaw on 2010-05-16
> **Kaleyla said:**
> Thank you all for your responses. Ibuclaw, your solution was the problem solver. I hit the ESC key and HP gave me two options: HP IE mobile experience, and System recovery. System Recovery was the closest thing to what you mentioned, but it involves erasing the data and formatting the hard drive. Since the few items I added to my friend's desktop was previously backed up to a portable USB flash drive, this option worked the best for me. I hope this helps someone else who may come across this rare and odd issue. I managed to remove her and instate myself as the only user in the Netbook. I haven't checked to see if I actually have admin rights yet, so look for me to be posting for help about THAT issue! LOL. Thank you, Ibuclaw, and to all of you who cared enough to reply so supportively.
 
 
Sincerely,
Kaydee

Sounds like you run **HP Mini Mi Edition**, which is based off Ubuntu 8.04, but not really the same distribution that people who frequent here use.

---

