---
title: "Going Real Slow!"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by Lukehluke on 2009-01-27
Hi,

I installed Ubuntu as my only OS.
It starts up fast'ish when I start up the computer but after 10 - 30 mins it starts to slow down.

For example it freezes youtube etc vids for a few secs and then plays them for a min then freezes them etc.

It takes ages to switch tabs, sometimes it even slows down so much that it takes 20 secs to move the mouse a little bit across the screen.

Comp Info:
Pent 4 3Ghz.
250 GB HD.
512MB RAM.
ATI Radeon 300SE.

---

### Post by mikewhatever on 2009-01-27
Go to applications-accessories-terminal, get the output of <ps -aux> and post it here.

---

### Post by Lukehluke on 2009-01-28
How do I get that?
What command?

---

### Post by HotShotDJ on 2009-01-28
> **Lukehluke said:**
> How do I get that?
What command?Just open a terminal (Applications --> Accessories --> Terminal) and type the following:```
ps -aux
```

---

### Post by Lukehluke on 2009-01-28
This is what I get:

```
ERROR: Garbage option.
********* simple selection *********  ********* selection by list *********
-A all processes                      -C by command name
-N negate selection                   -G by real group ID (supports names)
-a all w/ tty except session leaders  -U by real user ID (supports names)
-d all except session leaders         -g by session OR by effective group name
-e all processes                      -p by process ID
T  all processes on this terminal     -s processes in the sessions given
a  all w/ tty, including other users  -t by tty
g  OBSOLETE -- DO NOT USE             -u by effective user ID (supports names)
r  only running processes             U  processes for specified users
x  processes w/o controlling ttys     t  by tty
*********** output format **********  *********** long options ***********
-o,o user-defined  -f full            --Group --User --pid --cols --ppid
-j,j job control   s  signal          --group --user --sid --rows --info
-O,O preloaded -o  v  virtual memory  --cumulative --format --deselect
-l,l long          u  user-oriented   --sort --tty --forest --version
-F   extra full    X  registers       --heading --no-heading --context
                    ********* misc options *********
-V,V  show version      L  list format codes  f  ASCII art forest
-m,m,-L,-T,H  threads   S  children in sum    -y change -l format
-M,Z  security data     c  true command name  -c scheduling class
-w,w  wide output       n  numeric WCHAN,UID  -H process hierarchy
```

---

### Post by HotShotDJ on 2009-01-28
> **Lukehluke said:**
> This is what I get:

```
ERROR: Garbage option
```Since you left off the part that shows us exactly what you typed, I can't possibly know why you got that output.  I suspect you didn't type EXACTLY the command I showed you. (just to be sure, I copied and pasted the command from my last post just in case I typed the command poorly.  It worked as it should.)  Try again.  If it still gives you that error, please include the line that you typed in your output.

---

### Post by sdennie on 2009-01-28
The output of the following command might be useful:

```

free -m

```

---

### Post by Lukehluke on 2009-01-28
It was working fine to start with but it has crashed twice in the last 30 mins; and I had to do a hard shut down.

I tried the ps -aux but the first time I couldn't even get to the terminal, it was going that slow.

But the second time I got to the terminal but it completely froze after I typed in the command and pressed enter.

It randomly dims the screen even though all the power settings are set to never and screensaver is set to 1 hour.

---

### Post by Lukehluke on 2009-01-29
Any ideas on this issue?

Anything else I can try?

---

### Post by mikewhatever on 2009-01-30
Try ps -A instead of ps -aux. If the two don't work, try looking under system->Admin->system processes, perhaps one of the processes is using an excessive amount of resources.

---

### Post by PreviousN on 2009-01-30
First of all, there are several things that could be slowing down your computer:

1) An application is encountering a bug, and eating all of your cpu cycles.
2) You have too many applications open, causing your computer to run out of ram.
3) A physical problem (such as a dying hard drive), may be the cause of the problem.

