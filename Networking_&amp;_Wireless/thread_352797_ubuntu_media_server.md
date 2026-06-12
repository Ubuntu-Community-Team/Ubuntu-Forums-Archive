---
title: "ubuntu media server"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by Loki57701 on 2007-02-03
Currently I have a home media server running winXP pro, a simple system volume share along with some USB drives on my local network of 4 computers. Ive already got ubuntu installed on 1 of my laptops (for the last 6 months or so). And I am interested in using ubuntu as my servers OS. My primary concerns are:

1. Remote desktop connection. Is there remote desktop connection software similar to the one MS uses, for linux. I really depend on the ability to log into my server from a different computer, because I dont have alot of extra monitors laying around. I suppose I could buy a KVM switch though.

2. I havent really looked into SAMBA that much but it seems like thats what I would need to do the same thing im doing now for sharing drives over my network. Its looks pretty complicated, and although im willing to try using it in the command line is there a better way to use it preferably with a gui of some sort (i know i know, all u noob haters out there can have something to rant on now)

3. Do I have to use the server version of Ubuntu or can i install the desktop version and download all the SAMBA stuff.

---

### Post by jinx099 on 2007-02-03
1) VNC is the linux standard of remote desktop.  Although you may have to tweak it because Ubuntu's VNC server is kinda sketchy, unlike most other distros I've tried.  Also, theres SSH ;)

2)  If you are sharing with Windows, Samba is what you want.  If you are sharing files with another linux box, NFS is faster and a lot easier to set up.  But Samba is not that hard, just read the Ubuntu wiki on it.

3) It sounds like you actually would want to stay away from the server version because by default, there is no window manager.  The desktop version will work fine.

If you're scared of setting up server stuff via .conf files and CLI, you may want to try openSUSE.  It comes with YAST which is a great GUI tool to set up that stuff.

---

### Post by IcarusR on 2007-02-04
SAMBA can be administered via SWAT a web based amin tool

---

