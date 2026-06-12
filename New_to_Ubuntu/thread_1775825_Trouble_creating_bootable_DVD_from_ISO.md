---
title: "Trouble creating bootable DVD from ISO"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by harlanwolfe on 2011-06-05
Using Brasero, I'm burning the image to DVD. When I try to boot from the DVD, I just get a flashing cursor mark upper left corner, DVD spins, but no action.
Anyone?

---

### Post by TeoBigusGeekus on 2011-06-05
How did you download the iso? If it was through torrents then you should be fine (torrent clients check md5 sum automatically).
Try burning it again with minimum speed.

---

### Post by harlanwolfe on 2011-06-05
Thanks for the help. Downloaded , burning contents of image file at 4X, will update shortly.

---

### Post by TeoBigusGeekus on 2011-06-05
Waiting for the results.

---

### Post by harlanwolfe on 2011-06-05
Same results. I'm committed to Ubuntu, but need to reinstall Windows to run some Windows programs for work. Wine will install, but not execute thr running of the programs.

---

### Post by harlanwolfe on 2011-06-05
I have no trouble creating bootable CDs, but so far no luck with larger files on DVD.

---

### Post by TeoBigusGeekus on 2011-06-05
Open a terminal and do this
```
growisofs -dvd-compat -speed=4 -Z /dev/dvd=/path/image.iso
```
Replace /dev/dvd with whatever applicable (/dev/cd, /dev/sr0, /dev/scd0, etc.)

---

### Post by harlanwolfe on 2011-06-05
To be clear,should it be dev/cd instead of dev/dvd?

---

### Post by harlanwolfe on 2011-06-05
Before I run in terminal, what result am I looking for? What will this command accomplish?
Thanks again for your time!

---

### Post by harlanwolfe on 2011-06-05
I've been playing with this command, inserting different paths, etc. and I keep getting "no file or path found".
I'm not sure if this command is supposed to burn the dvd, or open it, or what.
Thanks again for your time & assistance.

---

### Post by TeoBigusGeekus on 2011-06-05
This command does burn the dvd, indeed.
Try
/dev/dvd
/dev/cd
/dev/sr0
/dev/scd0
/dev/cdrw

---

### Post by harlanwolfe on 2011-06-05
Pardon my newbiness, but do I need to edit anything else in the code (path, filename)?

---

### Post by TeoBigusGeekus on 2011-06-05
Yes, replace /path with the actual path of the image file and image.iso with the actual image name.

---

### Post by harlanwolfe on 2011-06-05
Seems to be burning fine, I'll let you know the outcome.
By using this command, Are we hoping for a more bootable DVD than was produced by Brasero, or CD?DVD Creator?

---

### Post by TeoBigusGeekus on 2011-06-05
Brasero and K3b have been known to go through cycles of brokenness throughout the years. I don't use them anymore. 
If this command fails, then I'm afraid you'll have to find another iso.

---

### Post by harlanwolfe on 2011-06-05
Here's the outcome, will try to boot now, will get back to you.

