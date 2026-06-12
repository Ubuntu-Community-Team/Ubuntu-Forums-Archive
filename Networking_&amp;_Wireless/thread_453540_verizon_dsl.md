---
title: "verizon dsl"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by cong06 on 2007-05-24
I'm trying to connect my old laptop to Verizon's DSL.

Our family has a network set up, a DSL router(Westell 2200) sends the connection into a Linksys Router. which my laptop is hooked up to.

I followed through this thread:
[http://ubuntuforums.org/showthread.php?t=368896](http://ubuntuforums.org/showthread.php?t=368896)
and got a bit confused, but mostly changed a bunch of settings that didn't seem to do much.

The biggest question I have, I guess, is that my windows computer needs a username and password to get on the verizon DSL connection. Where do I set that up for my ubuntu computer?

---

### Post by cong06 on 2007-05-24
Well, I have the computer connected to the home network. (I guess that's the easy part?)

But I still can't figure out how to configure it for the verizon DSL setup.
At college, I simply had to plug it in, and the T1 Connection was automatic. But I've always had trouble after I bring my compuer home. Especially since my parents have a password for their internet connection.

With ubuntu, I don't even know where to begin. Like I said in the last post, the thread was very confusing, and while I may have learned a bit, I'm not sure what they were doing.

---

### Post by sikdogg on 2007-05-24
You could configure your Linksys router to connect to DSL using the PPPOE username/password and it will eliminate the need to configure it on all your workstations. Doing this would make connecting to the Internet just like at college...

---

### Post by str8line on 2007-08-23
The problem is that the Westell 2200 needs to be set in Bridge mode to function with the Linksys router.  There are a couple of options for this that are not OS specific.  I will include the instructions here but you can also print out a set of instructions from dslstart.verizon.net in the Help link.

To configure the modem in pass through, make a direct connection from the modem to the pc.  Open a browser....navigate to 192.168.1.1...when prompted for a username and password, the default is admin for username password is password.  Once logged into the Westell GUI, click on Configuration->VC Configuration.....change the VC1 Config from PPPoE to Bridge...this will change the Mode and give option  of "Routed Bridge" under Bridge Settings....set this to Bridge and click Set VC.....this will reset the modem.

When the modem returns to the Home Page again click on Configuration and choose DHCP Configuration....turn the Private LAN to off and click on Save....the modem is now in passthrough mode.

Close the browser and connect the router (unplug ethernet cable from modem and connect to port 1 of router - then connect cable from the Internet Port of the Linksys to the Westell modem).  Again open a browser and navigate to 192.168.1.1.  Default for the Linksys router is username (left blank) and Password of admin.  In the Linksys GUI set Internet Connection type from Obtain IP automatcally to PPPoE and add your DSL username and password....set the MTU settings to 1492 and click Apply.

The router will now do the heavy lifting of your internet connection and you will be ready to go.

---

