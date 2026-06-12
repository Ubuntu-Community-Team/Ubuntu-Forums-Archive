---
title: "NFS and video over wireless"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by williammanda on 2007-05-09
I have setup a computer with a wireless connection - G 54Mhz with three other computers hard wired to a lan. I have also setup nfs on all the computers - server and client. I have been accessing video on the wireless computer from one of the other hard wired computers via nfs. The video will drop out for a moment or stop all together. This can happen randomly, after watching the video for an hour or right at the start. Is there any way of reducing the dropouts or eliminating them? I setup the nfs per this tutorial: [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)
My settings are:
Server:
/etc/exports

For Full Read Write Permissions allowing any computer from 192.168.1.1 through 192.168.1.255

/home 192.168.1.1/24(rw,no_root_squash,async)

Client:
/etc/fstab
 
192.168.1.100:/home /C2D nfs rsize=8192,wsize=8192,timeo=14,intr

The names and addresses change accordingly for other computers but all have the same settings otherwise.

Also I use Mythtv with the above setup but not using nfs and the same problem exists of dropouts.
Thanks

---

### Post by williammanda on 2007-05-09
I wanted to add that I am using feisty on all computers but mixed, 32 bit and 64 bit. The wireless is 32 bit. I'm thinking at this point it is more of a network issue than anything else. Any ideas on fine tuning how the network address dropouts?
Thanks

---

### Post by williammanda on 2007-05-11
Any takers?

---

### Post by netztier on 2007-05-11
> **williammanda said:**
> 
Also I use Mythtv with the above setup but not using nfs and the same problem exists of dropouts.
Thanks

That should rule out NFS as the culprit. The next question is: does the problem exist if you (temporarily) use wired Ethernet for the server? With both MythTV and NFS?

Another question: what kind of throughput do you achieve over your WLAN? Consider using **iPerf** to do some tests, it should be available in either universe or multiverse repositories.  If you get something in the 22-25Mbits/s range, consider it good. "54Mbps" is basically a lie already.

Then again: are there other sendersin the 2.4GHz range in your environment? Wireless headsets or wireless signal transfer to stereo speakers come to mind - or a zoo of Bluetooth and wireless keyboards/mice would be another topic - or even your upstairs neighbor with his WLAN access point using the same channel as yours. So changing to another channel might be a good idea.

best regards

Marc

---

### Post by williammanda on 2007-05-11
> **netztier said:**
> That should rule out NFS as the culprit. The next question is: does the problem exist if you (temporarily) use wired Ethernet for the server? With both MythTV and NFS?

Wired ethernet works fine between every computer, for file transfer, mythtv, other video, etc....

> Another question: what kind of throughput do you achieve over your WLAN? Consider using **iPerf** to do some tests, it should be available in either universe or multiverse repositories.  If you get something in the 22-25Mbits/s range, consider it good. "54Mbps" is basically a lie already.

I have monitored the best I can so far by using the gnome monitor. I can see the bit transfer rate. Typically for SDTV or a video the transfer rate per second is 600K to 800K and for HDTV it is 1.5M to 2.5M. I watch both the sent on the wireless and the receive on the wired computer and they pretty well match each other.
I will try out the program you suggested.

> Then again: are there other sendersin the 2.4GHz range in your environment? Wireless headsets or wireless signal transfer to stereo speakers come to mind - or a zoo of Bluetooth and wireless keyboards/mice would be another topic - or even your upstairs neighbor with his WLAN access point using the same channel as yours. So changing to another channel might be a good idea.

I'm not on the same frequency for any other wlan's close by. I checked using ipconfig or iwconfig. 


Thanks for your help

---

### Post by larytet on 2008-01-19
i experienced exactly the same problem when opening video files in VLC when the files are on the remote NFS server. Connection is WiFi (Linksys, G)

I solved the problem by installing SSH on the server and mounting SFTP on the client. I discovered that FTP/SFTP transfers utilize the link much better than NFS. I can not explain this. May be packet drop kills performance of the UDP based NFS protocol,while TCP based FTP is more forgiving/tolerant.

This is not a matter of buffer size in VLC either, because for VLC the file is part of the local file system in both setups. It leaves only NFS - there is a problem with NFS performance in Ubuntu. I tend to think that this is a Ubuntu specific problem, because at least some versions of Suse and RedHat (I did not install them) work just fine in similar setups.
May be some fine tuning of NFS server is required


P.S. try to transfer large files over NFS and FTP and compare the performance. FTP tends to utilize 100% of the link, NFS fails to do so. MS NETBios behaves even better than FTP in the file transfer - rate almost does fluctuate.

---

### Post by thor2002ro on 2008-01-24
i got the exact same problem i tried kaffeine , mplayer , totem ,vlc its happening in all of them i'm streaming from a windows server share so its a client side problem... anyone got any ideeas?:confused:

---

