---
title: "Can't open ports"
date: 2022-02-23
forum: Networking &amp; Wireless
---

### Post by Steve_Corman on 2022-02-23
I have an ubuntu 20.04 box running MythTV. There is a smart phone app Mythmote that provides a remote for MythTV. To talk the two require ports 6456 and 6948/udp. I created UFW rules to permit this, and I ran UFW status to verify they are listed. When I do an Nmap from another machine on the myth box, it does not show those ports as open. Could there be something other than the firewall blocking them?

---

### Post by The Cog on 2022-02-24
According to this page, you need to open 3 TCP ports, and they don't match the ports you quote: [https://www.mythtv.org/wiki/MythTV-HOWTO_-_0.26](https://www.mythtv.org/wiki/MythTV-HOWTO_-_0.26)
So to my mind at least, there is some doubt about which ports are needed,
First question is whether the MythTV box is actually listening for packets.
This will show you all listening TCP and UDP ports, and the application that is using the port:
```
sudo ss -lntup
```
If you can't see the application listening there, then you have a problem with the application - check it is running and correctly configured.

If you see that the ports are listening, then try turning off the firewall and see if it works then. If that makes it work, then compare the ss list of listening ports against the firewall configuration.

If it still doesn't work with the firewall disabled and the application running then I'm afraid I'm out of ideas.

---

