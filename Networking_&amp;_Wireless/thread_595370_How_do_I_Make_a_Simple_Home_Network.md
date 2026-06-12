---
title: "How do I Make a Simple Home Network?"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by bigbee79 on 2007-10-28
I have two machines running 7.10.  

I want to share an external harddrive that's connected to the desktop with my laptop.

Is there a simple way?  And by simple, I don't want to hear "Oh yeah!  That's so simple.  Just put blee blah bloopity blee into the terminal and then edit the blabbity.conf file and then do a magical wish dance to the Lord of the Underworld."

Is there a simple, quick way to do this?  Using something with a GUI?  I've searched everywhere, and every how-to ends up with people editing stuff in the terminal.  That just seems ridiculous to me.  Shouldn't there just be a simple gui that controls file sharing a few drives?

If not, I'll just switch the desktop back to XP.  At least that had an easy way to share folders. . .

---

### Post by bigbee79 on 2007-10-28
I just turned off my firewall to be able to share folders, but this doesn't seem like the best solution at all.  It just seems really dangerous to be without a firewall.

---

### Post by beerfan on 2007-10-28
> **bigbee79 said:**
> I have two machines running 7.10.  

I want to share an external harddrive that's connected to the desktop with my laptop.

Is there a simple way?  And by simple, I don't want to hear "Oh yeah!  That's so simple.  Just put blee blah bloopity blee into the terminal and then edit the blabbity.conf file and then do a magical wish dance to the Lord of the Underworld."

Is there a simple, quick way to do this?  Using something with a GUI?  I've searched everywhere, and every how-to ends up with people editing stuff in the terminal.  That just seems ridiculous to me.  Shouldn't there just be a simple gui that controls file sharing a few drives?

If not, I'll just switch the desktop back to XP.  At least that had an easy way to share folders. . .

The easiest and most secure way to access your remote computer is to use the Places menu. Both computers should be running SSH servers so use Synaptic to install "openssh-server". Once that is running then you simply go to Places > Connect to Server and create a connection to your remote computer. You will enter the username and password of your account on the remote computer and you can store that in your local keyring if you like so that when you use the connection in the future it will just work without asking your for your password. In the path area, you can leave it blank or you can enter the path of the external drive you want to use (e.g., /media/mydrive).

If you have a firewall you'll need to ensure that port 22 (the ssh port) is open.

There ya go...no terminal commands ;-)

---

