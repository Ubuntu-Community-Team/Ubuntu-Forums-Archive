---
title: "Can Samba on Gutsy LAMP disrupt windows workgroups?"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by Hopworks on 2008-05-26
This has happened to me enough times over the past few years to finally ask about it. My networking between my laptop and my Main winblows desktop has been fine for the last several weeks until I started playing around with samba on my Gutsy Server (LAMP). Now either machine cannot access the workgroup, although they can see it. Even after reboots on both machines.

I'm in NO WAY blaming Linux, or Ubuntu. I'm sure it's something Winblows can't handle that is causing the issue. I just wanted to know if it is possible that Samba is trashing it for my Winblows machines. That would help me to rule out something with those boxes. They are both different flavors of Winblows also. Main is XP Pro, and Laptop is XP Media Edition.

I wasn't going to ask for it here, but I'm at my wits end. It's Samba that is killing me right now. I have Gutsy Server installed (nvidia issues on Hardy), LAMP configured, Webmin installed and Samba, and the Gnome desktop with 3d acceleration. I LOVE IT. 

Anyway, all this was working on my Feisty, and I could map network drives (shares) just fine on both Winblows machines. The install was my first Ubuntu though, and when I moved it over to new hardware, the errors were too many to work. It was time for a fresh install.

Now I can't get back my shares access ability for the life of me. I've searched for two days now, tried everything google searches had to offer. I should have taken notes! I'm so paranoid of missing something again, I've written down what I've done so far AND populating a LAN-BASED Wiki.

Doesn't help me remember what I did to get Samba to work for me back a year ago though.

At least I can ping the Gutsy server from windows, can open Putty using SSH, although I've lost my ability to use VNC, and not sure why. Something to do with SSH I assume. I can access webmin AND after using chown and chmod, I'm able to access my lan site just fine. I haven't tried any MySQL stuff yet.

Just can't do the shares. I can't even access my other windows machine atm using my workgroup.

Thanks for your time!

Hop

---

### Post by dmizer on 2008-05-27
for sharing files from ubuntu to windows, see the first link in my sig.  for mounting windows shares in ubuntu, see the second link in my sig.  these two methods DO work, and i have tested them often.

they are command line based, so the nifty: places > network does not work, but these methods are superior to the gui based method of sharing and mounting shares.

two things that you should try before resorting to the howtos in my sig:
- check or disable firewalls in windows (and ubuntu if necessary)
- make sure that all your windows and ubuntu machines are part of the same workgroup.

both of these items are critical to a working file share.

---

### Post by Hopworks on 2008-05-28
> **dmizer said:**
> for sharing files from ubuntu to windows, see the first link in my sig.  for mounting windows shares in ubuntu, see the second link in my sig.  these two methods DO work, and i have tested them often.

they are command line based, so the nifty: places > network does not work, but these methods are superior to the gui based method of sharing and mounting shares.

two things that you should try before resorting to the howtos in my sig:
- check or disable firewalls in windows (and ubuntu if necessary)
- make sure that all your windows and ubuntu machines are part of the same workgroup.

both of these items are critical to a working file share.

Thank you for the guidance! It was the links in your signature that put me on the correct path. I had to go to a few more links to figure it out. It seems though, that Webmin was hurting me a little. For some reason, I had Force User = <user> and Force Group = <group> in the smb.conf file under the share. I took those out, did a couple of other things I read about, and now it works. It's not like it was, meaning that windows acts a little differently when I click on the mapped network drive for the first time, but I have access now.

One of the things I have I didn't have before is the ability to browse the shares when setting up a new mapped network drive. That's pretty neat!

Another thing I have is the knowledge that it is much better to set samba up via the command line and editing the smb.conf directly. I still have a ton of questions, but I realize now that it is a good thing to learn about all the options available via that config file.

For one thing, I don't get FQDN, and how that relates to my network configuration. I'm easily confused between Host Name and Domain Name in the network settings from Gnome. After all, I'm just using Ubuntu Gutsy as a LAMP server on a LAN behind a firewall router. It's sole function is to serve up LAN site pages, offer access to its storage shares, and PVR (eventually), and downloading via Hellanzb. All behind the hardware firewall. I think I finally figured out about aliases, since I played with that, and now can ping each of those with expected results.

I have a lot to learn, but thank you for helping me finally solve my samba issue. =)

One last question, totally unrelated, but maybe you can advise me what forum to ask about it... it's the hot spot on the edges of windows in Gnome. They seem really narrow. I have to move my mouse back and forth a lot just to get the cursor JUST RIGHT to resize a window. Is there a way to expand that hot spot on the edges? Where should I ask about that?

Sorry for the additional off-topic question. I don't normally ask anymore because I don't believe in 'bumping' topics, and most of those type of questions I ask are never answered, for lack of the right forum it is asked in I believe.

Thanks for your time!

Hop

---

### Post by Iowan on 2008-05-28
> **Hopworks said:**
> One last question, totally unrelated, but maybe you can advise me what forum to ask about it... it's the hot spot on the edges of windows in Gnome. They seem really narrow. I have to move my mouse back and forth a lot just to get the cursor JUST RIGHT to resize a window. Is there a way to expand that hot spot on the edges? Where should I ask about that? Would that fall under [Desktop Effects and Customization]("http://ubuntuforums.org/forumdisplay.php?f=330")?

---

### Post by Hopworks on 2008-05-28
> **Iowan said:**
> Would that fall under [Desktop Effects and Customization]("http://ubuntuforums.org/forumdisplay.php?f=330")?
Sounds like a good place to try, and I posted there. Thank you!

Hop

---

### Post by dmizer on 2008-05-28
glad you got it working to your satisfaction. 

> **Hopworks said:**
> For one thing, I don't get FQDN, and how that relates to my network configuration. I'm easily confused between Host Name and Domain Name in the network settings from Gnome. After all, I'm just using Ubuntu Gutsy as a LAMP server on a LAN behind a firewall router. It's sole function is to serve up LAN site pages, offer access to its storage shares, and PVR (eventually), and downloading via Hellanzb. All behind the hardware firewall. I think I finally figured out about aliases, since I played with that, and now can ping each of those with expected results.

here's a good article on your naming confusion: [http://kb.iu.edu/data/aiuv.html](http://kb.iu.edu/data/aiuv.html)

> **Hopworks said:**
> One last question, totally unrelated, but maybe you can advise me what forum to ask about it... it's the hot spot on the edges of windows in Gnome. They seem really narrow. I have to move my mouse back and forth a lot just to get the cursor JUST RIGHT to resize a window. Is there a way to expand that hot spot on the edges? Where should I ask about that?

take a look here: [http://www.keyxl.com/aaae677/56/Linux-Gnome-Window-Manager-keyboard-shortcuts.htm](http://www.keyxl.com/aaae677/56/Linux-Gnome-Window-Manager-keyboard-shortcuts.htm)

> Alt+F8
Resize the currently focused window. After pressing this shortcut, you can resize the window using either the mouse or the arrow keys. To finish the resize, click the mouse or press any key on the keyboard.

---

### Post by Hopworks on 2008-05-28
> Alt+F8
Resize the currently focused window. After pressing this shortcut, you can resize the window using either the mouse or the arrow keys. To finish the resize, click the mouse or press any key on the keyboard.

I didn't KNOW that. Thanks for the heads up! I'll make use of it! and your link.

Hop

EDIT: Thanks for the follow up on the other links too. I'll read everything I can find on it. Some say ignorance is bliss, but I say that when it comes to Linux, there is nothing happy about not knowing or even TRYING to know about all the wonderful features available.

---

