---
title: "Ubuntu as a VPN client"
date: 2005-11-02
forum: Networking &amp; Wireless
---

### Post by Wharry on 2005-11-02
I want to set up an Ubuntu box as a VPN client to hook a remote network. It doesn't need to be a permanent link just as and when needed. Something that replicates the Windows VPN client would be ideal, but I have yet to find anything for Linux that is that simple. I don't want to over complicate the procedure to prevent any confusion for the user. Any pointers?

---

### Post by hajk on 2005-11-03
I recommend installing the "vpnc" package, which has the same functionality as the well-known Cisco VPN client. You should prepare (with sudo gedit) a configuration file for your connection, /etc/vpnc/<name>.conf, where <name> is any name that you give the connection. This file needs the following 
lines (use only a single space between words):

IPSec gateway <address>
IPSec ID <groupID>
IPSec secret <groupSecret>
XAuth username <yourID>
XAuth password <yourPW>

ask your IT people for <address>, <groupID> and <groupSecret>.
The connection is started with the command "sudo vpnc <name>.conf".
Alternatively, you could start with "sudo vpnc" and then the info will be requested interactively. Note that the "vpnc-connect" script, mentioned in the documentation, is no longer available. The connection is closed by issuing the command "sudo vpnc-disconnect".

Don't install the "resolvconf" package to handle the change in nameservers in /etc/resolv.conf -- vpnc is quite capable of handling that and restoring that file after disconnecting. 

Passing VPN traffic through a firewall requires some additional rules. If you use Firestarter, then add the following to /etc/firestarter/user-pre (you may have  to make this file writable first with the command "sudo chmod 600 ...."):

iptables -A INPUT -j ACCEPT -s <address> -p esp
iptables -A INPUT -j ACCEPT -s <address> -p udp -m multiport --sports isakmp,10000
iptables -A INPUT -j ACCEPT -i tun+
iptables -A OUTPUT -j ACCEPT -d <address> -p esp
iptables -A OUTPUT -j ACCEPT -d <address> -p udp -m multiport --dports isakmp,10000
iptables -A OUTPUT -j ACCEPT -o tun+
\end{verbatim}

where <address> is the same as above. Note that the instructions in the Firestarter on-line documentation on passing VPN IPSec traffic do not apply to vpnc (and do not work).

I hope this works for you, it did for me...:smile:

---

### Post by reuben on 2005-11-28
You can also try using GuardDog instead of Firestarter. Open PPTP and VPN in the internet zone.

---

### Post by naomi on 2005-11-28
Hey, many thanks hajk! When I installed Ubuntu about a month ago I exactly had the same problem. I tried various things (including the solution posted on the firestarter website), but nothing worked. So I ended up, using my vpn connection with a disabled firewall :( But I just found your post and it works for me, too! :)

Thanks again!
Naomi

---

### Post by jmooney on 2005-11-28
[QUOTE=naomi]Hey, many thanks hajk! When I installed Ubuntu about a month ago I exactly had the same problem. I tried various things (including the solution posted on the firestarter website), but nothing worked. So I ended up, using my vpn connection with a disabled firewall :( But I just found your post and it works for me, too! :)

Thanks again!
Naomi[/QUOTE]

OK, your VPN tunnel is active, can you tell me step-by-step how you actually browse files?  Firefox? Nautilus? whatever....I just want to be able to see my files and nobody seems to be able to tell me what I'm supposed to do.

Can anybody tell me how to browse files on the other side of the VPN tunnel?

Thank you

Joe

---

### Post by cwaldbieser on 2005-11-28
[QUOTE=jmooney]OK, your VPN tunnel is active, can you tell me step-by-step how you actually browse files?  Firefox? Nautilus? whatever....I just want to be able to see my files and nobody seems to be able to tell me what I'm supposed to do.

Can anybody tell me how to browse files on the other side of the VPN tunnel?

Thank you

Joe[/QUOTE]
The VPN tunnel just acts like a link over the Internet.  It makes two networks look like they are connected instead of being seperated by the whole Internet.  Once you have the connection set up, you can use whatever sort of client you would normally use if the other computer were on your LAN (ssh, telnet, ftp, VNC, remote desktop, etc.).

