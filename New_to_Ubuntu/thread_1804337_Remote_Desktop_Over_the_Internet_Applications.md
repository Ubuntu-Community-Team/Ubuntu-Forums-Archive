---
title: "Remote Desktop Over the Internet Applications"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by eyeofreason on 2011-07-14
I have recently changed my parents over from M$ to Linux Ubuntu. They live a good hour away from me so I would like to have an easy gui application that will allow me to view and access their machine from the Internet if they have questions or issues. 
 I HAVE done the usual Google search and found plenty of answers, however I've come to trust this forum and would like advise from you guys. IT MUST BE SAFE.
 Much thanks for taking the time to respond.

---

### Post by seawolf167 on 2011-07-14
Two things:

[LIST=1]
[*]Use X forwarding over SSH for a completely secure connection to manage their computer (can't log into their existing session though)
[*]Enable remote desktop on the machine, then use a viewer like [UltraVNC Viewer ]("http://www.uvnc.com/download/1082/1082viewer.html")to connect to their machine (or tunnel through SSH if you need security)
[/LIST]

---

### Post by bodhi.zazen on 2011-07-14
> **eyeofreason said:**
> I have recently changed my parents over from M$ to Linux Ubuntu. They live a good hour away from me so I would like to have an easy gui application that will allow me to view and access their machine from the Internet if they have questions or issues. 
 I HAVE done the usual Google search and found plenty of answers, however I've come to trust this forum and would like advise from you guys. IT MUST BE SAFE.
 Much thanks for taking the time to respond.

+1 to learning ssh, you can do most any sys admin task needed over ssh.

If you *must* forward graphical applications, again, ssh -X

With ssh, disable password authentication and use keys.

If you *must* forward an entire desktop - FreeNX is faster and more secure then VNC (although you can increase VNC security via ssh as suggested by seawolf167).

---

### Post by hookitup on 2011-07-14
i use team viewer, [http://www.teamviewer.com/en/index.aspx](http://www.teamviewer.com/en/index.aspx) u can set it so u just  jump into there machine  without there permission or you have them supply you there temp password. i had to do a little tweakin in the settings because i dont have people on the other end and its still works great,, if u have an iphone there is an app for it as well , just in case its an emergency and u arnt around a computer, its very straight forward.

Good Luck

---

