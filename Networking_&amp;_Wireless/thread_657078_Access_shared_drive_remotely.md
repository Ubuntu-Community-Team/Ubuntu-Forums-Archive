---
title: "Access shared drive remotely"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by PhatBob55 on 2008-01-03
Hi

I can sucessfully access my shared drive from other machines on my network, XP, XBMC etc, but I would like to be able to access it remotely across the internet, i.e. from work?

Is there a way to do this, or is it simply a case of forwarding the correct port (which is) on the router to the linux box?

Bob

---

### Post by Predator[23rd] on 2008-01-03
Hi!

I believe you have to do some port forwarding.

If you only need FTP access put a ftp/ssh server to work on your machine and forward port 22 to it. You can use a SFTP (filezilla is a nice one) or SSH (putty rulz) client to connect and upload/download files...

---

### Post by PhatBob55 on 2008-01-03
Hi Predator

I can already ftp and ssh into my box remotely, but I just wanted to add it as a drive on my xp machine at work.

---

### Post by Predator[23rd] on 2008-01-03
I have no clue if it will work or not but try to forward SMB ports and see if you can connect to your box like to any other network computer smb;//<your-router-ip-address>.

good luck!

---

### Post by jetsam on 2008-01-03
I think opening the Samba ports to the net could be made to work, but it isn't recommended for security reasons to expose Samba or Windows networking directly to the internet.

This is something I've been wanting to look into myself, so I don't have a lot of details to offer, but I think you need to set up VPN.   

Here's a forum post from a web hosting forum which explains the big picture and gives a few packages to look into:
[http://www.linode.com/forums/viewtopic.php?t=818&highlight=samba]("http://www.linode.com/forums/viewtopic.php?t=818&highlight=samba")

---

