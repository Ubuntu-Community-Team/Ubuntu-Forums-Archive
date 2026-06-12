---
title: "How to set clock to 24 hour display mode?"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by jespdj on 2010-10-11
I've just installed Ubuntu 10.10 Netbook Edition.

The clock in the right-hand corner of the screen is in 12-hour mode, e.g. it shows "10:41 PM". I'd like to change it to 24-hour mode (so that it shows "22:41"), but I don't see any option to do this.

Right-clicking the clock and going to "Time & Date Settings": there's no option to set it to 24-hour mode.

How do I set the clock display to 24-hour mode?

Also, the weather thingy that was there in Ubuntu 10.04 doesn't appear. How can I make it appear?

---

### Post by ubunterooster on 2010-10-11
right-click>preferences>general>clock format

---

### Post by jespdj on 2010-10-11
Right-click where? On the clock? There is no "Preferences" option when you do that. Only a "Time & Date Settings" option, but it does not have a "General" tabsheet (no tabsheets at all!) and no way to set the clock to 24-hour format.

Note, this is about the Netbook Edition.

---

### Post by jespdj on 2010-10-11
Entered a bug report: [https://bugs.launchpad.net/ubuntu/+bug/658738](https://bugs.launchpad.net/ubuntu/+bug/658738)

---

### Post by yanaek on 2010-10-19
same here, thanks for submitting it

---

### Post by TobyLL on 2010-10-27
Not very user friendly workaround:

First install dconf-tools via the terminal:
sudo apt-get install dconf-tools

Then run dconf-editor. In the configuration window that opens navigate to "/apps/indicators/datetime" and change time-format to "24-hour".

Thanks to: [http://www.omgubuntu.co.uk/2010/09/enable-date-day-seconds-on-indicator-datetime/](http://www.omgubuntu.co.uk/2010/09/enable-date-day-seconds-on-indicator-datetime/)

---

### Post by TobyLL on 2010-10-27
Slightly more involved solution:

```
sudo apt-get install libglib2.0-bin
gsettings set org.ayatana.indicator.datetime time-format "'custom'"
gsettings set org.ayatana.indicator.datetime custom-time-format "'%a %d %b %T'"
```
(Note single quotes inside double quotes above).

See [http://no2.php.net/strftime](http://no2.php.net/strftime) for format strings.

---

### Post by g0kb3rk on 2010-11-06
Why are there these kind of unnecessary problems in 10.10? 10.04 was much better.

---

### Post by RAdams on 2011-02-05
The bug was marked as a duplicate of a bug regarding setting the clock and other standards when in another region. Please, everyone with this issue mark the bug linked in this thread as affecting you, and add support via commenting that this is **not** a duplicate!

---

### Post by oldgeezer1 on 2011-02-15
> **jespdj said:**
> I've just installed Ubuntu 10.10 Netbook Edition.

The clock in the right-hand corner of the screen is in 12-hour mode, e.g. it shows "10:41 PM". I'd like to change it to 24-hour mode (so that it shows "22:41"), but I don't see any option to do this.

<snip>

I don't know if the netbook version of 10.10 is different that the desktop edition but here is how I got my clock to display 24 hour format.

1.  Left click on the calendar/time display
2.  To the right of the "Locations" link, left click on edit
3.  Under the "General" tab you can change the Clock Format.

Finding the "General" tab was a show stopper for me until I found out where it was located.

---

### Post by Paqman on 2011-02-15
> **g0kb3rk said:**
> Why are there these kind of unnecessary problems in 10.10? 10.04 was much better.

Because Unity isn't finished yet. If you can't live without some of the features that are missing, you can still run the normal Gnome desktop.

---

### Post by per engberg on 2011-04-26
Thanks - perfect

---

### Post by per engberg on 2011-04-26
Re.: Slightly more involved solution:

Thanks - perfect

---

