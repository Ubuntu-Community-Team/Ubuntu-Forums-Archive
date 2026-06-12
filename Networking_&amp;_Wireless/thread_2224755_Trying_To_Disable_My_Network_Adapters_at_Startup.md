---
title: "Trying To Disable My Network Adapters at Startup"
date: 2014-05-17
forum: Networking &amp; Wireless
---

### Post by Drunyan on 2014-05-17
I am trying to disable my network adapters at start up, but I can not figure out how toi do it. I have foilowed the instuructions on this page, [http://www.upubuntu.com/2012/01/how-to-disable-your-network-adapter.html](http://www.upubuntu.com/2012/01/how-to-disable-your-network-adapter.html), but I am still able to connect to my wireless network. I have also tried to set up a user account that requires the sudo password to be entered before a connection to the network can be made. 
Can some one help me figure out how to disable my network connections at start up? Could I do it in the BIOS Settings?

Thank You

---

### Post by varunendra on 2014-05-21
Welcome to the forums Drunyan!

Could you please elaborate a bit? Why do you want to do this? Do you want to restrict some (or all) users or just make it a manual operation?

You can simply blacklist the drivers so they don't load automatically at startup. A user of 'sudo' group would then need to load the driver manually before the adapter can be used. But of course any user of the 'sudo' group would be able to do that.

The method you followed should also work, but I don't know if Network Manager can override it, or if the 'down' command needs to be delayed.

By the way, the 'sudo' is not required in rc.local file, since it already runs with root privilege.

---

