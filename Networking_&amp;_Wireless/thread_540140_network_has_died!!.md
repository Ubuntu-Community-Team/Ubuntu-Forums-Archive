---
title: "network has died!!"
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by fugative on 2007-09-01
Recently and inexplicably my internet went down, the sagem usb modem boots, loads, connects but no internet! I tried firestarter, checked configuration and eventually uninstalled it -- no change.
from the network monitor applet i got my isp's ip and pinged it success tried to ping google (by name) network tools froze and i had to do a force quit. I checked my chap and pap secrets and all's well there infact sys log says that connection occurred ok and a few packages are sent and recieved. 

Now i also noticed that my wlan is down and the couple of networks i usually find are not to be found. 

I then try my laptop that runs the same feisty the ad-hoc wlan is down and cannot find anything in roaming mode. I connect the sagam to it and the same senario again can ping but no net (e-mail, synaptic et al). Of course i tried the setup in windows and no problems there so isp hasn't cut me off and hardware is ok. 

so I come to a couple of conclusions either my isp has some anti-ubuntu devise or a recent update has broken the system. Not very convinced about either. 

BTW have checked DNS everything ok there,  it's like a firewall has cut me off but i've removed firestarter anyone help me check iptables.

I'm at a loss, I can't reinstall everytime something like this happens (i need to learn how to fix it)

Thanks

---

### Post by fugative on 2007-09-02
PLEASE, SOMEBODY must have an idea 
i started playing with iptables accepting all traffic and still nothing and i don't want to mess around where i don't know.

desperate!!!

---

### Post by johnbl on 2007-09-02
This situation is surely an update gone wrong. I have the same situation, the lights are on but no ones at home it appears. Horrid to say, but if it wasn't for a MS box I'd have no ability to get to the net at all.

Those with one box and that Ubuntu would be tearing hair in isolation.
 
I've followed the various threads on the problem and ' fiddled ' with menu.lst etc attempting suggested fixes but all to no avail.

Computer [ notebook ]  works a treat just refuses to usably connect whilst logs suggest/  indicate it is all ok, at least in so far as there are no glaring ERROR messages. My level of competence isn't such as to be able to say I could read every line though, I'm a sort of a minor geek in training.

 A corrective patch isn't going to work if update manager is to be the delivery / install mechanism when systems are unable to get on line anyway. A Catch 22! So if anyone can point to a location for a deb that can rectify the " every thing is ok but nothing works situation "  I and others seem to be in, please please post it in the sticky section of the forums.

---

### Post by fugative on 2007-09-03
Kinda relieved that I'm not on my own here but it's definitely a club i'd  prefer not be be a member of.
The more i look the more i discover but frustratingly no solution. I posted a request on launchpad but no replies there.
Did a iptables -L report which takes ages to complete and i only know that this is not normal because i found an old HDD with edgy on it.
OK John so we've figured that it's probably an update gone pear-shaped and we'll have to reinstall but how do we guard against this in future and how can we make the reinstallation less than a two day row with the Mrs.

Developers: can we have some kind of back-stepper so we can undo these situations or can we ghost our present installation (without the glitch). I love my 'buntu box and i've hated looking at the world through windows the last few days. 

