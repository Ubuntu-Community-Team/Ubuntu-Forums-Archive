---
title: "Link my internal vfat32 Hard Drive to WedDAV home directory"
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by mdsypr on 2007-08-26
I have Apache2 running, SSL working so I can connect securely and WedDAV is working so I can login to my davhome directory which is located /var/www/davhome.

My problem is this ... I have an internal vfat32 drive with over 200GB of data that I want to access using WedDAV so

HOW DO I POINT DAVHOME TO MY WINDOWS DRIVE WHICH IS LOCATED ON /MEDIA/SERVER?

I know how to connect to server but that puts a shortcut on the desktop and I can't copy and paste to my davhome directory.

I am sure there is an easy easy way, can someone help?

Thanks
Mike - new Ubuntu user, love it.

---

### Post by mdsypr on 2007-08-27
I am disappointed in this forum ... I though this was for new Ubuntu users can go for answers?

This post is almost a day old and no one can provide any assistance?

I started using Ubuntu 4 weeks ago and in that time I formatted 3 computers, shared my internal windows drive, configure apache, SSL on apache and installed the WebDAV as well so I know alittle more than the average user.

WebDAV is so poorly discussed in this forum is unbelievable ... where are the basic posts that discuss:

1) What is required for WebDAV?  Do you need LAMP or just Apache?

2) Do you need a client to see the files to upload using WebDAV? If so what are they?

3) Seems for Web Folders to work with XP your WebDAV needs to have frontpage extentions running otherwise you can't connect your WebDAV folder .. if that is true how do you do that?

4) Is there a web based client to access your WebDAV folder? No, just typing in the URL only lets you view files, it doesn't let you upload.  I can't believe there isn't a JAVA app or something you can use.  I did find OpenWebFolders extention in Firefox but no idea how to use it (no documentation) and when I typed in my URL and clicked OPEN AS WEB FOLDER nothing happended, just hung.

5) Do you need separate services to listen to music or watch videos online? What about opening Opeoffice and PDF's?  You know the basic stuff anyone would want to know.

Thank God I am pretty good with computers but all these basic questions WITHOUT easy to understand and detailed answers are what is stopping Ubuntu to kick XP and OS X.  

A little help would be greatly appreciated.

Frustrated Ubuntu user.

---

### Post by mdsypr on 2007-08-29
Again what a dissapointment .... my original post was from 2 days ago, my latest from a day ago and still no one can help me out?

Well I figured out finally (Samba always changes) how to mount my /SERVER to my /VAR/WWW/DAVHOME but now I have a new problem.

1) When I enter my user name and password for /var/www/davhome instead of seeing whats in the file I get a 405 error.  I am the owner of the /SERVER windows drive and I think it has something to do with permissions?  

2) Even if I get this to work I realized that to mount my drive in windows via web folders I need to have frontpage extentions loaded ... does anyone know this?  Is there a client based on HTTP that I can load so when I login to my drive it shows up IN FIREFOX with the full features of WebDAV? upload/download  ???

3) This isn't a problem but once I figure out how to map my drive I would love to add a music and video capability to it so I can easily listen and watch my stuff on the road.

Please, someone out there point me in the right direction.

Thanks,
Mike

---

### Post by will71110 on 2007-08-29
mdsypr,  Sorry to hear that no one is responding to your thread.  Just remeber some times the forums get out of control ie to many at one time and yours might have goten over looked by someone who might know.

Couple of questions though,

How are you mapping the drive using samba?
Do you have to log into the drive to have access to it?

---

### Post by mdsypr on 2007-08-29
WIll,

Thank you so much for at least responding ... I installed the smb client and mounted it with that protocal.

My ID Mike has access to that hard drive and I know when I created /var/www/davhome I chmod some type of permission and wondering if that has something to do with it since that folder is part of the www-data group (I believe) which is different that my "mike" ID.

