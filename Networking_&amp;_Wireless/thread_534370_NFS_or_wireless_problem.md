---
title: "NFS or wireless problem"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by WMG_Perth on 2007-08-25
Hi,

Last weeks I have been trying to get NFS working between my laptop and server via a wireless router. I set up three directories at the server that automatically get mounted on my laptop during start up. Mounting works fine: on my laptop I can navigate to the directories on the server and read the content.
However, writing to the server stalls after a couple of seconds especially when I try to copy multiple files. Copying starts with a speed of about 30KB/s and within seconds drop down to zero and the copying is stalled.
Since I can read files from the server and since the internet connection on the server works fine, I think it is not a problem with the wireless connection on the server, but I'm not 100% sure.

I tried various settings in the export file on the server, currently I have:

/home/andrea/server-andrea 10.1.1.1(rw,no_root_squash,async,no_subtree_check) 10.1.1.2(rw,no_root_squash,async,no_subtree_check) 10.1.1.3(rw,no_root_squash,async,no_subtree_check)

/home/wouter/server-wouter 10.1.1.1(rw,no_root_squash,async,no_subtree_check) 10.1.1.2(rw,no_root_squash,async,no_subtree_check) 10.1.1.3(rw,no_root_squash,async,no_subtree_check)

/home/wouter/server-music 10.1.1.1(rw,no_root_squash,async,no_subtree_check) 10.1.1.2(rw,no_root_squash,async,no_subtree_check) 10.1.1.3(rw,no_root_squash,async,no_subtree_check)

On my laptop the relevant lines in fstab are

10.1.1.4:/home/wouter/server-wouter /home/wouter/server-wouter nfs rsize=8192,wsize=8192,rw,hard,intr 0 0
10.1.1.4:/home/andrea/server-andrea /home/andrea/server-andrea nfs rsize=8192,wsize=8192,rw,hard,intr 0 0
10.1.1.4:/home/wouter/server-music /home/server-music nfs rsize=8192,wsize=8192,rw,hard,intr 0 0

If I'm correct these settings are for NFSv2, I tried NFSv4 as well, but basically got the same results.

I checked various log files but could not find anything relevant, but I might be missing things. 
Is there anybody who could help me?

Thanks

---

### Post by Debrann on 2007-08-25
Hi..,
Just new to Linux world but not to computering, I also experience the same trouble, thru wireless no sharing, no matter how many configurations tried, simply it doesnt work. 
How ever I can see the machine, a desktop with mandriva amd64 with raid 0 and cable link to the router, (static IP), from a wirelss laptop, Intel 3945, I cannot manage to see the contents of the files shared, (NFS or SMB), neither from this, neither from the desktop. 
But I do see, and others do see me if connexion to router and from this to computers if its thru RJ45, no matter if windows XP or Linux. 
Does it relater to wireless wep encription ?
For sure I am doing something wrong, but after long time searching for clues in the forums had no luck.
Any good samaritan to share time and acknowledge this poor and unfortunate?
Just for the score, my config is just plain, no special rigs, only the modules needed to establish comunication. 
Thnx in advance.

---

### Post by WMG_Perth on 2007-08-27
Thanks Debrann.

Although the problems seem to be similar, I do have read access to my NFS server. The problem is really with writing to the NFS share.

My server uses a Atheros AR5005G wireless card. I have used the default ath_pci driver as well as the ACER net5211 driver via ndiswrapper.
While using ndiswrapper my signal strength is around 75, using ath_pci normally gives only 35. However, still no write access via NFS.
I have been changing the ipfrag_high_thresh and ipfrag_low_thresh values as well, but it does not seem to make a difference.

Anyone has an idea?

---

### Post by Debrann on 2007-08-30
Hi WMG_Perth..,

I see you are deeply involved with server matters, I do gont so far yet.
Unfortunately I cant, I only see there is a network, but I cant go any further, sorry to not be a help, but anyone over there can give us a hand ?

---

### Post by netztier on 2007-08-30
> **WMG_Perth said:**
> 
Since I can read files from the server and since the internet connection on the server works fine, I think it is not a problem with the wireless connection on the server, but I'm not 100% sure.


Wireless Networks have a strong tendency to be lossy. Now...

As you define with the  rsize= and wsize= mount options, your NFS requests are 8192bytes in size. 

