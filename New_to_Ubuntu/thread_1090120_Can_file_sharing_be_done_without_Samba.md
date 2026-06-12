---
title: "Can file sharing be done without Samba"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by ubuntu1sttimer on 2009-03-07
Have been trying to move to Linux and Ubuntu for several years. One of the main things I need is the ability to share files with other machines including Windows 98, 2000, and XP. 

I know it can be done with Samba as I got it working on Dapper once. But then Dapper trashed it's self and I have been trying now for over two years to get Samba to work again. An indication of just how bad it is, there is one post on these forums with over 700 replies on how to make Samba work. Mark Shuttleworth has even stated that something is needed.

Simply put, I am sick and tired of fighting Samba when I can do the same thing with a few key strokes in Windows. It is like, why am I doing this to myself? Why don't I just use Windows?

I am not interested in spending any more time on trying to make Samba work, just want to find a better way to share files. Does it exist?

---

### Post by estamand on 2009-03-07
You could use Filezilla to do a SFTP connection.  It's a file transfer over the ssh protocol.

---

### Post by arsmith on 2009-03-07
Try NFS.

---

### Post by T.J. on 2009-03-07
If you are looking for drag and drop file sharing - and are certain you don't want to deal with Samba, I'd install ssh on the Linux machine, and then use WinSCP on the Windows machine. You won't have automatic network detection, but if you use IP address of the Linux machine the files will transfer quickly and easily.

I'm surprised you are having problems with Samba.  Normally, it's really easy to setup as long as you remember three caveats:

1) Make sure that all of your LAN IP addresses are on the same subnet (e.g. 192.168.1.x).  Windows fileshares don't work well otherwise. Not a bug in Samba - that's Windows.
2) Make sure that all machines have the same Network Neighborhood name - another Windows quirk.
3) Make sure that your Samba setup has the shares listed in the samba files and that Samba can read those folders on the Linux box.

---

### Post by ubuntu1sttimer on 2009-03-13
:popcorn: Thanks all. Unfortunately work took me away form these keys for a few days. Want to thank all of you for your ideas. I used them and a couple others that I ran across and got Samba working to share files between Ubuntu and WIN98. Still have the others to get going but at least, after all this time, I have made progress.

---

### Post by CREEPING DEATH on 2009-03-14
Samba is easy on the newer versions of Ubuntu *BUT* you *MUST* reboot after you install it to set it up.  Setting permissions is as easy as Windows though.

CD

---

### Post by HermanAB on 2009-03-14
Microsoft Services for Unix (NFS) is a free download 
[http://www.microsoft.com/DownLoads/details.aspx?familyid=896C9688-601B-44F1-81A4-02878FF11778&displaylang=en](http://www.microsoft.com/DownLoads/details.aspx?familyid=896C9688-601B-44F1-81A4-02878FF11778&displaylang=en)

Another easy way to share files on a LAN with good old FTP.  
[http://filezilla-project.org/](http://filezilla-project.org/)

Cheers,

Herman

---

