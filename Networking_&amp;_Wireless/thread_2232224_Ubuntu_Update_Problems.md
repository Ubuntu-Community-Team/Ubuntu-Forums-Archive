---
title: "Ubuntu Update Problems"
date: 2014-06-30
forum: Networking &amp; Wireless
---

### Post by ken0069 on 2014-06-30
I don't know where to put this so I decided to just post it here.  If there's a better section for it then please move it.

I've got an internet connection problem that seems to mostly involve Linux updates and some other downloads and I was wondering if there are any IT experts here that I could get some info from as my ISP has refused to help me any further.  FYI this involves multiple computers and a laptop on my network that run Ubuntu 12.04/14.04 and Mint 17 and they are all "multiboot" systems with each Windows and Linux OS on it's own hard drive.  

This problem involves HTTP downloads via both Windows and Linux and updates to both Ubuntu and Mint however Windows updates doesn't seem to be affected at all in update area.  The laptop works fine with both Linux and Windows on another wireless service that I have access to, which is how I do some of these HTTP downloads.  It is a pain in the butt though to have to drive somewhere to do a download!

What's happening is when I'm notified of Ubuntu updates and I select the "Install Now" option there's a problem with data throughput.  I've got NetSpeed applet installed on all systems and when the update download starts it will pass data up around 250 to 350 kbps for about 10 seconds then it starts dropping off and within a short time goes to zero.  It will sit at zero for a minute or two then it will pass data again for a short period of time then stop again??  It's almost like a cache burst then it runs out, refils then passes data then runs out again, etc.  And BTW, it does the same thing if I sudo the update in terminal.

I've also tried downloading stuff from Distrowatch via HTTP and NONE of those downloads will complete successfully.  I've also done downloads via FTP and those will usually complete but not without a disconnect or two and restarting.

FYI, this isn't something new as it started mid August of last year.  At that time I contacted tech support about it and got every excuse in the world about why it wasn't THEIR problem.  When I proved their excuses wrong they would put out another and that circus ran for about 3 weeks and that was when they told me that my USB data card was too old and no longer supported?  They claimed that it was defective but the funny part of this is that I have TWO of those devices and both do the EXACT same thing??  So what is the chance that BOTH of them would suffer the same failure when the backup one basically has been sitting on the shelf for the better part of 3 years?

So here I sit with a connection that takes all day or more to do a single kernel update because of the starting and stopping issue and with an ISP that doesn't care if my connection works or not.  

Please don't suggest I change providers because the only other options to me are satellite (twice as expensive and usually not much better) and dialup and you know what that is.  

Any info on what could cause this would be appreciated.  

Thanks,

Ken

---

### Post by sandyd on 2014-06-30
Ive moved this to networking and wireless where you may get better help.

----------------------

Try running a mtr to the Ubuntu Servers for your country

Install MTR
```

sudo apt-get install mtr
```

Run MTR (this is for USA)
```

mtr us.archive.ubuntu.com
```

Let it run for a while, and then press the letter 'p' on your keyboard to pause MTR

You can then wipe out personally identifiable information and post a screenshot here.

---

### Post by ken0069 on 2014-06-30
Thanks for your reply and for moving this thread.  I started to put it here but wasn't sure so I just stuck it in "General".  

OK I see.  MTR is a traceroute program and I've tried to run traceroute from a Windows command prompt back when the problem first manifest itself but it doesn't work.  I questioned tech support about it last August as I was trying to identify where the packet loss or bottleneck was but I was told that traceroute was disabled on the server and that they couldn't enable it??  :frown:

I did try MTR just now and it doesn't work either.

And yes, this is the first time I've ever had an ISP that wouldn't allow a traceroute as I use to do that all the time on dialup trying to find good routes to game servers. 

This doesn't leave many options does it?

---

### Post by ken0069 on 2014-09-29
UPDATE:  On the 9th of July I noticed that my internet connection was  doing very well.  Updates to Ubuntu around 3am were showing data  throughput up around 370kbps and that is screaming fast for a 3G  cellular connection.  Next day the connection was in the toilet again so  I got to checking my IP addresses where I log in on my forum.  The IP  address that worked very well was different from the one that didn't so I  rebooted my router until it came back up on the "good" IP address and  all was well again.  

Fast forward to last week and after being  able to use the "good" IP address for that long a period of time all of a  sudden THAT one went in the toilet also and now it's worse than it was  before??

All this begs the question of why it worked OK for about  9 weeks and now it doesn't so what got changed by whom and for what  reason?  More questions than answers but IMHO seems that someone is  jerking me around for some reason or the other.  

Oh, and just in  case you are wondering who this provider is, it's Ntelos Wireless, a  regional cell service provider here in the mid Atlantic region of the  USA.

---

### Post by ian-weisser on 2014-09-29
Well, seems like you have your answer.
Your ISP is issuing out the IP addresses.
And apparently throttling based on the IP address.

---

### Post by ken0069 on 2014-09-29
> **ian-weisser said:**
> Well, seems like you have your answer.
Your ISP is issuing out the IP addresses.
And apparently throttling based on the IP address.

Yeah but it just doesn't make sense since I'm on a metered service anyway and I never run over my monthly allocation??  Looks to me like it would make sense for them to make it as fast as possible so I'd run out and have to buy more?  I guess not tough.  

Ennywho, I'm looking for another ISP and hopefully I'll find one that will work like it's suppose to.  It's a PITA to try doing 150MB of updates on Ubuntu or Mint with the connection acting like it is now.  :frown:

---

