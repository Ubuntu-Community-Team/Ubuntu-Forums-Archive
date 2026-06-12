---
title: "Ubuntu + Windows Network"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by Toksin on 2007-03-22
Hi all,

Recently just killed Vista Home Basic on my laptop and installed Ubuntu 6.10 on it.

Managed to get wireless and such working, everything works fine, and I see my wireless network and can access the internet with no problems.

However, I do have a lot of music stored on my desktop (XP) and we have a network in the house so we can swap music & files etc between me and my flatmates.

Now, I've installed Samba etc but I can't really find anything that teaches me how to use it.  I've searched and searched, and I'm very new to Linux and getting very frustrated.  What I want to do is access the other computers on the network.  I go into Network Servers, and see "Windows Network" but once I click on that nothing shows up.  I don't have the slightest clue where to begin and nothing I've tried has seemed to work.

Please help, I'm really enjoying Linux but am getting frustrated that I can't access my desktop PC from my laptop.

Thanks.

---

### Post by ffxr on 2007-03-22
this works for me:

[http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba+how+to](http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba+how+to)

you'll need to setup ubuntu as a wins server (this is just a matter of ticking a box somewhere in network settings.. i use xubuntu so m not 100% sure where this is in GNOME) & point your xp machine at it.. & make sure both  machines are in the same workgroup..

if you've tried anything & are still having problems, post as much detail as u can..

---

### Post by Toksin on 2007-03-22
Thanks ffxr, that link helped a lot.  Followed it to the letter.  Slight problem though - I can access my laptop from my XP box, but not the other way around!

---

### Post by scxtt on 2007-03-22
what do you get if you enter "smb:/" in a Location bar in Nautilus?  can you see the workgroup names of other XP machines?  if you know the IP of your XP box, try putting "smb:/<ip address>/ into Nautilus as well ...

---

### Post by ffxr on 2007-03-22
is the folder shared out in xp? do u have file & printer sharing installed on the xp box? have a look at the permissions of the shared folder (both share & folder permissions).. i dont know if you can add your 'linuxbox'\usename' to the permissions list, ; my windows knowledge is fading rapidly tbh, although u could probably just share it to everyone i guess..

---

### Post by Toksin on 2007-03-22
> **scxtt said:**
> what do you get if you enter "smb:/" in a Location bar in Nautilus?  can you see the workgroup names of other XP machines?  if you know the IP of your XP box, try putting "smb:/<ip address>/ into Nautilus as well ...

smb:/ shows my network.  Double clicked it and the only thing that shows up is my laptop.

ffxr: The folders are being shared, they get accessed fine by the other XP boxes on the network.

---

### Post by scxtt on 2007-03-22
did you try it w/ the specific IP address?

---

### Post by Toksin on 2007-03-22
I've tried to ping the XP box's IP address but I get no return.  Putting the IP address into the location bar also yields nothing :(

---

### Post by scxtt on 2007-03-22
firewall in XP?
you're sure they're on the same network?
did you do "smb:/<ip-address>/" or just ip-address (this would default to HTTP)?

no ping returned is a bad sign ...

i'm unable to "browse" samba from KubuntuL
smb:/ yields nothing for me
smb:/192.168.1.103 gives me the samba shares for server 2003 VM

---

### Post by Toksin on 2007-03-22
All I get is "Couldn't display 192.168.1.6  The location is not a folder"

Quite sure they're on the same network.  XP's firewall is set to enable file and printer sharing.

Should I just disable Windows Firewall altogether and see if that works?

---

### Post by scxtt on 2007-03-22
> Should I just disable Windows Firewall altogether and see if that works?always my 1st try :)

enabling it just allows you to do it, it's independent of the firewall blocking those ports (137 ~ 139, i think) ...

---

### Post by Toksin on 2007-03-22
Holy crap it works!

Didn't even disable firewall.  All I did was go places > connect to server.  Entered the IP address of the XP box and whammo.  Works.

Thanks for the help guys :D

---

