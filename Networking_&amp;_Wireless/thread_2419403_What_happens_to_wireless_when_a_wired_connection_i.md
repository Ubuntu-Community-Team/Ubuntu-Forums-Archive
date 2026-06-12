---
title: "What happens to wireless when a wired connection is plugged in?"
date: 2019-05-21
forum: Networking &amp; Wireless
---

### Post by Krause on 2019-05-21
On my laptop I have a dock with a wired NIC, what happens to the active wifi connection when I plug in the dock and it "switches" over to the ethernet. If I click WiFi it still shows the connected SSID, is it still active?

Trying to figure out if its safe to set a dnsmasq setting on my router to give both ports the same IP/Hostname instead of unique ones to make NFS share permissions easier instead of treating each connection it uses like a seperate PC.

---

### Post by TheFu on 2019-05-21
I don't see how NFS permissions are impacted. It is just 1 other allowed computer in the exports file.  As for file and directory permissions, that is all about the userid and groupid mappings being correct. Those wouldn't change at all based on wifi or wired ethernet connection.  Just setup DHCP reservations for all your portable devices, so they effectively get a static IP on your network while still using DHCP for convenience away from home.

Or did I misunderstand the issue?
 
Displaying a wifi SSID doesn't mean the interface is up or connected.

As you know,** it is not safe to have the same IP on different network devices if there is any way for both to be active concurrently**. Terrible things happen if that is allowed, and if you tell Linux to do it, it will. You run the OS, not the other way around.  Because Linux is very flexible, both interfaces can be active concurrently.  Some client-side network management tools can be configured to prefer the wired connection over wifi and disconnect, then bring the wifi interface down, whenever the wired connection is active.  You'd have to test the exact version on your exact OS to know.  Especially since you didn't mention either in the question.

Anyway, if you want an exact answer, probably should use the CLI tools on the system to see what happens. Try it. Use **ifconfig** or **ip addr** commands to see if the wireless still has an IP after the wired connection is made.

---

