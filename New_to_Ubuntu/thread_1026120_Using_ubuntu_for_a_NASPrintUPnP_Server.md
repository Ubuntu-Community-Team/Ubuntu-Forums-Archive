---
title: "Using ubuntu for a NAS/Print/UPnP Server"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by jonnydy2j on 2008-12-30
Hi all.

i am completely new to Linux/Ubuntu but have been doing some testing of FreeNAS within my home network and have had some good results (but not perfect).

I have the following setup:

Old Compaq laptop with AMD Athlon(tm) XP2000+ processor, 1GB ram, 60GB HDD.

I am trying to create a storage server and from what I have read Linux seems to be the best option with a lot of people saying that Ubuntu is a good option for the OS.

From what I have been reading about this type of storage i have found out the following.

I will need SAMBA so that I can access my files from my Windows boxes.

I would also like FTP for use within my local network.

I have experimented using SSH for access for my files from outside of my network and this seems to be the most secure option which I seem happy with.

I want to be able share my printer from the server.

I also want to be able to stream my Music, Videos and Photos from the server to my XBOX360 and Playstation 3. I am aware that I need a DLNA compatible UPnP server to do this but the one that comes with FreeNAS is causing problems with the XBOX although I can stream to the Playstation. FreeNAS uses Fuppes but I am unable to edit the config files since when I reboot the server they revert back to their original state and from what I have read you need to change some settings to get it to work with the XBOX (I may be wrong)

The ability to setup a software RAID configuration would be a benefit but I have not looked into this option yet since I am still in the initial testing stage for what I finally want.

A HTTP server would also be a plus since I have a domain from NOIP pointing at my static IP address for the remote access via SSH and would like to display a static page since my router allows you to see its status if you type the domain name into a browser.

I am quite happy using a command line interface if that is the better way of going instead of a GUI but since I am running this server from a Laptop the display is no worry.

I am basically looking for some pointers in the correct direction as to what I need to do for each of the above points since I know nothing about Linux at all and don't fancy the prospects of trying to set these things up without knowing what to do first.

Any help as to what I need to install on the server and also how to configure the services to work correctly would be great.

Also as an after thought I would also like to be able to send an email from the server to my email account once a day with stats about the previous 24 hours of the server. This is just an extra that would be nice but is not essential.

Hopefully someone will be able to help me with this and I hope that this hasn't been answered already but I have spent hours looking all over the Internet with no final conclusion so I have had to come to you guys.

Thanks in advance and a Happy New Year to all that read this post.

Jonathan :D

---

### Post by blueridgedog on 2009-01-02
> **jonnydy2j said:**
> 
I am basically looking for some pointers in the correct direction as to what I need to do for each of the above points since I know nothing about Linux at all and don't fancy the prospects of trying to set these things up without knowing what to do first.


Well, you are starting on a long journey that will be a lot of fun.  I would not try and do all of these things at once.  I recommend you start with getting Ubuntu server onto your box and working to get samba working.  There is a link in my signature regarding sharing files with windows systems - setting up samba.  

Start there and come to the forums for help until you are satisfied, then move on to the next task.  

I also suggest you document the process so that you can write it up when you are done, leaving out the dead ends and learning experiences, so that others can have a resource that will help them do what you are about to start.

---

