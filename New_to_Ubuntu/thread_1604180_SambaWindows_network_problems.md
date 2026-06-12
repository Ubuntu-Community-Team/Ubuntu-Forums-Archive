---
title: "Samba/Windows network problems"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by baldy4eva on 2010-10-23
I've just done a fresh install of Maverick on my HP G60-214 laptop, and I'm trying to sort out connecting to my home network (wired & wireless, mixed XP and 7 boxes and a couple of NAS), Router wise, I have a WRT54GS for wireless bridge (non DHCP) connected to a DG834 which acts as my router and internet connection.

I have tried following stormbringer's How To for setting up samba (a little old, I realise) to no avail. I've also been trawling through these forums for the past 3 days for a clue of how to set it up.

I CAN connect to each of my NAS using the Connect To Server tool, and I can use the Terminal Server Client (Remote Desktop) to view the XP and 7 boxes.

I'd be grateful if someone could either post some help, or point me to a thread to get me through this. Thanks :D

---

### Post by sandyd on 2010-10-23
> **baldy4eva said:**
> I've just done a fresh install of Maverick on my HP G60-214 laptop, and I'm trying to sort out connecting to my home network (wired & wireless, mixed XP and 7 boxes and a couple of NAS), Router wise, I have a WRT54GS for wireless bridge (non DHCP) connected to a DG834 which acts as my router and internet connection.

I have tried following stormbringer's How To for setting up samba (a little old, I realise) to no avail. I've also been trawling through these forums for the past 3 days for a clue of how to set it up.

I CAN connect to each of my NAS using the Connect To Server tool, and I can use the Terminal Server Client (Remote Desktop) to view the XP and 7 boxes.

I'd be grateful if someone could either post some help, or point me to a thread to get me through this. Thanks :D

so what are you truying to accomplish?

to share files with other computers?
if yes,
```

sudo apt-get install samba
sudo apt-get install system-config-samba
gksudo gedit /etc/samba/smb.conf
```

Replace the line that has
```

security= user
```in it (including the semicolon, if there is one)
to
```

security= share
```
save the file
```

gksudo system-config-samba
```
In the prefrences thingy, set the workgroup to your workgroup.

You can then press the "+" sign to add shares.

---

### Post by baldy4eva on 2010-10-23
Thanks for your response Sandyd. What I'm trying to achieve is to be able to see my windows shares from my Ubuntu box. I've tried your suggestions, and they don't seem to have worked. I still can't seem to see the machines on the network. 

I've tried pinging from either end and, although i can see my Ubuntu box from windows, i can't get a response from windows machines or NAS when pinging from Ubuntu.

---

### Post by luvshines on 2010-10-24
> **baldy4eva said:**
> Thanks for your response Sandyd. What I'm trying to achieve is to be able to see my windows shares from my Ubuntu box. I've tried your suggestions, and they don't seem to have worked. I still can't seem to see the machines on the network. 

I've tried pinging from either end and, although i can see my Ubuntu box from windows, i can't get a response from windows machines or NAS when pinging from Ubuntu.

For accessing windows share from Ubuntu, you don't need to setup Samba server on Ubuntu side.
What you need is only samba client.
You say that you are not able to ping Windows machine, what error do you get when you ping it. I hope you have tried both the hostname and the ip of Windows machine

---

### Post by arju305 on 2010-10-24
> **luvshines said:**
> For accessing windows share from Ubuntu, you don't need to setup Samba server on Ubuntu side.
What you need is only samba client.
You say that you are not able to ping Windows machine, what error do you get when you ping it. I hope you have tried both the hostname and the ip of Windows machine

Guys I am having a problem with samba.
firstly i installed it :
$sudo apt-get install samba
$sudo apt-get install system-config-samba
then i restarted the server.
from administrator-> samba i customized it for access to every one.
I found that.
from my ubuntu, I could access windows 7
but from windows 7 I cannot access ubuntu.
need your help.
Thanking you in advance.

---

### Post by baldy4eva on 2010-10-24
luvshines,

I've had to switch from wlan0 to eth0 to get some results (another problem!) . So, using the Network Tools gui thing, i get no results from using the ping command with either IP address or hostname. From Terminal, when I run a ping command to the IP address, I get the following

64 bytes from 192.168.0.2: icmp_req=1 ttl=128 time=0.478 ms
64 bytes from 192.168.0.2: icmp_req=2 ttl=128 time=1.49 ms
64 bytes from 192.168.0.2: icmp_req=3 ttl=128 time=0.736 ms... etc

