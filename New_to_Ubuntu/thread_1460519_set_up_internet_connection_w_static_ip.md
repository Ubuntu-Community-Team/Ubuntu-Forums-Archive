---
title: "set up internet connection w/ static ip"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by mvalviar on 2010-04-22
I was able to set it up by editing /etc/network/interfaces. Is there a way to do this through a GUI? I was given my ip address, subnet mask, default gateway and dns server by my provider. I was able to set it up in xp through a gui.

---

### Post by unmole on 2010-04-22
1) Right click on the Network Manager Applet and go to edit connections.
2) Select your network and hit edit.
3) Go to the IPv4 settings and change the method to Manual
4) Enter the values provided by your service provider.
5) That should do it.

---

### Post by 2hot6ft2 on 2010-04-22
> **unmole said:**
> 1) Right click on the Network Manager Applet and go to edit connections.
2) Select your network and hit edit.
3) Go to the IPv4 settings and change the method to Manual
4) Enter the values provided by your service provider.
5) That should do it.
And don't forget to remove all but the first 2 lines in the /etc/network/interfaces file before you reboot once you set it up it that way.

---

