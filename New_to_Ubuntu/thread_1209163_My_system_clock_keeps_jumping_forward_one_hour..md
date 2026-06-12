---
title: "My system clock keeps jumping forward one hour."
date: 2009-07-10
forum: New to Ubuntu
---

### Post by anthony62490 on 2009-07-10
It started a few days ago when I added a European timer to my system clock. Now it's 11:30, but my clock says 12:30. I've reset the clock and it works fine for the rest of the night. When I shut down the computer, I even see a notice on the splash screen that says, "saving system time...". But when I turn it on again, it jumps ahead one hour. It's not a huge problem or anything, but it IS a bit annoying. Got any ideas?

Note: When I tried to add a European clock to my computer, I was trying to add it to the system tray. That way I could have more than one clock. It didn't work out. I ended up deleting and adding the clock several times. I don't know if that helps at all, but it may be relevant.

---

### Post by philcamlin on 2009-07-10
set it in the bios?

---

### Post by mattbutsko on 2009-07-10
frankly just today my clock starting setting itself an hour behind. 

didn't do anything to it and the system time is correct. weirdest thing.

---

### Post by fballem on 2009-07-10
> **anthony62490 said:**
> It started a few days ago when I added a European timer to my system clock. Now it's 11:30, but my clock says 12:30. I've reset the clock and it works fine for the rest of the night. When I shut down the computer, I even see a notice on the splash screen that says, "saving system time...". But when I turn it on again, it jumps ahead one hour. It's not a huge problem or anything, but it IS a bit annoying. Got any ideas?

Note: When I tried to add a European clock to my computer, I was trying to add it to the system tray. That way I could have more than one clock. It didn't work out. I ended up deleting and adding the clock several times. I don't know if that helps at all, but it may be relevant.

I'm going on hazy memory, and very recent experience, but Linux assumes that the bios clock is stored as UTC time, and then applies the appropriate factor to determine the correct time in your location.

I noticed that on your screenshot, the time in Arad was being reported as EEST+7, which suggests that you may be located in the Eastern Time Zone of North America - same as me.

If you restart your computer and enter bios setup, please check to see what time is set there. It should be the UTC time. Toronto, which is in the Eastern Time Zone of North America, is currently UTC-4, so if the current local time is 1:37 AM, then the time according to my bios is 5:34 AM. If the bios clock isn't correct, then change it so that it is the correct UTC time.

Arad, which appears to use Daylight Savings Time, is currently UTC+3.

By the way, UTC time is also referred to as Greenwich Mean Time (GMT), which is why the display shows GMT-4 for Toronto and GMT+3 for Arad when you are first setting it up.

Hope this helps.

---

### Post by superprash2003 on 2009-07-10
how old is your pc? maybe time to change the CMOS battery?

---

### Post by anthony62490 on 2009-07-11
Okay, I looked at the BIOS clock and it WAS one hour ahead. That's weird, because I haven't touched the BIOS in months. Also, even though I changed the BIOS clock, the Ubuntu system clock still says that it is one hour fast. I've reset the computer twice and checked the BIOS again, but no dice.

As a last ditch effort if no one has any more ideas, I'm going to scavenge a fresh(er) battery from another computer and see if that doesn't help.

---

### Post by earthpigg on 2009-07-11
first, ensure you are set to the right time zone:

```
sudo dpkg-reconfigure tzdata
```

next, have your computer autosync with a time server of your choice:

system -> administration -> time and date -> unlock -> configuration -> keep synced with internet servers -> let it install NTS....

...restart time and date -> pick some time servers that look trustworthy to you.

i picked germany because i trust the germans to build a good clock.

---

### Post by anthony62490 on 2009-07-20
Thanks pig, that worked perfectly.

---

### Post by Popeyedasailorman on 2010-05-24
I know this thread hasn't had much interest in about a year now but i am something of a newbie to Linux and Ubuntu. I've had a quick read through here but i'm still in the dark as to how to resolve this timing issue.

