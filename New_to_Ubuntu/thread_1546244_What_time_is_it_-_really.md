---
title: "What time is it - really?"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by J.Alec.West on 2010-08-05
I've seen posts similar to this in the Ubuntu forums.  But, I've never seen anyone give a definitive answer on why it happens - or when/how it will be fixed.  Here goes.

I have a two-hard-drive dual-boot system.  WinXP Pro SP3 is on my secondary drive, Ubuntu 10.04 is on my primary drive.  I've noticed this weirdness before.  But this time, I did a 3 test-boots.

First, keep in mind that I'm in the Pacific Time zone in the USA.

BOOT #1 - Booted into WinXP.  Time on the system clock is 10:42 PM, August 4th.

BOOT #2 - Restarted computer and booted into Ubuntu.  When the first screen came up, the system timeclock was set to 3:42 PM, August 4th - 7 hours earlier than the REAL time.  However, when I entered my ring password (and after a few seconds), the system timeclock on the screen "jumped" back to the real time - 10:42 PM, August 4th.

BOOT #3 - Restarted computer and booted into WinXP.  Time on the system clock said 5:45 AM, August 5th - 7 hours ahead of the REAL time.

I also did test "re-boots" in WinXP.  As long as I didn't boot Ubuntu, my time remained correct.  But once I booted into Ubuntu again, the same scenario mentioned above repeated itself.

And, I also did test "re-boots" into Ubuntu.  As long as I didn't boot WinXP, my time remained correct.

Any idea what the heck is going on here?  Is there a "fix" for this?

---

### Post by J.Alec.West on 2010-08-05
Just a brief PS to my last post.

My last post was made in my WinXP environment.  I'm now in my Ubuntu environment and did one more test.  This time, when I was prompted to enter my password, I just sat and waited for a full minute.  The timeclock dropped 7 hours back and sat there as well.  It wasn't until I entered my password and actually "logged on" to my desktop that the timeclock reverted to the correct time.

So, this is clearly a Ubuntu issue ... not a WinXP issue.

---

### Post by J.Alec.West on 2010-08-05
And, a brief PS to my last PS (grin).

I decided on one more experiment.  I opened up my system time/date window in Ubuntu and modified the timeclock ... setting it back 7 hours from the correct time.  Then, I clicked on the button to accept the change - and my mouse pointer "froze" on the screen.  However, the system timeclock in the upper right corner of my screen was modified and counting.  So, I rebooted my computer, this time into WinXP.  The timeclock read the correct time.

Yup, seems to be a Ubuntu issue ... not to mention the mouse-pointer freeze when I attempted to change the time.

BTW, I don't have to go through the trouble of resetting my timeclock manually in the WinXP environment.  I have a utility that pings the atomic clock in Ft. Collins, Colorado - setting my system clock to the proper time automatically.

---

### Post by J.Alec.West on 2010-08-05
Anybody got an answer?  This post was "buried" during a forum glitch.

---

### Post by louieb on 2010-08-05
One is setting the system clock to local time - the other probably Ubuntu is setting the system clock to UTC (universal time)

check and if needed edit **/etc/default/rcS** and change the line UTC=yes to UTC=no

---

### Post by QIII on 2010-08-05
In /etc/defaults/rcS change "UTC=yes" to "UTC=no"

(Dang... Got distracted and was beaten to the draw!)

---

### Post by marshmallow1304 on 2010-08-05
This is happening because the two OSs are handling the system clock in different ways.

Ubuntu expects the system clock to be in [UTC]("http://en.wikipedia.org/wiki/Coordinated_Universal_Time").  Then to display the time, Ubuntu adds or subtracts from the system clock according to the user-specified time zone.

Windows expects the system clock to be in local time.

You're on [Pacific Daylight Time]("http://www.timeanddate.com/library/abbreviations/timezones/na/pdt.html") now, which is UTC - 7.  That accounts for the seven hour shifts.


To fix this, you can easily set Ubuntu to read the system clock as localtime to avoid conflicts with Windows:

Press Alt+F2 and type in
```
gksudo gedit /etc/default/rcS
```
Edit the file, changing
UTC=yes
to
UTC=no
Save and exit the editor.





(Got really distracted and was beaten by 10+ minutes.)

---

### Post by J.Alec.West on 2010-08-05
Thanks to all.  The fix is in and works great.

This would make an interesting thing for future developers.  Using Windows alone, no problem.  Using Ubuntu alone, no problem.  Dual-boot, problem.  Perhaps in a future incarnation, developers could put a question in as part of the setup process - asking if users will be using a "dual boot with Windows" system.  If they say "yes," then the setup process could automatically modify the rcS file to say "no" for UTC.

Or (blush) is this already a part of the setup process that I just missed?

One more question. Is there a Ubuntu utility that, like my Windows utility, will ping the atomic clock for time accuracy sake?

---

### Post by jtarin on 2010-08-05
[Time Synchronization]("http://www.linux.org/docs/ldp/howto/Kerberos-Infrastructure-HOWTO/time-sync.html") the standard Unix way.

---

### Post by tommynz1975 on 2010-08-05
I may have this wrong, having one of those years


If you go in the Menu
System--> Administration--> Date and Time,

Click on unlock and enter your password.

Now all you should have to do is change the drop down box for configuration to read  
"Keep synchronized with Internet servers" or set to "manual" if you don't want that to happen

---

### Post by jtarin on 2010-08-05
[The Ubuntu way.]("https://help.ubuntu.com/9.04/serverguide/C/NTP.html")

---

### Post by tgalati4 on 2010-08-06
If you triple boot (with other linux distros), I find it better to set Windows to UTC.  There is a setting somewhere (probably in Control Panel, Date & Time).  This way Windows stores UTC in the hardware clock and behaves like Linux.  So any future installs will work as you would expect.

---

### Post by yunone on 2010-08-06
> **tommynz1975 said:**
> I may have this wrong, having one of those years


If you go in the Menu
System--> Administration--> Date and Time,

Click on unlock and enter your password.

Now all you should have to do is change the drop down box for configuration to read  
"Keep synchronized with Internet servers" or set to "manual" if you don't want that to happen


thats what i do


Ubuntu can be weird sometimes and it jumps around, but once you sync with the internet all should be fine...., i really dont blame Windows for being different..it just doesnt always work right :)

---

### Post by marshmallow1304 on 2010-08-08
> **tgalati4 said:**
> If you triple boot (with other linux distros), I find it better to set Windows to UTC.  There is a setting somewhere (probably in Control Panel, Date & Time).  This way Windows stores UTC in the hardware clock and behaves like Linux.  So any future installs will work as you would expect.

It's great if there is a setting like that.  I thought the only way to make Windows use UTC was to edit the registry.

---

### Post by DrMelon on 2010-08-08
On my Windows 7 install, I enabled UTC - perhaps older version of Windows do not have this feature?

---

### Post by Emmtor on 2010-08-08
Just skimmed through the thread. The time problem really intrigued me..Great thread!

---

