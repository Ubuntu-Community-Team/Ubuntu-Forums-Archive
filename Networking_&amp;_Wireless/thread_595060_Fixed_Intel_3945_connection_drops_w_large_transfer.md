---
title: "Fixed Intel 3945 connection drops w/ large transfers"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by specker on 2007-10-28
Since first switching to Gutsy in early August I have had a persistent problem with my network connection dropping while doing large file transfers over NFS or HTTP.  I have found that switching to the iwl3945 instead of ipw3945 has solved all of my issues.  I can only speak to it working on my system which is the Dell 1420 (Intel 3945abg network adapter).  Here is how I blacklisted ipw3945 and enabled iwl3945 at boot.

1. Create a text file called ```
blacklist-ipw3945
```and add ```
blacklist ipw3945
```Save and exit

2. Copy blacklist-ipw3945 to /etc/modprobe.d/```
sudo cp blacklist-ipw3945 /etc/modprobe.d/
```

3. Add iwl3945 to /etc/modules```
sudo gedit /etc/modules
```and add ```
iwl3945
```Save and exit.

4. Restart and once connected to your wireless network right-click the network-manager applet and choose "Connection Information".  Verify the driver is iwl3945.

This solved all my issues, but again I can't vouch for it working on anyone elses system.  If it doesn't simply remove blacklist-ipw3945 from /etc/modprobe.d/ and iwl3945 from /etc/modules.

If you want to test to see if iwl3945 works before making it permanent check[ this thread]("http://ubuntuforums.org/showthread.php?t=593728&highlight=iwl3945").

---

### Post by kuja on 2007-11-01
> **specker said:**
> Since first switching to Gutsy in early August I have had a persistent problem with my network connection dropping while doing large file transfers over NFS or HTTP.  I have found that switching to the iwl3945 instead of ipw3945 has solved all of my issues.  I can only speak to it working on my system which is the Dell 1420 (Intel 3945abg network adapter).  Here is how I blacklisted ipw3945 and enabled iwl3945 at boot.

1. Create a text file called ```
blacklist-ipw3945
```and add ```
blacklist ipw3945
```Save and exit

2. Copy blacklist-ipw3945 to /etc/modprobe.d/```
sudo cp blacklist-ipw3945 /etc/modprobe.d/
```

3. Add iwl3945 to /etc/modules```
sudo gedit /etc/modules
```and add ```
iwl3945
```Save and exit.

4. Restart and once connected to your wireless network right-click the network-manager applet and choose "Connection Information".  Verify the driver is iwl3945.

This solved all my issues, but again I can't vouch for it working on anyone elses system.  If it doesn't simply remove blacklist-ipw3945 from /etc/modprobe.d/ and iwl3945 from /etc/modules.

If you want to test to see if iwl3945 works before making it permanent check[ this thread]("http://ubuntuforums.org/showthread.php?t=593728&highlight=iwl3945").

