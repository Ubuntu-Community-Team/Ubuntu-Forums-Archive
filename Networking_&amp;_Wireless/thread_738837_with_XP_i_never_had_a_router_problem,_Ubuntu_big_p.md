---
title: "with XP i never had a router problem, Ubuntu big problem with amule"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by MeTylerDurden on 2008-03-29
With xp it was always (would you like to allow this program accesss)  and you check yes...... with Ubuntu there is nothing  - like some1 forgtot to do anything about that ..  I install amule and whamo i am having firewall issues and have looked at 20 threads and searched sites and everything and no1 has the simple answer just a general (go that way) this is pointless...     I dont know how to open a port on myy router for amule.    Ubuntu dropped the ball  here..  :popcorn:

 the liberator who destroyed my property has realigned my perception.

---

### Post by IsawSp4rks on 2008-03-29
Actually you dropped the ball, no offense intended.  You installed firestarter and know nothing at all about firewalls and routing.  Simply put, start firestarter (which is just a pretty front end for Linux IPtables - the linux kernel firewall) and then turn it off.  No, don't close the Firestarter window, but actually turn the firewall off by pressing the STOP button in the Firestarter window.  Restart Amule and presto magico it'll work.

---

### Post by MeTylerDurden on 2008-03-29
ahh, and that takes care of the router 2.. nice... :popcorn:    where were you 6 hours ago!

---

### Post by MeTylerDurden on 2008-03-29
i dont really like amule either
                   i cant even play the songs i download they just go to shared files and sit there.. did any1 ever dream maybe i want to put em in a folder for access to play them .. durrr.    or put em to desktop  
  or just push play to listen ..             no  there is some special secroet code out there or password like allah shazam,      i am just stupid cuz i didnt write the program or go to college where there was 100  people to lay down the facts :popcorn:

              you failed me Renfield now you will pay the penalty

---

### Post by Hallvor on 2008-03-29
Try 
```
sudo iptables -A INPUT -p tcp --dport 4711 -j ACCEPT
```

to open tcp port 4711, and

```
sudo iptables -A INPUT -p udp --dport 4712 -j ACCEPT
```

to open udp port 4712. (To close the ports again, use the same parameters, except replace «ACCEPT» with «DROP».)

Perhaps Frostwire would be better for you if you like to download smaller files. aMule is optimized for sharing large files.

---

### Post by lesergi on 2008-03-29
Hello,

Maybe the problem is caused by closed router ports. Please, I need the router model to help you in order to open the ports.

Regards.

---

### Post by MeTylerDurden on 2008-03-29
The router is linksys NR041 router 4 port, sorry for the wait on the reply ( I had to get some required sleep)  :popcorn:

the Liberator who destroyed my property has realigned my perception

---

### Post by MeTylerDurden on 2008-03-29
> **lesergi said:**
> Hello,

Maybe the problem is caused by closed router ports. Please, I need the router model to help you in order to open the ports.

Regards.

the router is a Linksys NR041 4 port ,  sorry about reply delay .:popcorn:

 the Liberator who has destroyed my property has realigned my perception

---

### Post by Prefix100 on 2008-03-29
> **lesergi said:**
> Hello,

Maybe the problem is caused by closed router ports. Please, I need the router model to help you in order to open the ports.

Regards.

+1

It sounds like port forwarding from the router, rather than a problem with Ubuntu.

Find your routers local ip and type it into firefox, then type nothing for username and 'admin' for the password.

Tell me if that logs you into the router.

---

To find your routers ip goto your connection information in network manager, there should be a ip starting with 192.168.x.x ( where x is any number), labeled 'Defualt Gateway' or something.

Typical router address' are 192.168.0.1 and 192.168.1.1

---

### Post by lesergi on 2008-03-29
Hi,

