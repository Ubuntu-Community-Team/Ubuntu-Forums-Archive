---
title: "new user networking problems"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by Phil Binner on 2009-02-28
I have just loaded Ubuntu 8.1 and was initially very impressed. I'd love to ditch Windows altogether. I have two problems, however.

When I start my machine I gat a message "Enter password for default keyring to unlock. The application 'Network Manager applet (/usr/bin/nm-applet) wants to access the default keyring but it is locked." I enter my password and immediately get the message again, ad-infinitum. I then close the box manually and, if I'm lucky, I get another window asking for the 26 char wireless network authentication key. When I enter that I get the first message again, and I enter my password and I'm in. On one occasion I started the process and then went away for 10 - 15 minutes. When I tried again I got to the point of entering the 26 char key, but the wireless network loaded automatically before I entered it. This sort of suggests a delay issue, but if it is it's a long delay. When I first set up the network connection I told it to connect automatically.

My second problem is that, although I can use the internet fine, and I can see the rest of the windows network, when I try to load the network I get the message "unable to mount location". I followed the documentation to Samba, which seems like a sledgehammer to crack a nut, but I got through it. When I had made my changes, however, I attempted to run the command "root#  testparm /etc/samba/smb.conf.master" and got the message "root# : command not found"

So now I'm stuck. 

Can anyone help please.

---

### Post by sgosnell on 2009-02-28
For the first, just cancel it.  Ubuntu wants to store the password in the keyring, and you don't have to do that.

For the second:  do not enter root#.  That's probably what you saw from some how-to, and would be the command-line prompt for that system.  Use 'sudo' instead, thus

"sudo testparm /etc/samba/smb.conf.master" and enter your user password when prompted.  I'm not sure that's the correct entry, though, too many '.'s.

---

### Post by Iowan on 2009-02-28
Before I change configuration files, I like to make a backup copy as disaster protection.  That also lets me keep a virgin copy of the file (usually filled with copious comments).  My working copy can be edited and extra comments and unused options deleted.
*/etc/samba/smb.conf.master* is the sort of name I'd give my backup copy. Samba is probably going to expect the configuration file to be called simply */etc/samba/smb.conf* (though you might be able to change it somewhere).

---

### Post by Phil Binner on 2009-02-28
Thanks for that. With regard to teh keyring, it seems that cancelling it is OK, but I'm still getting asked for teh full 26 char security key for the wireless network. Can I make it automatic some way. Also, can I cancel the keyring some way. A password is not realy required in my attic.

---

### Post by Phil Binner on 2009-02-28
Thanks, I did make a backup copy. With regard to your friendship request, was it you who helped me with version 7.10 a year ago. I don't know anyone else on the Ubuntu forums. Regardless, friends are welcome. Death to Windows.

---

### Post by benerivo on 2009-02-28
I'm not sure how to cancel the keyring, or how to save your password so that the keyring uses it automatically. You could try using wicd instead of the 'gnome network manager applet'. I use it and it is independent of the gnome keyring. See [here]("https://help.ubuntu.com/community/WICD")

---

### Post by badmedic on 2009-02-28
> **benerivo said:**
> I'm not sure how to cancel the keyring, or how to save your password so that the keyring uses it automatically. You could try using wicd instead of the 'gnome network manager applet'. I use it and it is independent of the gnome keyring. See [here]("https://help.ubuntu.com/community/WICD")

+1 to this... I had issues with 8.10 and gnome network manager applet on my laptop... It constantly prompted me to reenter my Wifi network password at login and only connected sporadically. 

Switched to WiCD and it has worked great since! :guitar:

---

### Post by Phil Binner on 2009-03-01
I guess I'm moving forward. but slowly. I have now reached the dizzy heights of knowing to use 'sudo' instead of 'root#'. This knowledge has not availed me, however, as i still can't update smb.conf to get my network visible, because I have no permissions in /etc/samba.

---

### Post by Phil Binner on 2009-03-01
Definite froeward movement. WiCD solved my problems with the wifi. One more question before closing this thread, is Samba really the way I should be looking to connect to the windows network. All I want to do is share files and printers. I'll keep at the documentation, but i seem to remember that I occasionally got to see other network computers without this when I was trialing Gutsy Gibon:lolflag:

---

### Post by clive littlewood on 2009-03-01
Hi

The simple way to connect to your network and windows is as follows.

Create a "shares" folder in your documents.

Right click on the folder and click set as share.

If you do not have samba installed it will offer to install it for you.

When installed just place files or whatever for transfer into the shares folder.

If you go onto the windoze box and click networks your Linux box will be visible.

When transfering from windoze to Ubuntu you will be asked for your username and password.

Hope this helps (works for me !!!):P

Clive

---

### Post by Phil Binner on 2009-03-01
This worked for letting windows see ubuntu, but not the other way round. Is there an easy fix for that.:lolflag:

---

### Post by Phil Binner on 2009-03-03
I hope this is the way to close a thread

---

### Post by swoody on 2009-03-03
Well, I'm glad everything has worked out for you :)

The "SOLVED" and "Thank You" options have been temporarily removed, so I wouldn't worry about it at this time. Typically, there is an option under "Thread Tools" at the top of a thread, it used to have an option "Mark Thread as Solved"
Check here for more info:
[http://ubuntuforums.org/showthread.php?t=1044714](http://ubuntuforums.org/showthread.php?t=1044714)

---

