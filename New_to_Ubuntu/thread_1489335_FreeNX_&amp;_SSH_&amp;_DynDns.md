---
title: "FreeNX &amp; SSH &amp; DynDns"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by swan14 on 2010-05-21
Hi,

I want to us FreeNX so I can access my NAS (which runs Lucid) over the internet etc.

I feel I have followed all relevant documentation in setting up SSH, FreeNX and a DynDNS account - I also have ddclinet running to update my IP.

When I'm not sure if I'm using the correct credentials when trying to log on using the FreeNX client from NoMachine.

Should I be using the DynDns host name as my login? Or the user name and password of my NAS.

I'm just not sure how FreeNX, DynDns and SSH all come together to make this remote desktop stuff work.

Cheers,

Sam

---

### Post by Peter09 on 2010-05-21
FreeNx uses ssh as a 'carrier'. The first thing you need to do is see if you can login using ssh.
the format of the command is
 
```
ssh <your username>@<ipaddressof the target machine>
```
 
what happens when you do this?

---

### Post by swan14 on 2010-05-21
> **Peter09 said:**
> FreeNx uses ssh as a 'carrier'. The first thing you need to do is see if you can login using ssh.
the format of the command is
 
```
ssh <your username>@<ipaddressof the target machine>
```what happens when you do this?

Well I only have a windows machine as my main desktop.

I installed putty on this and it allowed me to SSH into my Ubuntu NAS.  So I guess SSH is working fine.

---

### Post by Peter09 on 2010-05-21
OK - and have you install FreeNX server, node and client on the NAS?

---

### Post by swan14 on 2010-05-21
> **Peter09 said:**
> OK - and have you install FreeNX server, node and client on the NAS?

I'm not sure what node is?

I didn't install client as the client will be my windows machine (or work machine etc..).  Should I still install client on my Ubuntu NAS?

I followed the instructions as per this link 

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX) 

under the Lucid 10.04 section.

Any ideas?

Thanks for the help by the way.

---

### Post by Peter09 on 2010-05-21
What happens when you start freenx on the client and attempt to login to the server?

---

### Post by swan14 on 2010-05-21
This is the details it gives when it fails to log in.

Firstly it says "the NX service is not available or the NX access was disabled on host 192.168.2.7"

then details

NX> 203 NXSSH running with pid: 3252
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.2.7 on port: 50000
NX> 202 Authenticating user: nx
NX> 204 Authentication failed.

I think I'm having a problem with authentication or my login credentials are wrong.

---

### Post by Peter09 on 2010-05-21
On the server NX requires a user called nx - can you check that you have a user of that name. It should have been generated when you installed the NX.

---

### Post by t0p on 2010-05-21
I'm afraid I can't answer your questions, as I have used FreeNX only over a local network.  But as SSH seems to be working fine between your local Windows machine and remote Linux box, perhaps one of [these solutions]("http://www.biac.duke.edu/library/documentation/xwin32/Security.html") may work?

Alternatively, something [here]("http://www.google.co.uk/#hl=en&newwindow=1&safe=off&q=using+freenx+with+dyndns&aq=f&aqi=&aql=&oq=&gs_rfai=&fp=15c416821a814cfb") may help.

---

### Post by swan14 on 2010-05-21
> **Peter09 said:**
> On the server NX requires a user called nx - can you check that you have a user of that name. It should have been generated when you installed the NX.

I entered "lastlog" into terminal and it listed a username called nx.  It has never logged in though.

---

### Post by Peter09 on 2010-05-21
I seem to remember that NX also generates a Group called - I cannot remeber - but I think you should recognise it. If I recall your user must be a memeber of that group as well.

---

### Post by swan14 on 2010-05-21
there was a "nx" group listed.  I checked my user name under the properties of this group.

Still nothing.

I might try re-installing FreeNX and see what happens

---

### Post by Peter09 on 2010-05-21
You may need to reboot the system to get that registered.
 
Are you still getting the same error?

---

### Post by swan14 on 2010-05-21
I did a reboot and changed a few things around on my router.

Still not connecting but this time a got a pop up message from FreeNX client asking about the security key. 

I might try and make a key through SSH and import it to FreeNX and see where that gets me.

---

### Post by Peter09 on 2010-05-21
Try logging in using ssh again, it may generate a key automatically for you. You should be able to configure ssh/Nx to not require a key.

---

