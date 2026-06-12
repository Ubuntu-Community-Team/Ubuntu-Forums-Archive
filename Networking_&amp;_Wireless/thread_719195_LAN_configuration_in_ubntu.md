---
title: "LAN configuration in ubntu"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by nagaraj on 2008-03-08
i had  a LAN of 8pcs working on windows xp. recently i changed over to ubuntu on two. liked it and started installing ubuntu on all machines (gutsy). everything was fine till i replaced windows with ubuntu on the last pc. now none of the pcs recognise any other pcs on the network ( i mean places>network shows 'windows network' but on clicking goes blank) all pcs can ping all others on the network. i've installed samba in all the pcs. can anybody help me with a step by step guide to have a proper network? tried searches and got lost in the wilderness of info not understanding a damn thing and just geting myself confused. i thought atleast the names of pcs on the network should appear on clicking places>network, even if file sharing doesn't work? or am i wrong?.

---

### Post by Eiríkr on 2008-03-08
Part of the problem is that Windows is one heck of a promiscuous setup, it happily broadcasts its presence to all and sundry.  However, even on Windows, you have to set up a share (usually by right-clicking a folder and selecting "Sharing and Security", though some things are [somewhat frighteningly] shared by default).  On Ubuntu, you have to set up shares too (and there are *no* default shares open right off the bat).  

However, if you're only sharing between Ubuntu machines, Samba is definitely *NOT* your best bet.  Have a look at [post=4387032]this post[/post] about setting up NFS sharing.  Or, if you'd prefer, you can install the openssh-server package (on *each machine* you want to share *from*) and instead use the [font=courier]fish://[/font] protocol in Konquerer, or the [font=courier]sftp://[/font] protocol in either Konqueror or Nautilus.  (You'd add the hostname after the double-slash -- note that the hostname *must be known* to the machine you're typing this in on, which means either a) you've got DNS set up, or b) you have added all hostnames and related IP addresses to the /etc/hosts file.  Otherwise, instead of hostname, you'll have to type the IP address.)

HTH,

Eiríkr

---

### Post by nagaraj on 2008-03-09
thanks for that but i must tell u i'm still confused. i mean still i dont understand why the pcs on the network are not detected? when i was using windows all workgroup computers were seen irrespective of whether there were shared folders on them or not. moreover i can understand so far as installing nfs and then i am not so sure how to go further. how can i set up a workgroup/domain and make other pcs in the network 'clients'? right now i can connect to the internet through a dsl modem connected to a hub on the network and for this purpose i have added the ip address of 'opendns' 208.67.222.222 in the 'DNS' tab of network configuration. i've not touched any other part of the network configuration. i've also created atleast one shared folder in each pc with samba.

---

### Post by HereInOz on 2008-03-09
I have known this issue to happen if you have one PC on the network which is blocking SMB from the others.  Make sure that all your machines have the firewall configured to allow open communication between them all, or at least ports 135 - 139 allowed on all machines.

It may not be that this is the cause, but I felt it was worth a mention as it has happened to me in the past.

---

### Post by HereInOz on 2008-03-09
On second thougths, it also sounds like a browsemaster issue.  The Windows machine was acting as the Browsemaster for the network and when you removed it, the network didn't know where everything was.

If you put a Windows machine back in there, and it all works, then it is probably a Browsemaster problem, but unfortunately I can't offer you definitive assistance with it, as I have never had to solve such an issue.

Try accessing machines by their IP addresses rather than their network names - that might make a difference.  Use the "Connect to Server" function and connect using the IP address rather than the host name, and see how you go.

Do you have samba users set up on all machines, as well as the samba shares active?

---

### Post by Eiríkr on 2008-03-09
> **nagaraj said:**
> thanks for that but i must tell u i'm still confused. i mean still i dont understand why the pcs on the network are not detected? when i was using windows all workgroup computers were seen irrespective of whether there were shared folders on them or not. 

Reread:
> Part of the problem is that **Windows is one heck of a promiscuous setup, it happily broadcasts its presence to all and sundry**...

Ubuntu doesn't do this, *by design*.  There's more set up involved before your machines become visible and accessible to others.  It might be less convenient, but it's still far better than getting rooted before you're even done installing.  

> **nagaraj said:**
> moreover i can understand so far as installing nfs and then i am not so sure how to go further. how can i set up a workgroup/domain and make other pcs in the network 'clients'? 

NFS is completely different from Samba -- *there are no workgroups*.  If you've followed the full setup directions in the post I linked to above, including the second section about setting up and restarting Avahi, you should be able to see your shares in Konquerer (provided you also have the kdnssd package installed, which should come by default if you get the full KDE install) by typing in [font=courier]zeroconf:/[/font] in the address bar.  Gnome's Nautilus is sadly substantially less functional and has neither any [font=courier]zeroconf:/[/font] nor [font=courier]nfs:/[/font] browsing support, so if you really don't like Konqueror and prefer Nautilus, you'll need to mount the NFS shares manually.  Or easier still, go with openssh and the [font=courier]sftp://[/font] approach.

> **nagaraj said:**
> right now i can connect to the internet through a dsl modem connected to a hub on the network and for this purpose i have added the ip address of 'opendns' 208.67.222.222 in the 'DNS' tab of network configuration. i've not touched any other part of the network configuration. i've also created atleast one shared folder in each pc with samba.

So no, you do not have a DNS server running on your network.  Consequently, none of your Ubuntu machines are going to know the hostnames of other machines, except possibly by means of the nmbd (Samba Netbios name server) process, which is consulted during Samba connections.  

HereInOz has a good point -- are you sure your Samba shares are active?  Pick a machine you want to share *from*, log in, and type [font=courier]ps aux | grep mbd[/font].  This should show a list of running processes with the string "mbd" somewhere in their names, which should therefore show your smbd (Samba daemon) and nmbd (Samba Netbios name daemon) -- *if* they're running.  If either (or both) of them are missing, type [font=courier]sudo /etc/init.d/samba restart[/font] to restart Samba.  Double-check that both smbd and nmbd are running (use the [font=courier]ps[/font] command again; it's okay if you get multiple instances).  If they're *still* not running, check the log of the missing one(s) by typing either [font=courier]less /var/log/samba/log.smbd[/font] or [font=courier]less /var/log/samba/log.nmbd[/font], whichever one is missing, and copy what you find into a post in this thread, together with the contents of your smb.conf file ([font=courier]less /etc/samba/smb.conf[/font]).

I know this is all a bit complicated and a bit of a PITA, but there's a fine line between convenience, and dangerous availability.  The Wonderful World of Windows Worms has shown us what happens when things are *too* convenient.  :-|  Anyway, bear with us, and we'll get you set up.  :D

Cheers,

Eiríkr

---

### Post by nagaraj on 2008-03-09
well i am confused alright but i can see a ray of the light at the end of the tunnel. i will try all that u've suggested or atleast as far as i can go and then get back with a load of further queries (i'm sure). thanks for ur help but let me tell u this is far from over

---

### Post by Eiríkr on 2008-03-09
No trouble at all, we'll be here.  :)  And learning system-level stuff (which is what you're doing now) is a long, long road -- but hopefully a rewarding one.  :D

Cheers,

Eiríkr

---

### Post by the.dark.lord on 2008-03-11
posted by mistake. my apologizes.

---

