---
title: "problem starting ubuntu ...please help"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by karan_sharma01 on 2010-08-24
hi I am using ubuntu 8.10 on my desktop ...and theres a problem ...its not getting started.

After the routine checkup it showed some error .....and i used fsck command to manually recover the error ....after recovering all the errors its showing something like during booting 

starting kernel log deamon ....[ok]
mkdie: cannot access directory '/var/run' : Read only file system
chown: cannot access '/var/run/Klogd': No such file or directory
mkfifo: cannot create fifo '/var/run/klogd/kmsg': No such file or directory
...
....
start-stor-deamon:Unable to open pidfile '/var/run/klog/kmsgpipe.pid' for writing : No such file or directory (No such file or directory


and after this a blue screen comes up saying ..
Server Authorization directory (deamon/ServerAuthDir) is set to /var/lib/gdm but this does not exist.Please correct GDM configuration and restart GDM.

Im not been able to access my computer .... and need serious help

thanx in advance

---

### Post by ubudog on 2010-08-24
Looks like a bunch of needed files are missing.  You may have to reinstall.  If you can get to the recovery console, you can backup your stuff to a flash drive or cd.

---

### Post by karan_sharma01 on 2010-08-24
:(:(:(:(:(:(
Is there any way around .......or anything so that i can save my data..??

---

### Post by DrMelon on 2010-08-24
As has been said, you might want to use a newer version (like 10.04, for example).

---

### Post by ubudog on 2010-08-24
Start the recovery mode.  Insert a cd or flash drive, and copy the files to it.
```
cp nameoffile /media/nameofdrive
```

Then, go on another computer and get a 10.04 cd and install ubuntu from that.

Oh, and you have to type cp -a for directories.

---

### Post by karan_sharma01 on 2010-08-24
tried sudo fsck -fy...still the same problem.....and yes i'll try to use 10.04......but is there any way to sove this problem???

---

### Post by karan_sharma01 on 2010-08-24
sudo dpkg-reconfigure gdm is giving the output

Unrecognize chalacter \xA8 in column 1 at /usr/lib/perl/5.10/IO/File.pm line 1.
Compilation failed in require at /usr/share/perl/5.10/FileHandle.pm Line 9.
Compilation failed in require at /usr/share/perl/5.10/Debconf/Template.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl/5.10/Debconf/Template.pm line 8
.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
.

Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl/5.10/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7
BEGIN failed--compilation aborted at /usr/share/perl/5.10/Debconf/Db.pm line7
Compilation failed in require at /usr/sbin/dpkg-reconfigure line 9.
BEGIN failed--compilation aborted at /usr/sbin/dpkg-reconfigure line 9
:(:(:(

---

### Post by sadaruwan12 on 2010-08-24
> **Chauncellor said:**
> ....um, did you.... log in as root and start thrashing around folders? O.o.

It does seem kind of like reinstalling would be the easiest route. Things look all sorts of messed up. I'm afraid I don't know what to do there.

You don't need any command line to get your files off, just a liveCD. You can boot up via the cd, mount your hard drive, and drag 'n drop the files onto another drive.

I'm sorry if this doesn't get resolved, but this looks nasty. I'll keep following and input any suggestions if I can think of one.

I also agree with Chauncellor this kind of error comes when you hdd get messed up the remedy for this kind of a error is to do a clean install to recover your files you might have to use the live cd and from that you can copy your data to pen drive.

And theres no way around this kind of a problem.

---

### Post by karan_sharma01 on 2010-08-24
Ive been using ubuntu for some time now .... i dont think i did something like this 
anyways thanx for your help:)..... i'll try to this with live cd

---

### Post by sadaruwan12 on 2010-08-24
> **karan_sharma01 said:**
> Ive been using ubuntu for some time now .... i dont think i did something like this 
anyways thanx for your help:)..... i'll try to this with live cd

Well thats thing Bro you haven't we have any way If your home folder is in a new partition you can format and install the root with out loosing your data but best advised to take a backup.:D

Oh .... and if you can use a new version live cd.

---

### Post by karan_sharma01 on 2010-08-28
hey i've logged in with live cd (ubuntu10.04) ....but m not been able to find the data ... the partition is showing the appropriate used data in the partition...can you guys please tell where this data can be found ....it was stored with xyz users dekstop....

---

### Post by karan_sharma01 on 2010-08-28
no the partion dont have /home/xyz ......but its showing the appropriate used space..:(

---

### Post by karan_sharma01 on 2010-08-28
its showing no files found :(:(:( ....

---

### Post by karan_sharma01 on 2010-08-28
hey with terminal its shoewing all the files ...but thres some input/output error...

root@ubuntu:/home/ubuntu# cd /media/eaf4f0c4-a137-4e73-9845-e8761df4d092
root@ubuntu:/media/eaf4f0c4-a137-4e73-9845-e8761df4d092# ls
ls: cannot access media: Input/output error
ls: cannot access home: Input/output error
bin    dev   initrd          lib         mnt   root  sys  var
boot   etc   initrd.img      lost+found  opt   sbin  tmp  vmlinuz
cdrom  home  initrd.img.old  media       proc  srv   usr  vmlinuz.old
root@ubuntu:/media/eaf4f0c4-a137-4e73-9845-e8761df4d092# cd home 
bash: cd: home: Input/output error
root@ubuntu:/media/eaf4f0c4-a137-4e73-9845-e8761df4d092# cd ./home
bash: cd: ./home: Input/output error


:(

---

### Post by ubudog on 2010-08-28
Maybe this will help, found it in another thread.

[http://ckdevelop.org/download/count.php?id=4](http://ckdevelop.org/download/count.php?id=4)

---

### Post by karan_sharma01 on 2010-08-28
yes after unmounting the file system ..i did check file system .... and it showed filesystem is not clean ....what should be done so that i can recover my data....and can i install ubuntu10.04 on this partition???

---

### Post by karan_sharma01 on 2010-08-28
Inode 688258 has illegal block(s).  Clear? yes

Illegal block #403 (3157884729) in inode 688258.  CLEARED.
Illegal block #404 (909834553) in inode 688258.  CLEARED.
Illegal block #405 (2990175290) in inode 688258.  CLEARED.
Illegal block #406 (758902586) in inode 688258.  CLEARED.
Illegal block #407 (2856020795) in inode 688258.  CLEARED.
Illegal block #408 (658303035) in inode 688258.  CLEARED.
Illegal block #409 (2755421500) in inode 688258.  CLEARED.
Illegal block #410 (574481212) in inode 688258.  CLEARED.
Illegal block #411 (2705154365) in inode 688258.  CLEARED.
Illegal block #412 (540991549) in inode 688258.  CLEARED.
Illegal block #413 (2688442430) in inode 688258.  CLEARED.
Too many illegal blocks in inode 688258.
Clear inode? yes

Inode 688259 has illegal block(s).  Clear? yes

Illegal block #321 (1924214234) in inode 688259.  CLEARED.
Illegal block #322 (1448838071) in inode 688259.  CLEARED.
Illegal block #323 (118139309) in inode 688259.  CLEARED.
Illegal block #324 (4025122178) in inode 688259.  CLEARED.
Illegal block #325 (1733186555) in inode 688259.  CLEARED.
Illegal block #326 (272594672) in inode 688259.  CLEARED.
Illegal block #327 (780995380) in inode 688259.  CLEARED.
Illegal block #328 (1659748606) in inode 688259.  CLEARED.
Illegal block #329 (537582070) in inode 688259.  CLEARED.
Illegal block #330 (3350278158) in inode 688259.  CLEARED.
Illegal block #331 (2198558125) in inode 688259.  CLEARED.
Too many illegal blocks in inode 688259.
Clear inode? yes

Inode 688261 has illegal block(s).  Clear? yes

Illegal block #320 (1603461241) in inode 688261.  CLEARED.
Illegal block #321 (2701197097) in inode 688261.  CLEARED.
Illegal block #322 (2115582177) in inode 688261.  CLEARED.
Illegal block #323 (1594762911) in inode 688261.  CLEARED.
Illegal block #324 (2432261901) in inode 688261.  CLEARED.
Illegal block #325 (2477832996) in inode 688261.  CLEARED.
Illegal block #326 (217408692) in inode 688261.  CLEARED.
Illegal block #327 (2572461375) in inode 688261.  CLEARED.
Illegal block #328 (2456013456) in inode 688261.  CLEARED.
Illegal block #329 (2197484037) in inode 688261.  CLEARED.
Illegal block #330 (2540889451) in inode 688261.  CLEARED.
Too many illegal blocks in inode 688261.
Clear inode? yes

Inode 688262 has illegal block(s).  Clear? yes

Illegal block #403 (3157884729) in inode 688262.  CLEARED.
Illegal block #404 (909834553) in inode 688262.  CLEARED.
Illegal block #405 (2990175290) in inode 688262.  CLEARED.
Illegal block #406 (758902586) in inode 688262.  CLEARED.
Illegal block #407 (2856020795) in inode 688262.  CLEARED.
Illegal block #408 (658303035) in inode 688262.  CLEARED.
Illegal block #409 (2755421500) in inode 688262.  CLEARED.
Illegal block #410 (574481212) in inode 688262.  CLEARED.
Illegal block #411 (2705154365) in inode 688262.  CLEARED.
Illegal block #412 (540991549) in inode 688262.  CLEARED.
Illegal block #413 (2688442430) in inode 688262.  CLEARED.
Too many illegal blocks in inode 688262.
Clear inode? yes

Inode 688263 has illegal block(s).  Clear? yes

Illegal block #320 (207002579) in inode 688263.  CLEARED.
Illegal block #321 (2613000045) in inode 688263.  CLEARED.
Illegal block #322 (1332212569) in inode 688263.  CLEARED.
Illegal block #323 (2227173411) in inode 688263.  CLEARED.
Illegal block #324 (337451701) in inode 688263.  CLEARED.
Illegal block #325 (3831670301) in inode 688263.  CLEARED.
Illegal block #326 (496782286) in inode 688263.  CLEARED.
Illegal block #327 (1576650071) in inode 688263.  CLEARED.
Illegal block #328 (4092171558) in inode 688263.  CLEARED.
Illegal block #329 (2760969760) in inode 688263.  CLEARED.
Illegal block #330 (2723644831) in inode 688263.  CLEARED.
Too many illegal blocks in inode 688263.
Clear inode? yes

Inode 688264 has illegal block(s).  Clear? yes

Illegal block #320 (2600297237) in inode 688264.  CLEARED.
Illegal block #321 (346643367) in inode 688264.  CLEARED.
Illegal block #322 (2559997684) in inode 688264.  CLEARED.
Illegal block #323 (2385576191) in inode 688264.  CLEARED.
Illegal block #324 (240590199) in inode 688264.  CLEARED.
Illegal block #325 (601235949) in inode 688264.  CLEARED.
Illegal block #326 (1272865472) in inode 688264.  CLEARED.
Illegal block #327 (272790185) in inode 688264.  CLEARED.
Illegal block #328 (2440359812) in inode 688264.  CLEARED.
Illegal block #329 (4130893716) in inode 688264.  CLEARED.
Illegal block #330 (4103022396) in inode 688264.  CLEARED.
Too many illegal blocks in inode 688264.
Clear inode? yes

Inode 688265 has illegal block(s).  Clear? yes

Illegal block #321 (1618788333) in inode 688265.  CLEARED.
Illegal block #322 (4022135819) in inode 688265.  CLEARED.
Illegal block #323 (1893611748) in inode 688265.  CLEARED.
Illegal block #324 (963702120) in inode 688265.  CLEARED.
Illegal block #325 (2112959246) in inode 688265.  CLEARED.
Illegal block #326 (1768525336) in inode 688265.  CLEARED.
Illegal block #327 (1168713890) in inode 688265.  CLEARED.
Illegal block #328 (4203464027) in inode 688265.  CLEARED.
Illegal block #329 (1903252062) in inode 688265.  CLEARED.
Illegal block #330 (490983348) in inode 688265.  CLEARED.
Illegal block #331 (3806947508) in inode 688265.  CLEARED.
Too many illegal blocks in inode 688265.
Clear inode? yes

Inode 688266 has illegal block(s).  Clear? yes

Illegal block #320 (2137585489) in inode 688266.  CLEARED.
Illegal block #321 (3117472919) in inode 688266.  CLEARED.
Illegal block #322 (383584481) in inode 688266.  CLEARED.
Illegal block #323 (3545780141) in inode 688266.  CLEARED.
Illegal block #324 (1274857716) in inode 688266.  CLEARED.
Illegal block #325 (530692315) in inode 688266.  CLEARED.
Illegal block #326 (1291138803) in inode 688266.  CLEARED.
Illegal block #327 (1015680994) in inode 688266.  CLEARED.
Illegal block #328 (812476219) in inode 688266.  CLEARED.
Illegal block #329 (1323080886) in inode 688266.  CLEARED.
Illegal block #330 (453374484) in inode 688266.  CLEARED.
Too many illegal blocks in inode 688266.
Clear inode? yes

Inode 688267 has illegal block(s).  Clear? yes

Illegal block #403 (3157884729) in inode 688267.  CLEARED.
Illegal block #404 (909834553) in inode 688267.  CLEARED.
Illegal block #405 (2990175290) in inode 688267.  CLEARED.
Illegal block #406 (758902586) in inode 688267.  CLEARED.
Illegal block #407 (2856020795) in inode 688267.  CLEARED.
Illegal block #408 (658303035) in inode 688267.  CLEARED.
Illegal block #409 (2755421500) in inode 688267.  CLEARED.
Illegal block #410 (574481212) in inode 688267.  CLEARED.
Illegal block #411 (2705154365) in inode 688267.  CLEARED.
Illegal block #412 (540991549) in inode 688267.  CLEARED.
Illegal block #413 (2688442430) in inode 688267.  CLEARED.
Too many illegal blocks in inode 688267.
Clear inode? yes

Inode 688269 has illegal block(s).  Clear? yes

Illegal block #329 (3009147498) in inode 688269.  CLEARED.
Illegal block #330 (1617403692) in inode 688269.  CLEARED.
Illegal block #331 (3615193881) in inode 688269.  CLEARED.
Illegal block #332 (1971965927) in inode 688269.  CLEARED.
Illegal block #333 (2511972137) in inode 688269.  CLEARED.
Illegal block #334 (2261773402) in inode 688269.  CLEARED.
Illegal block #335 (3440452665) in inode 688269.  CLEARED.
Illegal block #336 (2703647094) in inode 688269.  CLEARED.
Illegal block #337 (1881568633) in inode 688269.  CLEARED.
Illegal block #338 (2931116262) in inode 688269.  CLEARED.
Illegal block #339 (4089492831) in inode 688269.  CLEARED.
Too many illegal blocks in inode 688269.
Clear inode? yes

Inode 688271 has illegal block(s).  Clear? yes

Illegal block #320 (3133848102) in inode 688271.  CLEARED.
Illegal block #321 (787230603) in inode 688271.  CLEARED.
Illegal block #322 (12158257) in inode 688271.  CLEARED.
Illegal block #323 (535969650) in inode 688271.  CLEARED.
Illegal block #324 (3478477485) in inode 688271.  CLEARED.
Illegal block #325 (1703253690) in inode 688271.  CLEARED.
Illegal block #326 (1812064934) in inode 688271.  CLEARED.
Illegal block #327 (1412394318) in inode 688271.  CLEARED.
Illegal block #328 (1782049116) in inode 688271.  CLEARED.
Illegal block #329 (1579546630) in inode 688271.  CLEARED.
Illegal block #330 (1666162545) in inode 688271.  CLEARED.
Too many illegal blocks in inode 688271.
Clear inode? yes

Inode 688270, i_blocks is 232, should be 104.  Fix? yes

Inode 688274 has illegal block(s).  Clear? yes

Illegal block #320 (1034470033) in inode 688274.  CLEARED.
Illegal block #321 (1473185102) in inode 688274.  CLEARED.
Illegal block #322 (547660879) in inode 688274.  CLEARED.
Illegal block #323 (1751955357) in inode 688274.  CLEARED.
Illegal block #324 (297020636) in inode 688274.  CLEARED.
Illegal block #325 (2883184146) in inode 688274.  CLEARED.
Illegal block #326 (2836917900) in inode 688274.  CLEARED.
Illegal block #327 (2080849175) in inode 688274.  CLEARED.
Illegal block #328 (798203255) in inode 688274.  CLEARED.
Illegal block #329 (366357669) in inode 688274.  CLEARED.
Illegal block #330 (4209192466) in inode 688274.  CLEARED.
Too many illegal blocks in inode 688274.
Clear inode? yes

Inode 688276 has illegal block(s).  Clear? yes

Illegal block #320 (380420542) in inode 688276.  CLEARED.
Illegal block #321 (3779580677) in inode 688276.  CLEARED.
Illegal block #322 (1902381334) in inode 688276.  CLEARED.
Illegal block #323 (2783586363) in inode 688276.  CLEARED.
Illegal block #324 (1828268107) in inode 688276.  CLEARED.
Illegal block #325 (3050924739) in inode 688276.  CLEARED.
Illegal block #326 (1769017755) in inode 688276.  CLEARED.
Illegal block #327 (3097508924) in inode 688276.  CLEARED.
Illegal block #328 (3412278416) in inode 688276.  CLEARED.
Illegal block #329 (2828554159) in inode 688276.  CLEARED.
Illegal block #330 (3770692288) in inode 688276.  CLEARED.
Too many illegal blocks in inode 688276.
Clear inode? yes

Inode 688275 has illegal block(s).  Clear? yes

Illegal block #320 (1030059372) in inode 688275.  CLEARED.
Illegal block #321 (1533820221) in inode 688275.  CLEARED.
Illegal block #322 (1530879281) in inode 688275.  CLEARED.
Illegal block #323 (1983536497) in inode 688275.  CLEARED.
Illegal block #324 (2103270202) in inode 688275.  CLEARED.
Illegal block #325 (1714318651) in inode 688275.  CLEARED.
Illegal block #326 (1702128745) in inode 688275.  CLEARED.
Illegal block #327 (1145646706) in inode 688275.  CLEARED.
Illegal block #328 (1853187645) in inode 688275.  CLEARED.
Illegal block #329 (1869182051) in inode 688275.  CLEARED.
Illegal block #330 (745285742) in inode 688275.  CLEARED.
Too many illegal blocks in inode 688275.
Clear inode? yes

Restarting e2fsck from the beginning...
Pass 1: Checking inodes, blocks, and sizes



and still processing....

can i reinstall ubuntu in this partition??

---

### Post by karan_sharma01 on 2010-08-28
now done with the processing ...but still showing the same input/output error

ubuntu@ubuntu:~$ cd /media/eaf4f0c4-a137-4e73-9845-e8761df4d092
ubuntu@ubuntu:/media/eaf4f0c4-a137-4e73-9845-e8761df4d092$ ls
ls: cannot access media: Input/output error
ls: cannot access home: Input/output error
bin   cdrom  etc   initrd      initrd.img.old  lost+found  mnt  proc  sbin  sys  usr  vmlinuz
boot  dev    home  initrd.img  lib             media       opt  root  srv   tmp  var  vmlinuz.old
ubuntu@ubuntu:/media/eaf4f0c4-a137-4e73-9845-e8761df4d092$ cd home
bash: cd: home: Input/output error
ubuntu@ubuntu:/media/eaf4f0c4-a137-4e73-9845-e8761df4d092$

---

### Post by karan_sharma01 on 2010-08-28
still "File system is NOT clean."...:(

---

### Post by karan_sharma01 on 2010-08-28
yes in disk utility with check filesystem button..

---

### Post by karan_sharma01 on 2010-08-28
the output..assessment in other rows is good or N/A ...only in row with id 5 its showing the warning

---

### Post by karan_sharma01 on 2010-08-28
yes its is an old drive about ...i think 5-6 yrs old...

Just to clear you i have 80 GB Hard disk ...and this is happening on one partition ..... other partition are showing clean from disk utility 
  
now can I just format this partition and reinstall ubuntu 10.04 on it ...
why should i have to re-partition ???

---

