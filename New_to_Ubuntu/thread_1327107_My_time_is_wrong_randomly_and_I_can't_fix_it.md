---
title: "My time is wrong randomly and I can't fix it"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by slughappy1 on 2009-11-15
My time has been right until tonight. I changed the look of the clock to custom. I don't understand how my time changed. The time zone is set correctly, but the time wont be fixed. I have a dual boot and Windows 7 shows the correct time. How can I fix Ubuntu's time?

Sorry if I make little sense, really tired.

---

### Post by nitstorm on 2009-11-15
Go to Systems --> Administration --> Time and Date

There you'll need to unlock the settings with your password, then in the configuration bar, choose either "manual" and set the time or "Keep synchronized with Internet servers"

cheers :D

---

### Post by slughappy1 on 2009-11-15
I did that. "Time zone:" is set to the correct place, "Configuration" is set to "Keep Synchronized with Internet servers", and "Time servers" has one checked box in Las Vegas because that is the closest site to mine. My time is still wrong. When I set it to Manual it doesn't change.

---

### Post by nitstorm on 2009-11-15
Go to System --> Administration -->Login Window . Under the general tab there is an option called Use 24-hour clock select the option "Auto"  . hopefully that'll work :)

---

### Post by The Cog on 2009-11-15
It might be interesting to see the result of this command:
> sudo ntpdate ntp.ubuntu.com

---

### Post by slughappy1 on 2009-11-15
@nitstorm, System -> Administration -> Login Window is not there in Karmic.
@The Cog, The output for that is ```
jason@Barnaby:~$ sudo ntpdate ntp.ubuntu.com
[sudo] password for jason: 
15 Nov 12:48:03 ntpdate[2301]: adjust time server 91.189.94.4 offset -0.000160 sec
jason@Barnaby:~$ 

```

---

### Post by The Cog on 2009-11-17
Hmm. This:
offset -0.000160 sec
tells us that the system time is correct. So I guess it'a an issue with the way the clock displays the time. I don't know where to go from there though.

---

### Post by ukripper on 2009-11-17
can you reboot and go into BIOS and see if time dispayed there is correct?

---

### Post by slughappy1 on 2009-11-17
In bios the time is correct, when Ubuntu is set to the correct Time Zone. I live in SLC Utah and have the time zone set to Boise Id. If I have it set to any other time zone, which I tried, the time in Ubuntu does not change. I tested the time and this is what I got.```

_BIOS_         _Ubuntu_         _Time Zone_         _Actual Time_ 
5:50 PM      4:50 PM        Europe/Paris      9:50 AM
9:50 AM      4:50 PM        America/Boise     9:50 AM

```
Why would Ubuntu's time not change? Also, I have Windows 7 installed and it's time stays correct if Ubuntu's time zone is set to Boise. If the time zone is not set correctly, Windows time is wrong as well.

---

### Post by winotree on 2009-11-17
This may or may not help *but* there's a thread hereabouts somewhere re: time, and how Windows and Linux read and set computer time differently from each other.  The point is this may be what is causing the discrepancies you're seeing between the two systems.  And then again, maybe not.  :?  ;)

---

### Post by snkiz on 2009-11-17
your Bois needs to be set to GMT I believe for auto sync to work. Win Xp used to actually change the bios time, witch messed up Ubuntu. Not sure if win 7 still does that.

---

### Post by slakkie on 2009-11-17
> **snkiz said:**
> your Bois needs to be set to GMT I believe for auto sync to work. Win Xp used to actually change the bios time, witch messed up Ubuntu. Not sure if win 7 still does that.

