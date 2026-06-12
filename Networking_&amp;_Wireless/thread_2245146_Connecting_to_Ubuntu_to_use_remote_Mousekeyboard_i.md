---
title: "Connecting to Ubuntu to use remote Mouse/keyboard in Mocha VNC Lite"
date: 2014-09-21
forum: Networking &amp; Wireless
---

### Post by mcweb2 on 2014-09-21
[FONT=Verdana]Hi folks,[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]I wonder if someone could please help me. I need to have a wireless mouse and keyboard on my Ubuntu desktop computer. I am trying to install the product Mocha VNC Lite seems like a good option.[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]This is the hardware I have:[/FONT]
[FONT=Verdana]
[/FONT]
**[FONT=Verdana]My Ubuntu Computer (originally a Windows PC)[/FONT]**[INDENT][FONT=Verdana]Desktop Sharing Settings  [/FONT][/INDENT]
[INDENT=2][FONT=Verdana]&#9745;&#65039; Allow other users to view your desktop[/FONT][/INDENT]
[INDENT=2][FONT=Verdana]&#9745;&#65039; Allow other users to control your desktop[/FONT][/INDENT]
[INDENT=2][FONT=Verdana]&#9745;&#65039; Require the user to enter this password (password has been typed in)[/FONT][/INDENT]
[INDENT][FONT=Verdana]Firewall 
[/FONT][/INDENT]
[INDENT=2][FONT=Verdana]Has been turned on, Port 5900 is used by the application vino-server. I added a rule to allow Mocha Lite on Port 5901.[/FONT][/INDENT]
[INDENT][FONT=Verdana]Internet
[/FONT][/INDENT]
[INDENT=2][FONT=Verdana] My computer has no WIFI card, I am using a TP-Link 150 Mbps Wireless N Nano USB Adapter.[/FONT][/INDENT]
[INDENT=2][FONT=Verdana]I have tried connecting to the Internet via two different WIFI Networks. [/FONT][/INDENT]

[LIST=1]
[*=2][FONT=Verdana]Network Name=  "mcWeb Apple Wireless". It is hosted on our Apple Time Machine which is connected to the Internet via a router that our Internet Provider "Rogers" has installed.[/FONT]
[*=2]Network Name= "WV Network Rogers" which is hosted directly on the "Rogers" router.
[/LIST]
**[FONT=Verdana]Apple iPad 3[/FONT]**
[FONT=Verdana]I am running Mocha VNC Lite, I always make sure I'm connected to the same WIFI Network as the Ubuntu computer.[/FONT]
[FONT=Verdana]
[/FONT]
**[FONT=Verdana]Testing[/FONT]**
[FONT=Verdana]1. IP Address port 5900, Computer and iPad on the same networks, tested on both WV Network Rogers WIFI Network and mcWeb Apple Wireless WIFI Network.[/FONT]
[FONT=Verdana]2. #Name Address port 5901, Computer and iPad on the same networks, tested on both WV Network Rogers WIFI Network and mcWeb Apple Wireless WIFI Network. From what I have read if your connecting to a MAC you need to use the#name address.[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]I haven't been able to connect at all, the closest I have gotten is when I get this error message "Host has closed the session". Could you please tell me what I am doing wrong.[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]Thank you very much,[/FONT]
[FONT=Verdana]
[/FONT]
McWeb2

---

### Post by weatherman2 on 2014-09-21
First, test VNC on your local network (with the iPad near the Ubuntu computer).  That means, you must connect the Ubuntu computer and the iPad to the same WiFi.  

It sounds like you aren't sure if your wireless card is working correctly (connecting to a wireless network) on the Ubuntu machine.  Is it?  If not, you need to fix that first.

If you have successfully connected the Ubuntu machine to the wireless and have the iPad connected to the same wireless, then proceed from there.

Connecting to the Ubuntu machine from outside(?) your home using the iPad is a little more complicated but is doable.  But you must get the local connection working with VNC first.

---

### Post by mcweb2 on 2014-09-21
Thanks for your help!

i am fine connecting the Ubuntu Computer to both networks. It tells me it connects to each WIFI network and I can see the other computers in my network whenI open up file manager.

i can't get the Mocha VNC program to connect to the VNC on my Ubuntu.

---

### Post by mcweb2 on 2014-09-21
[FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]More testing from my original post.  

