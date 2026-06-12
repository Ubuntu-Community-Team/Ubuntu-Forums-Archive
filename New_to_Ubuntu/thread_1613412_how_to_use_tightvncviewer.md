---
title: "how to use tightvncviewer"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by Willye on 2010-11-04
Hi folks, i have installed tightvncserver and tightvncviewer in ubuntu and windows, i been able to connect from windows to linux fine, but from linux to windows does not work, appears (connection closed), i have ubuntu 10.04 and running (remote desktop viewer) and trying to connect to windows xp, thanks for your comments

---

### Post by MartyBuntu on 2010-11-04
Is there a firewall on the Windows side?

---

### Post by Zzl1xndd on 2010-11-04
Do you have a VNC server program installed on the Windows PC, or just the viewer? 

Ubuntu has a VNC server installed by default and Windows doesn't.

If you do have a VNC server installed on Windows the issue maybe Firewall related. 

Also for this kind of thing I am a Big fan of Teamviewer. Easy to set, will work through Firewalls/Routers without config and cross platform.

[http://www.teamviewer.com/index.aspx](http://www.teamviewer.com/index.aspx)

---

### Post by marshall1001 on 2010-11-05
Is it xtightvncviewer in Ubuntu? That's what I used to use. If not then open a terminal and

```
sudo apt-get install xtightvncviewer
```

This will install xtight. Then find out the IP of the Windows machine on the network. Open another terminal and type

```
xtightvncviewer 192.168.1.65
```

Please ensure you substitute the IP given here for the actual IP of the machine. If the VNC server is password protected it will ask you for it.

I used to use this for going into both OS X and Windows machines so it should work fine.

---

