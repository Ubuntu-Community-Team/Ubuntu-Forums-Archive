---
title: "Can Anyone Help with Linux to Linux File Sharing"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by Ingla on 2007-06-19
Hello.

I have two machines running Dapper. I have shared the Home directories using SMB. I did the following on both computers:

sudo aptitude install samba

sudo smbpasswd -a (my name )

sudo smbpasswd -e (my name )

Under Places>Network Servers, I see a network (other than the one I have to a Windows machine) but can see no files from either machine (neither the one I'm on nor the one I'm trying to connect to).

Setting up a network to a windows box was a snap, but Linux to Linux has me frustrated. I'm a bit afraid to try NFS because of security problems and because I don't fully understand the instructions. FTP would be OK if someone could walk me through it. Meanwhile, I'm half way into the SMB thing so, if that could be fixed, great.

It would be nice to have a two way network, but if it has to be server-client, I can live with that.

Can anyone please set me straight on how to get this working (remembering that I need a command by command walk through as I've never set up a Linux to Linux network and know nothing about it)?

Any help appreciated.

Thanks.

---

### Post by hartz on 2007-06-19
Hi there Ingla.

You are not the only one finding NFS hard.  Fortunately everything is only difficult the first two times you do it.

In this thread I discussed in soe depth how to use NFS:
[http://ubuntuforums.org/showthread.php?t=451400](http://ubuntuforums.org/showthread.php?t=451400)

Have a look at it and see if it answers your questions.

You mention security ... what is it that is bothering you about NFS security?

P.S. Once you've got NFS set up, it is stable and FAST.  I really recommend it.

---

### Post by bodhi.zazen on 2007-06-19
+1 NFS >:)

[http://doc.gwos.org/index.php/NFS_Easy_Way](http://doc.gwos.org/index.php/NFS_Easy_Way)

Takes less then 10 minutes

---

### Post by Ingla on 2007-06-19
Thanks for the replies.

Re: security of NFS, I just read that, if I didn't get some things right, my machine would be open to invasion by anyone who knows how (for example, by spoofing an IP that is OK's by the system). I understand there are measures to take to help prevent this, but do not fully understand what they are or how to implement them.

Generally, I have some trouble understanding some of the answers you point me to.  

1.My machines are all connected through a hub to a router. Computer 1 is connected with a static IP on eth2 and Computer 2 (just did fresh Dapper install) is using DHCP (eth0). (I'm not sure how the 1st machine got on eth2. There were two cards at one point and one was removed (one of my kids did that while setting up his Windows network, so I don't really know details) ... Ubuntu just configured itself that way). (There is a Computer 3, but it's only running Windows (for now) and that network works fine with Computer 1 running Ubuntu).

2.If I do sudo dpkg-reconfigure portmap, what will happen? I ran dpkg-reconfigure once on something else (at the suggestion of someone on the forum) and was presented with a whole lot of questions I didn't know how to answer. I mainly went for the defaults presented and, somehow, it all worked out.

If I run it for this, what do I have to know first (what will it ask me to decide)?

3."For Full Read Write Permissions allowing any computer from 192.168.1.1 through 192.168.1.255 "

How do I know what IP range I want (as I mentioned, one machine has an IP I assigned and the other is set for DHCP [so far]). I'm sure, if i check ifconfig, it has an IP which isn't in the same range (unless I allow the whole world in).

Do I need to try to make a static IP for machine 2?

As I said, I kind of need a walk through.

Thanks.

---

### Post by bodhi.zazen on 2007-06-19
> **Ingla said:**
> Thanks for the replies.

Re: security of NFS, I just read that, if I didn't get some things right, my machine would be open to invasion by anyone who knows how (for example, by spoofing an IP that is OK's by the system). I understand there are measures to take to help prevent this, but do not fully understand what they are or how to implement them.

You are on a router, so security is less an issue.

> Generally, I have some trouble understanding some of the answers you point me to.  