Hurrah! I don't know why it just now happened today of all times, but I started running into exactly the same problem. Thanks for the enlightening post, and it's a good thing my google-fu was strong enough to find it, seeing as it seems to have worked for me (transferred 1.5gb over sftp without dropping the connection) Here, I had spent half the bloody night (it's now 5:16am) convinced it was my router that was causing the problem. Oh well, I'll be back later, I need to go find something to take out my stress on ...

At any rate, it works very well, we/you/someone needs to get this tidbit of magic a spotlight space on the dell 1420n wiki.

---

### Post by specker on 2007-11-01
Thanks.  It seems like a lot of people are having this problem but it is hard to know exactly whats causing the problem.  For a long time I thought it was network-manager.  I couldn't find any threads that specifically spelled out a solution.  So I figured I better put out what worked for me.   I've been dealing with this for two months before I tried the iwl3945.  Seems to work real solid.

---

### Post by daveyiv on 2007-11-01
did your signal strength drop significantly when you did switched to iwl3945, I just gave it a shot and with iwp3945 I was getting around 97% signal, now with iwl3945 I am getting around 77%

---

### Post by specker on 2007-11-02
> **daveyiv said:**
> did your signal strength drop significantly when you did switched to iwl3945, I just gave it a shot and with iwp3945 I was getting around 97% signal, now with iwl3945 I am getting around 77%

Yes it did.  I did not even notice until you pointed it out.  What was a 90+% signal is now showing about 79%.  Also, at least on the Dell I'm running, the wifi activity light doesn't work.  I'm just happy I can transfer over NFS again though.

---

### Post by kuja on 2007-11-02
I've not noticed any loss of signal strength here, it's holding about the same for me.

Have either of you had any trouble getting reconected after resuming from suspend? This is really troublesome because I had to reboot to get online to post this message :( 

I made sure the module was loaded and it was, I'm suspecting knetworkmanager was just being a piece of crap ... but yeah. Kind of tedious for me to reboot, seeing as I have to punch in 7 or 8 passwords.

---

### Post by Jeffrey04 on 2007-11-08
the driver works perfectly if i am using my laptop at the same level as the router but if I move my laptop to another level, then the connection became unstable..... is there any way to update the driver version?

for those who are getting an interface with the name wlan0_rename, you may comment out the line which describes eth1 interface in /etc/udev/rules.d/70-persistent-net.rules

then reboot to get a proper name (wlan0) for the interface.

Reference: 
[http://ubuntuforums.org/showpost.php?p=3562827&postcount=5]("http://ubuntuforums.org/showpost.php?p=3562827&postcount=5")

---

### Post by Alte on 2007-11-15
It seems to work fine on my Acer Travelmate 6291! Thanks m8! U :guitar:

---

### Post by chrisrx on 2007-11-15
This just seems to give me a completely different problem.  I've switched to the iwl3945 driver and now the network lasts a lot longer before disconnecting when I'm downloading.
The thing is that with the old driver I used to be able to fix this by flicking the killswitch on and off, even though the network would drop again a few minutes later.
But now when the network fails I can't reconnect at all until I reset the computer.

---

### Post by kuja on 2007-11-16
Odd, though perhaps it may be more isolated than you think chrisrx. I've been keeping connected for days at a time without any trouble at all.

---

### Post by specker on 2007-11-16
> **kuja said:**
> Odd, though perhaps it may be more isolated than you think chrisrx. I've been keeping connected for days at a time without any trouble at all.
Me too.  I haven't had any disconnects since switching.

---

### Post by jdelaros1 on 2007-11-16
Issue documented on Dell Ubuntu Wiki:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues)

---

### Post by tpischke on 2007-11-16
I had this problem, and it went away with iwl3945.  It seems to happen only with intensive high-volume data transfer.  At any rate, can't imagine this wouldn't affect all stock 1420n laptops equally, so I'd recommend the iwl3945 driver to anyone who dislikes forcibly rebooting their computer when trying to transfer large files at high speed.

---

### Post by specker on 2007-11-16
Excellent to see it documented on Dell's wiki.  Might want to mention that the wifi activity light on the 1420n show zero activity when using the iwl3945.  Not a big deal but could raise some questions from people.

---

### Post by seraphim on 2007-11-17
thank you!
seems to work great with my hp dv9560eg!
i already thought i'd have to wait for the next version of ubuntu, but now everything is up and running! great job, thanks again! *happy*

---

### Post by tpischke on 2007-11-30
My only problem with the iwl3945 driver is that it doesn't work after suspend/resume.  Still hoping to stumble across a solution.  Otherwise iwl3945 works perfectly.  Unfortunately, suspend and hibernate are useless with this driver though, since it seems hopelessly dead after restart.

---

### Post by heldal on 2007-12-03
I've seen the same problem on an Acer Aspire with a 3945ABG interface. Switching to the iwl3945-driver as described above seemed to improve things slightly, but the system would still freeze occasionally. What seemed to do the trick for me was to enable hardware encryption for the iwl3945 module. If you have this problem and you use encryption you might want to try this:

```
sudo gedit etc/modprobe.d/iwl3945

insert the line:

  options iwl3945 hwcrypto=1
```

Then reboot.

My test system used to lock up after transferring anything from a few MB up to one or 2 GB. With HW encryption enabled I just completed a transfer of more than 40GB with no problems.

---

### Post by Cirrocco on 2007-12-06
Specker, you're awesome.

after loading this driver:
-my wifi connects almost immediately after logon.
-is less flaky
-signal strength is improved

Thank you VERY much!

/Dell Latitude D830
/Gutsy x64

---

### Post by mblind on 2007-12-07
this new driver helps a little.. But now I can't connect to WEP or WPA access points.. Only wi-fi that is password free..

So I bought the GIGABYTE WI01GT miniPCI EXPRESS Wireless card - Atheros Super G

And now I want to totally UNINSTALL the 3945 drivers.  How would I do that please.

thanks so much

---

### Post by R. McC on 2007-12-25
> **chrisrx said:**
> This just seems to give me a completely different problem.  I've switched to the iwl3945 driver and now the network lasts a lot longer before disconnecting when I'm downloading.
The thing is that with the old driver I used to be able to fix this by flicking the killswitch on and off, even though the network would drop again a few minutes later.
But now when the network fails I can't reconnect at all until I reset the computer.
This sounds very similar to the issue a number of people (including me!) have been having, as outlined [here](http://ubuntuforums.org/showthread.php?t=625916).  No permanent fix as of yet, but we have found a workaround that avoids the need to restart problem.

---

### Post by kuja on 2007-12-26
Reporting back after a long while using the iwl3945 driver. It seems that sometimes after having been connected for a long while the connection speed drops off the grid, down to like a measly 100kbs ( as evinced through LAN transfers, not internet stuffs). Switching to Offline mode and back to Online mode seems to be enough to correct it, fortunately, but it's still annoying.

Another thing, does anybody notice any issues with it and (K)NetworkManager scanning? It seems to only scan once and if I want to rescan for other networks and/or check the current signal strength I have to "sudo iwlist wlan0 scanning". Is there any way to get it to scan intermittently?

---

### Post by specker on 2008-01-13
I only have one  issue that is still given me fits  after using iwl3945 for a bit now and that involves automatically mounting shared NFS directories.   The ipw3945 would mount NFS shares upon connection.  The iwl3945 doesn't do this, for me at least. Anyone know of a workaround.

---

### Post by prankst3r on 2008-01-24
> **kuja said:**
> Reporting back after a long while using the iwl3945 driver. It seems that sometimes after having been connected for a long while the connection speed drops off the grid, down to like a measly 100kbs ( as evinced through LAN transfers, not internet stuffs). Switching to Offline mode and back to Online mode seems to be enough to correct it, fortunately, but it's still annoying.


I have continual issues with slowness when using either the iwl or iwp drivers. Has anyone made any progress on this issue?

---

### Post by seaq on 2008-02-10
i'm having suspend / hibernate problems after using the iwl3945 anyone else seeing this??

---

### Post by Mr_Congeniality on 2008-04-30
Works like a charm. 

Thanks specker!

---

