---
title: "[SOLVED] Wireless for Beginner - Please Help"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by jludeman on 2007-05-02
I am new to wireless. I have set up hundreds of wired tcpip networks under windows and linux. Some of these networks were peer to peer in an industrial setting in order to share inputs and set outputs accordingly. Others were simple office peer networks to share files, printers and high speed internet connections.

Now I have a Broadband card in the desktop. An Atheros card in the laptop. A Buffalo router.

I would like to to share files, printers and an internet connection over the wireless network.

I would like to go to a hotel or coffee shop and access their wifi on my laptop.

I may be making the mistake of thinking of my wireless cards as invisible cables to a network. 

I truly do not understand how to tell if my wireless card is working. Should I be able to see my router?

I learned to use iwconfig from the forums. Here is what I find on the desktop.

eth1      IEEE 802.11b/g  ESSID:"this"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

The router is alive and I believe factory set to 192.168.11.1. I think I should be able to see it?

If anyone would be kind enough to share some knowledge or point me in the right direction I would appreciate it.

---

### Post by Emerzen on 2007-05-02
I find it helpful to think in terms of LAN vs. WAN(big-bad-internet), where everything on your side of the router is LAN and the other side WAN.

Your router connects to the WAN and is the first line of defense/firewall (assuming you have one built in to the router).  Each device on your LAN may or may not have security set up (software firewalls etc...)  Also, the actually radio transmission needs some form of security from eavesdropping...hence, encryption.  

So, I recommend, for starters, chaning the log-on password to your router if you haven't because everyone knows the default factory password.  Then, step 2 is setting up security/encryption.  My opinion is to broadcast your SSID w/ at least WPA encryption (WEP is easily crackable).  Now, any wireless device that enters the area of your wireless LAN will see the router.  For example:


When I turn on Ubuntu there's a little set of 4 bars in the upper right hand corner -> the network manager applet.  A single left click will show all the SSID's it detects in your area (you can name your SSID via the router config).  So, if I were to turn on my lappie in your network, I would see your SSID and then left click it to log on...since you've encrypted it I will have to enter a password you've set on your router.  If all is correct, I'll be connected shortly.  The same idea applies to any lappie moving into any wireless broadcast.

Some other considerations, each device on your LAN should likely have a firewall itself.  This will be important when you set up file/printer sharing.  My isp assigns my main ip dynamically DHCP.  This can be problematic for sharing w/in your LAN and moreso for remote logins.  So, another helpful step is to have your router assign each device on your LAN a static ip, no matter what the main ip is.  The next thing i do is register my main ip w/ the free DyneDNS service...this helps w/ remote/WAN access.

Sharing then - file sharing.  I prefer SSH although there are a myriad of alternatives.  If LAN is w/out any Windows machines, this is definately the way to go.  Logging in to a your SSH server from a remote Windows machine is also pretty easy.  The value of SSH is that all traffic is encrypted.  I install SSH and SSHFS from Synaptic on all of my boxes and make sure they are set to run via the Services panel in System->Admin->Services.  To configure, on each LAN device allow incoming connections on Port 22 from everyother device on your LAN.  Once done, go to Connect to Server under places, select SSH login, and enter the static-ip of your LAN device that you set your router to configure (this is the server).  A folder will pop up on your desktop w/ the ip under it, double click it and it will ask for a username and password for the machine you are logging into.  Once done, a nautilus window will pop open with the directory for that machine that you can drag and drop to.

To log on from the WAN.  First you have to tell your router to forward any SSH traffic to port 22 on one of your LAN devices (via it's assigned static ip).  So, if your on a machine, say a Windows box at work, and want to log in to home you would.  Open WinSCP*, enter your home ip for the server and hit connect-> again, it will ask for your log on information and, again, if all goes well a browseable folder will pop open on your desktop.  (WinSCP is an opensource SSH client that is free and a snap to use).  Also, you will have to have told your software firewall on your LAN device to accept SSH requests from any WAN-ips you will use (say your ip at work).  (You can select to allow any calls on Port 22 but this is pretty insecure, I recommend only allowing known ip's).  

Finally, the tricky part is typically figuring out what your home-ip is if your ISP assigns it dynamically.  If you sign up w/ DyneDNS, again free, they will assign a hostname to your current ip.  There are several ways to keep the ip of your hostname accurate.  My router actually does this for me automatically when it detects an ip change, it tells DyneDNS (Linksys).  So, I know my hostname and don't really ever know what my ip is.  If your router doesn't have this function, there are both Linux and Windows apps that run in the background and will do the same thing (forward any change in ip to DyneDNS).

Well, that's alot to throw at you and I hope it helps some.

I almost forgot about Printer sharing.  Similar process.  Enable the CUPS system on your machines.  Allow the software firewalls to accept traffic on the CUPS port (lpp 631).  When you install your printer, install it as a network printer in the wizard.  Any other LAN device should then automatically detect it and be able to utilize it.  I've never gotten into the details of printer sharing as I keep it basic, but this has been the easiest for me.

---

### Post by jludeman on 2007-11-07
I got this and a lot of other problems on my home lan fixed. See a detailed description on the following link.
[http://ubuntuforums.org/showthread.php?t=587560](http://ubuntuforums.org/showthread.php?t=587560)

---