/dev/dvd: "Current Write Speed" is 4.1x1352KBps.
          0/3243413504 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/3243413504 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
     360448/3243413504 ( 0.0%) @0.1x, remaining 1949:24 RBU 100.0% UBU  76.7%
   17924096/3243413504 ( 0.6%) @3.8x, remaining 47:59 RBU 100.0% UBU  99.9%
   36405248/3243413504 ( 1.1%) @4.0x, remaining 27:53 RBU 100.0% UBU  99.9%
   54886400/3243413504 ( 1.7%) @4.0x, remaining 22:16 RBU 100.0% UBU  99.9%
   70352896/3243413504 ( 2.2%) @3.3x, remaining 19:32 RBU 100.0% UBU  99.9%
   88834048/3243413504 ( 2.7%) @4.0x, remaining 17:09 RBU 100.0% UBU  99.9%
  107315200/3243413504 ( 3.3%) @4.0x, remaining 16:04 RBU 100.0% UBU  95.6%
  125796352/3243413504 ( 3.9%) @4.0x, remaining 14:52 RBU 100.0% UBU  99.9%
  144277504/3243413504 ( 4.4%) @4.0x, remaining 13:57 RBU 100.0% UBU  99.4%
  162758656/3243413504 ( 5.0%) @4.0x, remaining 13:33 RBU 100.0% UBU  99.9%
  181239808/3243413504 ( 5.6%) @4.0x, remaining 12:57 RBU 100.0% UBU  99.9%
  199720960/3243413504 ( 6.2%) @4.0x, remaining 12:26 RBU 100.0% UBU  99.9%
  218234880/3243413504 ( 6.7%) @4.0x, remaining 12:14 RBU 100.0% UBU  99.9%
  236716032/3243413504 ( 7.3%) @4.0x, remaining 11:51 RBU 100.0% UBU  99.9%
  255197184/3243413504 ( 7.9%) @4.0x, remaining 11:30 RBU 100.0% UBU  96.4%
  273678336/3243413504 ( 8.4%) @4.0x, remaining 11:23 RBU 100.0% UBU  99.9%
  292192256/3243413504 ( 9.0%) @4.0x, remaining 11:06 RBU  99.9% UBU  99.9%
  310673408/3243413504 ( 9.6%) @4.0x, remaining 10:51 RBU 100.0% UBU  99.9%
  329154560/3243413504 (10.1%) @4.0x, remaining 10:46 RBU 100.0% UBU  99.9%
  344227840/3243413504 (10.6%) @3.3x, remaining 10:40 RBU  99.1% UBU  72.5%
  363102208/3243413504 (11.2%) @4.1x, remaining 10:26 RBU  99.9% UBU  68.2%
  381583360/3243413504 (11.8%) @4.0x, remaining 10:22 RBU  99.5% UBU  92.9%
  400031744/3243413504 (12.3%) @4.0x, remaining 10:11 RBU 100.0% UBU  84.3%
  418578432/3243413504 (12.9%) @4.0x, remaining 10:00 RBU 100.0% UBU  90.8%
  434044928/3243413504 (13.4%) @3.4x, remaining 10:01 RBU 100.0% UBU   4.7%
  452526080/3243413504 (14.0%) @4.0x, remaining 9:52 RBU 100.0% UBU  99.9%
  471007232/3243413504 (14.5%) @4.0x, remaining 9:42 RBU 100.0% UBU  96.5%
  489488384/3243413504 (15.1%) @4.0x, remaining 9:39 RBU 100.0% UBU  98.8%
  508002304/3243413504 (15.7%) @4.0x, remaining 9:30 RBU 100.0% UBU  99.9%
  526483456/3243413504 (16.2%) @4.0x, remaining 9:22 RBU 100.0% UBU  99.9%
  544964608/3243413504 (16.8%) @4.0x, remaining 9:19 RBU 100.0% UBU  99.9%
  563478528/3243413504 (17.4%) @4.0x, remaining 9:11 RBU 100.0% UBU  92.6%
  581959680/3243413504 (17.9%) @4.0x, remaining 9:04 RBU 100.0% UBU  99.9%
  600440832/3243413504 (18.5%) @4.0x, remaining 9:01 RBU 100.0% UBU  99.7%
  618921984/3243413504 (19.1%) @4.0x, remaining 8:54 RBU 100.0% UBU  99.9%
  637403136/3243413504 (19.7%) @4.0x, remaining 8:47 RBU 100.0% UBU  93.8%
  655917056/3243413504 (20.2%) @4.0x, remaining 8:44 RBU  99.9% UBU  99.9%
  674398208/3243413504 (20.8%) @4.0x, remaining 8:38 RBU  99.9% UBU  99.9%
  692879360/3243413504 (21.4%) @4.0x, remaining 8:31 RBU  99.9% UBU  99.9%
  711360512/3243413504 (21.9%) @4.0x, remaining 8:29 RBU 100.0% UBU  99.9%
  729841664/3243413504 (22.5%) @4.0x, remaining 8:22 RBU 100.0% UBU  99.9%
  745242624/3243413504 (23.0%) @3.3x, remaining 8:19 RBU 100.0% UBU  99.9%
  763723776/3243413504 (23.5%) @4.0x, remaining 8:16 RBU 100.0% UBU  99.9%
  782204928/3243413504 (24.1%) @4.0x, remaining 8:10 RBU 100.0% UBU  99.9%
  800686080/3243413504 (24.7%) @4.0x, remaining 8:05 RBU 100.0% UBU  99.9%
  819200000/3243413504 (25.3%) @4.0x, remaining 8:02 RBU 100.0% UBU  99.9%
  837681152/3243413504 (25.8%) @4.0x, remaining 7:56 RBU 100.0% UBU  99.9%
  856162304/3243413504 (26.4%) @4.0x, remaining 7:51 RBU 100.0% UBU  99.9%
  874643456/3243413504 (27.0%) @4.0x, remaining 7:48 RBU 100.0% UBU  99.9%
  893124608/3243413504 (27.5%) @4.0x, remaining 7:43 RBU 100.0% UBU  99.9%
  911638528/3243413504 (28.1%) @4.0x, remaining 7:37 RBU  99.9% UBU  88.2%
  930119680/3243413504 (28.7%) @4.0x, remaining 7:35 RBU 100.0% UBU  99.9%
  948600832/3243413504 (29.2%) @4.0x, remaining 7:29 RBU 100.0% UBU  99.9%
  967114752/3243413504 (29.8%) @4.0x, remaining 7:24 RBU 100.0% UBU  99.9%
  985595904/3243413504 (30.4%) @4.0x, remaining 7:22 RBU 100.0% UBU  99.9%
 1004011520/3243413504 (31.0%) @4.0x, remaining 7:17 RBU 100.0% UBU  99.9%
 1022590976/3243413504 (31.5%) @4.0x, remaining 7:12 RBU 100.0% UBU  99.0%
 1041072128/3243413504 (32.1%) @4.0x, remaining 7:09 RBU 100.0% UBU  97.7%
 1059520512/3243413504 (32.7%) @4.0x, remaining 7:04 RBU 100.0% UBU  98.5%
 1078034432/3243413504 (33.2%) @4.0x, remaining 6:59 RBU 100.0% UBU  99.9%
 1096548352/3243413504 (33.8%) @4.0x, remaining 6:57 RBU 100.0% UBU  85.0%
 1115029504/3243413504 (34.4%) @4.0x, remaining 6:52 RBU 100.0% UBU  91.6%
 1133510656/3243413504 (34.9%) @4.0x, remaining 6:47 RBU 100.0% UBU  99.9%
 1148813312/3243413504 (35.4%) @3.3x, remaining 6:46 RBU 100.0% UBU  99.9%
 1167294464/3243413504 (36.0%) @4.0x, remaining 6:41 RBU 100.0% UBU  99.9%
 1185808384/3243413504 (36.6%) @4.0x, remaining 6:37 RBU 100.0% UBU  99.9%
 1204289536/3243413504 (37.1%) @4.0x, remaining 6:34 RBU 100.0% UBU  99.3%
 1222770688/3243413504 (37.7%) @4.0x, remaining 6:29 RBU 100.0% UBU  99.9%
 1241251840/3243413504 (38.3%) @4.0x, remaining 6:25 RBU 100.0% UBU  99.7%
 1259732992/3243413504 (38.8%) @4.0x, remaining 6:22 RBU 100.0% UBU  93.8%
 1278214144/3243413504 (39.4%) @4.0x, remaining 6:18 RBU 100.0% UBU  99.9%
 1296695296/3243413504 (40.0%) @4.0x, remaining 6:13 RBU 100.0% UBU  99.9%
 1315176448/3243413504 (40.5%) @4.0x, remaining 6:10 RBU 100.0% UBU  99.9%
 1333657600/3243413504 (41.1%) @4.0x, remaining 6:06 RBU 100.0% UBU  94.9%
 1352171520/3243413504 (41.7%) @4.0x, remaining 6:02 RBU  99.9% UBU  99.9%
 1370652672/3243413504 (42.3%) @4.0x, remaining 5:59 RBU 100.0% UBU  97.2%
 1389133824/3243413504 (42.8%) @4.0x, remaining 5:55 RBU 100.0% UBU  99.9%
 1407614976/3243413504 (43.4%) @4.0x, remaining 5:50 RBU 100.0% UBU  99.3%
 1426096128/3243413504 (44.0%) @4.0x, remaining 5:47 RBU 100.0% UBU  99.9%
 1444610048/3243413504 (44.5%) @4.0x, remaining 5:43 RBU 100.0% UBU  99.9%
 1463091200/3243413504 (45.1%) @4.0x, remaining 5:39 RBU 100.0% UBU  96.9%
 1481572352/3243413504 (45.7%) @4.0x, remaining 5:36 RBU 100.0% UBU  98.8%
 1500053504/3243413504 (46.2%) @4.0x, remaining 5:32 RBU 100.0% UBU  99.9%
 1518567424/3243413504 (46.8%) @4.0x, remaining 5:28 RBU 100.0% UBU  85.6%
 1537048576/3243413504 (47.4%) @4.0x, remaining 5:25 RBU 100.0% UBU  99.9%
 1552449536/3243413504 (47.9%) @3.3x, remaining 5:22 RBU 100.0% UBU  99.7%
 1570963456/3243413504 (48.4%) @4.0x, remaining 5:18 RBU  99.9% UBU  99.9%
 1589444608/3243413504 (49.0%) @4.0x, remaining 5:15 RBU 100.0% UBU  99.0%
 1607892992/3243413504 (49.6%) @4.0x, remaining 5:11 RBU 100.0% UBU  99.9%
 1626406912/3243413504 (50.1%) @4.0x, remaining 5:07 RBU 100.0% UBU  99.9%
 1644789760/3243413504 (50.7%) @4.0x, remaining 5:04 RBU 100.0% UBU  94.2%
 1663369216/3243413504 (51.3%) @4.0x, remaining 5:00 RBU 100.0% UBU  99.3%
 1681850368/3243413504 (51.9%) @4.0x, remaining 4:56 RBU 100.0% UBU  99.9%
 1700364288/3243413504 (52.4%) @4.0x, remaining 4:53 RBU 100.0% UBU  99.9%
 1718845440/3243413504 (53.0%) @4.0x, remaining 4:49 RBU 100.0% UBU  99.9%
 1737326592/3243413504 (53.6%) @4.0x, remaining 4:45 RBU 100.0% UBU  99.9%
 1755807744/3243413504 (54.1%) @4.0x, remaining 4:42 RBU 100.0% UBU  99.9%
 1774288896/3243413504 (54.7%) @4.0x, remaining 4:38 RBU 100.0% UBU  99.9%
 1792770048/3243413504 (55.3%) @4.0x, remaining 4:34 RBU 100.0% UBU  99.9%
 1811251200/3243413504 (55.8%) @4.0x, remaining 4:31 RBU 100.0% UBU  99.9%
 1829732352/3243413504 (56.4%) @4.0x, remaining 4:27 RBU 100.0% UBU  99.9%
 1848213504/3243413504 (57.0%) @4.0x, remaining 4:23 RBU 100.0% UBU  99.9%
 1866694656/3243413504 (57.6%) @4.0x, remaining 4:20 RBU 100.0% UBU  99.9%
 1885175808/3243413504 (58.1%) @4.0x, remaining 4:16 RBU 100.0% UBU  99.9%
 1903656960/3243413504 (58.7%) @4.0x, remaining 4:12 RBU 100.0% UBU  99.9%
 1922170880/3243413504 (59.3%) @4.0x, remaining 4:09 RBU 100.0% UBU  99.9%
 1940652032/3243413504 (59.8%) @4.0x, remaining 4:05 RBU 100.0% UBU  99.9%
 1959133184/3243413504 (60.4%) @4.0x, remaining 4:01 RBU 100.0% UBU  99.9%
 1977614336/3243413504 (61.0%) @4.0x, remaining 3:58 RBU 100.0% UBU  98.8%
 1996128256/3243413504 (61.5%) @4.0x, remaining 3:54 RBU  99.9% UBU  99.9%
 2014609408/3243413504 (62.1%) @4.0x, remaining 3:51 RBU 100.0% UBU  99.9%
 2033090560/3243413504 (62.7%) @4.0x, remaining 3:48 RBU 100.0% UBU  99.9%
 2051604480/3243413504 (63.3%) @4.0x, remaining 3:44 RBU 100.0% UBU  99.9%
 2070085632/3243413504 (63.8%) @4.0x, remaining 3:40 RBU 100.0% UBU  99.9%
 2085486592/3243413504 (64.3%) @3.3x, remaining 3:38 RBU 100.0% UBU  99.9%
 2103967744/3243413504 (64.9%) @4.0x, remaining 3:34 RBU 100.0% UBU  99.9%
 2122481664/3243413504 (65.4%) @4.0x, remaining 3:30 RBU  99.9% UBU  99.9%
 2140962816/3243413504 (66.0%) @4.0x, remaining 3:27 RBU  99.9% UBU  99.9%
 2159443968/3243413504 (66.6%) @4.0x, remaining 3:23 RBU 100.0% UBU  99.9%
 2177925120/3243413504 (67.1%) @4.0x, remaining 3:20 RBU 100.0% UBU  99.9%
 2196406272/3243413504 (67.7%) @4.0x, remaining 3:16 RBU 100.0% UBU  99.9%
 2214920192/3243413504 (68.3%) @4.0x, remaining 3:13 RBU 100.0% UBU  99.9%
 2233401344/3243413504 (68.9%) @4.0x, remaining 3:09 RBU 100.0% UBU  99.9%
 2251882496/3243413504 (69.4%) @4.0x, remaining 3:06 RBU 100.0% UBU  99.9%
 2270363648/3243413504 (70.0%) @4.0x, remaining 3:02 RBU 100.0% UBU  99.9%
 2288844800/3243413504 (70.6%) @4.0x, remaining 2:58 RBU 100.0% UBU  99.9%
 2307358720/3243413504 (71.1%) @4.0x, remaining 2:55 RBU 100.0% UBU  99.9%
 2325839872/3243413504 (71.7%) @4.0x, remaining 2:52 RBU 100.0% UBU  99.9%
 2344321024/3243413504 (72.3%) @4.0x, remaining 2:48 RBU 100.0% UBU  99.9%
 2362802176/3243413504 (72.8%) @4.0x, remaining 2:45 RBU 100.0% UBU  99.9%
 2381283328/3243413504 (73.4%) @4.0x, remaining 2:41 RBU 100.0% UBU  99.9%
 2399764480/3243413504 (74.0%) @4.0x, remaining 2:37 RBU 100.0% UBU  99.9%
 2418245632/3243413504 (74.6%) @4.0x, remaining 2:34 RBU 100.0% UBU  96.7%
 2436726784/3243413504 (75.1%) @4.0x, remaining 2:30 RBU 100.0% UBU  99.9%
 2455207936/3243413504 (75.7%) @4.0x, remaining 2:27 RBU 100.0% UBU  98.7%
 2473721856/3243413504 (76.3%) @4.0x, remaining 2:24 RBU 100.0% UBU  99.9%
 2489155584/3243413504 (76.7%) @3.3x, remaining 2:21 RBU 100.0% UBU  99.9%
 2507636736/3243413504 (77.3%) @4.0x, remaining 2:17 RBU 100.0% UBU  98.8%
 2526117888/3243413504 (77.9%) @4.0x, remaining 2:14 RBU 100.0% UBU  99.9%
 2544599040/3243413504 (78.5%) @4.0x, remaining 2:10 RBU 100.0% UBU  99.9%
 2563112960/3243413504 (79.0%) @4.0x, remaining 2:07 RBU 100.0% UBU  99.9%
 2581594112/3243413504 (79.6%) @4.0x, remaining 2:03 RBU 100.0% UBU  99.3%
 2600075264/3243413504 (80.2%) @4.0x, remaining 2:00 RBU 100.0% UBU  99.9%
 2618556416/3243413504 (80.7%) @4.0x, remaining 1:56 RBU 100.0% UBU  99.9%
 2637004800/3243413504 (81.3%) @4.0x, remaining 1:53 RBU 100.0% UBU  94.0%
 2655551488/3243413504 (81.9%) @4.0x, remaining 1:49 RBU  99.9% UBU  99.1%
 2674032640/3243413504 (82.4%) @4.0x, remaining 1:46 RBU 100.0% UBU  73.4%
 2692546560/3243413504 (83.0%) @4.0x, remaining 1:42 RBU 100.0% UBU  99.9%
 2711027712/3243413504 (83.6%) @4.0x, remaining 1:39 RBU 100.0% UBU  82.4%
 2729508864/3243413504 (84.2%) @4.0x, remaining 1:36 RBU 100.0% UBU  99.9%
 2747990016/3243413504 (84.7%) @4.0x, remaining 1:32 RBU 100.0% UBU  99.9%
 2766471168/3243413504 (85.3%) @4.0x, remaining 1:28 RBU 100.0% UBU  82.6%
 2784985088/3243413504 (85.9%) @4.0x, remaining 1:25 RBU 100.0% UBU  98.7%
 2803466240/3243413504 (86.4%) @4.0x, remaining 1:22 RBU 100.0% UBU  99.9%
 2821947392/3243413504 (87.0%) @4.0x, remaining 1:18 RBU 100.0% UBU  99.0%
 2840461312/3243413504 (87.6%) @4.0x, remaining 1:15 RBU 100.0% UBU  99.9%
 2858942464/3243413504 (88.1%) @4.0x, remaining 1:11 RBU 100.0% UBU  99.9%
 2877423616/3243413504 (88.7%) @4.0x, remaining 1:08 RBU 100.0% UBU  99.9%
 2895937536/3243413504 (89.3%) @4.0x, remaining 1:04 RBU  99.9% UBU  99.9%
 2914418688/3243413504 (89.9%) @4.0x, remaining 1:01 RBU 100.0% UBU  99.9%
 2932899840/3243413504 (90.4%) @4.0x, remaining 0:57 RBU 100.0% UBU  99.9%
 2951380992/3243413504 (91.0%) @4.0x, remaining 0:54 RBU  99.9% UBU  99.9%
 2969862144/3243413504 (91.6%) @4.0x, remaining 0:50 RBU  99.9% UBU  99.3%
 2988343296/3243413504 (92.1%) @4.0x, remaining 0:47 RBU 100.0% UBU  99.9%
 3006824448/3243413504 (92.7%) @4.0x, remaining 0:44 RBU 100.0% UBU  99.9%
 3022159872/3243413504 (93.2%) @3.3x, remaining 0:41 RBU  99.9% UBU  99.9%
 3040641024/3243413504 (93.7%) @4.0x, remaining 0:37 RBU 100.0% UBU  99.7%
 3059154944/3243413504 (94.3%) @4.0x, remaining 0:34 RBU 100.0% UBU  99.9%
 3077636096/3243413504 (94.9%) @4.0x, remaining 0:30 RBU 100.0% UBU  98.8%
 3093889024/3243413504 (95.4%) @3.5x, remaining 0:27 RBU 100.0% UBU  60.5%
 3111059456/3243413504 (95.9%) @3.7x, remaining 0:24 RBU 100.0% UBU  98.7%
 3129540608/3243413504 (96.5%) @4.0x, remaining 0:21 RBU  99.8% UBU  96.7%
 3148021760/3243413504 (97.1%) @4.0x, remaining 0:17 RBU 100.0% UBU  96.1%
 3166535680/3243413504 (97.6%) @4.0x, remaining 0:14 RBU 100.0% UBU  99.9%
 3185016832/3243413504 (98.2%) @4.0x, remaining 0:10 RBU 100.0% UBU  95.6%
 3203530752/3243413504 (98.8%) @4.0x, remaining 0:07 RBU 100.0% UBU  77.3%
 3222011904/3243413504 (99.3%) @4.0x, remaining 0:03 RBU  63.9% UBU  99.9%
 3240493056/3243413504 (99.9%) @4.0x, remaining 0:00 RBU   8.8% UBU  99.9%
builtin_dd: 1583712*2KB out @ average 3.9x1352KBps
/dev/dvd: flushing cache
/dev/dvd: closing track
/dev/dvd: closing disc
/dev/dvd: reloading tray
harlan@ubuntufan:~$

---

### Post by harlanwolfe on 2011-06-05
Same result. 2 different iso images. This time, the system reverted to Ubuntu login after a couple minutes, and now the disc is being recognized as a blank.
I'm stumped.

---

### Post by TeoBigusGeekus on 2011-06-05
Get a different iso from a different source.

---

### Post by harlanwolfe on 2011-06-05
Thanks for the burn command & the tip about the gui burners, tho...will use it from now on!

---

### Post by corncob on 2011-06-05
Just a thought: you are burning the contents to the disk, not just copying the iso file?  What does it look like when you open the DVD in a running computer to view files?  I burnt some DVDs recently (pinguy and Linux Mint) with no problem using K3b.

---

