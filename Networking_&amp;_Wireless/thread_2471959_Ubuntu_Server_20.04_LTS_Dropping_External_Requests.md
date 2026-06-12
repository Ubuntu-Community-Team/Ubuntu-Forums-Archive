---
title: "Ubuntu Server 20.04 LTS Dropping External Requests After Update and Reboot"
date: 2022-02-14
forum: Networking &amp; Wireless
---

### Post by jmferris on 2022-02-14
I've been re-teaching myself Linux after not working with it in better than fifteen years, and have an Ubuntu 20.04 LTS install that has been up for a few weeks now. Everything has been working perfectly, until yesterday. After doing an apt update/upgrade and rebooting, I've started experiencing a strange behavior that I've been unable to hunt down.


Namely, external requests that are forwarded to my server are behaving like they are being dropped. I have a couple of different ports forwarded to this server, as well as to another server. After the reboot, attempting to access any of these ports externally results in a refused connection. Meanwhile, though, I can still access them from within the network, normally. In the event it is relevant, this is a Docker container using host networking.


First thing that I wanted to do was to verify how far the traffic was making it, first ruling out the IP address that the DDNS provider was using (it was correct) and verifying that traffic was making it through the router via tcpdump on the server. From the below output, 208.127.85.157 is my client IP address, and 192.168.0.101 is the internal IP address of the server.


```
jmferris@ferris-smarthome:/array/container-data/home-assistant/config/www$ sudo tcpdump -ni any port 8123 | grep '208.127.85.157'
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on any, link-type LINUX_SLL (Linux cooked v1), capture size 262144 bytes
16:41:26.678096 IP 192.168.0.101.8123 > 208.127.85.157.9247: Flags [P.], seq 3167168894:3167169046, ack 1455471558, win 501, length 152
16:41:28.238427 IP 208.127.85.157.9247 > 192.168.0.101.8123: Flags [F.], seq 1, ack 0, win 1029, length 0
16:41:28.238984 IP 192.168.0.101.8123 > 208.127.85.157.9247: Flags [F.], seq 9480, ack 2, win 501, length 0
16:41:28.243236 IP 208.127.85.157.34200 > 192.168.0.101.8123: Flags [S], seq 1121415575, win 65280, options [mss 1344,nop,wscale 8,nop,nop,sackOK], length 0
16:41:28.243306 IP 192.168.0.101.8123 > 208.127.85.157.34200: Flags [S.], seq 1635185161, ack 1121415576, win 64240, options [mss 1460,nop,nop,sackOK,nop,wscale 7], length 0
16:41:28.245639 IP 208.127.85.157.63320 > 192.168.0.101.8123: Flags [P.], seq 3874385583:3874386056, ack 3032168147, win 1029, length 473
16:41:28.245681 IP 192.168.0.101.8123 > 208.127.85.157.63320: Flags [.], ack 473, win 501, length 0
16:41:28.247308 IP 192.168.0.101.8123 > 208.127.85.157.63320: Flags [P.], seq 1:153, ack 473, win 501, length 152
16:41:28.247380 IP 192.168.0.101.8123 > 208.127.85.157.63320: Flags [P.], seq 153:2841, ack 473, win 501, length 2688
16:41:28.247392 IP 192.168.0.101.8123 > 208.127.85.157.63320: Flags [P.], seq 2841:5529, ack 473, win 501, length 2688
16:41:28.247628 IP 192.168.0.101.8123 > 208.127.85.157.63320: Flags [P.], seq 5529:8217, ack 473, win 501, length 2688
16:41:28.247647 IP 192.168.0.101.8123 > 208.127.85.157.63320: Flags [P.], seq 8217:9481, ack 473, win 501, length 1264
16:41:28.291053 IP 208.127.85.157.34200 > 192.168.0.101.8123: Flags [.], ack 1, win 1029, length 0
16:41:28.950056 IP 192.168.0.101.8123 > 208.127.85.157.63320: Flags [P.], seq 8217:9481, ack 473, win 501, length 1264
16:41:29.299335 IP 208.127.85.157.63320 > 192.168.0.101.8123: Flags [P.], seq 0:473, ack 1, win 1029, length 473
16:41:29.299373 IP 192.168.0.101.8123 > 208.127.85.157.63320: Flags [.], ack 473, win 501, options [nop,nop,sack 1 {0:473}], length 0



```When I attempt to access the site externally, I do see traffic inbound, as shown above. I don't understand the non-standard ports showing up, however. This is an instance of Home Assistant, which runs on 8123, so I am unsure what 9247, 34200, or 63320 are. 34200 is normally used for Plex, but this server isn't hosting Plex, either. But, I can at least verify here that traffic I generate off network is making it this far, but this is seemingly as far as I get. The browser, in this case, Chrome, is never getting any acknowledgement and will eventually timeout with a Connection Refused error.


