---
title: "How do I connect to the Internet?Ubuntu 10.04"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by Suzanne42 on 2010-09-07
Finally I got Ubuntu 10.04 working. Now, I want to know how I can restore my Internet connection via Network Tools(I had access to the Internet before Ubuntu 10.04 crashed). I only see Network Tools under System followed by Administration. Some forum suggested adding the Gnome Network Manager, it turns out the package is already included. Qn is now how to restore my connection?

---

### Post by gldearman on 2010-09-07
How do you connect to the internet?  Do you use a wired connection (e.g., ethernet) or a wireless connection.  Knowing that will give people someplace to start helping you troubleshoot.

---

### Post by coffeecat on 2010-09-07
> **Suzanne42 said:**
>  Some forum suggested adding the Gnome Network Manager, it turns out the package is already included.

Yes, it is in a default install, but check in Synaptic that the package network-manager is installed, just in case. 

Normally network manager should be installed and functional and the network manager icon should be showing on your upper panel towards the right - just left of the volume control icon. If it isn't, open System > Preferences > Startup Applications. Under the Startup Programs tab check to see that Network Manager is listed and ticked. If not, this is what you need to add:

Name:  Network Manager
Command:  nm-applet --sm-disable
Comment:  Control your network connections

The other reason for the network manager icon not appearing is if the panel applet 'notification area' has been removed.

Once you've found the network manager icon, simply click on it. If you are connecting by ethernet cable, you shouldn't have to do anything - NM should connect automatically once it detects a live ethernet connection. If you're connecting wirelessly, click on the NM icon and a list of wireless networks should drop down. Click on yours, put in your wireless passkey where prompted and you should be OK. If wireless networks are not shown, this could be a driver issue and we'll need more information to be able to help.

---

### Post by Suzanne42 on 2010-09-08
Its ok, I think there was some problem with my earlier installation so I din see the available connections but now after I reinstalled I can see the connections. Can someone pls tell me how I can resolve the boot error intrafms? Whenever I logon, I have to type exit continuously after each intrafms until it goes to my desktop. This is irritating, before when I used Ubuntu 10.04 also I had this prob, dunno how to resolve.

---

### Post by coffeecat on 2010-09-08
> **Suzanne42 said:**
> Can someone pls tell me how I can resolve the boot error intrafms? Whenever I logon, I have to type exit continuously after each intrafms until it goes to my desktop. This is irritating, before when I used Ubuntu 10.04 also I had this prob, dunno how to resolve.

We need some more details to diagnose this. Do you mean at the login screen that you are getting some sort of error message which involves 'intrafms'? I think you mean initramfs. I've not seen an initramfs error at the login screen so please post the exact error message, or at least the first couple of sentences if very verbose.

If this is what I think it is, it's easily fixed but I don't want to give you the wrong solution, so post some more details and we'll take it from there.

---

