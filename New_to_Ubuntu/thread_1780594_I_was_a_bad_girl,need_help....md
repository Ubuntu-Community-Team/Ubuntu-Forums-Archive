---
title: "I was a bad girl,need help..."
date: 2011-06-12
forum: New to Ubuntu
---

### Post by smcrossman on 2011-06-12
[LEFT]Yesterday was NOT one of my better days! I was doing something that led me to the sudoers.d directory and I created a file which had some bad syntax in it.  Now I cannot get access to anything that requires root or other special privileges.  Of course this means I cannot move, delete, or edit the bad file (which is generally unnecessary...). I can't open synaptic package manager.   Yes I KNOW you aren't supposed to do anything involving that particular command. What referenced me to making changes there was dealing with something totally different and I just didn't register what I was doing.

Of course I spent most of the day trying to figure out the wireless networking on the monster desktop (I did an "upgrade 11.04 to 11.04" install without properly preparing). Finally out of desparation I did an extended cable to the ethernet port (which we thought was bad since we couldn't get it to activate in Windows) and at least I can now update and upgrade the software & such.

So back to sudoers.....any fixes or workarounds?  Or do I need to somehow "reinstall" to this netbook as well?  BTW I did uninstall Samba since that is the app that creates the file that changes the sudoers.conf to read the sudoers.d I think....but I doubt that will undo the mess I've caused!
[/LEFT]

---

### Post by VOT Productions on 2011-06-12
Go to Ubuntu recovery and choose drop to root. Then you can run removal commands, etc.

---

### Post by mobilediesel on 2011-06-12
You can delete the file if you boot from a liveCD. You would probably have to mount the drive with your root partition. After booting with the liveCD, open a terminal:
```
sudo mkdir /mydrive
sudo mount /dev/sda1 /mydrive
```
Use whichever drive holds your root partition instead of **sda1**
Then you just go into sudoers.d directory in /mydrive and remove or edit the offending file.

**Edit:**
VOT Productions' answer might be faster. I didn't think of doing it that way.

---

### Post by smcrossman on 2011-06-12
Thanks! I don't think the password reset will work so its option2. Now to see if I already have a 32 bit Ubuntu iso that I can put on USB or if I need to download and make one.  I will let y'all know how I do with this!

---

### Post by VOT Productions on 2011-06-12
[Deleted not to confuse matters]

---

### Post by mobilediesel on 2011-06-12
> **smcrossman said:**
> Thanks! I don't think the password reset will work so its option2. Now to see if I already have a 32 bit Ubuntu iso that I can put on USB or if I need to download and make one.  I will let y'all know how I do with this!

The way VOT Productions said can be done from the recovery option in the grub menu when you boot. No boot CD needed.

---

### Post by smcrossman on 2011-06-12
I found the i386.iso on the windows portion of the netbook. So I have the USB burned.  I'll copy the file I created so you'll see why I don't think it's a password fixable issue.  I will try the recovery option though, simply because I am using each opportunity to learn as much as possible, and its something that I haven't done yet.

EDIT:  Duh, once I'm in recovery I can probably delete the file there as well huh?  New things, new things.....so much to learn and process! LOL

---

### Post by mcduck on 2011-06-12
Resetting the password indeed won't help here, as it's not a case of a bad password but of a bad configuration.

However booting into the recovery mode *will* allow you to remove (or fix) the offending configuration file you created as recovery mode gives you root access (without having to depend on sudo).

---

### Post by VOT Productions on 2011-06-12
I haven't saw the file, so I can't give you more advice.

---

### Post by smcrossman on 2011-06-12
Well going into recovery didn't work. I did change my password (so I was there) but sudo is just totally disabled.

The USB I made gives error no operating system. So I am downloading a clean copy to put onto USB in linux (so much easier and more reliable).

I don't recall exactly what I did but I believe I identify admin= 1 or 2 user groups and then sudo= 1 of those groups.  I'm trying to figure out ways to secure networking, etc.  One of the wiki pages (I think) suggested doing that rather than doing individuals, etc. BUT:  either I missed it or the warning about changing sudo from default without much caution wasn't there and I was distracted by the wireless networking issues.  

Whenever I try using sudo I get:

> suzanna@suzanna-dell:/$ sudo gedit etc/default/grub
>>> /etc/sudoers.d/sudoersadd: syntax error near line 20 <<<
>>> /etc/sudoers.d/sudoersadd: syntax error near line 25 <<<
sudo: parse error in /etc/sudoers.d/sudoersadd near line 20
sudo: no valid sudoers sources found, quitting
suzanna@suzanna-dell:/$ 

Someday maybe I'll be smart enough that when I'm having a major brain fog day I won't try to program or alter anything major in my life!

---

### Post by VOT Productions on 2011-06-12
Odd... try creating a Live USB from Windows.

---

### Post by JKyleOKC on 2011-06-12
> **smcrossman said:**
> Well going into recovery didn't work. I did change my password (so I was there) but sudo is just totally disabled.When you are in recovery mode, you don't need to use "sudo" at all. This point isn't at all obvious, especially when in your situation of (a) being new to the system and (b) trying to undo a major boo-boo!

The command line is your friend in such a case. When you are operating as "root" the last character of your prompt will be "#" while when you are in your normal user id it will be "$" so it's easy to know whether you have root privilege or not.

To get sudo back into action, assuming that the bad file in sudoers.d is the only problem, do the following:

1. Boot into recovery mode as you did to change your password.

2. Open a terminal from the GUI.

3. Type "cd /etc/sudoers.d" and hit Enter.

4. Type "ls" to see all the files in the directory.

5. Type "rm " followed by the first few letters of the name you gave the bad file, then hit Tab to automatically fill in the rest of the name and hit Enter.

6. Repeat step 4 to be sure that the file is deleted.

7. Reboot normally and see whether sudo now works.

The sudo program does require at least one file to be present in the sudoers.d directory, so be sure to leave the README file that's there alone. Any other files must follow all the syntax rules of "sudoers" itself, so it's best to create them by first adding them to "sudoers" with "visudo" (which will catch any syntax errors and keep you from running into this again), then cutting the lines from "sudoers" and pasting them into a new file in "sudoers.d"

However due to the way sudoers works, specifically because it parses lines in sequence and later lines override the effects of earlier ones, it's best not to use "sudoers.d" at all, and simply make any additions to /etc/sudoers itself, using visudo.

Hope this helps!

---

### Post by Swagman on 2011-06-12
In my humble experience.. If you don't b0rk anything then you don't learn anything.

ie: Your on the right track

:-)

