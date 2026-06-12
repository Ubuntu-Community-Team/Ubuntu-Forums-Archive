---
title: "Read-only file issue"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by grantmj on 2009-09-11
Hi All--

New to Ubuntu, and love it...except for 1 problem.  I have jaunty jackalope on a computer being used as a file server with a large # of windows machines accessing the data.  My problem is that I can't seem to change the server files that they access from being read only.

@ one of the windows machines I can right click and change them to not be read only, but when I exit out of the window and go back, the read only check box is colored in again.  When I try this on the ubuntu computer it says that I'm not the owner and that I can't change the permissions.  I have a lot of people who can't edit previous work because any changes to the file and it says it's read only. I know this is a permissions issue and I've looked at it forever and I just seem to not be able to figure it out.  I thought this forum might have seen this before.  Help!  Thanks!:KS

---

### Post by Liolikas on 2009-09-11
Command line based tutorial:
[http://catcode.com/teachmod/](http://catcode.com/teachmod/)
[http://www.hscripts.com/tutorials/linux-commands/chown.html](http://www.hscripts.com/tutorials/linux-commands/chown.html)
If you do not have permission to enter command just provide sudo in front of it:
like:
sudo chown ... ...
---
Also consider **pure-ftpd** as alternative to windows file sharing solution. It is much easier to manage just install it, add to startup and users can login into ftp (even with IE or other capable ftp software like filezilla) with their Ubuntu login name/password to their files.

---

### Post by philinux on 2009-09-11
Have you shared the ubuntu folder where the data is stored and ticked the box to allow write access?

---

