---
title: "Samba machine not showing in Windows 10 Network folder"
date: 2016-01-13
forum: Networking &amp; Wireless
---

### Post by Roadsguy on 2016-01-13
[FONT=Segoe UI]Not sure if here or Ten Forums is the correct place to post this, so I'm posting to both.[/FONT]

[FONT=Segoe UI]I have a file server running Ubuntu Server 14.04, with Samba set up for Windows file shares. I have it all set up to do mostly what I want, but there's one odd problem that I can't seem to fix: even though I can manually go to //192.168.1.3 (the IP) or //fileserver and browse my shares and files normally, I can't get the file server to show up in Windows' Network folder.[/FONT]

[FONT=Segoe UI]No amount of refreshing the folder, restarting Samba, or rebooting either my computer or the file server seems to fix this. All that shows up is the machine I'm using, as well as whatever other Windows PCs are running (which means that network discovery is definitely set properly). Also, I can map network drives to the specific shares without an issue.[/FONT]

[FONT=Segoe UI]I've confirmed that both machines are on the same workgroup (smb.conf has workgroup = WORKGROUP, and my Windows 10 machine is on WORKGROUP as well (and is stuck on that, too, since it's running 10 Home). Googling the issue showed other people with similar problems, and offered various config options in smb.conf as a solution, but none of them work. (I did of course restart Samba after each attempt.)[/FONT]

