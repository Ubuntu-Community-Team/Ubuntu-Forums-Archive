---
title: "SAMBA Share Becomes Inaccessible to Windows Computers Occassionally"
date: 2014-02-02
forum: Networking &amp; Wireless
---

### Post by jesse-8 on 2014-02-02
I have recently installed Ubuntu 12.04 with the intention of using it as a simple fileserver. 

I enabled the share by right clicking on my public folder and going to share options. I installed Samba (version 3.6.3), like it requests, and then checked that users could both read and write, as well as enabling guest accounts. I then set the folder permissions to 0777.

Initially it worked fine. All computers on the network could access the share, as well as create, modify and delete files/folders.

Occasionally, however, the connection seems to drop for the Windows computers. Once the connection has been dropped Windows users begin to have problems with permissions, which typically can only be resolved by restarting their computer. All work they had been doing is lost.

Here is a samba log for one of the Windows machines: 

```
[2014/01/27 19:57:05.616120,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/27 19:57:06.156330,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/27 19:57:06.555439,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/27 19:57:07.202654,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/27 19:57:23.280258,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/27 19:57:23.292040,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/27 19:57:23.887695,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/27 19:57:23.890911,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/27 19:57:24.399822,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/27 19:57:24.402479,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/27 19:57:24.851230,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/27 19:57:24.851397,  0] lib/fault.c:47(fault_report)
  ===============================================================
[2014/01/27 19:57:24.851435,  0] lib/fault.c:48(fault_report)
  INTERNAL ERROR: Signal 11 in pid 4263 (3.6.3)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2014/01/27 19:57:24.851482,  0] lib/fault.c:50(fault_report)
  
  From: http://www.samba.org/samba/docs/Samba3-HOWTO.pdf
[2014/01/27 19:57:24.851527,  0] lib/fault.c:51(fault_report)
  ===============================================================
[2014/01/27 19:57:24.851559,  0] lib/util.c:1117(smb_panic)
  PANIC (pid 4263): internal error
[2014/01/27 19:57:25.110828,  0] lib/util.c:1221(log_stack_trace)
  BACKTRACE: 22 stack frames:
   #0 smbd(log_stack_trace+0x1a) [0x7f6b699dee3a]
   #1 smbd(smb_panic+0x25) [0x7f6b699def15]
   #2 smbd(+0x40a1d8) [0x7f6b699d01d8]
   #3 /lib/x86_64-linux-gnu/libc.so.6(+0x364a0) [0x7f6b6657f4a0]
   #4 /lib/x86_64-linux-gnu/libc.so.6(+0x89111) [0x7f6b665d2111]
   #5 smbd(push_ucs2_talloc+0x2c) [0x7f6b699cddec]
   #6 smbd(E_md4hash+0x1e) [0x7f6b697a9b8e]
   #7 smbd(create_volume_objectid+0x27) [0x7f6b6970a8c7]
   #8 smbd(+0x126ede) [0x7f6b696ecede]
   #9 smbd(reply_nttrans+0x75f) [0x7f6b696ef46f]
   #10 smbd(+0x177224) [0x7f6b6973d224]
   #11 smbd(+0x17763b) [0x7f6b6973d63b]
   #12 smbd(+0x177a53) [0x7f6b6973da53]
   #13 smbd(run_events_poll+0x34e) [0x7f6b699eebfe]
   #14 smbd(smbd_process+0x812) [0x7f6b6973f1c2]
   #15 smbd(+0x686b8f) [0x7f6b69c4cb8f]
   #16 smbd(run_events_poll+0x34e) [0x7f6b699eebfe]
   #17 smbd(+0x428d9a) [0x7f6b699eed9a]
   #18 smbd(_tevent_loop_once+0x90) [0x7f6b699ef920]
   #19 smbd(main+0xed0) [0x7f6b696bd090]
   #20 /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed) [0x7f6b6656a76d]
   #21 smbd(+0xf7575) [0x7f6b696bd575]
[2014/01/27 19:57:25.111236,  0] lib/util.c:1122(smb_panic)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 4263]
[2014/01/27 19:57:25.189889,  0] lib/util.c:1130(smb_panic)
  smb_panic(): action returned status 0
[2014/01/27 19:57:25.189988,  0] lib/fault.c:372(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2014/01/27 19:57:28.300020,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/27 19:57:28.302768,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:10:31.217539,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:10:31.548538,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:10:31.552341,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:10:31.889528,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:10:32.297193,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:10:32.300328,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:10:33.297304,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:10:33.300505,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:10:42.036042,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:10:42.039085,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:10:49.217304,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:10:49.221021,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:10:51.045975,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:10:51.049143,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:10:51.578054,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:10:51.581534,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:10:52.274800,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:10:52.277461,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:10:53.396562,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:10:53.399259,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:10:55.181796,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:10:55.184508,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:11:58.947439,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:11:59.130948,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:11:59.506165,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:11:59.510203,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:11:59.796791,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:11:59.800253,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:12:03.757120,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:12:03.759845,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:12:04.097867,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:12:04.100980,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:12:06.408728,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:12:06.411705,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:12:38.155923,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:12:38.159463,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:12:48.141734,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:12:48.144800,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:12:48.495312,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 19:12:48.511952,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:47:37.896493,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:47:37.897550,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:47:37.900723,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:47:38.220119,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:47:38.510588,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:47:38.784497,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:47:38.787790,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:47:39.124644,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:47:44.871487,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:47:45.138813,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:47:45.412695,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:47:51.838119,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:47:52.095482,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:48:08.439615,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:48:08.763163,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:48:09.078497,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:48:42.750813,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:48:43.057811,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:48:45.765852,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:48:55.610591,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:48:55.867914,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:48:56.143537,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:48:59.135330,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:48:59.400957,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:48:59.666681,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:49:03.401295,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:49:03.675178,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:49:04.048419,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:49:10.151025,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:49:11.908605,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:49:12.157669,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:49:12.464692,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:49:12.730342,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:49:12.730983,  0] lib/fault.c:47(fault_report)
  ===============================================================
[2014/01/30 21:49:12.731034,  0] lib/fault.c:48(fault_report)
  INTERNAL ERROR: Signal 11 in pid 8602 (3.6.3)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2014/01/30 21:49:12.731081,  0] lib/fault.c:50(fault_report)
  
  From: http://www.samba.org/samba/docs/Samba3-HOWTO.pdf
[2014/01/30 21:49:12.731126,  0] lib/fault.c:51(fault_report)
  ===============================================================
[2014/01/30 21:49:12.731158,  0] lib/util.c:1117(smb_panic)
  PANIC (pid 8602): internal error
[2014/01/30 21:49:12.806834,  0] lib/util.c:1221(log_stack_trace)
  BACKTRACE: 22 stack frames:
   #0 smbd(log_stack_trace+0x1a) [0x7f6b699dee3a]
   #1 smbd(smb_panic+0x25) [0x7f6b699def15]
   #2 smbd(+0x40a1d8) [0x7f6b699d01d8]
   #3 /lib/x86_64-linux-gnu/libc.so.6(+0x364a0) [0x7f6b6657f4a0]
   #4 /lib/x86_64-linux-gnu/libc.so.6(+0x89111) [0x7f6b665d2111]
   #5 smbd(push_ucs2_talloc+0x2c) [0x7f6b699cddec]
   #6 smbd(E_md4hash+0x1e) [0x7f6b697a9b8e]
   #7 smbd(create_volume_objectid+0x27) [0x7f6b6970a8c7]
   #8 smbd(+0x126ede) [0x7f6b696ecede]
   #9 smbd(reply_nttrans+0x75f) [0x7f6b696ef46f]
   #10 smbd(+0x177224) [0x7f6b6973d224]
   #11 smbd(+0x17763b) [0x7f6b6973d63b]
   #12 smbd(+0x177a53) [0x7f6b6973da53]
   #13 smbd(run_events_poll+0x34e) [0x7f6b699eebfe]
   #14 smbd(smbd_process+0x812) [0x7f6b6973f1c2]
   #15 smbd(+0x686b8f) [0x7f6b69c4cb8f]
   #16 smbd(run_events_poll+0x34e) [0x7f6b699eebfe]
   #17 smbd(+0x428d9a) [0x7f6b699eed9a]
   #18 smbd(_tevent_loop_once+0x90) [0x7f6b699ef920]
   #19 smbd(main+0xed0) [0x7f6b696bd090]
   #20 /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed) [0x7f6b6656a76d]
   #21 smbd(+0xf7575) [0x7f6b696bd575]
[2014/01/30 21:49:12.807211,  0] lib/util.c:1122(smb_panic)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 8602]
[2014/01/30 21:49:12.844486,  0] lib/util.c:1130(smb_panic)
  smb_panic(): action returned status 0
[2014/01/30 21:49:12.844590,  0] lib/fault.c:372(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2014/01/30 21:49:13.592501,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/30 21:49:14.404556,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 11:29:21.766378,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 11:29:22.056831,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 11:29:22.059472,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 11:29:22.330699,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 11:29:22.629506,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 11:29:22.911718,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 11:29:26.193021,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 11:29:32.925502,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 11:29:33.232495,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 11:29:33.506451,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 11:29:33.788649,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 14:05:51.313460,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 15:35:09.454841,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 22:19:08.395012,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 22:19:08.397936,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 22:19:08.551274,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 22:23:08.219570,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 22:23:08.224414,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 22:23:08.501834,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 22:24:11.542591,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 22:24:11.816619,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 22:24:12.073868,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 22:24:41.076855,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 22:25:40.936425,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 22:25:40.940205,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 22:25:41.202037,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 22:25:55.393404,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 22:25:55.675583,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/01/31 22:25:55.957755,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 20:32:05.663646,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 20:32:05.853678,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 20:32:05.873370,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 20:32:06.160753,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 20:32:06.393251,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 20:32:06.396027,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 20:32:06.625768,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 20:32:06.858307,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 20:33:07.535340,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 20:33:07.846181,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 20:33:08.086994,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 20:33:08.352646,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 20:36:01.605580,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 20:36:02.583213,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 20:36:02.857173,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 20:36:03.114474,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 20:36:03.355280,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:10:41.565398,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:10:41.568386,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:10:41.814462,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:10:42.535462,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:10:42.538377,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:10:42.801104,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:10:43.041919,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:11:24.081317,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:12:04.915957,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:12:04.919444,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:12:05.181577,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:12:05.438934,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:12:05.441323,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:12:08.494704,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:12:08.743775,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:12:08.747125,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:12:09.001161,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:12:45.374314,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:12:45.631680,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:12:45.872651,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:12:46.138312,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:12:46.428792,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:12:46.677898,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:12:46.993408,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:12:47.234210,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:12:47.491552,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:12:47.748971,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:12:47.989746,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:12:48.240532,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:12:48.663485,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:12:48.937407,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:12:49.186502,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:13:40.121226,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:13:40.353774,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:13:40.992022,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:13:41.249389,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:13:41.490202,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:13:41.739258,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:14:26.118194,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:14:40.624084,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:14:40.856605,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:14:40.866037,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:14:44.045137,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:14:46.811133,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:14:47.060231,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:14:47.062928,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:14:47.301060,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:14:47.533547,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:14:47.533810,  0] lib/fault.c:47(fault_report)
  ===============================================================
[2014/02/01 21:14:47.533868,  0] lib/fault.c:48(fault_report)
  INTERNAL ERROR: Signal 11 in pid 4179 (3.6.3)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2014/02/01 21:14:47.533918,  0] lib/fault.c:50(fault_report)
  
  From: http://www.samba.org/samba/docs/Samba3-HOWTO.pdf
[2014/02/01 21:14:47.533965,  0] lib/fault.c:51(fault_report)
  ===============================================================
[2014/02/01 21:14:47.533999,  0] lib/util.c:1117(smb_panic)
  PANIC (pid 4179): internal error
[2014/02/01 21:14:47.562602,  0] lib/util.c:1221(log_stack_trace)
  BACKTRACE: 22 stack frames:
   #0 smbd(log_stack_trace+0x1a) [0x7fcea5608e3a]
   #1 smbd(smb_panic+0x25) [0x7fcea5608f15]
   #2 smbd(+0x40a1d8) [0x7fcea55fa1d8]
   #3 /lib/x86_64-linux-gnu/libc.so.6(+0x364a0) [0x7fcea21a84a0]
   #4 /lib/x86_64-linux-gnu/libc.so.6(+0x89111) [0x7fcea21fb111]
   #5 smbd(push_ucs2_talloc+0x2c) [0x7fcea55f7dec]
   #6 smbd(E_md4hash+0x1e) [0x7fcea53d3b8e]
   #7 smbd(create_volume_objectid+0x27) [0x7fcea53348c7]
   #8 smbd(+0x126ede) [0x7fcea5316ede]
   #9 smbd(reply_nttrans+0x75f) [0x7fcea531946f]
   #10 smbd(+0x177224) [0x7fcea5367224]
   #11 smbd(+0x17763b) [0x7fcea536763b]
   #12 smbd(+0x177a53) [0x7fcea5367a53]
   #13 smbd(run_events_poll+0x34e) [0x7fcea5618bfe]
   #14 smbd(smbd_process+0x812) [0x7fcea53691c2]
   #15 smbd(+0x686b8f) [0x7fcea5876b8f]
   #16 smbd(run_events_poll+0x34e) [0x7fcea5618bfe]
   #17 smbd(+0x428d9a) [0x7fcea5618d9a]
   #18 smbd(_tevent_loop_once+0x90) [0x7fcea5619920]
   #19 smbd(main+0xed0) [0x7fcea52e7090]
   #20 /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed) [0x7fcea219376d]
   #21 smbd(+0xf7575) [0x7fcea52e7575]
[2014/02/01 21:14:47.562972,  0] lib/util.c:1122(smb_panic)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 4179]
[2014/02/01 21:14:47.585240,  0] lib/util.c:1130(smb_panic)
  smb_panic(): action returned status 0
[2014/02/01 21:14:47.585348,  0] lib/fault.c:372(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2014/02/01 21:14:47.974661,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:14:47.976093,  0] lib/fault.c:47(fault_report)
  ===============================================================
[2014/02/01 21:14:47.976140,  0] lib/fault.c:48(fault_report)
  INTERNAL ERROR: Signal 11 in pid 4190 (3.6.3)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2014/02/01 21:14:47.976187,  0] lib/fault.c:50(fault_report)
  
  From: http://www.samba.org/samba/docs/Samba3-HOWTO.pdf
[2014/02/01 21:14:47.976241,  0] lib/fault.c:51(fault_report)
  ===============================================================
[2014/02/01 21:14:47.976274,  0] lib/util.c:1117(smb_panic)
  PANIC (pid 4190): internal error
[2014/02/01 21:14:47.979898,  0] lib/util.c:1221(log_stack_trace)
  BACKTRACE: 22 stack frames:
   #0 smbd(log_stack_trace+0x1a) [0x7fcea5608e3a]
   #1 smbd(smb_panic+0x25) [0x7fcea5608f15]
   #2 smbd(+0x40a1d8) [0x7fcea55fa1d8]
   #3 /lib/x86_64-linux-gnu/libc.so.6(+0x364a0) [0x7fcea21a84a0]
   #4 /lib/x86_64-linux-gnu/libc.so.6(+0x89111) [0x7fcea21fb111]
   #5 smbd(push_ucs2_talloc+0x2c) [0x7fcea55f7dec]
   #6 smbd(E_md4hash+0x1e) [0x7fcea53d3b8e]
   #7 smbd(create_volume_objectid+0x27) [0x7fcea53348c7]
   #8 smbd(+0x126ede) [0x7fcea5316ede]
   #9 smbd(reply_nttrans+0x75f) [0x7fcea531946f]
   #10 smbd(+0x177224) [0x7fcea5367224]
   #11 smbd(+0x17763b) [0x7fcea536763b]
   #12 smbd(+0x177a53) [0x7fcea5367a53]
   #13 smbd(run_events_poll+0x34e) [0x7fcea5618bfe]
   #14 smbd(smbd_process+0x812) [0x7fcea53691c2]
   #15 smbd(+0x686b8f) [0x7fcea5876b8f]
   #16 smbd(run_events_poll+0x34e) [0x7fcea5618bfe]
   #17 smbd(+0x428d9a) [0x7fcea5618d9a]
   #18 smbd(_tevent_loop_once+0x90) [0x7fcea5619920]
   #19 smbd(main+0xed0) [0x7fcea52e7090]
   #20 /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed) [0x7fcea219376d]
   #21 smbd(+0xf7575) [0x7fcea52e7575]
[2014/02/01 21:14:47.980264,  0] lib/util.c:1122(smb_panic)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 4190]
[2014/02/01 21:14:47.982458,  0] lib/util.c:1130(smb_panic)
  smb_panic(): action returned status 0
[2014/02/01 21:14:47.982547,  0] lib/fault.c:372(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2014/02/01 21:14:48.357905,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:16:22.551297,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:16:22.858333,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:20:20.109476,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:20:20.375133,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:20:20.657397,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 21:20:20.939556,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 22:03:42.622034,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 22:03:42.722786,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 22:03:43.005460,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 22:03:43.007462,  0] lib/fault.c:47(fault_report)
  ===============================================================
[2014/02/01 22:03:43.007530,  0] lib/fault.c:48(fault_report)
  INTERNAL ERROR: Signal 11 in pid 4194 (3.6.3)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2014/02/01 22:03:43.007580,  0] lib/fault.c:50(fault_report)
  
  From: http://www.samba.org/samba/docs/Samba3-HOWTO.pdf
[2014/02/01 22:03:43.007627,  0] lib/fault.c:51(fault_report)
  ===============================================================
[2014/02/01 22:03:43.007670,  0] lib/util.c:1117(smb_panic)
  PANIC (pid 4194): internal error
[2014/02/01 22:03:43.011324,  0] lib/util.c:1221(log_stack_trace)
  BACKTRACE: 22 stack frames:
   #0 smbd(log_stack_trace+0x1a) [0x7fcea5608e3a]
   #1 smbd(smb_panic+0x25) [0x7fcea5608f15]
   #2 smbd(+0x40a1d8) [0x7fcea55fa1d8]
   #3 /lib/x86_64-linux-gnu/libc.so.6(+0x364a0) [0x7fcea21a84a0]
   #4 /lib/x86_64-linux-gnu/libc.so.6(+0x89111) [0x7fcea21fb111]
   #5 smbd(push_ucs2_talloc+0x2c) [0x7fcea55f7dec]
   #6 smbd(E_md4hash+0x1e) [0x7fcea53d3b8e]
   #7 smbd(create_volume_objectid+0x27) [0x7fcea53348c7]
   #8 smbd(+0x126ede) [0x7fcea5316ede]
   #9 smbd(reply_nttrans+0x75f) [0x7fcea531946f]
   #10 smbd(+0x177224) [0x7fcea5367224]
   #11 smbd(+0x17763b) [0x7fcea536763b]
   #12 smbd(+0x177a53) [0x7fcea5367a53]
   #13 smbd(run_events_poll+0x34e) [0x7fcea5618bfe]
   #14 smbd(smbd_process+0x812) [0x7fcea53691c2]
   #15 smbd(+0x686b8f) [0x7fcea5876b8f]
   #16 smbd(run_events_poll+0x34e) [0x7fcea5618bfe]
   #17 smbd(+0x428d9a) [0x7fcea5618d9a]
   #18 smbd(_tevent_loop_once+0x90) [0x7fcea5619920]
   #19 smbd(main+0xed0) [0x7fcea52e7090]
   #20 /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed) [0x7fcea219376d]
   #21 smbd(+0xf7575) [0x7fcea52e7575]
[2014/02/01 22:03:43.011696,  0] lib/util.c:1122(smb_panic)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 4194]
[2014/02/01 22:03:43.013832,  0] lib/util.c:1130(smb_panic)
  smb_panic(): action returned status 0
[2014/02/01 22:03:43.013916,  0] lib/fault.c:372(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2014/02/01 22:03:43.362171,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 22:03:43.644457,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 22:03:43.926662,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 22:03:51.328978,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 22:03:51.602872,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/01 22:03:51.619081,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
``` 

