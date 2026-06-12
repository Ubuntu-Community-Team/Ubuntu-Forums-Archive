---
title: "[SOLVED] possible unauthorized ftp access?"
date: 2007-11-20
forum: Networking &amp; Wireless
---

### Post by dave37 on 2007-11-20
I am running dapper desktop for a simple Samba soho file server serving one directory to two machines on my internal LAN.  I recently have it set up to do a nightly backup using sbackup 0.10.4.  I began noticing that even though the nightly backup run which uploads to my ftp account on a webhosting service had completed, there was still a lot of activity on that local machine's network, to the point that it was bogging down the rest of the lan.

I ran the netstat command yesterday and it showed an established connection through ftp to a website also hosted by the same company that hosts my website and ftp.  Not being a security expert I was puzzled.

Again this morning the same thing, here is the relevant output of netstat:

```
mgrant@mlgpc-server:~$ netstat
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        1      0 192.168.2.3:60048       48h00.com:ftp           CLOSE_WAIT
tcp        0      0 192.168.2.3:60054       48h00.com:ftp           ESTABLISHED
tcp        0      0 localhost:52318         localhost:38802         ESTABLISHED
tcp        0      0 localhost:38802         localhost:52318         ESTABLISHED
tcp        0  88952 192.168.2.3:42595       48h00.com:50049         ESTABLISHED
tcp        1      0 192.168.2.3:39885       48h00.com:50071         CLOSE_WAIT
```


It clearly (to me) shows an established connection to 48h00.com through ftp, even though I did not intervene to initiate the connection, which I find quite worrisome.  Besides the bogging down of my network, what exactly is it transferring or doing that is causing the bog down?

My hosting company responded that it was not a hack, it was an ftp connection. (I think they thought I was running an ftp server on the local machine)  I have replied that since I am not running an ftp server, and a portscan shows no open port 21, how is this other connection coming from their end?

Just in case I have reported it as a bug, but how can I block ftp access from 48h00.com?  My router only allows a none or all blocking of ftp, and allows blocking of [www.48h00.com](www.48h00.com) but not [ftp://48h00.com](ftp://48h00.com)  (I'm using an smc 2804wbrp-g home router with firewall on).

Thanks!

---

### Post by netztier on 2007-11-20
> **dave37 said:**
> Besides the bogging down of my network, what exactly is it transferring or doing that is causing the bog down?


(please use CODE tags when you post command output, so it will be interpreted with a fixed-with font that renders "text table" information a lot more readable)

Most common broadband connections have a much lower upstream bandwith  than downstream.
If that connection is outbound (i.e. uploading things) to that remote site, your upstream bandwith is probably fully saturated. 

Now if you want to download something, the downloading TCP connection depends on small "TCP ACK" messages that must make it back to the server so that it can continue sending the next "batch of data packets" - upon it will wait for another ACK message from the client. If these ACK messages are delayed or dropped because he upstream capacity is completely congested, the server will spend a lot of time waiting for the client's ACKs (while holding back data to be send) and will try to retransmit unack'ed batches of data packets. As the main result, the download rate will drop through the floor. 

Check if you can enable some QoS features on your broadband router, it can take care of this and will make sure that TCP ACKs are treated with preference and find their places as small packets (60bytes) between the larger packets of the upload stream. 

Now where that upload stream comes from is yet another question. 

Try **sudo netstat -napt**, so you'll see the process ID or program name that is using that open socket.

best regards

Marc

---

### Post by dave37 on 2007-11-20
Thank you.  The router has SPI but that is about it for QOS.  I will try what you have suggested.  Thank you for the suggestion on the code tags, I was wondering how to make it display properly.

---

### Post by dave37 on 2007-11-20
My hosting provider responded this morning with the following, which still concerns me as while this was accidental, perhaps it could be done maliciously to gain access to a local system.  When they refer to "your server" they are referring to their server that my site is hosted on.  I have requested that they follow up with the root cause in detail.

Here is their response:

We have identified the FTP issue. It appears that the 48h00.com account was once active on your server. It recently expired but was never properly shut down. There may have been some incorrect DNS cross linking going on here and our admins are currently trying to identify the exact cause of the problem to make sure it won't happen again.

We have removed this account from your server now and you should not experience anymore FTP problems from it.

Please feel free to contact us again at any time if you need additional assistance. Thank you for contacting us.

I'll report back if they respond back with a root cause.

---

### Post by netztier on 2007-11-20
> **dave37 said:**
>  Thank you for the suggestion on the code tags, I was wondering how to make it display properly.

Just mark the text to display as "Code" with the mouse and use the toolbar button "#" (the hash sign). You can even try this by editing your first post - might have to press the "go advanced..." button to get all the editing tools displayed.

regards

Marc

---

### Post by dave37 on 2007-11-27
The hosting company changed something as it is now all working fine, didn't do anything at my end.

---

