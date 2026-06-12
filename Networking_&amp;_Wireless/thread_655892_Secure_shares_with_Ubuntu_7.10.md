---
title: "Secure shares with Ubuntu 7.10"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by manfarb on 2008-01-01
I've been working with Ubuntu 7.10 for a week or two now, and for the most part have it doing what I want.  I've found information about Samba to be somewhat varied, confusing, and inaccurate.  I wish there was a definitive document that would show me how to properly share a folder that a Windows XP box can access, but I want it to be secure, so the rest of the family PCs (I have 3 teenage boys with PCs) can't get to it without logging in.

Right now I've got shared folders working, but I did it with what I'm sure is a fairly common method of editing the smb.conf file and adding/modifying the "security = share" line.

I've found documentation that has me adding a user with the "smbpasswd -a username", but that doesn't work.  I've found documentation that has me change the browseable parameters and the writable parameters in the smb.conf, but that doesn't work.  I found a video on YouTube that I think was for 6.10, but that didn't work.  It sure seemed like the guy knew what he was talking about.  I think the problem is that I haven't found a document that includes all the steps.

So for now I've got an unsecured share, and I just want to make it secure.  Can anyone direct me to the right information?  And maybe this is asking too much, but I'm hoping I don't have to wade through all sorts of documentation.  I would have to believe that someone else has needed the same thing.  FYI, I've got the workgroup set to the same name on both the XP box and the Ubuntu box.  And I don't have a domain controller on our home network.

---

### Post by heatpumpcontrol on 2008-01-02
Try this link...

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

.. it worked for me. If you want to share a specific folder then just add that folder to your shared folders list... then just 


Code:

sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username

and that will restrict access to users mentioned above. Of course, these users have to have an active account in the Ubuntu machine.

---

### Post by manfarb on 2008-01-02
Well I was up until 4 AM working on this, and I finally got it.  I think I had things so hosed up that I decided to do a re-install of Ubuntu and then everything went just fine.  To be honest, in all the documentation I looked at I'm not sure that any of it made it clear that you need add a user in the Ubuntu Users and Groups maintenance before running the "sudo smbpasswd -a username" command.  It's also possible that the username I was running on my XP box "man" (those are my initials) is maybe not the best username for whatever reason.  Not sure about that though.

Anyhow, after re-installing Ubuntu, I changed my XP box username to something more obscure, added that same username to Ubuntu, ran the smbpasswd command for that same username, did all the other stuff like enabling sharing and things, and it all just worked.  Didn't even have to edit the smb.conf file.

So I'm a very happy Ubuntu camper.  I've now got a P4 1.6 gig Ubuntu box with a 200 gig drive holding all my data and every morning a combination of GRSync and KCron syncing that data to a 250 gig drive, all shared out nicely to my main PC which is a XP Pro box.  And of course I have the VNC remote desktop enabled so I can VNC into the Ubuntu box from my XP box.  There's a couple of things I want to do with the Ubuntu box, like use GRSync to sync some Web sites, and I would like to be able to have VNC active at login-time, but I'll tackle those down the road.

So thanks for your help.  I'm thinking about documenting my entire Ubuntu experience in the forum.  We'll see.  I did document all my steps with that late-night re-install (it was my 3rd time) last night, so it wouldn't take much to post it.  Again, thank you!

---

