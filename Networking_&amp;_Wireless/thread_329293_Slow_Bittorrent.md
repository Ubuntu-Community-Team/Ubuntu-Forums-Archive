---
title: "Slow Bittorrent"
date: 2007-01-01
forum: Networking &amp; Wireless
---

### Post by rykel on 2007-01-01
Hi,

I have a very unusual bittorrent problem here...

I am using utorrent in Ubuntu (yes, it works), have forwarded the port correctly (both TCP and UDP) on a Prolink Hurricane 9000C ADSL modem/router. I have GREEN light for the forwarded port and in fact, one of the torrent file is downloading at 50kB/s.

However, for 2 other torrents that are running, I am getting extremely miserable download rates of 1-10 kB/s. These torrents have more than 5 seeds/80+ peers, and on my other broadband network, the very same downloads were coming in at least 40-50kB/s.

Could you please advise me on what I should do to utorrent and/or my modem to speed things up?

I have reset the modem/router, upgraded its firmware and disabled NAT, but to no avail...   ](*,)

---

### Post by daverave999 on 2007-01-05
I had similar issues, but I just [disabled IPv6]("http://www.ubuntuforums.org/showthread.php?t=87798") and that seemed to sort things out.

Might work for you?

---

### Post by rykel on 2007-01-06
> **daverave999 said:**
> I had similar issues, but I just [disabled IPv6]("http://www.ubuntuforums.org/showthread.php?t=87798") and that seemed to sort things out.

Might work for you?

Hi, I saw that you posted the last message on that thread... I am also on Edgy, so how do I disable IPv6? Thanks!

---

### Post by daverave999 on 2007-01-06
Type (or copy&paste!)```
sudo gedit /etc/modprobe.d/blacklist
``` into the terminal.

Add ```
#Added by rykel for excessive timing out?
blacklist ipv6
``` to the end of that file. Save it and close it. Reboot.

Put ```
ip a | grep inet6
``` into the terminal. If you don't get any output from that then IPv6 is turned off (I believe!)

I'd be pleased if this worked for you. Getting bittorrent to work was one of may major issues too...

---

