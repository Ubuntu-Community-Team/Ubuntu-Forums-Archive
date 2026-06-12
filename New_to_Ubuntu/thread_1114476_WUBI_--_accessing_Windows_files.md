---
title: "WUBI -- accessing Windows files"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by brandoncolorado on 2009-04-02
Hi,

We just installed WUBI on my roommate's computer.  In Ubuntu we can see the system partition that HP uses, but we cannot see the regular Windows files.  On my computer with Ubuntu on its own partition, I can see my windows files by default.

Should I have to mount that separately, or am I missing something?

Thanks

---

### Post by HermanAB on 2009-04-02
The absolutely easiest way to share files is with good old FTP.  So on Windows install FileZilla server and client.  On Linux, install Proftpd and use the regular Nautilus file browser as the client.

The second easiest method is to install Windows Services for Unix (NFS) on Windows (a free download from Microsoft.  NFS requires two lines of configuration - one on the server and one line on the client.

The third method which is two orders of magnitude more problematic than the above two is to use Samba (Windows networking) with Linux.  Samba requires hundreds of lines of configuration and the Linux wizards suck.

---

