---
title: "Home media network with Samba"
date: 2014-07-22
forum: Networking &amp; Wireless
---

### Post by aaron50 on 2014-07-22
Hello All,

I am creating a home media server using ubuntu 14.04. I am brand new to Ubuntu and i am trying to learn the in's and out's. I have successfully installed ubuntu, openssh, and samba. I am able to connect to my server via webmin, but i am trying to do everything via the command propt to learn (this is meant to be a time consuming process). I have followed the instructions here:[http://linuxhomeserverguide.com/server-config/Samba.php](http://linuxhomeserverguide.com/server-config/Samba.php) to set up my server and to configure samba and my windows machine. I have followed all of the instructions and looked around online. I have tried everything that i could find online to get my pc to see my server, but no luck. Like i said, i can see my server from webmin, and i have used it to set up samba a little, but my windows (win 7) cannot see the server. Is there a way in the command line of my server to see if it is putting out a signal or anything, why can my laptop not see my server. I have tried to set up my mac to see it as well with the same site: [http://linuxhomeserverguide.com/server-config/NFS.php](http://linuxhomeserverguide.com/server-config/NFS.php) and i had no luck there either, the mac couldn't see the server either. Can someone please help me out. 

Thanks,

Aaron

---

### Post by TheFu on 2014-07-22
Can the systems all 'ping' each other by name?  That usually means modifying /etc/hosts on each of the machines to include static IPs for all the machines on the subnet.

What is the output from **testparm**?  This will help troubleshoot samba/CIFS shares.  If you have the client libraries loaded, nautilus should have a "sharing" menu item that can be used to manage shared directories.

It is good that you are trying to get NFS working. It is faster than other options and maintains file/directory permissions as expected, unlike CIFS.  Make certain that userids match (the numbers) between all the /etc/passwd files.  1001 on ubuntu needs to be 1001 on OSX.

If your playback machines/systems are DLNA, setting up Plex Server might be easier. Unfortunately, Plex Server is NOT F/LOSS, but it is Free software.  I think it is the best DLNA server available and really easy to setup.  Smart-TVs, WDTV, Chromecast, XBMC, Android, and any other DLNA client/renderer will work with it.  I tried about 5 other methods and have switched to Plex (without a plex-pass or even a plex login) about 9 months ago. Wish I would have done that years earlier.

---

### Post by aaron50 on 2014-07-22
Thank you for your response. 

I am a little unsure about the things you are talking about. Treat me as being brand new to the environment without windows GUI (i have never done command line work, and am trying to learn). I am an experienced code writer and reader in many different languages, but i have never delt with the "guts" of a computer. That being said. 

On my windows laptop i can see my windows desktop in the network section and vice versa. So i know those computers are set up to talk to one another. I need to be able to get the server to communicate with them.

The mac is not so important to me at the moment. I really am looking to get the server talking to windows, since that is what i primarily use.

I have looked into XBMC because of a coworker, but your suggestion of Plex server looks like a go to first. Although, my first real task is to set up the communication from computer to computer.

What do you mean testparm? do i put this into my ubuntu command line? Could you please explain a little more on what i need to do.

Again, thank you for your help, it is much appretiated!

---

### Post by TheFu on 2014-07-22
The nfs how-to seems to be missing changes to the server, /etc/exports file.  Webmin is the long way around for that and can be a huge security risk (webmin is good AFTER you already know what you are doing, not as a short-cut to get there. It hides important details.  google "ubuntu nfs" for the ubuntu nfs how-to.  It is 1 line in 1 fine to add, then restart the nfsd service. That's it.

---

### Post by aaron50 on 2014-07-22
i thought i couldn't use nfs to talk to windows, don't you have to use samba? Thanks

What do you mean 1 line in 1 fine to add?

The output from testparm are three catagories: Global, printers, and print$. What are you looking for inside them?

---

### Post by TheFu on 2014-07-23
> **aaron50 said:**
> i thought i couldn't use nfs to talk to windows, don't you have to use samba? Thanks
Need? no.  Is NFS on Windows usually the best idea? No. CIFS is what Windows wants and Samba is the CIFS implementation of choice around the world.

> **aaron50 said:**
> What do you mean 1 line in 1 fine to add?
/etc/exports on the NFS server. It needs 1 line to NFS share storage.
google "ubuntu nfs" will find the Ubuntu NFS how-to.

> **aaron50 said:**
> The output from testparm are three catagories: Global, printers, and print$. What are you looking for inside them?  All of them. It is hard to troubleshoot a problem when information is being limited.  OTOH, if you ran nautilus and found the built-in "sharing" menu for cifs, that would be much easier.

---

### Post by aaron50 on 2014-07-25
I figured it out. I found a site that was really helpful to start up users [http://www.howtoforge.com/samba-server-ubuntu-14.04-lts](http://www.howtoforge.com/samba-server-ubuntu-14.04-lts) for any future readers

---

### Post by TheFu on 2014-07-25
While the howtoforge does make great how-tos, don't expect them to be secure by default - that means be careful putting anything from there on the internet without doing your own research around the security of their instructions.

If this is solved, please mark the thread in that way so others find it.

---

### Post by aaron50 on 2014-07-25
The fu,

thank you for that not. I will look into ways to secure it. Thanks!

---

### Post by gordintoronto on 2014-07-26
For future use, you might also look for how-to's in the Ubuntu Community Documentation. Some of it is out of date, but a lot of it is excellent.

Example Google search: ubuntu server samba

It's not clear whether you installed Ubuntu Server, or Ubuntu Desktop. Server is command-line only, which means it takes three times as long to set anything up -- but the performance is superior.

---

