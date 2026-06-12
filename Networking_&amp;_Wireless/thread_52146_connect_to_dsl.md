---
title: "connect to dsl"
date: 2005-07-26
forum: Networking &amp; Wireless
---

### Post by inet78 on 2005-07-26
I have a dsl connection to which I connect to through a router or switch. 

Regardless, in windows I connect to it through network connections -> connection using a broadband connection that requires a username and password. 

Then I input a username and password and just "connect" to the internet using the icon created in network connections.

I can't figure out how to do this in Ubuntu..thanks in advance.

---

### Post by ubuntp on 2005-07-26
I don't quite understand the question. Why do you have to enter username/password when you are behind a router? Shouldn't the router handle the authentication?

Try **pppoeconf** from the command line.

---

### Post by inet78 on 2005-07-26
No the router does not handle the user/password in this case. The people who setup the router wanted it that way each client logging in individouly. 

I tried pppoeconf earlier and it did not provide the means through which I can enter the user name and password. Any other ideas?

---

### Post by ubuntp on 2005-07-26
pppoeconf only works when it detects a direct connection to a dsl access point (from your provider) on the other line.

---

### Post by inet78 on 2005-07-26
I'm positive that its a dsl connection exists since I am connected to the internet on the same machine through a dsl ISP. (I'm running ubuntu through vmware). 

Every other client is also connected to that same dsl line and has to type in the main dsl account user/pass. 

I'm just describing how the network is setup in my case, I did not design it, and how I log onto it through windows. All I need is a linux equivalent of doing that.

---

### Post by inet78 on 2005-07-27
anybody? I really need to get this working...

I thought linux was designed for being able to run in any network and the way my network is setup isn't that complicated since windows has an option for exactly this type of user/password situation. 

I'm willing to try any ideas.

---

### Post by gruepig on 2005-07-27
One possibility would be to connect the Ubuntu box  directly to the DSL modem (bypassing the router) so that you can use pppoeconf.  I'm not sure if this would work.

Another would be to edit the files /etc/ppp/pap-secrets and /etc/ppp/peers/* directly.  pap-secrets should contain something like:  
```
<username>@<provider> * <password>
```
The ppp config in peers/ should contain something like: 
```
user "<username>@<provider>"
```

I don't use DSL, but maybe someone else could share their config options.

---

### Post by inet78 on 2005-07-27
I can't physically touch the router or the modem..it's at my work. 

What do you mean by <provider>. Does it even matter what I enter as the provider?

---

### Post by varunus on 2005-07-27
What you are doing in windows is using something called PPPoE to have a "broadband connection with a password."  The "pppoeconf" should have asked you for a username and password to connect to your network from what I can see about it.  What happened exactly when you ran it?  Did you run it with "sudo pppoeconf" or just "pppoeconf"?  Try it with sudo...

---

