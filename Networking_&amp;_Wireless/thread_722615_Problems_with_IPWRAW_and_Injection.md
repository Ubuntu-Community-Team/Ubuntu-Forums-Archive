---
title: "Problems with IPWRAW and Injection"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by Ryanmt on 2008-03-12
Ive got a intel 3945 and ive installed the latest ipwraw-ng driver and aircrack-1.0beta1. Everything loads fine but injection fails 
```
ryanmt@ryanmt-laptop:~/Desktop/ipwraw-ng$ sudo modprobe -r ipw3945 
ryanmt@ryanmt-laptop:~/Desktop/ipwraw-ng$ sudo modprobe ipwraw 
```



```
ryanmt@ryanmt-laptop:~/Desktop/ipwraw-ng$ sudo airodump-ng eth1

 CH  7 ][ Elapsed: 8 s ][ 2008-03-12 20:58                                     
                                                                               
 BSSID              PWR  Beacons    #Data, #/s  CH  MB  ENC  CIPHER AUTH ESSID
                                                                               
 00:1AXXXXX    0        3        0    0   6  54. WPA  TKIP   PSK  BT Fu 
 00:1AXXXXX    0        6        0    0   6  54. WEP  WEP         BTBus 
 00:1XXXXXX   0        6        0    0  11  54. WEP  WEP         Belki 
 00:1XXXXXX    0       46        0    0   6  54  WEP  WEP         Ryanm 
                                                                               
 BSSID              STATION            PWR   Rate  Lost  Packets  Probes       
                                                                               
 (not associated)   00:19:XXXXXX   0   0- 0    27        4               



```


```
ryanmt@ryanmt-laptop:~/Desktop/ipwraw-ng$ sudo aireplay-ng --test eth1
20:59:53  Trying broadcast probe requests...
20:59:55  No Answer...
20:59:55  Found 3 APs

20:59:55  Trying directed probe requests...
20:59:55  00:13:64:32:25:95 - channel: 6 - 'Ryanmt'
21:00:01   0/30:   0%

21:00:01  00:1A:C4:D7:95:C3 - channel: 6 - 'BT Fusion-5924'
21:00:07   0/30:   0%

21:00:07  00:1A:C4:D7:95:C1 - channel: 6 - 'BTBusinessHub-924'
21:00:13   0/30:   0%


```

The same setup works fine in backtrack but i dont want to have to install 2 distros on my laptop and backtrack needs a few bits installing when using the live cd.

What is there different in ubuntu that stops injection from working??

Ive tried renaming the card from eth1 to wlan0 or wifi0 but that just stops the driver from loading

---

### Post by imlepid on 2008-03-13
I'm having similar issues _but_ it does occasionally work (i.e. says "Injection working!", however no AP responds to pings).  It works only the first time I try after loading the ipwraw drivers.  That is to say, I do:
modprobe -r ipw3945
modprobe ipwraw
iwconfig wifi0 rate 1M
ifconfig wifi0 up
aireplay-ng -9 wifi0
and then about 10% of the tries result in "Injection Working", the other 90% it says "No Answer..."  After that first success it doesn't work.  I have to repeat the above commands over and over.  I think there is something I'm missing because I'm hesitant to think that it it's purely a chance thing.

I tried the iwlwifi w/ injection drivers ([http://tinyshell.be/aircrackng/forum/index.php?topic=2898](http://tinyshell.be/aircrackng/forum/index.php?topic=2898)) but couldn't get those working either.  Any help would be much appreciated.

---

### Post by Ryanmt on 2008-03-13
Ive also had it working a few times but its very hit and miss, the test sometimes get 1 reply to the 30 packets it sends, fake auth has never worked.

Does anybody have a solution? Whats so different between Ubuntu and Backtrack that stops the driver from working properly!

---

### Post by imlepid on 2008-03-13
Ok, I've made a ton of progress and have even successfully cracked a 40-bit key!  Basically, I stopped doing the test pings with airplay and proceeded to the next step when I knew that injection was working.  Here is the latest:

1) I was successfully able to get it to say "Injection Working!" after every time I loaded the raw drivers.  BUT after it said it once it never said it again until I removed the raw drivers and reloaded them.  So, what I did was /assume/ injection was working when I loaded the module and proceeded to the next steps of monitoring + injecting.  After gathering some data, I cracked it and was in!

2) Next, I went to work on a 128-bit WEP network and got no where fast.  I did the same process as before but the data came in much more slowly.  Perhaps the signal wasn't as good as before?  I let it run for 20 minutes with aircrack constantly saying it needed 5,000 IVs where as I only had ~200.  Is this normal?

