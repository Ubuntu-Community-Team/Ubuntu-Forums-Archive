---
title: "AR9285 can't connect to my home network on 14.04"
date: 2016-09-29
forum: Networking &amp; Wireless
---

### Post by georges4 on 2016-09-29
Hello everyone,

I'm running a dual boot of Lubuntu 14.04 and Windows XP 32 bit on a netbook (Packard Bell dot-se 3, Intel Atom N570).

For a while now I have been unable to connect to my home network (b/g/n with WPA-CCMP security) (see 'Neko' in my wireless_info.txt). It also happened on my father's network (which I believe is also b/g/n and WPA-CCMP) and I cannot find the common denominator, so I fear the problem could happen on other networks. Since I am planning to sell/give away this laptop, I would very much like to have it work on any network, especially since it is quite fit for nomads like myself.

Here is the problem in more details, followed by more detailed info about my setup :

- I can connect to other networks which also use WPA with CCMP (and I think  they are also b/g/n). (see "Freebox-6270D8" and "HP-Print-BA-Photosmart  6520" in my wireless_info.txt)
- Other machines (running Android, iOS, Ubuntu, OSX or Windows 7) have no trouble  at all with this network, as well as this very laptop while running on  the Windows XP partition.
- Problem started happening about a year ago, a while after I switched from Ubuntu to Lubuntu, most likely (but not sure) changing from Maverick or Precise to Trusty. Before that I never had any problem on any network whatsoever (including the two currently problematic ones).
- I tried running different ubuntu versions, including 10.10, 15.10 and 16.04 and the problem is the same. I also tried on Puppy Linux (Lucid 5.2.8) and it didn't work either.
- I can connect to the same network if I change the security to WEP. On the other hand, changing between CCMP and TKIP or mixed doesn't seem to change anything.

LInk to wirelesss_info script results : [http://paste.ubuntu.com/23252398/](http://paste.ubuntu.com/23252398/)

Another thing that puzzles me is that my adapter is supposed to support b/g/n and so is my home network as well as the other networks I can connect to, yet iwlist scan only shows bitrates of the following values for all those networks : 1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s; 18 Mb/s; 36 Mb/s; 54 Mb/s :6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s. Aren't those supposed to be bitrates of b/g networks ?

I have tried various fixes found here and there (seems like a lot of people have trouble with this adapter, though none seemed to match with my problem), including addind nohwcrypt=1 option to ath9k, blacklisting acer_wmi, installing versions of backports which I read worked well (though they are older than my current kernel, so I don't know if that makes any sense) and using ndsiwrapper with the inf file I found on my windows xp partition, as well as with another set of files I found on driverguide.com

None of it worked.

I'm really clueless, and would very much appreciate your help on this one !



PS: if you happen to find this thread ([https://ubuntuforums.org/showthread.php?t=2317053](https://ubuntuforums.org/showthread.php?t=2317053)) which seemed to match my issue ... well it was actually me who started it, about the same issue. The only thing that came out of it was that I switched my network security to WEP for a while, but that was obviously just a workaround

---

### Post by georges4 on 2016-10-02
Up ?

---

