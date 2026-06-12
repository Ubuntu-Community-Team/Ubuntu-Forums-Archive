---
title: "Sleep Then Hibernate"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by Jr. on 2010-05-05
Hey guys, quick question. Is there a way to set the computer to sleep after 20 mins then hibernate after 1hr? I use my netbook mostly for school and I don't want it shutting down between classes but I also don't want it to drain battery life through the night. Any help is appreciated. Thank you.

---

### Post by Troublegum on 2010-05-05
> **Jr. said:**
> Is there a way to set the computer to sleep after 20 mins then hibernate after 1hr?

The former is possible, but I don't know about the latter.
If you go to "System" -> "Preferences" -> "Power Management" you see the setting "Put computer to sleep when inactive for XY". You can select 10, 30, 60 or 120 minutes.

---

### Post by Jr. on 2010-05-06
Yes, that is how I have it set now. I'm looking for a way to sleep after some time and hibernate some period of time later.

---

### Post by transformania on 2011-06-13
bump

I'm also very interested in this, after I saw this feature in Vista.

What I'd really like is to take it a step further and have a laptop not got to suspend/sleep at all when you close the lid for 5 minutes, then suspend/sleep and *then* after an hour, hibernate.

The reason I'd want the 5 minutes of no action is those times when you want to go from one room to another with your laptop, or get on the elevator or walk to another nearby place, and not have to carry it around with the lid half open, balanced horizonally, like a pizza.

Where/what are the scripts that control what happens when you close the lid?  I've seen them before but modifying them didn't seem to work; something else is going on in the background.

---

### Post by tgalati4 on 2011-06-13
The problem is when your computer is sleeping, the processor is effectively stopped and RAM contents are maintained.  So there is no way to process a timer to send to hibernate mode.

The problem with hibernate mode in linux is that (in my experience) it takes as long to load the hibernate RAM snapshot from disk as it does to cold boot.  So on my IBM thinkpad t43p, I just use sleep mode all the time.  I don't know how many hours I get on sleep mode, but it's a lot, perhaps 20 or so.  I can usually go a couple of days before having to plug back in when in sleep mode.

So, for me, hibernate mode is slow and only useful if you are taking a plane trip and you need to keep your work session intact over several hours of inactivity.  If you are moving from class to class and only have one or two apps open, then sleep mode should be sufficient and you should be able to get through the day on a single charge.  If not, then you need a second (backup) battery or an extended battery.

You will find the sleep/resume scripts in /etc/acpi.  You have to follow the logic of the scripts carefully because they jump around quite a bit.  I also trimmed my scripts way down, taking out all stuff that is not needed for my machine.  That speeds up the sleep and resume response quite a bit.  The sleep/resume framework under linux is buggy, complicated, and mostly works.  It requires some work on your part to optimize it for your laptop.  Once that is done, then it works consistently and relatively quickly.  Not as nice as Mac, but usable and repeatable.

---

