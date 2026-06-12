---
title: "Error message when trying to sync iPod touch 2G"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by Aliceaurus on 2010-04-30
Just installed the 10.4 update, super excited to finally be able to sync my iPod touch (2G), plugged it in, Rhythmbox recognizes it and everything, woo, all is going well... I successfully deleted everything off my ipod only to find that I get this error message when trying to put songs back on it:

Error Transferring Track
Error while getting peer-to-peer dbus connection: The name :1.82 was not provided by any .service files

Please help, someone tell me that I haven't just screwed my ipod to hell. This computer is my only syncing option right now.

(And, before you say it, I realize that it was really stupid to delete all my music before testing it first. My bad, I was a bit overexcited.)

---

### Post by kesken88 on 2010-05-06
Same exact error

Ubuntu 10.04 + Rhythmbox + iPhone 3GS w/ 3.1.3

Edit: i'm not complaining though, i love the new support.  Thanks Gnome + Canonical

---

### Post by kapetanski on 2010-05-09
I have a similar problem as well when trying to transfer files to the iPod:

Error while getting peer-to-peer dbus connection: The name :1.136 was not provided by any .service files

Ubuntu 10.04, Rhythmbox and iPod Touch 1G 8GB. I have not tested to delete files yet.

---

### Post by vhenninot on 2010-05-10
Hello,

Same problem for me after upgrade from karmic to lucid !
But no problem with a fresh new install of lucid lynx... to bad !

I hope someone will fond where is the problem...

Vincent

---

### Post by achase79 on 2010-05-10
> **vhenninot said:**
> Hello,

Same problem for me after upgrade from karmic to lucid !
But no problem with a fresh new install of lucid lynx... to bad !

I hope someone will fond where is the problem...

Vincent

So only upgrades have the problem?  Sounds like a configuration file didn't get changed (or configured correctly) during the upgrade.  I personally don't know which one, I don't have a iPhone or iPod Touch to test.

This sounds like a good instance to submit a bug report.

---

### Post by judoclint on 2010-05-11
I was having the same problem until I updated my 2G itouch firmware to  3.1.3
If you're running old firmware, maybe an update will solve the issue.

---

### Post by matti_bauer on 2010-05-12
I got the same error message with my iPod touch. But after I deleted ".gconf/apps/rhythmbox" it started working.

bye
matti

---

### Post by Diderik From on 2010-05-13
matti_bauer:

Thanks! It worked for me on my iPhone 3GS (with the newest firmware).

Edit: It is rather unstable though.

---

### Post by TripleEye on 2010-05-15
This worked for me to! Just upgraded from karmic to 10.04. Using 3rd generation 8GB Ipod Touch.

Thanks!

---

### Post by Joao Cid on 2010-05-16
Great!!!
I was having the same - I have an iPhone 3GS - and this worked...
Many thanks for the tip!

---

### Post by fizban9 on 2010-05-17
> **matti_bauer said:**
> I got the same error message with my iPod touch. But after I deleted ".gconf/apps/rhythmbox" it started working.

bye
matti

This works for me too, but I only deleted the config file in .gconf/apps/rhythmbox/plugins/ipod and restarted the program,

Thanks!

---

### Post by subehsharma on 2010-05-22
Hi.

Please tell me where to search for .gconf file as i can't seem to find it.

kartikay@kartikay-laptop:/$ rm .gconf/apps/rhythmbox
rm: cannot remove `.gconf/apps/rhythmbox': No such file or directory
kartikay@kartikay-laptop:/$ 
kartikay@kartikay-laptop:/$ rmdir .gconf/apps/rhythmbox
rmdir: failed to remove `.gconf/apps/rhythmbox': No such file or directory


tried searching for it in "Search folder" with the option of checking the hidden files but can't find it.

Thanks in advance,
Subeh

---

### Post by Kurt Arndorfer on 2010-06-03
I used gconf-editor (sudo gconf-editor in a terminal window), navigated to apps-rhythmbox-plugins-ipod, unchecked "active" in the right pane, restarted rhythmbox (don't know if this was necessary), and it now works. 

I don't know how or why it works, but this is true of most things I've learned about Linux.

---

### Post by Doobie9 on 2010-06-07
> **Kurt Arndorfer said:**
> I used gconf-editor (sudo gconf-editor in a terminal window), navigated to apps-rhythmbox-plugins-ipod, unchecked "active" in the right pane, restarted rhythmbox (don't know if this was necessary), and it now works. 

I don't know how or why it works, but this is true of most things I've learned about Linux.

This also worked for me.

---

### Post by chiccoch on 2010-06-07
> ...but I only deleted the config file in .gconf/apps/rhythmbox/plugins/ipod and restarted the program...

This worked for me. THX!

---

### Post by ada-m on 2010-06-24
> **matti_bauer said:**
> I got the same error message with my iPod touch. But after I deleted ".gconf/apps/rhythmbox" it started working.

bye
matti


Worked for my with iOS4 on 3g

---

### Post by ADK1 on 2010-07-13
I'm running Linux Mint 9 and get the same message, "Error while getting peer-to-peer dbus connection: The name :1.346 was not provided by any .service files" when trying to add files to my ipod touch (I can play/delete etc. to my heart's content, just can't add).

I followed Kurt Arndorfer's instructions for unchecking "active" for the ipod plugin (thanks for the detail! I would have deleted the whole Rhythmbox folder). (By the way I didn't need to restart Rhythmbox).

This solution didn't work for me, though, because with the plugin deactivated I can't see my ipod in the Rhythmbox sidebar! Thus, I cannot drag any files to it :(

This may be related to another problem I have, which is that when I first plug in my ipod touch Rhythmbox launches but the ipod doesn't show up in the sidebar. For that to happen I have to disconnect the ipod and reconnect it. Oddly enough, after I've disabled the ipod plugin using gconf ed., when I plug my ipod in Rhythmbox still launches, I just can't get the ipod to show up by plugging it in a second time.

I would really appreciate it if any of you who have had success with this could relieve me from having to boot into Vista to add songs to my Ipod :I

---

### Post by chudder on 2010-07-15
> **fizban9 said:**
> This works for me too, but I only deleted the config file in .gconf/apps/rhythmbox/plugins/ipod and restarted the program,

Thanks!

That was the question I was going to ask, the whole directory or a specific config file.  I'll report back what happens

---

### Post by chudder on 2010-07-16
> **chudder said:**
> That was the question I was going to ask, the whole directory or a specific config file.  I'll report back what happens


So far it seems to work.

I've been told that once you start fiddling with an ipod, if you hook it up to iTunes it will tell you that you've messed it up, etc.  is that true?

---

### Post by donc on 2010-08-05
The solution to remove the rhythmbox config files works like a charm with my updated iphone (ios:4.0.1)

---

### Post by kliffs on 2010-08-09
I had this problem three times on different installs on different computers! I searched forums and googled for a long time. Every single time this happened simply reinstalling ubuntu-restricted-extras from synaptic worked istantly after restarting rythmbox.

---

### Post by tim.sargent on 2010-08-18
> **matti_bauer said:**
> I got the same error message with my iPod touch. But after I deleted ".gconf/apps/rhythmbox" it started working.

First Gen. iPod Touch running firmware 3.1.3.  
this fix seems to have worked for now using rhythmbox.  
thanks for the help the forums are great

---

### Post by pucca_and_garu on 2010-08-22
can you explain how to delete ".gconf/apps/rhythmbox"? sorry.. i can't seem to figure it out><

---

