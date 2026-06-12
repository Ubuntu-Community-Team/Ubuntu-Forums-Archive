---
title: "Remote Desktop Viewer to view Windows machines?"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by brucewagner on 2010-04-17
What is the best application to run on Windows.... that would allow me to use  Applications --> Internet --> Remote Desktop Viewer  to view and control Windows machines?   (all versions of Windows, XP, Vista, 7)

I am running Lucid 10.04

---

### Post by Baneblade on 2010-04-17
If you want to use the native RDP on Windows (or RDPv5 in anything newer than XP) then Terminal Server Client is your best bet. Otherwise its not too much trouble install a VNC server on your windows installation, and that way you can use the remote Desktop Viewer that you would use for other 'nix systems too!

Hope that helps :)

---

### Post by brucewagner on 2010-04-17
Please pardon my ignorance, but...

(1)  How do I start the "hosting" side of RDPv5 (or RDP, in the case of XP).... on the Windows machine.

(2)  How do I use the "Terminal Server Client" to connect to the Windows machine and control it.  What exact credentials do I need to enter?

---

### Post by Baneblade on 2010-04-17
> **brucewagner said:**
> Please pardon my ignorance, but...

(1)  How do I start the "hosting" side of RDPv5 (or RDP, in the case of XP).... on the Windows machine.

(2)  How do I use the "Terminal Server Client" to connect to the Windows machine and control it.  What exact credentials do I need to enter?

1) You will need to allow remote access to the machine under System Properties (see attached picture)

2) After starting Terminal Server Client on your ubuntu machine you can enter a local or remote IP in the "Computer" field. (you can also enter local hostnames if you prefer)
Then select the correct protocol (in this case RDP/RDPv5)
Username
Password
Workgroup
and finally the client hostname (your ubuntu machines' name)

If you have any more issues feel free to PM me.

---

### Post by howefield on 2010-04-17
Edit: 
oops. sorry.

---

### Post by brucewagner on 2010-04-17
In Windows Vista I get a slightly different dialog box.  It wants me to "create an invitation" for a session... and give it a time limit, etc.

It results in saving a "Invitation.msrcincident" file.

I am supposed to email this file to the "support person" who is going to take remote control of my Vista machine.

I have no idea what to do with this in Terminal Server Client in Ubuntu.  I get the attached error window...

---

### Post by brucewagner on 2010-04-17
Would it perhaps be easier for me to install and run [http://www.tightvnc.com](http://www.tightvnc.com) on the Vista machine... and then use Ubuntu's "Remote Desktop Viewer" to connect to it....?

---

### Post by kg87 on 2010-04-17
Yes it would!

Install Tightvnc server, and start it. (make a note of your ip (just hover over the vnc icon in the system tray)
Now on your ubuntu machine, launch terminal server. Click connect, enter the ip adress with :0 or :5900 after (display number), and that should be it.

You may want to set a password up on the Windows box, and remember if you change the display number, you'll have to match that when trying to access the pc. 

nice and straight forward!? 

Hope that helps

---

### Post by howefield on 2010-04-17
> **brucewagner said:**
> Would it perhaps be easier for me to install and run [http://www.tightvnc.com](http://www.tightvnc.com) on the Vista machine... and then use Ubuntu's "Remote Desktop Viewer" to connect to it....?

If you want easy, you could have a look at Teamviewer.

Especially now that there is linux(ish) version. By (ish) I mean it is a downloadable .deb package but is really teamviewer packaged with wine, but works very well and is better than running the windows version in wine.

---

### Post by Butters_O_O on 2010-06-27
had the same problem. kg87 suggestion worked for me :KS

---

### Post by sonnymamawan on 2010-06-27
Thanks Baneblade.  Your instructions worked perfect for LAN.
I am now able to remote from Ubuntu Intrepid machine to Windows XP machine.

> **Baneblade said:**
> 1) You will need to allow remote access to the machine under System Properties (see attached picture)

2) After starting Terminal Server Client on your ubuntu machine you can enter a local or remote IP in the "Computer" field. (you can also enter local hostnames if you prefer)
Then select the correct protocol (in this case RDP/RDPv5)
Username
Password
Workgroup
and finally the client hostname (your ubuntu machines' name)

If you have any more issues feel free to PM me.

---

### Post by andrew732 on 2010-12-01
Exactly what is the difference between Remote Desktop Viewer and Terminal Server Client?  TSC can connect to both RDP and VNC servers but RDV can only connect to VNC servers?  Or do I have it wrong?

---

### Post by NCLI on 2010-12-01
> **andrew732 said:**
> Exactly what is the difference between Remote Desktop Viewer and Terminal Server Client?  TSC can connect to both RDP and VNC servers but RDV can only connect to VNC servers?  Or do I have it wrong?
Please start a new thead and ask your question there. This thread has been solved.

---

### Post by andrew732 on 2010-12-03
> **NCLI said:**
> Please start a new thead and ask your question there. This thread has been solved.

Even after OP's issue has been "solved", can't we still discuss the general topic?

---