Also, even if I get this to work I will at least be able to download my files but I still don't know if there is a web based WebDAV protocal so I can use my portable firefox and login to upload or download my files.

My office locks down everything but I can hit my web site using SSL and was hoping WebDAV was the solution.

Thoughts?
Mike

---

### Post by will71110 on 2007-08-29
Oh I just relized this is an internal hard drive.  On fat32 I dont believe you can assign permissions to that drive.  It's generically access to all. I believe root initally has access to the shared folder first.  Are you sure it's fat32 and not NTFS?  If it is NTFS then that can cause issues.

Also chaning files on the fat32 can damage windows ( as it can in NTFS but NTFS is read only in ubuntu by it self).  Carefull when messing with it.  You will not need SAMBA to do this.  SAMBA is only for access to a drive over a network.

Anyways let me know.

---

### Post by mdsypr on 2007-08-29
Will,

Thanks again  .. a few things

1) Yes it is a FAT32 drive and currently I only use Linux but wanted the flexibility if I get XP or OS X.

2) My "mike" ID and "mike" group only has permissions for that drive and the security works ... I created another ID and tried to open the drive and it wouldn't let me.

3) It is internal so if I don't need Samba how else would I mount a windos drive to /var/www/davhome?

4) Is there any web clients I can use once I get this working?  As I said XP needs you to have frontpage extensions loaded to use it as a web folder and my company locks down everythings and I don't have admin rights on my work laptop so I can't install anything ... even if I can install something on my portable firefox the way the company configures the networks, ports, is a nightmare so was hoping for a web app or something.

What if I just added my "mike" id to the group www-data that /var/www/davhom owns?  Can I add "mike" to two different groups?

I did build 3 Ubuntu computers from scratch in a month and have them all sharing files, got apache 2.0 to work, SSL for encryption and now WebDAV so I am somewhat knowledgeable about computers.

Thanks, 
Mike

Mike

---

### Post by will71110 on 2007-08-29
If you are mounting it on the computer the hard drive is installed on then no you do not need SAMBA.   SAMBA only deals with smbfs Session Message Block File System which only deals with file sharing over networks.  If you are mounting over a network (mapping is what windows calls it) from linux to windows or windows to linux then yes you will need it.

Are you trying to mount it to two location on the same computer?  Now if you restrict your name to only have access to the drive then no one will beable to access though web.  You'd have to atleast give everyone read access.

for your other question, webmin is a good admin tool

---

### Post by mdsypr on 2007-08-29
Yes, I am installing the internal hard drive on the same machine and in two different locations.

Currently it is mounted on /media/SERVER and I also wanted to mount it to /var/www/davhome so I can use WedDAV to access the drive via the net (SSL of course).

Like I said even if I get it to work I still need a way to upload and download via the WebDAV protocal via the net.  If I can use Webmin your telling me it has in support for WebDAV?

If it does how would I hit it from the net?  My public IP address would have to be re-directed in apache somehow to Webmin?

If WebDAV works then only my ID can open the folder, at that point I don't care who reads or writes to it because it will only be me.

Am I making sense?  
Mike

---

### Post by will71110 on 2007-08-29
I believe you can only mount it once on a PC but I haven't tried it.  You don't have to have it mounted in the /dev/ folder.  you can mount it to any folder you wish but the folder has to be empty.

Also with Webmin,  I'm not sure if it supports webDAV.  webmin is a admin web tool so you can manage server type software remotely (you can even send commands to run from it real nice feature to have).  Webmin can manage apache I know of.  

As for webDAV, I haven't played with it so I don't know much about it.  Anyways sorry if this isn't much help.

---

### Post by mdsypr on 2007-08-29
will,

thanks, I can confirm that I can mount my internal drive to multiple mount points.

When I click on /var/www/davhome I am still getting 405 errors, I don't have permissions.

I know it has something to do about permissions but I don't know what.

Permissions for my SERVER = username=mike, group=root

