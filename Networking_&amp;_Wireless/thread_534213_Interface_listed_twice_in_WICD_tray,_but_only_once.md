---
title: "Interface listed twice in WICD tray, but only once in iwlist scan?"
date: 2007-08-24
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-08-24
First Im not having a problem connecting or with my connection, just having a strange problem with the WICD tray.py application.  It is showling my wireless LAN twice, telling me it is connected at the bottom of the GUI, but the tray icon shows that the status is disconnected.  When I do a iwlist scan,  my LAN is only shown once. (See screen capture).

I do have a problem oftentimes with my router showing 2 or 3 times with the results of iwlist scan, particularly if letting the laptop sit for many hours in combination with a poor wireless signal.  In order to resolve this problem, I either have to reboot, or unload/reload the ndiswrapper/broadcom driver combination. (This is probably another problem however unrelated to what I am seeing here however.)

Any input would be great!

---

### Post by imdano on 2007-08-26
Have you had this problem since you installed it, or did this just start recently?

---

### Post by kevdog on 2007-08-26
This happens periodically -- but I dont know how to make it happen.

Here is some more insight into my situation, Im not expecting you to solve it but maybe my solution isnt correctly thought out.

Ive think Ive told you once before that oftentimes my router becomes listed twice in the results of iwlist scan.  It often does this at least after 30 minutes of connection (maybe more), and when it is listed twice, my current wireless connection doesnt work.  The only way Ive found to remedy this problem (short of rebooting), is to actually unload the ndiswrapper module and then reload it.  Here is the script that I use:

#!/bin/bash
ifconfig wlan0 down
if ps -ef | grep //opt//wicd//tray.py &>dev/null; then killall tray.py edgy.py; fi
modprobe -r ndiswrapper
modprobe ndiswrapper
ifconfig wlan0 up
/etc/init.d/wicd start >/dev/null 2>&1
sleep 10
/opt/wicd/tray.py& >/dev/null 2>&1

To call this script, I have set up a cron daemon under root (or in the /etc/crontab) that runs a script every 5 minutes that looks for duplicate entries in the iwlist wlan0 scan result.  If a duplicate entry is found, then the script posted above is called to bring down and then bring back up the wireless device.  

Problems that Im having are the following:
1. The command for wicd components still echo (stderr) to the command terminal
2. Bringing up tray.py doesnt always work (although the wicd daemon never has a problem)
3. Sometimes the tray.py process (as searched for in ps) is listed as tray.py, other times it is edgy.py
4. Sometimes when running the script, I get funny results as discussed in the original post with the tray.py listing the interface twice after resetting the network, although the results of iwlist scan no longer list duplicate entries.
5. Basically the tray.py thing is a pain in the *** -- so if its there great, if it isnt no big deal (its just nice to have some visual confirmation when looking at the screen that the network is up).

Ill gladly do some more debugging for you if you have any ideas.  I know you are doing a rewrite of the tray.py script right now anyway.  I installed wicd from "svn" about 3 weeks ago.  I cant remember what branch.  I havent updated since.

---

### Post by imdano on 2007-08-28
I think some of your tray.py problems are fixed in newer versions on the SVN.  The problem with wireless networks showing up more than once looks to be a driver issue, although if I get some free time I can write a workaround that will keep it from showing both.  Won't do anything to solve the root problem though.

When you say that sometimes after that script reloads ndiswrapper wicd still shows your network twice, does it continue to do that even after refreshing, or just initially?  Also, technically the tray doesn't handle displaying scan results, so your beef there is actually with gui.py :)

> 1. The command for wicd components still echo (stderr) to the command terminalCould you elaborate on this a little?  Do you mean the commands in the script?

---

### Post by kevdog on 2007-08-28
If you tell me what SVN branch to use, I will try it -- I know I have a driver problem down below.

I had the syntax incorrect with the other problem.

> does it continue to do that even after refreshing, or just initially?

Not sure what you mean???
I dont really refresh anything.  I kill the program and then restart it.  That is all.  I thought stopping and then restarting the program is like "refreshing".

Also sometimes I notice, that although usually the process is listed as tray.py in the ps (process list).  If I do the commands repeatedly (bug testing), sometimes it appears as edgy.py.  I know tray.py calls edgy.py, but I found this behaivor strange and most of all inconsistent.

---

### Post by imdano on 2007-08-28
I mean that when you click the refresh button in the gui, do you still see your network showing up twice.  I've noticed that sometimes old scan results stay loaded in the tray until you press refresh, even though it's supposed to run a fresh scan when the gui loads.  At some point I'll sit down and figure out what's going on there.

You could download the edgy.py from the testing branch of the svn, but the only bug I think it might help with is the tray occasionally not launching.  Not sure what causes edgy.py to show up in ps instead of tray.py, I don't think I've ever observed this myself.

---

### Post by kevdog on 2007-08-28
The next time dual interfaces show up, Ill try the refresh, although I think Ive done this and nothing happened.  Ill double check just to make sure (again I cant make the behaivor happen on cue).

Is the testing branch the most recent?? Id be happy to try the most alpha code, didnt know if it was testing or experimental.

---

### Post by imdano on 2007-08-28
Experimental is the newest, you'd just have to make sure you downloaded all the .py files in there, there are some large changes in the way the code is organized.

---

### Post by kevdog on 2007-08-29
If updated by svn sources, so I assume if I copy all my .py files from the experimental branch into /opt/wicd I will be OK???  I assume I do not want to overwrite my encryption and data folders??

---

### Post by imdano on 2007-08-29
Right.

---

