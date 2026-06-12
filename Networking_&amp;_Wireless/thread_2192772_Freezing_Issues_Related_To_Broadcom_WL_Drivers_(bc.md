---
title: "Freezing Issues Related To Broadcom WL Drivers (bcmwl-kernel-source)"
date: 2013-12-09
forum: Networking &amp; Wireless
---

### Post by Kirk Schnable on 2013-12-09
We've been noticing a large amount of issues with our netbooks periodically freezing.  When the machine freezes, it becomes totally unresponsive, and isn't able to drop to TTY.  The keyboard and the mouse become unresponsive.  The system logs stop abruptly, and so there is nothing in the logs which indicate what the source of the problem is.

We are running Xubuntu 12.04 LTS, with the latest bcmwl-kernel-source currently available from the Ubuntu repository.  I think we've seen this issue on more than one Broadcom chipset, but one that comes to mind right now is BCM43224.

In some test cases, we ran the computers with network cables instead of using the wireless, and the netbooks in our test cases never froze while they were using a wired network.  The freezing issues therefore appear to be related to the usage of the wireless connection.

It's been difficult for us to narrow this problem down due to the lack of logs, but we're confident enough in our conclusion that we'd like to find out if anyone else has experienced similar issues with this driver, and what some possible resolutions might be.

Is there any way that we can increase the verbosity of the logging, so we can gather some more information?  

Thanks,
Kirk

---

### Post by Kirk Schnable on 2014-01-02
I talked with chili555 about this issue, on IRC.  I'm recording the chat here for my reference and the reference of anyone who may find this thread in the future with a similar problem.

> **"IRC"]
<Kirk> Thanks for hopping on IRC with us.
<chili555> Afternoon, sir
<chili555> what can I do to help?
<Kirk> I'm compiling a list of our chipsets from asset tracking, we've got 3 or 4 different ones.
<chili555> Have you checked here? [https://help.ubuntu.com/community/BroadcomSTA%28Wireless%29](https://help.ubuntu.com/community/BroadcomSTA%28Wireless%29)
<Kirk> BCM4312, BCM4313, BCM43224, and BCM43228 according to my asset tracking.  One of those might be one we've replaced.  We're trying to go all dual-band.
<Kirk> We are currently running Xubuntu 12.04 on everything we have in production.  We're using the Broadcom STA (WL) drivers from the Ubuntu repo.  (bcmwl-kernel-source)
<Kirk> The BCM43222 cards were a little project to get 30 or so old laptops back into production use... we may just abandon those cards.
<chili555> The model numbers don't help much. the pci.id like 14e4:4315 is very useful
<Kirk> What we really want to figure out and get pinned down is this freezing issue we're having.
<Kirk> [http://ubuntuforums.org/showthread.php?t=2192772](http://ubuntuforums.org/showthread.php?t=2192772)
<chili555> what is freezing?
<Kirk> Everything dude.  The machines totally seize up.
<Kirk> But we have narrowed it down to the point we believe it's wireless related.  We have a few machines that do it very often and we've tested them on ethernet connections with the wireless switch turned off, and they do not freeze in that test case.
<chili555> I'd want to see the pci.id to start helping: lspci -nn | grep 0280
<Kirk> I've got a Dell Latitude next to me which is one of the models we're having the problem with.  Moment please.
<chili555> ok
<Kirk> This one's a BCM43224 chipset.  14e4:4353.
<Kirk> I believe we have probably at least 200 of these cards out there in production in this model netbook.
<Kirk> I've heard from some of our end users that they freeze 2-3 times a day and have to be rebooted.
<Kirk> When they freeze they do not drop to TTY, the logging stops, and they become totally non-responsive unless you press and hold the power button and kill them.
<Kirk> We have one end user who freezes 5-6 times a day so we've made her our test subject.  When she's used ethernet cables and switched the WiFi off, she hasn't frozen.
<chili555> bcmwl-kernel-source is supposed to be correct.  My first step would be to try an earlier version said:**
> http://askubuntu.com/questions/337643/problem-with-ubuntu-12-04-and-ideapad-n581-broadcom/[/url]
<chili555> Remove bcmwl-kernel-source and install the earlier version
<Kirk> We can certainly give that a try.
<Kirk> We'd need to come up with a way to deploy that with Puppet if it turned out to solve the problem, but I'll certainly entertain testing it.
<chili555> with an ethernet connection, it should take about two minutes
<Kirk> Unfortunately (as I'm sure you've noticed with the day(s) gaps in my replies sometimes) I don't have our test machine here but I will be able to get my hands on it next week when the end-user returns.
<Kirk> The Latitudes we have in our office don't seem to freeze. :P  That's just usually how it goes right?
<Kirk> So I probably don't have a machine to try with until next week.
<Kirk> Anything else off the top of your head which we can try next week?
<chili555> Yes, trouble or no trouble with no real explanation with Broadcom cards?? Yes, exactly!
<Kirk> Hahaha.
<Kirk> Sounds like our experience.
<howto> ow! my squealyspooch!
<chili555> If the earlier version doesn't help, then I'd try the very newest as outlined in my forum post
<chili555> shall I await your PM after you test?
<Kirk> Okay yeah I was doing that for a different chipset\different problem.  We can certainly try your instructions on a test case with this "freezing issue" also.


We'll give this a try next week and report back soon!  The other thread he's referring to is here:  [http://ubuntuforums.org/showthread.php?t=2192764&p=12889336#post12889336](http://ubuntuforums.org/showthread.php?t=2192764&p=12889336#post12889336)

---

### Post by Kirk Schnable on 2014-01-14
I apologize that it took much longer than we expected to get ahold of the test machine.  I've installed the older driver on the test machine today.  We will see how it goes!

---

### Post by chili555 on 2014-01-14
Fingers crossed.

---

