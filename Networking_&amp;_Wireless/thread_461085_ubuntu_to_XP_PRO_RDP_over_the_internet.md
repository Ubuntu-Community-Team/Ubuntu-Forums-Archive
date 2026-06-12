---
title: "ubuntu to XP PRO RDP over the internet?"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by h8train on 2007-06-01
Ok so I have read just about all of the topics about ubuntu and RDP, nows heres myproblem.
I can connect to my xp pro RDP on my lan from ubuntu, but when I go to work and try an connect over the internet it times out.I have myports forwarded correctly because when I'm at work I can remote inot my home machine fine under windows, but I would like to be able to use linux at work to remote into my home machine. I have searched for quite a while on this and can't seem to find the fix (or maybe my search terms aren't good enough to find the answer).

Anyhelp with this problem would be greatly appreciated.

Thanks,

Rich

---

### Post by brigux on 2007-06-01
Possibly tcp/3389 (rdp) is blocked by your FW at work.

Anyway opening RDP on the Internet is not very secured.
I would suggest you to install a ssh server on your ubuntu (easy)
then tunnel the rdp protocol through the ssh connection. there are plenty of howTo on the Internet

---

### Post by lazyart on 2007-06-01
When you're doing this from work are you setting the termimal services client protocol to RDP?  I think it defaults to VNC which isn't what you want.

---

### Post by h8train on 2007-06-04
as for firewall at my work there is no problem as RDP out is working fine under XP just not under Ubuntu, and I assume ubuntu knows wich port to connect on for RDP.

Yes I am choosing RDP and not VNC when I attemp to connect to my home.

The RDP client for ubuntu works absolutely fine when I am on my LAN @ home, but not when trying to connect over the internet. like I said I have my router at home configured correctly to forward ports to my RDP host because I have no problems connecting through XP from work. I was hoping there was some config for the RDP client in ubuntu to allow internet connections to made outgoing. Has anyone else had this problem with RDP client in ubuntu working on LAN and not over the internet?

Thanks again for replies and for future replies to help me fix this problem.

Thanks

Rich

---