but when I run ping hostname, it's showing an external IP address as below

PING midge (some other number) 56(84) bytes of data... etc 

Using the Connect To Server tool, an error message pops up with 

Cannot display location "smb://beast;cliff@192.168.0.4/public/public" No such file or directory

But looking at the desktop, I can see the folder is mounted, and browseable. 

This is on a vanilla install of Maverick, no samba installed yet, as I'm just after the ability to browse the windows shares on my network. Thanks in advance

---

### Post by luvshines on 2010-10-24
> **baldy4eva said:**
> luvshines,

I've had to switch from wlan0 to eth0 to get some results (another problem!) . So, using the Network Tools gui thing, i get no results from using the ping command with either IP address or hostname. From Terminal, when I run a ping command to the IP address, I get the following

64 bytes from 192.168.0.2: icmp_req=1 ttl=128 time=0.478 ms
64 bytes from 192.168.0.2: icmp_req=2 ttl=128 time=1.49 ms
64 bytes from 192.168.0.2: icmp_req=3 ttl=128 time=0.736 ms... etc

but when I run ping hostname, it's showing an external IP address as below

Using the Connect To Server tool, an error message pops up with 

Cannot display location "smb://beast;cliff@192.168.0.4/public/public" No such file or directory

But looking at the desktop, I can see the folder is mounted, and browseable. 

This is on a vanilla install of Maverick, no samba installed yet, as I'm just after the ability to browse the windows shares on my network. Thanks in advance

Try connecting from nautilus itself. Open nautilus, press ctrl+l then type the following:
```
smb://192.168.0.4
```

When it prompts for username/password, enter that and see if you can access your windows share

PS: **I would suggest you to edit your earlier post and remove the public IP which have posted, for your security** :)

---

### Post by luvshines on 2010-10-24
> **arju305 said:**
> Guys I am having a problem with samba.
firstly i installed it :
$sudo apt-get install samba
$sudo apt-get install system-config-samba
then i restarted the server.
from administrator-> samba i customized it for access to every one.
I found that.
from my ubuntu, I could access windows 7
but from windows 7 I cannot access ubuntu.
need your help.
Thanking you in advance.

Hi arju

I would suggest you to start another thread with your problem description, instead of hijacking this thread :)

When you start another thread, please post the output of ```
testparm -sp
```
Also if you shared some folders with right_click->sharing options, post output of ```
net usershare info
```

---

### Post by arju305 on 2010-10-24
sorry...... but it was my first attempt .... and i didnt know how to do it...........

---

### Post by arju305 on 2010-10-24
I

---

### Post by luvshines on 2010-10-24
> **arju305 said:**
> I am again sorry...... please dont laugh.....
Its embarassing
how do we start a new thread......... I m searching and searching..... but not getting the way to start a new thread....

See the screenshot ;)

PS: I am not laughing, but similing :)

---

### Post by CharlesA on 2010-10-24
> **arju305 said:**
> I am again sorry...... please dont laugh.....
Its embarassing
how do we start a new thread......... I m searching and searching..... but not getting the way to start a new thread....

Click [here]("http://ubuntuforums.org/newthread.php?do=newthread&f=326").

---

### Post by baldy4eva on 2010-10-24
> **luvshines said:**
> Try connecting from nautilus itself. Open nautilus, press ctrl+l then type the following:
```
smb://192.168.0.4
```When it prompts for username/password, enter that and see if you can access your windows share

PS: **I would suggest you to edit your earlier post and remove the public IP which have posted, for your security** :)

Thanks luvshines, edited previous post as suggested... oops!

Right, I've tried connecting through Nautilus, my xp box and  NAS opens straight away. My Win7 box doesn't and keeps asking for the password and workgroup. I've tried several times with the correct information, changing the case of the inputs doesn't seem to help. Any clues? 
I'd like to just be able to browse through the network from Nautilus by clicking on the Network icon. It'll open and show my home network, but fails to retrieve a list of servers.

---

### Post by CharlesA on 2010-10-24
What OS is the NAS running? You might have to change a setting on the Win7 box.

I had a similar problem when connecting to a NT4 box and had to change the "Network security: LAN Manager authentication level" to "Send LM & NTLM - user NTLMv2 session security if negotiated" in the local security policy: Local Policies > Security Options. See [here]("http://www.windowsreference.com/windows-7/unable-to-access-network-resources-on-non-windows-7-systems-from-windows-7-pc/"), for a bit of a better explanation.

