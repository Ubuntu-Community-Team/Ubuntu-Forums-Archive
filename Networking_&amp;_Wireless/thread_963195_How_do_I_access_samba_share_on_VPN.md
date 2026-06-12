---
title: "How do I access samba share on VPN?"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by muramura on 2008-10-30
Hello all!

I have a Ubuntu server (latest version) at a remote location on another network, and can connect from home with SSH perfectly.  Now I want to setup a mapped network drive to access that server’s files from Windows XP Pro.  I've assumed a combination of VPN and Samba is the way to go, but am having trouble.

I created a VPN using pptpd, configured correctly (I hope), and was able to connect from my Windows PC successfully.  Next, I setup a Samba share, with "hosts allow = (MyIP) 192.168.0.1", in hopes that would allow me to connect via VPN.  (That second IP is what I configured the VPN to assign me when I connect.)  I’ve successfully setup Samba before when on the same network, so lets assume those basic settings are correct. What am I missing to allow Samba access via VPN?  Or am I way off base here?

Thanks in advance

---

### Post by dmizer on 2008-10-30
I don't know anything about pptpd, but it looks really intersting. I'm planning to check it out later as I've been looking for a solution that's not as complicated as openvpn.

According to Poptop, you need a RADIUS plugin in order to access SAMBA shares: [http://poptop.sourceforge.net/dox/radius_mysql.html](http://poptop.sourceforge.net/dox/radius_mysql.html)

---

### Post by muramura on 2008-10-30
Yikes - I'm cross-eyed already!  Maybe this isn't easier than OpenVPN afterall.  Does that support what I'm trying to do?

Does anyone know an easier way to access remote linux files via Windows Explorer?

---

### Post by dmizer on 2008-10-30
VPN is easy.

Accessing Windows shares over VPN is not so easy.

Perhaps you could try configuring your Windows computer to use FTP instead? Take a look at this howto: [http://ubuntuforums.org/showthread.php?t=218630](http://ubuntuforums.org/showthread.php?t=218630)

---

### Post by muramura on 2008-10-30
I really don't want FTP.  I'd like the share, so I can open files and save them directly to the server.  Plus FTP is insecure (sure you can secure it, but while I'm at it, why not do VPN with Samba).

So again... anyone... how can I get Samba and VPN to work together?  Anyone?  Have I really stumped the entire Ubuntu community yet again?

:cry:

---

### Post by dmizer on 2008-10-31
Sorry, I meant: If you access your network over VPN, and then access your local shares with FTP instead of SAMBA, you shouldn't run into this problem. So, do what you're trying to do, but replace "samba" with "ftp". FTP shouldn't have the same cross platform problems over VPN as SAMBA.

I'm not suggesting that you access your shares from remote by FTP. That's scary. :)

---

