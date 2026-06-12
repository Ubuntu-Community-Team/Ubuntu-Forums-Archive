---
title: "Windows Network (mshome icon) disappearing"
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by Quicky on 2006-08-11
I've connected in the past to a Windows PC in my home network and accessed files by clicking 'Windows Network' then 'mshome' (my home network/workgroup name) and opening the shared folders on the Windows computer.

However, occasionally there is no 'mshome' icon (or any other icon) visible after double clicking on 'Windows Network'. I'd like to stress that no settings on the windows PC or my Ubuntu laptop have changed, both PCs are wireless and can access the internet independently, but seemingly at random, my mshome workgroup will vanish the Windows Network folder of my Ubuntu laptop.

Is there any explanation as to why I would not be able to access computers on the workgroup? Any help would be appreciated!

Cheers

---

### Post by meng on 2006-08-11
Others will know better, but in nautilus I press ctrl-L and type
smb://(ipaddress) to access my shares. Alternatively, smb://(hostname), assuming /etc/hosts contains the hostname-ip correlations.

---

### Post by Quicky on 2006-08-11
Thanks, I'm aware that it should be possible to do that. but whenever I have tried that method while 'mshome' in not visible in Windows Network as described above, it has not worked. It does work when the 'mshome' icon is visbile however, (but not right now as this is one of those instances when I can't access the Windows PC).

FYI, my network is dhcp, so I would provide the hostname in that instance.

---

### Post by Quicky on 2007-01-12
Realised I should have posted an update to this some months ago – as it turns out the mshome icon only refused to appear shortly after boot up. It seems that Samba takes around two minutes or so (on my machine at least) after the desktop has loaded to 'discover' the mshome network. After that, there's no problem. Pure impatience.

---

### Post by s_raghu20 on 2007-08-21
Hi,

I am facing the same problem. When I installed the original Feisty Fawn on my laptop, it could immediately see the windows network, and thereafter the windows machine that I have in my network.  I could access shares and everything looked perfect.

I cant really claim that I have not changed settings on the system in general, but I can sure claim that I have not touched any file sharing settings.  Since I receive package updates quite frequently, it might have happened automatically without any intentions, thats one possibility.

So, when I tried to access my windows network today, it shows that there is a windows network. Fine, but then there it cant find anything.

Checking the system, I found that Samba has disappeared. I know that samba supports file sharing from a different side (to other servers from this server), but I was equally surprised, since I haven't made any conscious changes to samba installation/configuration.

What could be going on with my system/network ? any suggestions ...

PS : And, I am not using wireless. I am using the good old ethernet cables for connecting to the other system (through a router, which shares the internet connection).

regards
raghav..

---

