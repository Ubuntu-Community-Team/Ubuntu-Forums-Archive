---
title: "Remote Desktop to 14.04 from Windows"
date: 2014-05-23
forum: Networking &amp; Wireless
---

### Post by Jonathan_Portwood on 2014-05-23
Hello,
I'm pretty new to the Linux world. Have dabbled a little in the past, but always ended up stumped with some problem or other, that I couldn't sort out.

I'm trying again with Ubuntu 14.04 LTS on a Dell Dimension 5100 desktop. I've installed the 64-bit version as I have 4 Gb RAM in the system and I also have a nVidia GeForce 210 graphics adaptor. 

Having got Ubuntu installed and updated as of today, I am now trying to connect to the Ubuntu system via VNC from my Windows 8.1 desktop. I've enabled the Gnome Desktop Sharing applet (v3.8.1) an have made sure the VNC ports are open in the firewall in Ubuntu. But when I try to connect using the IP address for the Ubuntu system, RealVNC Viewer gives the following error;
'Unable to connect to the VNC Server at address <IP Address> using your chosen security setting. Either upgrade the VNC Server to a more recent version, from RealVNC or select a weaker level of encryption.'

I have set encryption in the Viewer settings to 'Prefer Off' which is the weakest level available, but I still get this issue. I've tried the connection with two different versions of the RealVNC Viewer (v5.1.1 which is the latest version, and v4.1.3). Both give basically the same error message.

Can anyone please point me in the right direction for getting this to work? I remember using the RealVNC Viewer progam to connect to previous versions of Ubuntu, so I'm puzzled as to why this isn't working anymore.

Thanks in advance for your advice and suggestions.

Yours faithfully,

Jonathan R. Portwood.
PS.
I am an IT Consultant, working almost exclusively in the Windows world. So I consider myself pretty knowledgeble generally about computing and the various issues involved. It's just that I'm relitively new to the Linux world.:)
JRP.

---

### Post by bill-wz6b3 on 2014-07-12
Getting the same message and same issue.  Worked fine 13.10 before I did a clean install to 14.04, now I'm stumped as to where the issue might be - encouraged to see others are experiencing the same issue.

> **Jonathan_Portwood said:**
> Hello,
I'm pretty new to the Linux world. Have dabbled a little in the past, but always ended up stumped with some problem or other, that I couldn't sort out.

I'm trying again with Ubuntu 14.04 LTS on a Dell Dimension 5100 desktop. I've installed the 64-bit version as I have 4 Gb RAM in the system and I also have a nVidia GeForce 210 graphics adaptor. 

Having got Ubuntu installed and updated as of today, I am now trying to connect to the Ubuntu system via VNC from my Windows 8.1 desktop. I've enabled the Gnome Desktop Sharing applet (v3.8.1) an have made sure the VNC ports are open in the firewall in Ubuntu. But when I try to connect using the IP address for the Ubuntu system, RealVNC Viewer gives the following error;
'Unable to connect to the VNC Server at address <IP Address> using your chosen security setting. Either upgrade the VNC Server to a more recent version, from RealVNC or select a weaker level of encryption.'

I have set encryption in the Viewer settings to 'Prefer Off' which is the weakest level available, but I still get this issue. I've tried the connection with two different versions of the RealVNC Viewer (v5.1.1 which is the latest version, and v4.1.3). Both give basically the same error message.

Can anyone please point me in the right direction for getting this to work? I remember using the RealVNC Viewer progam to connect to previous versions of Ubuntu, so I'm puzzled as to why this isn't working anymore.

Thanks in advance for your advice and suggestions.

Yours faithfully,

Jonathan R. Portwood.
PS.
I am an IT Consultant, working almost exclusively in the Windows world. So I consider myself pretty knowledgeble generally about computing and the various issues involved. It's just that I'm relitively new to the Linux world.:)
JRP.

---

### Post by steeldriver on 2014-07-12
possibly the same issue as here --> [http://ubuntuforums.org/showthread.php?t=2233675&p=13070891&highlight=Vino#post13070891](http://ubuntuforums.org/showthread.php?t=2233675&p=13070891&highlight=Vino#post13070891)

---

### Post by Ben_Cunningham on 2014-07-13
Just use TeamViewer. That's what I use and it works great. And of course if you just want terminal you can use SSH

---

