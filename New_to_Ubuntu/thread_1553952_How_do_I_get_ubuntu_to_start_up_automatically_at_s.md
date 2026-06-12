---
title: "How do I get ubuntu to start up automatically at specified times and dates?"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by Old Jimma on 2010-08-15
Hi Ubuntu:

I'm working on making my computer more "green" by shutting down my computer automatically using [COLOR="Red"]**crontab**[/COLOR] and [COLOR="red"]**shutdown**[/COLOR] after it has completed scripts that I've written.

No sense in burning electricity needlessly. 

However, this poses a problem for me. **Afer getting crontab and shutdown to shut my computer down automatically, I need it to wake up and start working again... automatically on spcified days and times...  on other scripts that I've written.**

[COLOR="Red"]**How do I get ubuntu to start up automatically at specified times and dates?**[/COLOR]

THanks!
Phil Smith
Duluth, GA

---

### Post by SpockVulcan on 2010-08-15
This can be done in the BIOS.

---

### Post by M93 on 2010-08-15
could u please tell me how to do it in the BIOS:)

---

### Post by proxyofsocks on 2010-08-15
If you have a dd-wrt capable router, the firmware has a WOL daemon.

---

### Post by Aearenda on 2010-08-15
See [this link]("http://www.mythtv.org/wiki/ACPI_Wakeup") - but in my experience, it's very BIOS dependent - some computers do it perfectly, others less so.

---

### Post by diablo75 on 2010-08-16
I only know of two ways to do this, and doing it through the BIOS is one that was mentioned.  In my experience, you are limited to a specific date and time, but not multiple dates and times.

The other method would involve some sort of Wake-On-Lan feature, which is also dependent upon your BIOS having the capability to listen for an incoming "Wake UP!" signal on the network.  And it's something I've never messed with so couldn't tell you more.  From the looks of it, someone else has already pointed out an open-source firmware replacement for your router which could be configured to administer these wake up signals, but you should investigate your BIOS first to see if it would even work.

---

### Post by wojox on 2010-08-16
If you shutdown you've turned it off.

If you need it to wake up you've suspended or hibernated.

Which is it. :confused:

---

### Post by diablo75 on 2010-08-16
> **wojox said:**
> If you shutdown you've turned it off.

If you need it to wake up you've suspended or hibernated.

Which is it. :confused:

The OP is trying to automate his computer to turn itself on AND off at specific times in an effort to save electricity.

---

### Post by Old Jimma on 2010-08-16
Hi All:

I was the originator of this discusion.

How about something short of shutdown? Ie, rather than shutting down, how about 'hibernate' or 'suspend?'

I don't know too much about those. Could they reduce power demands but alow crontab to continue working?

Phil Smith
DUluth, GA

---

### Post by Aearenda on 2010-08-16
I use crontab to schedule the shutdown after priming the BIOS to wake the computer at a set time, as described in the [Myth wiki]("http://www.mythtv.org/wiki/ACPI_Wakeup") I linked above. I have crontab set different wake times on different days.

No crontab will work during standby or hibernate. The only choices are to trigger a wake via the network card, or use the timer, both of which are BIOS dependent.

---

### Post by LightningCrash on 2010-08-16
> **proxyofsocks said:**
> If you have a dd-wrt capable router, the firmware has a WOL daemon.

I have done this before and it worked pretty well.

---

### Post by Old Jimma on 2010-08-16
Thanks Aearenda!!!

---

### Post by Old Jimma on 2010-08-19
Hi Aearenda:

Thanks so much for providing the link. It looks exactly like what I'm looking for!

Phil Smith
Duluth, GA

---

### Post by Aearenda on 2010-08-19
Good! I just wish it always worked - on some computers it does, others not.

---