---

### Post by philinux on 2011-06-12
This might help.

[Fix broken sudo]("http://www.psychocats.net/ubuntu/fixsudo")

---

### Post by smcrossman on 2011-06-12
Okay...all back to normal realtively speaking.  I had to re-download the iso and put it onto USB on the other computer (the one not doing wireless right now).  I had already tried the windows route and that one was missing the OS. I used the netbook...downloaded and made USB and kept getting an error in install.  It still wasn't right....I wiated about 30 mins from choosing Try on the Install menu until I used C+Alt+Del which put me into my try state after another 10 mins or so.  Went in deleted the bad file, and the backup of it. Then came home.  Came in via recovery, and sure enough I didn't need sudo at all! LOL  It wouldn't let me open a terminal...said it wasn't installed.....so I just used the cd to go into a directory I knew would require sudo and copied a file. Then it wouldn't let me delete it...but I came on into full blown and went in, renamed it and deleted it in Gnome Commander with root privileges.

THANK YOU very much for the information, guidance and learning experience!

BTW here is the goofy file that screwed everything up:

#
# As of Debian version 1.7.2p1-1, the default /etc/sudoers file created on
# installation of the package now includes the directive:
# 
#     #includedir /etc/sudoers.d
# 
# This will cause sudo to read and parse any files in the /etc/sudoers.d 
# directory that do not end in '~' or contain a '.' character.
# a
# Note that there must be at least one file in the sudoers.d directory (this
# one will do), and all files in this directory should be mode 0440.
# 
# Note also, that because the sudoers file is not a 'conffile' in the Debian 
# sense, and sudoers contents can vary widely, no attempt is made to add this 
# directive to existing sudoers files on upgrade.  Feel free to add the above 
# directive to the end of your /etc/sudoers file to enable this functionality 
# for existing installations if you wish!
#

[Users]




[Groups]

#Add a line  in the "group" section 
## Members of the winusers group may gain root privileges
%admin ALL=(ALL) ALL
%suzanna ALL=(ALL) ALL
%winusers   ALL=(ALL) /bin/mount,/bin/umount,/sbin/mount.cifs,/sbin/umount.cifs
%suzanna   ALL=(ALL) /bin/mount,/bin/umount,/sbin/mount.cifs,/sbin/umount.cifs


EDIT: my netbook posted on its own before I finished!  :line 20 is around the users header and that would put line 27 close to the group header  I remember now that I was going to restrict sudo to basically me (with about 7 user names) then decided to only give sudo to the linux user ids and give mounting to all of us.  Since mounting is turning into an issue while trying to share files & set up Samba.  Next time I will copy the sudoers.cfg file into home and study the syntax a little more.

Now on to make sure I really have to copy, compile and install these drivers to get the monster to talk to the router without a cord!

---

