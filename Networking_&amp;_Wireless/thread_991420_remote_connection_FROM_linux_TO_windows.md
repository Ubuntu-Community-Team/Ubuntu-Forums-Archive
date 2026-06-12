---
title: "remote connection FROM linux TO windows"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by mbturner on 2008-11-23
I didn't know where else to post this so it's on networking.

Ok:

I need some help getting a remote connection from my ubuntu laptop in idaho to my windows desktop in washingon.
I have found out that since my windows pc is behind a firewall i need to use SSH to do this, and that's about ALL i know. No one has actually explained to me HOW this works. All I know is that you can definately not connect using the IP address my computer shows,because i'm not even CLOSE to being on the same subnet, and it shows a 192 IP. Can anyone help me? 
-Assume I am absolutely new to this-  

( i do have vncserver installed on my windows pc)
-update: i have also successfully connected while in the same room using ubuntu's "remote desktop viewer" in the applications menu, but like i said, i'm out of state

---

### Post by Iowan on 2008-11-24
I could point you at the [SSH-VPN]("https://help.ubuntu.com/community/SSH_VPN") help page, or the [VPN-Client]("https://help.ubuntu.com/community/VPNClient") page, but it won't help you connect the Windows box to internet.  If the Windows box is behind a router, it will need to forward a port to the Windows box (or open a port in the firewall). Unfortunately, this will probably need to be done from home.

---

### Post by superprash2003 on 2008-11-24
how about just using logmein [www.logmein.com](www.logmein.com)

---

### Post by uzi09 on 2008-11-27
> **mbturner said:**
> I didn't know where else to post this so it's on networking.

Ok:

I need some help getting a remote connection from my ubuntu laptop in idaho to my windows desktop in washingon.
I have found out that since my windows pc is behind a firewall i need to use SSH to do this, and that's about ALL i know. No one has actually explained to me HOW this works. All I know is that you can definately not connect using the IP address my computer shows,because i'm not even CLOSE to being on the same subnet, and it shows a 192 IP. Can anyone help me? 
-Assume I am absolutely new to this-  

( i do have vncserver installed on my windows pc)
-update: i have also successfully connected while in the same room using ubuntu's "remote desktop viewer" in the applications menu, but like i said, i'm out of state


Hey there. I'm quite new to this as well, and am in a similar situation.

You can access computers over the net by using remote desktop applications (ex: VNC).
To access a computer from the network with VNC, you need to be able to provide an IP address to the computer you want to connect to. Now in your circumstances, the ip address seems to be 192.xxx.xxx.xxx. All ip address starting with 192 are in a special category of ip address that are restricted for private use within private networks (like at home, or at an office). Whenever you install a router on your network, majority of the routers presently use the 192.xxx.xxx.xxx ip range. So chances are you're behind a router. It's all fine and dandy as long as you're at your office and referring to that particular computer using a 192.x.x.x (sorry, short form from now on) address, however as soon as you step outside of your office (and basically off of that router), that computer is can't be referred to with a 192.x.x.x address.

WHAT YOU HAVE TO DO:
So here's what you have to do. You're ROUTER is given a *real* IP address by your ISP for it to have access to the internet. You need to refer to your network using that particular ip address which can be determined by going on a website like: [http://whatismyipaddress.com/](http://whatismyipaddress.com/)
That's great, however we have a problem. You may have 5 different computers behind your router, so how do you know which one to connect to???
The solution is that each computer must be specified some how. We do this by using PORTS. You router has thousands of ports (as do computers, but since we're connecting to your router, we're going to use its ports). If you go to your router configuration page, you will have to assign a port for the particular computer you want to connect to over the internet. This must be done even if you only have one computer on the router because the router essentially blocks all the ports and doesn't allow access to anything with exception of some basic things (like port 80 for internet browsing).
Unfortunately, because there are hundreds of types of routers available and they all have different ways to adjust their settings, I can't specify unless we know what type of router you're using.
Basically, the idea is you look for something along the lines of "Port forwarding" or just "Forwarding" on your configuration page of the router.
To get to this page, you need to figure out the IP address of your router. Do this by:

1) Read your routers manual

2) On a windows machine, go to Start > Run > and type: cmd
then type: ipconfig
You will then have to determine then look for something along the lines of "gateway". You should have an IP address that looks like 192.168.100.1 or something really similar. The last digit would probably be either 0, 1, 2, or 100. The second last set is often 100, 10, or 2. The first two sets should be the same.

On a linux box, open up the terminal and type:
ifconfig
Similarly, you need to look for an IP address similar to the one I mentioned above.

Once you have that, you go to a browser and just type that address in. It'll ask you for credentials, which you'll have to refer to the manual (or search online based on the router) for its default credentials, or put in the ones you would have set yourself if you ever did change them.

Ones at the port forwarding page, you need to specify the computer you want to give access to the net by referring to its ip address. Then you want to open up the port that the APPLICATION (like VNC) uses. You could find that either in the VNC server settings, or try the common port that the VNC website would give you (like this one: [http://www.realvnc.com/support/portforward.html](http://www.realvnc.com/support/portforward.html)).

Ones the settings have all been saved you're good to give it a go.

Go to your client and type in the IP address of your ROUTER (remember the one we got from the website?). This will connect you to your router and VNC will automatically be looking for port 5900 (or whatever port it is depending on the application you decide to use). The router will forward the connection automagically to your host computer :).

Now please note. This opens your computer COMPLETELY to the world. So if you have some really important information on there, be careful because it can be hacked.

Some **basic** steps you can take to secure it is:
1) USE A **STRONG** PASSWORD!!!!!!!!!
2) Try to change the port from your VNC server settings to a different one ([here]("http://www.governmentsecurity.org/articles/CommonPorts.php")'s a list of common ports that are available and should give you an idea of the range of the ports that are available. Just pick anything in between any of those)
3) Backup your computer
4) keep in mind these are all basic security measures. someone can still get in....someone can *always* get in :)

Hope it helps. Let us know if you have any problems.

---

### Post by lorenzosu on 2008-11-29
Hi uzi,
My company's computer (running Windows) is behind proxy, firewall etc. and of course I have no access to all of that. I successfully use LogMeIn free ([www.oegmein.com](www.oegmein.com)) to access my machine, although it is a very 'windows-centric' application.
The nice thing about log me in is that unlike VNC, SSH etc. it uses http(s) so that any machine with web access can be seen.

From ubuntu it was really hard to use, though I discovered from this page: [https://answers.launchpad.net/ubuntu/+question/13929](https://answers.launchpad.net/ubuntu/+question/13929) that they have released a beta firefox plug-in for linux: I tested and for me (on 8.10) works great: [https://secure.logmein.com/labs.asp](https://secure.logmein.com/labs.asp)

Of course all usual security cautions are recommended (strong passwords, don't share user data, clear browser histories often etc.)

Kind regards,
Lorenzo

---

