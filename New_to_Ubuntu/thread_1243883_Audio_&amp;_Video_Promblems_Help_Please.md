---
title: "Audio &amp; Video Promblems Help Please???"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by Zlap on 2009-08-18
Hey everyone, once again i am having a problem with ubuntu (still awesome though)


I am trying to watch some vids and meeting with no success. I can get Youtube to play the vids but not hear sound, and i can get my "other video websites" :lolflag: to play the vid for 1-3 sec, and have to click the spot where it left off and it will last another 2 seconds, and once again not have sound.

My speakers can play music off my computer but not on the vids.

Please trust me when i say i have googled for a answer and have tried i guess everything i looked at that was similar to my problem. I will post my about:plugins information as i am running firefox and you guys would most likely ask.

Thank you Guys YOU:guitar:

About:Plugins Info:
---
Instead of adding the image directly here, i will add link b/c ppl say it is to big so.

[http://img208.imageshack.us/img208/1511/screenshotkix.png](http://img208.imageshack.us/img208/1511/screenshotkix.png)


Thanks guys.

---

### Post by zerhacke on 2009-08-18
Install the ubuntu-restricted-extras package and it should solve everything.  Use Synaptics or apt-get to do so, there is no need to look on the internet for it because it's already in the Ubuntu repositories.

---

### Post by Zlap on 2009-08-18
I installed it. No errors or nothing restarted firefox 3 times, no success. Any other ideas?

---

### Post by Zlap on 2009-08-18
Can anyone help with this or am i screwed??? I really don't want to go to Windows...

---

### Post by stoogiebuncho on 2009-08-18
Are you using Ubuntu 9.04?  There is a bug that has been affecting video playback (and audio too, in some cases I've heard of).

Open a terminal and enter this code:
```
cat /proc/mtrr
```

Post the output back here.

---

### Post by Zlap on 2009-08-19
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg02: base=0x0d0000000 ( 3328MB), size=  256MB, count=1: write-combining

Sorry about the lateness man. Here you go.

---

### Post by stoogiebuncho on 2009-08-19
> **Zlap said:**
> reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg02: base=0x0d0000000 ( 3328MB), size=  256MB, count=1: write-combining

Sorry about the lateness man. Here you go.

Well the good news is that this output means you are not affected by the bug I thought you might be.  The bad news is that we'll probably have to do a few more things to figure out what is going on.

First, you should try re-installing your flash plug-in.  The method will depend on how you installed flash in the first place, but if you installed it through Synaptic, all you need to do is this:

```
sudo apt-get update
sudo apt-get purge flashplugin-installer flashplugin-nonfree
sudo apt-get install flashplugin-installer flashplugin-nonfree
```

---

### Post by Zlap on 2009-08-19
ok man do you want to do this by chat or something, or do you wanna just do it through here?

---

### Post by Zlap on 2009-08-19
K did it, and got 0 errors. So im going to restart firefox and see if it worked.

---

### Post by stoogiebuncho on 2009-08-19
I'd prefer to do it here if that's ok with you.  That way it's documented so other people can read it if they have the same problem.

---

### Post by Zlap on 2009-08-19
K i restarted firefox, and now the "other" videos only play stop frame, like if i click where i want it to play from it will only go to that frame and stop and on youtube the videos play fine but once again with no audio. Any suggestions?

---

### Post by Zlap on 2009-08-19
Deleted as i said in next post..

---

### Post by Zlap on 2009-08-19
I understand man, it would be better for the community in general if we do it here. Ok cool =P


BTW, i don't remember how exactly i got it installed the first time, Horrible memory. But i can post the results of the commands you gave me:

> zlap@zlap-laptop:~$ sudo apt-get update
[sudo] password for zlap: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US           
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg [189B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg [189B]  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release [49.6kB]    
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release.gpg               
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Translation-en_US    
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release [49.6kB]      
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release                             
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                       
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages [69.9kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages [136kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages [2589B]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources [41.7kB]    
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages [2391B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources [20.4kB]        
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources [522B]    
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages [26.8kB]   
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources [623B]   
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages [46.0kB]  
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources [13.9kB]   
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages [4968B] 
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources [1661B]  
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources [6577B]     
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages [1662B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources [588B]
Fetched 476kB in 3s (129kB/s)  
Reading package lists... Done
zlap@zlap-laptop:~$ sudo apt-get purge flashplugin-installer flashplugin-nonfreeReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  flashplugin-installer* flashplugin-nonfree*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 221kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 127513 files and directories currently installed.)
Removing flashplugin-nonfree ...
Removing flashplugin-installer ...
Purging configuration files for flashplugin-installer ...
zlap@zlap-laptop:~$ sudo apt-get install flashplugin-installer flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer flashplugin-nonfree
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/21.1kB of archives.
After this operation, 221kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-installer.
(Reading database ... 127501 files and directories currently installed.)
Unpacking flashplugin-installer (from .../flashplugin-installer_10.0.32.18ubuntu0.9.04.1_i386.deb) ...
Selecting previously deselected package flashplugin-nonfree.
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.0.32.18ubuntu0.9.04.1_i386.deb) ...
Setting up flashplugin-installer (10.0.32.18ubuntu0.9.04.1) ...
Downloading...
--2009-08-18 21:37:34--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.32.18.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.32.18.orig.tar.gz)
Resolving archive.canonical.com... 91.189.90.142
Connecting to archive.canonical.com|91.189.90.142|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4023856 (3.8M) [application/x-gzip]
Saving to: `./adobe-flashplugin_10.0.32.18.orig.tar.gz'

     0K .......... .......... .......... .......... ..........  1% 77.9K 50s
    50K .......... .......... .......... .......... ..........  2%  279K 31s
   100K .......... .......... .......... .......... ..........  3%  275K 25s
   150K .......... .......... .......... .......... ..........  5%  436K 21s
   200K .......... .......... .......... .......... ..........  6%  500K 18s
   250K .......... .......... .......... .......... ..........  7%  634K 16s
   300K .......... .......... .......... .......... ..........  8%  606K 14s
   350K .......... .......... .......... .......... .......... 10%  634K 13s
   400K .......... .......... .......... .......... .......... 11%  616K 12s
   450K .......... .......... .......... .......... .......... 12%  637K 11s
   500K .......... .......... .......... .......... .......... 13% 32.8K 19s
   550K .......... .......... .......... .......... .......... 15%  165K 19s
   600K .......... .......... .......... .......... .......... 16%  306K 18s
   650K .......... .......... .......... .......... .......... 17% 1.97M 17s
   700K .......... .......... .......... .......... .......... 19% 5.55M 15s
   750K .......... .......... .......... .......... .......... 20%  253K 15s
   800K .......... .......... .......... .......... .......... 21%  322K 14s
   850K .......... .......... .......... .......... .......... 22%  439K 14s
   900K .......... .......... .......... .......... .......... 24%  622K 13s
   950K .......... .......... .......... .......... .......... 25%  615K 13s
  1000K .......... .......... .......... .......... .......... 26%  634K 12s
  1050K .......... .......... .......... .......... .......... 27%  603K 11s
  1100K .......... .......... .......... .......... .......... 29%  622K 11s
  1150K .......... .......... .......... .......... .......... 30%  625K 10s
  1200K .......... .......... .......... .......... .......... 31%  612K 10s
  1250K .......... .......... .......... .......... .......... 33%  634K 10s
  1300K .......... .......... .......... .......... .......... 34%  619K 9s
  1350K .......... .......... .......... .......... .......... 35%  634K 9s
  1400K .......... .......... .......... .......... .......... 36%  601K 9s
  1450K .......... .......... .......... .......... .......... 38%  624K 8s
  1500K .......... .......... .......... .......... .......... 39%  566K 8s
  1550K .......... .......... .......... .......... .......... 40%  697K 8s
  1600K .......... .......... .......... .......... .......... 41%  334K 7s
  1650K .......... .......... .......... .......... .......... 43%  602K 7s
  1700K .......... .......... .......... .......... .......... 44%  626K 7s
  1750K .......... .......... .......... .......... .......... 45%  102K 7s
  1800K .......... .......... .......... .......... .......... 47% 56.8M 7s
  1850K .......... .......... .......... .......... .......... 48% 57.8M 6s
  1900K .......... .......... .......... .......... .......... 49% 40.7M 6s
  1950K .......... .......... .......... .......... .......... 50% 56.7M 6s
  2000K .......... .......... .......... .......... .......... 52% 49.5M 6s
  2050K .......... .......... .......... .......... .......... 53%  264K 5s
  2100K .......... .......... .......... .......... .......... 54%  277K 5s
  2150K .......... .......... .......... .......... .......... 55%  408K 5s
  2200K .......... .......... .......... .......... .......... 57%  604K 5s
  2250K .......... .......... .......... .......... .......... 58%  445K 5s
  2300K .......... .......... .......... .......... .......... 59%  448K 5s
  2350K .......... .......... .......... .......... .......... 61%  587K 4s
  2400K .......... .......... .......... .......... .......... 62%  470K 4s
  2450K .......... .......... .......... .......... .......... 63%  566K 4s
  2500K .......... .......... .......... .......... .......... 64%  296K 4s
  2550K .......... .......... .......... .......... .......... 66%  331K 4s
  2600K .......... .......... .......... .......... .......... 67%  472K 4s
  2650K .......... .......... .......... .......... .......... 68%  453K 3s
  2700K .......... .......... .......... .......... .......... 69%  617K 3s
  2750K .......... .......... .......... .......... .......... 71%  469K 3s
  2800K .......... .......... .......... .......... .......... 72%  635K 3s
  2850K .......... .......... .......... .......... .......... 73%  462K 3s
  2900K .......... .......... .......... .......... .......... 75%  507K 3s
  2950K .......... .......... .......... .......... .......... 76%  517K 3s
  3000K .......... .......... .......... .......... .......... 77%  330K 2s
  3050K .......... .......... .......... .......... .......... 78%  451K 2s
  3100K .......... .......... .......... .......... .......... 80%  519K 2s
  3150K .......... .......... .......... .......... .......... 81%  498K 2s
  3200K .......... .......... .......... .......... .......... 82%  587K 2s
  3250K .......... .......... .......... .......... .......... 83%  515K 2s
  3300K .......... .......... .......... .......... .......... 85%  568K 2s
  3350K .......... .......... .......... .......... .......... 86%  514K 1s
  3400K .......... .......... .......... .......... .......... 87%  582K 1s
  3450K .......... .......... .......... .......... .......... 89%  528K 1s
  3500K .......... .......... .......... .......... .......... 90%  577K 1s
  3550K .......... .......... .......... .......... .......... 91%  561K 1s
  3600K .......... .......... .......... .......... .......... 92%  540K 1s
  3650K .......... .......... .......... .......... .......... 94%  598K 1s
  3700K .......... .......... .......... .......... .......... 95%  331K 0s
  3750K .......... .......... .......... .......... .......... 96%  219K 0s
  3800K .......... .......... .......... .......... .......... 97%  353K 0s
  3850K .......... .......... .......... .......... .......... 99%  631K 0s
  3900K .......... .......... .........                       100%  502K=10s

2009-08-18 21:37:49 (384 KB/s) - `./adobe-flashplugin_10.0.32.18.orig.tar.gz' saved [4023856/4023856]

Download done.
Flash Plugin installed.

Setting up flashplugin-nonfree (10.0.32.18ubuntu0.9.04.1) ...
zlap@zlap-laptop:~$ 




---

### Post by stoogiebuncho on 2009-08-19
Just for kicks, open your volume control and make sure that the PCM volume is up as well as the master volume.

My only other suggestion would be to reinstall the pulseaudio package.  If that doesn't work, you may have to wait for someone more knowledgeable to come along.

---

### Post by Zlap on 2009-08-19
K, i checked and it was all the way up along with every other volume control selection. Ok, i am going to check for pulseaudio in Add/Remove. Lemme see.

---

### Post by Zlap on 2009-08-19
There is over 5 packages which one?

---

### Post by stoogiebuncho on 2009-08-19
If pulseaudio is not in Add/Remove, do a search for it in Synaptic Package Manager (System > Administration).  You can right-click on it and choose reinstall and click apply.

---

### Post by stoogiebuncho on 2009-08-19
Sounds like you'll have to use synaptic.  It's just called "pulseaudio"

---

### Post by Zlap on 2009-08-19
K, man i re-installed it and restarted firefox. Still no sound, any ideas??????

---

### Post by stoogiebuncho on 2009-08-19
Sorry, that was my last idea.  Hopefully someone else knows more than I do.

---

### Post by Zlap on 2009-08-19
So anyone have an idea, i really enjoy using ubuntu and i would perfer not to switch OS's because if i cant watch or listen to the internet not much point in running Ubuntu.

---

### Post by Zlap on 2009-08-19
K,  now i forgot to say, but now VLC doesn't play audio. So im guessing by now i should just call quits lolz. Anyone know of a OS, like Ubuntu but like works a lot better?

---

### Post by stoogiebuncho on 2009-08-19
If you're thinking of trying another distro, you might give Linux Mint a shot.  It's based on Ubuntu (which is based on Debian) but it has a lot more set up out of the box, so there's less fiddling for you to do.

Good luck.

---

### Post by utnubuuser on 2009-08-19
Try:> [http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html]("http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html")

---

### Post by Zlap on 2009-08-19
You guys will not believe this, i was running my battery low and it died, so when i plugged it back into my computer amazingly, it worked 100% sound & video on youtube + sound and video on "Other" videos so... but this is how it worked in the first place then magically it messed up. I guess if it ever messes up again i will fix using this. Small price to pay for a non windows OS. Amazingly we only have 3 options in Os's. Weird huh, we are so far in technical world yet all we have is 3 os's to choose from.

---