3) The biggest issue right now which is causing me great anxiety, is that my laptop has frozen 3 times in the course of doing this (mouse doesn't move and nothing responds).  I blame it on the "untested" nature of these raw drivers.  Is anyone else out there having the same things happen?  Is there any solution?

---

### Post by Ryanmt on 2008-03-14
re 2) - thats a sign that injection isnt working, the number of IVs should go up alot faster than that. With the 40bit key i think you just gathered enough IVs to crack it without having to inject to speed up the process.

re 3) Ive had it happen once, i just put it down to bad drivers same as you.

---

### Post by Ryanmt on 2008-03-15
*bump* nobody got any ideas??

---

### Post by Ryanmt on 2008-03-18
*thump*

---

### Post by Ryanmt on 2008-03-22
upgraded to hardy heron and still the same problem, booo!

---

### Post by Ryanmt on 2008-03-24
Ive got the latest Ipwraw driver installed (2.3.4) and it seems to work fine when scanning for networks etc. Im using aircrack-ng1.0beta1

My problem is that when running aireplay-ng --test wifi0 that it will only inject once, the first result is aways 1/30 and the latter tests are always 0/30, Dropping the rate down to 1mb has had no effect. 

my dmesg output might throw some light on things. This error is repeated over and over ... i suspect for each time it tries to inject after the initial success 

```
[ 2464.649396]  =======================
[ 2464.649451] WARNING: at include/asm/dma-mapping_32.h:25 dma_map_single()
[ 2464.649457] Pid: 9204, comm: aireplay-ng Tainted: P        2.6.24-12-generic #1
[ 2464.649476]  [<f8af2635>] ipw_net_hard_start_xmit+0xd95/0xe90 [ipwraw]
[ 2464.649504]  [<c0124b0e>] __wake_up+0x3e/0x60
[ 2464.649539]  [<f9c1b090>] packet_rcv+0x0/0x3a0 [af_packet]
[ 2464.649553]  [<c02a64bc>] dev_hard_start_xmit+0x21c/0x2a0
[ 2464.649570]  [<c02b831b>] __qdisc_run+0x5b/0x1a0
[ 2464.649582]  [<c029cb32>] sock_alloc_send_skb+0x162/0x1b0
[ 2464.649597]  [<c02a8a77>] dev_queue_xmit+0x227/0x300
[ 2464.649605]  [<c02a1cf7>] memcpy_fromiovec+0x37/0x60
[ 2464.649619]  [<f9c19e2c>] packet_sendmsg+0x21c/0x270 [af_packet]
[ 2464.649642]  [<c0299aa9>] sock_aio_write+0x109/0x120
[ 2464.649655]  [<c0122ef7>] update_curr+0x87/0x110
[ 2464.649681]  [<c018def5>] do_sync_write+0xd5/0x120
[ 2464.649692]  [<c031776a>] schedule+0x20a/0x600
[ 2464.649700]  [<c01449b2>] enqueue_hrtimer+0x72/0x100
[ 2464.649724]  [<c0141b80>] autoremove_wake_function+0x0/0x40
[ 2464.649739]  [<c0318329>] do_nanosleep+0x59/0x70
[ 2464.649751]  [<c014532c>] hrtimer_nanosleep+0x5c/0xd0
[ 2464.649767]  [<c0144cb0>] hrtimer_wakeup+0x0/0x20
[ 2464.649783]  [<c018e8a1>] vfs_write+0x161/0x170
[ 2464.649798]  [<c018ef31>] sys_write+0x41/0x70
[ 2464.649813]  [<c01053c2>] sysenter_past_esp+0x6b/0xa9
[ 2464.649838]  =======================

```

---

### Post by msjones on 2008-04-11
sorry to bump this.

Has anybody got ipwraw working for them in Hardy?!

---

### Post by mahdi on 2008-04-17
Sort of works for me. I also Ryanmt's problem, but that is an known issue (ipwraw-ng is not compatible with aireplay -9 on aircrack 1.0 suite). The attacks, however, seem to work. Skip the testing step and proceed directly to the attack steps. If it can't inject, try reloading ipwraw, rebooting, etc... I'm running up-to-date hardy with ipwraw and was able to crack a 64bit WEP last night (my own AP, just for testing issues).

---

