---
title: "Guide to install/config home media server"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by OverrRyde on 2011-04-04
Hi guys! New to the Linux world and looking to have a media home server. I have currently installed Xubuntu on the box.
 
Basicly what it would be doing is serve media files to other devices aroudn the house ie: ps3, xbox 360, wd tv live and other Windows PC's. (xp/vista/7)
 
I trying to find a guide that can help me achieve this task but i found mostly outdated guide online (4-5 yrs old) or geared towards the more advanced Nix users. This box would basicly be headless with access from Windows via VNC and i would be transferring my media files from a regular windows laptop to the box to be served over my home network.
 
I would really appreciate if someone could point me in the right direction for a "newb" guide to achieving the above task!
 
Thanks!

---

### Post by davidmohammed on 2011-04-04
have a read of this [how-to]("http://www.havetheknowhow.com/") guide.

Also - here is some community info on [this]("https://help.ubuntu.com/community/MediaTomb").

The latter is what I use for my back-end server - I use XBMC as my front-end.

---

### Post by OverrRyde on 2011-04-04
Thank you, that first guide looks good, will be trying that out tonight when i get home. Will also be doing the second one aswell as they appear to go hand in hand.
 
As far as seeing the shared media folder on windows, is it just a matter of mapping a network drive in windows? should i be seeing it in network computers?
 
Thanks again

---

### Post by inkrypted on 2011-04-04
I have had great success with a program called PS3 Media Server. I know the title sounds kinda one sided but it's really versatile and supports alot of devices. It is also the only server I have used that supports my Blu Ray rips .mt2s and .mkv. I'll put a couple of links here for a guide and a PPA.

PPA: [https://launchpad.net/~paissad/+archive/pms-linux](https://launchpad.net/~paissad/+archive/pms-linux)

Video Guide: [http://www.youtube.com/watch?v=bvmlTpUXJBM&feature=related](http://www.youtube.com/watch?v=bvmlTpUXJBM&feature=related)

Linux Specific Forum: [http://www.ps3mediaserver.org/forum/viewforum.php?f=3&sid=ea9a57ee6b7a53259934d13ffc371cc8](http://www.ps3mediaserver.org/forum/viewforum.php?f=3&sid=ea9a57ee6b7a53259934d13ffc371cc8)

---

### Post by OverrRyde on 2011-04-05
So i followed the guide from havetheknowhow.com
 
So far so good, ubuntu setup, putty up and running, vncserver up and running, webmin up and running.
 
I setup the shares as specified in the guide, however, i cannot see the share in my windows laptop. I am completetly stuck.
 
I logged in via vnc and ubuntu cannot see windows shared either.
 
If it matters, i am running Vista Home Premium on the latop and using a Linksys WRT120N router
 
Thanks for helping out guys, i feel i am so close!

---

### Post by davidmohammed on 2011-04-05
I presume you have been following this part of the [instructions]("http://www.havetheknowhow.com/Configure-the-server/Create-users-share-folders.html")?

It worth checking that your windows box can actually see the ubuntu server.

Make sure both your server and windows box is connected to your router via cable (i.e. not wireless).

Get the ubuntu server IP address

ifconfig

then from your windows box use a DOS box

ping <ipaddress>

If you get a reply at least you know that its not a networking issue.

---

### Post by OverrRyde on 2011-04-05
Yes that is the guide i followed and is where i am.
 
I am currentyl on wireless connection from my laptop and i can definetly see the ubuntu box as i have pinged and am able to connect via putty and vnc (using server-name:1)
 
Not sure what i am doing wrong...

---

### Post by davidmohammed on 2011-04-05
can you post your smb.conf file?

Also can you confirm your Vista workgroup name

what is the result of

ls -ld /home/<yourusername>/<sharedfoldername>

---

### Post by OverrRyde on 2011-04-05
Will be doing that tonight, still at the office until 10pm!
 
Thanks!

---

### Post by OverrRyde on 2011-04-06
Ok so here is the results from doing the command you suggested:

drwxr-xr-x 2 andres andres 4096 Apr  6 00:56 /home/andres/testfolder

i also attached smb.conf file

Thanks!

PS: i actually started all over for the server, reinstalled and everything and still not able to see the shared folder!

---

### Post by davidmohammed on 2011-04-06
hi there,
  I'm not an expert at this - but these are my thoughts

Have a look at the smb.conf file - you'll see the

[global] section.

The instructions say to add

follow symlinks = yes
wide links = yes
unix extensions = no

to this section - I dont see this in your file

Try and widen the permissions for your testfolder - DONT DO THIS if you intend to make the folder visible over the internet...

chmod 777 /home/andres/testfolder

try changing the [testfolder] section to the following
	comment = testfolder
        path = /home/andres/testfolder
        browsable = yes
        writeable = yes
	public = yes

Dont forget to reboot your server after making the above changes

---

