---
title: "display problems"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by whvw on 2010-04-19
I have a few questions...I've been using Linux for a few years and am generally satisfied, that is I would never want to go back to Windoze. There are a few little quirks I would like to fix but cannot find how.
1. Date display: I have gotten the system date to display properly, but the desktop date in the panel INSISTS on displaying month-day-year (backwards to me) rather than day-month-year (the way I want it). How does one fix this?
2.Text below icons: No matter what I've tried, this text displays as white with a black drop shadow. I would like to choose my own colour, and that of the drop shadow, or eliminate the drop shadow altogether.
3. Icons: Some programmes display some form of generic icon instead of the proper one. how can I fix this?
4. How can I get user programmes to also be available in root?

Any help would be greatly appreciated.

---

### Post by Felix-the-Cat on 2010-04-20
Are you using Ubuntu 9.01 with GNOME?
It also would be handy to have some screen shots for question #2

Question #1:

That sounds like your locale setting is not en-US and therefore it doesn't display as such. I used the es locale for a while and it displayed as such.

Question #2 & #3:

That sounds like a theme issue. What theme are you using? It is standard with Ubuntu or third-party?

Question #4:

Just for the record (I know you know this but others may not) you shouldn't run anything as super user unless you **absolutely** have to.

[LIST=1]
[*]Press Alt+F2
[*]Type gksu *program-name-goes-here*
[/LIST]

OR

You can open a terminal (Applications>Terminal) and type "sudo *program-name-goes-here*"

OR

You can create a desktop launcher by right clicking on the desktop and then clicking "create launcher". On the line that says command type gksu *program-name-goes-here*

---

### Post by whvw on 2010-04-20
Dear Felix The Cat:

1. I'm using Ubuntu 9.10 w/gnome
2. How do I set the system to "en-us"
3. The desktop theme has been created from standard Ubuntu templates. In Winderz, for example, you could customise just about every parameter of your desktop display. Screen shot attachment enclosed. (I think)
4. I know I shouldn't use root too often, but Linux is a bit too protective, (like always defaulting to not showing hidden files, for example, so I have to change it each time, and rigamaroles when I want to overwrite files, and, worst of all asking for a password for the "default keyring" (whatever the $#@& that is),etc).

Thanks, whvw

---

### Post by jaco223 on 2010-04-20
> **whvw said:**
> Dear Felix The Cat:

1. I'm using Ubuntu 9.10 w/gnome
2. How do I set the system to "en-us"
3. The desktop theme has been created from standard Ubuntu templates. In Winderz, for example, you could customise just about every parameter of your desktop display. Screen shot attachment enclosed. (I think)
4. I know I shouldn't use root too often, but Linux is a bit too protective, (like always defaulting to not showing hidden files, for example, so I have to change it each time, and rigamaroles when I want to overwrite files, and, worst of all asking for a password for the "default keyring" (whatever the $#@& that is),etc).

Thanks, whvw

Go to system>Administration>Language Support

There is an option there to change the date/time format

If  that doesn't work have a look at this link. You can adjust the time/and date with the command  line.

[http://ubuntuforums.org/showthread.php?t=448935](http://ubuntuforums.org/showthread.php?t=448935)

Hope this helps.

Jaco

---

### Post by pj_kare on 2010-04-21
> **whvw said:**
> 
1. Date display: I have gotten the system date to display properly, but the desktop date in the panel INSISTS on displaying month-day-year (backwards to me) rather than day-month-year (the way I want it). How does one fix this?
My panel date stays as (Month/Day/Year) even though my system is set as en-AU. We use Day/Month/Year. 
Language/Location is one of the first things you are asked during install.

To change the date format:
Open configuration editor. ([COLOR=Red]gconf-editor[/COLOR] in terminal). Go to /apps/panel/applets/clock_screen0/prefs

For format (9th entry down current value is 12) change 12 to the word "[COLOR=Red]custom[/COLOR]". (without quotes).
Either double-click NAME or highlight and single click VALUE to change.

___________________________________________________________________________

For: Day Date - Month - Year Time AM/PM (e.g. Wed 21-Apr-10 04:30 PM)

change "custom_format" (3rd entry down) to: %a %d-%b-%y %I:%M %p (copy and paste in).
Either double-click NAME or highlight and single click VALUE to change.
___________________________________________________________________________

For: Day Date-Month-Year Hour Min AM/PM (e.g. Wed 21-04-10 04:30 PM)

change "custom_format" to: %a %d-%-m-%y %I:%M %p (copy and paste in)
____________________________________________________________________________

*Change I to H for 24hr clock*

*change %b to %B for full month name* or to %m if you just want month number (April = 04 etc) use %-m if you want single digit month, (4 instead of 04 etc.)

*change %y for year "10" to %Y for full year "2010"
____________________________________________________________________________

You can change "-" to "/" (without quotes) or whatever you like (I think) between them.
So it displays as: Wed 21/04/2010 etc. you can leave out any element you don't want.
For example, leave out %a if you don't wan't the day displayed, leave out %y or %Y if you don't want the year displayed. Swap things around to your liking.

Only downsides to this is that if you right click on the date/clock and select copy date, then paste it somewhere it still appears as it did originally.
The clock will also show 2 digits for HOUR, 06:30 PM for 6:30 PM etc.
It's also possible to add colour (color) to the start of the code for different text colour, I can't remember how at the moment.

For further reference try here: [http://php.net/manual/en/function.strftime.php](http://php.net/manual/en/function.strftime.php)

[COLOR=Red]**EDIT:**[/COLOR] Change Colour/color enter the following into custom_format in gconf_editor: ```
<span color="[COLOR=Red]#FF0000[/COLOR]">[COLOR=Blue]%a %d-%-m-%Y %I:%M %p[/COLOR] </span>
``` Change [COLOR=Red]#FF0000[/COLOR] ([COLOR=Red]RED[/COLOR]) to color of your choice, change [COLOR=Blue]%a %d-%-m-%Y %I:%M %p[/COLOR] to format of your choice.[COLOR=Red][COLOR=Black]
You could also use[/COLOR][/COLOR] ```
<span color="[COLOR=Red]#FF0000[/COLOR]">[COLOR=Red]%a %d-%-m-%Y [/COLOR]</span><b>[COLOR=Red]%I:%M %p[/COLOR] </b>
```[COLOR=Red] [COLOR=Black]to show date in normal text and time in **bold black**. Any errors and it will all appear as text in panel.
If you know CSS you'll surely do better than me :-k
[/COLOR] [/COLOR]

---

