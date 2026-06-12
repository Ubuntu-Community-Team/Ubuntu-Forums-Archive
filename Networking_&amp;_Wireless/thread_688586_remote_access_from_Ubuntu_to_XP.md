---
title: "remote access from Ubuntu to XP"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by eekfonky on 2008-02-05
I live in Scotland and my colleague lives in France. I don't use Microsoft as it doesn't really work! However my colleague does and I can no longer do remote access/assistance from my computer since making the switch.

Can someone, anyone PLEASE tell me if it's possible to connect to and use his PC.

I have his IP address, I have tried various VNC clients - nothing works!!! Is it possible perhaps to use WINE and install MSN Messenger and do it that way?

He is using a Speedtouch USB modem with XP SP2

Any help would be fantastic

Thanks

---

### Post by karhulitos on 2008-02-05
I guess you can use Apps -> Internet -> Terminal Server Client for standard RDP use. But I guess you can't do remote assistance (your colleague sees what you do) with it..

---

### Post by eekfonky on 2008-02-06
Please explain, how exactly I use terminal server client?  What need set up on the XP machine e.g. Terminal server client asks for username, passwords domain etc. What is this? Can I get in with just his IP address. He doesn't need to see what I'm doing but I need to be able to access and use/fix his machine.

Any Ideas?

---

### Post by rickyjones on 2008-02-06
> **eekfonky said:**
> Please explain, how exactly I use terminal server client?  What need set up on the XP machine e.g. Terminal server client asks for username, passwords domain etc. What is this? Can I get in with just his IP address. He doesn't need to see what I'm doing but I need to be able to access and use/fix his machine.

Any Ideas?

If I remember correctly then Remote Assistance works with Remote Desktop (RDP).

The terminal server client program is what you want to use. It should give you fields for the Hostname/IP, Username, Password, and Domain. Ignore the domain. Enter the IP address and your friends username/password for accessing that computer. Then click connect (if I recall correctly).

Hope it helps!

-Richard

---

### Post by eekfonky on 2008-02-06
His XP computer doesn't use a username or password. Is there an XP default to access it. I can tell you that on startup he has the option to login as himself or other users by clicking on the relevant icon but it isn't password protected. This may be where I was going wrong. Any suggestions?

Thanks

---

### Post by -Vampyre- on 2008-02-06
I believe he will need to set a password, and make sure in his computer properties that remote desktop is checked. Also if he is behind a router, he will need to put in port forward rules to make port 3389 forward to the ip of his pc. You would need to put in his external ip into the terminal services client. That is if it is over the internet.

---

### Post by eekfonky on 2008-02-06
I'll ask him to try that, thank you. where will he find out how to port forward to his IP?

Thanks for the help

---