I have checked the permissions for /var/lib/samba/usershares/public and set them to 0777 as well as setting the group to sambashare.

Aside from that though, I'm not really sure how to make heads or tails of the panics of faults. Can anyone suggest how I can identify why the connection is being dropped?

It's since failed again. I've checked syslog and all it has is:

```
server CRON[7530]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

And this is the new messages in /var/log/samba/log.computer:

```
[2014/02/02 22:16:57.032921,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/02 22:16:57.033787,  0] param/loadparm.c:8851(check_usershare_stat)
  check_usershare_stat: file /var/lib/samba/usershares/public owned by uid 1000 allows public write. Refusing to allow as a usershare file.
[2014/02/02 22:16:57.035896,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/02 22:16:57.036301,  0] param/loadparm.c:8851(check_usershare_stat)
  check_usershare_stat: file /var/lib/samba/usershares/public owned by uid 1000 allows public write. Refusing to allow as a usershare file.
[2014/02/02 22:17:01.300845,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/02 22:17:01.301371,  0] param/loadparm.c:8851(check_usershare_stat)
  check_usershare_stat: file /var/lib/samba/usershares/public owned by uid 1000 allows public write. Refusing to allow as a usershare file.
[2014/02/02 22:17:01.301916,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/02 22:17:01.302730,  0] param/loadparm.c:8851(check_usershare_stat)
  check_usershare_stat: file /var/lib/samba/usershares/public owned by uid 1000 allows public write. Refusing to allow as a usershare file.
