---
title: "very very slow _intranet_ speeds, recently updated to 3.19 kernel"
date: 2015-11-21
forum: Networking &amp; Wireless
---

### Post by jason63 on 2015-11-21
Hey guys. I'm experiencing very slow intranet speeds.

About 3 weeks ago, I was getting 60-80 mb/s write speeds over the GbE network to my 14.04.3 server and equally fast or better read speeds. This is through the mounted drives over Samba to my Windows and Mac machines.

System is;

Ubuntu 14.04.3
[COLOR=#393939][FONT=arial]Linux 3.19.0-33-generic kernel[/FONT][/COLOR]
i5-4570
12gb ram
120gb ssd as boot/root/swap
3x WD 4tb red in Raid5 (used to store manual backups only)
3x WD 2tb green in Raid5 (used to server media/music/plex)
1x WD 500gb blue as a disk off my 3ware SAS expander (this gets motion detected video pushed to it from a IP Camera)


hdparm -Tt /dev/md0 yields buffered disk reads of 232 MB/sec on my GREEN drives and 300 MB/sec on my RED drives.

pv tests between drives shows real world speeds of 100-150 MB/sec transfers. 

So I don't believe its hardware related.

Now when I'm copying files from the server to my windows machine, I'm getting maybe ~5-7 MB/sec read and maybe  ~5 MB/sec write.


Only four things have changed, other than regular updates.


1. I've installed an IP camera to my network. This sits on a 10/100 PoE switch, which connects to my GbE router. It only pipes video to the server when it (the camera) detects motion. And even then its only a 4090 Kbps stream.

2. I have a wget cron job scheduled every 3 minutes to pull a jpg from the camera. These files are 200KB in size.

3. I got the brainwave to upgrade from Kernel 3.13.x-xx-generic to  3.19.0-33-generic

4. I've only just now noticed my ROOT partiton (of 57GB) is 99% full.

I've done speedtest-cli and found that my server can max my internet connection (57 Mbit / 3.2 Mbit up) which is actually faster than I'm getting transfers within my network :(

I've also installed bmon, and watched traffic. There are no processes gobbling up bandwidth that I can see.


Any ideas guys ?

Should I downgrade back to  Kernel 3.13 ?

Thanks

---

### Post by jason63 on 2015-11-23
Well, so I did a VM of ubuntu server. And through smbclient, I connected to the machine that was giving me the issues... and I was able to pull 50+ MB/s average speed from it. peaking at ~85 MB/s 

So it looks like its my windows machine thats causing the issues.

---

### Post by jason63 on 2015-11-30
Update, my hard wired macbook pro canget 80+ mb/s speeds from the server.

Somethings fishy.

---

### Post by jason63 on 2015-11-30
SOLVED:

Was running a program on my Windows 7 machine  called NetBalancer - that monitors network traffic. Under my ethernet card properties among the TCP/IP v4 and v6 protocols was another one pertaining to the NetBalancer App. I removed it and BOOM, 100mbps samba transfers!

---

### Post by 1clue on 2015-12-01
I think you still have something wrong. I don't use samba but my gigabit network gets 110-123 mb/s from every host. You should be close to wire speed unless the hardware just can't keep up.

---

### Post by jason63 on 2015-12-03
> **1clue said:**
> I think you still have something wrong. I don't use samba but my gigabit network gets 110-123 mb/s from every host. You should be close to wire speed unless the hardware just can't keep up.


well the drives easily benchmark locally on the server at well over 200 MB/s.

The server has more than enough power (i5-5750, 16gb ram, ssd os drive etc)

the client is even more powerful than that.

Crystal Disk mark benches the mapped network drives at;

Sequential rear and writes ~111 MB/s
512K read and writes  ~107 MB/s
and 4k QD32 ~ 114 MB/s write and 75 MB/s read

So I think everything else is good to go.

Also after retrying some copies, I can write 95-100 MB/s to the server and read almost the same.


Update: after uninstalling TeraCopy and trying coping using windows copy, I can do 110-120 MB/s . I suspect windows is over reporting transfer speeds.

---

