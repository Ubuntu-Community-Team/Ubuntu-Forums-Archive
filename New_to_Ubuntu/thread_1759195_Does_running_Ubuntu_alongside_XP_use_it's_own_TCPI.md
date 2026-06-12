---
title: "Does running Ubuntu alongside XP use it's own TCP/IP settings?"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by TracyA on 2011-05-15
Hi All, 
I would like to try Ubuntu alongside my XP, but my XP's TCP/IP settings are broken:
Due to either an undetected virus, or a too-quick-click I don't know, I lost my TCP/IP settings on my XP. Gone. I therefore cannot connect to internet, and also unless I startup in diagnostic mode my computer hangs up at 100% trying to resolve the conflict. 

After all resets and fixes I can find on the internet to no avail, it appears this will require a re-install of the OS. So I'd like to try Ubuntu first, before making the decision as to which OS to install.
 
If I install Ubuntu alongside my broken XP network settings, will it redefine its own network settings and run with them, or will it try to use my broken ones. .. or will it fix my broken ones.

Thanks in advance!
Tracy

---

### Post by Hedgehog1 on 2011-05-15
If you do a dual-boot install of Ubuntu, It will make it's own 'typical' tcp/ip setup (using DHCP - where it gets the data from your router or your cable modem).

You can also do this:

Boot from the Ubuntu LiveCD/LiveUSB, and see of you have internet access.  If so, look at the network setups and write down what they are.  You can then use these setting to re-setup your XP settings.


***The Hedge***

:KS

p.s. For surfing the web, a Linux install is much safer as it is immune to viruses.  A Linux install also tends to run much faster that a Windows install.  So there are some advantages to dual-booting above and beyond getting the network settings to use to restore your XP's settings

---

### Post by NoNameWill on 2011-05-15
In windows have you tried 

```
ipconfig /renew
``` 

Try that in Start>Run

---

### Post by TracyA on 2011-05-15
Thanks Hedgehog.. I know I could've just tried it for myself but I thought I'd ask ahead of time... After past 2 days of disappointing trial and error I wanted some glimmer of hope before another let-down again.  I do intend on trying it as a dual boot first, then I can be sure to always have my Windows stuff still available. (as I've know there are some things that I can't run on ubuntu .while I wean myself off of Windows..)
And yes that's the reason I'm wanting to try it because I'm sick of killing viruses.

Will...(with no name :) )
Oh ya, I have been at this for 2 days. ipconfig with any parameter comes up with "internal error occurred, the request is not supported.. unable to query host name." 
I have reset the winsock and did a netsh reset of the tcp/ip, and the nic. IP settings are blank and ignore/reject any numbers I put in there. I did everything except physically pulling the NIC and replugging it. Nah, not doing that. 
So, yeah, this is a last resort.  .. and, well this is an ubuntu forum so I'll just shutup on Windows now except to say it suuucks!. !! I'm frustrated!

Thanks again.. I'll post back if I have trouble. 
Tracy

---

### Post by slooksterpsv on 2011-05-15
Run these commands on Windows in order:
```

ipconfig /release
ipconfig /flushdns
ipconfig /renew
ipconfig /registerdns
netsh int ip reset reset.txt
netsh int ip reset reset.txt
netsh winsock reset catalog

```

Reboot, if that fails to fix it let me know

---

### Post by TracyA on 2011-05-15
Thanks Slookster, 
all ipconfig commands get  "Windows IP Configuration An internal error occurred: The request is not supported. Please contact Microsoft Product Support Services for further help. Additional information: Unable to query host name. 
And any netsh ip commands get WARNING: Could not obtain host information from machine: [THINKPAD]. Some commands may not be available. The service cannot be started, either because it is disabled or because it has no enabled devices associated with it. 
The netsh reset command says it was successfully reset but after reboot nothing changes.
I've run a few different Winsock resets too. 

As I said, I've been at this 2 days, Googled my brains out, and I'm pretty much ready to give up and just do a clean install.. of something, I just haven't decided what OS yet. 

That's why I have asked the question here.. I want to see if Ubuntu is going to try and use the defective Windows settings or make its own, if I install it as a dual. 
That way I can still have an OS while I'm deciding.

---

### Post by Hedgehog1 on 2011-05-15
TracyA,

If you boot off the an Ubuntu LiveCD, and select 'TRY', does it successfully connect to your network?

If it does, you can look at the setting from there without installing anything.

***The Hedge***

:KS

---

### Post by slooksterpsv on 2011-05-15
Not a problem, I've had to fix issues with tons of Windows Machines, seeing an error like that tells me that either the network components of your system are corrupt, the network settings for the device on the OS is corrupt, or the driver is corrupt. - I'm learning more of how to Fix Ubuntu issues cause Windows is the same - slow computer with Windows? Clean registry, remove viruses and spyware, install better antivirus (lower footprint), more RAM, poss. video card, yeah - it's essentially the same.

