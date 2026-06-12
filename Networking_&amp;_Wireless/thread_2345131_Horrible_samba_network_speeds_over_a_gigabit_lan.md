---
title: "Horrible samba network speeds over a gigabit lan"
date: 2016-11-30
forum: Networking &amp; Wireless
---

### Post by ncage on 2016-11-30
Hello Everyone,


I&#8217;ve been running Ubuntu since 14.04 and have upgraded as soon as new versions have came out. My network speed has always been crappy sometimes its been better than other times. I remember one point which I couldc onsistently get 50MB/sec and believe it or not I was happy. Right now with 16.11 I get 6MB/sec for downloads and 7MB/sec for uploads.This is all over a gigabit lan. I&#8217;ve tried every recommendation that I could find from googling. So i&#8217;ve played a lot with my smb.conf settings an absolutely nothing i&#8217;ve done has helped. For one I know my hardware supports jumbo frames. I only buy intel nics but honestly when ive tried to play with enabling jumbo frames it has made the situation worse. 


The file server I'm reading/writing to is a Server 2016. It was previously Server 2012 R2. When i&#8217;m using a windows client I can get 80MB/sec easily. The other day I blew out my smb.conf file and started over but nothing has helped. Even with a suboptimal smb.conf and not enabling jumbo packets I should still be much better than 6MB/Sec. Here is an example of something i&#8217;ve tried:
[https://ubuntuforums.org/showthread.php?t=2279604](https://ubuntuforums.org/showthread.php?t=2279604)


Right now my smb.conf is bare bones (I can send it if you want but there is not much there). Trouble shooting this is a pain in the neck. 


When I tried jumbo packets I set the packet size on my windows server to 9014 which I thought was weird but thats what I have to select on the windows server if I want to have 9k frames but I would have thought it would have been 9216. On ubuntu I tried both 9014 and 9216 and both were crappy. I end up going back to the default &#8220;automatic&#8221;.


Like a lot of people I have windows software that I need to run so I use vmware workstation. Unfortunately the network issues have been a major issue with lightroom my images reside on the file server & I shoot a [COLOR=#111111][FONT=Amazon Ember]36.3[/FONT][/COLOR][COLOR=#111111][FONT=Amazon Ember]MP camera and all my images are in raw (very large files) so these network issues have almost made it unusable.[/FONT][/COLOR]


[COLOR=#111111][FONT=Amazon Ember]I hope I can get these issues resolved because if I can&#8217;t I have to go back to windows 10 which I HATE with a passion. [/FONT][/COLOR]


[COLOR=#111111][FONT=Amazon Ember]Any help would be GREATLY appreciated.[/FONT][/COLOR]

---

### Post by TheFu on 2016-12-01
First, check the log files.  They are usually very helpful and announce errors and warnings.  Look at system and samba logs.

Jumbo frames is a loose standard. At least it has been implemented very differently by different vendors, IME.  I've had to use 8960 as the packet size, since some vendors think anything near, close-to, 9000 is fine. Even after validating specifications, my Windows machine wouldn't keep correct time when jumbo frames were configured.  Performance wasn't THAT bad without it - usually 65-80MB/s.

What is this "mysmb.conf" - you keep mentioning?  The config file is "smb.conf" a different name will require passing that into the startup.

So, normal troubleshooting would start by looking at the specifications for all hardware involved.  SPECIFIC HARDWARE, model numbers AND lots.  Then look at all the software involved. Get the exact versions.  Server and client.  Test using another protocol to find out if CIFS is the only issue or if there is a failing switch port or if there is a failing cable involved.  Simplify and test.  Did that solve it or not?  Simplify and test again.

Also, testing using a live-boot, not an install, could help determine if this is a config issue or not. And lastly, sometimes drivers get corrupted (I've not experienced this myself) I've heard.  I only run LTS releases. Don't need any more surprises on work machines than already happens. 6 months of support just isn't enough.

I'm curious, what is 16.11? Never heard of that.

---

