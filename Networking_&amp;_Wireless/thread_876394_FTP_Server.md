---
title: "FTP Server"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by thevenerablez on 2008-07-31
Hi,

I have Ubuntu 8.04 desktop installed on a Mini-ITX machine and I'm looking for an FTP server so I can access the files on the machine from anywhere. I would like to be able to type in an IP address to an FTP client and be able to connect to my Ubuntu machine.

Has anyone done something like this before? If at all possible, I would like a GUI. If you have a link to a step-by-step walkthrough, I would greatly appreciate it.

Thanks,
Zach

---

### Post by linux6994 on 2008-07-31
You can run several types of FTP server on your Ubuntu and they run well. I am running pureftp see attached file. The pureadmin will allow you to see who is connected and to clear connections but that is all it is needed for. Users are created via the normal add user method System > Admin > User & Groups.

Things to remember:

1. Ports 21 & 22 are used for ftp, they will need to be open if coming in and through a router. Best to use a static that way the ports will always hit the correct machine.
2. Point users to their desired home directory.

Thats about it, simple. There are several ftp server types available vi Synaptic you just need to choose the one best for you. Its easy to install and remove them so try a bunch.Some give you more control than others.

To test it out load up filezilla and connect to your self.

---

### Post by tamoneya on 2008-07-31
i install vsftpd following this guide: [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html)

Was very straight forward and it worked with no problems.

---

### Post by thevenerablez on 2008-07-31
Thanks for your help! I have a couple more questions...

I would like to be able to access this server from outside my home. Will that be possible? I have a fiber optic internet connection, if that means anything. I install vsftpd, but I don't know how to run it now. The terminal told me that the server was running, so how do I access it via a FTP client?

Thanks,
Zach

---

### Post by tamoneya on 2008-07-31
that isnt very difficult.  Just go into your router and look for the port forwarding section.  You want to forward port 21 (default for ftp, if you changed it you should alter accordingly) from your router to port 21 of your server.  You do this by giving the internal IP address of your server.

---

### Post by thevenerablez on 2008-07-31
Thanks again tamoneya, this seems to make sense. Don't internal IP addresses change though? Does vsftpd account for this or is there something I have to do when I forward port 21 to the Ubuntu machine?

Thanks,
Zach

---

### Post by tamoneya on 2008-07-31
they can change but if in your router you can tell it to always assign the same IP address when it sees the MAC of your server.  The other option is to setup a static IP although I personally find the former to be a little easier.

---

### Post by linux6994 on 2008-07-31
Under firefox there is an ad-on for live ip this will tell you what you liveip when you open the browser. Just keep note of it and use it when acessing from remote places. You can even access it either from the local ip or the remote ip drom home just to test things out. This is recommenced to give you the warm fuzzy feeling before you leave home.

---

### Post by tamoneya on 2008-07-31
> **linux6994 said:**
> Under firefox there is an ad-on for live ip this will tell you what you liveip when you open the browser. Just keep note of it and use it when acessing from remote places. You can even access it either from the local ip or the remote ip drom home just to test things out. This is recommenced to give you the warm fuzzy feeling before you leave home.

Its easier if you use a dynamic DNS service.  Otherwise if you are away and the external IP of your server changes you are still okay.  I use this site: [http://www.dyndns.com/](http://www.dyndns.com/)

---