I have a laptop which has Windows installed on it. I also have Ubuntu 9.1 which is installed on a USB HDD. Every time i switch from one to the other there is a time difference of one hour. I have checked that my region is correct (Europe, London) and that DST is on and i use a UK time server as that is where i am based. I've also tried this on other computers, including the missus's brand new laptop so i know it's not the CMOS battery. Whilst it's not the end of the world as Ubuntu quickly 'Corrects' the time shortly after logging in it is a bit of a pain in the bum when it comes to Windows as i have to do it manually there. The BIOS clock is correct and I've noticed that during the non-DST months it's not a problem

Am i missing something?

Any help is much appreciated, Thanks

---

### Post by redbook4574 on 2010-05-24
> **Popeyedasailorman said:**
> I know this thread hasn't had much interest in about a year now but i am something of a newbie to Linux and Ubuntu. I've had a quick read through here but i'm still in the dark as to how to resolve this timing issue.

I have a laptop which has Windows installed on it. I also have Ubuntu 9.1 which is installed on a USB HDD. Every time i switch from one to the other there is a time difference of one hour. I have checked that my region is correct (Europe, London) and that DST is on and i use a UK time server as that is where i am based. I've also tried this on other computers, including the missus's brand new laptop so i know it's not the CMOS battery. Whilst it's not the end of the world as Ubuntu quickly 'Corrects' the time shortly after logging in it is a bit of a pain in the bum when it comes to Windows as i have to do it manually there. The BIOS clock is correct and I've noticed that during the non-DST months it's not a problem




Am i missing something?

Any help is much appreciated, Thanks

Enable NTP and select a uk server, I use cambridge.

---

### Post by srs5694 on 2010-05-24
> **Popeyedasailorman said:**
> I have a laptop which has Windows installed on it. I also have Ubuntu 9.1 which is installed on a USB HDD. Every time i switch from one to the other there is a time difference of one hour.

Your problem is probably due to the fact that Windows assumes the system's hardware clock, which keeps the time when the system is shut down, is set to local time, whereas Linux can use either local time or UTC (aka GMT). According to [this site,](http://wwp.greenwichmeantime.com/time-zone/europe/uk/england/london/time/) London time is currently one hour ahead of UTC/GMT, so my hunch is that your Linux setup is configured to use UTC/GMT for its hardware clock, thus creating the flip-flops between the two.

My own preference is to [set Windows to use UTC.](http://weblogs.asp.net/dfindley/archive/2006/06/20/Set-hardware-clock-to-UTC-on-Windows-_2800_or-how-to-make-the-clock-work-on-a-Mac-Book-Pro_2900_.aspx) This makes problems around Daylight Saving Time changes less likely, since the hardware clock doesn't need to be reset. (If the hardware clock must change, as it must if it's set to local time, then the question becomes: Which OS should change it? It could easily get reset twice.) After making this change, you'll have to be sure to reset the hardware clock to UTC. This might be done automatically when you shut down, or you might have to do it manually via your BIOS setup utility.

The alternative is to set Linux to interpret the hardware clock as being set to local time. There's probably a GUI control somewhere in Ubuntu to do this, but I'm not sure offhand where it is. (I don't currently have an Ubuntu desktop system booted, so it's not convenient for me to look for it.)

---

### Post by srs5694 on 2010-05-24
Oh, incidentally, it doesn't really matter in what time zone your NTP server resides, although the overall network distance to the time server does matter. This is because NTP uses UTC for time references, so a time server in London gives the same time as do servers in New York, San Francisco, Beijing, Moscow, or Cairo, assuming they're all configured correctly. If you're in London, though, the London server will probably respond more quickly and with less variability in the time to transfer packets than the others I've mentioned, and this will improve the accuracy of the time when you use a nearby server. Depending on the quirks of the network topology, though, it's conceivable that a server in Paris would respond more quickly than one two blocks away from you in London.

---

### Post by Popeyedasailorman on 2010-05-30
OK thanks for your reply, the one thing that i have noticed is that when going into BIOS after using Ubuntu it is always one hour behind. If i correct the time and then log into Ubuntu the time shows as one hour ahead, after a minute or two it then synchronises with a time server (which i have set as time.nist.gov) and it will correct the time. I then restart the computer and go into BIOS and the time is once again one hour behind, so is Ubuntu reading the BIOS clock wrong or is there a setting I can use to change so that Ubuntu doesn't add an hour on?

---

