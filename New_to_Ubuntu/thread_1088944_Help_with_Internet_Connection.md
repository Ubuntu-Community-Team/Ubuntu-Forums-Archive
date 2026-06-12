---
title: "Help with Internet Connection"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by js@lloyd on 2009-03-06
I have my desktop set up with dual boot.  XP has not problems with the network...Internet works fine. The deskptop is wired to the Modem (2Wire 2700HGV-B2). Modem is fine, as I'm connected wireless with my laptop that I'm on right now. When I boot into 8.10, it says Connection Established under the Network Icon. When I left click on the Network Icon on the top right, the "Auto eth0" is checked, and if I right click, "enable networking" is checked.  Here are a few screen shots.
[IMG]http://i728.photobucket.com/albums/ww284/jsinlloyd/Screenshot3.jpg[/IMG]

[IMG]http://i728.photobucket.com/albums/ww284/jsinlloyd/Screenshot4.jpg[/IMG]

---

### Post by blueridgedog on 2009-03-07
What is the assigned gateway and the dns server you are using?  You can get these with:

```
route
```

and

```
cat /etc/resolv.conf
```

---

