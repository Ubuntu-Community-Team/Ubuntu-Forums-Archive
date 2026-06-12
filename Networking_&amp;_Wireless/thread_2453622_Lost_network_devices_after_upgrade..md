---
title: "Lost network devices after upgrade."
date: 2020-11-14
forum: Networking &amp; Wireless
---

### Post by dwater on 2020-11-14
Ubuntu 20.04.1 LTS
Dell XPS 13 9360 (075B)

It boots fine.

No networking devices shown in network manager, and 'lshw -c network' shows the 'wireless network adaptor' as 'DISABLED'.
'rfkill list all' shows '{Soft,Hard} blocked: no' for 'phy0: Wireless LAN'.

I don't see anything suspicious in dmesg when looking for ath10k_pci - only 'unsupported HTC service id: 1536'.

Tried:

1. h/w dell diagnostics - seems fine
2. booting to older kernels - same problem
3. reinstalling linux-firmware (1.187.4_all.deb), and updating it to the latest (1.191_all.deb) - same problem.

Obviously, it's difficult to cut/paste...

Any ideas how to get networking back again?

---

### Post by dwater on 2020-11-14
After some trial and error, I followed the instructions on this page:

[https://www.linuxbabe.com/ubuntu/connect-to-wi-fi-from-terminal-on-ubuntu-18-04-19-04-with-wpa-supplicant](https://www.linuxbabe.com/ubuntu/connect-to-wi-fi-from-terminal-on-ubuntu-18-04-19-04-with-wpa-supplicant)

to get the wifi network up again...and it seems to work...of course, it's only a workaround, but at least I can cut/paste command output from there now.

My real solution is to get it working from Network Manager again.

Pointers welcome....

---

### Post by dwater on 2020-11-14
This fixed it:

[https://gist.github.com/micrypt/1207324](https://gist.github.com/micrypt/1207324)

> 
su root
# Don't you hate when you need to root to fix dumb issues?
service network-manager stop
rm /var/lib/NetworkManager/NetworkManager.state
service network-manager start
reboot -h now


---

