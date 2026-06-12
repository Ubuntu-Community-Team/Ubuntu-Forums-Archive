---
title: "help!  evdo download speed super slow!! :("
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by KillaKurt on 2008-05-01
Hello everyone, this is my first post on the forums.  I'm using Gutsy.

I'm the biggest kind of n00b there is to linux so talk to me like I'm mentally handicapped please!!!

I'm having speed issues with my Verizon USB720 modem.  I was able to get it connected and everything but I'm downloading some package files right now and my speed is only running between 679B/s - 2000B/s.  That's right...B/s not kB/s.

What can I do?!

EDIT: Downloads in Windows are ~150KB/s in utorrent.  Downloads in Gutsy before were reaching ~180KB/s (had to format partition and reinstall...messed up a video driver pretty bad lol)

---

### Post by tamoneya on 2008-05-01
what is the result of typing```
ifconfig
``` in terminal. You can copy and paste it out of terminal by using ctrl-shift-c unlike the normal ctrl-c.

---

### Post by KillaKurt on 2008-05-01
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:922 errors:0 dropped:0 overruns:0 frame:0
          TX packets:922 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:50820 (49.6 KB)  TX bytes:50820 (49.6 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:75.204.115.38  P-t-P:66.174.52.4  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4517 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3714 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:4193402 (3.9 MB)  TX bytes:369924 (361.2 KB)

---

### Post by tamoneya on 2008-05-01
so your evdo is ppp0.  I was expecting to see some dropped packets or something but that doesnt seem to be the case.  I find this rather odd as well.  try testing it with a torrent instead of with a package.  It may be something weird about how ubuntu package manager is picking the mirrors since you have evdo.

---

### Post by KillaKurt on 2008-05-01
if it helps at all it seems to get bursts of higher speeds once in a while (the light on the modem blinks faster and the download rate goes up to about 40kB/s)

i don't have bittorrent installed right now...about to try that out (haven't tried it yet)

---

### Post by tamoneya on 2008-05-01
a bittorrent client is installed by default on hardy.  It is called transmission.

---

### Post by KillaKurt on 2008-05-01
i'm not running hardy i'm running Gutsy.  but there is a bittorrent client installed already...i just don't know how to use it i guess?  i don't see it in my list of applications but when i go to add/remove it IS listed and checked as installed...

do i have to run this from terminal somehow?  *tries it* lol

---

### Post by KillaKurt on 2008-05-01
ok figured that out (ran gnome-btdownload at terminal, gives me gui for bittorrent).  copied a torrent file over from my windows rig to a thumbdrive and opened that torrent with this gnome-btdownload dealy i got goin on.  speeds on this are steady...50KB/s right now.  So this is a problem with package manager?  Cause on my last Gutsy install package manager was downloading at about 180KB/s...

---

### Post by KillaKurt on 2008-05-01
ok now that those files i was downloading at the time are done i went to enable my restricted nvidia drivers and now it's downloading some new package files and it's going much faster.  maybe there was something wrong with my connection to the server that the other package files were being downloaded from, or the mirror(s) like you said (5 different files were downloading).  But I'll deal with this for and I'll come back to the forums here if I run into the problem again.  Thank you for your help!!!

---

