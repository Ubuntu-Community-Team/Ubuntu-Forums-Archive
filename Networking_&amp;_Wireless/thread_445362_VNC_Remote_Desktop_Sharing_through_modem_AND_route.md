---
title: "VNC Remote Desktop Sharing through modem AND router (double NAT)?"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by willnapier on 2007-05-15
Hi, sorry for the length of this post, but I want to be clear about the problem.

**Ultimate aim:**  I want to remotely share my mother's kubuntu feisty desktop via the internet, from my kubuntu feisty desktop.

**What I can already do:** I can connect to a friend's kubuntu feisty desktop with no problem, using her ip address but attaching :5900 to the end, the port that VNC uses. I had initial problems getting this friend to share my desktop, but worked out that the 'create invitation' in krfb offers the internal ip and that I had to find my external ip and ask her to tag on :5900. this worked.

**Problem:** However, I can't connect to my mother's machine using this strategy. When I call up Krdc and enter her external, static ip, plus the :5900 (having set things up in Krdc so that she accepts uninvited connections temporarily), I get an error message saying that the connection failed because there was no server running that the given address and port.

**Network hardware:** I believe that this is because my mother has an adsl modem (Zoom X3), which connects into a wireless router (Linksys), ie I apparently have 'double NAT'. In the router, which (from her PC) I could access with a 168.192.1.1 internal ip, I set up port forwarding for VNC, specifying :5900 (which is what worked for me on my router).

**Possible solution:** However I realise I have to do something with the settings on the zoom modem (which she can reach with 10.0.0.2 from her PC). Someone suggested getting rid of NAT, and dchp, and manually specifying the ip (although I'm not totally clear which ip). Another option that occurred to me was to go into the modem setup and enable 'bridge'. This didn't seem to work. So now I read in the Zoom X3 modem's manual

[http://www.zoom.com/techsupport/adsl/adsl_5560.shtml]("http://www.zoom.com/techsupport/adsl/adsl_5560.shtml")

that they call 'port-forwarding'  a 'virtual server'. They give clear examples of how to do this, but step five (enter the host ip address) is not clear to me (their instructions are for Windows). It tells me that I can obtain this address in the LAN settings. It says that I'll see (I can't now since I need to talk my mother through this on the phone) the defined starting and ending ip address range "for example, 10.0.0.3 and 10.0.0.14. It then says "Your host should be a static IP address outside of this range - say, 10.0.0.15"


**Question 1: ** The zoom manual then explains how to set this static ip address in Windows. How can I do this in K/ubuntu? (It says to highlight the NIC card's TCP/IP entry, click properties, and then enter specified ip address, subnet mask, default gateway, and preferred dns server.

**Question 2:** Once this is done, will it mean that I can do the same as when I connect to my friend's computer (the external ip, plus :5900) ?

As you will realise, my knowledge in this area is growing but not adequate to the task. I greatly appreciate any help.

With thanks, Will

---