Not needed, you need to change one config file to make it work.
[http://www.shivaranjan.com/2009/06/20/how-to-prevent-ubuntu-linux-from-resetting-or-changing-computer%E2%80%99s-bios-or-hardware-clock/](http://www.shivaranjan.com/2009/06/20/how-to-prevent-ubuntu-linux-from-resetting-or-changing-computer%E2%80%99s-bios-or-hardware-clock/)

---

### Post by snkiz on 2009-11-17
> **slakkie said:**
> Not needed, you need to change one config file to make it work.
[http://www.shivaranjan.com/2009/06/20/how-to-prevent-ubuntu-linux-from-resetting-or-changing-computer%E2%80%99s-bios-or-hardware-clock/](http://www.shivaranjan.com/2009/06/20/how-to-prevent-ubuntu-linux-from-resetting-or-changing-computer%E2%80%99s-bios-or-hardware-clock/)

I disagree why should you have to change Ubuntu to to manage windows wrong behavior. It would be better to set your bios to utc and fix the time setting in windows.

---

### Post by slughappy1 on 2009-11-17
I've already checked that. According to [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime) ```
...
As of to Intrepid (8.10), UTC=no is now default.
...

```

I also don't see why changing the BIOS time would do anything in Ubuntu. If you look at my post #9, the BIOS time changed but Ubuntu's time didn't.

---

### Post by winotree on 2009-11-17
> **slakkie said:**
> Not needed, you need to change one config file to make it work.
[http://www.shivaranjan.com/2009/06/20/how-to-prevent-ubuntu-linux-from-resetting-or-changing-computer%E2%80%99s-bios-or-hardware-clock/](http://www.shivaranjan.com/2009/06/20/how-to-prevent-ubuntu-linux-from-resetting-or-changing-computer%E2%80%99s-bios-or-hardware-clock/)
I do believe that *that* is the article I was thinking of -- so it wasn't in the forums after-all.  [Mumbles to self as he bookmarks page].

---

### Post by slakkie on 2009-11-17
> **snkiz said:**
> I disagree why should you have to change Ubuntu to to manage windows wrong behavior. It would be better to set your bios to utc and fix the time setting in windows.Good luck disagreeing. Fact remains that you can fix it.

---

### Post by slughappy1 on 2009-11-17
If it can be fixed, why is Ubuntu's time NOT changing?

---

### Post by winotree on 2009-11-17
Would it require a reboot?

---

### Post by slughappy1 on 2009-11-17
I have rebooted many times.

---

### Post by slughappy1 on 2009-11-17
So I was able to finally fix it. It turns out that some how gmt_time got enabled. I had to uncheck it in Configuration Editor apps -> panel -> applets -> clock_screen0 -> prefs

---

### Post by quinnten83 on 2009-11-17
You can try to alter the way your time is displayed in gconf-editor
in /apps/panel/applets/clock_screen0/prefs.
change the format to costum and then in costum format place:
```
<span font =  "bold 12" >%R  %a %d %B %y  </span>
```

the link on this page will tell you what you can display:
[http://nl2.php.net/strftime]("http://nl2.php.net/strftime")

If you say that you changed the way the clock is displayed, it is very difficult to go back, but you can try this, see if it helps.

Q.

---

### Post by quinnten83 on 2009-11-17
Never mind, got beaten to it.

---

### Post by rykel on 2009-11-18
Hey guys,

I am having a similar problem too on Karmic...

My Timezone and Servers are all correct and selected, but the time on my clock is still wrong.

ntpdate also showing some "errors"...

> sudo ntpdate ntp.ubuntu.com
18 Nov 17:15:00 ntpdate[20176]: the NTP socket is in use, exiting


Please help?

---

### Post by slughappy1 on 2009-11-18
How is it wrong? What time does your bios say? What time does Ubuntu say? What time is it actually?

---

### Post by leorolla on 2009-12-02
@rykel
This is a conflict with ntp. See [http://ubuntuforums.org/showthread.php?t=1341576](http://ubuntuforums.org/showthread.php?t=1341576)

@slughappy1

I guess you are root on both Ubuntu and Windows, right?

Could you run

date ; sudo ntpdate ntp.ubuntu.com ; date

give us the output and tell us exactly what time you did it?

---

### Post by slughappy1 on 2009-12-02
If by root you mean the admin of my computer then yes. I didn't enable a root account in Ubuntu, just use sudo and su when needed. I fixed my time, as I think I mentioned in a previous post. I might not have though. I still can do that if you want.

```
jason@Barnaby:~$ date ; sudo ntpdate ntp.ubuntu.com ; date
Wed Dec  2 09:57:58 MST 2009
[sudo] password for jason: 
 2 Dec 09:58:03 ntpdate[3410]: the NTP socket is in use, exiting
Wed Dec  2 09:58:03 MST 2009
jason@Barnaby:~$ 

```
I have unfortunately seen that error before and still don't know how to fix it.

---

### Post by leorolla on 2009-12-02
You clock is fine. Maybe 1-3 minutes late.

Please run this
```
date
sudo /etc/init.d/ntp stop
sudo ntpdate ntp.ubuntu.com
sudo ntpdate ntp
sudo /etc/init.d/ntp start
date
```

When you boot in Windows it is scrambled?

What do you see at BIOS setup?

---

