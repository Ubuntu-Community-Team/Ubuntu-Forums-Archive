---
title: "ubuntu 9.10 wants files from WinXP"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by kowalsky on 2009-12-01
hi all,
I am trying to connect from a Ubuntu 9.10 box to a WinXP box on a network.
At some point there was a domain controller that created MYDOMAIN. Currently the XP box is running under a local account and the domain controller is down. The network name as defined by the router is MYNETWORK.

I installed samba (simply sudo apt-get install samba).
I edited the smb.conf so that workgroup = MYNTEWORK.

What next? How exactly I establish a connection between the machines?
Do I connect from my Ubuntu box ? ls -al myXPbox/shared_folder?
I tried that and it didn't work. I tried to change  workgroup=MYDOMAIN and it still didn't work.
Any ideas?

Thanks,
kowalsky

---

### Post by running_rabbit07 on 2009-12-01
> **kowalsky said:**
> hi all,
I am trying to connect from a Ubuntu 9.10 box to a WinXP box on a network.
At some point there was a domain controller that created MYDOMAIN. Currently the XP box is running under a local account and the domain controller is down. The network name as defined by the router is MYNETWORK.

I installed samba (simply sudo apt-get install samba).
I edited the smb.conf so that workgroup = MYNTEWORK.

What next? How exactly I establish a connection between the machines?
Do I connect from my Ubuntu box ? ls -al myXPbox/shared_folder?
I tried that and it didn't work. I tried to change  workgroup=MYDOMAIN and it still didn't work.
Any ideas?

Thanks,
kowalsky

I haven't been able to much as far as retrieving material from my Windows Machine from my Ubuntu machine, but I am able to create a shared folder on the Ubuntu machine and drop the files in it from the Windows machine.

---

### Post by kowalsky on 2009-12-01
thank you for the information,
how do you do that?
When I try to go this way, the Xp is prompting me for user&pwd and wants to connect to MYDOMAIN.myUbuntu machine ... it is useless to give it any password it won't recognize anything.

thanks,
kowalsky

---

### Post by running_rabbit07 on 2009-12-02
When you set up the folder on Ubuntu, right click, go to properties, click on the share tab, click all three boxes. It isn't good for network security, but in a home network, it is fine.

---

### Post by Dullstar on 2009-12-02
Hmm, picking a descriptive topic title is usually a good idea...

I've never done file sharing between a WinXP box and a 'buntu box, because I don't need to.  I don't know if it's possible, but it probably is.

---

### Post by running_rabbit07 on 2009-12-02
> **Dullstar said:**
> Hmm, picking a descriptive topic title is usually a good idea...

I've never done file sharing between a WinXP box and a 'buntu box, because I don't need to.  I don't know if it's possible, but it probably is.

It is possible, just a matter of getting the permissions ironed out. There are programs within Synaptic Package Manager that deal with Samba to make it easier to do this, but I haven't made time to learn it yet.

---

### Post by kowalsky on 2009-12-02
it must be a little more than that.

As far as the permissions are concerned, instead of ironing I suppose a chmod 777 will do the trick.
But right now I ping the myUbuntu box and the xp box automatically assigns the myUbuntu to the MYDOMAIN domain, trying to find (unsuccessfully) MYDOMAIN.myUbuntu.com - the ip address it shows is a very weird address, I'll look that one up.

The same thing when I try to ping the myXP box from the linux box - it tries to find MYNETWORK.myXP ...

If i ping the ips (looked up with ifconfig and ipconfig) they reply just fine ...

Does anybody know how to do this?
thanks,
kowalsky

---

### Post by BDNiner on 2009-12-02
What shares have you setup on the windows box?

Ubuntu should be able to see the shares when you go to network.

---

### Post by BDNiner on 2009-12-02
Also it does help in my experience to have the same username and password logged into both the windows machine and the ubuntu machine. You should not get prompted for a login when connecting that way.

---

### Post by Dougie187 on 2009-12-02
Have you worked through this?

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

---

