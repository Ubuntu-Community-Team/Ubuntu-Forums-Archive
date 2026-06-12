---
title: "Hamachi connect error using Ubuntu Feisty Fawn"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by ProvostZak on 2007-09-05
Hi, 
    I was trying to set up Hamachi on my Dell Optiplex GX 260 using the UbuntuForums Hamachi and VNC  guide at [http://ubuntuforums.org/showthread.php?t=135036](http://ubuntuforums.org/showthread.php?t=135036). My version of Ubuntu is Feisty Fawn (7.04).  I have followed all the steps detailed in the guide exactly. However all attempts to login to the Hamachi network fail. Hamachi start works perfectly. I am attaching below the output of Hamachi in debug mode.

root@vm-ubuntu:/home/vm/Desktop/hamachi-0.9.9.9-20-lnx# sudo hamachi -c /etc/hamachi start debug
05 15:11:17.904 [ 147] [25155] ipc: login 
05 15:11:17.904 [ 147] [25155] ses: set_reconn(no)
05 15:11:17.904 [ 147] [25155] ses: go_online
05 15:11:17.904 [ 147] [25155] ses: state 1.1 -> 2.0
05 15:11:17.907 [ 148] [25155] ses: resolved bibi.hamachi.cc -> 63.208.197.212
05 15:11:17.907 [ 148] [25155] ses: state 2.0 -> 2.1
05 15:11:17.907 [ 148] [25155] ses: state 2.1 -> 3.0
05 15:11:17.907 [ 148] [25155] ses: connecting to 63.208.197.212:12975 ..
05 15:14:26.905 [ 149] [25155] ses: io_ready -- 0.0.0.0:34600
05 15:14:26.905 [ 149] [25155] ses: state 3.0 -> 3.1
05 15:14:26.905 [ 149] [25155] ses: state 3.1 -> 4.0
05 15:14:26.905 [ 149] [25155] ses: sending helo ..
05 15:14:26.967 [ 149] [25155] ses: error 2 send 32 0
05 15:14:26.967 [ 149] [25155] ses: go_offline
05 15:14:26.967 [ 149] [25155] ses: state 4.0 -> 1.0
05 15:14:26.967 [ 149] [25155] ses: state 1.0 -> 1.1
05 15:14:26.967 [ 149] [25155] ses: purging state ..
05 15:14:26.967 [ 149] [25155] ses: error 2 write 0 0
05 15:14:26.967 [ 149] [25155] ses: go_offline
05 15:14:26.967 [ 149] [25155] ses: state 1.1 -> 1.0
05 15:14:26.967 [ 149] [25155] ses: state 1.0 -> 1.1
05 15:14:26.967 [ 149] [25155] ses: purging state ..
05 15:14:26.968 [ 150] [25155] ipc: socket_recv() failed with 104

Could someone please help me with this? Am totally lost here.

---

### Post by verticaltier on 2007-11-19
Anyone have an answer to this one?  I get the same result with 7.10 also.

I had to download and install upx as hamachi would not even work.

I get the same results as above:
19 11:33:11.798 [  97] [25324] ipc: login 
19 11:33:11.798 [  97] [25324] ses: set_reconn(no)
19 11:33:11.798 [  97] [25324] ses: go_online
19 11:33:11.798 [  97] [25324] ses: state 1.1 -> 2.0
19 11:33:11.801 [  98] [25324] ses: resolved bibi.hamachi.cc -> 69.25.21.221
19 11:33:11.801 [  98] [25324] ses: state 2.0 -> 2.1
19 11:33:11.801 [  98] [25324] ses: state 2.1 -> 3.0
19 11:33:11.801 [  98] [25324] ses: connecting to 69.25.21.221:12975 ..
19 11:36:20.800 [  99] [25324] ses: io_ready -- 0.0.0.0:58045
19 11:36:20.800 [  99] [25324] ses: state 3.0 -> 3.1
19 11:36:20.800 [  99] [25324] ses: state 3.1 -> 4.0
19 11:36:20.800 [  99] [25324] ses: sending helo ..
19 11:36:20.846 [  99] [25324] ses: error 2 send 32 0
19 11:36:20.846 [  99] [25324] ses: go_offline
19 11:36:20.846 [  99] [25324] ses: state 4.0 -> 1.0
19 11:36:20.846 [  99] [25324] ses: state 1.0 -> 1.1
19 11:36:20.846 [  99] [25324] ses: purging state ..
19 11:36:20.846 [  99] [25324] ses: error 2 write 0 0
19 11:36:20.847 [  99] [25324] ipc: socket_send() failed with 32
19 11:36:20.847 [  99] [25324] ses: go_offline
19 11:36:20.847 [  99] [25324] ses: state 1.1 -> 1.0
19 11:36:20.847 [  99] [25324] ses: state 1.0 -> 1.1
19 11:36:20.847 [  99] [25324] ses: purging state ..

---

### Post by hjdivad on 2008-03-04
bump.

I have this problem on a feisty box that I used to be able to log on to hamachi with until today.

---