Packet size on Ethernet and Wireless is 1500 bytes. Each NFS read or write request needs up to 6 Ethernet Frames to be transported. If only one of them is lost due to data corruption, the whole NFS request goes "down the drain" and has to be repeated. On a full duplex wired ethernet, packet loss is practically zero, on a classical 10Mbit Half duplex network, you are bound to lose some packets due to collisions. On a Wireless LAN however, packet loss is very common.

At first, install **iPerf** from the universe repositories and see what throughputs in raw tcp you can achieve between server and client. Be sure to try client and server role in iPerf at both ends (nota: iPerf has an inversed notion of "server" and "client": the client is *sending* to the server.

Then you might want to try either or both of these:
[LIST]
[*] go for NFS-over-TCP with the option **proto=tcp** in /etc/fstab. TCP brings an extra layer of flow control, error detection and retransmission.
[*] reduce rsize/wsize to 1024 bytes, so each NFS request fits into one Ethernet frame. A packet loss won't trigger the retransmission of 6 but only 1 frame.
[/LIST]

best regards

Marc

---

### Post by WMG_Perth on 2007-09-01
Hi Marc,

Thanks for the reply.
I installed iperf and got the following results: with my server in the server role I got on average 8.8Mbits/sec. With my server in client role I got on average 5.5Mbits/sec.

I tried both options you gave, using proto=tcp and reducing [r/w]size to 1024. But still not the results I would like to have.
However, I noticed that I was able to write large files to my server: copying a couple of mp3 files (average size 6MB) to the server was no problem. However, copying a couple of small files (average size < 100 KB) makes nfs hanging during the copy of the first file: copying starts with a speed of 30 KB/sec and within seconds goes back to 0 and the copy stalls. I then have to restart nfs on the client to have my konsole or konqueror reacting again.

Thanks, 

Wouter

---

### Post by netztier on 2007-09-02
> **WMG_Perth said:**
> 

Thanks for the reply.
I installed iperf and got the following results: with my server in the server role I got on average 8.8Mbits/sec. With my server in client role I got on average 5.5Mbits/sec.


Hm, a 802.11g WLAN is able to reach 20-25MBit/s - sounds like WLAN client and the AP are a bit apart. Are the results better when you are near the WLAN AccessPoint? If there's other RF active devices in your household (such as wireless speakers of your stereo or your neighbors WiFi network on the same or nearby channel, switching to another WLAN channel might help - remember to leave a gap of at least four channels to your neighbor's WiFi if there is one).

> **WMG_Perth said:**
> 
I tried both options you gave, using proto=tcp and reducing [r/w]size to 1024. 


Did you try them one by one? Try switching back to UDP but keep the rsize/wsize down at 1024 and see what happens.

I'm not quite sure, but have the statement somewhere back in my head that using TCP for NFS lets the rsize/wsize default to 32k, but I can't remember if that value can be overridden with lower values.

Please let us also know the results from both NFS and iPerf when the WLAN client is close to the AccessPoint.

best regards

Marc

---

### Post by WMG_Perth on 2007-09-03
ok, I put both computers close to the AP (within 1 meter). 
The results for iPerf are as follows:

Server running in server role: average 8.8Mbit/sec. Server running in client role: average 9Mbit/sec.

No other wireless networks were available at the time of testing.
Signal strength according KWifiManager: server 100, client 99

The results for copying via NFS (both machines still within 1 meter from AP):
I changed the fstab and removed the proto=tcp so only the rsize=1024 and wsize=1024 remained. After remounting, trying to copy multiple smaller files failed with the first file, copying simply stopped after 1 or 2 seconds.
Changed the fstab to put the proto=tcp back and removed the rsize=1024 and wsize=1024. After remounting got basically the same result: copy stalled after 1 or 2 seconds while copying the first file.
In both situation, konqueror just hangs and has to be killed.

Thanks, Wouter

---

### Post by AchimRS on 2007-09-03
Hi WMG_Perth,
I', not sure whether it is really a data transfer problem or only a problem in the status-display of the copy process.
I have the same problem. With Feisty and Gutsy and even under SuSE 10 - also with wireless WLAN (WiFi 11Mb via FritzBox) and LAN (100Mb Ethernet): 
If I copy big files with KDE, after some seconds the "Copying" window says "stalled" and the progress bar don't move anymore for about 2 minutes, than it continues as it should for some seconds and stalles again... until the file recently is completly transferred.

