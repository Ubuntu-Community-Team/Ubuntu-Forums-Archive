---
title: "Ubuntu 20.04 samba nightmare"
date: 2020-10-05
forum: Networking &amp; Wireless
---

### Post by kato1144 on 2020-10-05
Im some what new to linux so maybe im missing some obvious detail but i have been trying to get samba to work between my plex server running ubuntu 20.04 and my file server also running ubuntu 20.04, i first used the GUI folder options to share my folder, it installed samba, then i added a used on the PC for access but that did not work, i tried some edits on the smb.conf file that was recommended after doing some searching, sadly this just broke the samba service so i had to purge and reinstall this time in console. turning on gust access would get me further then he password and user name menu but i would instead get a permission denied window...

Latter one after much googling I found the "sudo smbpasswd -a username" and used that with a username and password matching the account i made on the plex server for connecting to it, same username and password on my file server as well(just mentioning this detail incase it part of my problem), it seemed to kinda work before using my username and pass would just cause the password windows to keep popping up but now i got the "Failed to mount Windows share: Permissions denied" window now.... so progress i guess 

anyway after not making much progress i look for the log files, find the files and they make no sense to me so I came here for help.
log.

```

[2020/10/04 17:34:54.099129,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 17:34:54.101607,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 17:34:54.101906,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 17:34:54.102453,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 17:34:54.102853,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 17:34:54.102973,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 17:35:11.430502,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 17:35:11.431700,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 17:35:11.431852,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 17:35:11.431981,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 17:35:11.432258,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 17:35:11.432356,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 17:36:12.519269,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 17:36:12.520564,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 17:36:12.520699,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 17:36:12.520795,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 17:36:12.521026,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 17:36:12.521117,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:32:54.149007,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 18:32:54.150152,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:32:54.150306,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:32:54.150406,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:32:54.150682,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:32:54.150782,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:46:50.232627,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 18:46:59.306603,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 18:47:00.649273,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:03:45.889441,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:03:46.988086,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:03:47.537829,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:03:47.851010,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:03:48.261441,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:03:48.680095,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:03:49.081320,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:03:49.466797,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:09:19.053156,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:27.214807,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:28.407371,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:28.942106,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:29.545793,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:30.026334,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:30.423931,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:30.664640,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:31.016508,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:31.371107,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:31.729004,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:32.107449,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:32.463180,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:32.848026,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:33.228375,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:33.618160,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:33.998521,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:34.384532,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:34.777505,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:35.159904,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:35.568696,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:35.965929,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:36.344800,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:36.764478,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:37.160375,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:37.586053,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:37.998956,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:38.421708,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:38.830550,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:39.232380,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:39.629104,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:39.826224,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:40.275151,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:40.678347,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:41.077539,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:41.494802,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:41.931207,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:42.534477,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:36:45.805481,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 20:40:08.232823,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 22:10:54.184161,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/local failed. Permission denied
[2020/10/04 22:10:54.189997,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:10:54.190162,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:10:54.190273,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:10:54.190575,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:10:54.190673,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:12:07.969909,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 22:21:19.624954,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:21:20.542962,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:21:20.978176,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:21:21.830259,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:21:23.630801,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:21:24.102730,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:21:24.505567,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:21:24.903185,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:21:25.287738,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:21:25.683147,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:21:26.021772,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:21:26.382869,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:21:26.793099,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:21:27.138880,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:21:27.318851,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:21:27.619573,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:21:27.935841,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:21:28.305437,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:21:28.651234,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:21:29.015140,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:21:59.318340,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:21:59.319560,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:21:59.319731,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:21:59.319835,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:21:59.320135,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:21:59.320234,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:22:16.542145,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:22:24.518582,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:22:24.519768,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:22:24.519916,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:22:24.520015,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:22:24.520269,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:22:24.520366,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:22:30.695254,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:22:30.697803,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:22:30.698827,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:22:30.698958,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:22:30.699237,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:22:30.699336,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!

```


log.torr

