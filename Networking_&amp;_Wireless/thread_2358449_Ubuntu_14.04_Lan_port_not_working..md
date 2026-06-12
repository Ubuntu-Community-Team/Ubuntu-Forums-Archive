---
title: "Ubuntu 14.04 Lan port not working."
date: 2017-04-13
forum: Networking &amp; Wireless
---

### Post by vladur on 2017-04-13
Hello I've installed ubuntu 14.04 on a gigabyte h81 ms motherboard with i3 2120 and the lan port doesn't work unless I enter (sudo ethtool -s eth0 speed 100 duplex full autoneg off) in terminal after that everything works fine. Is there a way to make this command work automatically on start up? or any other alternative where I don't have to enter the above command everytime I want to use the networking features?  Any and all help is appreciated.

---

### Post by TheFu on 2017-04-13
You can put it into the "post-up" section of the *interfaces* file or add it, without the sudo, to the middle of the /etc/rc.local file.  Really, anywhere above the exit.  The 2nd choice is probably better.  Be certain to completely use the full path to the ethtool command - never trust the PATH in scripts.

When you move to 16.04, beware that eth0 probably will not be the device name.

---

### Post by vladur on 2017-04-14
First of all thanks for the quick reply and sorry for my late reply.  So if enter  (ethtool -s eth0 speed 100 duplex full autoneg off) in the middle of the /etc/rc.local file the lan port on my machine will start working as soon as ubuntu has booted? One more thing what do you mean by "anywhere above the exit". Thanks again.

---

### Post by TheFu on 2017-04-14
Look at the file. It is self explanatory.  Try something. If it works, great. If not, post the file for help.

---