---

### Post by TracyA on 2011-05-15
Well Guys, looks like it's a no-go...Selecting the Try option just puts ubuntu under windows so therefore it still can't see my network. .. ](*,)
Next I'll try to run it alongside the xp and see how that goes... I'm still a wee bit ascared so first I've got to go and make aaaaabsolute sure I have everything I want backed up .. then I'll play.
I'll let you know if running beside it works.

In the meantime I can also play a bit with the OS without going online. Gotta give ubuntu a chance.. because I'd really like to have an OS that doesn't get viruses! (As I think that's what caused this problem in the first place!)
Tracy

---

### Post by jtarin on 2011-05-15
In Windows go into Device Manager and see about the status of your nic/ethernet card.

---

### Post by tkelito on 2011-05-15
In Windows if you have TRULY tried all the settings, stop.  Run a HDD test. 


A common symptom in Windows of a failing drive (bad sectors usually) is internet not working.  I had a unit today not pulling DNS names correctly, went through the normal 15 different Windows Fixes and then it went into HW diags.  HDD failed Read and Read/Verify tests.

Just something to think about, don't mask a bigger issue with a reload.

---

### Post by jtarin on 2011-05-16
My reinstalls normally take about 15-20 minutes. Less time than most HDD test. However, I do agree......there is a remote possibility it could be a hardware problem.

---

### Post by tkelito on 2011-05-16
> **jtarin said:**
> there is a remote possibility it could be a hardware problem.

With how common HDD failures are these days, I don't trust a device that hasn't seen diagnostics if it has a serious issue.  A reload could mask the problem if it doesn't hit any bad sectors.

To name a few:

Drive Fitness Test
PC-Check
Western Digital Data Lifeguard
SeaTools

---

### Post by TracyA on 2011-05-16
Thanks guys.. Yeah my nic and everything else all looks hunky dorey in the device manager.. 

Would an HDD problem be indicated by deleted IP settings? Hmmm doesn't make sense to me, but yes, I will test it before I reload.

 As I said I've been at this a few days.. and although I'm not a computer geek or anything (well I used to be a Techie for a living but that was back in the days of mainframes, when dinosaurs roamed the land, and there was no such thing as a gig.)  ... anyway therefore I am pretty comfortable so I think I've tried pretty much everything that makes technical sense to me. 

From what I have read, other people have had the same problem and some have had to re-install and some have been lucky enough to have been successful using one of the gazillion suggestions that I've tried. 

I am pretty sure it was caused by a virus (although the scans are showing clean).. I got it from one of the bandwidth monitor programs I was trying.. I was trying several to get one that would give me the reporting I wanted. So therefore that kind of s/w would be accessing my tcp/ip and nic settings. Or possibly there was just a conflict between more than one running concurrently... buuuut I'm still thinkin' virus.. because I just spoke with a friend of mine today and her son had what she thinks was the same thing on his computer. She is going to ask her husband how he got rid of it if he remembers. Unfortunately, with this, and most other viruses, what works for one, doesn't always work for all.
Stay tuned.
T.

---

### Post by Learning Linux 2011 on 2011-05-16
How do/did you connect to the internet?  Do you have an Internet Service provider like Verizon or Comcast?

---

### Post by Learning Linux 2011 on 2011-05-16
I can tell you from experience that I have Comcast and I installed Ubuntu 10.10 and everything works flawlessly.  Ubuntu gets the IP address from Comcast.  It makes no difference if I have Windows installed or not.

You *might* need to reset your cable modem if you have one.  You might also contact your ISP and ask them if there are network troubles (outages) in your area.

Also, are you using a router?

---

### Post by jtarin on 2011-05-16
> **tkelito said:**
> With how common HDD failures are these days, I don't trust a device that hasn't seen diagnostics if it has a serious issue.  A reload could mask the problem if it doesn't hit any bad sectors.

To name a few:

Drive Fitness Test
PC-Check
Western Digital Data Lifeguard
SeaToolsOK....run your checks before backup and reinstall....whatever. I'm for expediency and thoroughness. An image ,virus -free,  I'll take any day to avoid jumping through hoops for anyone. That's why I always backup.

---

### Post by TracyA on 2011-05-17
Ah yes.. I've always said that: "He who laughs last, probably made a backup" .. (sounds like something we should get in a fortune cookie, no?)
Nothing wrong with my modem or my connections or my ISP. I have tried connection on both wireless and ethernet. I have 4 other computers in the house, an xbox, 2 ipod touch's and 2 blackberries, that all use the internet connection. Connection is dandy.

It appears we digress.. Let's get back to the ubuntu question..
My IP and NIC settings have been wiped to blank by what I suspect is a virus, and nothing will let me redefine or reset them.
Ok so .. No time today but I will try to install it alongside XP and see if it creates its own network settings. Which really was my original question .. Let's find out.. I think it will. We shall see. ....

---

### Post by jtarin on 2011-05-17
> **TracyA said:**
> 
It appears we digress.. Let's get back to the ubuntu question..
My IP and NIC settings have been wiped to blank by what I suspect is a virus, and nothing will let me redefine or reset them.
Ok so .. No time today but I will try to install it alongside XP and see if it creates its own network settings. Which really was my original question .. Let's find out.. I think it will. We shall see. ....I believe I saw something about a Network Manager bug the other day.....might check for that before going off the deep end with this virus thing. That's a Windows mind-set for something gone wrong. No offense.

---

### Post by Linux_junkie on 2011-05-17
> **TracyA said:**
> Well Guys, looks like it's a no-go...Selecting the Try option just puts ubuntu under windows so therefore it still can't see my network. .. ](*,)
Next I'll try to run it alongside the xp and see how that goes... I'm still a wee bit ascared so first I've got to go and make aaaaabsolute sure I have everything I want backed up .. then I'll play.
I'll let you know if running beside it works.

