---
title: "VPN connection at uni"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by Choad on 2006-11-02
my university has wireless and wired internet available, but it needs VPN or some such thing

not entirely sure about the details, but what would be the best thing to use for VPN. does the network manager support this automagically?

this is from the uni site:
> 
Setup Instructions

There are three steps to configure your computer to use the Roaming Internet Access service:

   1. Configure your network connection, this can be either a wired or wireless connection.
   2. Create your VPN connection, in order to access the Internet a VPN (Virtual Private Network) connection is needed.
   3. Configure your web browser, you need to configure your web browser so you are able to access the Internet.

detailed linux guide doesnt talk about ubuntu specifically, it says
> 
Create your VPN connection
A VPN (Virtual Private Network) connection is needed in order to securely
connect to the University network and access the Internet.
     Now Do This …
1. Go to pptpclient.sourceforge.net. Locate your Linux distribution on the
   left hand menu and follow the detailed instructions for Installing the PPP,
   PPTP and MPPE modules.
2. Continue to the Configure section of the instructions and enter the following
   details when prompted.
   • Name: University of Plymouth VPN.
   • Server: roaming.plymouth.ac.uk.
   • Username: Set this to your portal username.
   • Password: Set this to your portal password.
3. Select the DNS tab, and select the Automatic tick box.
4. Select the Encryption tab, select the Require Microsoft Point-to-Point
   Encryption.
5. Press the Add button. This will save the configuration for future use when
   you next open up the program.
6. Open the PPTP Client program, or run pptpconfig, as root.
7. Select University of Plymouth VPN.
8. Press the Start button. This will connect your computer to the roaming
   VPN server.
9. To Close the connections click the Stop button and close the PPTP Client
   program.


but obviously i dont want to do all that, there will be a .deb package for doing this shizzle for sure

any help?

---

### Post by marianom on 2006-11-02
There is, look for pptp-linux with Synaptic. Regarding pptconfig (the GUI) I really don't recall, I think you need to install it without deb.

See if this thread helps:
[http://www.ubuntuforums.org/showthread.php?t=236710](http://www.ubuntuforums.org/showthread.php?t=236710)

---

### Post by Choad on 2006-11-02
ok, i found one of those threads and done pptpconfig

its really ugly. is there no better way of doing this? i mean you cant even launch the thing from the main panel, you have to command-line it

not that i am opposed to the command line, i just feel there should be a nice gui way of doing this if ubuntu is to truly become *the* desktop OS

---

### Post by marianom on 2006-11-02
I did not actually try to modify that "feature" but I guess you can either grant some permission with chmod to the pptconfig file or modify the desktop conf file.

It can be done, for sure.

---

### Post by Choad on 2006-11-02
still, the app it's self is ugly as sin.

i feel this may be my call in to the open-source dev world

---

### Post by marianom on 2006-11-02
Yeap, it's not beautiful but, as a concept, I think it represents my mood when I need to use it (and i'm still trying to use it successfully): I totally hate the pptp protocol. 
If you can make it look prettier, I'm sure your help will be appreciated.

---

