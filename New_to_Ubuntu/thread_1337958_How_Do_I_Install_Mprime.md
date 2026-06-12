---
title: "How Do I Install Mprime?"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by He's Dead Jim on 2009-11-25
hi everyone..

i am trying to install mprime which is the linux version of the prime95 stress test, and i have no idea how...

i just completed my first successful installation of ubuntu and i need to run this test overnight..

i don't know anything about linux other than the installation, and although i downloaded the free pdf for the pocket guide, i need to set this up in the next half hour and i can't read that fast...lol..

any ideas??

thanks..

---

### Post by Paqman on 2009-11-26
Hmm, looks complicated. Do you actually need this particular app, or will any stress tester do?

---

### Post by He's Dead Jim on 2009-11-26
anything that will stress out the processor and possibly the memory would be great....

thanks...

:)

---

### Post by Paqman on 2009-11-26
BOINC/Seti@home? It's in the repos, and you'd be doing something useful at the same time.

---

### Post by XCan on 2009-11-26
You could also run, for example, Gaussian elimination in linpack in some infinite loops [http://en.wikipedia.org/wiki/LINPACK](http://en.wikipedia.org/wiki/LINPACK) . But BOINC attached to some project must be the easiest way as everything's in the repos.

---

### Post by He's Dead Jim on 2009-11-26
thanks for the quick replies....

i downloaded the boinc program from berkely, but how do i get it to run??

thanks...

---

### Post by MooPi on 2009-11-26
I am currently running Prime95 on a new set-up and installation is not required. Simply download the tarball from [http://mersenneforum.org/gimps/mprime259.tar.gz](http://mersenneforum.org/gimps/mprime259.tar.gz)

Extract the contents to a folder of your choice or create one specifically for Prime95. Navigate to this folder and open a terminal and execute this command "./mprime". 
It should ask you a few questions as to how to torture test your computer and away you go.

[IMG]http://i559.photobucket.com/albums/ss36/MooPii/prime95.png[/IMG]

---

### Post by He's Dead Jim on 2009-11-26
wow, that was super easy...

thanks..

mprime is running nicely now...

what is the linux version of a batch file?

---

### Post by MooPi on 2009-11-26
Now that is a loaded question. Linux scripts or executable text files are a basic function of linux and this is how most of what I do on my computer functions. Learn your basic terminal commands and then read about #!/bin/bash scripting and the world of Linux will open up to you. If you look at the screenshot I provided you can see a broken script on the lower panel. It's the little red X on the lower right hand. Recently updated my Firefox browser and for some reason it broke my desktop script Icon. I will simply open the script with gedit and correct the icon change.
[IMG]http://i559.photobucket.com/albums/ss36/MooPii/scripting.png[/IMG]

---

### Post by Paqman on 2009-11-26
> **He's Dead Jim said:**
> 
i downloaded the boinc program from berkely, but how do i get it to run??


You cooould do it that way, but it's always better to get your software from the repos. Go to System > Admin > Synaptic and browse in wonder at the tens of thousands of packages available for immediate installation!

---

### Post by He's Dead Jim on 2009-11-26
thanks again you two....

looks like this is gonna be a fun ride....

i'm still used to win-doze double click stuff, but if i could quit smoking after 30 years, i can learn linux...

:)

---

### Post by egalvan on 2009-11-26
Go to the phoronix web site and gaze in wonder at the magnificent test suite... :)

[http://www.phoronix.com/scan.php?page=article&item=pts_22_bardu&num=1](http://www.phoronix.com/scan.php?page=article&item=pts_22_bardu&num=1)

It is probably far more than you need.

Sorry Paqman, I couldn't resist... :)

---

### Post by egalvan on 2009-11-26
> **MooPi said:**
> 


MooPi, where did that gorgeous back-ground come from?

---

### Post by He's Dead Jim on 2009-11-26
> **egalvan said:**
> Go to the phoronix web site and gaze in wonder at the magnificent test suite... :)

