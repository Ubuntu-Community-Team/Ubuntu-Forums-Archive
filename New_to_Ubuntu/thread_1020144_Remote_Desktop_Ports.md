---
title: "Remote Desktop Ports?"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by jdpearson on 2008-12-23
I'm attempting to configure Ubuntu's Remote Desktop for external access to my computer.  It appears to be a version of VNC - which I use all the time in the Windoze world.  I have forwarded port 5900 in my router yet I cannot connect from my office computer.  

At the office I'm using Ultra VNC, which has never given me any grief before.

I'm wondering if I'm missing something on the Ubuntu side (since I'm a Linux n00b).

Thanks

---

### Post by bodhi.zazen on 2008-12-23
So you are trying to connect to Ubuntu from Windows ?

Port 5900 should be correct, but this is not overly secure. I suggest you VNC over SSH or look into FreeNX.

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

In terms of connection there could be any number of problems. How are you trying to connect ? Are you using your public IP address ? Firewall ?

---

### Post by jdpearson on 2008-12-24
> **bodhi.zazen said:**
> So you are trying to connect to Ubuntu from Windows ?

Port 5900 should be correct, but this is not overly secure. I suggest you VNC over SSH or look into FreeNX.

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

In terms of connection there could be any number of problems. How are you trying to connect ? Are you using your public IP address ? Firewall ?


At first I thought I had a boneheaded mistake, but that should be resolved.  I am connecting remotely.  I have a Dynamic IP but I know what it is currently and also have been using services like dyndns.org.  I CAN connect internally from my XP box so I know that it's working.  My router seems configured correctly, just changed the port from Windows RDP to 5900.  Rebooted the router. 

Any default firewall in Ubuntu I should look at?  Although that would typically block access from my internal network as well.

---

### Post by halitech on 2008-12-24
maybe check here [http://portforward.com/routers.htm](http://portforward.com/routers.htm) to make sure the router is setup correctly. If I remember right, you need ports 5900 and 5800 open in order to have vnc work correctly

---

### Post by deputy on 2008-12-24
I had problems also using Ubuntu's Remote Desktop feature with my pc behind a router so I ended up setting up my own VNC server using this [guide]("https://help.ubuntu.com/community/VNC?action=show&redirect=VNCOverSSH"). I used tightvncserver btw.

---

### Post by jdpearson on 2008-12-24
> **halitech said:**
> maybe check here [http://portforward.com/routers.htm](http://portforward.com/routers.htm) to make sure the router is setup correctly. If I remember right, you need ports 5900 and 5800 open in order to have vnc work correctly

I'm almost certain that 5800 is used only for the Java viewer, but I'll double-check.

---

### Post by halitech on 2008-12-24
you could be right, been a while since I've used it and not currently setup on this system

---

### Post by deputy on 2008-12-24
Are you getting errors or does the connection time out?

---

### Post by generic_idea_machine on 2008-12-24
Have you tried accessing the host from your local subnet? And if so does it work?

It might be worthwhile to check the various settings under "Remote Desktop Preferences" (system ---> Preferences)

---

### Post by jdpearson on 2008-12-24
> **deputy said:**
> Are you getting errors or does the connection time out?

Just fails to connect to server.  Basically a time out I think.

---

### Post by jdpearson on 2008-12-24
> **generic_idea_machine said:**
> Have you tried accessing the host from your local subnet? And if so does it work?

It might be worthwhile to check the various settings under "Remote Desktop Preferences" (system ---> Preferences)

Yeah, as I mentioned it works great internally.  Just not from the outside world yet.

---

### Post by halitech on 2008-12-24
since it works inside your lan, I'm thinking its more of a router issue not being setup correctly.

---

### Post by generic_idea_machine on 2008-12-24
> **jdpearson said:**
> Yeah, as I mentioned it works great internally.  Just not from the outside world yet.

Did you check the "Advanced" tab under the remote desktop preferences?
There is an option there to only allow "connections from local subnet". Make sure it is **un-checked**

---

### Post by generic_idea_machine on 2008-12-24
> **halitech said:**
> since it works inside your lan, I'm thinking its more of a router issue not being setup correctly.

I was thinking along the same lines. Most probably the i.p for the machine has changed..but the router port fwding config have not been updated. static i.p should fix that.

---

### Post by bodhi.zazen on 2008-12-24
The default port is 5900 (5800 is for java)

See if this how-to helps (it reviews options)

[http://www.ubuntugeek.com/how-to-use-remote-desktop-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-use-remote-desktop-in-ubuntu-810-intrepid-ibex.html)

---

