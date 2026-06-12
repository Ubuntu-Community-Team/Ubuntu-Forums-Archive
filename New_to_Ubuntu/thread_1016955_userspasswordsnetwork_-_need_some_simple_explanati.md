---
title: "users/passwords/network - need some simple explanations"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by jimmy the saint on 2008-12-20
I have been using Ubuntu for a couple years now and I have enjoyed learning so much.  I still feel that what I do know is just a tiny speck of what there is to know.  One issue that I am still a little unsure of relates to users on a network.  I am not a network admin (just a home admin).  Can someone please clarify this for me in plain english?  

***NOTE** I have one linux server. I also have a main box, and several laptops, pda's etc which I will collectively call PCs in the house.  All (that matter) run linux.  ***/NOTE***

1)  All of the PCs have different users.  In other words one has "user1" antoher "user2" and so on.  This makes it difficult when accessing each other over ssh via nautilus, for example, because ownership issues crop up.  Should they all have the same admin user?  should this user have the same password on all machines?  I am still getting used to networking concepts so I am not sure what the security/usability implications are.  Also, should I use this user/password for things like SSH,FTP,MYSQL, and other services, or should they have different users?  Which services should have unique users?  

2)  The server does a lot (daap, smb for XBMX, deluged etc).  It is a refurb Dell with a dual core proc, 1gig ram and plenty of storage.  I am behind a router (and the server is behind a wireless bridge).  I have been reluctant to mess with iptables.  Should I be spending a lot of time tweaking the firewall?  There are several open ports (standard ports + daap) but with the routers, I feel (reasonably) safe.  Am I being foolish?

3)  I am learning the CLI, but sometimes I just need to do something without first learning.  For quick fixes, I intend to employ either x-over-ssh, or FreeNX.  I assume that I need to have a full desktop installed and running (or at least X) in order to use x over ssh.  Is that a correct assumption, or can I just install the program, and let the client side take care of the X work?

Thank You for your help.  These are issues that I would like to understand before I upgrade my server this week.  If anyone has any advice on Hardy vs Intrepid servers I would love to hear it as well.  I am leaning toward Hardy because it will be supported for a long time, but knowing me I will probably want to upgrade in a while anyway.  

Thanks

JTS

---

### Post by Dedoimedo on 2008-12-20
Hi there,

1. Keep the separate passwords, that's the whole idea of a multi-user environment, otherwise use a single account. Plus use different passwords for different uses.

2. If you're not forwarding your ports in the router, then you need not mess with iptables.

3. You need X to see X :)

Cheers,
Dedoimedo

---

### Post by jimmy the saint on 2008-12-20
So the server and PCs should all have one user, but the password should be different for each individual box?  I guess that would solve the ownership issues but still maintain a little security there.  Thanks

---

### Post by Iowan on 2008-12-20
For SSH in particular, you can log into a machine as a different server.  If you "ssh machinename" it will try to log in as your current username (which may not exist on machinename.  You can also connect via "ssh machineuser@machinename" The requested password will then be for machineuser.
In your case, if user1 on machine1 wants to SSH into machine2 (which has no user1, but user2) you could "ssh user2@machine2"

---

### Post by handydan918 on 2008-12-20
> **jimmy the saint said:**
> So the server and PCs should all have one user, but the password should be different for each individual box?  I guess that would solve the ownership issues but still maintain a little security there.  Thanks

I beg to differ. The very easiest way to use ssh is if you have an identical user with an identical password on each box. Obviously, this is suboptimal in the enterprise, but at home, behind a router,....well, I have not had any issues in all the years (6? 7?) I have done it this way.

---

### Post by jimmy the saint on 2008-12-21
I'm marking this as solve, but if anyone has any additional input, I would love to hear it.  Thank you guys for your replies!

---