### Post by vladur on 2017-04-15
Ok I edited the [COLOR=#000000]/etc/rc.local file as this 

[/COLOR]#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
# ethtool -s eth0 speed 100 duplex full autoneg off
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

But I still have to enter [COLOR=#000000](sudo ethtool -s eth0 speed 100 duplex full autoneg off) in terminal before the lan port starts working.[/COLOR]

---

### Post by TheFu on 2017-04-15
# is a comment. Remove that.
/sbin/ethtool is what you need to specify. Always use the full path to any programs inside a script.

I would have put the ethtool near the bottom, so it isn't buried in comments.

---

### Post by vladur on 2017-04-16
Okay say if I understand you correctly the file should be like this

#!/sbin/ethtool
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
# ethtool -s eth0 speed 100 duplex full autoneg off
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
  ethtool -s eth0 speed 100 duplex full autoneg off
exit 0
 I'm also giving you a link to my rc local file please have a look at it and do any corrections to it if needed.

---

### Post by TheFu on 2017-04-16
Closer. You should/must specify the full path to the ethtool program, as I've said twice above. Never trust the PATH in a script. rc.local is a script, hence, you should never trust the PATH.  If you don't know what a PATH is, do a little research to gain understanding.

---

### Post by vladur on 2017-04-16
Here' a link to the file [https://drive.google.com/file/d/0Bz7ZhM0jpMpKWkRQYkhLTHRMdGM/view?usp=sharing](https://drive.google.com/file/d/0Bz7ZhM0jpMpKWkRQYkhLTHRMdGM/view?usp=sharing)
please edit it so that the lan starts working automatically on boot.

---

### Post by chili555 on 2017-04-16
> **vladur said:**
> Here' a link to the file [https://drive.google.com/file/d/0Bz7ZhM0jpMpKWkRQYkhLTHRMdGM/view?usp=sharing](https://drive.google.com/file/d/0Bz7ZhM0jpMpKWkRQYkhLTHRMdGM/view?usp=sharing)
please edit it so that the lan starts working automatically on boot.That's not necessary. You had it almost right here:```
#!/sbin/ethtool
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
# ethtool -s eth0 speed 100 duplex full autoneg off
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
ethtool -s eth0 speed 100 duplex full autoneg off
exit 0
```TheFu suggests, and I quite agree, that it be amended to:```
#!/sbin/ethtool
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
# ethtool -s eth0 speed 100 duplex full autoneg off
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
[COLOR="#FF0000"]/sbin/[/COLOR]ethtool -s eth0 speed 100 duplex full autoneg off
exit 0
```Proofread carefully, save and close the text editor and reboot.

Is your ethernet now working as expected?

---

### Post by vladur on 2017-04-16
Ok I will try it and hopefully it'll work. The system I'm having issues with is at the place I work.

---

### Post by TheFu on 2017-04-16
> **vladur said:**
> Ok I will try it and hopefully it'll work. The system I'm having issues with is at the place I work.

I have a personal stance on doing work for others.  That's $150/hr with a 1,000 hr minimal contract.

OTOH, I will spend weeks here trying to help YOU learn to do it for yourself for $0. I'd like to improve.  Besides just handing the answer, how could I have been more helpful?

BTW, the ethtool method is very common with GigE cable NICs on 10/100 networks and likely to have solved the issue. But, if it doesn't, we can probably figure it out.

---

### Post by vladur on 2017-04-17
I'm still not able to get the lan port to work automatically on start up. The lan port works completely  fine in windows 7 pro 64bit. Please give me a list of possible solutions to my problem.

---

### Post by TheFu on 2017-04-17
It appears we don't know the root cause of the issue, so guessing at solutions isn't possible.  Need data and facts first.  Best to post all data you have, being careful NOT to interpret that data.  Misinterpretation is where this stuff usually fails.

Show both the command being run AND the output from it.

First, is the rc.local file actually running?  Prove that. If you run **ethtool eth0**, we should see the settings without change. Then run the command above to see the settings change, followed by running the **ethtool eth0** cmd to see that the changes stuck.  In theory, these changes should show up in the system log files somewhere. 

We are assuming that the first post which claimed running the ethtool cmd from a shell worked.  Please prove that is works still.

It would also help to know the exact NIC and the driver being used.  **sudo lshw -C network** will provide that data.  Then I'd check that the driver shown and the NIC chip used are known to work together - use google with the NIC, ubuntu, and the specific driver in the query.  Read about 10 of those results. If there are lots and lots of results, add 14.04 to the query to pair it down.

If you just need this solved and throwing a little money at the problem is acceptable, buy an Intel PRO/1000 NIC and install it. Disable whatever NIC this is via the BIOS.

The fact that it works with Windows isn't necessarily good.  There have been reports of the Windows drivers modifying the EEPROM with broken settings for some NICs.  MS-Windows ignores those broken settings, but ever other OS doesn't. Sometimes Windows doesn't leave the NIC properly shutdown, so a hot-reboot doesn't clear prior settings.  A cold reboot is necessary.
Then there are cards reported to need initialization by the Windows driver, followed by a hot-restart into Linux to get them working correctly.  I've never personally seen or owned any NICs that required either of these methods to work, but I've seen both methods claimed to be a fix on reputable sites.  The google results would lead my efforts with these methods.

---

### Post by vladur on 2017-04-17
Unfortunately gigabte h61ms doesn't have a pci slot as installing a NIC was the first thing I tried when I realized that the lan port isn't functioning in ubuntu. Right now I have 2 systems that are having lan port issues which have ubuntu installed on them the other system's lan port is working fine now after applying one of the potential solutions provided in this thread which is editing the rc.local file as this -
   [FONT=&quot]
#!/bin/sh -e[/FONT]

  [FONT=&quot]#[/FONT]
  [FONT=&quot]# rc.local[/FONT]
  [FONT=&quot]#[/FONT]
  [FONT=&quot]# This script is executed at the end of each multiuser runlevel.[/FONT]
  [FONT=&quot]# Make sure that the script will "exit 0" on success or any other[/FONT]
  [FONT=&quot]# value on error.[/FONT]
  [FONT=&quot]#[/FONT]
  [FONT=&quot]# In order to enable or disable this script just change the execution[/FONT]
  [FONT=&quot]# bits.[/FONT]
  [FONT=&quot]#[/FONT]
  [FONT=&quot]# By default this script does nothing.[/FONT]
  [FONT=&quot]/sbin/ethtool -s eth0 speed 100 duplex full autoneg off[/FONT]
  [FONT=&quot]exit 0

But editing the file in the exact same way doesn't seems to work on the h61m system.
Right now the h61m system isn't present but I will run the commands which you have asked in the above post and submit the results soon.

Once again appreciate all the help and support provided by you and others in this thread.
[/FONT]

---

### Post by vladur on 2017-04-18
Please take a look at the below screenshots.

[IMG]http://i65.tinypic.com/jtupg1.png[/IMG][IMG]http://i64.tinypic.com/zt9lzr.png[/IMG][IMG]http://i66.tinypic.com/14y1rwm.png[/IMG][IMG]http://i65.tinypic.com/2m63chs.png[/IMG]

---

### Post by TheFu on 2017-04-18
the lshw (most important) is cut off.
BTW, please don't post images. They are extremely wasteful for low-bandwidth people.
Redirect the output to a file and move the file off to be copy/pasted into a message here. 'code tags' highly appreciated, so things line up.

**sudo lshw -C network > /tmp/file.lst**

---

### Post by raccoonstrait on 2017-04-18
[COLOR=#000000]Not sure if you have the same issue as I did, but there is a bug out there. See response #2 on this thread, it solved my issue.[/COLOR]

[https://ubuntuforums.org/showthread.php?t=2358631](https://ubuntuforums.org/showthread.php?t=2358631)

[COLOR=#000000]RaccoonStrait[/COLOR]

---

### Post by vladur on 2017-04-19
Doing a complete format of the system and  installing ubuntu 14.04 in single boot mode has seemed to fix my issue.

Thanks again everyone for your support and suggestions.

---