[http://www.phoronix.com/scan.php?page=article&item=pts_22_bardu&num=1](http://www.phoronix.com/scan.php?page=article&item=pts_22_bardu&num=1)

It is probably far more than you need.

Sorry Paqman, I couldn't resist... :)

good stuff...

i was originally given that link by a friend, but chose mprime because i just need to load down the cpu while i run a 8 or 10 hour latency test.....

thanks much though....

---

### Post by MooPi on 2009-11-26
Thats from the National Geographic. I actually don't like that one much. It just happened to be up when I was responding.
If your looking for a benchmark test that will bench your Mac , Windows and Linux computer try Geekbench from Primate Labs.. It's how I measure mine.

---

### Post by Joel Barnes on 2010-02-11
Does anyone know why this is happening? I haven't had a problem running any other executables, and I had plenty of practice trying to get the ******* lm-sensors working. I've rebooted since downloading it, and I've tried to run the executable in the gui as well - no error, no execution. The readme lists a lot of files not in that dir, but I've downloaded the .gz from a few targets and they are all the same file. And my file list looks like a screenshot someone else posted here. I'm stumped.

[FONT=Courier New]joel@joel-desktop:~/mprime$ ls -l
total 4156
-rw-r--r-- 1 joel joel    2110 2009-03-16 10:22 license.txt
lrwxrwxrwx 1 joel joel      24 2010-02-11 00:41 Link to mprime -> /home/joel/mprime/mprime
-rwxr-xr-x 1 joel joel 4140905 2009-03-16 10:22 mprime
-rw-r--r-- 1 joel joel   23062 2009-03-16 10:22 readme.txt
-rw-r--r-- 1 joel joel    6860 2009-03-16 10:22 stress.txt
-rw-r--r-- 1 joel joel   19768 2009-03-16 10:22 undoc.txt
-rw-r--r-- 1 joel joel   53776 2009-03-16 10:22 whatsnew.txt
joel@joel-desktop:~/mprime$ mprime
No command 'mprime' found, did you mean:
 Command 'prime' from package 'prime' (universe)
mprime: command not found
joel@joel-desktop:~/mprime$ sudo mprime
[sudo] password for joel: 
sudo: mprime: command not found
joel@joel-desktop:~/mprime$ ./mprime
bash: ./mprime: No such file or directory
joel@joel-desktop:~/mprime$ sudo ./mprime
sudo: unable to execute ./mprime: No such file or directory
[/FONT]

---

### Post by Eric K on 2010-02-15
Joel, I'm a bit of a novice myself when it comes to Linux, but let me see if I can help.

First of all, the correct command in this case is would be one of the following: ```
./mprime
./mprime -t
```
The second example is used if you want to go straight to the torture test mode.

Second, the extra files that the readme talks about are temp files that mprime will create while it is running to save the work units in between shutdowns of mprime.

Third, are you sure you got the correct version for your machine?  For example, this isn't a 64-bit executable on a 32-bit version of Ubuntu?

---

### Post by Joel Barnes on 2010-02-23
Yes, the problem was the executable version. I was trying to run the 32-bit on a 64-bit system.

Thanks,
Joel

---

### Post by NX Hades on 2011-05-29
> **Paqman said:**
> You cooould do it that way, but it's always better to get your software from the repos. Go to System > Admin > Synaptic and browse in wonder at the tens of thousands of packages available for immediate installation!

I dunno why folks discourage people from learning anything about the terminal. The learning curve involved is pretty much what separates normal windows users from a typical linux poweruser. 

Seriously, the terminal is the best thing in the world. It's so damned powerful. Having that much control over your software is intoxicating. 

I like using the terminal so much (because it looks pimp to everyone watching you use your computer) that I installed DOSbox for kicks so I could learn new old windows commands (and play non-ported and old games). 

edit: besides, mprime/prime95 is not available on synaptic, at least I couldn't find it

---

### Post by hugecast on 2011-05-30
[FONT=Verdana][SIZE=3]Install and autostart MPrime on Ubuntu 11.04 Natty (Desktop or Server)
with crontab autostart 'bootup script'[/SIZE][/FONT]

After some years I tried again to launch MPrime using the autostart bootup start-script by Gareth Randall, Sun, 12 Nov 2000, originally posted on a mailing list archive, here: [http://www.mail-archive.com/mersenne.../msg05245.html]("http://www.mail-archive.com/mersenne@base.com/msg05245.html") , as I did in former years.

Since I run Ubuntu Natty 11.04 on my [AMD Fusion E-350]("http://en.wikipedia.org/wiki/AMD_Fusion")  computer, [Upstart ]("http://en.wikipedia.org/wiki/Upstart")([http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)) has replaced the former /etc/init.d method. So I got the error message:
> *su*: must be run from a *terminal*when using the startup script by Gareth Randall, see above.

Here's the steps I followed to achieve the installation and bootup / autostart of MPrime on my Ubuntu Natty 11.04 driven PC:
----------------------------------------------------------

0) On the terminal I created the folder /gimps:```
master_and_commander@1stcomputer:~$ mkdir /home/master_and_commander/gimps
```> ### Hints:
# path of mprime-binary in Ubuntu then is:   /home/master_and_commander/gimps/
###1) Downloaded and extracted mprime266-linux64.tar.gz (or whatever the appropriate version is) from [www.mersenne.org]("http://www.mersenne.org/") to the ~/gimps folder.

1st the 64bit variant:
```
master_and_commander@1stcomputer:~$ cd ~/gimps
master_and_commander@1stcomputer:~/gimps$ wget ftp://mersenne.org/gimps/mprime266-linux64.tar.gz
...
    [                                                                 <=>                                ] 4.019.958    372K/s   in 14s      

2011-06-01 21:41:04 (271 KB/s) - »mprime266-linux64.tar.gz« saved [4019958]

master_and_commander@1stcomputer:~/gimps$ tar xzvf mprime266-linux64.tar.gz
license.txt
mprime
readme.txt
stress.txt
undoc.txt
whatsnew.txt
master_and_commander@1stcomputer:~/gimps$

```2nd the 32bit variant:
```
master_and_commander@1stcomputer:~$ cd ~/gimps
master_and_commander@1stcomputer:~/gimps$ wget ftp://mersenne.org/gimps/mprime266.tar.gz
...   
2011-06-01 21:41:04 (271 KB/s) - »mprime266.tar.gz« saved [4019958]

master_and_commander@1stcomputer:~/gimps$ tar xzvf ftp://mersenne.org/gimps/mprime266.tar.gz
license.txt
mprime
readme.txt
stress.txt
undoc.txt
whatsnew.txt
master_and_commander@1stcomputer:~/gimps$

```2) In the terminal changed to this directory and run the ./mprime -m from xterm to set up the preferences by the MPrime menu:```
master_and_commander@1stcomputer:~$ cd  ~/gimps 
master_and_commander@1stcomputer:~/gimps$ ./mprime -m
[Main thread May 30 15:17] Mersenne number primality test program version 26.6
[Main thread May 30 15:17:38] Optimizing for CPU architecture: AMD K8, L2 cache size: 512 KB
         Main Menu

     1.  Test/Primenet
     2.  Test/Worker threads
     3.  Test/Status
     4.  Test/Continue
     5.  Test/Exit
     6.  Advanced/Test
     7.  Advanced/Time
     8.  Advanced/P-1
     9.  Advanced/ECM
    10.  Advanced/Manual Communication
    11.  Advanced/Unreserve Exponent
    12.  Advanced/Quit Gimps
    13.  Options/CPU
    14.  Options/Preferences
    15.  Options/Torture Test
    16.  Options/Benchmark
    17.  Help/About
    18.  Help/About PrimeNet Server
Your choice: 
```3) Now I used cron to have MPrime autorun in the background at start up boottime. See 
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto) 
```
master_and_commander@1stcomputer:~$ cd gimps
master_and_commander@1stcomputer:~/gimps$ crontab -e

Select an editor. To change later, run 'select-editor'.
1. /bin/ed
2. /bin/nano <---- easiest
3. /usr/bin/vim.tiny

Choose 1-3 [2]: _




```Accept [2] with <RETURN>.
You will see the editor "nano" displaying the content of your crontab file:
```
 GNU nano 2.2.6 Datei: /tmp/crontab.2smR8O/crontab



[ read one line ]
^G Help ^O save ^R Open file^Y Page up^K Snipp^C Cursor
^X Close ^J .. ^W Were is^V Page down ^U Snipp r^T Syntax

```Here, directly, type in the following line, save with <Strg-O> and close the editor with <Strg-X>
```
@reboot /home/master_and_commander/gimps/mprime &

```Hints:
"[COLOR=#006600]@reboot[/COLOR]" at every bootup ..
do " /home/master_and_commander/gimps/mprime &", that is in the bash   shell, start mprime program-code "   /home/master_and_commander/gimps/mprime" ..
and run it in the bachground ("[COLOR=#006600]&[/COLOR]") , tht is without any output at stdout (=terminal window).

