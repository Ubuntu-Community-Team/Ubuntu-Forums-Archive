---
title: "How do i change the name of the pc?"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by asdfghjkl67 on 2011-02-03
When im connected to a network the machine name of my pc turns up as 'mymachine'-can i change this somehow?

---

### Post by killfall on 2011-02-03
1. Open a terminal window.

2. Input the following command and hit Enter:
gksudo gedit /etc/hostname

3. When prompted, enter the administrator password and click the OK button.

4. The hostname file will open, displaying the current computer name. Replace the current computer name with the desired new name.

5. Click Save.

6. Close all open windows and restart your system.

After your system has restarted, it will have the new computer name.

---

### Post by oldfred on 2011-02-03
My notes say you also need to edit hosts.

Computer Name
Must do both & reboot right away
sudo gedit /etc/hostname
sudo gedit /etc/hosts

---

### Post by uRock on 2011-02-03
Moved to [ABT]("http://ubuntuforums.org/forumdisplay.php?f=326")

---

### Post by lhb1142 on 2011-02-03
> **asdfghjkl67 said:**
> When im connected to a network the machine name of my pc turns up as 'mymachine'-can i change this somehow?

In my opinion the easiest way to effect such changes is to install the Ubuntu Tweak  < [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) > program.

This program allows one to make many changes and adjustments to his/her system. In addition it allows easy implementation of new PPAs and programs.

It also 'cleans up' unneeded files subsequent to installation of programs or updates. (I also use the BleachBit program for this; it cleans some things which Ubuntu Tweak does not.)

To change your computer's name, merely open up Ubuntu Tweak and scroll down to Computer Details. Within that option you'll see the control to change the hostname.

Try this program. I'll bet you'll like it.

Lawrence ):P

---

### Post by jerryvlad on 2011-03-23
Hi I'm also entirely new to Linux and I want to change the name of my computer as well, I wonder if changing the name of the localhost in the hosts file and the name of the hostname in that last file, or do I need to change the name of the computer that appears in a line commented as "IP provided by network manager" that also has the old name of the computer. I am trying to learn networking very slowly and step by step, and am trying not to get in trouble meanwhile.

---

### Post by crispy_420 on 2011-03-23
Thought you could just go "sudo hostname NEWNAME" and reboot? Where the NEWNAME is what you would like it to be.

[http://ss64.com/bash/hostname.html](http://ss64.com/bash/hostname.html)

---

