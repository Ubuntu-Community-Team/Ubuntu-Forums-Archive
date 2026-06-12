---
title: "WAN incoming fine, LAN incoming really slow"
date: 2006-09-24
forum: Networking &amp; Wireless
---

### Post by notch on 2006-09-24
I have a strange problem. My small network consists of a PC dual booting XP and Ubuntu, an Xbox and a laptop all sitting behind a NAT router on 192.168.*.* priv network.

When I download stuff directly to the PC runnning Ubuntu from WAN via a web browser or ftp client I get full speed throught the NIC. 

The problem starts when I try to move files across the LAN. Files going out of the ubuntu box move at full speed to xbox or laptop for example but when I try to move file the other way the speed is beyond slow. We are talking over 30 mins for a 10mb avi.

When in windows the network functions as it should in both directions.

Any help would be much appreciated. I had the exact same setup working fine before, but after a re-install of ubuntu I have had this weird problem.

---

### Post by notch on 2006-09-25
Anyone... this is really confounding me.

---

### Post by rgeide on 2006-09-25
I've encountered the same thing in a Windows/Linux computer lab; the next semester it was fast, but I don't know the solution.

I dug this up out of my smb.conf  (/etc/samba/smb.conf):

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

Not sure what your's looks like, but it's worth a shot.

I would open the smb.conf file from xterm with the following:
sudo kate /etc/samba/smb.conf

else, you won't be able to do much editing.

Hope this helps.

---

### Post by notch on 2006-09-25
Thanks, will give this a shot even though I'm sure I didn't have to do this when I had my network working before the re-install.

EDIT: That option was already present in my smb.conf

---