I just did some measurements with KDE System Guard performance monitor. I put the sensors 
**localhost->Network->Interfaces->ath0->Transmitter->Data **
on the client and 
**...Receiver->Data **
at the server into the system-load worksheet as Signal Plotter.
Now I saw on both, the client and the server, continuous data flows leaving/arriving at the machines. There is no change in data-flow during the copy-window shows "stalled" or a nice transfer-rate.
BTW, on my WiFi connected laptop the tranfer data-rate measured with the KDE System Guard is at maximum 750kbyte/s (even very close to the AP), which is net 6MBit/s on a 11Mbit/s wireless and therefore realistic.
The CPU of the sender is almost on 100%.

So I guess it is simply a bad representation of a full queue during sending in KDE...

Cheers
  Achim

---

### Post by raananschwartz on 2007-09-03
Never saw it before tbh.. and i pretty know wireless.

________________
[www.iplobster.com](www.iplobster.com)

---

### Post by netztier on 2007-09-04
> **WMG_Perth said:**
> 
Server running in server role: average 8.8Mbit/sec. Server running in client role: average 9Mbit/sec.

No other wireless networks were available at the time of testing.
Signal strength according KWifiManager: server 100, client 99


Hum. Now that's not exactly good performance. What kind of WLAN hardware do we have here? Is that 802.11g or 802.11n? With 802.11g, you should be seeing 22-25Mbit/s in either direction, but of course not bidirectional. 

OTOH, coming to think of it... If both server and client use WiFi in this scenario, this is normal. Data travels from the server to the AP and from there to the Client - so each data packet uses the "medium" twice, occupies the "carrier" twice - at the price of halving the throughput. 

Consider connecting the server with a wired connection and see what iPerf delivers now - even if it's just for testing, then start experimenting with NFS again. I've found a paper that showed best throghputs with [r¦w]size of 4096 in a (old) WiFi environment.

You can also use **dd** to write and read from an NFS-mounted (or any other, at that) directory - I'll have to look up the command syntax (I just can't properly remember it)  and I'll post them later or tomorrow.

best regards

Marc

---

### Post by WMG_Perth on 2007-09-04
@Achim, I checked the System Guard output and the graph goes back to zero on the server as well as the client after one initial peak(shorter than a second). It then stays around zero.
The stalling you describe I have seen while copying large files. For me it says *sometimes* for some seconds 'stalled' but the copying just continued. However, with small files it just really stalls.