The command that the former posts are asking you to run (ps aux) will produce an output of all running applications/processes, the user, the % of cpu usage, the % of memory use, and finally the process name. The output is useful in finding out which process/program is running amok.This is not the only tool for that, however... 

There are several things that I would suggest. First, and foremost, everyone forgets this, but linux comes to a grinding hault when there is not enough hard drive space. I would suggest you check how much space you have on the hard drive. If it is less than 200Megabytes, you may try to free up space. Second, you may try running the command that others have suggested (ps aux). If you do that and post the output here, we all can see what exactly is taking up so much cpu cycles. 

Thirdly, try running this command in the terminal (applications --> accessories --> terminal) "top". 
```
previousn@flipper:~$ top 
```

Top produces an output of processes in a similar fashion to ps aux. I, however, find ps aux unwieldy, since it produces SO much output. If you run top, you can find the application that is running amok by looking at the top process, which indicates the program taking up the most % of your cpu. After finding that program, enter this command in the terminal:

```
previousn@flipper:~$ sudo killall [program that is taking up resources]
```

If after "killing the process" your computer speeds up, then we are good to go (ie: we know the process that is causing you trouble, and we know that if we prevent it from running your computer will not slow down). If, however, your computer remains slow, then we can consider alternatives.

Alternatives would include increasing your "swap" partition. More on that later if the above doesn't work.

---

### Post by DavidFourer on 2009-02-04
> **PreviousN said:**
> First of all, there are several things that could be slowing down your computer:

Thirdly, try running this command in the terminal (applications --> accessories --> terminal) "top". 
```
previousn@flipper:~$ top 
```


***Edit*** The OS is trying to fix itself.  I rebooted this morning and it works fine.  We'll see if there are any more problems.

If this thread is still going, I'd like to get in on it.  8.10 graphics is real slow, and it's not Firefox.  Windows open and close slowly an video is hopeless.  And I think it was fast right after the upgrade from 8.04, a week ago.  I liked your explanatory post.  Here's some info I've collected.

Dell inspiron notebook 6000 with 1 gig ram
Free memory hard drive--26 GB out of 40
Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
System monitor reports excessive CPU activity from sys, was 3% a few days ago and now more like 50% when idle.  Strangely, System monitor is the process using 50% of resources.  Everything else is near zero.

> david@davidf:~$ top

top - 16:15:19 up  2:30,  2 users,  load average: 0.76, 0.57, 0.51
Tasks: 115 total,   1 running, 114 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.3%us,  0.7%sy,  0.0%ni, 98.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1025280k total,   656440k used,   368840k free,    27640k buffers
Swap:        0k total,        0k used,        0k free,   277204k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND               
 5466 root      20   0  356m  17m 8092 S  2.6  1.8   5:53.08 Xorg                  
 8599 david     20   0  2416 1148  884 R  0.7  0.1   0:01.12 top                   
 8378 david     20   0  166m  50m  21m S  0.3  5.0   0:44.15 firefox               
    1 root      20   0  3056 1884  564 S  0.0  0.2   0:03.74 init                  
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kthreadd              
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0   
"free" run with no windos open except the terminal.
Running firefox and a few other apps didn't add much
> david@davidf:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1001        586        414          0         26        269
-/+ buffers/cache:        291        709
Swap:            0          0          0 
The only thing I've done recently is solve a network connection problem.  I dissabled Network Manager and set the IP address.

Thanks

---

### Post by PreviousN on 2009-04-08
So, sorry for the slow reply. Are you still encountering the error? 

The problem with windows opening slowly, with your particular graphics chipset is interesting. From what I understand, the Intel 915 uses shared memory. You may try going to your bios menu and upping the amount of shared memory. Not all bios allow you to do that, however. 

Also, are you running compiz? You could try running metacity, which is ubuntu's desktop environment (thingy...I don't know the technical term for it). Anyways, press "alt F2" and then type "metacity --replace". That will take away all desktop effects like the cube, etc. 