Permissions for /var/www/davhome = username=root, group=www-data

Any ideas?

I also created a LINK to SERVER but that doesn't even show up when I load the page in Firefox, I can't see the directory to click on it within davhome.

Thanks,
Mike

---

### Post by will71110 on 2007-08-30
Somehting that poped into mind.  Have you check the Apache log to see why you are getting the 405 error?  It could give you a hint?

---

### Post by mdsypr on 2007-08-30
No I haven't but that is a good idea ... I am sure it has something to do with permissions with the WebDAV folder and my server.

I am at work but I will check.

So even if I get this to work I still need a client to use the WebDAV protocal so I can add and remove files, is the best WEB based thing out there Webmin?  If that is the case how would I set-up my router to access it?  Just create a special port that isn't blocked by my ISP and port forward to whatever port Webmin is running on?  Does anyone know what port that is and if it is configurable?

Mike

---

### Post by will71110 on 2007-08-30
webmin works off port 10000 but you can chane that (Port 10000 is in the public range of ports and shouldnt be blocked).  I use No-Ip.com to set up an DNS entry on the WWW so that I can access it from anywhere even if my ISP changes my IP address.

---

### Post by mdsypr on 2007-08-30
Will,

Isn't No-IP a scam? I mean I have had dynamic IP for 4 years and not once did my IP change on me.

A few questions:

1) Do I have to register my IP so instead of typing in 71.71.71.71 a person can just type in [www.mike.com](www.mike.com) ?  Or does apache have something in there that I can utiliize?

2) Is there an easy way to have apache run off my internal windows drive since I have much more storage there?

3) Does anyone know if it is true (I did read it is) if you need Frontpage extentions to run with WebDAV to mount it in windows?

4) Also, is there any web based client one can use to access WebDAV.

I am only looking for secure file transferring via the web (SSH won't work from my office, they block everything) and I thought WebDAV would be it so I have SSL working in Apache 2.0 but as you know I can't seem to link my hard drive to the /var/www/davhome and even if I do I need a client to run to access it and I don't want anything Microsoft.

Is Webmin the ultimate solution?

Mike

---

### Post by will71110 on 2007-09-04
No-Ip is prob a adware site.  It works though. (my IP changes everytime my router gets rebooted). Anyways if you want to get a named Host in DNS you'd have to register it outside your network.  That's if you are planning to access stuff  from outside your network. 


For the SSH,  Have you tired openSSH?  It automatically installs SFTP which is secure. You can use Core FTP to connect to it using port 22.  When you say your work blockes it, you mean on the network right?

---

### Post by mdsypr on 2007-09-08
Will,

Yeah I was away on vacation and yes my company blocks everything.

I still need to figure out how to link my directory (with all my files) to the Webdav home directory.

I know it has something to do with permissions, the Webdav home directory is owned by Root and www-data group .... my directory is owned by Mike, group root and only has read/write/execute access for me mike, no one else.

I am thinking Webdav need to work with files owned by root?  Anyway around this or to apply permissions when using Webdav?

Also, is there a work around to mount a Webdav folder in windows if I don't have the frontpage extensions loaded?

Any help would be appreciated.

Thanks,
Mike

---

### Post by mdsypr on 2007-09-09
Super disspointed ... no one (besides Will) can post to help out a fellow Ubuntu user?

Been weeks, guess basic questions aren't worth it? Where are the guys that know exactly how to fix this so I can learn as well as many others?

Bottom line is you can't change permissions on a fat32 drive and WebDAV needs to have the group = www-data so I am going to just reformat to ext3 and chmod to that group and see if that works.

But seriously, this is a weak board if no one can post, WebDAV is a huge area of growth and what I am trying to do is not that uncommon but it's not documented well at all on the net .. now the last thing I don't understand is why Microsoft needs you to have frontpage extentions running on your server to access WebDav, that is just stupid.

Mike

---

