---
title: "which distro for a 512 ram/2.8 ghz machine?"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by erazerhead on 2011-01-02
hello there,

as the title indicates im looking for advice to choose a proper distro for my rather old computer. im quite a newby; a week ago the first time ever i installed and used a linux system.

the computer in question is [a B]VAIO desktop pc with 512 ram, a 2.8 ghz processor and 120 gb hd[/B] in good shape. the machine will primarily be used for standard tasks by my parents who are *absolute* computer beginners.

the major priorities are:

-lieghtweight - there should be maximum speed for simple tasks like surfing, email, writing
-intuitive GUI
-full german localization has to be available

less important are:

-big software bundles
-fancy eycandy - compisitioning effects, 3d desktop etc are nice but not necessary


in that first week of my linux-experience the system passed installs with **lubuntu** and **linux mint xfce** but neither one met the requirements. the speed on the old computer was ok - both considerably faster than the win xp that was installed before - but both distros looked sometwhat "under construction". system properties spread across the system, no central configuration tool (like in mac os x, there i can access all macro configuration from a single winow), no complete german language support - even after i updated it - and unnecessary redundancies. also both systems werent that stable.
while i honour the engagement of the develepers of the two testet distros - well, both would have been better than the win xp the machine came with - they didnt do the job for me.
i searched for a few days now but havent come to a conclusion regarding my choice for a third - and hopefully final ;) - distro to stick with. ubuntu or a derivate would be nice, but i fear the 512 ram are not enough. i have been close to download xubuntu but it seems that the "lieghtweight" derivate is now not really lighter than ubuntu. another appropriate distro would be ok too


so, whats your advice for me? i am sure that there have been topics like this one many times before, but after i couldnt come to a conclusion after days of extensionsive web search i thought that i might give the utilization of the ubuntu-philosphy of answering noob questions, no matter how often they come, a try ;) thank you for reading & answering.

---

### Post by Nytram on 2011-01-02
Hi Erazerhead, welcome to these forums

I would give regular Ubuntu a try, 512mb isnt bad for common tasks like browsing. I've used it with a Gb before and never went above 50% memory usage.

---

### Post by TeoBigusGeekus on 2011-01-02
Lubuntu.

---

### Post by ajgreeny on 2011-01-02
> **TeoBigusGeekus said:**
> Lubuntu.
+1
It's fast, and whilst not a Canonical official *ubuntu family member, still does everything the Ubuntu way and uses the repos.

---

### Post by khelben1979 on 2011-01-02
In my opinion, I think Ubuntu 10.04 "Lucid" would be the best choice if thinking about what version to choose from.

Otherwise you have Debian Squeeze, which works good and 512MB of RAM is enough for general usage, but if you decide to work a lot with video editing or complicated photo management using GIMP, you need at least another 512MB more in RAM to feel it's acceptable.

There are many ways to reduce memory usage no matter what distribution you choose from, and that is to understand the system and control what applications is started in /etc/init.d/ (the file path might differ depending on choice of distribution).

Also make note that what type of graphics it has and that slow open source graphic drivers (if ATi or nVidia) will create a more sluggish 2D/3D experience, go for non-free drivers instead if you want to avoid that.

---

### Post by astrobob.tk on 2011-01-02
I backup [khelben1979]("http://ubuntuforums.org/member.php?u=443262") for choosing Debian. I personally tried Ubuntu on my 256 MB RAM desktop & it couldnt launch, so I resorted to Debian 5.0 (at the time), now there's 6.0 (squeeze). I suggest Debian

good luck

---

### Post by PPPilot on 2011-01-02
I'm currently dual  booting both 10.04 Lucid and 10.10 Maverick on a Frankenstein machine built from the remains of 6 old machines. It  has 512 MB ram, 32 MB of which is used by the on-board video, and it has a 1200 Mhz Athlon CPU. Both operating systems run just fine and I even do some audio/video editing. It runs far faster than it ever did on Windows. 

It seems to help if you tweak the way Ubuntu uses the swap partition. To do this you need to add a couple of lines to the                       sysccti.conf file.

 First open a terminal and type in:

```
gksudo gedit /etc/sysctl.conf
```You will be asked for your password. You will not see any characters as you type in your password, that is normal, hit return.This will open the Gedit program and allow you to edit the sysccti.conf file. Below the last line of the file add these two lines:

 ```
vm.swappiness = 20
vm.vfs_cache_pressure = 50 
```Save the file, close Gedit and close the terminal.

