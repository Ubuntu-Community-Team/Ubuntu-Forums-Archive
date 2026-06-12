---
title: "[SOLVED] IP based samba authorization"
date: 2007-09-16
forum: Networking &amp; Wireless
---

### Post by panda726 on 2007-09-16
I have looked but not found found a way to do this under linux (Kubuntu in particular).  I would like to set up my network (multi OS) so that the samba shares on my computer will accept the source IP of a request as sufficient authentication to read and write to shares.  Yes, I already have static IPs assigned to the computers belonging to the file sharing network.  I also have DHCP enabled because we often have other people use our high speed internet.  (DHCP pool already scaled to not include the range in which static IPs fall.)  I had something like this working in windows through the messy means of a firewall to block all but the assigned static IPs.  I am sure there is a better method that I have not found, and any help to get this working would be appreciated.

---

### Post by al_erola on 2007-09-16
You should be able to use the function "host allow" in the smb.conf file.  

from:  [http://www.linux.com/whatislinux/118625](http://www.linux.com/whatislinux/118625)

... it is very important that you restrict access to only known and trusted hosts - the computers in your household. Consult your router's manual for instructions on assigning specific IP addresses to each computer in your home network. Once you have a list of trusted hosts, enter them into the following lines in the [global] section:

hosts allow = computer1 computer2 computerN
hosts deny = ALL

Although you have specified that ALL hosts be denied, any host listed on the hosts allow line will still be given access. The format of the IP addresses assigned to each computer by your router will vary. For instance, if machines on your local network are given addresses of the format 192.168.0.x, the following lines will restrict Samba access to local hosts:

hosts allow = 192.168.0.
hosts deny = ALL

Note that the final digit of the IP address was left off on the hosts allow line. This specifies that any IP address in that range be allowed. For additional security against external access, look into blocking Samba ports with a firewall.

---

### Post by panda726 on 2007-09-16
Thank you.  I tried something like this, but something wasn't quite right.  This seems to be working to allow my computers to access without passwords, therefore I will mark this solved.  If you would happen to know the smb.conf option I would use to set an individual shared folder to require a password this would be a bonus, but what I have will do just fine.

Again thank you for finding a wording of this that fit what I could easily understand as one who is new to linux coming from an intemediate power user on windows.

---

