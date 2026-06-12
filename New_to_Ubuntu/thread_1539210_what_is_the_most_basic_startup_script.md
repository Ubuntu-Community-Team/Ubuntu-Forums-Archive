---
title: "what is the most basic startup script"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by B34ST1Y on 2010-07-26
Hello! 

Can someone give me a little insight on the matter. I seem to be getting mixed, and not straight answers. 

Is there a folder in Linux that will run every script inside of it, everytime at bootup? 

like, say I have 3 scripts that need to run @ bootup. How do I accomplish this?

---

### Post by Calash on 2010-07-26
At what point during startup do you want them to run and what user privileges will they need to execute?

There are many points that you could put a script to execute, so it really depends on the timing you need.

---

### Post by jtarin on 2010-07-26
> **B34ST1Y said:**
> Hello! 

Can someone give me a little insight on the matter. I seem to be getting mixed, and not straight answers. 

Is there a folder in Linux that will run every script inside of it, everytime at bootup? 

like, say I have 3 scripts that need to run @ bootup. How do I accomplish this?
Off the main menu: System > Preferences > Sessions. Click Startup Programs, Add, type your line, and click OK
As mentioned above...just depends on what and when it needs to execute. Slackware uses an rc.local file but Ubuntu has nothing like this with the exception of the scripts in /etc/init.d

edit: It turns out Ubuntu does have the /etc/rc.local file as Slack...only in a different location. Your simplest.You can edit with Nano in the terminal.

---

### Post by B34ST1Y on 2010-07-26
I'd like to do it all within a console, if possible not using the GUI.


Ideally, after all normal startup actions have taken place. I have an snmpd monitor I need to automatically start up, as well as a few other things like a vncserver. 


A couple of things will need to run with root privileges, while others will not.

---

### Post by prodigy_ on 2010-07-26
For things that require root privileges and don't have GUI, you can use **/etc/rc.local** file. To edit this file, press Alt+F2, type **gksu gedit /etc/rc.local** into the window that will appear and click "Run" button.

For your user-specific startup scripts you can just add launchers to Startup Applications. For this, press Alt+F2, type **gnome-session-properties** into the window that will appear and click "Run" button.

---

