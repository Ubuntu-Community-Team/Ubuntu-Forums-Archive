---
title: "XP Pro Laptop. Gutsy Desktop. How can I have the laptop take control?"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by Roasted on 2008-03-18
What the title says. I have a samba server set up, so I can get into my home directory and stuff from my laptop easily. But I want to take full control... kind of like remote desktop in the windows side of things.

How can I accomplish this?

---

### Post by Eiríkr on 2008-03-18
On the GUI level, I'm not entirely sure if this fits your bill, but you might want to look into remote desktop approaches such as VNC or FreeNX.  I'm currently musing whether to try carrying out the directions in [thread=467219]this thread[/thread] for remote desktop capability, tunneled over ssh for security.  

On the CLI level, things are much simpler -- install ssh on Ubuntu, and PuTTY on Windows, and you're good to go.  

Cheers,

Eiríkr

---

### Post by Roasted on 2008-03-18
Well, I'm certainly no expert, but I did go to school for network security and stuff like that... so I'd love the opportunity to tinker with something like VNC. It's not something I'd be afraid of.

I'd like full gui control, if possible. Should I find a VNC client for Ubuntu and Windows, and then see about connecting them later?

---

### Post by Eiríkr on 2008-03-18
Having just two client programs won't get you very far -- don't forget that you'll need at least one server program too.  :)

Cheers,

Eiríkr

---

### Post by Roasted on 2008-03-22
Okay, well, what do I need to do? 

I have remote desktop on my ubuntu machine enabled and I install tightvnc on my xp pro laptop. Now what do I do? I seem to be at a road block... am I to do something at the run box?

---

### Post by thesoothsayer on 2008-03-22
How about trying x11vnc? It allows you to connect to the "real" X session running on your desktop, instead of a separate X session.

Check it out here:
[http://www.karlrunge.com/x11vnc/](http://www.karlrunge.com/x11vnc/)

---

### Post by Glaxed on 2008-03-31
I have TightVNC viewer installed on XP Pro (wireless) and Gutsy remtoe desktop (sys-->Pref) enabled.

If I were on a different computer that has TightVNC viewer installed, how would I gain full GUI access to my Desktop via XP?

Can I do this while on the same network as my Desktop?

---

### Post by chilinski on 2008-03-31
The vnc server process must be running on any machine you want to connect to. Once that's done, all you have to do is run the vnc viewer and enter the name/ip of the server and the password.

A note:

On XPPro with SP 2, the firewall will block incoming vnc so you have to exclude the port in Windows Firewall.

---

### Post by Roasted on 2008-04-01
So essentially on my desktop, the vnc process needs to be currently running. Then I can just enable vnc on my laptop and take control. Eh?

---

### Post by Glaxed on 2008-04-02
Yep, worked very nicely for me.
Next step is to modify VNC Spy \-!-/, jk.
Thanks guys.

---

### Post by XstatyK on 2008-07-11
Did you already find a working solution?  I just connected using Freenx and it works very nicely.  Actually seems a lot nicer than VNC.

---

### Post by Roasted on 2008-07-11
Ahh I haven't tinkered with it at all. I've been messing with figuring out why the hype of pulse audio is so big and completely forgot about the whole controlling thing.

Plus, I found a hack for my wireless card on my laptop (currently unsupported) so if I get that working, I can just use rdesktop to my ubuntu desktop. 

This is on the list of priorities, but relatively low at this point. I'll check back when I have time to tinker with it. :)

---

### Post by lisati on 2008-07-11
I use a server from [www.realvnc.com](www.realvnc.com) on my (mainly) XP machine, and Gnome-RDP on my (mainly) Ubuntu machine; I have them running now so I can monitor (and control) my XP machine from Ubuntu (they are in different rooms)

---

### Post by XstatyK on 2008-07-11
No worries, I will post what I have done in case you want to look at it again sometime later:

download (all 3) installation packages for linux: client, node, server
[http://www.nomachine.com/download-package.php?Prod_Id=5](http://www.nomachine.com/download-package.php?Prod_Id=5)

Remote client for windows:
[http://www.nomachine.com/download-client-windows.php](http://www.nomachine.com/download-client-windows.php)

run the following command:
sudo /usr/NX/bin/nxserver --install --setup-nomachine-key --clean --purge
copy key from: /usr/NX/share/keys/default_id.dsa
To windows NX client and import key

To change default ssh port you will need to make the changes in the following files:
/etc/ssh/sshd_config
/usr/NX/etc/node.cfg
/usr/NX/etc/server.cfg

Restart ssh and NXserver
ssh- sudo /etc/init.d/ssh restart
Nxserver sudo /usr/NX/bin/nxserver --stop
--start
On windows NXclient configure to connect to specified port

---

