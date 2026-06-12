---
title: "&quot;connection was reset&quot; error"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by watching on 2007-03-05
I've just started using Ubuntu (version 6.10), and I've been having an unusual problem while browsing the web. For every few pages that I view in Firefox, I get an error saying "the connection was reset." The error doesn't happen for every single page I load, but it happens with enough frequency to be very annoying.

The problem seems somehow related to cookies. As an example, after I sign into my Yahoo account, I get the "connection was reset" error every time I try to load a Yahoo page, and the error persists no matter how many times I try refreshing the page. However, if I delete yahoo's cookies and sign out, I can use the site with barely any problem. If I completely disable cookies in Firefox, almost every website I visit works fine. 

I thought this might have been a Firefox flaw, but using Opera resulted in the same issue. So I don't know what the problem is. My connection is through a college LAN, so it could be a network problem, but when I use Firefox on Windows over the same network, I don't get this error at all. If anybody has an idea of what is causing this problem, or how it might be fixed, I'd be glad for your input.

---

### Post by Mr. C. on 2007-03-05
Verify that your network is function correctly.

ifconfig -a
ethtool -S eth0 (or whatever your ethernet device is)

Look at /etc/resolv.conf

Verify that the ip addresses there are reachable quickly by trying:

host  [www.apple.com](www.apple.com) DNS_IP1_HERE
host  [www.harvard.edu](www.harvard.edu) DNS_IP2_HERE
host  [www.mit.edu](www.mit.edu) DNS_IP3_HERE

replacing DNS_IP{1,2,3}_HERE with each IP address you see - go from topmost to bottom.   If the queries for each host come back quickly, your DNS is resolving properly.  If they take 10 or more seconds, and then fail, remove, or move lower in the file, that DNS entry.

Let's start with this,
MrC

---

### Post by watching on 2007-03-05
Thanks for replying.

I tested the DNS servers as you said, and they worked fine, with no delay. My overall connection seems fine, it's just that I get the error nearly every time I try to load pages that require cookies. I'm using Windows now, because after I logged into this forum to reply, I couldn't even open the page to post a message without getting the error.

The results from "ifconfig -a" and "ethtool -S eth0" are below.

```

ifconfig -a

eth0    Link encap:Ethernet  HWaddr 00:17:31:F7:71:2E  
          inet addr:138.49.166.35  Bcast:138.49.167.255 Mask:255.255.254.0
          inet6 addr: fe80::217:31ff:fef7:712e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:61666 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31847 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:66375201 (63.3 MiB)  TX bytes:3043053 (2.9 MiB)
          Base address:0xff00 Memory:fdfc0000-fdfe0000

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3745 (3.6 KiB)  TX bytes:3745 (3.6 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

```

ethtool -S eth0

NIC statistics:
     rx_packets: 63187
     tx_packets: 32550
     rx_bytes: 68026686
     tx_bytes: 3100467
     rx_errors: 0
     tx_errors: 0
     tx_dropped: 0
     multicast: 0
     collisions: 0
     rx_length_errors: 0
     rx_over_errors: 0
     rx_crc_errors: 0
     rx_frame_errors: 0
     rx_no_buffer_count: 0
     rx_missed_errors: 0
     tx_aborted_errors: 0
     tx_carrier_errors: 0
     tx_fifo_errors: 0
     tx_heartbeat_errors: 0
     tx_window_errors: 0
     tx_abort_late_coll: 0
     tx_deferred_ok: 0
     tx_single_coll_ok: 0
     tx_multi_coll_ok: 0
     tx_timeout_count: 0
     rx_long_length_errors: 0
     rx_short_length_errors: 0
     rx_align_errors: 0
     tx_tcp_seg_good: 0
     tx_tcp_seg_failed: 0
     rx_flow_control_xon: 0
     rx_flow_control_xoff: 0
     tx_flow_control_xon: 0
     tx_flow_control_xoff: 0
     rx_long_byte_count: 68026686
     rx_csum_offload_good: 52003
     rx_csum_offload_errors: 0
     rx_header_split: 52003
     alloc_rx_buff_failed: 0

