---
title: "nautilus doesn't recognize dns name when openning windows(smb) directory"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by puqing on 2007-03-26
Hi, in the nautilus address bar, when I enter "smb://xxx.xxx.xxx.xxx/", the IP address of a windows machine, the shared directories are displayed and I can use them without problem.

However, if I enter "smb://yyy.dyndns.org/", which is the DNS name of the windows machine, nautilus pop up a dialog box saying:

          Sorry, couldn't display all the contents of "Windows Network: yyy.dyndns.org".

So, IP address works here but DNS name doesn't.

By 'ping yyy.dyndns.org' in a terminal, it seems the name can be properly resolved to its IP address xxx.xxx.xxx.xxx. But it seems nautilus or samba doesn't resolve it.

Anyone encountered similar problem? How to solve it?

Thanks in advance!

---

### Post by netztier on 2007-03-26
> **puqing said:**
> 
However, if I enter "smb://yyy.dyndns.org/", which is the DNS name of the windows machine, nautilus pop up a dialog box saying:

          Sorry, couldn't display all the contents of "Windows Network: yyy.dyndns.org".

So, IP address works here but DNS name doesn't.

By 'ping yyy.dyndns.org' in a terminal, it seems the name can be properly resolved to its IP address xxx.xxx.xxx.xxx. But it seems nautilus or samba doesn't resolve it.

Anyone encountered similar problem? How to solve it?


Is xxx.xxx.xxx.xxx the "internal" LAN adress, for example behind your broadband router, and you are trying to access this windows machine from within the same LAN? Let's assume that we have 192.168.0.20 for the windows box. The broadband router registers it's external address as yyy.dyndns.org.

So you're saying that (from the inside LAN) **smb://192.168.0.20/** works, but **smb://yyy.dyndns.org/** doesn't? That would be expected, since yyy.dyndns.org resolves to the router's public IP address. A router in good configuration state will not allow this kind of connection: return-connects back to itself are not allowed.

To resolve this, you'd have to find a way that your Ubuntu machine somehow gets the IP address 192.168.0.20 when looking up the hostname yyy. Adding the entry to **/etc/hosts ** might help here.

If you are trying to access the Windows Box from **outside** the router (i.e. the Internet), you'd also have to configure port-forwarding for CIFS or NetBIOS towards the windows box. (*eeeeww....* looking at the continuous port scans for tcp/445 and NetBIOS ports, I *strongly* doscourage to do this).

So: basic questions first: is there a (broadband) router in here somewhere, which system does register which IP address with dyndns.org and where in this network setup is the ubuntu box?

In a nutshell: **what does your network look like?**

best regards

Marc

---

### Post by puqing on 2007-03-26
Thank you for your patient reply!

The IP address obtained by windows box's 'ipconfig' command is exactly the same with the IP address obtained on the Ubuntu by "ping yyy.dyndns.org". So I think the IP address is not the router's public address. And I can visit the windows box's shared directories using its IP address, "smb://xxx.xxx.xxx.xxx". But I can't directly "smb://yyy.dyndns.org" to visit it.

I am not very aware of the network structure here. It is a campus network. The two machines are on different sub-network. One is a pc running windows, the other is my laptop running Ubuntu. The pc connects to a wired network, while the laptop connects to a wireless network. They are physically very close to each other, which I don't think matters. I tried 'tracepath', but it only gives a lot of "no reply" information and can't generate a full path. So, I guess there is firewall there.

I tried to modify the "name resolve order" in "smb.conf" by moving "host" to the first of the list. But it didn't fix the problem.

Maybe I still miss something. Any help will be appreciated.

---

### Post by netztier on 2007-03-26
> **puqing said:**
>  The IP address obtained by windows box's 'ipconfig' command is exactly the same with the IP address obtained on the Ubuntu by "ping yyy.dyndns.org". 

Be careful with using ping as name resolution tool. On Unix it's not that much of an issue - on a Windows system that might use WINS instead of DNS to resolve a name (without letting ou know though), you might lose hours of valuable time trying to track down what appears to be a name resolution problem. You guessed it: been there, done that ....

> **puqing said:**
> I am not very aware of the network structure here. It is a campus network. The two machines are on different sub-network.

Are these addresses "private" addresses as per RFC1918? In extenso: 10.*.*.*, 172.[16-31].*.* or 192.168.[0-255].* ? Or is it true "public" addresses? Have you tried a reverse-lookup for the addresses your PCs are obtaining? maybe the campus' network admin already has a hostname  in his DNS for your PCs?

> **puqing said:**
> One is a pc running windows, the other is my laptop running Ubuntu. The pc connects to a wired network, while the laptop connects to a wireless network. They are physically very close to each other, which I don't think matters. I tried 'tracepath', but it only gives a lot of "no reply" information and can't generate a full path. So, I guess there is firewall there.


This might very well be - can you connect a small hub or switch to the wired connection and plug the laptop in there alongside the PC? Like that, you can try to connect from machine to machine while staying on the same subnet. Chances are good that there is some kind of firewall shielding off the wired network from the "public" Wireless network -- no.. it's working when done by IP address, you said.. *grmbl*:confused:  This is my wit's end, for the moment.


best regards

Marc

---