1.My machines are all connected through a hub to a router. Computer 1 is connected with a static IP on eth2 and Computer 2 (just did fresh Dapper install) is using DHCP (eth0). (I'm not sure how the 1st machine got on eth2. There were two cards at one point and one was removed (one of my kids did that while setting up his Windows network, so I don't really know details) ... Ubuntu just configured itself that way). (There is a Computer 3, but it's only running Windows (for now) and that network works fine with Computer 1 running Ubuntu).

It is nice to put the server on a static IP so the address does not change.

You can leave the client on DHCP

Sounds as if the numbering of the cards is a residual of having two cards at one point.

> 2.If I do sudo dpkg-reconfigure portmap, what will happen? I ran dpkg-reconfigure once on something else (at the suggestion of someone on the forum) and was presented with a whole lot of questions I didn't know how to answer. I mainly went for the defaults presented and, somehow, it all worked out.

If I run it for this, what do I have to know first (what will it ask me to decide)?

Hmm .... You do not need to re-configure portmap ...

> 3."For Full Read Write Permissions allowing any computer from 192.168.1.1 through 192.168.1.255 "

Yes, that allows for any box on your LAN to access the nfs server. Use this unless you want to use static IP and manually add each address to the server.

> How do I know what IP range I want (as I mentioned, one machine has an IP I assigned and the other is set for DHCP [so far]). I'm sure, if i check ifconfig, it has an IP which isn't in the same range (unless I allow the whole world in).

Sounds like you need to do some reading on networking and networking protocols. 

IP = phone number.

On your LAN your phone numbers range from 192.168.1.1 (this is the router) to 192.168.1.255. Your router may be able to handle I think up to 100 connections, so you will not use all the numbers.

Static = you choose and set the IP (phone number)
DHCP = router will set phone number automatically.

This IP is ONLY on your local LAN. Your IOP provider uses DHCP and gives you a different # for the internet.

So how do you know the range ? YOU set one automatically with a static IP, or you use DHCP and you router will do it all automagically. The range is determined by the type of router you have.

> Do I need to try to make a static IP for machine 2?

No

> As I said, I kind of need a walk through.

Thanks.

The link I gave you is a walk through. Sounds like you want a read through, which is fine.

NFS : [http://nfs.sourceforge.net/nfs-howto/](http://nfs.sourceforge.net/nfs-howto/)

Networking : [http://tldp.org/HOWTO/Networking-Overview-HOWTO.html](http://tldp.org/HOWTO/Networking-Overview-HOWTO.html)

---

### Post by srt4play on 2007-06-19
I use sshfs and gftp to do the file transfers because it's easy to set up and it works.  Just throwing it out there as an alternative.

---

### Post by Ingla on 2007-06-19
Thanks.

I'll read through the suggested material and get back.

---

### Post by Ingla on 2007-06-19
Thanks.

I'll read through the suggested material and get back.

One question, though. Where do you get "On your LAN your phone numbers range from 192.168.1.1 (this is the router) to 192.168.1.255?" Is that an example, or is it a standard, i.e. are those the numbers I really use?

---

### Post by Mr. C. on 2007-06-19
> **Ingla said:**
> One question, though. Where do you get "On your LAN your phone numbers range from 192.168.1.1 (this is the router) to 192.168.1.255?" Is that an example, or is it a standard, i.e. are those the numbers I really use?

Read: Networking Basics notes : [http://cis68c1.mikecappella.com/](http://cis68c1.mikecappella.com/)

MrC

---

### Post by bodhi.zazen on 2007-06-20
> **Ingla said:**
> Thanks.

I'll read through the suggested material and get back.

One question, though. Where do you get "On your LAN your phone numbers range from 192.168.1.1 (this is the router) to 192.168.1.255?" Is that an example, or is it a standard, i.e. are those the numbers I really use?

Do you have the information that came with your router ?

Try opening firefox and putting : ```
192.168.2.1
``` into the browser (where you would type [www.google.com](www.google.com))

This should bring up a config  page for your browser.

*Stay with it*

---

### Post by Ingla on 2007-06-20
Sorry, t, if Iook off for some sleep. It was 4:00 AM here.

Re: router documentation, I'm not sure there is any. But I know its IP, as in to log in to it's admin interface. I gave Computer 1 an IP one number higher than the router itself. E.G. - router: 10.0.0.108, computer 10.0.0.109. I'm not sure what Windows is doing, but checking IP on that box usually shows something like 10.0.0.1 or 2 or 3. I checked an old linux machine we had running here on DHCP and it showed something like 10.0.0.4, if memory serves.

Typing 192.168.2.1 into the address bar doesn't take me anywhere. Typing the router's IP takes me to the router admin login page.

In any case, I haven't yet read the material, but, if my router IP and the IP I gave the machine are the numbers we're talking about, it seems I would either have to use a range like 10.0.0.1 - 10.0.0.109 OR, give Computer 2 a static IP like 10.0.0.110 and use a range like 10.0.0.8-10.0.0.110. 

Am I on the right track?

One more issue. When sharing a directory, I need to share it as SMB or NFS. The connection to the Windows box uses smbfs plugin. If I share the folder on Computer 1 using NFS (to connect to the Linux box), will that break the network to Windows? Would I need to change the sharing method manually to connect to each machine?

---

### Post by bodhi.zazen on 2007-06-20
> **Ingla said:**
> Sorry, t, if Iook off for some sleep. It was 4:00 AM here.

Re: router documentation, I'm not sure there is any. But I know its IP, as in to log in to it's admin interface. I gave Computer 1 an IP one number higher than the router itself. E.G. - router: 10.0.0.108, computer 10.0.0.109. I'm not sure what Windows is doing, but checking IP on that box usually shows something like 10.0.0.1 or 2 or 3. I checked an old linux machine we had running here on DHCP and it showed something like 10.0.0.4, if memory serves.

Typing 192.168.2.1 into the address bar doesn't take me anywhere. Typing the router's IP takes me to the router admin login page.

In any case, I haven't yet read the material, but, if my router IP and the IP I gave the machine are the numbers we're talking about, it seems I would either have to use a range like 10.0.0.1 - 10.0.0.109 OR, give Computer 2 a static IP like 10.0.0.110 and use a range like 10.0.0.8-10.0.0.110. 

Am I on the right track?

Yes. Looks like I got the wrong IP from your previous post. Usually the IP of the router ends in a 1, but it depends on your router. Looks like your router may be 10.0.0.108 ?

> One more issue. When sharing a directory, I need to share it as SMB or NFS. The connection to the Windows box uses smbfs plugin. If I share the folder on Computer 1 using NFS (to connect to the Linux box), will that break the network to Windows? Would I need to change the sharing method manually to connect to each machine?

NFS will not affect a windows network. Actually Windows is capable of serving as both a NFS server and client. Yes, you can mount a nfs share on windows :)

[http://doc.gwos.org/index.php/MountNFS](http://doc.gwos.org/index.php/MountNFS)

I prefer this over samba because I think nfs on a Linux server is more secure. You need to isolate the shared directory from everything else (don't share /home, share /mnt/data/nfs_shares or some such).

---

### Post by Ingla on 2007-06-20
Thanks. Sorry this reply is so long. It contains a lot of info.

Right, my router is at 10.0.0.138.
Re: NFS and Windows, I saw somewhere it's dangerous to use it to write to an NTFS file sytem.

Also, until now, I **have** shared the Home folders. Could change that.

In any case, I've been reading and trying things. No go!

Here's a summary of some things I've tried and some terminal outputs to provide information that someone probably understands much better than I. 

SMB
------
I guy on the forum wrote this:

sudo aptitude install samba (it was already installed)

sudo smbpasswd -a (my name )

sudo smbpasswd -e (my name )

just right click the files you want to share ... you will find your shares in places network.

Under Places>Network Servers, I see a network (other than the one I have to a Windows machine) but can see no files from either machine (neither the one I'm on nor the one I'm trying to connect to).


====================================================================================
**NFS**
-----
Verifying that NFS is running (from a How To)
To do this, query the portmapper with the command rpcinfo quota to find out what services it is providing. 

**rpcinfo quota**
-----------------------------
Usage: rpcinfo [ -n portnum ] -u host prognum [ versnum ]
       rpcinfo [ -n portnum ] -t host prognum [ versnum ]
       rpcinfo -p [ host ]
       rpcinfo -b prognum versnum
       rpcinfo -d prognum versnum

"if you do not at least see a line that says portmapper, a line that says nfs, and a line that says mountd then you will need to backtrack and try again to start up the daemons."
??!!??

-------------------------------
INFO
------------------------------
**netstat -rn**
----------------
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.0.0.0        0.0.0.0         255.0.0.0       U         0 0          0 eth2
0.0.0.0         10.0.0.138      0.0.0.0         UG        0 0          0 eth2

**ifconfig -a**
---------------
eth2      Link encap:Ethernet  HWaddr 00:17:31:91:F4:90
          inet addr:10.0.0.139  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::217:31ff:fe91:f490/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2450826 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2678398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1475425349 (1.3 GiB)  TX bytes:1641956224 (1.5 GiB)
          Interrupt:209 Base address:0x6c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:377 errors:0 dropped:0 overruns:0 frame:0
          TX packets:377 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:37369 (36.4 KiB)  TX bytes:37369 (36.4 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

**ps aux | grep portmap**
-----------------------------------
daemon    3755  0.0  0.0   1668   356 ?        Ss   Jun19   0:00 /sbin/portmap
aba       4534  0.0  0.0   2888   808 pts/0    R+   17:20   0:00 grep portmap

----------------------
**NFS Question** (Quote from How To):
----------------------
 /etc/hosts.allow and /etc/hosts.deny
"...in addition to controlling access to services handled by inetd (such as telnet and FTP)."

Is this going to mess up my ftp downloads (or telnet -which I almost never use) if I don't specifically allow every ftp server?

I have not modified these files pending an understanding of this issue.


====================================================================================
**SSH** (From a How To)
----
Transferring Files Remotely With SSH
Graphically (from GNOME)
---------------------------------------------------

Nautilus can access remote computers via SSH, and browse and transfer files. Click File -> Connect to Server. Select SSH for Service Type, write the name or IP address of the computer you're connecting to in Server, the user you'd like to connect as in User Name, and a name for the connection if you wish.

Files can be copied by dragging and dropping between this window and other windows. 

Command Line
-----------------------
ssh <username>@<computer name or ipaddress>

I tried the GUI a couple of times and the command line once.
Command line returned "connection refused". Some forum I googled said that means port 22 is closed.
----------------------------------------------------------------------------------------------------------------------------------------------
**INFO:**
----------------------------------------------------------------------------------------------------------------------------------------------
**iptables -L**
---------------
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


---------------------------------------------------------------------------------------------------------------------------------------------------------


opened port 22 in my router for both IP's.
NOTHING.

Then I noticed two folders had been placed on my Desktop with different names for the other computer. Neither could be opened (Cannot Display ... Connection Failed)
==================================================================================
**sshfs and gftp**
---------------------
Any how-to's for that around?
==================================================================================
This whole thing is getting to be a bit much! Absolutely nothing works the way folks say it should ... or something's missing here ... or I'm missing something. As it stands I have to upload files to an ftp server and download on the other machine... or burn them to a CD. All possible, but what a pain!

All I did to connect to the Windows box was to install the smbfs plugin ad share the folder. It's there in Network Servers whenever I boot and just works. That's what I'm trying to do  Linux to Linux. It's a good thing this network isn't mission critical ... I'm just trying to learn Linux (plus it would be a lot more convenient than the methods mentioned above).

---

### Post by notwen on 2007-06-20
[Hamachi]("https://secure.logmein.com/products/hamachi/default.asp") is easy enough, you should give it a try. =]

---

### Post by Mr. C. on 2007-06-20
> **Ingla said:**
> This whole thing is getting to be a bit much! Absolutely nothing works the way folks say it should ... or something's missing here ... or I'm missing something. As it stands I have to upload files to an ftp server and download on the other machine... or burn them to a CD. All possible, but what a pain!

Ingla,  I'd like to advise that you take one step at a time.  You seem to be trying to configure many services all at once, and this will only confuse matters.

You have some basics to learn first, and without that, this process will seem like voodoo.

I noted in your posted routing table, there is no route for the loopback network.  Was that simply omitted from cut and paste, or is there no 127.0.0.0 route like:
```
127.0.0.0       *               255.0.0.0       U     0      0        0 lo
```

Let's step back to the basics.  What **one** goal are you trying to solve?

MrC

---

### Post by Ingla on 2007-06-20
Hello. Thanks for the reply.

If you mean the output from netstat -rn, that's all there is. I ran it again. Or did you mean the output for another command ... I really know nothing about these except to post results for those more knowledgeable.

As for what I'm trying to accomplish, it's as I wrote:

"All I did to connect to the Windows box was to install the smbfs plugin and share the folder. **It's there in Network Servers whenever I boot and just works.** That's what I'm trying to do Linux to Linux."

I really don't care which way I get it working, as long as I don't wind up wide open to all kinds of easy intrusions.

The methods I tried were just what people suggested. So, when one didn't work, I tried another.

1. I want some kind of network (primarily for simple, though sometimes large, file transfers), even if all transactions have to be initiated from one computer (unlike my Windows to Windows network, which works in both directions).

2. I don't want it to break  my existing Linux to Windows connection, which uses the smbfs plugin.

3. I don't want to use a method that would endanger an NTFS file system by writing to it (the smbfs plugin seems fine).

4. I don't want too many security risks. Even though this is a home network, who knows? I'm behind a router but, there are all kinds of folks out there.

Thanks for your help. If you can tell what might work from the info I provided, or if more would help, please let me know.

---

### Post by bodhi.zazen on 2007-06-20
Ingla : AWESOME

I love seeing a new user willing to learn, and sink their teeth into it :)

Don't get frustrated, you are learning stuff that has been hidden to you from your old os.

BUT do not make it more complicated either ...

Samba shares work "out of the box" with fiesty :)

Go to your windows box and enable shared folders.

Go to Locations -> Network -> windows -> and you should be able to see the shared folder.

It is pretty much like this :

[http://lifehacker.com/software/mac-os-x/how-to-mount-a-windows-shared-folder-on-your-mac-247148.php](http://lifehacker.com/software/mac-os-x/how-to-mount-a-windows-shared-folder-on-your-mac-247148.php)


===========


See ? easy ..

OK next you can work through nfs or ftp if you like.

Keep in mind there are two steps :

1. Configure server

2. Configure client.

If you have problems, disable the firewall to make sure that is not what is holding you up ... 

 ===========


Don't try to do it all at once :)

---

### Post by Ingla on 2007-06-20
Thanks.

The Windows connection is no problem. Uses smbfs plugin and is only "one-way", but that's OK. I use it regularly.

I have no firewall, except what Ubuntu uses out of the box ... iptables. If I read this correctly, it isn't the problem:
--------------------------------------------
iptables -L
---------------
Chain INPUT (policy ACCEPT)
target prot opt source destination

Chain FORWARD (policy ACCEPT)
target prot opt source destination

Chain OUTPUT (policy ACCEPT)
target prot opt source destination
-----------------------------------------------

The router, of course, might cause a problem if I need to open some specific port. It isn't blocking the connection to Windows or normal ftp ports, as I'm always uploading and downloading things.

Can you tell me how to do the ftp method? Entering an IP, user name, and password in gftp just gets "connection refused".

Thanks.

---

### Post by bodhi.zazen on 2007-06-20
Well, yes, but not at the moment.

I almost would advise you start a new thread specific to ftp or look in the server forums. Others will help you as well.

If you would like help, more info please.

What is your ftp host ? Windows or Ubuntu ?

What how-to are you following ?

---

### Post by Mr. C. on 2007-06-20
Stop and restart the loopback interface:

```
ifdown lo
ifup lo
```

See if netstat -rn shows a route for 127.0.0.1.  Without this, you'll have all sorts of networking troubles, one of which is that NFS can't work (no way for it to contactf portmap).

MrC

---

### Post by Ingla on 2007-06-20
Thanks for the replies.

bodhi.zazen,

FTP host is Linux (trying to make Linux to Linux network ... two machines running Dapper).

I don't have a how-to for FTP.

Mr. C.,

I ran ifdown lo and ifup lo. No change in netstat -rn output:

-----------------------------------------------------------------------
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.0.0.0        0.0.0.0         255.0.0.0       U         0 0          0 eth2
0.0.0.0         10.0.0.138      0.0.0.0         UG        0 0          0 eth2
------------------------------------------------------------------------

Any ideas?

---

### Post by bodhi.zazen on 2007-06-20
Well, for the ftp server, see if this helps :

[http://doc.gwos.org/index.php/FTP_Server](http://doc.gwos.org/index.php/FTP_Server)

---

