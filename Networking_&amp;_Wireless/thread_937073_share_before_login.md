---
title: "share before login"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by Kramerdawg on 2008-10-03
I've got a ubuntu box that i am using for a dhcp/dns and fileserver for my little peer to peer network.  It has multiple USB harddrives attached and these are shared to the network.  I want to run it headless and remote in with VNC when i need to do something on it, which is rarely. So far everything is great except for two issues:

1.) I cannot access any of the shares from any other machine on the network until I log on to the Ubuntu machine locally.  So if i reboot the ubuntu box i can't access any of those shares until i unplug the monitor/kbd from one PC, plug it into the ubuntu box and log on.  Then everything is accessible.  DNS/DHCP work fine before login.

2.) Cannot remote in with VNC until i have logged onto the ubuntu box locally.  My first idea was just to VNC into it and log in, then i could access the shares, but this doesn't work since the remote doesn't work before login.

Any help is much appreciated.  I searched the hell out of the forums and could only come up with solutions for mounting REMOTE shares automatically at login, which is kind of the opposite of what i'm attempting.

I can't imagine this is that hard, it's making me feel dumb.

Thanks,
Joe

---

### Post by jones139 on 2008-10-03
It's definitely possible, because my little server does it.
How are you doing the network sharing, NFS or samba?
If it is NFS you should just be able to put the share into /etc/exports and it won't matter whether you are logged into the server or not.

---

### Post by mbratch on 2008-10-03
If you have static Samba shares, then they may need to go into /etc/fstab.

---

### Post by jones139 on 2008-10-03
Not quite - you put the share into /etc/fstab on the client to get it to mount the share automatically when it boots up.  This works with NFS, and I think samba.
On the server you should only need to put it in /etc/exports to give the clients permission to connect to the share by NFS.
Samba has its own configuration file (something like /etc/smb.d/samba.conf that needs to be set up on the server instead of /etc/exports.

GJ

---

### Post by Kramerdawg on 2008-10-04
Thanks for the replies, guys. 

Yea, I should have stated that they are all Samba shares.

I read a lot about /etc/fstab, but i think you're right, thats for automounting shares on the client.   This box is the server and I'm trying to get to it from windows and mac clients.  Like i said, works great except i can't connect to it unless it's been logged into locally.

I'll look into the etc/exports and see if I can figure it out.  I've been thru samba.conf pretty thoroughly but I'll parse it again and see if i missed something. 

It's driving me nuts cause other than that it's a bulletproof, set-it-and-forget-it little box.  I guess i could just never reboot it..........  :-)

Thanks again for helping me out.

joe

---

### Post by jones139 on 2008-10-04
Ok - setting up samba should just work without needing to log on, but I noticed that you said you can not remotely access the computer via VNC either, which makes me think it is something to do with your network setup.
How is your network set up - wired or wireless?
Are the IP addresses static or dynamic?
Can you 'ping' the server without having logged into it?
If the above reads like gibberish just say and I'll explain!

GJ

---

### Post by Kramerdawg on 2008-10-11
Thanks, Jones.  Sorry for the delayed reply.  It's been a rough week.

Network is wired, although there is an AP hanging off it, it's not part of this issue.

The ubuntu box is the DNS and DHCP server for my little network, and those services work great before login, and i can ping it, by IP or hostname.

Ive set up samba for guest access so i don't need credentials to access the shares once they're there.

Interestingly, once i've logged in locally, i can access both the SMB shares and VNC, but if I log back off, I can still access the shares I've already accessed.  But VNC won't work once i'm logged back off.
---
Edited:  I just checked and if I log onto the ubuntu box so that the shares become accessible, then i log back out,  i can still access any share on that box, regardless of whether or not i touched it when i was logged in.
---
I think you're on the right track, it seems like something that should be starting on boot isn't starting until login.  I can't tell if the shares aren't mounting until i log in, or if they're mounting but somehow not accessible.  I'm getting up to speed (slowly :-} ), but i'm still unclear on how things get started during each of those two stages in ubuntu.  I may be forced to RTFM.  :-}

I finally have some time to play with it this weekend so I'll try some stuff and post back the results.

Thanks again for your help.

Joe

---

### Post by Kramerdawg on 2008-11-25
Ok, so i never solved this and i had basically broken samba playing around with this box so I thought I'd just do a reinstall of 8.10 and set it up again and see if i had the same issues.  

I installed 8.10 and it would hang shortly after login, before I got to the desktop.  I tried Ubuntu 8.10, ubuntu alternate 8.10 and kubuntu 8.10 and got the exact same results so must be something this box doesn't like about 8.10.  Installed 8.04, boots perfectly.  Just for fun ran the update to 8.10 and it boots fine.  Weird.

SO i reconfigure dhcp and bind and setup sharing.  I like the improvements in 8.10 for samba sharing.  When i tried to share the folder, it informed me it wasn't installed, and offered to install it.  I let it and when i shared the folder it complained about one thing, but told me exactly what file to edit and exactly what to add, and where.  Worked perfectly and sharing is up and going and working great.  Very quick and easy, big improvement.

So I log off the box and pop over to windows and I'm right back where i started.  Can't connect to shares or connect with VNC while the box is logged off.  If i log onto the box locally both of those things work fine.  If i connect to a share with the box logged in and then log out of it I can still access that share, but i can' t connect to others.

So i'm thinking it has something to do with authentication, even though these are guest shares.  Not really sure where to go next though.   This is either such a stupid-easy problem, and i'm just not getting it or I'm the only one having it cause i can't seem to find a solution searching.  

Thanks to those who have tried to help, I'll post back when i solve this.  

Joe

---