Just to verify that the problem is not related to the singular application, I created two more port forwarding rules on my router for two other ports that are accessible and working from inside of the network, and I am getting the same behavior.  Additionally, I verified that port forwarding rules I have that point to another machine in my home infrastructure are working as expected.  It is definitely isolated to requests to this specific machine.


From what I read, this sounded a lot like an firewall rule dropping requests. But, dfw is inactive, if I check its status and iptables is not installed. From this point, I am at a total loss to explain or understand what is going on, apart from it was working absolutely fine until I updated my packages and rebooted the machine. I am not sure if it will help, but here is the output my /var/log/apt/history.log file, too.


```
Start-Date: 2022-02-13  14:39:33
Commandline: apt-get upgrade
Requested-By: jmferris (1000)
Upgrade: update-manager-core:amd64 (1:20.04.10.9, 1:20.04.10.10), libdrm-nouveau2:amd64 (2.4.105-3~20.04.2, 2.4.107-8ubuntu1~20.04.1), libglapi-mesa:amd64 (21.0.3-0ubuntu0.3~20.04.5, 21.2.6-0ubuntu0.1~20.04.1), snapd:amd64 (2.51.1+20.04ubuntu2, 2.54.2+20.04ubuntu2), ubuntu-advantage-tools:amd64 (27.5~20.04.1, 27.6~20.04.1), initramfs-tools-bin:amd64 (0.136ubuntu6.6, 0.136ubuntu6.7), libdrm-amdgpu1:amd64 (2.4.105-3~20.04.2, 2.4.107-8ubuntu1~20.04.1), python3-update-manager:amd64 (1:20.04.10.9, 1:20.04.10.10), libdrm2:amd64 (2.4.105-3~20.04.2, 2.4.107-8ubuntu1~20.04.1), libgl1-mesa-dri:amd64 (21.0.3-0ubuntu0.3~20.04.5, 21.2.6-0ubuntu0.1~20.04.1), sosreport:amd64 (4.1-1ubuntu0.20.04.3, 4.2-1ubuntu0.20.04.1), libdrm-intel1:amd64 (2.4.105-3~20.04.2, 2.4.107-8ubuntu1~20.04.1), libdrm-radeon1:amd64 (2.4.105-3~20.04.2, 2.4.107-8ubuntu1~20.04.1), mesa-vulkan-drivers:amd64 (21.0.3-0ubuntu0.3~20.04.5, 21.2.6-0ubuntu0.1~20.04.1), initramfs-tools-core:amd64 (0.136ubuntu6.6, 0.136ubuntu6.7), initramfs-tools:amd64 (0.136ubuntu6.6, 0.136ubuntu6.7), libglx-mesa0:amd64 (21.0.3-0ubuntu0.3~20.04.5, 21.2.6-0ubuntu0.1~20.04.1), libdrm-common:amd64 (2.4.105-3~20.04.2, 2.4.107-8ubuntu1~20.04.1)
End-Date: 2022-02-13  14:40:27



```If anyone had any advise on where to look, or what to try, it would be most appreciated.


Thank you, in advance.

---

### Post by jmferris on 2022-02-15
Further information that appears to be relevant, although I do not understand where to look or what to look at.  The machine has two NICs (technically, it has four NICs, but I am only using two of them).  After rebooting, I see the behavior from the original post, where outbound traffic as part of an inbound request is "lost".  However, the moment I unplug the cable from the second NIC, it all starts working.  Then, even if I plug back in to the second NIC, it continues to work, until I reboot again.

So this definitely isn't firewall related, but somehow networking configuration.  Can anyone point me at what to look for?

Thank you!

---

### Post by jmferris on 2022-02-15
This has been resolved.  What caused this to happen was that it was autodetecting the default gateway.  From what I understand, it was a "last in wins" scenario, so the default gateway for the second NIC was the one that was being used.  Went in and added the default gateway through the netplan yaml file to the correct interface, then removed the other gateway through a "route delete".  After removing the route for the second default gateway and rebooting, it behaves as expected.

I obviously still have a lot to learn about Linux networking.

---

