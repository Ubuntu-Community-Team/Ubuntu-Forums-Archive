---
title: "Edgy Wireless WPA"
date: 2006-10-30
forum: Networking &amp; Wireless
---

### Post by k_smolka on 2006-10-30
Hi All 

This is a repost after my initial post failed to get any responses.

It seems like lots of people are having problem with wireless after upgrading to edgy.

I am having problems connecting to a WPA encrypted network and maintaining a connection. I am not a networking expert by any stretch. I am using network manager to connect to the network

I am able to connect to the network  on boot but the connection then hangs and I am unable to connect. 

I am using the ipw220 driver.

Here is the output from ifconfig, 

 RX packets:51 errors:293 dropped:304 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:76202 (74.4 KiB)  TX bytes:47724 (46.6 KiB)
          Interrupt:11 Base address:0x6000 Memory:ffdff000-ffdfffff 

Does anybody know what was changed on edgy to break the wireless for so many people.

Any help would be most appreciated

Regards 

Karl
](*,)

---

### Post by rex123 on 2006-11-07
Here's my experience. I don't know whether it will help anyone else:

I got wpa wireless working on Dapper, but never had network-manager working, so I had to run wpa_supplicant manually after logging on. That was OK, but I thought I'd give network-manager another shot after upgrading to Edgy. It didn't work...

So I uninstalled wpasupplicant (which removed network-manager), and manually removed all config files from /etc/ that looked like they were wpa-related. Then I reinstalled network-manager-gnome, and tried again. This time it worked. My reasoning is that the manual messing about I needed to do in Dapper or before was interfering with network-manager. I have no real proof of this, though, because I have no idea what files network-manager writes to, or what files affect its behaviour. That's the problem with an app that "just works". If it doesn't just work, it's just mysterious.

[edit] WARNING: uninstalling wpasupplicant removes ubuntu-minimal (don't ask me why), and I ended up with an unbootable system after this (had to boot to live CD, mount, chroot, install upstart to get going again). So make sure you reinstall ubuntu-minimal if you try doing what I did.

---

