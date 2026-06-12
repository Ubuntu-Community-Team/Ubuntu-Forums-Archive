---
title: "How to Connect Xubuntu, Kubuntu, &amp; Win XP"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by LaneLester on 2007-12-21
I have a LAN at home, and the three machines are Xubuntu ( my main machine, Gutsy <> Hardy), Kubuntu (wife's), and Win XP (for when it can't be avoided).

How do you recommend that I share files between these three machines? I would like to be able to both download and upload from the others to my Xubuntu.

I thought Samba might provide the mechanism for all three. I have good sharing between Xubuntu and Win XP, but for some reason my Xubuntu is not seeing the Kubuntu, even though both have the same workgroup name in their smb.conf's.

Both pyNeighborhood and xSMBrowser on Xubuntu fail to see Kubuntu, even though findsmb on Xubuntu says this:

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.20    GL1           +[SIMBIOSYS] [Unix] [Samba 3.0.24]
192.168.1.121   PC1           +[SIMBIOSYS] [Unix] [Samba 3.0.28]

GL1 is the Kubuntu, and PC1 is the Xubuntu.

Lane

---

### Post by HermanAB on 2007-12-21
Samba is the most difficult way to do it:  [http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

FTP is the easiest: [http://filezilla-project.org/](http://filezilla-project.org/)

NFS is the one I would recommend: [http://support.microsoft.com/kb/324055](http://support.microsoft.com/kb/324055)

Cheers,

Herman

---

### Post by LaneLester on 2007-12-22
Thanks, Herman, for the thorough reply.

> **HermanAB said:**
> Samba is the most difficult way to do it:  [http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

'Nuff said; I'm forgetting that one.

> FTP is the easiest: [http://filezilla-project.org/](http://filezilla-project.org/)

Easy is good. Thanks for the FileZilla link; I see it provides the Windows server. It looks like proftpd is the way to go for Linux.

> NFS is the one I would recommend: [http://support.microsoft.com/kb/324055](http://support.microsoft.com/kb/324055)

Hmm. Well, if FTP (with which I'm comfortable for Internet access) doesn't work out, I'll investigate NFS (about which I know nothing). :)

Lane

---

### Post by LaneLester on 2007-12-22
Well, the setup with FileZilla as the server on the Win XP machine was easy and successful, and I can now FTP to it from my main Xubuntu machine. As is so often the case with me, the same step in Linux was not so successful. :(

I installed proftpd and gproftpd on the Kubuntu machine, and I configured it as well as I could. I set the upload/download directory (the same one) in both the server setup and the user setup. However, when I FTP to the Kubuntu machine from the Xubuntu, although I log on successfully, I get this error: 550 PWD: Permission denied 

The permissions of the up/down directory are 666.

How can I get permission to access the up/down directory?

Lane

---

### Post by sreenath on 2008-02-12
I've set up nfs sharing on my ubuntu 7.10 desktop, and i'd like to connect from my xubuntu laptop. Could give me the command to mount an nfs share on 192.168.1.2:/media/OneTouch4 on xubuntu?
I've tried 'mount.nfs 192.168.1.2:/media/OneTouch4' and 'mount -t nfs 192.168.1.2:/media/OneTouch4', but both did not work.

---

### Post by ender8282 on 2008-02-12
> **sreenath said:**
> I've set up nfs sharing on my ubuntu 7.10 desktop, and i'd like to connect from my xubuntu laptop. Could give me the command to mount an nfs share on 192.168.1.2:/media/OneTouch4 on xubuntu?
I've tried 'mount.nfs 192.168.1.2:/media/OneTouch4' and 'mount -t nfs 192.168.1.2:/media/OneTouch4', but both did not work.

Did you get an error message?

---

