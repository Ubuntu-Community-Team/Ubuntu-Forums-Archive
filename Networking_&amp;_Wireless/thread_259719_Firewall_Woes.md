---
title: "Firewall Woes"
date: 2006-09-17
forum: Networking &amp; Wireless
---

### Post by Protostar on 2006-09-17
Hello all. I'm using Kubuntu 6.06 and am having some issues with my network. I'm using a Linksys WRT54G wireless router to connect to the Internet and am having issues forwarding ports in Kubuntu. I installed the Guarddog firewall frontend and configured all the settings to my liking and everything works except Bittorrent and amule. When the firewall is enabled I can't connect to the tracker and download anything. When I disable it I can download but not upload which is bad as that sort of defeats the purpose of bittorrent. I opened TCP/UDP port 56000 in my router and it still wouldn't recognize it. It worked in windows at least for a while until I tried to open the port to connect to the edonkey2000 network, then it stopped working. Switching to Windows isn't an option for me b/c for some reason Windows won't install on my computer so I'm stuck with Kubuntu (not that thats a bad thing). Anyway, any help would be greatly appreciated. TIA.

---

### Post by foolsh on 2006-09-17
I use firestarter for my firewall/port forwarding gui frontend IMO its easier to understand
dont forget to allow connections from your internal network i.e. 192.168.0.0/16 
i found amule needs the MStraceroute protocal call to work correctly so make sure your not filtering that ICMP

---

### Post by Protostar on 2006-09-18
> **foolsh said:**
> I use firestarter for my firewall/port forwarding gui frontend IMO its easier to understand
dont forget to allow connections from your internal network i.e. 192.168.0.0/16 
i found amule needs the MStraceroute protocal call to work correctly so make sure your not filtering that ICMP

I will try that. I just liked Guarddog because it was so much more user friendly and would tell you the what the network protocol was/did and its default ports. Anyone else have any sugesstions?

---

