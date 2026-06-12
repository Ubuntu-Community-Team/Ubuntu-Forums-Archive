---
title: "Program Suggestions: remote management"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by TechDragon on 2010-07-13
I am setting up my Mom on Ubuntu 10.04.

I am looking for a remote assistance style of program where I can log in take over her computer and assist her with issues.  Something like goto computer or logmeinrescue.  Preferably something where I can tell her to go to "website" type in code and I take over.

Any ideas?

Thanks

---

### Post by nothingspecial on 2010-07-14
ssh

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by blazemore on 2010-07-14
Ubuntu comes with an application called Remote Desktop.

The first thing you need to do is enable desktop sharing on your mum's machine.
To do this, go to System -> Preferences -> Remote Desktop, and set it up to look like this: [http://dl.dropbox.com/u/315875/Screenshot-Remote%20Desktop%20Preferences.png](http://dl.dropbox.com/u/315875/Screenshot-Remote%20Desktop%20Preferences.png)

Try it out on your local network first; on your computer go to Applications -> Internet -> Remote Desktop Viewer.

Click Connect, change the protocol to VNC, and click Find to see if your mum's PC appears in the list. Then you can connect to it, and she'll have to confirm the connection.

If you want to connect over the Internet, you'll have to find out your mum's public IP address by visiting [www.whatismyip.com](www.whatismyip.com)
Remember, IPs often change every so often.

You can then connect to this IP manually in your remote desktop viewer.

---

### Post by YesWeCan on 2010-07-14
Yep.
The Remote desktop Viewer is also known as Vinagre.
The Remote Desktop Server is also known as Vino.

Note that vnc is not secure so it is not advisable to use it over a public internet connection except via an encrypted tunnel, such as an SSH port forward or VPN, either of which are fairly easy to set up.

---

### Post by yeleek on 2010-07-14
> **nothingspecial said:**
> ssh

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

+1

Native vnc etc are the way to pain - just search the forums for tales of people getting hacked via vnc.

---

