---
title: "FTP Xubuntu &amp; XP"
date: 2006-12-02
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2006-12-02
I'd like to access files on a Windows XP machine, from a Xubuntu machine.

Can I easily use FireFTP from within Firefox on the Xubuntu machine(client) to reach the Windows XP machine(server)? 

I use wireless on both machines, of course, with a router.

Do I have to use FireFTP on the Windows machine & what would I have to enter on each to get the connection?


Could I network both machines directly, with only an ethernet cable?

Thanks

---

### Post by taurus on 2006-12-02
If both machines connect to the same router, then you can set up samba and mount your XP on Ubuntu.  No need to run any ftp server...

---

### Post by FrodoB on 2006-12-02
If you really just want to use FTP then see:

[B][http://www.warftp.org/](http://www.warftp.org/)

[/B]It is a very good free FTP server for Windows.

---

### Post by DapperMe17 on 2006-12-02
Thanks!

As a newbie, I was under the impression that running FTP was easier than utilizing Samba.

Please, correct me if I'm wrong.

---

### Post by FrodoB on 2006-12-02
Well Samba will implement Windows style networking. 

If you are used to ftp it is simpler, though scp which is a part of the ssh toolset is more secure. If you are behind a firewall it should not matter to you.

Windows does not have a free built-in ftp server, so that is why you would need ftp.

Also note that Ubuntu does not come with an ftp server implemented for security reasons.

---

### Post by DapperMe17 on 2006-12-02
Thanks,

I have FireFTP thru Firefox, on the Ubuntu machine.

What would I need to set up on the Windows machine, in order to access it's files?

---

### Post by FrodoB on 2006-12-02
In the third post in this thread I give a link to the WarFTP server. Install and configure that on XP and then you can access its files from Ubuntu.

---

### Post by DapperMe17 on 2006-12-02
Thanks much!

---

