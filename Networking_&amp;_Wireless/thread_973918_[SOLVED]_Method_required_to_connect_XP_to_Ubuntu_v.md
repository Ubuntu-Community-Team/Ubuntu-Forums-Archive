---
title: "[SOLVED] Method required to connect XP to Ubuntu via a crossover cable!"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by Rytron on 2008-11-07
Hi,
I want to connect XP to Ubuntu via a crossover cable.
I need a simple step by step method.
I want to be able to share files between them.
Thanks.

---

### Post by kerpow on 2008-11-07
I take it you have a cross over cable.  If not you can find how to make one (just Google).

Next up you need to assign an IP address to both machines.  You can do this via the control panel in Windows and via the Network Manager in Ubuntu.  (For more info on how use Google).

Assign somthing like this:

ip:192.168.1.1 to Ubuntu
ip:192.168.1.2 to Windows
Network mask to both will be 255.255.255.0

With that done and the cable plugged in, you should be able to ping one from the other.

In XP : Start > Run > cmd <enter>

> ping 192.168.1.1

Should get you a nice list of replies.

And in Ubuntu : Applications > Accesories > Terminal <click>

> ping 192.168.1.2

Now this might not show any replies, if not you might need to fiddle with your XP (or third party) firewall.

Next you are after is Samba.  There is both a Samba server and client for Ubuntu that will allow it to exchange files with Windows machines.  Samba clinet is installed by default with Ubuntu so you will be able to see shared files on your XP machine already.

Make sure you have a folder on your XP machine shared:

Right click on a folder,
Click 'properties', then the 'sharing' tab (differs from Home and Pro).
Click 'Share this folder' and click <OK>.

In Ubuntu, click : Places > Home Folder.
Then in the window that apears click 'Go' > 'Location'
In the address bar that apears type:
smb://192.168.1.2

When you press enter you should be able to see the folder you just shared on yout XP machine.

---

### Post by kerpow on 2008-11-07
Once you have done that, if you want to see files from your Ubuntu machine on your XP machine:

[http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)

Saves me some typing.

---

### Post by Rytron on 2008-11-08
> **kerpow said:**
> I take it you have a cross over cable.  If not you can find how to make one (just Google).

Next up you need to assign an IP address to both machines.  You can do this via the control panel in Windows and via the Network Manager in Ubuntu.  (For more info on how use Google).

Assign somthing like this:

ip:192.168.1.1 to Ubuntu
ip:192.168.1.2 to Windows
Network mask to both will be 255.255.255.0

With that done and the cable plugged in, you should be able to ping one from the other.

In XP : Start > Run > cmd <enter>

> ping 192.168.1.1

Should get you a nice list of replies.

And in Ubuntu : Applications > Accesories > Terminal <click>

> ping 192.168.1.2

Now this might not show any replies, if not you might need to fiddle with your XP (or third party) firewall.

Next you are after is Samba.  There is both a Samba server and client for Ubuntu that will allow it to exchange files with Windows machines.  Samba clinet is installed by default with Ubuntu so you will be able to see shared files on your XP machine already.

Make sure you have a folder on your XP machine shared:

Right click on a folder,
Click 'properties', then the 'sharing' tab (differs from Home and Pro).
Click 'Share this folder' and click <OK>.

In Ubuntu, click : Places > Home Folder.
Then in the window that apears click 'Go' > 'Location'
In the address bar that apears type:
smb://192.168.1.2

When you press enter you should be able to see the folder you just shared on yout XP machine.

I presume the same method is used when connecting a Vista computer to an Ubuntu computer.
I can ping the Ubuntu IP address from the Windows pc. From the Ubuntu pc I cannot ping the Windows machine. I closed the 3rd party firewall. I am not using the Windows firewall.

In Ubuntu when I assign a manual IP address, what must I asign as the NetMask? Would 255.255.255.0 suffice? What will I use as the gateway? What about 10.0.0.1 as the DNS server?

---

### Post by kerpow on 2008-11-09
Yes, the same for Vista.

If you can ping one way you should be able to ping the other unless there is a firewall issue.  So as you have them turned off thats a little odd.

Yes the netmask should be 255.255.255.0, you shouldn't need a default gatway, but you may as well set it to the IP of the other computer, and there is no need at all for DNS.

So machine one: 
IP: 192.168.1.1
NM: 255.255.255.0
GW: 192.168.1.2

and machine two:
IP: 192.168.1.2
NM: 255.255.255.0
GW: 192.168.1.1

That should do the trick. Let me know.

---

### Post by Rytron on 2008-12-16
> **kerpow said:**
> That should do the trick. Let me know.

Please excuse late reply. It works. Thank you.

):P

---

