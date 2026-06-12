---
title: "Thunar and Windows AD Network - File Shares"
date: 2016-02-26
forum: Networking &amp; Wireless
---

### Post by OnyxDragun on 2016-02-26
It's been a while now and for some reason on my main desktop (Xubuntu 14.04) I haven't been able to navigate to any windows file servers that require an AD account/password in a while. 

When I use smb://ipaddress  it comes up with the required credentials needed, I enter them and then it's like nothing happens. In a varied amount of time I get back a window that says Failed to open "File System". Failed to retrieve share list from server. Connection refused.

When I use my other Xubuntu system (essentially the same 14.04 install), Thunar is able to navigate with the same credentials I apply to this machine.  For some reason this machine just wont connect to any shares via Thunar (or any other GUI based file manager as I've tried Dolphin as well). 

I have a smb server installed on this machine and I can access it from other machines without issues. 
I've tried using the smbclient via the CLI but if I recall that didn't work either. 

What are some other things I might try? I've been googling/searching for similar things and trying them but I am at a loss.

---

