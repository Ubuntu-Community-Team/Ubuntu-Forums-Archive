---
title: "Urgant!!! 10.04 rc is unstable!!!"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by crazyavery4444 on 2010-04-27
I was hoping this problem would fix itself (or be fixed in updates) and up until now it wasnt bothering me, when launching a full screen game or almost any program with rhythm box running the screen goes blank and the error "cannot write bytes: broken pipe" on 6 lines flashing roughly 8 or 9 times, it then goes to say Ubuntu is running in low graphics mode. After a restart, everything is working fine and there is no error detected. This error wasn't bothering me until today becuase it seemed to occur only while launching the game Urban Terror, before today, I had narrowed it down to starting the game when my CPU was under load (P4 here) but even after waiting for the CPU frequency scale to go to zero, it still happens. I've recently downloaded another game, Tremulous, and the same thing happens. I've found a similarity in both of those games, they have both been coded it C# so it appears that ubuntu 10.04 (at the moment anyway) is having problems dealing with C#.

---

### Post by arrrghhh on 2010-04-27
What video card are you running?  Did you install the proprietary drivers if they were needed?

---

### Post by MCVenom on 2010-04-27
> **arrrghhh said:**
> What video card are you running?  Did you install the proprietary drivers if they were needed?
Also, did you file a bug on launchpad?

---

### Post by crazyavery4444 on 2010-04-27
> **arrrghhh said:**
> What video card are you running?  Did you install the proprietary drivers if they were needed?
integrated, and built into the kernel

---

### Post by crazyavery4444 on 2010-04-27
> **BlackOtaku said:**
> Also, did you file a bug on launchpad?
launchpad fails to load on my connection, it takes roughly 15 minutes and I dont have the patients (verizon DSL@3 MBS)

---

### Post by arrrghhh on 2010-04-27
> **crazyavery4444 said:**
> integrated, and built into the kernel

That doesn't help... what card?  lspci or lshw output please?

---

### Post by crazyavery4444 on 2010-04-28
> **arrrghhh said:**
> That doesn't help... what card?  lspci or lshw output please?
I'm not sure, but I'd go with Ispci becuase to determine my card speed I have to go to PCI devices on the system profiler and benchmarked. the name of the card (again, according to system profiler and benchmark) is, Intel Corporation 82915G/GV/910GL integrated Graphics controller (rev 04)

---

### Post by teh603 on 2010-04-28
> **crazyavery4444 said:**
>  Ispci That's a lowercase L, not an uppercase I... Its supposed to be lspci.

---

### Post by LowSky on 2010-04-28
> **teh603 said:**
> That's a lowercase L, not an uppercase I... Its supposed to be lspci.

to be more clear ```
lspci
``` is a terminal command.

It will give all the information of the computers parts that run on the PCI bus.

also when was the last time you updated the system? the RC has new fixes out daily.

---

### Post by arrrghhh on 2010-04-28
I guess I was not clear to the OP.  I'm trying to determine what card you're running - you keep answering questions like you know the answer, but you obviously are just making great leaps of faith in your answer.

Please calm down, and take it one step at a time.  Don't just snap off an answer right away, perhaps we'd like the right answer rather than just any answer... make sense?

So the lspci command was explained wonderfully by LowSky, can you please paste the output of that command?

---

### Post by AlanR8 on 2010-04-28
My response would be "Yes it IS stable".

Have been using Lucid since Alpha 2 and apart from some early issues with Plymouth, well documented, no issues at all.

Everything's subjective but I also appreciate you have your own hardware set up and according to your post you're running a game. 

I have Lucid on this HP Mini, Sony Vaio laptop in my signature line, an HP Pavilion laptop and a home built desktop PC.

Everything just works. This I feel gives a fair spread of hardware, but I do admit I don't run games on computers.

That's what gaming machines are for!

Just my 2 pence worth.

Looking forward to the full release tomorrow of the most advanced version of Ubuntu and a Long Term Support version!

---

### Post by crazyavery4444 on 2010-04-28
> **LowSky said:**
> to be more clear ```
lspci
``` is a terminal command.

It will give all the information of the computers parts that run on the PCI bus.

also when was the last time you updated the system? the RC has new fixes out daily.

> **arrrghhh said:**
> I guess I was not clear to the OP.  I'm trying to determine what card you're running - you keep answering questions like you know the answer, but you obviously are just making great leaps of faith in your answer.

Please calm down, and take it one step at a time.  Don't just snap off an answer right away, perhaps we'd like the right answer rather than just any answer... make sense?

So the lspci command was explained wonderfully by LowSky, can you please paste the output of that command?
thanks to low sky for explaing that

