---
title: "[SOLVED] Firefox Problems"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by nebu on 2009-01-01
The firefox window no longer has a title bar.....

The thing was working all fine till yesterday.... today the thing seems to have gone wrong....

i use compiz with the emerald window decorator....

i think there is some sort of problem with compiz..... occasionally i am getting this kind of flicker in the firefox menu.... and the colours are all mixed up and very ugly.....

the problem persists if i use metacity as the window decorator instead of emerald or even if i use metacity instead of compiz

this problem occurs only in frefox and in no other application...

how do i fix this??

---

### Post by 5BallJuggler on 2009-01-01
What happens when you press F11?

---

### Post by nebu on 2009-01-01
it goes into full screen mode....

it looks just like it is supposed to....

but once i press f11 again....

title bar is not there....

---

### Post by fooman on 2009-01-01
this fix does not work for you?....

press f11 to go fullscreen and f11 again to get to a normal size screen.

next click the unmaximize button.

close firefox.

reopen firefox.

maximize firefox.

that should fix it....if does not fix it, please post a screen shot.

---

### Post by icyest on 2009-01-01
You know this same thing happened to me. I simply disabled the bells and whistles/settings and used the default theme. I then restarted, and re-applied the themes again and it worked; mysteriously. I decided to omit wobbly windows and shadows however, which leads me to suspect that compiz screws with with firefox on occasion.

The problem with firefox is that it conforms with metacity for a more consistent operating theme. This led to me having to deal with a rainbow firefox for days.

---

### Post by 5BallJuggler on 2009-01-01
Do you have "window decoration" turned On in Compiz, try turning it off

I'm not that familiar with Emerald, although it is on my system for some reason, but i find it odd that it just changed on it's own, have you done an update of the system?

You can also try looking at the the Titlebar settings in the Emerald program, i've just looked at mine, click on system-preferences-emerald theme manager.

when it opens go to the 2nd tab "emerald settings" is the bottom option (Compiz decoration blur type) set to "All decoration"

---

### Post by mynydd on 2009-01-01
Do you use a theme in Firefox? If so try changing it.
If not I would reinstall Firefox, because it is a local problem to that program.

---

### Post by ubuntu-freak on 2009-01-01
> **icyest said:**
> ...which leads me to suspect that compiz screws with with firefox on occasion.

 
It's not Compiz, it's the fact that Firefox is a bit funny when it comes to themes. I couldn't use the Crux theme with Firefox a few months ago in Debian Lenny, as Firefox would just completely freeze.
 
I recommend the OP backs-up his/her bookmarks, then deletes the Firefox folder in "/home/.mozilla", disable Compiz, then select the default theme in System > Preferences > Appearance, before launching Firefox again.

---

### Post by nebu on 2009-01-01
@fooman

it worked.... thanks.....

---

