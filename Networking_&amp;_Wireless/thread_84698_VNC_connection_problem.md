---
title: "VNC connection problem"
date: 2005-10-31
forum: Networking &amp; Wireless
---

### Post by crowndip on 2005-10-31
Hello, I have a strange problem with VNC.

I connect from local network through router linksys wrt54gs to a win xp computer using VNC.
VNC displays initial screen, takes inputs but does not display further screens.
It sort of freezes but continues to accept inputs from keybord & mouse.

Without router it works fine. But it works fine also from a virtual machine on my computer through the router.

I tried also realvnc with wine and it behaves the same way. ( file transfer works always fine )

It seems that incoming data are somehow blocked.

do you have any idea ?

Thanks
Filip

---

### Post by crowndip on 2005-11-02
Noone encountered this problem ???

.

---

### Post by jomofrodo on 2005-11-27
Not exactly sure what you are describing. I am having trouble with RealVNC through a router -- both the client and the Ubuntu machine (server) connected via wireless. Connection works fine, but about 2 minutes later the router kicks out the wireless connection to both machines. At which point I have to reboot the router. Router is a Netgear WG602

---

### Post by dbott67 on 2005-11-27
I use VNC to connect to my various home computers from work (Ubuntu laptop, XP Pro desktop, OSX box and my wife's computer).  I'm using a D-Link 614+ router, with port-forwarding setup in the following fashion:
1. 5900 (VNC default) to static IP of XP computer
2. 5901 to static IP of OSX
3. 5902 to static IP of Ubuntu
3. 5903 to static IP of my wife's laptop

I use UltraVNC on my XP computer and am able to transfer files without any issues.  Here are a few suggestions:
1. Update your router firmware to the latest version (or if you already did, try dropping down to the previous version).
2. Try using http access, as opposed to the viewer.  For example, you would enter **[http://your.home.ip.address:5800/](http://your.home.ip.address:5800/) **to connect to your home computer using Firefox.
3. Make sure you're using static internal IP addresses (probably not your problem, but it prevents your port-forwarding rules from getting messed up if your IP changes).
4. Try changing the port VNC listens on to something different (and make sure you change the appropriate port-forwards as well).  Some ISPs block ports of certain applications.  Changing it to a non-standard port, your ISP may not block it.

-Dave

---

### Post by Tennen on 2005-11-29
How do you change the default listening port for ubuntu? My school's Firewall blocks 5500 through 5900.

---

### Post by dbott67 on 2005-11-30
[QUOTE=Tennen]How do you change the default listening port for ubuntu? My school's Firewall blocks 5500 through 5900.[/QUOTE]

Rather than change the listening port, you could just change the ports on your NAT router.  For example, you could select port 85 as the 'forwarding port' on your router to go to your Ubuntu box (which is listening on 5900).

In your NAT router, just setup a rule that forwards all traffic on port 85 (public) to port 5900 (private) and send it to the IP of your Ubuntu computer.

Then, when you're trying to connect to your home computer, just use port 85 in vncviewer instead of the default 5900.  For example, in your browser type: [http://your.home.ip.address:85/](http://your.home.ip.address:85/) or using VNCViewer you would type **your.home.ip.address::85** (the port # would be separated by 2 colons).
This should take your to your NAT router, which will forward you through to your Ubuntu box on port 5900.  Feel free to use whatever public port you want.  85 was only an example.

The VNC documentation may help in changing the listening port [http://www.realvnc.com/faq.html#port](http://www.realvnc.com/faq.html#port) within VNC, although, I believe that Ubuntu/Gnome uses Vino instead of VNC (not sure what the difference is, though).

Hope this helps.

-Dave

---

### Post by Tennen on 2005-11-30
I think that will help me. I know how to forward ports but what I'm realy glad you posted was this
> using VNCViewer you would type your.home.ip.address::85 (the port # would be separated by 2 colons).
This should take your to your NAT router, which will forward you through to your Ubuntu box on port 5900. Feel free to use whatever public port you want. 85 was only an example.
What port would you suggest using if I want to connect from a very secure network at my school to my house? (I'm using a on ibm thinkpad with XP on it from school)

---

### Post by dbott67 on 2005-11-30
If you're not running a webserver at home, you could use port 80 (HTTP), which should be permitted on your school's network.  You could also use 21 (FTP), 23 (telnet), 25 (SMTP), 110 (POP3), 143 (IMAP), 443 (HTTPS).  These are all commonly used services by network users, so I doubt that they would be blocked.

The downside is that 'script kiddies' have automated scripts that will be scanning your home IP address and you'll have an open port on a fairly well-known port.  Just keep your computer's OS up-to-date and turn off any unneeded services (such as FTP, telnet, WWW or any other things that you don't use).

-Dave

---

### Post by Tennen on 2005-11-30
That helps alot. I have not had any experience with socket programming so I don't know much about specifying ports.

EDIT: I am not getting the results I expected. I know exactly what the problem is. When I change to port on my client(i.e. 85), everything is fine and dandy until I think that the information is all being sent to the changed routing table [VNC | 85-85 | Protocol:BOTH | IP Address: 192.168.1.103]. It is here that the information is sent ot the server but the server isn't accepting VNC connections on port 85 so......what to do what to do. I am back at the original problem of changing ubuntu's default VNC server port.

---

### Post by crowndip on 2006-04-17
Hello,

It was a router problem, it needed new firmware.

---

### Post by fakie_flip on 2006-12-02
Try using x11vnc instead of vinovnc. It does the same thing letting you use your already existing X without starting another one, and it should let you change the port number.

---