CALLING others in the same situation (though you probably can't get on-line to be here)


Together we may be able to crack this thing.

BTW John, cheers for the reply i was starting to get lonely in my misery.

can you point me towards the stuff you found on the subject

---

### Post by johnbl on 2007-09-03
Your far from alone there and like you, this is a club I'd rather not be an intimate off. 
This thread shows others working on it and have for some time.

[http://ubuntuforums.org/showthread.php?p=3030748#post3030748](http://ubuntuforums.org/showthread.php?p=3030748#post3030748)

I had been following the logic that wifi-radar was at the foot of it. I'd been attempting to get that up for some time but.. never with any sort of luck, as others. Pulled that but no network fix. So much for that great theory!

All the report tools that relate to networking seem to say all is A OK, bar one, eth1 shows package errors. I understand eth0 is the wired connect so not so sure what that means. Router says it's aware of the connected system. But something in there is saying no, bugger off!

I don't know enough to be able to back track through all the possible levels / applications that might be doing that or in fact know what could be. Frustrating thing is it's probably as simply as changing a script flag to 1 from 0 ...   < Sigh..>

Reticent to start again with a full reload for the very reason you illuminate, I could so easily go right back to where I am, bit like Snakes and Ladders! Notebook is a critical bit of kit for on road use and I'd rather not take a system out into the wild that I can't be rely upon. Makes one look such a sad case in front of others when the system one has been raving about spits the dummy.

---

### Post by fugative on 2007-09-04
PUNCH THE SKY!!!!!!!!!!!!!! I DID IT!

Well almost.....

I read the thread about network manager, which is of no use to me anyway, my modem is USB and my network is ad-hoc which NM doesn't manage. so i got shot of it. Then i could ping my isp, which although i said i could do it stopped working and i was in denial then i pinged myself using the client ip from my isp and checked firestarter which said i was getting an input from my wlan this should not be sending my internet signal so i disabled it with a # before auto wlan0 in interfaces. rebooted and BAM BBC world news live and ... well quite informative, i feel like a geek warrior. 

Now can i backtrack and solve the problem that the ubergeeks can't so i can get my wlan working again. I'll try but it seems obvious that NM is the culprit.

Question: somewhere there must be a file which tells the machine the ip to use when connecting to the net for me this had changes to 192.168.1.1 (my wlan static ip) then when i changed that to 192.168.0.1 it followed so it must have wlan0 as default connection to the net something that i changed in firestarter to ppp0 but only on deactivating wlan0 did it work. 

got to be enough info there to formulate a cure.

John, this 'buntu lark can try us but remember early windows, not the most reliable and they had shed loads of money behind them at least this keeps hackers of the streets doing something productive. 

but don't tell the wife!

cheers 
David

---

### Post by johnbl on 2007-09-07
David,
SOLVED, well at least as far as a wired etho connection.

I sat in a dark spot for a while going over options and things I did and didn't do, to quote Steve Nelson, or some such malarkey.

Conclusion was that as it did work out of the box as it were using network manager that HAD to be the source of the broken thing. Found a deb on line via my  ' trusty ' MS box, slid the file    libnm-glib-dev_0.6.5-0ubuntu9_i386.deb  onto a USB thumbnail and tried a reinstall of NM . Immediately broke on a missing glib0 error.  Looks like that might have been the missing link all along. That a deb hasn't all the dependencies covered was cause for a mild expleative, but you get that.

Back on line and at [http://download.tuxfamily.org/osrdebian/index.html](http://download.tuxfamily.org/osrdebian/index.html) 

found 

network-managerVersion:	0.6.4-8 

libnm-glib0Description:	network management framework (GLib shared library) More... 
Package:	libnm-glib0_0.6.4-8_i386.deb

libnm-util0Description:	network management framework (shared library) More... 
Package:	libnm-util0_0.6.4-8_i386.deb

network-managerDescription:	network management framework daemon More... 
Package:	network-manager_0.6.4-8_i386.deb

network-manager-gnomeDescription:	network management framework (GNOME frontend) More... 
Package:	network-manager-gnome_0.6.4-8_i386.deb  

Download and installed the lot, and here I am, immediately back up. YES!!

I assume that in the fullness, the auto update will bring the version up to most current.

As to the source of the hassle and the odd thought.

I know there are utilities around that will look at everything on a system and deduce dependencies and even remove redundant flotsam left by hasty or incomplete application removal. Or as my wife would put it, playing... But same isn't included in the default setup ' load ' of Ubuntu. One observation I'd make for design teams, when the system is down, that isn't the time to find out there is a utility that might light the path BUT.. Tools for recovery and stuff for highlighting incomplete dependencies MIGHT be seen as ' required on voyage'!

When the lights go out or even flicker isn't the time to discover what might have been available if only ...

Now, wireless, that will be SO much fun<g>

John

---

### Post by fugative on 2007-09-10
Nice try John (sorry, congtrats on deglitching your prob) didn't work for me. I reach the net through a usb modem and if i enable my eth0 or wlan0 and try to share the connection my ppp0 blocks. I carefully reinstalled the NM with the files you used and installed the header updates but woe is me didn't work. still think i need to get into the system where it defines the device that takes the adsl first. Everyone asumes that we all connect through a lan modem/router or wifi. Here in Greece a wifi router/modem is quite expensive and also why should i pay out for hardware to fix (maybe) a software deficiency.

If you find anything on your walkabouts let me know 

cheers John and don't give up buntu is nearly there in so many ways, i've had to use my doze partition lately and it feels wrong now and strangely buggy.

---

### Post by fugative on 2007-09-10
Nice try John (sorry, congtrats on deglitching your prob) didn't work for me. I reach the net through a usb modem and if i enable my eth0 or wlan0 and try to share the connection my ppp0 blocks. I carefully reinstalled the NM with the files you used and installed the header updates but woe is me didn't work. still think i need to get into the system where it defines the device that takes the adsl first. Everyone asumes that we all connect through a lan modem/router or wifi. Here in Greece a wifi router/modem is quite expensive and also why should i pay out for hardware to fix (maybe) a software deficiency.

If you find anything on your walkabouts let me know 

cheers John and don't give up buntu is nearly there in so many ways, i've had to use my doze partition lately and it feels wrong now and strangely buggy.

---

### Post by johnbl on 2007-09-10
I spoke a tad soon, premature elation <g>

See the thread "Slow I Mean SLOW start up " I opened. System hangs for 10 minutes on start up now, then get's over it and simply starts working.. Not good enough though, I don't HAVE 10 or more minutes to get a notebook up if a client is on hold <sigh>

But all the gory details are in the above thread. I won't give up on Ubuntu any time soon but these clitches sure try the patience!

Whilst learning more and more about the innards of Ubuntu there is a small problem with that learning loop.. Say a great quote the other day that sums it;
" Time is a great teacher, but it also kill all the pupils "

One thing I'd like to see would be a repository where the apparently arcane meanings of all the log entries were EXPLAINED. I often feel that the problem causing my heartache is hiding in plain sight but I'm too thick to be able to read the truncated implications in the various log files! 
On that, log files, it would seem like a great idea to place ALL log files in ONE place. 

<sigh>

John

---