---

### Post by jmooney on 2005-11-28
[QUOTE=cwaldbieser]The VPN tunnel just acts like a link over the Internet.  It makes two networks look like they are connected instead of being seperated by the whole Internet.  Once you have the connection set up, you can use whatever sort of client you would normally use if the other computer were on your LAN (ssh, telnet, ftp, VNC, remote desktop, etc.).[/QUOTE]

Yea, I've gotten that answer before, but nothing I try has worked.  Either I'm misunderstanding, or it's not working.

Can you give me a specific example?

---

### Post by cwaldbieser on 2005-11-28
[QUOTE=jmooney]Yea, I've gotten that answer before, but nothing I try has worked.  Either I'm misunderstanding, or it's not working.

Can you give me a specific example?[/QUOTE]
Well, since I am not sure what you are connecting to on the other end, I will just use how I remote into work as an example.

At home, I have my Ubuntu desktop.  At work, we have lots of computers connected to our LAN.  Among them are my Win2000 workstation, an Ubuntu workstation, and a UNIX mainframe.

When I am at work, I typically sit at the console of the Win2K machine.  I have Cygwin installed, so I can ssh to my Ubuntu machine or to the UNIX mainframe (both are on the LAN).  I can also pull up the console for the Ubuntu workstation.

If I need to work from home, I can connect to work via a Microsoft VPN using PPTP from my Ubuntu machine at home.  This establishes a connection to some server on our LAN.  It creates a "virtual interface" called ppp0 when I do an ifconfig.  I change my routing table so that any packets destined for my work's LAN travel through the ppp0 device.