Then, if you're still having issues, it sounds like xorg could be a problem. You may try posting the contents of your xorg.conf file. You'll find it in /etc/X11/xorg.conf 

Good luck.

---

### Post by DavidFourer on 2009-04-08
PreviousN--
Thanks for the note.  Intrepid has been less stable than Hardy, but tolerable.  Hardy was great!  Rebooting, sometimes more than once, fixes a lot of problems.  The really slow business fixed itself after several days and several reboots, and never bothered me again.  Therefore I have not spent any time looking into it.  For all the other little bugs--video, printing, loosing internet connection -- I'm waiting for Jaunty Jackalope.

---

### Post by PreviousN on 2009-04-08
Glad to hear it. From what I remember, hardy was a long term support release. So, naturally they were more conserative with what they included on it with regards to stability. Ibex was kind of a "lets try new things" from what I understand. 

I should have contributed to the community a little bit more, in that I've pretty much only been an end-user since adopting ubuntu. And if I had it my way they would have two releases, like debian. A stable and an unstable. I'd always be running the unstable though, lol. 

I have had many things break between fiesty, gutsy, hardy, and now ibex. The worst breakage I ever experienced was from fiesty to gutsy. It almost seemed like a downgrade. I lost both sound(!) and wireless. My laptop would kernel panic (read: FREEZE) on any connection to a network. Had to recompile alsa from source AND switch to ndiswrapper for my wifi drivers. 

Anyways, I'm also excitedly waiting for Jaunty but I'm doing so with some anxiety.  

With that said, what's this about your problems with video, printing, and losing internet connection? 

