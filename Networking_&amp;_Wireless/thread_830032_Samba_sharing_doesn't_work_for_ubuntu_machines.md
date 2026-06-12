---
title: "Samba sharing doesn't work for ubuntu machines"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by f37u5g0d on 2008-06-15
I have sort of a funky problem.  I have three computers all on a wireless network and all on the same workgroup.  Two of them are ubuntu 8.04 desktops (with wireless cards) and the third is a windows xp notebook.  All three of them have files set up to be shared on the network.  The odd thing is the windows notebook can see both of the desktops and access the files I have set to shared on either of them.  (side note I also had to set the permissions for non-users in order for the xp machine to access the files).  However the problem is that the ubuntu machines can see each other and the notebook but can't access any of the shares on any computer but themselves.  What am I missing?

I go to places > network > either of the machines.  It just loads for a very long time and then shows that computer has no files to share (empty nautilus window).

---

### Post by superprash2003 on 2008-06-15
in nautilus type smb://x.x.x.x where x.x.x.x is the ip of the ubuntu machine which contains the share

---

### Post by f37u5g0d on 2008-06-15
As a response to superprash2003.  When I put nautilus smb://*ip address of other ubuntu comp*  I get exactly what I wanted.  A nautilus window with the shared folders I set up.  It then correctly mounts those shared files and places icons both on the desktop and in the places menu.  However opening places > network > windows network > home workgroup > the name of the computer I want to access not work?

---

### Post by rplantz on 2008-06-15
I have the same problem. In addition, I have a Mac that will connect with either Ubuntu (8.04) machine.

The Mac requires that I supply my password. Then I can see my entire home directory on either Ubuntu.

Vista allows me to access my Ubuntu home directory without even requiring a password!

I am slowly getting there with Ubuntu-Ubuntu networking. But I have to explicitly allow sharing for each directory in my home directory. I would like to be able to get to my entire home directory, just as I can from my Mac.

This is a private network at my house. I'm not trying to set up a server. Very weird.

---

### Post by AlucardXXVII on 2008-06-15
> **superprash2003 said:**
> in nautilus type smb://x.x.x.x where x.x.x.x is the ip of the ubuntu machine which contains the share

I'm having the same problem, and I have another thread.  One thing, though.  I'm running a virtual windows xp machine.  The IP XP says it's using is not a typical router IP.  Is there a way to force VirtualBox to get an IP assigned by the router?  Maybe that's my problem

---

### Post by f37u5g0d on 2008-06-16
rplantz.  Why don't you just set /home/*your username* as a shared directory?  Sharing a parent directory automatically makes the child directories shared.  You still have to however alter the file permissions for other ubuntu users and windows users to access the files.

---

### Post by GenesisV2.0 on 2008-06-16
Stupid question but i take it you have set up samba lol

i set up samba server on ubuntu server edition and found the only hard part was creating groups.

have fun

---

### Post by standingfire on 2008-06-16
Have you tried sharing these file systems another way, for instance sshfs or nfs.
The other thing I would look at is matching everything up, double check permissions and the smbusers/smbpasswd files to ensure continuity. restarting the samba services on all machines. 
And I would look into the firewalls, if those are installed.[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)
:)

---

### Post by davec51 on 2008-06-17
I'm new to Ubuntu, though not new to Linux. I just booted the Xubuntu cd -- very nice. But there is no "network" choice in my Places menu. I seem to have a live wired connection, and I've set up the remote printer successfully. How do I get access to the files on the local hard drive and on the remote )Windows XP) machine. I hope I'm on the right forum for this question.

---

### Post by kevinatkins on 2008-06-17
Hi,

I'm experiencing similar behaviour, albeit problems browsing to Active Directory shares on a Windows 2003 server. I have a feeling your problem could be similar - a result of a problem with the new GVFS, whereby you're unable to browse password-protected shares - they just don't appear.... whereas what should happen is the shares should appear, then request a password when trying to access. That's how it used to work, up until 8.04... 

I might be completely wrong here, but anyway, a similar problem has been reported to the developers, who are working on a fix, I believe.