Now if I want to connect to my remote Ubuntu box or the remote UNIX mainframe, I can just open a terminal and ssh to the IP address of either one (I don't bother to set up a name server).  If I want to connect to the Win2K workstation, I can use krdc to remote desktop in.

I am not sure if that makes things any more clear for you.  What exactly are you trying to connect to, and what problems are you experiencing?

---

### Post by jmooney on 2005-11-28
[QUOTE=cwaldbieser]Well, since I am not sure what you are connecting to on the other end, I will just use how I remote into work as an example.

At home, I have my Ubuntu desktop.  At work, we have lots of computers connected to our LAN.  Among them are my Win2000 workstation, an Ubuntu workstation, and a UNIX mainframe.

When I am at work, I typically sit at the console of the Win2K machine.  I have Cygwin installed, so I can ssh to my Ubuntu machine or to the UNIX mainframe (both are on the LAN).  I can also pull up the console for the Ubuntu workstation.

If I need to work from home, I can connect to work via a Microsoft VPN using PPTP from my Ubuntu machine at home.  This establishes a connection to some server on our LAN.  It creates a "virtual interface" called ppp0 when I do an ifconfig.  I change my routing table so that any packets destined for my work's LAN travel through the ppp0 device.

Now if I want to connect to my remote Ubuntu box or the remote UNIX mainframe, I can just open a terminal and ssh to the IP address of either one (I don't bother to set up a name server).  If I want to connect to the Win2K workstation, I can use krdc to remote desktop in.

I am not sure if that makes things any more clear for you.  What exactly are you trying to connect to, and what problems are you experiencing?[/QUOTE]

I'm connecting to a Windows network

What's an "ifconfig" and how do you "do" it?

What is "ssh"?  is that like Telnet?

"IP address" may be the only network term you've mentioned that I recongnize

I've read the debian-HOWTO at sourceforge, but all it says is "try to access the network" without explaining how or with what.


Let's try this way, I'm sitting at an Ubuntu 5.10 computer.  My firewall is off, I"ve run pptpconfig with the debug window on and I can ping the server at the other side of the VPN tunnel.  

I would like to be able to see my files at the other side of that VPN tunnel, how do I do it or where can I find documentation that explains step-by-step how it is done?

Thanks again.....I set this up in 5 minutes on my Windows XP laptop, I've been working almost 5 days on my Ubuntu box.  I really don't think it's supposed to be this difficult.

---

### Post by jmooney on 2005-11-28
More on what I've tried.

I've systematically tried every option under "PLACES-CONNECT TO SERVER..."

I've entered everything even remotely appropos to what I am trying to reach in Firefox.  Including raw IP addresses.

I've tried doing the same in Nautilus [GO-LOCATION...]

Currently trying gftp in FTP mode and waiting to see what it will do.

---

### Post by jmooney on 2005-11-28
[QUOTE=jmooney]More on what I've tried.

I've systematically tried every option under "PLACES-CONNECT TO SERVER..."

I've entered everything even remotely appropos to what I am trying to reach in Firefox.  Including raw IP addresses.

I've tried doing the same in Nautilus [GO-LOCATION...]

Currently trying gftp in FTP mode and waiting to see what it will do.[/QUOTE]

gftp hangs and I have to force kill it.

---

### Post by cwaldbieser on 2005-11-29
[QUOTE=jmooney]I'm connecting to a Windows network

What's an "ifconfig" and how do you "do" it?

What is "ssh"?  is that like Telnet?

"IP address" may be the only network term you've mentioned that I recongnize

I've read the debian-HOWTO at sourceforge, but all it says is "try to access the network" without explaining how or with what.


Let's try this way, I'm sitting at an Ubuntu 5.10 computer.  My firewall is off, I"ve run pptpconfig with the debug window on and I can ping the server at the other side of the VPN tunnel.  

I would like to be able to see my files at the other side of that VPN tunnel, how do I do it or where can I find documentation that explains step-by-step how it is done?

Thanks again.....I set this up in 5 minutes on my Windows XP laptop, I've been working almost 5 days on my Ubuntu box.  I really don't think it's supposed to be this difficult.[/QUOTE]

ifconfig is a command you enter in the terminal and it shows you information about your network cards.  In widows, a similar command is called ipconfig.  For example, on my home network:
```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:E9:56:1C:AD  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fe56:1cad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:99418 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88375 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:95722037 (91.2 MiB)  TX bytes:10676403 (10.1 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6743 (6.5 KiB)  TX bytes:6743 (6.5 KiB)

```
The eth0 is my network card, and the 192.168.0.2 is the address that has been assigned to it on my local network.

ssh is like telnet, except it uses encryption to make sure outside parties can't intercept your messages and get your passwords.  You'd use it very close to how you's use telnet.
```

$ ssh -l carl 192.168.0.3

```
connects to the ssh server on 192.168.0.3 as user carl.  It will prompt for a password.  Windows servers don't commonly have ssh servers installed because they cost extra to install and there are not too many things you can do easily from the command line on a Windows server.

You should be able to use FTP if the machine you are pinging is running an FTP server.  Open a terminal and type:
```

$ ftp server-address

```
You'll be prompted for a user name and a password.  If it is set up for anonymous access, you can log in as "anonymous" and give something like "carl@home" as the password.  The "dir" or "ls" command from the ftp prompt should let you browse your files.

It all really depends on the server you are connecting to.  What kind of server is it, and what is it running?  Also, does it have a firewall that blocks certain ports?

Also, you mentioned you connected to it with WinXP.  What did you browse the files with from XP?  Did you use an FTP program there?  Did you just open up explorer and enter in a shared network drive like "\\192.168.0.3\shared\"?  Basically, whatever program you used with XP, you should be able to use the equivalent client from Ubuntu.

BTW, Windows network shares are also known as SMB shares after the protocol they use.  You can browse to them in Nautilus with the "smb://" URL, or you can use "smbclient" from the terminal.

---

### Post by jmooney on 2005-11-29
Thanks cwaldbeiser,

The SMB:// option turned out to be it.  Plus, it clarified that I needed to select 
[Places - Connect to Server... - Windows Shares] to do the Linux equivalent of "Mapping the Network Drive"

Right now, I'm set up as "all to tunnel", but, now that I've got it to work, I'll try to configure "client to LAN" again.

Thanks again,

Joe

---

