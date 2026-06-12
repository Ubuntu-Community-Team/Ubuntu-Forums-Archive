---
title: "ubuntu file sharing"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by amin1990 on 2010-06-11
hello. Do anyone have any ideas how to set up ubuntu file sharing for ubuntu operating system?  Not with windows.  Not the samba.  File sharing between two computers or more using ubuntu.  No windows.

---

### Post by spiky001 on 2010-06-11
Hi you will need to install ssh server it,s in synaptic manager install it on which ever pc you want to share from

---

### Post by Naggobot on 2010-06-11
I think you need Samba but there is nothing to be afraid of. I did it for two computers and it was quite manageable (I would like to say extremely easy).

Below are my old notes about sharing the home folder. 
  
> 
Home folder &#8594; click to upper level &#8594; select home folder icon and right click ->Sharing options
 

Click Share this folder
 Give share a name
 Click allow others to use
 

 Edit etc/samba/smb.conf file, set correct domain name 

 

 Set user rights  
 &#8594; group sambashare &#8594; add sharing users to group
 &#8594; select shared folder &#8594; groupaccess , sambashare
 Sharing the folder installs Samba automatically and I do not know if editing the smb.conf is actually required. I just picked it up from somewhere. I set the domain name to same I have defined in my local (wireless) router

User rights are edited through system->administration->users and groups

There are a lot of video tutorial available for older Ubuntu versions if you google a bit, search youtube, google videos and just google. 

I do admit that my experiences with shares are a bit contradictory since managing user groups and rights can be diffucult since rights are not inherited automatically from parent folder. I do not know if it is possible to set it up so that the rights are inherited but my understanding is that they can not be. This can be a problem when remote user creates a new folder to shared folder. Now user rights are not inherited and if the rights are not setup correctly then the local user has no access to folder / files. I have had some problems with this. Granted I do not use share a lot. 

I do not know about ssh, and ftp. You might be able to use either to transfer files between computer.

edit: It seems I use way too much time to write :-)

---

### Post by nhasian on 2010-06-11
there's several ways to do it.  samba is probably the easiest to get up and running.  i use ssh all the time to login and transfer files as well as forward X applications to my local display.  you may also want to look into [NFS]("http://ubuntuforums.org/showthread.php?t=42737")

---

### Post by Morbius1 on 2010-06-11
Nautilus-share ( described above ) is as easy as samba gets. However if you really don't want to use samba and your needs aren't too demanding I would suggest [COLOR=Blue]**Giver**[/COLOR] in an all ubuntu network:
> [COLOR=Black]Other people running Giver on your network are automatically
discovered and you can send files to them by simply dragging
the file to their photo or icon shown in Giver.[/COLOR]It's all done using avahi. 

Sets up an icon on the panel. Click on it and you see everyone else on the lan. Click on one of them and it will ask you if you want to give them a file or a Folder. The recipient gets a notification that something has arrived and clicking accept will place the file/folder on his desktop.

[COLOR=Blue]EDIT: Here's a better description with screenshots:[/COLOR]
[http://tombuntu.com/index.php/2008/12/19/simple-desktop-file-sharing-with-giver/](http://tombuntu.com/index.php/2008/12/19/simple-desktop-file-sharing-with-giver/)

---

### Post by HermanAB on 2010-06-11
There is nothing easier than NFS, which is the standard UNIX network file system:
[http://www.aeronetworks.ca/nfs-howto.html](http://www.aeronetworks.ca/nfs-howto.html)

---

### Post by egalvan on 2010-06-11
> **HermanAB said:**
> There is nothing easier than NFS, which is the standard UNIX network file system:
[http://www.aeronetworks.ca/nfs-howto.html](http://www.aeronetworks.ca/nfs-howto.html)

On a strictly *nix network...

+1 for NFS  (Network File System) which is native to *nix systems.

No NEED for ssh, or Samba, or Nautilus shares, etc-...
athough you can certainly go those routes if you choose.

CHOICE, it´s what makes *nix so good.

---

### Post by lukeiamyourfather on 2010-06-11
Samba will work but it has higher overhead and lower performance than NFS. Mostly Samba is there to share with other systems that are not Linux (e.g. Windows). Also NFS is easier to setup than Samba. Cheers!

---

### Post by drdos2006 on 2010-06-11
Here you are. Check this out.

[http://ubuntuforums.org/showthread.php?t=249889&highlight=HOWTO%3A+NFS+Server%2FClient](http://ubuntuforums.org/showthread.php?t=249889&highlight=HOWTO%3A+NFS+Server%2FClient)

regards

---

### Post by egalvan on 2010-06-11
> **drdos2006 said:**
> . Check this out.

[http://ubuntuforums.org/showthread.php?t=249889&highlight=HOWTO%3A+NFS+Server%2FClient](http://ubuntuforums.org/showthread.php?t=249889&highlight=HOWTO%3A+NFS+Server%2FClient)


One of the BEST (simple) guides to NFS.
Took me all of five minutes to network two Ubuntu machines together, by following this guide.

I had forgotten bout it.

---

### Post by baddnady23 on 2010-06-11
NFS is the way to go if your strictly using linux systems.  Follow the howto and install the neccessary packages on the server, then install the packages that are needed for the client.  Once it is set up, simply add 1 line to your fstab and the share will be available to you on you desktop everytime you bootup.  After trying many different ways to share files, I have found this to be hands down the best way to go.

---

### Post by amin1990 on 2010-06-12
I didn't know that NFS would be that easy.  Let me try and test it out.

---

### Post by 3rdalbum on 2010-06-12
On my all-Linux network, I still use Samba; because if I need to add Windows clients down the track, it still can be done without changing anything. Also I have two media boxes that plug into my TV and stream videos from across the network; they run on embedded Linux but I don't think they support NFS shares, only Samba.

---

### Post by amin1990 on 2010-06-12
Nice.  I click the link you gave me ([http://ubuntuforums.org/showthread.p...erver%2FClient](http://ubuntuforums.org/showthread.p...erver%2FClient)) and follow the instruction.  After that, when I click network in the menu, it only show windows network.  It doesn't show ubuntu network.  Why is that?  Does it have to do with ubuntu firewall or router firewall?  I may be missing something here.

---

### Post by DoctorTim on 2010-06-12
I am a complete newb, so take this with a grain of salt, but...
I installed 10.04 on a laptop a few weeks ago just to try it out. My house has 5 different machines running linux, XP, and mac OSX. My kids and I have been playing with the bluetooth file transfer system and it is virtually plug and play with all of the above as well as with my wife's iPhone.  I didn't need to download anything or update anything, just click on the bluetooth icon and setup was self explanatory.  My desktop machine (an older iMac) has bluetooth and all of the laptops support it. It only works within the house (obviously), but is quite functional for sending photos, music files and text.  It is a bit slower than over the wireless LAN, but works well.  Like the man said, the beauty of *nix is a choice.

---

### Post by amin1990 on 2010-06-14
I restart the ubuntu.  The file sharing is working now.  No wonder.  Thanks for the help.

---

