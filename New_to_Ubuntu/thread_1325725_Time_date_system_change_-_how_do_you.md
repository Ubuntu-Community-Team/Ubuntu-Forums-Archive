---
title: "Time date system change - how do you"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by urdrwho on 2009-11-13
Ok, is it ever going to end?  My constant amazment at how hard things are to do in this "new" OS compared to the old MS world.

Apparently the new OS has great aversions to GUI type of work and has a love affair with command lines.  Cool for geek-ism bad, very bad for the general public.  

All I want is to change my date and time arrangment so that it is a systme wide change.

I want my date to be:
month/day/year

I want my time to be on a 12 hour clock
hour first and minutes.

Not so hard in Windows world but searching the Net brings up many, many different pages and methods to do it.  All have to do with writing script.

Errrrrrrrrrrr.....going for a glass of wine.

---

### Post by HarrisonNapper on 2009-11-13
You should really read this: [Linux is NOT Windows]("http://linux.oneandoneis2.org/LNW.htm")

As I recall, this was a matter of right-clicking the time and going to preferences. I had my time set to military time for a long time, but I've run awn for awhile. I'll try this when I get home in a bit and edit with the results.

---

### Post by bennachie on 2009-11-13
Try right-clicking on the date/time display, then select "preferences".

---

### Post by durand on 2009-11-13
I don't know how Windows does it but I cannot think of a better way to change the time than just right clicking on the time and changing it. Maybe if it could read your mind...hmm...

---

### Post by oldsoundguy on 2009-11-13
Right click on the clock display.
Select preferences.
select12 hour or 24 hour format.
I also selected show seconds.
Since I use the weather applet in my lower panel, I unchecked the show weather and show temp.

Then went to system>administration>time and date and set it up to web synchronize.

My display is day/month/date/hour/minute/seconds am /pm

For Windows I install two programs .. TClockEX and atomachron.  Set them up as I like and in several years have NEVER had to re-set a Windows clock that has become kludged by a Windows update or because Windows really can't keep time.

---

### Post by wojox on 2009-11-13
You can also hack it yourself with gconf-editor

Alt+F2

Enter: gconf-editor

Go to /apps/panel/applets/clock_screen0/prefs/

Click format type: custom

Click custom_format 

Enter value: %b %d %y %H:%M

---

### Post by urdrwho on 2009-11-13
the reason I ask is I use Rainlendar calendar on the desktop.  In ubuntu the time is not showing as I want it.  I went to their website and found this:

"The date picker control is native operating system control and the date format cannot be changed. It will automatically use the format which is defined by the system locale.

So if the OS system must be setup correctly so the time will show correctly in Rainlendar.

---

### Post by urdrwho on 2009-11-13
I also need to get it to change to a 12 hour clock and not a 24 hour clock.


> **wojox said:**
> You can also hack it yourself with gconf-editor

Alt+F2

Enter: gconf-editor

Go to /apps/panel/applets/clock_screen0/prefs/

Click format type: custom

Click custom_format 

Enter value: %b %d %y %H:%M

---

### Post by wojox on 2009-11-13
```
%b %d %y %l:%M %p
```

Hows that?

---

### Post by oldsoundguy on 2009-11-13
> **urdrwho said:**
> I also need to get it to change to a 12 hour clock and not a 24 hour clock.

Once again.... RIGHT CLICK on the time and select preferences to set for 12 hour NO MATTER desktop or laptop!

---

### Post by HarrisonNapper on 2009-11-16
> **oldsoundguy said:**
> Once again.... RIGHT CLICK on the time and select preferences to set for 12 hour NO MATTER desktop or laptop!

Does this also work with Rainlender, though?

urdrwho: your problem is with Rainlender, not Ubuntu. There are probably lots of Windows applications that have a clock which are difficult to change (read: all of them). If this is the case, I am dittoing the person who said to use gconf-editor if you really don't want to use a terminal.

And hopefully you read the Linux is NOT Windows article; it has a lot of helpful information about how to approach asking questions with Linux. As it mentions in the article, you are not our customer and we are all volunteering our time to the community. I understand your frustration especially the frustration with Ubuntu's learning curve, but this is simply not a traditional customer/customer service relationship. If you ask questions in such an abrasive fashion as your original post, you will find a number of people tell you to ask for a refund and pay no more mind to your question.

---