I've got a file server set up using Samba and can connect fine as well as browse it thru "network" menu. I didn't have to mess with any security settings on any machine, but I did need to enable the local dns server on my router, so that the machines could resolved hostnames.

Are you able to connect using the hostnames or ip addresses with "connect to a server"?

---

### Post by Morbius1 on 2010-10-24
> Right, I've tried connecting through Nautilus, my xp box and  NAS opens  straight away. My Win7 box doesn't and keeps asking for the password and  workgroup.

There is also a Win7 / Windows Live Sign-in Assistant / Samba bug:

[http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527](http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527)

[https://bugzilla.samba.org/show_bug.cgi?id=7577](https://bugzilla.samba.org/show_bug.cgi?id=7577)

If you have Live Sign-in Assistant installed on Win7, you might consider uninstalling it.

---

### Post by luvshines on 2010-10-24
> **baldy4eva said:**
> Thanks luvshines, edited previous post as suggested... oops!

Right, I've tried connecting through Nautilus, my xp box and  NAS opens straight away. My Win7 box doesn't and keeps asking for the password and workgroup. I've tried several times with the correct information, changing the case of the inputs doesn't seem to help. Any clues? 
I'd like to just be able to browse through the network from Nautilus by clicking on the Network icon. It'll open and show my home network, but fails to retrieve a list of servers.

That luks like some progress, right ??
So the issues at present are:
1. Win7 shares
2. Network not listing the servers

For the first one, see what error terminal gives:
```
smbclient -L <win7-ip> -U<username>%<passwd>
```

---

### Post by baldy4eva on 2010-10-24
> **Morbius1 said:**
> There is also a Win7 / Windows Live Sign-in Assistant / Samba bug:

[http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527](http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527)

[https://bugzilla.samba.org/show_bug.cgi?id=7577](https://bugzilla.samba.org/show_bug.cgi?id=7577)

If you have Live Sign-in Assistant installed on Win7, you might consider uninstalling it.

That worked, I can now see the Win7 box and access files... Thank you :D

---

### Post by baldy4eva on 2010-10-24
> **luvshines said:**
> That luks like some progress, right ??
So the issues at present are:
1. Win7 shares
2. Network not listing the servers

For the first one, see what error terminal gives:
```
smbclient -L <win7-ip> -U<username>%<passwd>
```

The first one is now working. Problems with Win Live as per OP's suggestion.  But the terminal is showing the following anyway
 ```
Sharename       Type      Comment
    ---------       ----      -------
    ADMIN$          Disk      Remote Admin
    C$              Disk      Default share
    H$              Disk      Default share
    I$              Disk      Default share
    IPC$            IPC       Remote IPC
    Public2         Disk      
    USB1            Disk      
    Users           Disk      
session request to 192.168.0.2 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available

```

Still not listing the pc's on the network in nautilus :S

---

### Post by Morbius1 on 2010-10-24
I sure wish they would roll out the patch in Samba to fix this thing. Getting advice in a linux forum to uninstall something on Windows ( Win 7 - no less ) gives me the willies. :wink:

---

### Post by baldy4eva on 2010-10-24
> **Morbius1 said:**
> I sure wish they would roll out the patch in Samba to fix this thing. Getting advice in a linux forum to uninstall something on Windows ( Win 7 - no less ) gives me the willies. :wink:
Haha :D To be honest, win live isn't needed on that box... It's just a games machine/infotainment centre until i can get full dx11 support on Ubuntu..

---

### Post by CharlesA on 2010-10-24
> **Morbius1 said:**
> There is also a Win7 / Windows Live Sign-in Assistant / Samba bug:

[http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527](http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527)

[https://bugzilla.samba.org/show_bug.cgi?id=7577](https://bugzilla.samba.org/show_bug.cgi?id=7577)

If you have Live Sign-in Assistant installed on Win7, you might consider uninstalling it.

Wow. That's lame.

Thanks for the info on that, glad I don't use any Windows Live stuff.

@OP: Do you have any firewalls in place on the machines you are trying to access via the network menu?

I ran into the same issue when I mistakenly blocked UDP ports 137 and 138 (nmbd uses those)

---

### Post by baldy4eva on 2010-10-24
> **CharlesA said:**
> Wow. That's lame.

Thanks for the info on that, glad I don't use any Windows Live stuff.

@OP: Do you have any firewalls in place on the machines you are trying to access via the network menu?

I ran into the same issue when I mistakenly blocked UDP ports 137 and 138 (nmbd uses those)

Just the windows firewalls and MS Security essentials on the win boxes, and my router has a firewall (netgear dg834)

---

### Post by CharlesA on 2010-10-24
> **baldy4eva said:**
> Just the windows firewalls and MS Security essentials on the win boxes, and my router has a firewall (netgear dg834)

Hrm. On the Windows boxes, you have "file and printer sharing" enabled on the network connection properties and allowed thru the firewall?

I guess what you could do it scan the windows machines with nmap to see if those ports are open.

---

### Post by luvshines on 2010-10-24
> **Morbius1 said:**
> I sure wish they would roll out the patch in Samba to fix this thing. Getting advice in a linux forum to uninstall something on Windows ( Win 7 - no less ) gives me the willies. :wink:

The bugzilla link says, fixed, but in 3.4 I guess. Are they talking abt samba-common which is used by both samba server and client ?
Ubuntu 10.04 installs, 2.3..., are they running behind ?

---

### Post by baldy4eva on 2010-10-24
> **CharlesA said:**
> Hrm. On the Windows boxes, you have "file and printer sharing" enabled on the network connection properties and allowed thru the firewall?

I guess what you could do it scan the windows machines with nmap to see if those ports are open.

Yeah, file and printer sharing are enabled. I did notice that win7 is trying to use home group to manage network access, so thats been turned off. Now, it's just user accounts and passwords to access the win7 box.

nmap doesn't show the UDP ports 137 and 138 as being open, but I'm not sure if I ran nmap with the right switch to check UDP...  nmap  -PN <IP address>

---

### Post by CharlesA on 2010-10-24
Scanning UDP ports is tricky, they should be open as long as the firewall isn't blocking them.

Were TCP ports 139 and 445 open?

Note: I also have that "homegroup" thing enabled, but not configured on my Windows box and it works fine with my current setup.

---

### Post by baldy4eva on 2010-10-24
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds

Both those tcp ports are showing as open... There's a couple of others too, but i guess they're not needed for the sharing.

---

### Post by CharlesA on 2010-10-24
Yeah.. it should be working.

Try adding the machine name and ip address to the /etc/hosts file and see if you can connect.

```
gksu gedit /etc/hosts
```

I think it's a name resolution problem, but that'll rule it out if it isn't.

---

### Post by baldy4eva on 2010-10-24
Thanks CharlesA, it seems to be working. Just one little issue with one of my xp boxes, but it would seem I can browse the rest. I do seem to have 2 windows networks now though, one called **WORKGROUP** and another with my home network name. My Ubuntu box is occupying the WORKGROUP network, with the rest of the network in the other. Is there a way of getting my Ubu box to be part of my home network? Thank you again :D

---

### Post by CharlesA on 2010-10-24
So adding the name to the hosts file allowed it to connect?

Replace "WORKGROUP" in smb.conf with the name of your workgroup.

---

### Post by baldy4eva on 2010-10-24
Yup, adding the hostnames  and IP's worked brilliantly. As did the smb.conf edit you suggested.. One more time, Thank you

---

### Post by CharlesA on 2010-10-24
You are welcome.

Don't forget to mark it as solved from the thread tools menu. :)

---

### Post by baldy4eva on 2010-10-24
Done :D

---

### Post by xflbret on 2010-12-12
> **baldy4eva said:**
> Thanks luvshines, edited previous post as suggested... oops!

Right, I've tried connecting through Nautilus, my xp box and  NAS opens straight away. My Win7 box doesn't and keeps asking for the password and workgroup. I've tried several times with the correct information, changing the case of the inputs doesn't seem to help. Any clues? 
I'd like to just be able to browse through the network from Nautilus by clicking on the Network icon. It'll open and show my home network, but fails to retrieve a list of servers.

same problem with me...

---

### Post by tad1073 on 2010-12-15
I have read through this thread and tried the suggestions listed but to no avail

Results of nmap -PN
```

Host is up (0.017s latency).
Not shown: 992 filtered ports
PORT      STATE SERVICE
135/tcp   open  msrpc
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds

```

added the host to /etc/hosts file

removed MS Live Essentials 2011 etc.

---

### Post by tad1073 on 2010-12-17
bump

---