Otherwise try this command-line:
```
master_and_commander@1stcomputer:~$ echo "@reboot /home/master_und_commander/gimps/mprime & " | crontab -
[sudo] password for master_and_commander:
master_and_commander@1stcomputer:~$ 
```
4) You can edit the MPrime settings by hand / editor. These are my files customed to work with my AMD Fusion '*Zacate*' E-350  platform:
> CPU Information:
AMD E-350 Processor
CPU speed: 1569.06 MHz, 2 cores
CPU features: Prefetch, MMX, SSE, SSE2
L1 cache size: 32 KB
L2 cache size: 512 KB
RAM:
2GB of DDR3-1066 DDR-SDRAM (8.525 GB/s CPU/GPU shared bandwidth)~/gimps/local.txt
> OldCpuSpeed=1569
NewCpuSpeedCount=0
NewCpuSpeed=0
ComputerGUID=[COLOR=Red]*********[/COLOR]
ComputerID=[COLOR=Red]*********[/COLOR]
WorkerThreads=2
ThreadsPerTest=1
Pid=0
SrvrUID=[COLOR=Red]*********[/COLOR]
SrvrComputerName=[COLOR=Red]*********[/COLOR]
SrvrPO1=0
SrvrPO2=1
SrvrPO3=6
SrvrPO4=512
SrvrPO5=768
SrvrPO6=450
SrvrPO7=1410
SrvrPO8=1
SrvrPO9=2
SrvrP00=2
LastEndDatesSent=[COLOR=Red]*********[/COLOR]
RollingHash=[COLOR=Red]*********[/COLOR]
RollingStartTime=0
RollingCompleteTime=[COLOR=Red]*********[/COLOR]
RollingAverage=1000