Now reboot. I noticed improved performance after this tweak.


[FONT=Arial, sans-serif]
[/FONT]

---

### Post by walt.smith1960 on 2011-01-02
I too would recommend Lucid 32 bit desktop.  I have an old Thinkpad R31 that had 256 MB RAM  & 1 Ghz PIII processor.  I didn't notice much difference in performance between Xubuntu & desktop Ubuntu.  I later added another 256 MB. RAM and it is fine for basic tasks like web browsing & office tasks.  I did set my swap to 2X RAM but since having 512 MB RAM the swap is seldom if ever used.   Good Luck

---

### Post by snowpine on 2011-01-02
I think regular Ubuntu (or any of its derivatives) should work fine on those system specs. Obviously it will not be super-fast, because the computer itself is not fast. However I have run Ubuntu on systems as old as 500mhz pentium 3 with 256mb of RAM, so your specs are not *that* bad. :)

That being said, you won't find a more "lightweight" option for old hardware than Puppy Linux, plus it is very user-friendly for beginning Linux users.

---

### Post by erazerhead on 2011-01-02
thanks for your guidance. well, as it seems the standard ubuntu version isnt as hungry as i thought it to be ill give it a try. it just has that complete and polished feeling ;).
currently downloading the ISO and i havent yet fount out which hd formate  to choose of.  all i got is ext3 -> secure and better for older machines, ext -> fast on modern machines. well, ext3 or ext4 for my 512?
another thing i wanted to know is about the spap-partition. i wont boot another os than ubuntu on the pc - is swap even needed for a singe os? and if, how big should the partition be - does a swap greater than 2x ram make sense?

---

### Post by snowpine on 2011-01-02
> **erazerhead said:**
> thanks for your guidance. well, as it seems the standard ubuntu version isnt as hungry as i thought it to be ill give it a try. it just has that complete and polished feeling ;).
currently downloading the ISO and i havent yet fount out which hd formate  to choose of.  all i got is ext3 -> secure and better for older machines, ext -> fast on modern machines. well, ext3 or ext4 for my 512?
another thing i wanted to know is about the spap-partition. i wont boot another os than ubuntu on the pc - is swap even needed for a singe os? and if, how big should the partition be - does a swap greater than 2x ram make sense?

I would recommend using the default filesystem (ext4) and swap partition size, unless you have specific special needs. The default settings are carefully determined to work best for most users. (And yes, with only 512mb of RAM, you will definitely want a swap partition to give you extra "virtual RAM.")

---

### Post by PPPilot on 2011-01-02
I am using ext4 on both 10.04 and 10.10 with no problems so I would go that way for your install partition. As far as swap size goes, anything beyond 2x memory size is waste of drive space. Even rendering large video files, I have never seen swap usage go much above 10% of available space which on my system is 1.33 GB.

---

### Post by albert s on 2011-01-02
I have 10.04 on an old dell 1.6GHz celeron(IIRC) and 512 RAM and its fine for normal usage.
its not really much slower than my "proper" PC which is a core 2 duo 1.8GHz with 1G ram.
I know they may both seem very old and/or slow to lots of people but for me they are more than good enough for what I do,
some surfing , e.mails, music, and a bit of light video/photo editing, and some other mundane tasks.
the minimum requirements on the website seem to me to be a little high, perhaps in order for the system to run at full potential and avoid disappointment from over keen people wanting rocketship performance from not the lastest machinery.

EDIT:
BTW, my partitions are ;  15G   /      1G    /swap      and the rest  (24G)   /home  ,  I only have a 40G HDD in my "older" machine. my / is only about 6G used if I remember correctly.

---

### Post by Hippytaff on 2011-01-02
this is a good place to look [http://distrowatch.com/](http://distrowatch.com/)

but slitaz might meet your requirements and come highly recommended ;-)

however, not sure about the German language bit, but I wouldn't be surprised if this need is also met :-)

---

### Post by PPPilot on 2011-01-02
I have both the Gnome and KDE Desktops installed on both 10.04 and 10.10. I have noticed that the Gnome Desktop seems a little snappier than the KDE Desktop. I imagine this could be a function of my archaic on-board S3 video chip and the fact that it shares system memory. I've got some better video cards but this mother board does not have a AGP video card slot.

---

### Post by Hippytaff on 2011-01-02
I must admit, I missed the fact that this thread had advanced so far before I added my penneth worth :?

forgive my butting in :-)

---

