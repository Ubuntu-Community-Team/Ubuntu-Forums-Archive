---
title: "Virus,Stuck,Locked,..."
date: 2009-01-24
forum: New to Ubuntu
---

### Post by Leo Dragonheart on 2009-01-24
Here is what happened. I clicked on this site and these windows poped up. I tried closing them and all it did was alternate back and forth between the two... I finally had to just shut down and reboot. Is there anything I can do to prevent this or to escape it if it happens again?

I am using Ubuntu 8.10...

---

### Post by Muffinabus on 2009-01-24
Could have just killed the Firefox process, or were you not able to access a Terminal or the System Monitor for some reason?

---

### Post by Leo Dragonheart on 2009-01-24
I probably could have accesed it I just don't know how to kill it... I am use to the control-alt-delete...from SATAN!!!(Windows)

Edit: I did try to close Firefox by using the X up in the corner and closing it from the panel and they did not work...

---

### Post by leonardo_neo on 2009-01-24
This is strange! 

After restarting how your computer is behaving? Is it giving some trouble? 

I wish to know from some Linux guru, about the mechanism of this bug infected ubuntu? Also I wish to know what could be the consequences?

---

### Post by jemate18 on 2009-01-24
to kill it .

open a terminal then type

```
killall firefox
```

---

### Post by Muffinabus on 2009-01-24
Well for future reference, you can access the System Monitor under System > Administration > System Monitor, then you can kill a process by right clicking and choosing "Kill Process".

EDIT: or you can do as jemate18 says with the Terminal.

---

### Post by Leo Dragonheart on 2009-01-24
OK thanx for the info... Yea it is running fine it just locked me into that screen, but all is working fine as far as I can tell...

---

### Post by jemate18 on 2009-01-24
or you can try the hard way..

Open terminal..

type
```
ps ax  | grep firefox
```

```
Find the PID (Process ID)
```
it is usually the number in the 1st columns. (for example it has a pid of 1232.

then kill it using 
```
kill -SIGTERM 1232
``` or
```
kill -s 15 1232
```

---

### Post by snowbalance on 2009-01-24
Getting a screen like that happens sometimes when browsing.  It doesn't mean Linux has actually been infected, since the malware downloading will be targeted at a Windows OS.  Doesn't mean there are zero viruses for Linux, but seems like 99.9% of its users say they've never had a virus or known anyone who had on Linux ;) Thankfully.

---

### Post by carml on 2009-01-24
Just for my info,what you did before that window appear?I ask because I wish to try Ubuntu 8.10 under windows just for curiosity,even if I'm using 8.04 on a dual boot. :)

---

### Post by SunnyRabbiera on 2009-01-24
Yeh its probably a bad site, no virus involved as Ubuntu really doesnt have any that work like that.
For the future though, right click on your panel and select "add to panel"
and then add the force quit applet to solve future issues.

---

### Post by Leo Dragonheart on 2009-01-24
Yea I don't even have windows on this computer, and it did say windows was scanning my computer so I am sure it was a windows virus or whatever it was it was directed at windows. I was just wondering how it locked me there and how to deal with it if it happens again. It was just kinda weired...

just an update my computer is running fine...

---

### Post by Leo Dragonheart on 2009-01-24
> **SunnyRabbiera said:**
> Yeh its probably a bad site, no virus involved as Ubuntu really doesnt have any that work like that.
For the future though, right click on your panel and select "add to panel"
and then add the force quit applet to solve future issues.

You know what I have that in my little drawer on the panel... Didn't even think of that, maybe I will put it out where I can see it... Thanx.

---

### Post by leonardo_neo on 2009-01-24
> **Leo Dragonheart said:**
> Here is what happened. I clicked on this site and these windows poped up. I tried closing them and all it did was alternate back and forth between the two... I finally had to just shut down and reboot. Is there anything I can do to prevent this or to escape it if it happens again?

I am using Ubuntu 8.10...

> **Leo Dragonheart said:**
> Yea I don't even have windows on this computer, and it did say windows was scanning my computer so I am sure it was a windows virus or whatever it was it was directed at windows. I was just wondering how it locked me there and how to deal with it if it happens again. It was just kinda weired...

just an update my computer is running fine...

Good to hear that your comp is working fine... I guess, since it was  targeted for Windows, so it couldn't install on Ubuntu....:KS

---

### Post by SunnyRabbiera on 2009-01-24
> **Leo Dragonheart said:**
> Yea I don't even have windows on this computer, and it did say windows was scanning my computer so I am sure it was a windows virus or whatever it was it was directed at windows. I was just wondering how it locked me there and how to deal with it if it happens again. It was just kinda weired...

just an update my computer is running fine...

You know there is this one site that fakely scans for viruses but its actually a scam site used to infect and pick things apart.
Lucky for you firefox isnt tied into the kernel, if this was IE on windows you would be in trouble.

---

### Post by Firestone on 2009-01-24
Are you sure it isnt just a popup? I recon it did close on pressing cancel, but the code of the webby just presented it again(until you press OK ofc). Besides, closing firefox doesn't work with a query popup open. 
I'll bet that pressing OK would've given you a download for a .exe file cq. the actual virus.

---

### Post by SunnyRabbiera on 2009-01-24
> **Firestone said:**
> Are you sure it isnt just a popup? I recon it did close on pressing cancel, but the code of the webby just presented it again(until you press OK ofc). Besides, closing firefox doesn't work with a query popup open. 
I'll bet that pressing OK would've given you a download for a .exe file cq. the actual virus.

there are sites that can infiltrate firefox and IE without a .exe, IE more common of course but I heard of a few that can at least give firefox the jitters.

---

### Post by Zewbie on 2009-01-24
There is a thing called the "Russian Virus" also know as "ScareWare" targeted to Windows users...  It's a popup that says it's scanning your PC and then it tells you that your computer is infected with a "X" amount of Trojans, adware, spyware and whatever. It's all BS so you can then download there program for a price that does not do anything but tell you your system is clean.

From your screen shots it looks like your running under WINE or some kind of Windows emulator.  WINE is meant for running windows programs that you like or need not to browse the web.  Your running Ubuntu use the FireFox for Linux...  You can't tell me you want and need Internet Explorer and it you do then format your harddrive and install Vista.

Pease;)

