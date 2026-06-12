---
title: "Simple Ubunutu Network ?"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by celticbhoy on 2008-03-22
Just looking for a quick how-to to setup a simple wireless newwork between a Ubuntu Gutsyu machine & a Xubuntu Fiesty laptop.

Wireless works on both machines to connect to internet through hub.

I know this must have been covered a thousand times but there are a million posts covering networks, and I am not sure what one is right for me.

Thanx in advance.

---

### Post by Eiríkr on 2008-03-22
Depends on what you want it for, how much convenience you need, how technically adept and / or daring you are, etc. etc...

Given that one of your machines is Xubuntu, and given that Thunar is *only* a file browser and does not have the ability to browse Samba, NFS, or SFTP shares directly, you're going to have to either mount any shares onto your Xubuntu machine's filesystem, or install Nautilus or Konqueror on your laptop.  

Samba is one of the most widely used sharing apps in Ubuntu land, but it's also designed primarily for Lin -> Win sharing, and thus has *lots* of options specific to Windows that can get in the way of any Lin -> Lin sharing setup.  You'd have to mount the shares to your Xubuntu machine like so before browsing with Thunar:
```
sudo mount -t cifs -o username=USERNAME,password=PASSWORD,rw //SERVER/SHARE /MOUNTPOINT
```
One good start that discusses filesystem permissions setup as well is [post=4496702]this post[/post].  You can find much more about Samba configurations here on the boards just by searching.

NFS is one of the oldest Unixy filesharing setups, first developed by Sun and IBM back in 1984, but still maintained and still current, and still useful.  (Good Wikipedia article [here](http://en.wikipedia.org/wiki/Network_File_System_%28protocol%29).)  It has a number of complexities of its own, such as requiring that server and client user and group IDs (the numeric ones, *not* the text labels we're used to seeing) either match on both machines, or are mapped.  Otherwise you get all kinds of weird permissions behaviour.  Again, you'd have to mount before browsing in Thunar:
```
sudo mount -t nfs -o w SERVER:/SHARE /MOUNTPOINT
```
I wrote an NFS setup HOWTO a while back for Lin -> Mac sharing, but most of it is still applicable for Lin -> Lin networking.  Have a look [post=4387032]here[/post].  Again, searching on the boards will find you much more.

SFTP is simply FTP via SSH.  It's probably the simplest setup, requiring zero configuration and no mounting, but it would also require you to install another browser on your laptop given Thunar's simplicity.  To use SFTP, just install the [font=courier]ssh[/font] package on both machines.  Then in Konqueror or Nautilus, type [font=courier]sftp://IP.ADD.RE.SS[/font] in the location bar, replacing the caps with the IP address of the other machine.  

Hope this gets you started!

Cheers,

Eiríkr

---

### Post by Sam Lars on 2008-03-22
You just want file sharing?  I've found that NFS works great.  You can configure that through the Shared Folders utility.
I see I got beaten to it.

---

