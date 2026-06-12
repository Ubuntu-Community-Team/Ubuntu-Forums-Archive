---
title: "ubuntu &lt;-&gt; windows xp"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by rkakkar on 2007-02-20
my friend has windows xp installed on his laptop. we need to do some data transfer and basically have decided to connect our machines through lan (only the two of us on network). can someone guide me on how to enable my ubuntu machine to detect his windows xp and browse folders on his laptop? thanks.

---

### Post by louis_nichols on 2007-02-20
Sure. The program you use for this is called samba. Actually, Ubuntu comes by default with a subset of samba that allows browsing windows shares on other computers, so you only need the actual samba package if you also want to share. Accessing a windows share is as simple as going to Places>Network servers. There you should see an icon for the windows network. Clicking on that will show available workgroups and those will contain the available computers.

Of course all of the above is possible as long as the network is correctly configured. I don't know if you also need that part explained. Basically, this means setting the IP addresses and netmasks correctly. If done right, the computers must be able to ping each other. The simplest way to do this is to go in Ubuntu to System>Administration>Networking, selecting the network card used and entering the IP 192.168.0.1 and the default netmask. In windows, for the netcard, you should set IP 192.168.0.2 and also default netmask. This is a simple setup that should work. After this, Ubuntu should just be able to access windows shares the way I described above.

Sharing files means installing samba. The default install should also work without any tweaks (at least for me it did, with the IPs I wrote above), but a customization is sometimes needed. You can find instructions for doing this [here]("https://help.ubuntu.com/community/SettingUpSamba").

That's pretty much it, I think...

---

