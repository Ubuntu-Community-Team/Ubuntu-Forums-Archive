---
title: "Any solutions to pppoeconf issues?"
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by EminNew on 2006-08-07
(Please mind that I'm just a few days into Linux.)

I noticed my problems were closely duplicated by a bug post at bugs.debian.org

"...this bug is concerned to version 2.4.4b1-1
of the ppp package.  I just grabbed the old package from snapshot.debian.net
to get my network back.

The problem: In the beginn of this week I updated to the latest testing which
included an update of ppp.  After I tried to establish the next pppoe
(ADSL) connection this failed.  I verified the logfiles
(grep ppp /var/log/syslog) and compared these with the output of the
old ppp version but found nor relevant difference here (except the
version number of the pppd daemon).

I tried to reconfigure my setup using pppoeconf which worked for the
first time - but failed immediately after a poff; pon dsl-provider
sequence.  I was not able to get a connection until I rebooted the
next day.  At this day I've got some kind of random connections:  I tried
pon several times and sometimes this worked.  When I switched back to the
old version (see version number in bug report) this also did not worked
out of the box - another pppoeconf was necessary.  I do not really
understand what this script really does.  I never changed my input to
the script and the /etc/ppp directory did not changed after a call.
But now I got my ppp working again - well mostly.  Even when I switched
back to the former ppp version the connection can not be established
relieably after every pon.   ..."


The whole report can be found here:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=347958](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=347958)


My connection worked nicely after the first pppoeconf upon fresh Ubuntu installation, but not after reboot, and so far I'm unable to connect. This is the second time this is happening (I reinstalled Ubuntu today). 

Here's what I get from a plog:

Aug  7 10:13:34 Upstart pppd[5931]: Plugin rp-pppoe.so loaded.
Aug  7 10:13:34 Upstart pppd[5933]: pppd 2.4.4b1 started by emin, uid 1000
Aug  7 10:13:34 Upstart pppd[5933]: PPP session is 2212
Aug  7 10:13:34 Upstart pppd[5933]: Using interface ppp1
Aug  7 10:13:34 Upstart pppd[5933]: Connect: ppp1 <--> eth0
Aug  7 10:13:37 Upstart pppd[5933]: Remote message: Access Denied.^J
Aug  7 10:13:37 Upstart pppd[5933]: PAP authentication failed
Aug  7 10:13:37 Upstart pppd[5933]: Connection terminated.

I'm considering trying to install other versions of ppp and pppoeconf, but I would like to hear suggestions from experienced users first.

---

### Post by EminNew on 2006-08-07
Whu, nuthin'?

---

### Post by EminNew on 2006-08-07
Well,maybe I succeeded. Here's what I did:

I noticed in Synaptic that pppconfig is used with PAP authorization, which is what was failing according to plog output.

So I ran it, got discouraged when I realized it was probably meant to be used with dial-up modems, but filled out entries anyway - the login and password - selected dynamic DNS, didn't change default modem speed, and left out dial-up phone number completely (it still reads "enter_phone_number_blah"). Saved settings and tried pon dsl-provider.

My ADSL modem connected right away, at full speed.

Typed plog:

Aug  8 01:26:42 Upstart pppd[5482]: Connect: ppp1 <--> eth0
Aug  8 01:26:44 Upstart pppd[5482]: Remote message: Access Accepted.^J
Aug  8 01:26:44 Upstart pppd[5482]: PAP authentication succeeded
Aug  8 01:26:44 Upstart pppd[5482]: peer from calling number 00:90:1A:40:C5:FD authorized
Aug  8 01:26:44 Upstart pppd[5482]: not replacing existing default route through ppp0
Aug  8 01:26:44 Upstart pppd[5482]: Cannot determine ethernet address for proxy ARP
Aug  8 01:26:44 Upstart pppd[5482]: local  IP address xxxxxxxxxxxx
Aug  8 01:26:44 Upstart pppd[5482]: remote IP address xxxxxxxxxxxx
Aug  8 01:26:44 Upstart pppd[5482]: primary   DNS address xxxxxxxxxxxx
Aug  8 01:26:44 Upstart pppd[5482]: secondary DNS address xxxxxxxxxxxx

I left out adresses, 'cause I'm not that knowledgable to know whether it safe to post them here.

I said "maybe" I did it. Part of the problem was that the connection would sometimes even work for no apparent reason, and maybe this success has nothing to do with my actions. I'll have to test it some more. 

Hope it works, I've seen other people with the same problem and this would be great for them, 'cause it so simple to do.

---

### Post by EminNew on 2006-08-08
I'll just carry on debating with myself.

That was not the solution after all, as I still can't connect regularly.