[Worker #1]
Affinity=0
Memory=512 during 7:30-23:30 else 768

[Worker #2]
Affinity=1
Memory=512 during 7:30-23:30 else 768~/gimps/prime.txt
> V24OptionsConverted=1
WGUID_version=2
StressTester=0
UsePrimenet=1
DialUp=1
V5UserID=[COLOR=Red]*********[/COLOR]
AskedAboutMemory=1
WorkPreference=0
OutputIterations=10000
ResultsFileIterations=999999999
DiskWriteTime=15
NetworkRetryTime=15
NetworkRetryTime2=15
DaysOfWork=6
DaysBetweenCheckins=1
NumBackupFiles=3
SilentVictory=0
AMPM=2
TimingOutput=3
TimeStamp=2
CumulativeTiming=1
BootDelay=180
StaggerStarts=30
SequentialWorkToDo=0
InterimFiles=10000
GmpEcmHook=1
MaxLoad=3.5
MinLoad=2.9
PauseTime=3
UnreserveDays=61

[PrimeNet]
Debug=0
ProxyHost=For further information on my customisations see the 
~/gimps/undoc.txt
> This file lists the undocumented features available in the program.
These features may change or be discontinued at any time.  Their use is
totally unsupported.enjoy =)

-----------
See also these postings:
*  [**MPrime Daemon start-up script**]("http://ubuntuforums.org/showthread.php?t=102160&highlight=mprime") , in this ubuntu forums, from             December 11th, 2005
*  [**[SOLVED] crontabs job**]("http://ubuntuforums.org/showthread.php?t=1640016&highlight=crontab") , in this ubuntu forums.

---