You can get a manual of your router here: [ftp://ftp.networkeverywhere.com/manuals/nr041_ug.pdf](ftp://ftp.networkeverywhere.com/manuals/nr041_ug.pdf)

Anyway, you must open [http://192.168.1.1](http://192.168.1.1) and when you get a login screen, you must type "admin" in password field, user you'll let blank. Go to "Advanced Setup" tab and then click on " Forwarding ", subtab under " Forwarding ".Then click on " "Port Triggering" on this page.Then under "Trigger Port Range" and " Incoming Port Range" enter the required port number, for example the port used by aMule (see it in aMule config).

Regards!

---

### Post by MeTylerDurden on 2008-03-29
> **Prefix100 said:**
> +1

It sounds like port forwarding from the router, rather than a problem with Ubuntu.

Find your routers local ip and type it into firefox, then type nothing for username and 'admin' for the password.

Tell me if that logs you into the router.

---

To find your routers ip goto your connection information in network manager, there should be a ip starting with 192.168.x.x ( where x is any number), labeled 'Defualt Gateway' or something.

Typical router address' are 192.168.0.1 and 192.168.1.1

  ok  i have accessed the router with [http://192.168.1.1](http://192.168.1.1)  ,  this is a huge step  ..  i did make it to the administration / password before , but was not sure what to enter .      :popcorn:


the Liberator who destroyed my property has realigned my perception

---

### Post by lesergi on 2008-03-29
I've posted it, read it please.

Bye!

---

### Post by MeTylerDurden on 2008-03-29
Thanks Lesergi,   I will give that a try.!!     

Only after disaster can we be resurrected.

---

### Post by IsawSp4rks on 2008-03-29
> **lesergi said:**
> Hi,

You can get a manual of your router here: [ftp://ftp.networkeverywhere.com/manuals/nr041_ug.pdf](ftp://ftp.networkeverywhere.com/manuals/nr041_ug.pdf)

Anyway, you must open [http://192.168.1.1](http://192.168.1.1) and when you get a login screen, you must type "admin" in password field, user you'll let blank. Go to "Advanced Setup" tab and then click on " Forwarding ", subtab under " Forwarding ".Then click on " "Port Triggering" on this page.Then under "Trigger Port Range" and " Incoming Port Range" enter the required port number, for example the port used by aMule (see it in aMule config).

Regards!


I don't think any of that's necessary as the same manual points out that the router supports UPNP (Universal Plug aNd Play), which will automatically open and close the required ports as necessary - a much simpler and safer security practice in my view.

Tyler : If you're getting a consistent LowID, you should probably just remove your current amule 2.1.3 via synaptic and then install one the later 2.2.0 SVN based compiles listed here:-

[http://www.getdeb.net/search.php?keywords=amule](http://www.getdeb.net/search.php?keywords=amule)

The reason being that 2.1.3 doesn't support UPNP, but the later 2.2.0 releases do:-

[http://www.amule.org/wiki/index.php/FAQ_aMule#Does_aMule_support_Universal_Plug_and_Play_.28UPnP.29.3F](http://www.amule.org/wiki/index.php/FAQ_aMule#Does_aMule_support_Universal_Plug_and_Play_.28UPnP.29.3F)

Hope that clears things up and makes them simpler for you.

[SIZE="1"]
I personally do not recommend forwarding ports on a router when UPNP (or NAT PMP traversal for that matter) is available when using a secure OS like Linux.  Forwarding ports is generally bad practice for inexperienced users as it forces the router to leave ports open to attack.  Yes, it's a little more secure with triggered services but that still can leave them open on the WAN side, especially if an app crashes, as they tend to do.[/SIZE]

---

### Post by MeTylerDurden on 2008-03-30
> **IsawSp4rks said:**
> I don't think any of that's necessary as the same manual points out that the router supports UPNP (Universal Plug aNd Play), which will automatically open and close the required ports as necessary - a much simpler and safer security practice in my view.

Tyler : If you're getting a consistent LowID, you should probably just remove your current amule 2.1.3 via synaptic and then install one the later 2.2.0 SVN based compiles listed here:-

[http://www.getdeb.net/search.php?keywords=amule](http://www.getdeb.net/search.php?keywords=amule)

The reason being that 2.1.3 doesn't support UPNP, but the later 2.2.0 releases do:-

[http://www.amule.org/wiki/index.php/FAQ_aMule#Does_aMule_support_Universal_Plug_and_Play_.28UPnP.29.3F](http://www.amule.org/wiki/index.php/FAQ_aMule#Does_aMule_support_Universal_Plug_and_Play_.28UPnP.29.3F)

Hope that clears things up and makes them simpler for you.

[SIZE="1"]
I personally do not recommend forwarding ports on a router when UPNP (or NAT PMP traversal for that matter) is available when using a secure OS like Linux.  Forwarding ports is generally bad practice for inexperienced users as it forces the router to leave ports open to attack.  Yes, it's a little more secure with triggered services but that still can leave them open on the WAN side, especially if an app crashes, as they tend to do.[/SIZE]

             Allright  , /ty  
    much appreciated:  uninstalled  and reset all the ports to original settings.   (do you know when the newer version 2.2.0 will be available in synaptic manager.   (should be any day, huh)

  :popcorn:
 the Liberator  who  destroyed my property has realigned my perception

---

### Post by IsawSp4rks on 2008-03-30
Well Ubuntu generally follows the release schedule of associated apps so until emule actually make a release version of 2.2.0 (still in beta currently) then Ubuntu probably won't include it, unless the current SVNs prove stable and offer security fixes that people need.

I'm just guessing but it seems logical.

---

