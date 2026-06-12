---
title: "transfering files to other computers that are not yours"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by bigdee973 on 2008-08-30
hello, i have a question regarding transfering files via ubuntu.. i know how to transfer files via ssh, connecting to server, scp, and such but those require you to know the passwords of the other persons computer, now me and my friend would love to share files between each other but we want to keep our passwords secret. is there any protocols that would let u transfer files to each others computer without having to know  each others password? maybe like giving him a prompt to accept file?  we use pidgin but it fails most of the time.  im hoping there is an open source linux program for terminal or even a gui. does anyone know anything about this matter?

---

### Post by pytheas22 on 2008-08-30
One option I guess would be to run an Apache server on each machine and write a script allowing users to anonymously upload files through a web interface.

But why don't you just create additional accounts for each other and use them for ssh?  It would be a lot more secure, and no one would have to know the password of the main account of the other person.  The Apache approach is more of a security risk and would require a lot more work to get set up.

---

### Post by bigdee973 on 2008-08-30
> **pytheas22 said:**
> One option I guess would be to run an Apache server on each machine and write a script allowing users to anonymously upload files through a web interface.

But why don't you just create additional accounts for each other and use them for ssh?  It would be a lot more secure, and no one would have to know the password of the main account of the other person.  The Apache approach is more of a security risk and would require a lot more work to get set up.

ur right thats extactly what i was thinking of doing but i thought there was already a script or program available to do this but yeah i guess ill just take the appreach of creaing new users

---

### Post by .nedberg on 2008-08-30
I'd rather use ftp than http.

I have a server with vsftpd running, virtual users with only read rights. I give my friends the username and password when ever they want something from me. If I want something from them I also have a user with write access, but not read (ie can't see any files or dl anything).

That setup might not fit your case, but vsftpd can be configured as you like. ProFTPd is another option, and I think it has a GUI to configure it if you want that.

SFTP is way better though, but you would have to make extra users.

---

