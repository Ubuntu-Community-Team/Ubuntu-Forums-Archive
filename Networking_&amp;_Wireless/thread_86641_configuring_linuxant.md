---
title: "configuring linuxant"
date: 2005-11-05
forum: Networking &amp; Wireless
---

### Post by bobterri on 2005-11-05
I downloaded and installed the driverloader driver for linuxant for my wireless card.  Everything installs fine until the last step which is to configure the settings.  A browser window opens but a popup window also which tells me to type "root" and the "password" to give linuxant permission to finish the installation.  There is no "root" in Ubuntu, right?  The process halts at that point because  of no "root."  Is there anyone who has overcome this problem with Ubuntu?

Thanks.

---

### Post by adwait on 2005-11-06
Enable the root account by running
```
sudo passwd
```
The password you enter will be the new root password.

---

### Post by bobterri on 2005-11-06
No, I mean that the pop-up window from the browser configuration window asks me to type in "root" and then type in a password that linuxant gives me.  This operation is not being done in terminal, but in a popup in a browser window.

---

### Post by Lambert on 2005-11-06
If your device is recognized and the driver is installed then you can configure settings through ubuntu's network manager. 

At the top panel click on System>administration>Networking. You should see your wireless device in the list. Highlight it and click on properties.

Enter your network info, click ok and then click on activate.

If you're not getting your driver installed with linuxant, if you have some kind of access to the internet, install ndisgtk from the repositories.

Go[here]("http://www.ubuntuforums.org/showthread.php?t=85378&highlight=ndiswrapper") for more.

---

### Post by monkey89 on 2005-11-06
[QUOTE=bobterri]No, I mean that the pop-up window from the browser configuration window asks me to type in "root" and then type in a password that linuxant gives me.  This operation is not being done in terminal, but in a popup in a browser window.[/QUOTE]

He was giving you a way to create a root password, which you could then use in the driverloader (linuxant) password box.

---

### Post by bobterri on 2005-11-06
When the popup appears, it asks that you type the word "root" into the username space and then your "password" for "root" in the "password" space.  Are you saying I type the "password" I set with "sudo passwd" in the username space instead of "root?"  Then what will I use in the "password" space?  

Hasn't anyone running ubuntu successfully installed and configured linuxant?

---

### Post by bobterri on 2005-11-06
P.S. to Lambert,

The configuration that linuxant requires isn't the kind of configuration that the networking tool does.  It allows you to set the "key" which you purchase from linuxant.  Thanks, though.

---

### Post by adwait on 2005-11-06
Yes. Type the password you set with sudo passwd in the password field.

ps: please use quotes properly, otherwise you end of confusing everybody.

---

### Post by bobterri on 2005-11-06
I apologize for the quotes.  

I found the answer on one of the linuxant.com mailing lists.  I entered "sudo passwd root" in a terminal and then it asked me for a password which I created.  From there I was able to configure the linuxant driver and I am now on-line wirelessly.  

Thanks for everyone's help.

---

### Post by adwait on 2005-11-07
That's what I suggested in the first place!!!!!

---

### Post by bobterri on 2005-11-07
Well, from your post I only see "sudo passwd" not "sudo passwd root" which I needed to do.  Perhaps you could have been a little bit clearer, though I certainly do appreciate your help.

---

### Post by adwait on 2005-11-07
sudo passwd root = sudo passwd

With sudo, root is understood. No need to specify explicitly.......atleast that's my understanding. Anyway, next time Ill try and be more clear, the important thing is your problem is solved.......
cheers :)

---

### Post by bobterri on 2005-11-07
Amen!  And again, I really appreciated your help.

---

