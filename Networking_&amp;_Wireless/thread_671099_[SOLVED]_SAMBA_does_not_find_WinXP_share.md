---
title: "[SOLVED] SAMBA does not find WinXP share"
date: 2008-01-18
forum: Networking &amp; Wireless
---

### Post by yc2 on 2008-01-18
I connect my Ubuntu laptop to my XP laptop through a home network. It has worked well through Edgy and Feisty. I recently upgraded to Gutsy, I think this may have induced a networking problem?

(The Ubuntu computer has a static IP of 192.168.1.101, the XP computer is assigned IP by the router, it always gets 192.168.1.200)

When I click (in Gnome) Network / Windows network / <XP work group name> the system replies (my translation from Swedish):
```
The contents of the the folder could not be shown, unfortunately all the contents of Windows-network:<group name> could not be shown.
```

So Ubuntu has found the XP computer’s work-group-name but cannot find the XP computer’s name and cannot open the shared folders on the computer running XP.

I have tried entering the XP computer’s IP number and name in /etc/hosts. This seems to carry the process one step further. I can click Network / Windows network / <XP work group name> and then I see the XP computer’s name. But when I click that icon, I get the same error message.

Another factor that seems to matter is which computer is started first. If the XP computer is started first, Ubuntu (clicking Gnome: network …) does not seem to recognise even the Windows-group-name. However, putting
```
smb://<XP-computer's-name>
```
into the address window of Nautilus makes Nautilus reach and manipulate the share on the XP computer.

The situation is a little confusing and also requires restart of the computers so I may not have described the problem in full detail. However, previously the Ubuntu/XP network worked perfectly without problems and I hope I can get it back to that situation.

One work-around is to mount the share on the desktop:
```
mount -t smbfs //<XP-computer’s IP-number>/<name of share> /media/test_dir -o uid=1000
```

It is also possible to reach the Ubuntu system from the XP system.

However in the long run I am sure it is better to get this network running as intended. My impression is that somehow the Ubuntu system has not become fully aware that the XP computer is willing to share files

Thanks :KS

---

### Post by kbracer on 2008-01-19
I had been experiencing the same symptoms describe in a number of threads about issues accessing Windows shares. I solved of my problems accessing Windows shares by...

[LIST]
[*]Go to System>Administration>Network
[*]Select the General Tab of the Network Settings window.
[*]Set Domain Name to be the same as your home network workgroup name.
[/LIST]

I can now browse all of my machines and their shared folders through Places>Network

---

### Post by yc2 on 2008-01-20
kbracer, thanks for your advice.

After trying what I described above I felt I had temporarily run out of ammunition and decided to take a short rest from working on the problem.

When I read your advice today I first tried the small network without changing anything. I don't think any significant systemupdates, relating to the problem, have been made either.

However, when I now try the system it seems to work. Regardless of which computer is started first, SAMBA works. It is possible to reach the shares of both computers over the network, f. ex. through Places > Network.

The only small abberration is the following. The Ubuntu computer is dual boot with Win XP. The Ubuntu system now even shows the XP ntfs partition *on the same computer* as a share. Clicking that icon will give the same error message that I originally got. However, I am not sure it is a requirement that SAMBA should work this way. ntfs -3g works well when f.ex. accessed clicking the desktop icon where the XP partition is mounted.

Thanks kbracer, your advice will be the first thing I try the next time SAMBA starts acting up. :KS

---

