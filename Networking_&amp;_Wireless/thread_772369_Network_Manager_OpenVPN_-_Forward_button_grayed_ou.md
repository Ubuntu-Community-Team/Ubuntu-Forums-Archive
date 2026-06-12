---
title: "Network Manager OpenVPN - Forward button grayed out"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by sylaan on 2008-04-28
Hello all, 

I am trying to set-up an OpenVPN connection via the network manager: Left click -> VPN Connections - Configure VPN. However, whatever I enter in there, the "Forward" button is grayed out and I can't proceed. Also, if I try to import existing configuration file, it lets me choose a file but then the fields are still empty, not filled in with the data. See the attached screenshot for details. 



I have to mention that connecting from the command line with that configuration file works just fine. I just don't know why it's not working via the Network Manager. 

Any ideas ?

Thanks,
Sylaan

---

### Post by lazyart on 2008-04-29
the preshared key needs to be a file apparently.

---

### Post by sylaan on 2008-04-29
No, it has nothing to do with what I enter there. No matter what I put in those fields, the Forward button stays grayed out. I tried with pre-shared key (selected a file), certificates, anything. Something is wrong with the interface itself.

---

### Post by lazyart on 2008-04-29
did you try hitting the folder button to the right and browsing to the keyfile?  That is what lit up the button for me...

---

### Post by sylaan on 2008-04-30
Hm, ok, I don't know what exactly I was doing the first time but it seems to be working now :oops:

First of all you can't import an existing OpenVPN config file. The tooltip on the "Import" button says so, must've missed it the first time. So that's why my import was not working. 

I then just tried to re-create the connection from scratch. I set up a X.509 type connection, selected all my certificate files, key file and the "Forward" button suddenly became active. The connection works. 

I was not able to setup a VPN connection to my company though, as a Cisco VPN client. The configuration goes well but everytime I initiate the connection, NetworkManager crashes badly. But at least the OpenVPN connection to my homeserver works fine now :)

---

### Post by drachenstern on 2008-04-30
Okay, I noticed a couple of things on this thread, as I'm in the middle of trying to setup some slightly more exotic features on my OpenVPN at work (such as WINS redirect, ooooh, exotic) and I notice in the screenshot that there is no name provided for the created VPN in the very FIRST text box.  That will stop you from continuing.

Second, I imported an existing OpenVPN file just fine.

Third, the OpenVPN client SHOULD NOT connect to a Cisco VPN setup, as they use two different ideologies for VPNs

---

### Post by sylaan on 2008-05-01
You can actually install a NetworkManager addon for Cisco VPN setups, not only for OpenVPN. And with that, you are supposed to connect. Not working in my case.

---

