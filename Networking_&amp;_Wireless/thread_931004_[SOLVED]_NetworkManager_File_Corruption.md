---
title: "[SOLVED] NetworkManager File Corruption"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by jesusdemontreal on 2008-09-26
A few days after a fresh Mythbuntu 8.04 install I noticed that my NetworkManager icon was showing no Network Connection. 
A quick try from my laptop shows that I can ssh from it to my Mythbuntu box. 
Trying from the console a command like "ping google.com" tells me that it cannot find the site. I came to understand that my network was working as far as IP adresses go. When it came to DNS resolution, I wouldn't be able to connect anywhere. 
My network was DHCP managed, so I decided to take the good old manual configuration pattern. 
After modifying my /etc/network/interfaces and a "/etc/init.d/networking restart", ifconfig gives me the new and updated static IP but still no DNS. Ho, I forgot to modify /etc/resolv.conf . I try it to no avail, only to find myself doing a ls resolv* which gave me the following output:

ls: cannot access resolv.conf: No such file or directory

and ls -al gives me the following output:
drwxr-xr-x   3 root root     4096 2008-04-24 02:08 resolvconf
**-?????????   ? ?    ?           ?                ? resolv.conf**
-rw-r--r--   1 root dhcp       23 2008-09-26 19:07 resolv.conf.dhclient-new
-rw-r--r--   1 root root      152 2008-09-26 12:33 resolv.conf.tmp

Would anyone have any idea how I should go about to fix this? I'm about to try to boot on the LiveCD, delete the file and recreate it and if that fails, perhaps a fsck. 
I would be surprised that my hard drive would be corrupting data already, it's barely a month old (hopefully for the store manager, or else I know someone who's gonna know my name).

---

### Post by jesusdemontreal on 2008-09-27
Well it so happened that after a boot off the LiveCD, I still couldn't read/delete/modify resolv.conf.
I decided to go the fsck way and tada! The file was "erased" to lost+found and I was able to manually create the resolv.conf.
Having read somewhere that this might be a Network Manager issue, I decided to keep on going with my manual configuration and uninstalled Network Manager all together.

---

