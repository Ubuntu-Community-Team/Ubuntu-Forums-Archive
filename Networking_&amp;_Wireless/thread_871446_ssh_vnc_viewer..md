---
title: "ssh vnc viewer."
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by jonderson on 2008-07-26
I am able to connect to my ubuntu desktop at work. I am attempting to set up a remote desktop connection to that computer so I can get access from home. (like gotomypc.com)

i have set up openssh server on this desktop also so i could connect securely.

my computer at home is windows and i have successfully connected to the ssh server portion of the ubuntu machine at work. 

Now all I get is command prompt. How do I go about actually seeing the desktop. 
I am now stuck at
name@ubuntu:~$

Where do i go from here. What else to i need to get/install.

thanks

---

### Post by cariboo on 2008-07-27
Assuming you are running hardy on your office computer go to System-->Preferences-->Remote Desktop, select the settings you need, then use one of the vncviewer variants to access your desktop from Windows.

Jim

---

### Post by jonderson on 2008-07-27
I am able to use a VNC viewer inside of the LAN to connect to the ubuntu machine and see/control the desktop without a problem. but since that is not a secure thing to do over the internet i am trying to tunnel via ssh. so installed the ssh server on the ubuntu machine I am trying to connect to. I have successfully used PuTTY from my machine at home to connect to that machine and that is where I am now stuck. I have logged on to the ssh server and that putty screen is showing:
name@ubuntu:~$

i have tried typing vncviewer and get
ERROR: cant open display

tried vncviewer -via name@myipaddress:port ubuntu:port

and I get

ssh: myipaddress: Name or service not known
vncviewer: Tunneling command failed: /usr/bin/ssh -f -L 5599:Ubuntu:11800 name@myipaddress:port sleep 20.

the above command i have tried with all different types of ports and ip address. like
vncviewer -via name@myipaddress:22 ubuntu:5900
vncviewer -via name@myipaddress:5900 ubuntu:5900
vncviewer -via name@myipaddress:22 ubuntu:22
vncviewer -via name@myLANaddress:5900 ubuntu:5900

P.S. ubuntu is the name of the machine and i have tried that also with its LAN address. 

Also I have tried to open my vncviewer on my local machine at home and tried to connect just directly to ubuntu machine at work. with no luck. it says: Failed to connect to server. 


on my router i have forwarded almost every port that i can think of to that computer. 

AM i just not trying the right combination of things. Or am I lacking software??

---

### Post by jonderson on 2008-07-27
stupid smilies

---

### Post by Spudly on 2008-07-27
Have a look at this link:
[http://members.shaw.ca/nicholas.fong/vnc/]("http://members.shaw.ca/nicholas.fong/vnc/")

If that makes no sense, I'll try and assist...

I'm going to make the following assumptions:
[LIST]
[*]You are using TightVNC or UltraVNC;
[*]You are able to connect to your ubuntu system @ work on port 22 (you confirmed this in your previous post);
[*]You are at least vaguely familiar with setting up putty to forward a connection (for a local port) to a remote system & remote port;
[*]On your ubuntu system, under "System"->"Preferences"->"Remote Desktop", in the "Security" section, you have un-checked (disabled) the option that says "Ask you for confirmation" and checked (enable) the option "Require the user to enter this password" and set a nice secure password, and you know what this password is;
[/LIST]

Based on those assumptions, I would do the following:
[LIST=1]
[*]Setup putty to listen locally on the default VNC port "5900" (i.e. the local port), and set the remote machine to the ip or name of your ubuntu host, and the port to standard vnc port (i.e. "5900"). This makes connecting using vncviewer easier as you don't have to specify the port, since we are using the default (locally and remotely);
[*]Save this config, and open this putty session. This will create the tunnel;
[*]To use the tunnel, you connect "locally" - i.e. to the host named "localhost" or "127.0.0.1" (i.e. looping back to the system you are on, using the local port defined earlier, as that sends your connection thru the tunnel)
- e.g. vncviewer localhost:0
You don't need to specify the local port or remote host or remote port, coz you're using the tunnel and the default port. The ":0" is the display associated with your desktop, and this is ":0" (i.e. the first) unless you have changed the default or have multiple displays (I'm assuming you don't as it would be unusual!).
[*]When asked, enter the password you set;
[*]Wait for the VNC screen to appear and then go nuts!
[/LIST]

I tried this a moment ago and it worked successfully.

---

### Post by LoSeR_5150 on 2009-04-13
vncviewer -via "username@X.X.X.X -p XX" localhost:0

is what you are looking for I believe...

i.e. vncviewer -via "fakeuser@1.2.3.4 -p 22244" localhost:0 is what i am using.  Hope this helps.

---