I used to have my wifi drop randomly. It was a bug with the network manager applet and my particular wireless card (rt8185/7). I switched to wicd and never get a dropped connection. You may consider trying it, even though the interface is pretty terrible (at least I think so): [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

About your video problems... please elaborate, I might have seen it before. Or, you can wait tille the 23(?) and see if the next release fixes everything.

---

### Post by DavidFourer on 2009-04-10
> **PreviousN said:**
> With that said, what's this about your problems with video, printing, and losing internet connection? 

About your video problems... please elaborate, I might have seen it before. Or, you can wait tille the 23(?) and see if the next release fixes everything.


I'll start by saying that I'm handicapped by having a poor memory for computer jargan.  I learned computer programming 15 years ago, but had to keep a thousand notes because I couldn't keep any syntax in my head (Basic, C, Java).  It was very interesting but I gave up that hobby.  Now I'm sure my memory is worse.  I keep text files on my desktop with notes on every Linux fix, in case I have to refer to it.  Of course if I did something a year ago, I wouldn't expect to remember it.

I did the upgrade to Intrepid in mid-winter and I got kernal version 2.6.27-11-generic.  I read that this has problems.

Network-manager gave me no connection.  I turned it off permanently (thread here: [http://ubuntuforums.org/showthread.php?p=6669744#post6669744](http://ubuntuforums.org/showthread.php?p=6669744#post6669744)).  I've heard of wicd.  One thing about adding different components, when I upgrade to Jaunty, does it go back to standard?  As for wireless, I never got ndiswrapper to work for the Broadcom, and now there is a native driver for the Broadcom wireless.  Rarely get it working though.  Since I leave the computer on my desk, I don't worry about it any more.  The networking interfaces really confuse me--probably because they don't work.

I only know how to install software from the repos.  Can't remember how to download a file and install it.  I never learned how to compile source and install on Linux, even though I use to compile my own code.

Firefox 3 has become a little buggy, but it's hard to pin down.  It starts to limp, and then it hangs!  Multi-media is always suspect.

My Epson printer driver/interface does not work right/crashes but it's usable for my simple needs.  A forum reader with same printer says that Jaunty beta fixes that.

The xsane scanner software had been a technical marvel.  Now the interface is crashing but usable.  I actually used apport and reported to launchpad!

video--ugg.  There must be a hundred different things--Shockwave, Flash, Totem, Windows Media Player, Mplayer, Quicktime, Realplayer, gzine.  I don't know anything about it.  Usually it works in Firefox as long as a web site is not using Microsoft Silverlight.  I recently installed the ubuntu-restricted-extras.  Have no idea what that acomplished.  I watch a DVD once a week.  Movie Player totally crashes,  GNOME Mplayer and gzine are OK but fast-forward and backward don't seem to work, and it's buggy.  I can watch all the way through if I don't mess with anything.

Can't remember what else.

Forums is pretty much where I learn everything.  No one in Chicago I know has Linux.  I really do hope Linux reaches the tipping point in home computers.  I Just wanted to get rid of Windows.  I bought this computer 3.5 years ago (Dell Inspiron 6000 notebook) and it was loaded with what I call Ad-ware.  Teasers to buy junk-ware.  When I learned that I was suppose to spend $79 for a spell-checker, I got Linux.

This computer is getting old.

---David

---

### Post by PreviousN on 2009-04-11
Hmm. It sounds like you're having a linux nightmare lol. The good news is that things are getting better all the time. 

If you are planning on upgrading to Jaunty anyways, it's only a few weeks away and may solve your network manager problems, especially if there are newly created native drivers for your broadcom wireless card. I know I couldn't stand it if my wireless didn't work. 

I would suggest upgrading to Jaunty when it comes out, and if that doesn't fix your network issues, try wicd. It's simple to install. Just add a line to your sources list (System --> Administration --> Software Sources). And run "sudo apt-get install wicd" in a terminal.  

I wouldn't suggest compiling much from source if you aren't confident about it. Its easy to do (you only really run three commands - ./configure, make, make install). But in general its difficult to keep things up-to-date. Installing via ubuntu's apt-get takes care of upgrades. 

I'm sorry to hear about firefox 3 slowing down on you. You may try "swiftfox." It's a stripped down version of firefox that you can install via add/remove software or via terminal. 

Also, if you want to speed up your computer you may try using xubuntu. It's slightly more ugly, but it requires fewer resources and you'll notice a speed improvement. 

It sounds like Jaunty will fix your printer issues. That's good news. More reason to wait and upgrade when it comes out soon. 

About video: It really depends on what you prefer as a default video player. I personally don't like totem. I'm a VLC player fan all the way. And when that doesn't work I fall back to media player classic. But you were right to install the restricted-extras. Video on ubuntu without that (barring using VLC Player) is a real pain. 

About no one in chicago using linux, there are several linux user groups: [http://www.chicagolug.org/](http://www.chicagolug.org/)

Ubuntu may even have a specific group in chicago. I'm not involved in any linux user group, but from what I understand they are fun to belong to. Parties when they release a new version, community support for problems and advice, and in general they are just cool people. 

I applaud you being able to rid yourself of windows completely, that's a hard step that I haven't even been able to take. Free is way better :-).

---

### Post by EndorphinE on 2009-04-18
I have the same issue with memory usage. Here is the outs for the commands:

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          1001        948         52          0         20        541
-/+ buffers/cache:        387        614
Swap:         1427          4       1422

```
```

$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   3056  1896 ?        Ss   14:02   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   14:02   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   14:02   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   14:02   0:05 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   14:02   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   14:02   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S<   14:02   0:00 [khelper]
root        46  0.0  0.0      0     0 ?        S<   14:02   0:00 [kintegrityd/0]
root        48  0.0  0.0      0     0 ?        S<   14:02   0:02 [kblockd/0]
root        50  0.0  0.0      0     0 ?        S<   14:02   0:00 [kacpid]
root        51  0.0  0.0      0     0 ?        S<   14:02   0:00 [kacpi_notify]
root       118  0.0  0.0      0     0 ?        S<   14:02   0:00 [cqueue]
root       122  0.0  0.0      0     0 ?        S<   14:02   0:00 [kseriod]
root       159  0.0  0.0      0     0 ?        S    14:02   0:00 [pdflush]
root       160  0.0  0.0      0     0 ?        S    14:02   0:00 [pdflush]
root       161  0.0  0.0      0     0 ?        S<   14:02   0:02 [kswapd0]
root       201  0.0  0.0      0     0 ?        S<   14:02   0:00 [aio/0]
root      1211  0.0  0.0      0     0 ?        S<   14:02   0:00 [ksuspend_usbd]
root      1214  0.0  0.0      0     0 ?        S<   14:02   0:00 [khubd]
root      1240  0.0  0.0      0     0 ?        S<   14:02   0:00 [ata/0]
root      1242  0.0  0.0      0     0 ?        S<   14:02   0:00 [ata_aux]
root      1334  0.0  0.0      0     0 ?        S<   14:02   0:00 [scsi_eh_0]
root      1336  0.0  0.0      0     0 ?        S<   14:02   0:00 [scsi_eh_1]
root      2063  0.0  0.0      0     0 ?        S<   14:02   0:00 [kjournald]
root      2238  0.0  0.1   2656  1148 ?        S<s  14:02   0:00 /sbin/udevd --daemon
root      2482  0.0  0.0      0     0 ?        S<   14:02   0:00 [kpsmoused]
root      3665  0.0  0.0      0     0 ?        S<   14:02   0:00 [kjournald]
root      3669  0.0  0.1   3904  1040 ?        Ss   14:02   0:00 /sbin/mount.ntfs-3g /dev/sda1 /media/system -o rw,locale=ru_RU.UTF-8
root      3968  0.0  0.0   1780   524 tty4     Ss+  14:02   0:00 /sbin/getty 38400 tty4
root      3969  0.0  0.0   1780   524 tty5     Ss+  14:02   0:00 /sbin/getty 38400 tty5
root      3978  0.0  0.0   1780   528 tty2     Ss+  14:02   0:00 /sbin/getty 38400 tty2
root      3981  0.0  0.0   1780   524 tty3     Ss+  14:02   0:00 /sbin/getty 38400 tty3
root      3983  0.0  0.0   1780   524 tty6     Ss+  14:02   0:00 /sbin/getty 38400 tty6
root      4153  0.0  0.1   2308  1220 ?        Ss   14:02   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      4200  0.0  0.0      0     0 ?        S<   14:02   0:00 [kondemand/0]
syslog    4273  0.0  0.0   2012   712 ?        Ss   14:02   0:00 /sbin/syslogd -u syslog
root      4326  0.0  0.0   1940   540 ?        S    14:02   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4328  0.0  0.2   3372  2192 ?        Ss   14:02   0:00 /sbin/klogd -P /var/run/klogd/kmsg
108       4359  0.0  0.1   2952  1156 ?        Ss   14:02   0:00 /bin/dbus-daemon --system
avahi     4381  0.0  0.1   2888  1448 ?        Ss   14:02   0:00 avahi-daemon: running [gfl-1206.local]
avahi     4382  0.0  0.0   2888   496 ?        Ss   14:02   0:00 avahi-daemon: chroot helper
root      4410  0.0  0.1   5400  1028 ?        Ss   14:02   0:00 /usr/sbin/sshd
root      4457  0.0  0.2   6412  2340 ?        Ss   14:02   0:00 /usr/sbin/cupsd
root      4476  0.0  0.0   1996   520 ?        Ss   14:02   0:00 /usr/sbin/gpm -m /dev/input/mice -t exps2
lastfm    4499  0.0  0.3   7460  3952 ?        Ss   14:02   0:00 /usr/bin/python /usr/bin/lastfmsubmitd
root      4554  0.0  0.1   7156  1612 ?        Ss   14:02   0:01 /usr/sbin/nmbd -D
root      4556  0.0  0.2  12612  2840 ?        Ss   14:02   0:00 /usr/sbin/smbd -D
root      4577  0.0  0.1  12612  1104 ?        S    14:02   0:00 /usr/sbin/smbd -D
root      4578  0.0  0.1   9204  1472 ?        Ss   14:02   0:00 /usr/sbin/winbindd
root      4586  0.0  0.1   9332  1636 ?        S    14:02   0:00 /usr/sbin/winbindd
root      4588  0.0  0.0   2756   568 ?        Ss   14:02   0:00 /usr/sbin/zvbid
111       4615  0.0  0.4   6332  4180 ?        Ss   14:02   0:01 /usr/sbin/hald
root      4618  0.0  0.2  16388  2572 ?        Ssl  14:02   0:00 /usr/sbin/console-kit-daemon
root      4681  0.0  0.1   3364  1116 ?        S    14:02   0:00 hald-runner
root      4701  0.0  0.1   3436  1048 ?        S    14:02   0:00 hald-addon-input: Listening on /dev/input/event3 /dev/input/event2 /dev/input/event1
111       4707  0.0  0.0   2296   896 ?        S    14:02   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      4761  0.0  0.2  14636  2492 ?        Ssl  14:02   0:00 /usr/sbin/NetworkManager
root      4766  0.0  0.1   4244  1328 ?        S    14:02   0:00 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log
root      4769  0.0  0.3   7696  3800 ?        S    14:02   0:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
root      4799  0.0  0.1  14240  1768 ?        Ss   14:02   0:00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
root      4802  0.0  0.3  14776  3212 ?        S    14:02   0:00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
root      4806 22.5  4.5  59340 46484 tty7     Rs+  14:02  36:10 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      4822  0.0  0.1   4336  1152 ?        Ss   14:02   0:00 /usr/bin/system-tools-backends
daemon    4877  0.0  0.0   2068   456 ?        Ss   14:02   0:00 /usr/sbin/atd
root      4907  0.0  0.1   3412  1032 ?        Ss   14:02   0:00 /usr/sbin/cron
root      4923  0.0  0.0   2252   952 ?        S    14:02   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-et
root      4992  0.0  0.0   1780   524 tty1     Ss+  14:02   0:00 /sbin/getty 38400 tty1
falcon    5625  0.0  0.2  14700  2188 ?        S    14:18   0:00 /usr/bin/gnome-keyring-daemon -d --login
falcon    5635  0.1  0.9  16184 10236 ?        Ss   14:18   0:09 /usr/bin/openbox
falcon    5692  0.0  0.0   3124   672 ?        S    14:18   0:00 /usr/bin/dbus-launch --exit-with-session openbox-session
falcon    5693  0.0  0.1   2904  1092 ?        Ss   14:18   0:01 //bin/dbus-daemon --fork --print-pid 6 --print-address 9 --session
falcon    5699  0.0  0.4   7872  4832 ?        S    14:18   0:01 /usr/lib/libgconf2-4/gconfd-2
falcon    5701  0.0  0.2   5552  2088 ?        S    14:18   0:00 /usr/lib/gvfs/gvfsd
falcon    5707  0.0  0.1  29196  2036 ?        Ssl  14:18   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/falcon/.gvfs
falcon    5739  0.3  2.8  55656 29024 ?        S    14:18   0:32 gnome-panel
falcon    5741  0.0  0.3  40636  3472 ?        Ssl  14:18   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=16
falcon    5747  0.0  1.2  27800 12340 ?        S    14:18   0:02 /usr/lib/gnome-applets/gnome-keyboard-applet --oaf-activate-iid=OAFIID:GNOME_KeyboardApplet_
falcon    5750  0.0  1.5  40924 16212 ?        S    14:18   0:01 /usr/lib/gnome-applets/gweather-applet-2 --oaf-activate-iid=OAFIID:GNOME_GWeatherApplet_Fact
falcon    5753  0.0  0.2   5920  2888 ?        S    14:18   0:00 /usr/lib/gvfs/gvfs-hal-volume-monitor
falcon    5755  0.0  0.2   5544  2132 ?        S    14:19   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
falcon    5760  0.0  1.1  24368 12112 ?        S    14:19   0:00 /usr/lib/tsclient/tsclient-applet --oaf-activate-iid=OAFIID:GNOME_TSClientApplet_Factory --o
falcon    5763  0.0  1.5  51080 16264 ?        Sl   14:19   0:01 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --o
falcon    5766  0.0  2.3  43204 24232 ?        S    14:19   0:03 python /usr/lib/glipper/glipper --oaf-activate-iid=OAFIID:Glipper_Factory --oaf-ior-fd=34
falcon    5768  0.4  1.4  28716 15036 ?        S    14:19   0:37 xfce4-panel
falcon    5769  0.0  0.8  22560  8540 ?        S    14:19   0:00 /usr/lib/thunar/xfce4/panel-plugins/thunar-tpa socket_id 25165877 name thunar-tpa id 4 displ
falcon    5771  0.0  0.5  23812  5492 ?        Sl   14:19   0:00 /usr/bin/Thunar --daemon
falcon    5773  0.0  0.1   2992  1152 ?        S    14:19   0:00 /usr/lib/gamin/gam_server
falcon    5949  3.3  0.4  31004  4928 ?        Sl   14:22   4:41 /usr/bin/pulseaudio --log-target=syslog
falcon    5953  0.0  0.2   7532  2500 ?        S    14:22   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
falcon    5967  0.3  0.6  21716  6380 ?        Ss   14:22   0:30 gnome-screensaver
falcon    5992  1.6  6.3 110656 65460 ?        Sl   14:24   2:19 /usr/lib/opera/9.64/opera
root      6039  0.0  0.0      0     0 ?        S<   14:26   0:00 [scsi_eh_2]
root      6040  0.1  0.0      0     0 ?        S<   14:26   0:14 [usb-storage]
root      6093  0.0  0.1   3440  1056 ?        S    14:26   0:00 hald-addon-storage: polling /dev/sdb (every 2 sec)
root      6551  0.0  0.0   9204  1004 ?        S    14:58   0:00 /usr/sbin/winbindd
root      6552  0.0  0.1   9284  1504 ?        S    14:58   0:00 /usr/sbin/winbindd
root      6657  0.0  0.2  12632  3012 ?        S    15:00   0:00 /usr/sbin/smbd -D
root      6658  0.0  0.3  12656  3148 ?        S    15:00   0:00 /usr/sbin/smbd -D
root      6664  0.0  0.2  12632  3020 ?        S    15:01   0:00 /usr/sbin/smbd -D
root      6666  1.4  0.3  12656  3292 ?        S    15:02   1:28 /usr/sbin/smbd -D
falcon    6804  0.1  2.6  54796 27656 ?        S    15:15   0:07 /usr/bin/gedit
falcon    8569  0.7  3.0  91980 30920 ?        Sl   16:33   0:04 /usr/bin/python /usr/bin/terminator
falcon    8572  0.0  0.0   2912   760 ?        S    16:33   0:00 gnome-pty-helper
falcon    8573  0.0  0.3   6500  3828 pts/1    Ss   16:33   0:00 /bin/bash
falcon    8604 16.7  6.8 195152 70748 ?        Sl   16:34   1:24 /usr/lib/firefox-3.0.8/firefox
falcon    8765  6.7  1.8  93212 19296 ?        Sl   16:40   0:11 /usr/lib/lastfm/last.fm
falcon    8778  0.0  0.0   2744  1008 pts/1    R+   16:43   0:00 ps aux

```

Here is the usage for hard drive:
```

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             5.6G  4.2G  1.1G  80% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  368K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2.7M  498M   1% /dev
tmpfs                 501M  232K  501M   1% /dev/shm
lrm                   501M  2.0M  499M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda8             2.1G  1.1G  902M  54% /home
/dev/sda1              15G  8.7G  6.2G  59% /media/system
/dev/sda5              14G  9.8G  3.8G  73% /media/stuff
/dev/sdb1              15G  8.5G  6.4G  58% /home/falcon/FLASH

```

Please advice what can cause this issue. Thanks in advance.

---