@Marc, I tried the dd command with dd if=/home/wouter/somefile.txt of=/home/wouter/server-wouter/somefile.txt (I'm not sure that is what you had in mind) and it just stalled. After restarting and checking the server an empty files had been created, zero bytes in size.
I'll try to use the wired connection for the server and let you know.

Thanks,

Wouter

---

### Post by netztier on 2007-09-04
> **WMG_Perth said:**
> 
@Marc, I tried the dd command with dd if=/home/wouter/somefile.txt of=/home/wouter/server-wouter/somefile.txt (I'm not sure that is what you had in mind) and it just stalled. After restarting and checking the server an empty files had been created, zero bytes in size.


That's indeed what I had in mind, but you need to specify block size and block count. Plus you can use **/dev/zero** as an "infinitely fast" source of data (well.. all zeros, of course) and **/dev/null** as "infinitely fast" drain for something you read via NFS, so you can always keep the local disk I/O out of the equation:

So, from the client you do the **write test** first, resulting in a 8k x 32k = 256MByte file:

```
dd if=/dev/zero of=/path/to/nfs-mount/fileofzeroes bs=8k count=32k
```

used locally on my Laptop, that's the result I get:
```
marc@torch:~$ **dd if=/dev/zero of=/tmp/zerofile bs=8k count=4096**
4096+0 records in
4096+0 records out
33554432 bytes (34 MB) copied, 0.141803 seconds, 237 MB/s

```

The you do the **read test** for all of the 256MBytes:

```
dd if=/path/to/nfs-mount/fileofzeroes of=/dev/null bs=8k count=32k
```

The interesting thing about the block size is that you can match it to the NFS request size (rsize/wsize) or keep it just below that so that dd's block always fits into one NFS request. Of course, you can always use any other file of interest.

The advantage of **dd** over **iPerf** and the other raw-TCP/UDP oriented tools (which deserve their own place and right-to-be in the network debugging world) is that it uses any underlying mechanism you want it to, provided it can be accessed as a "file": NFS, CIFS, SMBFS, SSHFS, Gnome-VFS etc.

best regards

Marc

---

### Post by WMG_Perth on 2007-09-04
ok, running dd as you indicated

```
wouter@laptop:~$ dd if=/dev/zero of=/home/wouter/server-wouter/fileofzeroes bs=8k count=32k
32768+0 records in
32768+0 records out
268435456 bytes (268 MB) copied, 400.353 seconds, 670 kB/s

```

and reading it back

```
wouter@laptop:~$ dd if=/home/wouter/server-wouter/fileofzeroes of=/dev/null bs=8k count=32k
32768+0 records in
32768+0 records out
268435456 bytes (268 MB) copied, 301.433 seconds, 891 kB/s

```

I changed the count value to values between 1 and 25 to simulate the small files I have problems with and all went fine.
Changing the bs parameter to 1024 and the count value between 1 and 25 went fine as well.
I'm not getting the speeds as you indicated, but it works fine, no stalling when using the dd command.

Wouter

---

### Post by WMG_Perth on 2007-09-06
ok, I have my server now running via a wired connection.
Results with iperf are as follows: (client still within 1 meter from AP)

server in server role: average 18.0Mbits/sec
server in client role: average 9.7 Mbits/sec

I changed my fstab on the client to access my server via the wired connection and everything worked fine:confused:. I was able to copy small files, big files etc.etc.

So that leaves me with the fact that everything works fine while the server is connected via a wired connection, while I'm having trouble when the server is connected via a wireless connection. So it seems to be a wireless problem, although I can browse the internet from that server, download updates to the server, I'm running a mail server on the server without problems etc.
The wireless card in my server is an Atheros AR5005G card. I used to use the default native driver but that gave me a signal strength of only about 35. I now use the Windows driver with ndiswrapper and the signal strength is significantly higher.
I had the problems with NFS also when I used the native driver.

---

### Post by netztier on 2007-09-06
> **WMG_Perth said:**
> 
I changed my fstab on the client to access my server via the wired connection and everything worked fine:confused:. I was able to copy small files, big files etc.etc.


So that was with the client being WiFi and the server with a wired LAN connection, right? 

That's somewhat expected. NFS doesn't like LANs with high packet loss rates - which is what you had before when both client and server were sharing the available bandwith of the single AP.

Their packets travelling back and forth over the WLAN are competing *twice* for their share of free bandwith: Packets from the server first go to the AP, then from the AP to the client - using the same wireless medium - so each packet "occupies the air" twice.

The server's WLAN NIC has to back off and wait while the AP forwards the packet to the client - which itself has to wait to be able to send it's own next request. Hence the low throughput with iPerf when both client and server are connected via WLAN, and you see throughputs dropping through the floor. 

Now, with the server connected to the wired part of the LAN, all communication is "transit" for the AP, from the wireless side to the wired side or the other way - and there's no race for "free air time".

If you do SMTP and downloads from and to the server, all traffic is "transit" for the AP, not Wireless-to-Wireless traffic - hence these things work.  NFS however is "reflection" traffic for the AP, so we have the bandwith race and packet loss.

NFS was designed for low-latency LANs with not too much packet loss, which might be the reason why it fails. (see the introducing paragraphs of this document: [http://www.cs.umd.edu/projects/mcml/papers/toc97.ps](http://www.cs.umd.edu/projects/mcml/papers/toc97.ps) it's PostScript unfortunately, you'll need Ghostscript or something else to convert it to PDF or text). NFS-over-TCP should be better at this - I am still wondering why it didn't work properly when you tested it.

I therefore strongly suggest you keep that server on the wired part of the LAN - and enjoy the increased throughput you get on the Wireless part of your network. Make sure you disable the server's wireless NIC so there's never any confusion about which interface it should use, should it inadvertedly join your WiFi network.

best regards

Marc

---

### Post by WMG_Perth on 2007-09-06
Thanks for the help.
I see it might be a problem with dropped packets via the wireless connection. I'll keep it on a wired connection.
Thanks!

---

