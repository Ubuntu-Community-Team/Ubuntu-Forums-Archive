---
title: "diappear computer in workgroup in samba workgroup environment"
date: 2006-09-08
forum: Networking &amp; Wireless
---

### Post by stock99 on 2006-09-08
HI,

Most of computers in my office running win2k and now 2 of them and a little mini print server (netgear ps101 ) all can't be found or see other in the workgroup. 
The ping still communicate perfectly with them and the 2 computer can access resouce via \\192.168.0.2\folders But the problem is print server also got the same issue and no one can access that printer coz on one can resolve its device name (ok to ping its ip address). 

I have try to add the few lines below to smb.conf:

local master = yes 
os level = 65
preferred master = yes
domain master = yes


but still no luck. Can anyone give me some tips of this problem? Btw, everything work fine for years and it just turn sour yesterday. I am not sure exactly what is the surce of the problem.


ps: they work fine for almost a year now suddenly got this issue. Not sure if its because i leave the xp machine on overnight...

---

### Post by tbonius on 2006-09-08
Yeah.. turn off the "Master" browser options in your samba conf.  Samba and Windows will argue over who has the right to maintain the master list of browsable hosts for NetBIOS on a network.  Its a losing battle sometimes with Windows.. even when setting OS levels.

Try something like:

```
preferred master = No
local master = No
domain master = No

```

Remove the OS level line.

Let me know if this does not work for you

T

---

### Post by stock99 on 2006-09-10
well it was off before. But all of sudden 2 computers and all print server device (ps101 and another linksys print-server) disappear from workgroup. The only thing i can install lately is blockhosts which is a python scripts that automatically put ssh attacker into /etc/hosts.allow as 'deny access'. There is no problem for them to communicate in ip , just not by name. 


Other then that, i can't think of any reason. I chage the smb.conf to the setting as YES coz i thought promote samba to master browser , it can resolve the issue. 

What i don't understand is, i thought linksys is using linux base os (even embeded one, i would presume so). That should mean printer server device should immune from problem like win2k does right?

ps: we have a couple of winxp but most win2k. The 2 computer in problem are win2k.

---

### Post by tbonius on 2006-09-11
I think you might have answered your own question.  make sure you are not runnign a firewall or any sort of port blocking service?  Is this an internal private LAN?  Why would you need a port blocker in an internal network.

Some people are paranoid and use multiple layers of firewalls and port/protocol filtering.. which is fine.. just make sure you know what yorue doing when you do something like that.

You said you have a Linksys print server device.. sometimes these devices are noisy and can boradcast UPnP messages all over the network.  Disable your port blocking program and try again.

T

---

### Post by stock99 on 2006-09-18
the port blocking program is only for external not internal. So it doesn't block anything internal. In addition, it only block sshd nothing more.


The problem is solved by reseting one of the old 8 port switch which doesnt have "Auto Uplink" technology (not sure if its relavent at all, as i dono in great details on how switch work). After reset the switch, browstat.exe show that they have no problem recognizing my samba server as master browser. I came across an discussion thread about switch conflicting with netbios comunication but i didn't click in to read coz i thought its linux's problem.


Again, thx for the comment on help. ^^

---

### Post by ricesteam on 2006-09-18
Hi,

I have a similar problem.  

A moment ago I can see and read files on a shared Windows folder.  I closed Nautilus and relaunched Places->Network Servers.  

Now I can't see or access any Window computers.  

Is this a bug?

---

