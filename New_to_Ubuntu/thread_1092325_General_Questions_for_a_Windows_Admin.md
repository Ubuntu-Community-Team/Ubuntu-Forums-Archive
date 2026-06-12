---
title: "General Questions for a Windows Admin"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by Ravenhon on 2009-03-10
I am a Windows environment administrator for a web hosting company. I have verified that I can connect to our VPN from a Linux box. The only other question that I really have relates to Windows RDP. On Windows, I can get a manager that will allow me to store multiple RDP connections in a GUI. It stores my credentials as well as the connections. I would like to find something similar for Ubuntu. Does anyone know of such a thing? I have searched around Google for a while. I am fairly confident of my Google-fu.

---

### Post by Peter09 on 2009-03-10
I may be wrong here, but I think the 'connect to server applet' - which may be on your panel already, or can be added with a right click --add applet - will do what you want and includes RDP.

This is from memory as I am at work at the moment, so I may be wrong. There are quiet a few terminal clients in the repositories that will do it.

Thinks - also try the places menu, connect to server, which may also do it.

---

### Post by Ravenhon on 2009-03-10
Hey thanks a million. I've really been wanting to switch my home machine over to Linux for a while now. Linux is SO ready for prime time now that I can't resist the urge to switch. The only thing really holding me back is that I work for an all MS shop. That means that my VPN connection needs to work (spoke to security admin and it will) and the RDP thing. Thanks a lot!!

---

### Post by BDNiner on 2009-03-10
You can click on internet->Terminal Server Client. That client allows you to store connections.

---

### Post by CAPLinux on 2009-03-10
> **Ravenhon said:**
> Hey thanks a million. I've really been wanting to switch my home machine over to Linux for a while now. Linux is SO ready for prime time now that I can't resist the urge to switch. The only thing really holding me back is that I work for an all MS shop. That means that my VPN connection needs to work (spoke to security admin and it will) and the RDP thing. Thanks a lot!!

Ravenhon,  There is an open source RDP software for Linux called rdesktop, at the last company I worked for I used this software to remote into my work PC from Home.  It works just like Remote Desktop Connection does on Windows.

Here is the command Line to install RDesktop.

apt-get install rdesktop

---

### Post by Peter09 on 2009-03-10
Great,
it took me a while to realise how hugely 'connected' - sorry for the english- Linux is - machines can be made to interact in an amazing number of ways, from things like RDP which logs on to an existing descktop, to ssh and nxfree which allow you to truly log on multiuser, to sshd which allow folders on one machine to 'appear' on another --- great fun.

---

### Post by Ravenhon on 2009-03-10
I do have rdesktop installed. The features I am looking for would be like mRemote or VisionApp Remote Desktop.

---

### Post by Ravenhon on 2009-03-10
Thanks!! That's awesome! It never ceases to amaze me how open and helpful the Ubuntu community is. You guys really know how to welcome someone!

---

