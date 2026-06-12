---
title: "Connecting to an XP machine from Ubuntu"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by CorvetteFan86 on 2008-02-20
I am trying to test out vnc at my home. I have a router that i believe i configured for port forwarding and installed VNCserver and VNCviewer. I installed tight vnc on the windows xp laptop with a wireless card. I went ot connect to the VNC Server and it would not let me enter an ip address. My question to you guys is am I following this correct or not? if so what else do i need to do? Is there an easier way to do it?

---

### Post by CorvetteFan86 on 2008-02-20
Also I would like to connect to an outside computer that has xp. Is this the only place that needs to be filled out for port forwarding? [http://www.portforward.com/english/routers/port_forwarding/Dlink/DI-624/DI-6243.jpg](http://www.portforward.com/english/routers/port_forwarding/Dlink/DI-624/DI-6243.jpg)

thanks all,
Thomas

---

### Post by CorvetteFan86 on 2008-02-21
Anyone? I am stuck on authentication. It won't let me enter anything.

thanks,
Thomas

---

### Post by HereInOz on 2008-02-21
If you installed VNC viewer and server on the XP machine, then you ought to be able to connect to it from the Ubuntu machine using port 5900.  

If you are having problems, the best way to troubleshoot it is to get both machines on the same network, and then, for the sake of testing, turn off any firewalls on both machines.  If you don't know how to disable the firewall in Ubuntu, first install Firestarter (in the repositories) then use it to turn off the Ubuntu firewall.  

If the machines are on the same network, and the firewalls are disabled, and VNC server is running on the XP machine, use Applications > Internet > Terminal Server Client to attempt to connect to the XP machine,

Once you have achieved this, you will then need to put the firewalls back on and see if that breaks your connectivity.  If it does, then you need to configure the firewall at the receiving end to allow connections on port 5900.

Once you have both machines happily working together locally, it is time to venture out into the wide world.  When you port forward your router, you need to specify the private IP address of the XP machine - if it is a D-Link set to default it will be 10.1.1.xxx, and set the private port to 5900, and the public port to 5900.

Save your settings and restart the router to make sure it has held its settings.  You should then be able to use Terminal Server Client to access the XP machine by entering your public IP address (the one assigned to you by your ISP) and the connection, if you have done it properly, should be forwarded to the IP address of the XP machine,

---

### Post by HermanAB on 2008-02-21
You should not use VNC to connect to Windows XP.  Windows 2003 and XP have Citrix Terminal Server built in.  Enable Remote Desktop in Control Panel, System, forward port 3389 in your router and then use rdesktop to connect from Linux:

$ rdesktop -g 90% ipaddress

You can also do 'seamless' RDP using this: [http://www.cendio.com/seamlessrdp/](http://www.cendio.com/seamlessrdp/)

Windows RDP is a much superior solution to VNC.  RDP is secure (encrypted) and provides printer forwarding for example.

Cheers,

Herman

---

### Post by CorvetteFan86 on 2008-02-21
Thank you all for the prompt replies!
I forwarded the port and I tried using remote desktop and It showed me as connected. Is there a way to log on through remote desktop to allow the same abilities as VNC such as allowing more than one user on at a time. So I could use it like remote assistance?
 


Cheers,

Thomas

---

### Post by HermanAB on 2008-02-21
RDP *must* have an account password.

---

### Post by tuskenraider on 2008-02-21
yep i agree with the fellow right before me... i have remote desktop enabled on my server and my other desktop and i connect to them very easily.. the accounts MUST be password protected and "allow users to connect remotely to this computer" must be checked also. (in control panel -> system -> remote.)

btw... remote desktop will only work.. in windows xp professional. **xp home will not let you connect to it.. **

anyway.. the RDP program i use in ubuntu 7.10 is gnome-rdp. works very well for my purposes.

tusken

---

### Post by CorvetteFan86 on 2008-02-21
Does anyone know why when I type vncviewer in the terminal window and it comes up with the prompt box but will not let me enter any information.

thanks,
Thomas

---

### Post by Woody@N87 on 2008-02-25
Herman
  When I do what you suggest here I get a response from the terminal window that the keyboard selected is us-en or some such but nothing else.  Am I doing something wrong here?

  Nevermind, was a fat fingering problem, I have worked out now and it's working great.   Thanks all.  I used Herman's answer which worked perfectly.

---