[FONT=Segoe UI]This is my smb.conf, edited for privacy and to remove commented lines (it's mostly default):[/FONT]

```
global*

[FONT=Segoe UI]workgroup = WORKGROUP[/FONT]

[FONT=Segoe UI]server string = <server string>[/FONT]

[FONT=Segoe UI]dns proxy = no[/FONT]

[FONT=Segoe UI]log file = /var/log/samba/log.%m[/FONT]

[FONT=Segoe UI]max log size = 1000[/FONT]

[FONT=Segoe UI]syslog = 0[/FONT]

[FONT=Segoe UI]panic action = /usr/share/samba/panic-action %d[/FONT]

[FONT=Segoe UI]server role = standalone server[/FONT]

[FONT=Segoe UI]passdb backend = tdbsam[/FONT]

[FONT=Segoe UI]obey pam restrictions = yes[/FONT]

[FONT=Segoe UI]unix password sync = yes[/FONT]

[FONT=Segoe UI]pam password change = yes[/FONT]

[FONT=Segoe UI]map to guest = bad user[/FONT]

[FONT=Segoe UI][Share A][/FONT]
[FONT=Segoe UI]path = /home/fileserver/blah/blah[/FONT]
[FONT=Segoe UI]read only = no[/FONT]
[FONT=Segoe UI]writeable = yes[/FONT]
[FONT=Segoe UI]browseable = yes[/FONT]
[FONT=Segoe UI]create mask = 0770[/FONT]
[FONT=Segoe UI]force create mode = 0770[/FONT]
[FONT=Segoe UI]locking = yes[/FONT]

[FONT=Segoe UI][Share B][/FONT]
[FONT=Segoe UI]path = /home/fileserver/blah/blah[/FONT]
[FONT=Segoe UI]read only = no[/FONT]
[FONT=Segoe UI]writeable = yes[/FONT]
[FONT=Segoe UI]browseable = yes[/FONT]
[FONT=Segoe UI]create mask = 0770[/FONT]
[FONT=Segoe UI]force create mode = 0770[/FONT]
[FONT=Segoe UI]locking = yes[/FONT]

*Nothing but more shares with identical settings below here.*

```

[FONT=Segoe UI]Did I set something [SIZE=2]wrong [/SIZE]or what?

[SIZE=1]*Pretend this is in brackets. For some reason the formatting keeps wanting to autocorrect to having [global] in its own code block when it's in brackets. Interestingly it didn't do this on Ten Forums despite appearing to be the same forum software.
[SIZE=2]
**EDIT:** I just noticed that it all shows up like it should on my Surface RT's network folder, so the problem seems to be just on Windows' end on my main machine.
[/SIZE]
[/SIZE][/FONT]

---

### Post by TheFu on 2016-01-14
It is a Win10 issues, not Linux/Samba.
[https://social.technet.microsoft.com/Forums/en-US/26e5fd75-f3ab-4ffe-ace4-ed4ba96f82e5/not-discovering-ubuntu-server-on-network?forum=win10itpronetworking](https://social.technet.microsoft.com/Forums/en-US/26e5fd75-f3ab-4ffe-ace4-ed4ba96f82e5/not-discovering-ubuntu-server-on-network?forum=win10itpronetworking)

---

### Post by Morbius1 on 2016-01-15
It's a known 10 issue. From: [https://social.technet.microsoft.com/Forums/en-US/2131750e-d589-41f0-b6a3-1c7dac2361d9/cannot-connect-to-cifs-smb-samba-network-shares-shared-folders-in-windows-10-after-update](https://social.technet.microsoft.com/Forums/en-US/2131750e-d589-41f0-b6a3-1c7dac2361d9/cannot-connect-to-cifs-smb-samba-network-shares-shared-folders-in-windows-10-after-update)
> I wanted to provide an update on this thread to let you know that we  are currently investigating this issue and I am working with the product  group to determine root cause. The issue we are investigating is in  regards to 'Network Discovery' not locating  devices on the network.

 The issue appears that Windows 10 is not broadcasting out an NetBT or  RAP requests when searching for the devices on the network and only  uses WSD protocol. If you navigate to Explorer > Network and changed  to Details view and then add 'Discovery Method'  to the column bar you should see that if you are discovering any  devices they are more than likely only being found via WSD.

There's a lot of insane workarounds for this like setting smb in Windows 10 to a level it hasn't seen in a decade but for my money accessing the Linux machine by ip address is the most efficient followed by mDNS which Windows 10 can now do by default, Linux has done for a decade, and OSX has done longer than that.

---

### Post by Lloydb39 on 2016-01-20
I had the same problem. I solved it, sort of, by typing "\\linux.local" in the File Explorer address bar. That created a quick access icon and restored my ability to get files on the Linux machine across the wired network, which I had with Windows 7 before upgrading. Still doesn't show the connection under Network, however. Substitute the name of your machine for "linux," which is the name of mine. Still have not been able to access the Windows documents from the Linux machine, but that apparently is a Windows 10 bug.

---

### Post by a.c.m on 2016-12-14
> **Lloydb39 said:**
> I had the same problem. I solved it, sort of, by typing "\\linux.local" in the File Explorer address bar. That created a quick access icon and restored my ability to get files on the Linux machine across the wired network, which I had with Windows 7 before upgrading. Still doesn't show the connection under Network, however. Substitute the name of your machine for "linux," which is the name of mine. Still have not been able to access the Windows documents from the Linux machine, but that apparently is a Windows 10 bug.

I can confirm this worked. And I've spent like 3 hours debugging my linux htpc :/

---

### Post by TheFu on 2016-12-14
> **a.c.m said:**
> I can confirm this worked. And I've spent like 3 hours debugging my linux htpc :/

That will only work if avahi service is running.  Never used it. Generally purge it from my systems due to historical issues that it displayed eating 100% of CPU. That was many, many years ago, so perhaps it is fine.

Name resolution is a basic network skill.  Linux follows standards.  Avahi is an addon to make Unix-like systems announce their services more like netbeui did in 1988. It doesn't scale to internet levels, but does work great for a small home network.

Running **pgrep -a avahi** will show if that daemon is running or not on your Linux systems.  There is an ubuntu help page for it. The avahi-daemon.conf file has settings to control what the ".local" part is.  Perhaps you don't want to type that out?  ".LAN" might be nicer?  I dunno.  The issue is that every machine on the network has to have this service running, instead of having a simple text file (/etc/hosts) or 1 server (DNS) managing this stuff for all systems on the network.  Trade-offs.

However, I will keep the .local in mind when trying to help others in the future.  Writing this post will help me to remember it.

---

### Post by Morbius1 on 2016-12-14
> **a.c.m said:**
> I can confirm this worked. And I've spent like 3 hours debugging my linux htpc :/
This is more of a Gee Wiz thing but it might interest you to know that Windows 10 cannot only access another Linux or macOS machine with a .local but it will also do it in reverse as mDNS is now a standard component of Windows 10.

Only one teensy little problem: Incoming mDNS access is blocked by the firewall in WIndows. What I do is add a firewall rule for it:

Right Click the Start Button > Control Panel > System and Security   > Windows Firewall > Advanced Settings > Inbound Rules >  New Rule

Rule Type:         Port
Protocol:                UDP
Specific local ports:    5353
Action:        Allow the connection
[COLOR=#0000cd]**Profile:        Private**[/COLOR]
Name:        Allow mDNS for Samba on Private Network

Note: I added this rule for the "Private Network" not the "Public Network" so it's confined only to the LAN.

Now I can set up an entry in fstab to mount the Windows share with a //windows-host-name.local/share-name .....

BTW. The original problem / bug in WIndows 10 discovering the deprecated netbios names was fixed a while ago.

---