```

[2020/10/04 17:34:38.921482,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 17:35:39.829847,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 17:35:39.832067,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 17:35:39.832279,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 17:35:39.832381,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 17:36:08.599332,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 17:36:08.599612,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 17:37:04.328769,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 17:37:04.330181,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 17:37:04.330391,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 17:37:04.330537,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:26:31.654101,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 18:26:31.655237,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:26:31.655381,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:26:31.655495,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:26:31.655743,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:26:31.655831,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:27:08.780679,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 18:27:08.782249,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:27:08.782432,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:27:08.782550,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:27:18.086916,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 18:27:18.088327,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:27:18.088502,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:27:18.088612,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:27:18.088958,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:27:18.089063,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:32:45.309402,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 18:32:45.310708,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:32:45.310848,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:32:45.310949,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:32:45.311194,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:32:45.311290,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:42:30.588313,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 18:42:30.589813,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:42:30.590049,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:42:30.590149,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:42:30.590449,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:42:30.590581,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:43:10.296830,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 18:43:10.298143,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:43:10.298293,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:43:10.298390,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:43:10.298652,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:43:10.298744,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 18:46:34.883912,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 18:46:41.909637,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 18:47:21.145517,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:03:43.410122,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 19:34:11.399030,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 22:11:01.482590,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/local failed. Permission denied
[2020/10/04 22:11:01.486974,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:11:01.487200,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:11:01.487317,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:11:01.487624,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:11:01.487737,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:11:10.082495,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/plex-folder failed. Permission denied
[2020/10/04 22:15:16.679491,  0] ../../source3/lib/sharesec.c:427(delete_share_security)
  delete_share_security: Failed to delete entry for share plex-folder: NT_STATUS_NOT_FOUND
[2020/10/04 22:21:16.345764,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:28:06.043652,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:28:06.045627,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:28:06.045827,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:28:06.046451,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:28:06.047707,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:28:06.047839,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:28:35.401107,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:28:35.403034,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:28:35.403246,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:28:35.403376,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:28:35.403706,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:28:35.403836,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:54:56.895587,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 22:54:56.896686,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:54:56.896851,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:54:56.896962,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:54:56.897267,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 22:54:56.897377,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 23:07:34.830524,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 23:07:34.831966,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 23:07:34.832137,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 23:07:34.832242,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 23:07:34.832527,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 23:07:34.832690,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 23:35:11.069378,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 23:35:19.952041,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 23:36:56.197920,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 23:36:56.200051,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 23:36:56.200240,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 23:36:56.200361,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 23:36:56.200655,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 23:36:56.200759,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 23:52:42.437580,  0] ../../source3/param/loadparm.c:3362(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permission denied
[2020/10/04 23:52:42.438831,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 23:52:42.438994,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 23:52:42.439094,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 23:52:42.439368,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!
[2020/10/04 23:52:42.439470,  0] ../../source3/smbd/uid.c:448(change_to_user_internal)
  change_to_user_internal: chdir_current_service() failed!

```

log.smbd

```

[2020/10/04 15:13:51.720469,  0] ../../source3/smbd/server.c:1775(main)
  smbd version 4.11.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2019
[2020/10/04 15:13:51.912817,  0] ../../lib/util/become_daemon.c:135(daemon_ready)
  daemon_ready: daemon 'smbd' finished starting up and ready to serve connections
[2020/10/04 19:26:09.057141,  0] ../../source3/smbd/server.c:1775(main)
  smbd version 4.11.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2019
[2020/10/04 19:26:09.074746,  0] ../../lib/util/become_daemon.c:135(daemon_ready)
  daemon_ready: daemon 'smbd' finished starting up and ready to serve connections
[2020/10/04 19:26:56.217780,  0] ../../source3/smbd/server.c:1775(main)
  smbd version 4.11.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2019
[2020/10/04 19:26:56.231475,  0] ../../lib/util/become_daemon.c:135(daemon_ready)
  daemon_ready: daemon 'smbd' finished starting up and ready to serve connections
[2020/10/04 19:31:05.446496,  0] ../../source3/smbd/server.c:1775(main)
  smbd version 4.11.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2019
[2020/10/04 19:31:05.460032,  0] ../../lib/util/become_daemon.c:135(daemon_ready)
  daemon_ready: daemon 'smbd' finished starting up and ready to serve connections
[2020/10/04 19:33:14.912715,  0] ../../source3/smbd/server.c:1775(main)
  smbd version 4.11.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2019
[2020/10/04 19:33:14.926468,  0] ../../lib/util/become_daemon.c:135(daemon_ready)
  daemon_ready: daemon 'smbd' finished starting up and ready to serve connections
[2020/10/04 22:05:01.568645,  0] ../../source3/smbd/server.c:1775(main)
  smbd version 4.11.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2019
[2020/10/04 22:05:01.654623,  0] ../../lib/util/become_daemon.c:135(daemon_ready)
  daemon_ready: daemon 'smbd' finished starting up and ready to serve connections
[2020/10/04 22:54:07.051391,  0] ../../source3/smbd/server.c:1775(main)
  smbd version 4.11.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2019
[2020/10/04 22:54:07.074353,  0] ../../lib/util/become_daemon.c:135(daemon_ready)
  daemon_ready: daemon 'smbd' finished starting up and ready to serve connections

```

