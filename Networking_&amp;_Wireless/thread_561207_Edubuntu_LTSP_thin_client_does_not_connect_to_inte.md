---
title: "Edubuntu LTSP thin client does not connect to internet"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by Dragonbite on 2007-09-27
**_Setup_**

[LIST=1]
[*]Edubuntu (LTSP server) installed on a Dell Optiplex with a Static IP address
[*]a 1GB unmanaged D-Link wired-only Switch (not router or hub) with 8 ports
[*]1 Dell Dimension 4100 that I can set up to PXE boot and hook into the Optiplex (server)
[*]a Sony Vaio (7 years old) which I cannot connect to server (but that is for another thread)
[*]Dial-up internet connection (via external modem) There is an internal modem, but Edubuntu does not recognize it
[*]I know next to nothing about Networking. If it is plugged in and doesn't work, I'm clueless. :(
[/LIST]

**_Situation_**

***If you read this thread earlier, the entire scenario has changed!** I had overwritten Edubuntu 7.04 with 6.06 LTS and after finding my CD had a corrupt file which kept it from installing, I managed to install it using a 2nd CD I had lying around. Also, when I installed 7.04 it did not install all of the programs; gCompris did not install for whatever reason.*

As you can tell I have an Edubuntu thin client (LTSP) server running which I can successfully connect to over the network.

I am using dial-up and am able to connect and use this connection to surf the web.

Unfortunately, when I ran Synaptic it could not update from any of the repositories.

My suspicion is that Synaptic is trying to use [eth0] connected to my switch which does not have internet access, instead of [ppp0].

I do have the modem checked as "default internet connection".

**_Questions_**

[LIST]
[*]Is there a way to force Synaptic/Apt-get and anything (everything) else to use the modem internet connection?
[/LIST]

Thank you for any advice, suggestions or ideas.  Like I said, I am new to networking.

~Drew

---

### Post by Dragonbite on 2007-10-02
Well, I came across ONE solution though it is far from ideal.

I turn off [eth0] in Network Manager and then connect via modem and all internet apps will use the modem.  Kinda sucks because it means nobody can be logged in at the time.

I haven't tried it yet, but I wonder if I dial-in to the internet and THEN turn on [eth0] if the web applications would go to the "first" connection or still default to [eth0]?

---

### Post by SpiritIsReality on 2007-11-07
howdy
I have a basic ltsp working that might help you with your setup.
[http://ubuntuforums.org/showthread.php?t=599166](http://ubuntuforums.org/showthread.php?t=599166)
trails

---