---

### Post by f37u5g0d on 2008-06-17
I don't have any of my files password protected.

---

### Post by SolitudeX on 2008-06-19
I'm also having this problem. Not sure if it's isolated to the wireless network or not, however in my situation when I plug in an ethernet cable into the Machines, they all happily find and browse the workgroup computers from Places > Network. Maybe if you have a switch floating around trying plugging them all into cables and see if it starts working for you - however i've found you need to restart X (alt+ctrl+backspace) or reboot the machine for this to work. Let me know how you get on :-)

Also, after researching this problem for a few days, some people are blaming nautalis for this, so maybe some kubuntu users can chime in and see if they are experiencing any samba issues. Alternatively maybe we could try using a smb browser such as tksmb or pyneighborhood and see if samba shares are located. If so, then perhaps it's nautalis and the new gvfs in 8.04. Others are also claiming the a recent samba security update is causing this problem!

---

### Post by f37u5g0d on 2008-06-19
Well I can't do any tests to truely confirm nautilus as the culprit but I suspect that samba is doing everything it should becuase if I type "nautilus smb://*ip of computer*" in the command prompt I can then browse the network within nautilus with no problems.  I am on a wireless connection using ndiswrapper.  Maybe that has something to do with it?  Anybody else out there having this problem?

---

### Post by Megatog615 on 2008-06-26
Same problem. The IP address method is a good workaround; it seems something is wrong with the way gvfs is resolving host names. If I double click on a network computer in network:///, it will hang with "Opening <location>...", and eventually fail with:
```
Couldn't display "<location>".
There is no application installed for this file type
```

---

### Post by rplantz on 2008-06-26
I have mostly solved my problem.

I have:
1. Ubuntu 8.04 desktop
2. Windows Vista / Ubuntu 8.04 (dual bootable) laptop
3. Mac OS X 10.4

My router talks to the outside world through DSL and dynamically assigns IP addresses to each of my machines. I am not serving anything to the outside. I only want my machines on my local LAN to be able to connect to each other. I do not want to dedicate one to be a server. My desktop Ubuntu and Mac are connected to the router by wire, the laptop wireless.

They all talk to each other, except I have not yet gotten Vista to connect to the Mac.

The problem I was having with Ubuntu is that the technique for connecting is not (in my view) very obvious. I have found two ways:

1. Places -> Connect to Server...  Then select Windows share for service type. Then fill in the name of the machine you want to connect to for Server; for example, bob-desktop. And fill in user name for Share; for example, bob. (Even though it says this is optional, I need to do it.)

2. From a Nautilus window, Go -> Location...  Then enter smb://machine_name/user_name in the Location: box. For example,
```

smb://bob-desktop/bob/

```

Perhaps this is obvious to most, but it was new to me.

---

### Post by muzzamo on 2008-07-17
I am having this problem too. entering the IP adress seems to fix it. 

Strangely it has only just started to occur recently. I havent changed anything with my setup. Maybe it was a recent update that did it.

---

### Post by NickZA on 2008-08-09
Hi all

I'm experiencing the same problem, my server machine can serve OS X and WinXP on my workstation perfectly, however my Hardy installation on there does the "There is no application installed for this file type" thing.

Damn annoying!!!

:mad:

---

### Post by rafe101 on 2008-09-20
Sometimes everything works for me, sometimes it doesn't.  When it doesn't I get one of three problems.  None of my shares are password-protected, but sometimes it keeps asking for a password, which I don't have to give to it.  Second, it might give me the "no application is installed for this file type" line.  And third, sometimes, when I type in the address of the share I want, it might say "access denied."

But, sometimes everything works also.

---

### Post by yogm2k on 2009-04-02
Hi.. Friends..

even I have same issue at my office..

I am copying the files from network to my desk; making changes and placing at original place...

Need permanent solution for this...!!!

---

### Post by nickmcg on 2009-04-02
Does the addition of winbind & samba help? - see [http://ubuntuforums.org/showthread.php?t=1111565](http://ubuntuforums.org/showthread.php?t=1111565)

Nick

---