I have spent most of my day on this problem and i have no idea how to get this system to work, it seems easy and straight forward on the surface but this has been a nightmare so far, you think it would jsut work beding that im not even going to a diffrent OS it all the same verson of ubuntu.... anyway let me know if anyone can figure out why this wont work, what im doing wrong or if there is a better/ more preferable way of moving files over my home network. thanks

---

### Post by QIII on 2020-10-05
Please use code tags for terminal commands and results:

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by ajgreeny on 2020-10-05
I have never needed or used samba nor nfs but many Linux users find nfs much easier to use in a Linux only situation.

---

### Post by Morbius1 on 2020-10-05
If you want to pursue a samba solution we need to know how these shares are set up. Please post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by kato1144 on 2020-10-05
@  [**[COLOR=#990303][B]QIII**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=628170"), I knew the way I was doing it was wrong for posting the code and was not sure the correct way to post so thanks now I wont be taking up 60% of the page with repeating non sense :P

@ [**[COLOR=#C61919][B]ajgreeny**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=27747"), if all else fails I will look in nfs, i would like to use samba just for compatibility with windows OS down the road but if f comes down to it I only really need this to be a linux to linux connection 

@ [**[COLOR=#000000]Morbius1[/COLOR]**]("https://ubuntuforums.org/member.php?u=982144"), 

testparm -s

```
 
Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]
    log file = /var/log/samba/log.%m
    logging = file
    map to guest = Bad User
    max log size = 1000
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    unix password sync = Yes
    usershare allow guests = Yes
    idmap config * : backend = tdb


[printers]
    browseable = No
    comment = All Printers
    create mask = 0700
    path = /var/spool/samba
    printable = Yes

```

net usershare info --long

```


[media]
path=/media/plex/790c32a9-a918-470c-8e1f-6d76c4d66f60/media
comment=
usershare_acl=Everyone:F,
guest_ok=n


```

hopefully this will help shed some light on my situation, i really appreciate the help.

BTW is this normal to have so much issue with samba or is this just a symptom of my inexperience and should i be reading and learning stuff to better prepare my self for the world of linux, i have been a windows user my whole life, i do enjoy linux but i feel like i came to this os very unprepaird  being this is not the only thing i have struggled with, I am learning but the curve is steep.

---

### Post by Morbius1 on 2020-10-05
Do you plan on using this server for any other file sharing other than Plex?

If not edit /etc/samba/smb.conf and right under the workgroup = WORKGROUP line add this one:
```
force user = plex
```
THen restart smbd:
```
sudo service smbd restart
```

None of this has anything to do with samba. It has to do with Linux permissions. We are using samba however to fix the problem that the only user that can access the /media/plex/790c32a9-a918-470c-8e1f-6d76c4d66f60 mount point from the network is plex.

---

### Post by rsteinmetz70112 on 2020-10-05
Are smbd and nmbd running on your server?
What is the status of the smbd.service on the server?
```
sudo systemctl status smbd
```

Do you have a windows computer you can check to see if the shares are available?

Do you have smbclient on you client?

---

### Post by kato1144 on 2020-10-05
sudo systemctl status smbd```

&#9679; smbd.service - Samba SMB Daemon
     Loaded: loaded (/lib/systemd/system/smbd.service; enabled; vendor preset: enabled)
     Active: active (running) since Sun 2020-10-04 22:54:07 MDT; 16h ago
       Docs: man:smbd(8)
             man:samba(7)
             man:smb.conf(5)
   Main PID: 5674 (smbd)
     Status: "smbd: ready to serve connections..."
      Tasks: 4 (limit: 17846)
     Memory: 9.6M
     CGroup: /system.slice/smbd.service
             &#9500;&#9472;5674 /usr/sbin/smbd --foreground --no-process-group
             &#9500;&#9472;5676 /usr/sbin/smbd --foreground --no-process-group
             &#9500;&#9472;5677 /usr/sbin/smbd --foreground --no-process-group
             &#9492;&#9472;5678 /usr/sbin/smbd --foreground --no-process-group

Oct 04 23:35:19 Aspire smbd[7337]: pam_unix(samba:session): session closed for user nobody
Oct 04 23:36:56 Aspire smbd[7424]: pam_unix(samba:session): session opened for user torr by (uid=0)
Oct 04 23:36:57 Aspire smbd[7424]: pam_unix(samba:session): session closed for user torr
Oct 04 23:39:40 Aspire smbd[7438]: pam_unix(samba:session): session closed for user nobody
Oct 04 23:39:54 Aspire smbd[7449]: pam_unix(samba:session): session closed for user nobody
Oct 04 23:52:42 Aspire smbd[7480]: pam_unix(samba:session): session opened for user torr by (uid=0)
Oct 04 23:52:43 Aspire smbd[7480]: pam_unix(samba:session): session closed for user torr
Oct 04 23:56:55 Aspire smbd[7492]: pam_unix(samba:session): session closed for user nobody
Oct 05 02:04:02 Aspire smbd[6749]: pam_unix(samba:session): session closed for user nobody
Oct 05 08:55:56 Aspire smbd[10219]: pam_unix(samba:session): session closed for user nobody

```

Looked at the network on my windows PC and there is nothing from my linux machines besides the media sharing i enabled as a last ditch effort, the samba folder is not there

is smbclient something i have to install separately?

---

### Post by kato1144 on 2020-10-05
[**[COLOR=#000000]Morbius1[/COLOR]**]("https://ubuntuforums.org/member.php?u=982144") i got around to trying the "force user = "command and it is working now. this it a good work around for the mean time, if anyone wants to keep pluging away with me to get full functionality out of my smaba your welcome to keep helping but this is now doing the bar minimal i need so i can have functionality with this system now

---

### Post by TheFu on 2020-10-05
What file system does /media/plex/790c32a9-a918-470c-8e1f-6d76c4d66f60 have?  When it is mounted, **df -Th** should show the file system. Using NTFS will eventually lead to permissions problems that cannot be solved.

---

### Post by kato1144 on 2020-10-05
[**[COLOR=#000000]TheFu[/COLOR]**]("https://ubuntuforums.org/member.php?u=1037685"), the file system on /media/plex/790c32a9-a918-470c-8e1f-6d76c4d66f60 is ext4

also im having a new issue, every time i reboot or power down the plex server i lose the samba access to my folder and have to re initiate manually, its a minor pain in the ass but not game breaking, if some one could show me how to permanently share my folder i would appreciate it

---

### Post by TheFu on 2020-10-05
I've never setup samba shares through a GUI, like it appears you have. Sorry, I cannot help with that.
All my samba shares are configured in the /etc/samba/smb.conf file.

Using ext4 is helpful.  If plex runs on the same computer, then you don't need Samba for plex to have access.

---

### Post by kato1144 on 2020-10-05
[**[COLOR=#000000]TheFu[/COLOR]**]("https://ubuntuforums.org/member.php?u=1037685"), if you dont mind telling me how you setup samba with the smb.conf file, the GUI is letting me down hard

---

### Post by Morbius1 on 2020-10-06
> **kato1144 said:**
> [**[COLOR=#000000]Morbius1[/COLOR]**]("https://ubuntuforums.org/member.php?u=982144") i got around to trying the "force user = "command and it is working now. 
Great.
> ... this it a good work around for the mean time
Given the location of your mount point it is not a workaround. Unless you change your mount point or log into the share as the user "plex" it is the only way the client can access your share.
> ... if anyone wants to keep pluging away with me to get full functionality out of my smaba your welcome to keep helping but this is now doing the bar minimal i need so i can have functionality with this system now
I don't know what that means. What functionality are you missing?
> ... every time i reboot or power down the plex server i lose the samba access to my folder and have to re initiate manually, 
Re initiate what? The samba server? Redo the share?

This is just a hunch but what is the output of this command:
```
cat /etc/fstab | grep plex
```

---

### Post by kato1144 on 2020-10-06
[**[COLOR=#000000]Morbius1[/COLOR]**]("https://ubuntuforums.org/member.php?u=982144"), i tried the command "cat /etc/fstab | grep plex" and there was no output, i did not even get an error, i even sudo the command it just to be sure but nothing. Also what i ment by redoing the samba accesses i had to manually initiate the share on the folder, im doing it thru the GUI so maybe i need to do it in command to make it permanent

EDIT: i forgot to mention the function im missing is windows is still unable to see the share folder, it would be nice if i could get that to work too but that is something that is a want not a need

---

### Post by Morbius1 on 2020-10-06
> i tried the command "cat /etc/fstab | grep plex" and there was no  output, i did not even get an error, i even sudo the command it just to  be sure but nothing.
That means your partition is not being mounted at boot.
> Also what i ment by redoing the samba accesses i had to manually  initiate the share on the folder, im doing it thru the GUI so maybe i  need to do it in command to make it permanent
Because your partition is not being mounted at boot. The share definition is pointing to a mount point that does not exist yet.

If you post the output of the following command I'm sure someone here can help you set this up in fstab so that it will be more permanent:
```
sudo blkid -c /dev/null
```

---

### Post by TheFu on 2020-10-06
Good catch Morbius1!
I'd bet the UUID is: 790c32a9-a918-470c-8e1f-6d76c4d66f60 based on the automatic mounting.

Use **sudoedit /etc/fstab** to edit the file. Add this line to the bottom:
```
UUID=790c32a9-a918-470c-8e1f-6d76c4d66f60 /media/plex/790c32a9-a918-470c-8e1f-6d76c4d66f60 ext4   errors=remount-ro,nodev,nosuid 0 1
```

If it was me, I'd change the mount location to /media/plex1, so when the time comes to add more storage, you can add it as  /media/plex2 and  /media/plex3 and  /media/plex4 ....  but doing this will mean modifying the Plex database through the webgui for the different library locations.  

If you are interested, we can trick plex into the new storage by having a symbolic link, adding the new library locations, having plex see all the media twice (let it scan everything), then remove the old /media/plex/790c32a9-a918-470c-8e1f-6d76c4d66f60 location from the libraries and remove the symlink.  Then Plex would see only 1 of each media object and life will be good again.  Plex **must** see 2 copies of everything in the plex DB before removing the old, ugly, mount location which was automatically created.

The cost of not knowing stuff.

---

### Post by rsteinmetz70112 on 2020-10-06
> **kato1144 said:**
> [**[COLOR=#000000]Morbius1[/COLOR]**]("https://ubuntuforums.org/member.php?u=982144")  if anyone wants to keep pluging away with me to get full functionality out of my samba you're welcome to keep helping but this is now doing the bare minimal i need so i can have functionality with this system now

What functionality are your missing?

---

### Post by kato1144 on 2020-10-06
[**[COLOR=#000000]Morbius1, [/COLOR]**]("https://ubuntuforums.org/member.php?u=982144")
```

[sudo] password for plex: 
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: UUID="790c32a9-a918-470c-8e1f-6d76c4d66f60" TYPE="ext4" PARTUUID="c277c2c5-6db9-4bf0-ba7f-a4939e975432"
/dev/sdb1: UUID="A0D8-088C" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="a345b8b3-08ce-4692-b29f-d50436ffceb7"
/dev/sdb2: UUID="d3f35356-559c-488c-bcae-f030ed2b5acc" TYPE="ext4" PARTUUID="67d15dd5-f532-4571-a42b-6a945e40d096"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"

```

---

### Post by kato1144 on 2020-10-06
[**[COLOR=#000000]TheFu[/COLOR]**]("https://ubuntuforums.org/member.php?u=1037685"), turned this ```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb2 during installation
UUID=d3f35356-559c-488c-bcae-f030ed2b5acc /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb1 during installation
UUID=A0D8-088C  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

```

to this
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb2 during installation
UUID=d3f35356-559c-488c-bcae-f030ed2b5acc /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb1 during installation
UUID=A0D8-088C  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
UUID=790c32a9-a918-470c-8e1f-6d76c4d66f60 /media/plex/790c32a9-a918-470c-8e1f-6d76c4d66f60 ext4   errors=remoun>


```

EDIT: i rebooted remotely and she is working :)

as for adding additional media, that not going to be really necessary as this drive is 4TB and i wont be filling that for along long time, if i do need to add more down the road i will look in to having a crack at changing the drive naming scheme, for now its working better then before and im happy wit that

---

### Post by kato1144 on 2020-10-06
[**[COLOR=#000000]rsteinmetz70112[/COLOR]**]("https://ubuntuforums.org/member.php?u=252572"), the samba shared folder is not showing up on my windows machines but that might be a windows 10 issue, not really concerned with that right now

---

### Post by TheFu on 2020-10-06
I hope you got the complete line into the fstab. If not, problems can happen.
```
......     ext4   errors=remount-ro,nodev,nosuid 0 1
```
It all needs to be on 1 line, the same line.  May need to run
```
sudo systemctl daemon-reload
```
after any changes to the fstab so those get picked up.  I'm a little fuzzy as to when that is needed since systemd took over the fstab stuff recently.

---

### Post by kato1144 on 2020-10-16
[**[COLOR=#000000]TheFu[/COLOR]**]("https://ubuntuforums.org/member.php?u=1037685") oh ya[[COLOR=#000000][/COLOR]]("https://ubuntuforums.org/member.php?u=1037685") it just did not show the full code for some reasion when i copy and pasted it "ext4   errors=remount-ro,nodev,nosuid 0 1" is there in full

---

### Post by kato1144 on 2020-10-16
just one more question since were on the topic of mounting drives, my file server has 4 drives one is the boot and the other 3 are mass storage, and everytime i reboot it messes up my virtual box share folders on my VM that im using, and i have to remount the folders manually, anyway i just want to make sure that i can fstab them to mount on boot too, the GUI seems a bit inept with its auto mount feature
```

/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: UUID="2f0f8f8e-b2b5-49b8-bd5a-7c29e936a120" TYPE="ext4" PARTLABEL="TB4" PARTUUID="641c3e43-f263-4115-a010-59eee6a56d13"
/dev/sdb1: UUID="6eb53bfe-1551-490a-b62b-d8594d90a173" TYPE="ext4" PARTLABEL="TB3" PARTUUID="b666338e-ba99-4587-95bd-8393171820f4"
/dev/sdc1: UUID="9dbfb4e0-c1ff-4016-b1c3-d0f7ff56aa17" TYPE="ext4" PARTLABEL="TB8" PARTUUID="3e99c995-982d-420c-a946-aaf7a0bdc47b"
/dev/sdd1: UUID="608C-F300" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="e4035d7e-7673-44ae-b0c0-cc61935f1acd"
/dev/sdd2: UUID="3812d9cf-0377-45d8-a41d-15586edee4f5" TYPE="ext4" PARTUUID="9986e55c-7e4f-4ab9-8975-6a4afd655f27"
/dev/loop8: TYPE="squashfs"


```

is there a way to do this in the GUI or is fstab editing the best way, i just intimidates me alittle, for i feel a mistake while editing the fstab can lead to major issues

---

