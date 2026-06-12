---
title: "Ubuntu 10.04 LTS (Lucid Lynx) can't get on Internet"
date: 2014-09-19
forum: Networking &amp; Wireless
---

### Post by cybrsaylr on 2014-09-19
A friend has been using 64 bit Ubuntu 10.04 LTS (Lucid Lynx) forever with no problems. Suddenly he lost ability to get on the Internet. He had a wired desktop PC. When I check his network there is no wired network icon on upper system tray and nothing wired shows up in network connections. Anyone have amy ideas on what happened?

---

### Post by slickymaster on 2014-09-19
We highly recommend you upgrade to a supported release.
Upgrade to 12.04 : [https://wiki.ubuntu.com/PrecisePango...untu_12.04_LTS](https://wiki.ubuntu.com/PrecisePango...untu_12.04_LTS)
Install 14.04 : [https://help.ubuntu.com/14.04/instal...ide/index.html](https://help.ubuntu.com/14.04/instal...ide/index.html)

For old computers with lower specifications, you may :
Read this link: [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")
Try Lubuntu or Xubuntu 14.04 LTS (supported until April 2017)
Try Xubuntu 12.04 LTS (supported until April 2015)
Alternative to Unity on 12.04 LTS: [Gnome Classic]("https://help.ubuntu.com/community/PreciseGnomeClassicTweaks")


We will not provide any additional support to EOL releases, and in particular to the 10.04 desktop edition.

---

### Post by cybrsaylr on 2014-09-19
Thanks for the speedy reply.

A little more. He knows his HDD is failing, has lot of bad sectors, Hitachi drive is 5+ yrs old along with that 5+ yr old Compaq dual core PC.
He got a new 500GB Seagate Sata HDD.

Ran 64 bit 14.04 and 12.04 fine off 'Live CD/DVD' on the new HDD. Installed 14.04 and it ran awhile very well then it quit! Tried a reinstall of 14.04 a couple times and things got stranger. It showed 14.04 install was successful but would not boot up on repeated restarts!  
Then installed 12.04 which ran better, till the main desktop screen went black! All that shows was upper system tray and sidebar icons! 
Never had this happen before. Spent a day trying to trouble shoot with nothing good happening. Ended up putting the old failing HDD back in. It still works well but can't get on the Internet and keeps reporting 'drive failure is imminent'! I'm stumped....

Ran all the Compaq 'diagnostic' tools while the new HDD was in and it reports all is A-OK on that PC....

---

### Post by slickymaster on 2014-09-19
Please **_back up your data immediately_**, for example by using a Ubuntu Live CD and an external hard drive.

You can check the SMART status of a disk through Disk Utility. Modern disks have a set of tests and benchmarks as part of their S.M.A.R.T. profile and operating systems perform quick tests on them occasionally. When certain tests fall below their specified operating values, this is usually a sign that the disk is getting old and that its performance will likely quickly continue to deteriorate to the point where you suffer data loss or it just packs up and dies.

You can verify this through Disk Utility (sitting in **System** **->** **Administration**). Find the disk, click SMART Data and you'll see a list of tests. Not all tests are performed automatically so you can manually set it to run a full test cycle but as soon as you see bad sectors or tests that are failing really poorly, the disk is as good as dead.

---

### Post by Bucky Ball on 2014-09-19
And to add to what slickymaster has posted, please [see here.]("http://ubuntuforums.org/showthread.php?t=2229730")

And yes, backup what you need to immediately, probably best doing that from a Ubuntu Live install DVD/USB rather than the hard drive boot. Good luck.

---

### Post by cybrsaylr on 2014-09-19
He did back up all he wanted to save.
Ran Disk Utility which showed many bad sectors on old HDD.
He did notice  performance was continuing to deteriorate.

Ran Disk Utility on the new HDD and all was green but 14.04 and 12.04 showed they were both online, just wouldn't run after a short time.....

Could it be something as simple as a faulty cable?

---

