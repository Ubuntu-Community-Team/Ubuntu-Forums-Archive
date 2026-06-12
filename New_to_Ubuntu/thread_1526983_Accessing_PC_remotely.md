---
title: "Accessing PC remotely"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by nynoah on 2010-07-08
Is there a way that I can set up my desktop so that I can access it over the net.  I am doing some work in another area and need to be able to access my desktop from far away.  Is there a way that I can log into my computer remotely and still have access to all the functions of my desktop?  If someone has a link to a site that would help me, that would be great too.

Thanks

---

### Post by WRDN on 2010-07-08
If you have a fast connection, then you could use [VPN]("https://help.ubuntu.com/community/VNC"), tunnelling through SSH for added security. Once the VNC server is set up on a machine, a VNC Client can then connect to it, and view the users desktop (as well as control it).

At times, you may only want to use terminal programs, so you only need to use [SSH]("https://help.ubuntu.com/community/SSH") here. As with VNC, SSH uses the client-server model.

---

### Post by nynoah on 2010-07-08
Will this work with a wireless router, or do I have other issues that I need to address too?

---

### Post by partloer on 2010-07-08
Hi nynoah,

It depends on your network.  If you have a simple home network then all that is needed is to setup port forwarding setup.  However if this is on a business network it depends on your network policy/design.  

Here is information on the different [remote access]("http://ubuntuguide.org/wiki/Ubuntu:Lucid#Remote_Access") methods for Ubuntu.  Again depending on what you are trying to do will determine what method will work best with you.

Feel free to ask more questions and give more detail so that we may help out more.

---

### Post by nynoah on 2010-07-08
Home network.  I am reading about port forwarding right now.  Any other hints?

---

### Post by quinnten83 on 2010-07-09
teamviewer now works on linux.
and is easy to setup, you can try that, [www.teamviewer.com](www.teamviewer.com)

---