I finally made a little progress I realized I had mixed up my IP address  so I fixed that. Then I tried port 5800 and turned off the Firewall. When I did this the connection message changed to Negotiating VNC, but it didn't connect.
Then I read this page, "remote control ubuntu  using your iPhone VNC" setup.[http://kshwetabh.wordpress.com/2010/01/09/remotely-control-ubuntu-using-your-iphone-vnc-setup/](http://kshwetabh.wordpress.com/2010/01/09/remotely-control-ubuntu-using-your-iphone-vnc-setup/). I installed the x11vnc software, password and auto startup. The only problem I saw was the fact that according to the Firewall settings port 5800 was still attached to vino-server. I rebooted thinking things might iron themselves out. Unfortunately now all I am getting is a black screen after I boot up and see the Ubuntu logo. 

Can an anyone please help me to get this fixed. [/FONT]

---

### Post by weatherman2 on 2014-09-21
You don't need to turn off any firewall on the Ubuntu machine unless you explicitly set one up.  I do remote VNC access to machines on several Ubuntu machines and have never even setup a firewall on most of them.

You should use port 5900 by default.

Are you saying you now can't even boot the Ubuntu machine?  Can you Ctrl-Alt-F2 to drop into a terminal, login there, and check the tail of /var/log/syslog for any errors?

---

### Post by mcweb2 on 2014-09-21
Ok it was black I did Ctrl+alt+F2 nothing. Then I turned it off and on restarted it and it's ok now. 

Ok ok so I am setting the port my iPad/mocha VNC a to 5900. The message I get is "Information host has closed session".

---

### Post by mcweb2 on 2014-09-22
[SIZE=2][/SIZE][SIZE=2]The Mocha VNC Lite tech support got back to me. They got me to check if port 5900 was blocked at canyouseeme.org. I received this message back "[COLOR=red][FONT=HelveticaNeue]Error:[/FONT][/COLOR][COLOR=#444444][FONT=HelveticaNeue] I could [/FONT][/COLOR][COLOR=#444444][FONT=HelveticaNeue]not[/FONT][/COLOR][COLOR=#444444][FONT=HelveticaNeue] see your service on [/FONT][/COLOR][COLOR=#444444][FONT=HelveticaNeue]**"it gives the IP address of my router" **[/FONT][/COLOR][COLOR=#444444][FONT=HelveticaNeue]on port ([/FONT][/COLOR][COLOR=#444444][FONT=HelveticaNeue]5900[/FONT][/COLOR][COLOR=#444444][FONT=HelveticaNeue])[/FONT][/COLOR]
[COLOR=#444444][FONT=HelveticaNeue]Reason:[/FONT][/COLOR] C[SIZE=2]onnection timed out[/SIZE]" 
[SIZE=3]
I know from looking at the Firewall setting on my Ubuntu Computer that port 5900 is taken by vino-server. Can anyone tell me how to remove the vino-server from port 5900? [/SIZE]
[/SIZE]

---

### Post by weatherman2 on 2014-09-22
Unless you install another VNC server, vino-server will be acting as the VNC server (the one you are trying to connect to).  That's why it is using port 5900.  I use vino-server daily to connect to my remote Ubuntu machines using VNC.

I suggested you first test this out on your internal network, without worrying about external ports - meaning, the firewall on your home router that keeps outsiders out.  When a site like canyouseeme.org checks to see if a port is open, it can only check the external ports (home router).  If you are testing on your internal network, your home router's firewall (port 5900) is irrelevant, because you aren't coming through it.  You're going over the internal network from the iPad to the Ubuntu server, which should have port 5900 open (used by vino-server).

So to be clear: your iPad is connected to the same WiFi (and not using 3G/4G or data) to connect to the network, right?  I am not familiar with the iPad, but I would temporarily turn off 3G/4G data while testing this on your internal network, to make sure you are truly using the same WiFi as the Ubuntu machine.

Also, your router cannot be set for "AP Isolation" (a wireless security measure) or it won't allow wireless clients (like an iPad) to see any wired clients (like your Ubuntu server) on the network.  AP Isolation is turned on for privacy so people can use your WiFi without them being able to access any of your other computers.  Bu you want it OFF for sure to do what you are doing.  It may be called something besides "AP Isolation" I guess - I don't know what your router manufacturer might have called it.  I would try to "ping" your Ubuntu server first from the iPad to make sure you can truly "see" it on the network.  If not, figure that out before worrying about VNC.

---

### Post by mcweb2 on 2014-09-22
Hi Weatherman thanks for your patience&#55357;&#56842;
So my iPad only uses WIFI or Bluetooth to connect to the Internet. I have turned off the Bluetooth just in case it's an issue. 

My iPad is on on the same network as my Ubuntu computer.

The Firewall is off and I understand what you are saying about the router, basically leave it alone not part of the problem.

I have inserted the IP address for my Ubuntu computer into Mocha VNC. When I test the connection I get this message" Information Host has closed the session".

---

### Post by weatherman2 on 2014-09-22
Do you have any other computer you can use to test the VNC connection?  That way, you can be sure your VNC server is working correctly on the Ubuntu machine.  I'm not sure whether your issue is the Ubuntu machine or Mocha VNC, but if you can be sure the Ubuntu VNC server (vino-server) is working correctly, then you can contact Mocha VNC support again with that information.

---

### Post by weatherman2 on 2014-09-22
And as I said earlier: make sure sure you can "ping" the Ubuntu server from the iPad.  Try the Network Ping Lite app (for example).

---

### Post by mcweb2 on 2014-09-22
Ok so here is what I tried
- Mocha VNC on my iPhone to connect to my Unbuntu computer = same error message" host has closed the session"
- Mocha VNC On my iPad to connect to my MAC PRO = it works no problem
Now I will try to find the ping software you mentioned in the 2nd last post

---

### Post by mcweb2 on 2014-09-22
[FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]This might be a duplicate post I don't see my last post 
I did the ping test
Results
23 packets transmitted, 21 packets received, lost 8.7 %[/FONT]

---

### Post by mcweb2 on 2014-09-22
Maybe the problem is I installed the x11VNC server software and the machine is confused. I noticed when I opened the X11VNC interface up it has the port set to 5901?

---

### Post by mcweb2 on 2014-09-24
Ok I installed Remmina Desktop Client on my Ubuntu computer. I was able to create a new VNC connection to my MAC PRO desktop easily. So I guess that means my outgoing VNC setup on my Ubuntu computer is setup correctly. Does this mean I have a blocked port 5900?

---