### Post by -Vampyre- on 2008-02-06
it depends on the router. if it is linksys it will be at [http://192.168.1.1](http://192.168.1.1) and he will have to log in and it is under applications and gaming. if it is a different router it will be at the ip of his default gateway. Does he have cable internet or dsl. Some dsl modems act as routers as well, making setup a little more difficult.

---

### Post by eekfonky on 2008-02-06
It's an ADSL phone line USB modem/router, not cable if that helps

---

### Post by gruhland on 2008-02-06
> **eekfonky said:**
> 
I have his IP address, I have tried various VNC clients - nothing works!!! Is it possible perhaps to use WINE and install MSN Messenger and do it that way?


VNC clients alone make no sense. You have to start a VNC server on the Windows PC (p.e. TightVNC). I use the same to connect my Ubuntu laptop at  home to my Windows workstation in my office. Works really fine. I can remotely work on the Windows machine.

---

### Post by eekfonky on 2008-02-07
so if the XP machine is setup with tightVNC, I should be able access it from my ubuntu machine?

---

### Post by gruhland on 2008-02-07
I use it without problems. TightVNC-Server on Windows XP and any VNC client (I use vncviewer) on Ubuntu.
The command is "vncviewer x.x.x.x:0" where x.x.x.x is the IP number of your Windows machine and ":0" is the screen which you want to work on (let's say desktop no. 0).

And use passwords, otherwise other people can work on that machine as well.

---

### Post by eekfonky on 2008-02-07
Can someone please explain exactly how to set up the XP machine as it's driving my colleague and I crazy - we're not stupid just inexperienced at this type of protocol.

Step by step instructions would be useful. Please help

---

### Post by Liet_Kynes on 2008-02-07
> **eekfonky said:**
> Can someone please explain exactly how to set up the XP machine as it's driving my colleague and I crazy - we're not stupid just inexperienced at this type of protocol.

Step by step instructions would be useful. Please help

On the server pc (XP one)

```
Right click on My computer.

Click Properties

Click Remote

Click the checkbox that say allow remote connections to this pc.
```

Your colleague will have to set a password on his PC. I don't think you can connect remotely to a passwordless acount via rdp.


In ubuntu

```

Click Applications -> Internet -> Terminal Server Client

Type in the IP address of the XP computer under Computer.

Type in the Username on the XP computer under Username.

Type in the Password on the XP computer under Username.

Click Connect.

```

---

### Post by eekfonky on 2008-02-07
I thought it was that easy but it just return a minute later saying connection timed out. Do I have to open ports on my Netgear router, or perhaps does he on his Speedtouch Alcatel USB mmodem?

---

### Post by -Vampyre- on 2008-02-07
If he only has the one modem/router, then yes. He will need to log in and add a port forward rule for port 3389 for rdp. I do not know where this would be in his router admin page. He will need a name for the forward rule like remote desktop. Then it will ask for the port range 3389 to 3389. Then the ip to forward it to. Most routers put you lan at 192.168.1.100 or 192.168.0.100 depending on make.

---

### Post by Liet_Kynes on 2008-02-07
[http://www.thinkbroadband.com/hardware/reviews/2002/q4/st510v4.html](http://www.thinkbroadband.com/hardware/reviews/2002/q4/st510v4.html)

How to forward a port on that router.

---

### Post by eekfonky on 2008-02-07
If this is possible with a USB connection we'll give it a shot, thank you

---

### Post by gruhland on 2008-02-07
> **eekfonky said:**
> Can someone please explain exactly how to set up the XP machine as it's driving my colleague and I crazy - we're not stupid just inexperienced at this type of protocol.

Step by step instructions would be useful. Please help

If we talk about VNC-Server:
install VNC-Server on the Windows machine (I guess, you should have admin rights).
IMPORTANT: Start the VNC server. 
In the configuration dialog click on "accept socket connections" and type in a password.
At "display" you should click "full display".
That's it.
In Ubuntu you have to install vncviewer (if it isn't).
-> sudo apt-get install vncviewer

After installation you can start it in the terminal
-> vncviewer x.x.x.x:0
(x.x.x.x is the windows machine ip number, important is the following :0 for the correct desktop)
The password which you have to type in is the same typed into the VNC server configuration dialog.
Ready.

---

### Post by Liet_Kynes on 2008-02-07
What i dont like about vnc. User has to be logged in

If local and remote logged in at the same time its messy with both controlling the mouse etc.

---

### Post by gruhland on 2008-02-08
What do you mean? That there must be a user logged in into Windows? 
I'm not sure but it should be possible to start the VNC server as service. 
I never tried because I use it as connection to my office workstation. So when I'm home no one will sit at that machine using the mouse. 
And the advantage of VNC is that you can get it for most OS. I'm often on travel and have my PDA with me (I will not always take my laptop). Okay, it's not really nice to work with the small display but I can do the necessary things if I have a WLAN access point or via GSM. On the other side I can use my Ubuntu laptop as well.

---

### Post by ubutufan on 2008-02-08
VNC is not safe. Ii is fine for intanet use. Not when you are away from your office and connecting from any unsecure(they all are) line
If you are connecting remotely and you care about privacy then ssh connections is the right thing to do

---