```

---

### Post by Mr. C. on 2007-03-06
Ok, great.  The network looks clean.

- Do you have any Antivirus products running?
- Any Firefox / Opera add-ons, extensions, plug-ins ?
- Any proxies ?
- Is your firewall congured correctly?
- Does the problem occur with the firewall competely disabled?

It doesn't appear to be browser related, since both FF and Opera experience the same issue.

The browser is losing the connection whilst it is loading the page.  The question is, why is it loosing the connection?

Are you connected via PPPoE?

MrC

---

### Post by watching on 2007-03-06
Well, I'm not using PPPoE, and I haven't really modified any of Ubuntu's defaults for the network connection. No browser add-ons, no antivirus, no proxies, and no firewall, unless Ubuntu comes preconfigured with something. I know there is a firewall on my network, but I don't have access to that.

---

### Post by Mr. C. on 2007-03-06
Have you tried deleting all your cookies?  I thought you had, but now after re-reading your original post it seems only Yahoo's were deleted.

Try deleting all, exiting the browser, and see how Yahoo's pages load.

MrC

---

### Post by watching on 2007-03-06
I had actually deleted them all. The pages load without a problem once the cookies are deleted. But as soon as I accept cookies from some site, I start getting the error message again.

---

### Post by Mr. C. on 2007-03-06
Hmmm... this one is stumping me, but I keep thinking of packet fragmenting.

If you're comfortable with the tools, you could run tcpdump or wireshark and see what's happening at the packet level with the cookie TCP transaction.

That's where I'd go next personally,
MrC

---

### Post by watching on 2007-03-07
Well, I can certainly run the tools, but I don't really have any knowledge of networking, so I'm not sure what I'd be trying to find in the logs. Is there anything specific I should be watching for?

---

### Post by Mr. C. on 2007-03-08
Sorry, I dropped the ball on this one.  Is this still an issue?

MrC

---

### Post by IUPaterade724 on 2007-03-17
I have been Googling this problem for about a week and finally came across a thread on here with something similar but looks dead.  I have basically the exact same problem.  First let me say I don't know a great deal on computers compared to the mods that usually run theses sites, but am usually able to follow the answers they give.   I run the latest version of Firefox on Windows XP, Dell Inspiron 1150 laptop.  I have tried 2 different linksys Wrt54g routers and both gave me the same problem.  Also, I have reset them.  So I know it has nothing to do with them.  My connection never drops either.  I run AIM along with torrent downloaders a lot and they never have a problem.  It is only when I try and browse web pages.

Also to narrow down the problem,  I have a roomate whos computer is wirelessly configured to our router, along with mine.  When I take my computer entirely off the network, his computer works fine.  When I have mine wired into the network, his computer works fine.  However, when I have my computer running wirelessly...BOTH our computers get the "The Connection was Reset" error 2 out of 3 times we click on links on average.

I am stumped mostly because, I am thinking it isn't "physical" meaning my wireless card, because my AIM and Utorrent never stop working.  Its almost likely sometime the webpage tries to download too quick.

If this helps, I hope you come up with Something!

---

### Post by Mr. C. on 2007-03-17
IUPaterade724,

Because you indicate that the problem occurs to both you and your roommate when you are connected, I have to believe this is a router problem or an IP address  There is nothing your roommate's connection can really do for it to cause your connection's to be reset (I'm ignoring malicious intent).

There is no problem with web pages downloading too quickly.  Problematic hardware often shows itself during certain types of operations, but not others.  Web browsing, for example, makes dozens or more quick connections, whereas connection used by apps such as AIM or torrents are longer term.

Let's get some data about that router.  What make, model (you said Wrt54g), revision and firmware version ?

MrC

---

