---
title: "firestarter icmp hits with bittorrent"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by gridd on 2009-09-16
Iam trying to download Edubuntu using bit torrent but i am getting 91 serious hits from ICMP which i have blocked in firestarter how can i tell if they are friendly or hostile they seem to be coming from three sources
and i dont seem to be seeding any on my other download.

---

### Post by 3rdalbum on 2009-09-16
> **gridd said:**
> Iam trying to download Edubuntu using bit torrent but i am getting 91 serious hits from ICMP which i have blocked in firestarter how can i tell if they are friendly or hostile they seem to be coming from three sources
and i dont seem to be seeding any on my other download.

1. You can't tell.

2. It doesn't matter, they are being blocked by your firewall. That's what the firewall is there for. Incidentally, a firewall will block anything coming in that you haven't told it to allow, so there's no cause for alarm at any time.

3. That's why I don't recommend Firestarter - its logging capability unintentionally scares users into thinking that they are under attack. Please, people; ammend your HOWTOs and stop advising new users to install Firestarter. gUFW will make everyone sleep easier at night.

---

### Post by lovinglinux on 2009-09-16
> **3rdalbum said:**
> 1. You can't tell.

2. It doesn't matter, they are being blocked by your firewall. That's what the firewall is there for. Incidentally, a firewall will block anything coming in that you haven't told it to allow, so there's no cause for alarm at any time.

3. That's why I don't recommend Firestarter - its logging capability unintentionally scares users into thinking that they are under attack. Please, people; ammend your HOWTOs and stop advising new users to install Firestarter. gUFW will make everyone sleep easier at night.

I agree with 3rd album again :)

These connection attempts are simply other peer clients checking if your machine is available. 

I suggest you read the [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923), specially the Security section. Nevertheless, the rest of the information there will help you understand how BitTorrent works and help to troubleshoot connection issues.

---

