---
title: "Slow SSH"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by shingalated on 2008-11-02
I am running a server at home doing some simple stuff (A few websites, a jabber server, and some other stuff I don't remember)  I use comcast cable on the server's end and on my end here I am using the network at my college.  Whenever I SSH I get a super slow connection.  It is unbearably slow maybe about 22 bytes per second.  If I type a command in an SSH shell it will take about 15 seconds to appear.  This makes any sort of remote admin pretty much impossible.  I went to a coffee shop in town to use free wifi and I get the same results.  I tried running SSH on a non-standard port and get the same results.  Any ideas what is going wrong?

---

### Post by shortridge11 on 2008-11-02
try running a speedtest from your server end to see if a problem exists with that connection. You've probably already tried that, but just in case.

[http://www.whatismyip.com/speedtest/index.asp](http://www.whatismyip.com/speedtest/index.asp)

---

### Post by shingalated on 2008-11-02
I don't think I can do that easily.  My server is CLI only.  But it seems to be serving web pages and accepting HTTP uploads at a normal speed, so I think it is just SSH.

---

### Post by shortridge11 on 2008-11-02
well even if it's CLI you could at least try pinging a site.  I guess try pinging google.com
In any case, Another problem could be if you're forwarding the port to your box.  Is your network set up to forward the correct port to your box?  , what router/box setup are you using?

---

### Post by shingalated on 2008-11-03
Pinging google from the server takes an average of 44 ms.  I have both port forwarding from a non-standard port to port 22 set up and straight through port 22 external to port 22 internal.  Both have this speed issue.  SSH inside the network is fast.  With a VPN it is still slow (only slightly faster)

---

### Post by shingalated on 2008-11-06
Bump

---

### Post by john_navarro on 2008-11-06
Are there any errors in /var/log/syslog that relate to packet buffering or drops? Is this connection over a VPN?

If the connection is over a VPN try:  sudo ifconfig ppp0 mtu 1416

You will have to change ppp0 to the correct interface.

---

### Post by shingalated on 2008-11-06
No, the connection is not over a VPN I just tried that a few times to see if it would help the speed, but it did not.  There is nothing unusual in the syslog.

---

### Post by algould on 2008-11-06
In the file sshd_config, see if UseDNS is set to "yes".  If it is, change it to "no".  Then restart sshd (or reboot) and see if your performance improves.

---

### Post by shingalated on 2008-11-06
/etc/sshd_config doesn't exist, and sshd_conf exists but is empty.

---

### Post by algould on 2008-11-07
Try adding the following line to sshd_conf:

UseDNS no

---

### Post by shingalated on 2008-11-07
That helped a little, but it is still really of slow.

---

### Post by jonobr on 2008-11-07
Best way to do cli throughput testing is using something like iperf

Installing Iperf on both ends allows you try uploading and downloading files using tcp and udp.
It gives a good idea of throughput , latency, bandwidth and packet loss as well as results using different packet sizes

sudo apt-get install iperf

Theres a good few resources on the web for interpreting the results.
You could also post here.

---

