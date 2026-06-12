---
title: "Samba issues"
date: 2015-06-25
forum: Networking &amp; Wireless
---

### Post by michael136 on 2015-06-25
Greetings,
 
                 After Racking my brain and searching the forums for 3 days about why i can't access files on the Windows Machines on my network through the File Browser.

I have figured out that if you add the ip address and computer name to the hosts file then everything works great.

For those of you that are having issues this is how i did it and it works for me

example:

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

172.30.150.5        <computer name>


add yours like this then save the file and you should be all set

Hope this helps :)

Mike

---

