---
title: "Windows Shares With Samba Setup"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by cdenk on 2008-01-21
I have 2 computers networked together via a ADSL ROUTER, one with XP Pro, the other with XP Home using the typical MSHOME workgroup. When both are in Windows, all I have to do is in the remote computer, set the drive up for sharing, and full read/write priviledges are available shortly after granting.

Setting up Samba shares with Fiesty Kubuntu now on the XP Home computer, and will get to the XP Pro after getting one working well. Following the [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534), Reload this Page 
 Mount samba shares with utf8 encoding using cifs
I'd like to have the same flexibility of just giving the permission at the remote end once, and I guess that means if Kubuntu is running on both maachines also
I have edited /etc/fstab to include the following
//netbiosname/sharename    /media/sharename        cifs    guest,rw,iocharset=utf8,file_mode=0777 0 0

I do not use passwords on the Windows side. Do I need to create a /root/.smbcredentials file ?

when I do: sudo mount -a     I get the error: 
carl@COMPAQ:~$ sudo mount -a
mount error 111 = Connection refused
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

Where for next? I'm a newbie to Ubuntu. :)
Is there a way to just give the remote computer one share that covers all the drives, includinf CD's etc.?

Thanking in advance :)

---