as for you arrrghhh, youre kind of an *** so either deal with my incompetence or **** off, but here is the output of that command

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation 82915G Integrated Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)

---

### Post by LowSky on 2010-04-28
> **crazyavery4444 said:**
> thanks to low sky for explaing that

as for you arrrghhh, youre kind of an *** so either deal with my incompetence or **** off, but here is the output of that command


Come on dude, be nice. arrrghh is trying to help.
It does looks like you were correct in your original answer.```

Intel Corporation 82915G/GV/910GL Integrated Graphics Controller
```


Just to ask How did you install Urban Terror? It could be that you used the wrong method

I did find a DEB packaged version here. It might actually work better
[http://www.playdeb.net/updates/ubuntu/9.04/?q=Urban+Terror](http://www.playdeb.net/updates/ubuntu/9.04/?q=Urban+Terror)

---

### Post by MCVenom on 2010-04-28
> **crazyavery4444 said:**
> as for you arrrghhh, youre kind of an *** so either deal with my incompetence or **** off, 

Excuse me? He is trying to help you. I saw nothing at all rude in his post, he's just telling to slow down a bit... You seemed to be trying to assume things without actually doing them in your earlier posts. 

If you feel that someone is being rude to you, please ask them *lightly* to be a bit more understanding of your issue/point of view, please don't resort to throwing around insults and poorly concealed profanity.

---

### Post by lisati on 2010-04-28
> **crazyavery4444 said:**
> thanks to low sky for explaing that

as for you arrrghhh, youre kind of an *** so either deal with my incompetence or **** off, but here is the output of that command


Language, please! We appreciate your frustration.

Remember, we are all volunteers here and want to keep the forum as family friendly as possible.

---

### Post by LowSky on 2010-04-28
Also I did a bit of searching and that Intel chipset doesn't always play nice with Ubuntu, especially with screen resolutions. 

If your running things like Desktop Effects or the full version of Compiz-Fusion you might have gameplay issues aswell. The best thing to do is to turn off the effects while game playing. If you use Compiz the best option is to install compiz-fusion icon which will place a icon in the notificaiton area for easy mode switching.

---

### Post by arrrghhh on 2010-04-28
I am kind of curt with people, but I was not trying to belittle or be rude to you.

Seems you have a GX280, which indeed has an Intel GPU.  Just wanted to rule that out...

When this error occurs, can you drop to a terminal, CTRL-ALT-F1?  If so, I'd like you to do that instead of rebooting.  Then I'd like to see if you have anything in /var/log/messages or /var/log/syslog.  May help us figure out what is actually going on...

---

### Post by PRC09 on 2010-04-28
> launchpad fails to load on my connection, it takes roughly 15 minutes and I dont have the patients (verizon DSL@3 MBS)

> as for you arrrghhh, youre kind of an *** so either deal with my incompetence or **** off, but here is the output of that command


You sir are going to be a wonderful asset to the Ubuntu world!!!!

---

### Post by MCVenom on 2010-04-28
> **PRC09 said:**
> You sir are going to be a wonderful asset to the Ubuntu world!!!!
Now now, I think we've said enough. I'm sure the OP doesn't need anymore scolding or rudeness, from any of us. Let's concentrate on actually *helping him.* :p

---

### Post by arrrghhh on 2010-04-28
> **BlackOtaku said:**
> Now now, I think we've said enough. I'm sure the OP doesn't need anymore scolding or rudeness, from any of us. Let's concentrate on actually *helping him.* :p

Agreed.  Let's put the petty stuff behind and just help the OP...  OP, that goes for you as well.  Please leave the nasty comments and just help us help you by providing the information we ask for.

---

### Post by crazyavery4444 on 2010-04-28
> **LowSky said:**
> Come on dude, be nice. arrrghh is trying to help.
It does looks like you were correct in your original answer.```

Intel Corporation 82915G/GV/910GL Integrated Graphics Controller
```Just to ask How did you install Urban Terror? It could be that you used the wrong method

I did find a DEB packaged version here. It might actually work better
[http://www.playdeb.net/updates/ubuntu/9.04/?q=Urban+Terror](http://www.playdeb.net/updates/ubuntu/9.04/?q=Urban+Terror)

> **LowSky said:**
> Also I did a bit of searching and that Intel chipset doesn't always play nice with Ubuntu, especially with screen resolutions. 

If your running things like Desktop Effects or the full version of Compiz-Fusion you might have gameplay issues aswell. The best thing to do is to turn off the effects while game playing. If you use Compiz the best option is to install compiz-fusion icon which will place a icon in the notificaiton area for easy mode switching.

> **arrrghhh said:**
> I am kind of curt with people, but I was not trying to belittle or be rude to you.

Seems you have a GX280, which indeed has an Intel GPU.  Just wanted to rule that out...

When this error occurs, can you drop to a terminal, CTRL-ALT-F1?  If so, I'd like you to do that instead of rebooting.  Then I'd like to see if you have anything in /var/log/messages or /var/log/syslog.  May help us figure out what is actually going on...

> **BlackOtaku said:**
> Now now, I think we've said enough. I'm sure the OP doesn't need anymore scolding or rudeness, from any of us. Let's concentrate on actually *helping him.* :p

wow that was alot of replies!
sorry for my bad language, I do have a short temper (probably figured that out on your own.) so in order, I downloaded the .zip file from the urban terror site and just enabled executing on the file and it ran fine (in 9.10) it was when I switched to 10.04 (at beta 1) that I started to have problems, i'll get that .ded though. I did have a problem with the frame rate while desktop effects were running, disabling it worked for my frame rate, but dosnt help the chances of starting the game ( I say chances because its sort of a gamble to launch the game.) that resolution problem with intel GPU's, I had it and remedied it by switching from my stock monitor, to one that I found in my attic that was bigger and thinner (haven't a clue why I wasnt using that one in the first place) the logs are rather long to post here, would you like me to put them up on a file sharing site for you? as for dropping into terminal, I have yet to try that, but I will next time this occurs. and last, but not least, Thank you, BlackOtaku!

---

### Post by LowSky on 2010-04-28
You can put them here, just use [code] tags, it will condence the data to a scrollable window

its the button that looks like this: **# **if you use the Go advanced option for posting

---

### Post by crazyavery4444 on 2010-04-28
> **arrrghhh said:**
> I am kind of curt with people, but I was not trying to belittle or be rude to you.

Seems you have a GX280, which indeed has an Intel GPU.  Just wanted to rule that out...

When this error occurs, can you drop to a terminal, CTRL-ALT-F1?  If so, I'd like you to do that instead of rebooting.  Then I'd like to see if you have anything in /var/log/messages or /var/log/syslog.  May help us figure out what is actually going on...
didnt check both logs before posting, syslog does have quite some stuff in it, but its short enough to post here

```
Apr 28 07:46:07 avery-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="593" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Apr 28 07:46:24 avery-desktop anacron[2234]: Job `cron.daily' terminated
Apr 28 07:46:24 avery-desktop anacron[2234]: Normal exit (1 job run)
Apr 28 08:17:01 avery-desktop CRON[2435]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 28 09:17:01 avery-desktop CRON[2443]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 28 10:17:01 avery-desktop CRON[2451]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 28 11:17:01 avery-desktop CRON[2459]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 28 11:53:12 avery-desktop dhclient: DHCPREQUEST of 10.0.0.4 on eth0 to 10.0.0.1 port 67
Apr 28 11:53:12 avery-desktop dhclient: DHCPACK of 10.0.0.4 from 10.0.0.1
Apr 28 11:53:12 avery-desktop dhclient: bound to 10.0.0.4 -- renewal in 41689 seconds.
Apr 28 12:00:01 avery-desktop CRON[2470]: (root) CMD (if [ -x /usr/sbin/sbackupd ]; then /usr/sbin/sbackupd; fi;)
Apr 28 12:17:01 avery-desktop CRON[2475]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 28 13:17:01 avery-desktop CRON[2483]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 28 14:17:01 avery-desktop CRON[2491]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 28 15:17:01 avery-desktop CRON[2499]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 28 15:24:16 avery-desktop avahi-daemon[626]: Invalid query packet.
Apr 28 15:25:29 avery-desktop avahi-daemon[626]: last message repeated 5 times
Apr 28 15:59:11 avery-desktop avahi-daemon[626]: Invalid query packet.
Apr 28 16:00:30 avery-desktop avahi-daemon[626]: last message repeated 5 times
Apr 28 16:17:02 avery-desktop CRON[2726]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 28 16:35:06 avery-desktop avahi-daemon[626]: Invalid query packet.
Apr 28 16:36:32 avery-desktop avahi-daemon[626]: last message repeated 5 times
Apr 28 16:58:26 avery-desktop avahi-daemon[626]: Invalid query packet.
Apr 28 16:59:33 avery-desktop avahi-daemon[626]: last message repeated 5 times
Apr 28 17:17:01 avery-desktop CRON[7401]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 28 17:21:26 avery-desktop avahi-daemon[626]: Invalid query packet.
Apr 28 17:22:34 avery-desktop avahi-daemon[626]: last message repeated 2 times
Apr 28 17:26:27 avery-desktop avahi-daemon[626]: Invalid query packet.
Apr 28 17:27:34 avery-desktop avahi-daemon[626]: last message repeated 2 times
```

---

### Post by crazyavery4444 on 2010-04-28
> **LowSky said:**
> You can put them here, just use [code] tags, it will condence the data to a scrollable window

its the button that looks like this: **# **if you use the Go advanced option for posting
 
the log file is so long, that it wont allow me to paste in in the dialog box, even by typing ([CODE]) infront of it.

---

### Post by arrrghhh on 2010-04-28
Yea, using the "code" feature make things look nice.

I don't see anything glaring as far as a reason for the hangup, the reason I suggested dropping to a terminal is if you reboot, some of the error logs, if not all, will be lost.

It will make it more difficult to paste, I find using the python package "ix" works wonders - I just cat something and pipe it to the "ix" program, and it puts it on the clipboard AND dumps a link that also has the same text in it.  Very nice!  I use it on my server, but I'm sure it's just the same on a desktop machine.

Just read that it won't let you post because it's too long.  Can you post the last 20 lines or so shortly after the problem occurs?

---

### Post by crazyavery4444 on 2010-04-28
> **arrrghhh said:**
> Yea, using the "code" feature make things look nice.

I don't see anything glaring as far as a reason for the hangup, the reason I suggested dropping to a terminal is if you reboot, some of the error logs, if not all, will be lost.

It will make it more difficult to paste, I find using the python package "ix" works wonders - I just cat something and pipe it to the "ix" program, and it puts it on the clipboard AND dumps a link that also has the same text in it.  Very nice!  I use it on my server, but I'm sure it's just the same on a desktop machine.

Just read that it won't let you post because it's too long.  Can you post the last 20 lines or so shortly after the problem occurs?
well I can drop into a terminal, however its exactly like I just booted into Xterm, login prompt and everything, as for that python package, could you please post the full name? sudo apt-get install ix yielded no results, searching synaptic had no python packages either.

can do

```
Apr 28 17:36:55 avery-desktop kernel: [   12.929404] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr 28 17:36:55 avery-desktop kernel: [   13.158774] type=1505 audit(1272490615.689:5):  operation="profile_load" pid=742 name="/usr/share/gdm/guest-session/Xsession"
Apr 28 17:36:55 avery-desktop kernel: [   13.161701] type=1505 audit(1272490615.693:6):  operation="profile_replace" pid=744 name="/sbin/dhclient3"
Apr 28 17:36:55 avery-desktop kernel: [   13.162439] type=1505 audit(1272490615.693:7):  operation="profile_replace" pid=744 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Apr 28 17:36:55 avery-desktop kernel: [   13.162845] type=1505 audit(1272490615.693:8):  operation="profile_replace" pid=744 name="/usr/lib/connman/scripts/dhclient-script"
Apr 28 17:36:55 avery-desktop kernel: [   13.236370] type=1505 audit(1272490615.769:9):  operation="profile_load" pid=745 name="/usr/bin/evince"
Apr 28 17:36:55 avery-desktop kernel: [   13.246159] type=1505 audit(1272490615.777:10):  operation="profile_load" pid=745 name="/usr/bin/evince-previewer"
Apr 28 17:36:55 avery-desktop kernel: [   13.252415] type=1505 audit(1272490615.785:11):  operation="profile_load" pid=745 name="/usr/bin/evince-thumbnailer"
Apr 28 17:36:55 avery-desktop kernel: [   13.399599] type=1505 audit(1272490615.929:12):  operation="profile_load" pid=749 name="/usr/lib/cups/backend/cups-pdf"
Apr 28 17:36:55 avery-desktop kernel: [   13.400678] type=1505 audit(1272490615.933:13):  operation="profile_load" pid=749 name="/usr/sbin/cupsd"
Apr 28 17:36:56 avery-desktop kernel: [   13.465381] type=1505 audit(1272490615.998:14):  operation="profile_load" pid=750 name="/usr/sbin/tcpdump"
Apr 28 17:36:57 avery-desktop kernel: [   15.348429] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
```

well it seems that 1 error happens alot, before the first line, its all the same error as all the lines below it.

---

### Post by crazyavery4444 on 2010-04-28
Well, I can drop into a terminal and start a new X session so I no longer have to reboot i did ctrl+alt+f1 then logged in, then typed in

```
startx -- :1
```

its nice, but I prefer the error not happen at all.

---

