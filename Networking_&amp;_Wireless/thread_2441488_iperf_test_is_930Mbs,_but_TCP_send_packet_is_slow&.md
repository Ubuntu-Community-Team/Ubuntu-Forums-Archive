---
title: "iperf test is 930Mb/s, but TCP send packet is slow&#65292;why&#65311;"
date: 2020-04-24
forum: Networking &amp; Wireless
---

### Post by yangjian123 on 2020-04-24
I have an HTTP server, and two ports&#65288;eth1 and eth2&#65289; are LAN connections to a device to get data from the device. The HTTP server is connected to a gigabit switch through the eth0 port, which is connected to multiple PCS that access the HTTP server and request video data.



I deployed an HTTP server on the server (Intel® Atom® Processor C3758), tested 980Mb/s with iperf, and tested 980Mb/s with PC capturing HTTP video data. But when I deployed the HTTP server on an Intel i5 PC, the speed never reached 800Mb/s, and after that it dropped to 600Mb/s, but iperf tested it at 930Mb/s.



The operating system of the deployed server is: Ubuntu server 18.04, memory 4G.

---

### Post by TheFu on 2020-04-24
NICs on each?  Intel PRO/1000 or i210/211 NICs tend to scale fine.  Realtek and other NICs do not. iperf is just the NIC, not the NIC+CPU+storage.  An atom isn't too powerful, so if the webapp has to do much, then performance and throughput will be lower.  For example, if a client pulling the video requires that video to be transcoded, then an atom CPU would struggle.

Please explain what "capturing HTTP video data" means.  When I record TV, my computer uses a wget to pull a file from a network tuner which provides an HTTP interface to each broadcast TV channel.  It is basically a download and file save effort, so almost ZERO CPU involved unless the computer saving the stream also transcodes the mpeg2/TS into h.264/mkv on-the-fly for my convenience.  For me, editing mpeg2 is much easier even with the 2x larger files, so I only transcode for programs that won't be saved, like live sports. Most of the time, there will be processing to remove all commercials before I ever see the recording.

---

### Post by yangjian123 on 2020-04-26
HTTP gets video data, similar to wget without transcoding or other operations. After my HTTP server process started, I found that one of the cpus had 100% core usage and the others were around 30%. That may be the reason.

---

