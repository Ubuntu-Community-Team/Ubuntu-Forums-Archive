---
title: "Log error"
date: 2015-07-16
forum: Networking &amp; Wireless
---

### Post by Dii_Reno on 2015-07-16
My samba has been working fine for a few years now. About three weeks ago we started noticing that several times a day users around my office would start to have trouble logging into their share drives. When this is happening the ping rate goes erratic. When I powercycle my switch the problem resolves for up to a few days, and then starts to repeat again. 

I believe it's being caused by these commands being run, but I don't know what would cause these commands to be run in the first place. When I reboot the server I have no change, but when I power-cycle the switch the problem clears up for a bit. I think when the switch is powercycled it resolves the network connection and resets the interfaces. 

I believe these processes are being run over and over again and then being throttled when it can't complete. The throttling causing disconnects with my office. 

I just need to figure out what are causing the server to look in /var/lib/samba/usershares/.. for files. I have not stored anything in this directory and do not know what would cause this. 

```
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/matt.lnk failed. Permission denied
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.113103,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/matt.lnk failed. No such file or directory
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.113691,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/matt.lnk failed. No such file or directory
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.114473,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/matt.dll failed. Permission denied
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.115129,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/matt.dll failed. No such file or directory
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.115692,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/matt.dll failed. No such file or directory
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.117447,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/mat failed. Permission denied
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.118080,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/mat failed. No such file or directory
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.118650,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/mat failed. No such file or directory
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.120428,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/mat failed. Permission denied
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.121072,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/mat failed. No such file or directory
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.121614,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/mat failed. No such file or directory
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.123358,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/mat failed. Permission denied
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.123983,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/mat failed. No such file or directory
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.124521,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/mat failed. No such file or directory
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.126264,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/mat failed. Permission denied
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.126886,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/mat failed. No such file or directory
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.127450,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/mat failed. No such file or directory
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.128175,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/matt.bat failed. Permission denied
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.128994,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/matt.bat failed. No such file or directory
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.129633,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/matt.bat failed. No such file or directory
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.130733,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/matt.cmd failed. Permission denied
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.131557,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/matt.cmd failed. No such file or directory
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.132182,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/matt.cmd failed. No such file or directory
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.133311,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/matt.exe failed. Permission denied
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.134112,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/matt.exe failed. No such file or directory
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.135835,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/matt.com failed. Permission denied
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.136627,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/matt.com failed. No such file or directory
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.137270,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/matt.com failed. No such file or directory
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.138399,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/matt.pif failed. Permission denied
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.139226,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/matt.pif failed. No such file or directory
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.139834,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/matt.pif failed. No such file or directory
Jul 16 11:19:08 Server smbd[495]: [2015/07/16 11:19:08.140936,  0] param/loadparm.c:9114(process_usershare_file)
Jul 16 11:19:08 Server smbd[495]:   process_usershare_file: stat of /var/lib/samba/usershares/matt.lnk failed. Permission denied
Jul 16 11:19:08 Server rsyslogd-2177: imuxsock begins to drop messages from pid 495 due to rate-limiting
Jul 16 11:25:43 Server nmbd[833]: [2015/07/16 11:25:43.487511,  0] nmbd/nmbd_browsesync.c:351(find_domain_master_name_query_fail)
Jul 16 11:25:43 Server nmbd[833]:   find_domain_master_name_query_fail:
Jul 16 11:25:43 Server nmbd[833]:   Unable to find the Domain Master Browser name Server<1b> for the workgroup Server.
Jul 16 11:25:43 Server nmbd[833]:   Unable to sync browse lists in this workgroup.
Jul 16 11:40:42 Server nmbd[833]: [2015/07/16 11:40:42.472091,  0] nmbd/nmbd_browsesync.c:351(find_domain_master_name_query_fail)
Jul 16 11:40:42 Server nmbd[833]:   find_domain_master_name_query_fail:
Jul 16 11:40:42 Server nmbd[833]:   Unable to find the Domain Master Browser name Server<1b> for the workgroup Server.
Jul 16 11:40:42 Server nmbd[833]:   Unable to sync browse lists in this workgroup.
Jul 16 11:55:42 Server nmbd[833]: [2015/07/16 11:55:42.448560,  0] nmbd/nmbd_browsesync.c:351(find_domain_master_name_query_fail)
Jul 16 11:55:42 Server nmbd[833]:   find_domain_master_name_query_fail:
Jul 16 11:55:42 Server nmbd[833]:   Unable to find the Domain Master Browser name Server<1b> for the workgroup Server.
Jul 16 11:55:42 Server nmbd[833]:   Unable to sync browse lists in this workgroup.
Jul 16 12:10:41 Server nmbd[833]: [2015/07/16 12:10:41.655639,  0] nmbd/nmbd_browsesync.c:351(find_domain_master_name_query_fail)
Jul 16 12:10:41 Server nmbd[833]:   find_domain_master_name_query_fail:
Jul 16 12:10:41 Server nmbd[833]:   Unable to find the Domain Master Browser name Server<1b> for the workgroup Server.
Jul 16 12:10:41 Server nmbd[833]:   Unable to sync browse lists in this workgroup.
Jul 16 12:17:01 Server CRON[1042]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 16 12:25:42 Server nmbd[833]: [2015/07/16 12:25:42.411327,  0] nmbd/nmbd_browsesync.c:351(find_domain_master_name_query_fail)
Jul 16 12:25:42 Server nmbd[833]:   find_domain_master_name_query_fail:
Jul 16 12:25:42 Server nmbd[833]:   Unable to find the Domain Master Browser name Server<1b> for the workgroup Server.
Jul 16 12:25:42 Server nmbd[833]:   Unable to sync browse lists in this workgroup.
Jul 16 12:40:42 Server nmbd[833]: [2015/07/16 12:40:42.389612,  0] nmbd/nmbd_browsesync.c:351(find_domain_master_name_query_fail)
Jul 16 12:40:42 Server nmbd[833]:   find_domain_master_name_query_fail:
Jul 16 12:40:42 Server nmbd[833]:   Unable to find the Domain Master Browser name Server<1b> for the workgroup Server.
Jul 16 12:40:42 Server nmbd[833]:   Unable to sync browse lists in this workgroup.
Jul 16 12:55:43 Server nmbd[833]: [2015/07/16 12:55:43.362234,  0] nmbd/nmbd_browsesync.c:351(find_domain_master_name_query_fail)
Jul 16 12:55:43 Server nmbd[833]:   find_domain_master_name_query_fail:
Jul 16 12:55:43 Server nmbd[833]:   Unable to find the Domain Master Browser name Server<1b> for the workgroup Server.
Jul 16 12:55:43 Server nmbd[833]:   Unable to sync browse lists in this workgroup.
Jul 16 13:10:41 Server nmbd[833]: [2015/07/16 13:10:41.581938,  0] nmbd/nmbd_browsesync.c:351(find_domain_master_name_query_fail)
Jul 16 13:10:41 Server nmbd[833]:   find_domain_master_name_query_fail:
Jul 16 13:10:41 Server nmbd[833]:   Unable to find the Domain Master Browser name Server<1b> for the workgroup Server.
Jul 16 13:10:41 Server nmbd[833]:   Unable to sync browse lists in this workgroup.
Jul 16 13:17:01 Server CRON[1226]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 16 13:25:43 Server nmbd[833]: [2015/07/16 13:25:43.329843,  0] nmbd/nmbd_browsesync.c:351(find_domain_master_name_query_fail)
                                                                                                                                             

```

---

### Post by bielefeld33615 on 2016-04-14
Hi,

Knowing the question is old: I was experiencing the same issues lately,
and there are not many new answers to this problem, except for one:

It is most likely the client using Microsofts "Windows Defender", which
is correlated with these errors. The client will probably experience no
bad effects, the logfile spamming though is irritating... To verify this,
check the clients settings (Day, Time) for "Windows Defender" to run
and compare these with your logs: It was a hit in my case...

Modern MS Windows versions come with "Windows Defender" enabled,
see: [https://en.wikipedia.org/wiki/Windows_Defender](https://en.wikipedia.org/wiki/Windows_Defender)

Disabling "Windows Defender" is probably not a good option, so maybe
ignoring the logfile spam is best until the SAMBA people come up with
some decent solution...

Cheers,
Stefan

---

