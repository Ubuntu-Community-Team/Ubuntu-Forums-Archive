---
title: "setting up a fileserver"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by chumbawumba on 2010-02-01
Hi,

I'd like to set up a simple file server using ubuntu on a dell server (poweredge 840).

I'm fairly new to ubuntu and not particularly confident at using the command line.  I have a windows background.

I have googled this, but only find references to old versions of ubuntu and something called samba.

Does anybody have a step by step guide to installing ubuntu on that server and then how to secure it for file sharing use.

my company has about 30 windows pc's and we would use the server only for file sharing.  each user has their own password and can access parts of the share drive.

I have downloaded the latest ubuntu (not the server version) is it possible to use that version to achieve what i want?  the server version has no GUI (i think?)

Anyway thanks for the help, i look forward to becoming a ubuntu convert !
:)

---

### Post by nhasian on 2010-02-01
Hello chumbawumba,

once you have installed ubuntu on the computer, simply right click on the folder you would like to share and choose "sharing options" the tick the box "share this folder"  Also tick the boxes for "allow others to create and delete files in this folder" and "guest access" so they do not need a username or password. 

thats all there is to it.  simple samba fileserver that windows clients can access.  if you need to restrict folders to particular users, then you need to mess with user permissions and such but it sounds like this is what your looking for.

---

### Post by chumbawumba on 2010-02-01
thanks for the reply.  that sounds very easy!

I do want people to be able to access using a username/pwd, so i won't tick the 'guest access'. does this mean i do need to install samba ?

thanks

---

### Post by hemimaniac on 2010-02-01
I'm not sure how involved you would like to get, but you could fire in ubuntu server

and follow this quick [guide]("http://ubuntuforums.org/archive/index.php/t-318954.html") it is how i set up my first one

---

