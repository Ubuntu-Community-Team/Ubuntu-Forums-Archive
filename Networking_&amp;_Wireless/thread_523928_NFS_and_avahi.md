---
title: "NFS and avahi"
date: 2007-08-12
forum: Networking &amp; Wireless
---

### Post by lirelent on 2007-08-12
So I have a mixed linux/os X network.  I recently setup a ubuntu 7.04 server fileserver.  Setup NFS just fine and to make things easy for my girlfriend (the os X boxes are hers) I setup avahi and added a static service announcement for the nfs share.  I found that after I boot the server I have to run "sudo tcpdump -i eth0 ip multicast" before it will start responding to avahi requests, but one it responds to a few requests (I just run ping endeavor.local to generate some requests to the server) I can kill tcpdump and it runs fine from then on out.  This is wierd to me, and if anyone has any thoughts on this don't hesitate, but at least avahi works.  Back to my main question, the NFS share via avahi works perfectly for my gf on her os X boxes, she just goes to network in a finder window and the nfs share is there automajically.  My question is some digging around the web makes me thing that it *might* be possible to do the same on my ubuntu 7.04 laptop (go to network in nautulus and see the nfs share, without having to mount it via the command line).  Now on my laptop I can mount the share just fine via command line (so NFS client stuff is working alright).  I can also see the ftp server running my girlfriend's os X desktop and resolve .local hostnames, so the avahi client stuff is working fine.  But I don't see the nfs share under network in nautaulus.  Is there a way to make this happen, or is avahi under linux just not that mature yet?  I found something about nfs:// url support being removed from gnome because of a lack of a maintainer, but it was an old bug report (about a year) and don't know if this was fixed or if it is even related to what I'm trying to do.  Thank you for any help you could render in my quest.

---

### Post by cmdrunix on 2007-10-27
How did you get the NFS share to show up in Finder ? I created a nfs service file but the mac OS X 10.5 doesn't see it.

---

### Post by lirelent on 2007-10-27
> **cmdrunix said:**
> How did you get the NFS share to show up in Finder ? I created a nfs service file but the mac OS X 10.5 doesn't see it.

My service file is /etc/avahi/services/nfs_export.service

<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
<name replace-wildcards="yes">Export</name> ## Name
<service>
       <type>_nfs._tcp</type>
       <port>2049</port>
       <txt-record>path=/media/md0/export</txt-record> ## path to shared Folder
</service>
</service-group>

The howto I followed is [http://gentoo-wiki.com/HOWTO_Serving_Mac#NFS_and_ZeroConf](http://gentoo-wiki.com/HOWTO_Serving_Mac#NFS_and_ZeroConf)

Hope this helps!  	:biggrin:

---

### Post by cmdrunix on 2007-10-27
Thank you !

That is the same one I followed also but nothing shows up in Finder. I just copied yours and restarted avahi. I am running OS X 10.5 so it might be something different now since it just came out yesterday. For now I installed netatalk and added afpovertcp.service to avahi and BAM all the shares show up in the new Finder sidebar- So I guess for now I can use AFP but I think NFS has better performance BUT I have only 1 linux server and many MACS so I guess I am asking myself why not run the Protocol that Most of the boxes run instead of forcing them to use NFS.

BC

---

### Post by lirelent on 2007-10-27
yea the macs on my network are all running 10.4 and once I got avahi working they all saw the nfs share without any problem.  It's disappointing to hear that 10.5 may break that.

---

### Post by cmdrunix on 2007-10-27
Well It seems that only AFP and SMB shares get displayed in the new finder sidebar. Sine when I create the afp.service file the AFP shares pop right up in finder but nothing shows up with nfs.service :-( I'll keep playing with it as the days go on but for now at least I can access my file server.

BC

---

### Post by shaneperc on 2008-01-04
Someone has posted a Ruby script as a quick fix. I haven't tried it yet, but here's the link

[http://svwtech.com/site/]("http://svwtech.com/site/")

---

### Post by Yfrwlf on 2008-01-04
I don't mean to drag this off-topic, but why would you choose NFS over Samba, what are the good and bad points of each?  Samba file sharing works out of the box in Ubuntu and broadcasts the shares, so it's use would be a solution to your problem right?  Samba is capable of user-based security as well, so I think it's pretty secure too.  You can also mount SMB shares, so that *any* Linux program or service can access them, as far as I know, so I'm just curious as to why you want to use NFS over it.

Anyone know the advantages and disadvantages of NFS vs. SMB?  Aaah, gotta love freedom of choice. ;)

It would be nice seeing NFS shares being broadcast by default though in Ubuntu, or at least be given the option to do so.

---

### Post by jeffus_il on 2008-01-04
I find the easiest solution to file sharing on Linux systems is using sftp and and nautilus as a client, no setup required. Maybe the KDE file manager does the same. There is also an open source client for windows.

---

