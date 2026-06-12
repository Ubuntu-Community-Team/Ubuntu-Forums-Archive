---
title: "sound and drive sharing from windows"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by n8makar on 2008-09-13
Good Afternoon!

I have a ubuntu laptop that remotely accesses my XP Prof. desktop without a problem.

However, I want to share the drives from my desktop to my laptop, but can't seem to do so.

Lastly, even with sound sharing enabled, no sound plays on my laptop when connected to desktop. Sort of defeats the purpose of remote connection for me (I want to access all my music and movies from desktop)

I have searched to no avail so are there any gurus out there that can help?

Thanks!

---

### Post by n8makar on 2008-09-13
bumper

---

### Post by cariboo on 2008-09-13
You have to setup file sharing on your xp computer. Usually all you have to do is right click on the directory that you want to share and click share. You don't have to do anything to Ubuntu as smbclient is installed by default. Make sure the computers are in the same work group. Ubuntu uses WORKGROUP by default so just change the work group in xp to WORKGROUP also.

You should then be able to access your xp computer from Places-->Network

As for the sound do you have to enable network sound device discovery in
Pulse Audio Preferences. If you do have it installed search for padevchooser in Add/Remove Programs or Synaptic Package Manager.

Jim

---

### Post by n8makar on 2008-09-13
ok im going to try that after i grab a bite to eat. i think they are on the same workgroup now though

---

### Post by n8makar on 2008-09-13
actually i just reread your post and realized something. I'm actually connecting through remote desktop. so I'm on remote desktop trying pull files from that onto my laptop.

i know windows has the option to share drives when it is the one connecting (which i never did get working either) so what is the equivalent for ubuntu gutsy?

---

### Post by n8makar on 2008-09-14
this is ridiculous now i cant even open port 3389 in comodo on the windows to connect. this should be easier than it really this.

---

### Post by Bucky Ball on 2008-09-14
It is. Make them in the same workgroup, right click the drive in windoze (sitting at your windoze computer) you want to access through your linux machine and it should appear under Places->Network->Windows Network (from memory) on your Linux machine. No remote desktop required, that sounds like it is complicating things for what you want to do. You shouldn't need to fiddle with the port opening etc as you are on the same network and that should be fine.

Computer Name: Laptop
Domain: Workgroup (or whatever you choose)

Computer Name: Desktop
Domain: Workgroup

... will put them in the same domain and then you should see your Windoze box no problem.

A really easy way to set up a share folder that will appear on your Windoze desktop from Ubuntu is outlined here:

[http://ubuntuanswers.wordpress.com/](http://ubuntuanswers.wordpress.com/)

> 
i know windows has the option to share drives when it is the one connectingTo put this in perspective - Windoze has the option to *join a network* and share its drives/partitions/folders/files on that network, *regardless* of who's connecting. Once you have joined a network, as you know, you then simply right click on the item you would like to share and it is shared *on the network* (or in the domain - public/private domain) with the permissions you have set. We are not talking about a samba server/client situation here, unless you intentionally set one up.

---

### Post by n8makar on 2008-09-14
ok thanks for your help! ive been working on computer for awile but only ubuntu for about a year and ive just started fiddling with network config.

i actually have it working! this thread 

[http://ubuntuforums.org/showthread.php?t=824710](http://ubuntuforums.org/showthread.php?t=824710) 

(which i found on accident) helped me a lot and i got more advanced commands that i needed to get sound and share drives.

i understand what you are saying with domains and such too. im going to have to try that with a bunch of local computers. for now though im just going to keep messing with my remote laptop connection.

thanks again!

---

