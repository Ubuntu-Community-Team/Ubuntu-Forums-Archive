---
title: "VNC in a school situation"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by Shambler2 on 2007-05-17
Hello!

I'm fairly new to Ubuntu Feisty (2 weeks or so), and so far I'm loving it! I work at a school as one of the network administrators, and I've run into a little problem. Most of the tasks we do we've been able to find alternative ways of doing, except one. 
When called up about a problem in the past, we would use TightVNC (Windows) to connect to that person's computer by typing in the computer name (eg. BILL). Using Ubuntu, we can still VNC computers, but only if we know the I.P. address. This can be a big problem because we have 350+ computers, and it's impossible to remember all the computer names. 
Is there any way of making Ubuntu connect to the DNS so it's able to resolve the names into IP addresses? This will make our job a lot easier, at the moment we're running windows in VM for the sole reason of being able to use VNC easily.
Thanks for any help,

Sam

---

### Post by jonallport on 2007-05-17
Sorry if this sounds like a dumb question, but is the issue with VNC or DNS?  From what you've said it looks like you need your Ubuntu client(s) to register their DHCP-assigned IP addresses with the DNS server at boot, like Windows clients do.

If this is the case then you need to have a look at nsupdate, that's the utility for dynamic registration of DNS entries.

Hope that helps.

---

### Post by Shambler2 on 2007-05-28
I'm fairly certain the issue is with DNS, so I'm going to try that utility you mentioned, thanks a lot! =D

EDIT: Apparently not, I just thought about it some more and that's not quite the case. 

What I'm trying to do is use VNCviewer on my Ubuntu box, and connect to windows clients, as the rest of the network is Windows.
This works if you specify the IP address manually, but I can't seem to do what I can with the windows version, which is type in the machine name to connect.
Should have really clarified that, sorry
Thanks for you help and any more that you can give,
Sam

---

### Post by jonallport on 2007-05-30
Right-O, I'd got you the wrong way 'round!

I think you need to look at the DNS config on the Ubuntu box.  If name resolution wasn't working at all then it wouldn't work from ANY client, hence it looks like it just the way the Ubuntu box is configured.

Question: Do you use static IP addressing or DHCP?

Check /etc/resolv.conf contains a valid domain and DNS server IP address

I'm willing to bet real, actual, cash money that you are using DHCP and there will be no 'domain' value in your /etc/rosolv.conf.  I reckon that the DHCP server is not issuing default domain suffix, hence you can't resolv by hostname alone (test this by specifying a fully qualified domain name (FQDN) in your VNC client).  I don't think the Windows clients will have this problem because they will be using a default domain suffix gleaned from the ADS/Domain/Workgroup settings.

I hope I'm right, otherwise I have no idea, but I'll do what I can anyway!

J

---

### Post by Shambler2 on 2007-05-31
Hmm, that sounds interesting! I'll try that when I get to work tomorrow, thanks a lot! If this works, it'll make things a LOT easier =D
We use a Novell network, so here's hoping that'll work! =D
Sam

---

### Post by jonallport on 2007-06-01
Using Novell, hmm interesting!  What do(es) you Novell server(s) serve?

The reason I ask is your problem fits perfectly with using Windows/Active Directory but the DNS/DHCP parts of Netware (and OES of course) are Unix-like so shouldn't behave in the same way.

J

---

### Post by Shambler2 on 2007-06-01
I didn't  get a chance to test it out today, but we use Netware 6.5, serving the DNS, DHCP, files, printers, and the internet, mainly focused on Windows PCs. Recently support for Macs has been added, though they haven't implemented Linux support just yet.
That's why I mentioned it, I figured it could be possible that something might be different
Thanks for you help so far! =D
Sam

---

### Post by jonallport on 2007-06-01
Are you using Zenworks for workstation management or do they just 'do what they do' and rely on Netware scripts for mapping etc?

What I'm trying to get to the bottom of is if the Windows clients are picking up a domain suffix (ADS or workgroup name) amonst themselves or whether the domain suffix is issed form DHCP (unlikely given the symptoms) or via Zen policy.

Could you post a sample ipconfig /all from a working Windows machine and /etc/resolv.conf from your linux box?

Thanks
J

---

### Post by Shambler2 on 2007-06-01
Well, see it's funny there =P We're sort of half using Zenworks, though we haven't really implemented it fully either. It's all a work in progress/mess =P 
Mapping is done entirely by scripts at this stage. 
That's a point. I didn't really think about that part. 
I'll grab them for you on Monday morning, thanks for being such a great help!
Sam

---

