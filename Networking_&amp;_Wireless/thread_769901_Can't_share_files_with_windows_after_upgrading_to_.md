---
title: "Can't share files with windows after upgrading to 8.04"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by ThaDiggler on 2008-04-26
Ran into a problem after upgrading to Hardy.  I was unable to see my shared folders on my windows box. They don't appear under network servers; and I can't do a connect to server to get to them.  The only way I can get access to them is by adding a network folder via Konqueror.  If anyone knows how to resolve this please post a reply.

---

### Post by tvphil on 2008-04-27
Just like you, I was surprised to discover "Shared Folders" is no longer in system administration. Here's what the folks at Ubuntu replaced it with. First of all, in system administration>services, shared folders should be checked, if it isn't, check the box. Next, go to any folder in your Home folder or the entire Home folder itself, right click and you'll see the words "sharing options" right below "empty trash" as one of your choices. Click on sharing options and you'll see what has replaced Shared Folders.Hope this helps!

---

### Post by ThaDiggler on 2008-04-27
tvphil... Setting up the shares is the easy part.  I just can't see or access my windows shared folders from the network servers option after the upgrade.  From windows I can access my ubuntu shares.

---

### Post by tvphil on 2008-04-27
Sorry I misunderstood your problem the first time. You might want to go into synaptic and see if you have smbfs and smbclient installed. While you might have Samba and Samba common installed, you might not have these other 2. They give you the protocol Windows needs for you to access them from Ubuntu or any Linux distro.If you do have smbfs and smbclient, then it might be a permissions issue in Windows, such as read and write access.

---

### Post by GalloGlas on 2008-07-16
I'm having the same problem.  As are many as it appears.

I've got smbfs and samba installed but for some reason I can't see windows shares.  But I can go the other way.  Windows can see linux shares.  So if I want to transfer files I'm forced to write to linux from windows machine.

---

### Post by jtx472 on 2008-07-16
I'm having the same problem and I don't understand why none of the moderators has come up with a solution.  When I started my own thread, I got 17 hits but no replies???

---

### Post by GalloGlas on 2008-07-16
> **jtx472 said:**
> I'm having the same problem and I don't understand why none of the moderators has come up with a solution.  When I started my own thread, I got 17 hits but no replies???


Its probably a combination of things causing this.  I've seen many, many posts about this problem.  Some people have managed to solve it.  Unfortunately, none of the solutions worked for me.:confused:  

You gotta figure tho.  Samba isn't all that great.  It has caused me more problems across 3 versions of linux.  While it does suck to have to go to my windows machine and write into my linux box, at least i still have some network sharing capability.  Even if it is only one way.  

The Moderators are great here.  Most of the solutions I find are from the users.  The moderators do help from time to time but I wouldn't place blame on them for the lack of response.  My best suggestion is, go through all the threads about this problem that you can.  Maybe you'll be one of the lucky few that has one of those solutions actually work.   

I'll just have to keep looking for mine.

Until then... my hat goes off to all the wonderful people here that lend out their knowledge for free. :wink:

---

### Post by GalloGlas on 2008-07-16
omg... i'm an idiot.  I used the ip of the windows machine...

Just enter smb://"ipofwindowsbox"  

I tried it for giggles and sure enough the shares pop up.   Why it can't be accessed through the network browser is beyond me.  

Oh well... as long as it works.

EDIT:  btw... it might ask for a password.  I never set one so I left it blank and it still accessed the folder.  

Just save a bookmark and you're good to go.

---

### Post by sputnikkk on 2008-07-22
>  Re: Can't share files with windows after upgrading to 8.04
omg... i'm an idiot. I used the ip of the windows machine...

Just enter smb://"ipofwindowsbox" 

Where did you enter that?  Command line .... no?

---

### Post by adrien214 on 2008-08-21
> **sputnikkk said:**
> Where did you enter that?  Command line .... no?

no, go to your the File Manager, then to the Menu "Go..." and then click on "Location" 

an address bar will show up and you can enter the adress.

anotherway is to create a shortcu/launcher with *smb://ip.to.your.windows.box* in the command.Make sure, however, to select "location" when making a launcher and this **before** entering the name of your location, it doesn't work to write your location next to "command" and then selecting "location" from the dropdown menu, I guess we can call this a bug.

---

