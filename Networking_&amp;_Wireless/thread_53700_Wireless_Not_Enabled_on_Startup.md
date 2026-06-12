---
title: "Wireless Not Enabled on Startup"
date: 2005-08-01
forum: Networking &amp; Wireless
---

### Post by patonar on 2005-08-01
Hi,

Just installed Kubuntu for the first time and so am a linux newbie. I have managed  to get my Wirless Card working using the Linunxant driver loader utility.

It works fine when i go into KDE Network configurator and enable the connection via the GUI.

However i cant get Kubuntu to automatically enable and assign this card an IP address using DCHP on start up.

Does anyone have any ideas? If i just start up and do nothing it detects the card and shows me the signal strength to the access point in Kwifi manager but just doesn't assign and IP until i enable it in the GUI.

Also is there anything better to use than KWifi manager in KDE? Must be easy to install as i am currently a linux n00b 

:)


Alsoo

---

### Post by odin on 2005-08-02
Try  this:
edit /etc/network/interfaces with "vi" "vim" "nano" or whatever text editor you use nad then write:

If you want to get your settings via DHCP:
    auto eth1
    iface eth1 inet dhcp
    wireless_essid network_name
    wireless_key "s: password"(this is only if you have encryption
If you want an static IP:
    auto eth1
    iface eth1 inet static
    address x.x.x.x
    netmask x.x.x.x
    gateway x.x.x.x
    wireless_essid network_name
    wireless_key "s: password"

Remember that where I wrote "eth1" you should write your wireless device name.

hope it helps

---

### Post by ibanez88 on 2006-05-21
I'd like to re-open this old thread because I'm experiencing the same problem as the original post.  Everything else works fine in kwifi on ipw2200 wireless...  I plugged in a little script containing only "kdesu dhclient" to get a dhcp lease on connect.  chmod +x....  Cool, when I press "Activate" everything comes up nicely as expected.

However, as the OP states, this does not occur on kde startup even though the "Load preset configuration on startup" box is checked.  You can look at my screenshot that I'm attaching to verify.  It simply does not connect unless I open up the dialog box and press "Activate" manually.

I should note that I am not using kdm.  I log in via text console but I don't think that should matter.  If anyone has any experience with this I'd appreciate your sharing.  

PS - I can edit /etc/network/interfaces by hand without difficulty.  My interest is with using the kwifi program to manage my connections.  Is this a bug or am I missing something?

---

