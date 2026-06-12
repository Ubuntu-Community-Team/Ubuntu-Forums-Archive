---
title: "How to change Swap parition priority?"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by ravi_buz on 2011-05-02
Hi,

After installing Ubuntu 11.04 i deleted the swap file and increased the swap partition size. When i hit the "TOP" command i realized my Swap files were not used and so i check it and found this swaponswapon - s[PHP]ravi@Ravi:~$ swapon -s 
Filename				Type		Size	Used	Priority
/dev/sdb5                               partition	2784252	0	-1
[/PHP]

I see that my swap file is set to a priority of -1. How should i change this so that my system uses the swap partition?

---

### Post by ~Plue on 2011-05-02
Afaik, the priority value doesn't set how much the the system uses swap. Its used for determining which partition/file should be used first when two or more swap spaces are being used. (if you add another partition or file, it would be assigned -2, a lower priority the the first one). The tendency for the system  to swap tasks is set by the [swappiness value]("https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?"), and the default used should be fine for most users.

Try opening some memory intensive tasks like multiple VMs and check the 'used' value again

---

### Post by ravi_buz on 2011-05-02
Ok! but when i see the output of Top .. Its always that my swap is not used at all. The maximum value i saw was 12KB used. I tried opening few memory hogging apps and my system completely slowed yet the swap was not used.

---

### Post by ~Plue on 2011-05-02
> **ravi_buz said:**
> Ok! but when i see the output of Top .. Its always that my swap is not used at all. The maximum value i saw was 12KB used. I tried opening few memory hogging apps and my system completely slowed yet the swap was not used.
It could be the CPU that is slowing down the system and not the shortage of RAM, in which case, try keeping an eye on both of them..
The fact that even 12kb was used means the system is able to initialize  swap..(another way to test it out is to see if the computer can  hibernate or not)

Also, keep in mind that desktop applications being swapped is not necessarily a good thing as reading from a harddisk is a lot slower that reading directly from RAM..

---

### Post by wilee-nilee on 2011-05-02
To be honest swap runs slower then the memory, it is the hd not flash.
[http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_](http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_)

Most of us are trying to avoid stuff getting swapped.

---

### Post by ravi_buz on 2011-05-02
Hey guys! thank you so much. I used all the info you guys gave and few googleing and found the solution.
I think since the UUID was changed after installing my swap was not used and so formatted the Swap file system using this command.

**sudo /sbin/mkswap /dev/sd##**

and then changed the priority and swappness value from here [https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?)

Thats all.. now my system feel faster and the swap is also used.:)

---

### Post by Jon Hanna on 2012-07-16
It might be worth adding an answer about the priority asked about in the  beginning, for people finding this page through google if they are  interested in that or (as is what brought me here, I can never remember without checking) googling to  double-check the exact spelling needed.

Prioritising how heavy or  light Ubuntu is in its use of swap is, as the OP discovered  "swappiness" and the link above shows how to increase or decrease it.

The priority mentioned by *swapon - s *is the relative priority between different swap partitions on the same machine.

Since  the OP had only one swap partition, this value makes no difference,  leave it alone or set it to 42 if you're unbearable in your  Hitchhikers' Guide fandom.

If you have more than one swap  partition, then the default will prioritise them in order listed in  /etc/fstab. You can override this. For example, my system started with  the following in /etc/fstab:

[PHP]# swap was on /dev/sda6 during installation
UUID=8f759e89-0a95-43af-8368-ea82a4b64cbe none            swap    sw              0       0
# swap was on /dev/sdb6 during installation
UUID=42750b0c-3bea-4f46-9a3a-866b98f9b425 none            swap    sw              0       0[/PHP]And running  *swapon - s* shortly after booting up might show:

[PHP]/dev/sda6                               partition    6291452    0    -1
/dev/sdb6                               partition    6291452    0    -2[/PHP]Since  I have the two partitions on separate physical drives of the same make,  I want to give them the same priority, for reasons I'll get to. So I  change my /ect/fstab to:

[PHP]# swap was on /dev/sda6 during installation
UUID=8f759e89-0a95-43af-8368-ea82a4b64cbe none            swap    sw,pri=0        0       0
# swap was on /dev/sdb6 during installation
UUID=42750b0c-3bea-4f46-9a3a-866b98f9b425 none            swap    sw,pri=0        0       0
[/PHP]And running swapon -s after rebooting will show:

[PHP]/dev/sda6                               partition    6291452    0    0
/dev/sdb6                               partition    6291452    0    0[/PHP]The absolute values don't matter, it's the relative number that does.

If  two (or more) priorities are the same, the system will try to use both  partitions at the same time. This is good for me, because my sda and sdb  are equally fast drives, and the system splitting work between them is  better for performance.

It's bad if you've two swap partitions  (or files) on the same drive, as it'll waste time jumping from one to  the other (I don't know if there's logic to avoid that). In this case  you want to prioritise them differently so it'll use up one first and  then move onto the next.

It's bad if one drive is faster than the  other. Say you had a super-fast drive that you could only spare half a  gig of swap space on - more than enough for a lot of uses with a low  swappiness value, but not enough to hibernate with - and a large slower  drive with plenty of space. Then you'd want to prioritise the fast drive  higher than the slow one, so the system won't use the slow one until  it's run out of space on the faster.

---

