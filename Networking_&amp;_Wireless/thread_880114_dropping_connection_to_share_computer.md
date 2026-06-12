---
title: "dropping connection to share computer"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by p-stone on 2008-08-04
Hello

I'm encountering a strange network issue and I'm not even sure where to begin troubleshooting it. I'll describe the setup I have and the symptoms as best I can. I have two computers hooked up to an hp procurve 2524 switch, the one machine is my server, it has an ssh server as well as a nfs file share. From the switch I'm wired to a d-link wireless router which is hooked to a few laptops as well as the cable modem. The switch, router and file share machine all have static IPs, wireless computers connect over DHCP. From either the other machine hooked on to the same switch as the file share or a laptop connected on wireless I can initially ssh into the machine, as well as see all my files on the nfs share. However, after an indeterminate period of time/use (I can't find anything consistent) I suddenly lose my connection. I get messages saying access is denied when I try and load any of my shares and ssh connection gets the same. I can still ping the machine but beyond that I have no connectivity. If I reboot the machine (not the server, the client) I get my connectivity back, however it just drops off again after a while. One other thing I've noticed that might have to do with something is that I've noticed that my rsa keys seem to be changing from time to time, the only way I know to fix this is to delete my ~/.ssh/known_hosts file and connect again. I don't know much about RSA keys or why they would change. The most recent change to my network has been the addition of the switch. If anyone has any suggestions for areas of research or knows of some things I should check I'd appreciate it.

Thank you

---