To connect, I have to keep pon-ing.

Not sure if it matters, I assigned a static IP to my eth0 device.

---

### Post by EminNew on 2006-12-19
All this was long time ago, I'm using Edgy now, but still the same thing happened again.

I managed to solve it by:

1. Answering "No" when pppoeconf asks should it connect automatically on boot.

2. Poffing and poning againg if connection attempt fails (this rarely happens).

3. If step 2 does not work - deleting DNS entries in Networking, and then connecting.

---

### Post by Aleph42 on 2007-03-03
Thanx eminew. I had the same problem, so i'll try that. About what you said before, to me (with edgy) it is impossible to set the dial-up password without a phone number in the gui ("ok" button unclickable). Anyway, thanks for keeping on posting alone!

---

### Post by Aleph42 on 2007-03-03
I tested it, but didn't work. To sum up: I got my dsl to work with pppoeconf, then after reboot it didn't anymore, even when rerunning pppoeconf. I tried a number of other things (including some tweaking to /etc/network/interfaces and /etc/rc.local, as seen on some forums) but none worked (even with reboots and poff/pon). haven't had internet since that reboot (but it works with windows). I have a Dell Inspiron 9400 with Broadcom 440x 10/100 Integrated controller, Ubuntu edgy 6.10.
plog output:
Mar  3 10:05:49 daito pppd[5132]: PAP authentication failed
Mar  3 10:05:49 daito pppd[5132]: Connection terminated.
Mar  3 10:05:49 daito pppd[3720]: Connection terminated.
Mar  3 10:05:49 daito pppd[3720]: Modem hangup
Mar  3 10:05:49 daito pppd[3720]: Exit.
Mar  3 10:06:19 daito pppd[5132]: PPP session is 6535
Mar  3 10:06:19 daito pppd[5132]: Using interface ppp0
Mar  3 10:06:19 daito pppd[5132]: Connect: ppp0 <--> eth0
Mar  3 10:06:20 daito pppd[5132]: PAP authentication failed
Mar  3 10:06:20 daito pppd[5132]: Connection terminated.

---

### Post by Aleph42 on 2007-03-03
Ok, the fix is simple (finding it was trickier ;)

The problem was that the package "pppoe" is needed for pppoeconf, but is not automaticaly installed with it (someone on a bug report was requesting it, so maybe it will be fixed in the next ubuntus).

Now of course if you dont have internet you can't install this package with "sudo apt-get install pppoe", but you can download it using this link:[http://fr.archive.ubuntu.com/ubuntu/pool/universe/r/rp-pppoe/pppoe_3.8-1_i386.deb]("http://fr.archive.ubuntu.com/ubuntu/pool/universe/r/rp-pppoe/pppoe_3.8-1_i386.deb")
(see note below if this link doesn't work).

then put it on your ubunut desktop somehow (usb drive for exemple) and double-click it. It will install the package. Now rerun pppoeconf, after that it works.
All in all it was just a stupid mistake when setting the dependencies.

NOTE:

--If the link doesn't work:
actually, to get this link I ran synaptic (System -> Administration-Synaptic package manager), looked for "pppoe" (with "search") then tried to download it while offline. Of course it was hoplessly failing to do so, but when I pressed "cancel" I got this link in the error message. Then copy pasted it in a file and downloaded it from a connected computer.

--if it doesn't work:
I also installed the "pppoestatus" package in the same way (link:[http://fr.archive.ubuntu.com/ubuntu/pool/universe/r/rp-pppoe/pppoe_3.8-1_i386.deb]("http://fr.archive.ubuntu.com/ubuntu/pool/universe/r/rp-pppoe/pppoe_3.8-1_i386.deb"))
I dont think it was necessary, but you can give it a shot.

I hope I mannaged to make this understandable to a new user. This kind of thing can really kill your motivation to switch.

---

### Post by EminNew on 2007-03-18
I have a dual boot Ubuntu/XP machine.

I was able to determine that Ubuntu will not connect if I 

      - put XP in hybernation  

and then login to Ubuntu,

When I shutdown Ubuntu, login to XP and shut it down normally, I'll be able to connect with Ubuntu.

Not being an expert, I assume XP does something to my broadband modem which makes Ubuntu unable to detect and/or use it.

Looks to me as if Windows XP "locks" the modem,  and putting it in hybernation doesn't "unlock" it.

Would be nice if someone knowledgeable shed some light on what really happens here.

P.S.

THIS was the main reason I sometimes wasn't able to connect with Ubuntu.

So if you dual boot and hybernate your XP, and are having trouble connecting Ubuntu - try testing for this behaviour.

Hope this helps some of you guys out there searching the net like maniacs for an answer.

---

