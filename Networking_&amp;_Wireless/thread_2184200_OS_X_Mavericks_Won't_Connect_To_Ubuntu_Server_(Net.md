---
title: "OS X Mavericks Won't Connect To Ubuntu Server (Netatalk, Avahi)."
date: 2013-10-28
forum: Networking &amp; Wireless
---

### Post by sagabergman on 2013-10-28
Hi.

I'm really sorry for posting this. I have googled like crazy and I'm on the verge of desperation here.

Basically, I followed this guide:

[http://motionsoundfx.com/2012/05/ubuntu-vnc-afp-macosx/](http://motionsoundfx.com/2012/05/ubuntu-vnc-afp-macosx/)

To create a small personal file server. When I installed it, I was able to connect to it just fine, I connected with my Ubuntu username and password and I was able to see the home directory. But later, I had to restart the file server so I could prepare a couple of other hard drives to put in.

When the server restarted, I tried to connect to it, but I got an error message on my Mac:

"The version of the server you're trying to connect to connect to is not supported. Please contact your system administrator to solve this problem."

Again, I have googled like crazy for this, and everybody says it is a problem with OS X Lion and up (assuming it affects Mavericks too). I have tried all the fixes mentioned for Lion and Mountain Lion and I haven't had any luck. That's the reason I'm posting this here: I suspect the problem is with my Ubuntu server. This happened after I restarted the server. Before restarting the server, I just put in my credentials and saw my home directory. Something when I restarted the server must have been messed up.

I have found some other solutions, including to use "SHX2" in the conf file, but it hasn't worked for me.

I ask for your help to solve this issue.

Also please understand I'm completely illiterate when it comes to Linux. This is a nice chance to me to learn the OS so please give me detailed steps to do things if you deem it necessary. Thank you!

I'm using Ubuntu Server 13.10 (the latest one as of today).

---

### Post by sagabergman on 2013-10-28
Whoops accidentally posted a dead link. Fixed now.

---

### Post by Kmargo945 on 2013-11-23
I been having issues with Mavericks and Lion connecting to my server and I followed your link and saw this note in the tutorial: 
> **NOTE**: In Mac OS X Mavericks, Apple has shifted from  using AFP in favor of SMB2. I will update this post once I figure out  how to get Ubuntu and Mac to talk to each other. In the mean time please  hold off on configuring this if you are using Mavericks. Any suggestion  are welcome in the comments below.

Then I Googled Mavericks SMB2 and found this article on ZDNet:
[http://www.zdnet.com/mavericks-smb2-problem-and-fixes-7000022519/](http://www.zdnet.com/mavericks-smb2-problem-and-fixes-7000022519/)

Which had this line:
> Apple quietly announced that it was [replacing its ancient Apple Filing Protocol (AFP) with SMB2]("http://reviews.cnet.com/8301-13727_7-57588593-263/os-x-mavericks-switches-to-smb2-networking") in July.

I am not sure if Mavericks will support AFP or not, but this article( [http://www.macwindows.com/TIP--Workaround-to-Mavericks-file-sharing-is-to-force-SMB.html](http://www.macwindows.com/TIP--Workaround-to-Mavericks-file-sharing-is-to-force-SMB.html) ) says > Mavericks now defaults to SMB2 file sharing protocol, but a bug seems  prevent OS X from using SMB1 or AFP when the server doesn't support the  newer SMB2. Maybe switching to Samba from Netatalk for file sharing would be an option since Samba supports SMB2. I'm trying to get Time Machine to work on mine so that's not really an option for me. Wish I could offer more but I'm also learning to work with Linux.

If I find anything else out I'll post it here.

Raul

---

### Post by Kmargo945 on 2013-12-01
Got it to work on Mavericks, not sure how. I was on an Apple forum page, sorry I don't have a link, and one of the posts actually installed the dependencies before installing Netatalk. I did that and then followed [this]("http://pwntr.com/2012/03/03/easy-mac-os-x-lion-10-7-time-machine-backup-using-an-ubuntu-linux-server-11-10-12-04-lts-and-up/") tutorial. I configured AppleVolumes.default and the only change from before is that I removed the volume passwords. Once I restarted I was able to connect via Go -> Connect to server and put in my address. The volumes mounted and I was able to drag and drop filles to and from the server. So, outside of the dependencies and passwords, nothing is different from my previous attempts. Hope it helps.

Raul

---