[2014/02/02 22:17:04.044023,  0] param/loadparm.c:8851(check_usershare_stat)
  check_usershare_stat: file /var/lib/samba/usershares/public owned by uid 1000 allows public write. Refusing to allow as a usershare file.
[2014/02/02 22:17:31.503960,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/02 22:17:31.505984,  0] param/loadparm.c:8851(check_usershare_stat)
  check_usershare_stat: file /var/lib/samba/usershares/public owned by uid 1000 allows public write. Refusing to allow as a usershare file.
[2014/02/02 22:17:31.507194,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/02 22:17:31.508826,  0] param/loadparm.c:8851(check_usershare_stat)
  check_usershare_stat: file /var/lib/samba/usershares/public owned by uid 1000 allows public write. Refusing to allow as a usershare file.
[2014/02/02 22:17:31.512712,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/02 22:17:31.525231,  0] param/loadparm.c:8851(check_usershare_stat)
  check_usershare_stat: file /var/lib/samba/usershares/public owned by uid 1000 allows public write. Refusing to allow as a usershare file.
[2014/02/02 22:17:31.525877,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/public failed. Permission denied
[2014/02/02 22:17:31.545697,  0] param/loadparm.c:8851(check_usershare_stat)
  check_usershare_stat: file /var/lib/samba/usershares/public owned by uid 1000 allows public write. Refusing to allow as a usershare file.
```

---

