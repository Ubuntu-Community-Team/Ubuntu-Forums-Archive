---
title: "Please I need help before I drop my cumputer out a third story window..."
date: 2009-03-12
forum: New to Ubuntu
---

### Post by Leo Dragonheart on 2009-03-12
Ok I am having great difficulty staying connected to the internet. I am using Ubuntu 8.10. I am connected wirelessly. My ISP is ok or seems to be. My friends are not having problems that run windows. I did a complete reinstall yesterday. I have no bells and whistles except for a matrix type icon I am using for the mouse pointer. I am using FireFox 3.0, and have tried using Opera, Konquer, web browsers already.

I logged on this morning and all was fine. Booted up great, logged into the net fine, surfed for a couple of hours then dead. It all just slows to a snails pace. If I can get a page to load it takes minutes not seconds. Can someone please tell me WHAT IS GOING ON WITH MY COMPUTER PLEASE? It seems like it is possessed.

It is like my computer if working it *** off just to do a simple task like moving to the next page...HELP PLEASE!!! I DO NOT WANT TO HAVE TO GO BACK TO winblows just so I can be online...:-(

---

### Post by philinux on 2009-03-12
When its running ok run this

[http://www.speedtest.net/](http://www.speedtest.net/)

and repeat when on the go slow.

Could be your wireless signal loosing strength.

---

### Post by Peter09 on 2009-03-12
Can you post the output of the terminal command

```
ifconfig
```
and
```
lshw -C network
```

---

### Post by Leo Dragonheart on 2009-03-12
That must be the problem. So I need to move my usb connection closer to my box which is in the basement?

And thank you for that link...;-) Here are my results:

---

### Post by Leo Dragonheart on 2009-03-12
ifconfig:

```
leo@Illuzionz:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:47:fd:25:d3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2374 (2.3 KB)  TX bytes:2374 (2.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:7e:0a:04:62  
          inet addr:192.168.254.1  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7eff:fe0a:462/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:108049 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70079 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:104592605 (104.5 MB)  TX bytes:12853340 (12.8 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-7E-0A-04-62-34-36-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

---

### Post by Leo Dragonheart on 2009-03-12
lshw -Cnetwork:

```

leo@Illuzionz:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:03:47:fd:25:d3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=32 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1d:7e:0a:04:62
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.254.1 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 5e:bf:78:92:80:7e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
leo@Illuzionz:~$ 



```

---

### Post by Leo Dragonheart on 2009-03-12
Any suggestions?

---

### Post by KayakJim on 2009-03-12
What kind of internet connection do you have? It appears to be SDSL (or similar) based upon your speeds.

Your problem could also be related to your provider and/or your area. For example, with a cable connection everyone in your neighborhood shares the same line. As such, when the kids get home from school and all login to WOW your internet connection speed will be almost nothing.

---

### Post by Michaelg14 on 2009-03-12
if you are using a wireless USB adaptor you might need to move it closer to your computer.  I had one that would not work if the USB cable was longer that about 12 inches.  It would connect on a longer cable but would drop out after a few minutes.  It was an Engenius unit.  My solution was to get a PCI wireless card with an external antenna.

---

### Post by sandyd on 2009-03-12
have you tried lowering the bitrate of the connections?
 
Ubuntu sometimes runs the connections at the highest bitrate....
 
which causes the network to be unstable, slow, and has a weak signal.

---

### Post by theozzlives on 2009-03-12
> **Michaelg14 said:**
> if you are using a wireless USB adaptor you might need to move it closer to your computer.  I had one that would not work if the USB cable was longer that about 12 inches.  It would connect on a longer cable but would drop out after a few minutes.  It was an Engenius unit.  My solution was to get a PCI wireless card with an external antenna.

I had a roomate (before linux)  that used a usb adapter  and he had all kinds of  problems in Windows.

---

### Post by Leo Dragonheart on 2009-03-13
Ok I was on here yesterday and was having problems with my computer staying connected to the internet. I wake up this morning to find my friend that I talk to is having the same problems now and she has windows on her computer. Well I was not sure so I was going to do ANOTHER reinstall before I posted this just to check.

So I rebooted by accident lol and when it gave me a choice I choose a different boot and booted from a partition I did not even know I had but anyway it had one of my MANDRIVA installs on it come to find out. Well I booted it up and everything runs normally. Perfectly like nothing is wrong at all.

So what should I do with my Ubuntu 8.10 partition that is lets just say not working correctly. How can I fix this? Please help...

I only have ubuntu 8.10 and I guess mandriva on my computer that I know of. How can my friend check her computer and should she look for something inpiticular?

---

### Post by freak42 on 2009-03-13
please elaborate your problem further.

---

### Post by Therion on 2009-03-13
1.  Tell your Windows-using friend to scan her PC with a good antivirus application like [AVG Free Edition](http://free.avg.com/download-avg-anti-virus-free-edition) and then give them an Ubuntu LiveCD.

2.  At some point you installed Mandriva, and then you installed Ubuntu.  What I think you did when installed Ubuntu was, instead of using the entire hard drive, you used the defaults which set up separate partitions for both your existing Mandriva install and your new Ubuntu install.  If you want to have Ubuntu as your only operating system you can:

[INDENT]A.  Do a full reinstall using the "Use Entire Drive" option when prompted, or...

B.  Use Parted Magic/gParted LiveCD to delete the Mandriva partitions and then expand the Ubuntu partitions to use the newly freed-up space.[/INDENT]

---

### Post by gandaran on 2009-03-13
> So what should I do with my Ubuntu 8.10 partition that is lets just say not working correctly. How can I fix this? Please help...

explain what is wrong with the ubuntu partition?

---

### Post by scottuss on 2009-03-13
Yes we need more information. And you most likely **DO NOT** have a virus. Stop using your Windows mindset.

---

### Post by Leo Dragonheart on 2009-03-13
I don't know what you want to know. I connect to the internet usb wireless, I have no windows that I know of on my computer, I thought I only had ubuntu 8.10 but aparently I also have mandriva thankfully...;-). Ok for the lst 2 weeks I have been having a problem staying connected to the internet. When I was connected it took forever to load a page. Sometimes it would run great for 30 minutes or so then just stop. No matter what website I went to it was just slow. I thought it was my ISP but my friends say their computers are running fine. I reinstalled ubuntu 8.10 thinking that was the problem but I did not wipe the HD I just reinstalled is all. seemed to fix the problem for a minute then it started again. I have friends on Myspace that I talk to when I am online and now one of my friends are having the same problems. They can't check their emails, or chack their mail on myspace. 

So back to me I was just about ready to reinstall ubuntu 8.10 again but befor  I did I rebooted my computer by accident. so when it came to the login choices I picked a different choice ( trying to find DOS so I could wipe the HD) which happened to be a previous instolation of Mandriva a friend sent me That I used before I got ubuntu 8.10 disk in mail. So I loged in and let it load up. Then I logged into the net no problem, surfed around all the spots I could not get to before with my ubuntu and no problems. I am curently writing this from MANDRIVA. I don't know what else to say. If you need more info just ask me a question please...

---

### Post by Leo Dragonheart on 2009-03-13
> **Therion said:**
> 1.  Tell your Windows-using friend to scan her PC with a good antivirus application like [AVG Free Edition](http://free.avg.com/download-avg-anti-virus-free-edition) and then give them an Ubuntu LiveCD.

2.  At some point you installed Mandriva, and then you installed Ubuntu.  What I think you did when installed Ubuntu was, instead of using the entire hard drive, you used the defaults which set up separate partitions for both your existing Mandriva install and your new Ubuntu install.  If you want to have Ubuntu as your only operating system you can:

[INDENT]A.  Do a full reinstall using the "Use Entire Drive" option when prompted, or...

B.  Use Parted Magic/gParted LiveCD to delete the Mandriva partitions and then expand the Ubuntu partitions to use the newly freed-up space.[/INDENT]

in response to #1 I will. #2 No when I installed it i thought I used the whole disk but maybe not. I will try again. and B.) I will do that also thanx...

---

### Post by LowSky on 2009-03-13
> **Leo Dragonheart said:**
> 
So back to me I was just about ready to reinstall ubuntu 8.10 again but befor  I did I rebooted my computer by accident. so when it came to the login choices I picked a different choice ( trying to find DOS so I could wipe the HD) which happened to be a previous instolation of Mandriva a friend sent me That I used before I got ubuntu 8.10 disk in mail. So I loged in and let it load up. Then I logged into the net no problem, surfed around all the spots I could not get to before with my ubuntu and no problems. I am curently writing this from MANDRIVA. I don't know what else to say. If you need more info just ask me a question please...

Yea this isn't a virus, and you are being very limited in telling us what is actually going on with your computer. Not to mention how did you not know you had another OS on your PC? Trying to find DOS? DOS is a Microsoft product and how would you use it to to remove Ubuntu...? If you know the command prompts to delete a partition but don't know how to purge or remove Firefox, or reinstall the network files, then What am I to think?

Seriously this thread just makes little to no sense, and even if you are being sincere about your problem, you know too little of the actual issue to even assume what the problem is, your like a boy who cries wolf when it only the neighbor's dog. Your issue is you either have a internet connectivity issue or corrupted Firefox profile, both of which can explain the current situation you are in and why another OS works just fine.

---

### Post by DGortze380 on 2009-03-13
> **Leo Dragonheart said:**
> I don't know what you want to know. I connect to the internet usb wireless, I have no windows that I know of on my computer, I thought I only had ubuntu 8.10 but aparently I also have mandriva thankfully...;-). Ok for the lst 2 weeks I have been having a problem staying connected to the internet. When I was connected it took forever to load a page. Sometimes it would run great for 30 minutes or so then just stop. No matter what website I went to it was just slow. I thought it was my ISP but my friends say their computers are running fine. I reinstalled ubuntu 8.10 thinking that was the problem but I did not wipe the HD I just reinstalled is all. seemed to fix the problem for a minute then it started again. I have friends on Myspace that I talk to when I am online and now one of my friends are having the same problems. They can't check their emails, or chack their mail on myspace. 


Sounds like a driver problem to me. The trouble your friends are having are most likely coincidental... I frequently run into those symptoms with my D-Link adapter.

---

### Post by Leo Dragonheart on 2009-03-13
> **LowSky said:**
> Yea this isn't a virus, and you are being very limited in telling us what is actually going on with your computer. Not to mention how did you not know you had another OS on your PC? Trying to find DOS? DOS is a Microsoft product and how would you use it to to remove Ubuntu...? If you know the command prompts to delete a partition but don't know how to purge or remove Firefox, or reinstall the network files, then What am I to think?

Seriously this thread just makes little to no sense, and even if you are being sincere about your problem, you know too little of the actual issue to even assume what the problem is, your like a boy who cries wolf when it only the neighbor's dog. Your issue is you either have a internet connectivity issue or corrupted Firefox profile, both of which can explain the current situation you are in and why another OS works just fine.

I do sencirly apologise for the inconvieniance. I am not cying wolf I am having real problems and yes maybe I don't know how to explain myself clearly but I don't know this Linux crap and I don't know how to use it. I thought when I reinstalled ubuntu again I thought I used the whole drive but aparently I didn't so I was not looking for other pertitions. Fire fox is running great in Mandriva right now. I have only had ubuntu for about 2 months maybe any Linux at all for that matter. I don't know what else you want me to tell you about my problem.

When I go to log onto the internet with Firefox, Opera, or Kounquer browsers from my ubuntu installation it will not load I get an error page that says fire fox canot find the address. When I am able to log into the net it runs very slow and sluggish. I will be on a website and when I go to a new one I get the erro page again. I am curently using the Mandriva partition I did not know I had ( I am sorry if you don't believe me but it is true) and Firefox is working fine and running great. I can surf the web. It is fast and I am having no problems. What else would you like to know? Maybe you should explain yourself a little clearer. I have told you exactly what has been going on.

P.S. thanx for the info. can you please explain how I can correct my corrupt Fire fox problem?

---

### Post by fooman on 2009-03-13
> **Leo Dragonheart said:**
> When I go to log onto the internet with Firefox, Opera, or Kounquer browsers from my ubuntu installation it will not load I get an error page that says fire fox canot find the address. 

......

P.S. thanx for the info. can you please explain how I can correct my corrupt Fire fox problem?

if it also happens with opera and konqueror...what makes you think firefox is corrupt? 

anyways, how are you connecting to the internet? ...ethernet or wireless? ...cable or dsl?

if it is wireless....what wireless card/chipset is it?

---

### Post by gandaran on 2009-03-13
> **Leo Dragonheart said:**
> I do sencirly apologise for the inconvieniance. I am not cying wolf I am having real problems and yes maybe I don't know how to explain myself clearly but I don't know this Linux crap and I don't know how to use it. I thought when I reinstalled ubuntu again I thought I used the whole drive but aparently I didn't so I was not looking for other pertitions. Fire fox is running great in Mandriva right now. I have only had ubuntu for about 2 months maybe any Linux at all for that matter. I don't know what else you want me to tell you about my problem.

When I go to log onto the internet with Firefox, Opera, or Kounquer browsers from my ubuntu installation it will not load I get an error page that says fire fox canot find the address. When I am able to log into the net it runs very slow and sluggish. I will be on a website and when I go to a new one I get the erro page again. I am curently using the Mandriva partition I did not know I had ( I am sorry if you don't believe me but it is true) and Firefox is working fine and running great. I can surf the web. It is fast and I am having no problems. What else would you like to know? Maybe you should explain yourself a little clearer. I have told you exactly what has been going on.

P.S. thanx for the info. can you please explain how I can correct my corrupt Fire fox problem?

stick with mandriva, it is by far the best perfect linux, ubuntu has many bugs, ( I still prefer ubuntu with all it's bugs) if you cant fix those bugs continue using mandriva!

---

### Post by Leo Dragonheart on 2009-03-13
> **fooman said:**
> if it also happens with opera and konqueror...what makes you think firefox is corrupt? 

anyways, how are you connecting to the internet? ...ethernet or wireless? ...cable or dsl?

if it is wireless....what wireless card/chipset is it?

First off you are correct. It was not just firefox! I am just a little flustered from an earlier post and 2 weeks of not having my internet.

I connect to the internet wirelessly through a usb port. I am not sure what DSL stands for but I am sure it is not etho. I have a satilite package that includes  the net. (Satilite, Phone, and Internet) 

I installed ubuntu.8.10 around the beging of January this year and until this month everthing ran great. At the begining of this month is when I was not able to connect to the net.

I did try Opera, Konquer, and Firefox web browsers so it was not just firefox. I had the same problem with all of them. I have downloaded stuff to ubuntu and I don't really know how to install stuff correctly so maybe I mixed something up I do not know.

I was going to reinstall ubuntu and found I had Mandriva installed on here previously that a friend had sent me and it runs fine. so it has to be my ubuntu intillation. (not the instillation but something I did to it)

Can someone please tell me how to use gparted from my live CD so I can do a new clean install?

Thank you all for your help and for putting up with my frustration. Linux is not crap. I love Linux and I apologise for my earlier statment I was upset. Please forgive me... Thanx again for everyone help!!!

---

### Post by jimv on 2009-03-13
Good God, people, calm down!  This person is trying to get help.  We don't need a dozen people coming in here screaming "OMGZ NO YOU DO NOT HAVE A VIRUS NOOB!"  Geeze.

---

### Post by edwardLS on 2009-03-13
I am not at all sure this will help, but I feel that I may be remiss if I don't mention it.  The following information is from my son who has even less Ubuntu (Linux) experience than me.  He has Ubuntu 8.10 and when he last updated he got a new kernel.  He was never able to get his wireless working properly with that new kernel.  

To test this, I had him boot through GRUB, but select the earlier kernel and see if he still had the problem.  I am not saying this is the issue, but when he boots on the earlier kernel his wireless is working perfectly.

Just a thought.  Good Luck.

---

### Post by overdrank on 2009-03-13
Threads merged. :)

---

### Post by Perfect Storm on 2009-03-13
> **overdrank said:**
> Threads merged. :)

But bit confusing to read :lolflag:

---

### Post by Therion on 2009-03-13
> **jimv said:**
> Good God, people, calm down!  This person is trying to get help.  We don't need a dozen people coming in here screaming "OMGZ NO YOU DO NOT HAVE A VIRUS NOOB!"  Geeze.
Thank you.  I was trying to think of a calm, rational way to put this.  Now I can stop thinking about it.


**LEO:**

What you're going to need to do, in short, is this:

[INDENT]Download and burn the Parted Live CD (this is the new name, by the way, for gParted) to a bootable .iso, just like you would any other LiveCD, and then boot to it.

You'll then need to identify the Mandriva  partition on your hard drive.  Right-click on it to remove it and then click "Apply Changes".

Now select the remaining Ubuntu partition by clicking on it and then on the Resize/Move option.  You want to resize this partition.  Just use the slider so that the Ubuntu partition uses what's left of the drive.  Click on "Apply Changes", let Parted Magic do it's thing and you're done.[/indent]

Post back if you need more assistance.  It's really pretty simple once you actually SEE Parted Live in action.

---

### Post by Leo Dragonheart on 2009-03-13
> **edwardLS said:**
> I am not at all sure this will help, but I feel that I may be remiss if I don't mention it.  The following information is from my son who has even less Ubuntu (Linux) experience than me.  He has Ubuntu 8.10 and when he last updated he got a new kernel.  He was never able to get his wireless working properly with that new kernel.  

To test this, I had him boot through GRUB, but select the earlier kernel and see if he still had the problem.  I am not saying this is the issue, but when he boots on the earlier kernel his wireless is working perfectly.

Just a thought.  Good Luck.

Thanx that may be it. I had the manager set to update daily so maybe I got the same thing. Thanx for the info...

---

### Post by Leo Dragonheart on 2009-03-13
> **Therion said:**
> Thank you.  I was trying to think of a calm, rational way to put this.  Now I can stop thinking about it.


**LEO:**

What you're going to need to do, in short, is this:

[INDENT]Download and burn the Parted Live CD (this is the new name, by the way, for gParted) to a bootable .iso, just like you would any other LiveCD, and then boot to it.

You'll then need to identify the Mandriva  partition on your hard drive.  Right-click on it to remove it and the click "Apply Changes".

Now select the remaining Ubuntu partition and then on the Resize/Move option.  You want to resize it.  Just use the slider so that the Ubuntu partition uses what's left of the drive.  Click on "Apply Changes" and you're done.[/indent]

Post back if you need more assistance.  It's really pretty simple once you actually SEE Parted Live in action.

I hate to add to your already infuriated self. I have a ubuntu 8.10 live CD but I can not burn cds. No burner...;-(

Thanx for your assistance... I know I piss people off cause I get riled up and don't speak clearly...I am truly greatful for all the help!!!

---

### Post by chrisod on 2009-03-13
I have a Netgear USB wireless adapter that acts exactly like this with multiple distros of Linux.  It seems perfectly fine for the first 5 or 10 minutes and then ping times are suddenly measuring in whole seconds, which makes the Internet essentially useless. It works fine with Windows.

I solved it by  switching adapters - took one from a Windows box and put the Netgear on the Windows box.

---

### Post by Therion on 2009-03-13
> **Leo Dragonheart said:**
> I hate to add to your already infuriated self. 
I'm sorry if I sound, or soundED, "infuriated"... 

I assure you nothing could be further from the truth.  Just trying to help you out.

Good luck with whatever you decide to do!

---

### Post by geneross on 2009-03-13
> **Leo Dragonheart said:**
> 

I logged on this morning and all was fine. Booted up great, logged into the net fine, surfed for a couple of hours then dead. It all just slows to a snails pace. If I can get a page to load it takes minutes not seconds. Can someone please tell me WHAT IS GOING ON WITH MY COMPUTER PLEASE? It seems like it is possessed.


 It may be not problem with a configuration, you need to check a quality of the connection since other devices may cause interference for you card. Unfortunately I don't know how to check wifi media level in Linux, but may be someone will come up with guidelines.

---

### Post by dasunst3r on 2009-03-13
If you are on a wireless connection, there is a chance that the wireless band is being saturated (i.e. there are too many devices in your area).  I have been facing the same issue, and there are several ways to remedy this:
[list]
[*]Switch to a wired connection
[*]Do a "site survey" by issuing command *sudo iwlist wmaster0 scan*, tallying up how many SSIDs occupy each channel, and change your router to use the least-occupied channel.
[/list]

---

### Post by scottuss on 2009-03-13
> **jimv said:**
> Good God, people, calm down!  This person is trying to get help.  We don't need a dozen people coming in here screaming "OMGZ NO YOU DO NOT HAVE A VIRUS NOOB!"  Geeze.

No, but ignoring the fact that the user has most likely made a mistake in assuming he/she has a virus is not needed either. If a new user needs more time adjusting from a Windows mindset then fair enough, but they DO need to adjust, that part shouldn't really be up for debate.

---

### Post by Peter09 on 2009-03-13
Also note that if someone is downloading a torrent (or similar) some ISP's will seriously limit your bandwidth while that is happening.

---

### Post by Leo Dragonheart on 2009-03-13
> **scottuss said:**
> No, but ignoring the fact that the user has most likely made a mistake in assuming he/she has a virus is not needed either. If a new user needs more time adjusting from a Windows mindset then fair enough, but they DO need to adjust, that part shouldn't really be up for debate.

YOU ARE CORRECT!!! I need to asjust and Iwant to adjust. That was a carry over from windows and it most likely is NOT a virus. I am having a PROBLEM...:-) The virus thing was my bad sorry...

---