In the meantime I can also play a bit with the OS without going online. Gotta give ubuntu a chance.. because I'd really like to have an OS that doesn't get viruses! (As I think that's what caused this problem in the first place!)
Tracy

Hello, you said you tried running Ubuntu under Windows.  Well you don't need to do that, simply insert the Ubuntu CD in drive and restart computer.  Will then boot up using Ubuntu on the CD and not Windows (unless you have computer set up not to boot from CD).   It will run a bit slow from  CD but it should run and should set up network connections.

Have fun playing with Ubuntu

---

### Post by wildmanne39 on 2011-05-17
Hi, and if you think you have a virus,in windows you need to turn off system recovery because the virus can hide in there and as soon as you get it back up and running it comes back, at least that is what happened to me a couple of times when I actually used to use windows.

---

### Post by TracyA on 2011-05-20
Hi All,
Ok well the answer to my question, the title of this thread, is Yes.
I installed Ubuntu as dual-boot with Windows, and although my Windows network settings are corrupt, Ubuntu installed fine with it's own network settings and I am using it right now. (No internet on Windows side).

Well, I've had a chance to play with it a couple of days, and decided I'm going to scrap it all and install Win 7 as a clean install, getting rid of both Ubuntu and XP.  ..I figured from the beginning that this was the way I'd end up going anyway but I thought I'd just try Ubuntu out first.
I am just too impatient, and busy, to take the time to learn a new platform right now. I was trying to get stuff done quickly and felt like I had one hand tied behind my back. .. Sorry Ubuntu, some other time Honey.

Anyway, I now need to figure out how to get rid of Ubuntu so that I can do a clean install of Win 7.
The question does not belong in this thread so I started a new thread. If you guys can help me out now, then c'mon over here .. 
[http://ubuntuforums.org/showthread.php?p=10843671#post10843671](http://ubuntuforums.org/showthread.php?p=10843671#post10843671) 

Thanks very much!
Tracy

---

### Post by wildmanne39 on 2011-05-20
> **TracyA said:**
> Hi All,
Ok well the answer to my question, the title of this thread, is Yes.
I installed Ubuntu as dual-boot with Windows, and although my Windows network settings are corrupt, Ubuntu installed fine with it's own network settings and I am using it right now. (No internet on Windows side).

Well, I've had a chance to play with it a couple of days, and decided I'm going to scrap it all and install Win 7 as a clean install, getting rid of both Ubuntu and XP.  ..I figured from the beginning that this was the way I'd end up going anyway but I thought I'd just try Ubuntu out first.
I am just too impatient, and busy, to take the time to learn a new platform right now. I was trying to get stuff done quickly and felt like I had one hand tied behind my back. .. Sorry Ubuntu, some other time Honey.

Anyway, I now need to figure out how to get rid of Ubuntu so that I can do a clean install of Win 7.
The question does not belong in this thread so I started a new thread. If you guys can help me out now, then c'mon over here .. 
[http://ubuntuforums.org/showthread.php?p=10843671#post10843671](http://ubuntuforums.org/showthread.php?p=10843671#post10843671) 

Thanks very much!
Tracy
Hi, this link had the information you need to uninstall ubuntu.  [http://members.iinet.net.au/~herman546/p18.html](http://members.iinet.net.au/~herman546/p18.html)

---

