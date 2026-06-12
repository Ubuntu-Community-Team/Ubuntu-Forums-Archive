---
title: "Update manager stuck..."
date: 2009-04-26
forum: New to Ubuntu
---

### Post by chilimac02 on 2009-04-26
I ran update manager today, and it doesn't work. I'm running Jaunty by the way (9.04). 

When I get the update manager running, it says there are a # of updates and to click "install updates". Unfortunately, when I click on the "install updates" button, I get nothing... It just sits there.

---

### Post by alphacrucis2 on 2009-04-27
> **chilimac02 said:**
> I ran update manager today, and it doesn't work. I'm running Jaunty by the way (9.04). 

When I get the update manager running, it says there are a # of updates and to click "install updates". Unfortunately, when I click on the "install updates" button, I get nothing... It just sits there.


Try different mirrors. Start up Synaptic Package manager. Select Settings/Software Sources. On the Ubuntu Software tab where is says download from: You can change e.g main server, servers for various countries etc. Might just be there is a problem with the servers you are using.

---

### Post by chilimac02 on 2009-04-27
OK, tried that. Oddly, the amount of data (in MB) changes, but the problem still persists. 

When I click on "install updates" nothing happens. It's as if I didn't do anything at all.

---

### Post by pokogr on 2009-04-27
Can you try installing an application from terminal:

> sudo apt-get install yourpackagename

and post the output?

---

### Post by pokogr on 2009-04-27
Or even better, try to upgrade through terminal:
> sudo apt-get upgrade

---

### Post by bumanie on 2009-04-27
> sudo apt-get update && sudo apt-get upgrade should fix that. I had the same thing happening during jaunty testing and the above code fixed everything up.

---

### Post by chilimac02 on 2009-04-27
that totally worked. I also needed to run "sudo apt-get clean"

---

### Post by depatty on 2009-04-28
Had the same general thing happen today.  Only difference was when I would click on install updates it would go and get state information and then just return to the update manager without finishing.  Running the apt-get - clean, update, and upgrade, seems to have taken care of it.

Thanks for the info!
Dave

---

### Post by MaX on 2009-04-30
> **depatty said:**
> Had the same general thing happen today.  Only difference was when I would click on install updates it would go and get state information and then just return to the update manager without finishing.  Running the apt-get - clean, update, and upgrade, seems to have taken care of it.

Thanks for the info!
Dave

Yes running apt-get upgrades your system, but Update-manager is still broken...
```
/var/lib/python-support/python2.6/dbus/connection.py:242: DeprecationWarning: object.__init__() takes no parameters
  super(Connection, self).__init__(*args, **kwargs)
```
Is all I get from it when I press 'install updates'... nothing happens beyond that... This is with 9.04 release and it happened when the final release came.


Oh, and using synaptic doesn't work either... Synaptic doesn't find any upgradable packages.
Could something have happened with the permissions to apt?

---

### Post by samspectre on 2009-05-04
I"ve been having the same troubles... When I do a clean and upgrade, I get this:

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  brasero liblucene2-java
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

No idea. Very new to Ubuntu/Linux.

---

