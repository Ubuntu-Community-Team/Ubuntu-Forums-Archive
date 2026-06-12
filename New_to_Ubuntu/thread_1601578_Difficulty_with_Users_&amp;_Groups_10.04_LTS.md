---
title: "Difficulty with Users &amp; Groups 10.04 LTS"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by SwarfEye on 2010-10-20
Hey all,

I'm not sure if this is the right place to post this question, please let me know if I should move it.

I've been playing around with Ubuntu for some time, but I still consider myself relatively novice.

I've got 10.04 LTS running on an old dell, and connected to the internet with a static IP through a firewall.  It is a pretty much clean install.

I've been trying to setup various services and things.  Most recently I was trying to get the thing to mount a USB flash drive and/or my Lacie USB external drive.  In both cases the machine says no "Not Authorized".

Looking through various web pages I've come to the conclusion that... 

a) this is weird because 10.04 is supposed to mount these USB devices automatically in default installation (which is what I've got)

b) this is particularly weird because, the "Users and Groups" dialog box in System->Administrative->Users&Groups is not working... it will pop up, but then the only button that is active is the "Close" button.  I am unable to use the interface to create, delete, or modify anything!

So, I guess the questions... How do I fix Users and Groups?  But also more broadly, could this be a sign that my system has been infiltrated, and how might I go about testing that theory?  Also, the "System Testing" feature simply hangs and does not produce results.

Suggestions very much appreciated!

Thanks,

Bill

---

### Post by NightwishFan on 2010-10-20
System Testing is not for that purpose. I doubt you are infiltrated, are you using the user that you originally created or a new one? For root enabled tasks a user has to be authorized as an administrator.

---

### Post by SwarfEye on 2010-10-20
Yeah, I kind of figured that System Test was not for that, but the fact that it doesn't work gave me pause.

I'm logging in as an adminstrator.

B

---

### Post by NightwishFan on 2010-10-20
That does not give me pause. I believe it needs to be run as root and the menu link runs it as a normal user for some reason.

Check to see if your user is named as an administrator, and if so, press alt+f2 run this command for me:
```
gksudo gnome-system-monitor
```

Type password when prompted, and if the system monitor shows up you have no problems with sudo.

---

### Post by sisco311 on 2010-10-20
Check if polkit-gnome-authentication-agent-1 is running and your user is in the admin group. Post the output of:
```
pgrep -lf authentication
```
```
grep admin /etc/group
```
and
```
groups
```

---

### Post by SwarfEye on 2010-10-20
Nightwish,

System Monitor pops up fine.  Doesn't look like I'm having any trouble with sudo.

Sisco,

Here is the output of the commands you suggested I run...

```

swarfeye@hobbit:~$ pgrep -lf authentication
1417 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
swarfeye@hobbit:~$ grep admin /etc/group
lpadmin:x:105:swarfeye
admin:x:119:swarfeye
swarfeye@hobbit:~$ groups
swarfeye adm dialout fax cdrom floppy tape dip video plugdev fuse lpadmin admin sambashare

```

Thanks for your help.

B

---

