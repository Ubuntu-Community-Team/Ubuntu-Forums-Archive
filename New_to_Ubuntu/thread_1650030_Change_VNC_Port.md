---
title: "Change VNC Port"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by erilidon on 2010-12-21
How do I change the port used to connect to ubuntu with vnc? ie not 5900

---

### Post by jtarin on 2010-12-21
[http://www.realvnc.com/products/free/4.1/winvnc.html#Connections](http://www.realvnc.com/products/free/4.1/winvnc.html#Connections)

[http://www.ehow.com/how_6796359_change-vnc-listening-port.html](http://www.ehow.com/how_6796359_change-vnc-listening-port.html)

---

### Post by erilidon on 2010-12-21
I appreciate the effort but I am wanting to know how to do it for the built it vnc server in ubuntu. Those links are for addon programs for windows.

---

### Post by pricetech on 2010-12-21
Since VNC is inherently insecure, may I suggest SSH instead.  Easy to change the port too.

```

sudo cp /etc/ssh/sshd_conf /etc/ssh/sshd_conf_orig
sudo nano /etc/ssh/sshd_conf

```

The entry for port is right at the top of file.  Change it to whatever you want.

---

### Post by spiky001 on 2010-12-21
Yo cant change the vnc port I would 2nd **pricetech**'s option tunnel through with ssh, or install a vnc server

---

### Post by jtarin on 2010-12-21
And I appreciate the clarity of your posted request.

[http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop](http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop)
[http://www.techotopia.com/index.php/Image:Ubuntu_advanced_remote_desktop_preferences2.jpg](http://www.techotopia.com/index.php/Image:Ubuntu_advanced_remote_desktop_preferences2.jpg)

---

### Post by erilidon on 2010-12-22
> **jtarin said:**
> And I appreciate the clarity of your posted request.

[http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop](http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop)
[http://www.techotopia.com/index.php/Image:Ubuntu_advanced_remote_desktop_preferences2.jpg](http://www.techotopia.com/index.php/Image:Ubuntu_advanced_remote_desktop_preferences2.jpg)


yeah thats more of what I am looking for. But I am using 10.10 (maverick) and it doesn't appear to have that menu. However I have found that if you open gconf-editor and go to desktop -> gnome -> remote_access there is a alternate port option and a option tell it to use the alternate port. But it doesn't appear to work even after a restart... any ideas.

I've attached a screenshot of the gconf-editor

---

### Post by erilidon on 2010-12-23
I was able to achieve what I was wanting with Port Forwarding on my router... thanks anyways.

---