---

### Post by 3rdalbum on 2009-01-24
> **Zewbie said:**
> From your screen shots it looks like your running under WINE or some kind of Windows emulator.

No, it's just a web page made to look like the "My Computer" window on Windows. Very common trick for scammers.

---

### Post by Leo Dragonheart on 2009-01-24
> **Zewbie said:**
> There is a thing called the "Russian Virus" also know as "ScareWare" targeted to Windows users...  It's a popup that says it's scanning your PC and then it tells you that your computer is infected with a "X" amount of Trojans, adware, spyware and whatever. It's all BS so you can then download there program for a price that does not do anything but tell you your system is clean.

From your screen shots it looks like your running under WINE or some kind of Windows emulator.  WINE is meant for running windows programs that you like or need not to browse the web.  Your running Ubuntu use the FireFox for Linux...  You can't tell me you want and need Internet Explorer and it you do then format your harddrive and install Vista.

Pease;)

I have no windows on my computer... I hate windows. Windows is SATAN!!! I am running Ubuntu 8.10 w/Firefox...

---

### Post by mindbucket on 2009-02-02
I keep System Monitor and Terminal up on a workspace at all times.

If Firefox or Opera acts up I use 

kill -9   and the process ID # of the failing browser from the System Monitor.....works well for me.

---

### Post by kansasnoob on 2009-02-02
Ctrl + C should kill that process!

---

### Post by Praxicoide on 2009-02-02
Could be just pop-ups. There are some really mean rick-roll sites that won't let you close the window because of pop-ups. This is very annoying because I usually have some tabs, and afterwards I can't simply restore the windows (since it would bring back that site too). I have to get them through history

---

### Post by muteXe on 2009-02-02
It looks exactly like "scareware", as one of the chaps up from me said, trying to get you to buy registry cleaners or scanners.  It just assumes you have windows.

---

