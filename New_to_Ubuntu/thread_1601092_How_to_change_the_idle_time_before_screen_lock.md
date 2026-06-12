---
title: "How to change the idle time before screen lock?"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by jfry on 2010-10-19
I've tried System > Screensaver prefs and see
"Regard the computer as idle after " 5 minutes.

I'd like to change this to, say, 8 minutes...but it's greyed out for me.

Do you know how to make this editable? 
Or is there a way to do this from the terminal?

Thanks,
Jeff

---

### Post by robsoles on 2010-10-19
Welcome to UF.

That makes it sound like you are not the primary user of the machine, that is to say that you don't have admin privileges.

Please try```
sudo nano /etc/xdg/autostart/gnome-screensaver.desktop
```
System will prompt you for a password, enter your regular login password - if it is rejected then you don't have admin privileges for this system and you need to talk to the person that does.

If it opens a text editor with content then look for ```
X-GNOME-Autostart-Delay=5
``` and change the 5 to an 8, press [CTRL]+[X] and type [Y], [Enter] - log out and log back into your desktop and open the 'screensaver' item off 'System'->'Preferences' again to check that it is changed to 8.

How's that?

---

### Post by cgroza on 2010-10-19
You need root right just to change a screen saver delay time?

---

### Post by robsoles on 2010-10-19
> **cgroza said:**
> You need root right just to change a screen saver delay time?

Entirely not sure but inclined to try something for OP - the file (I think) influenced in /etc/xdg/autostart belongs to root so it seems logical enough to think that a 'guest' (or at least non-wheel/admin user) won't be allowed to change it.

---

### Post by jfry on 2010-10-20
Thanks so much, that worked!

I appreciate the speedy, helpful reply.

---

### Post by robsoles on 2010-10-20
Very welcome jfry, please consider using 'thread tools' (in red, above to right hand side) to mark your thread as solved.

---

### Post by cariboo on 2010-10-20
Have you gone to System->Preferences->Screensaver, and moved the slider to change the idle time? See screenshot

---

### Post by robsoles on 2010-10-21
> **cariboo907 said:**
> Have you gone to System->Preferences->Screensaver, and moved the slider to change the idle time? See screenshot

OP seemed competent enough to me to get into the right place to set their inactivity timeout and they said it was greyed out for them, like they were not a primary/admin user of their own machine (circumstance of greyed out options) so I pursued it and they've acknowledged that my crap worked out for them.

I'd love to know for sure that it's grayed out in their dialog box that opens when we follow your instructions and look at your attachment because it doesn't entirely make sense that it was grayed out for them but worked for sudo <themself>, obviously this is a bug, albeit a much less obvious one.

Sorry, I been drinking.

I still hope jfry marks their post as solved, been a lot of 'interesting problems' with 10.10, what I always wait to see before taking any 'major upgrade' indeed :)

---

### Post by AngusH on 2010-10-21
This is quite an interesting result. On my machine I don't need sudo authentication to change that setting (tried both after sudo -k and on a no privs account) and it worked fine. It is also a preference, not an administrative setting so it should be applied on a per account basis and therefore not require root. I assume your solution changed the default, since files specific to a single user should never be in a system folder.
Very puzzling...
Angus

---

### Post by robsoles on 2010-10-21
> **AngusH said:**
> This is quite an interesting result. On my machine I don't need sudo authentication to change that setting (tried both after sudo -k and on a no privs account) and it worked fine. It is also a preference, not an administrative setting so it should be applied on a per account basis and therefore not require root. I assume your solution changed the default, since files specific to a single user should never be in a system folder.
Very puzzling...
Angus
Hoping you are subscribed, would you mind telling us your current version of Ubuntu and how you got there? :)

[COLOR=Red]Could you answer the same question please, jfry?[/COLOR]

---

### Post by AngusH on 2010-10-21
Not sure what you mean. If you mean how did I obtain that result, I didn't do anything, just the tests I listed above. As I said, default behavior should be that it doesn't require any kind of privileged access.
Angus

EDIT I'm running 10.10 but like I say it shouldn't make a difference...

---

### Post by robsoles on 2010-10-21
> **AngusH said:**
> ...

EDIT I'm running 10.10 but like I say it shouldn't make a difference...

I'm running 10.04 which 'live upgraded' from 9.10, I have only used a primary user on this PC but I have a laptop. The laptop is also a 'live upgrade' from 9.10 to 10.04 and it has 'lesser users'. My six year old is a 'lesser user' on the laptop and I just logged in as 'her' and was allowed to manipulate the control in question.

I'd love to know how jfry got themselves into this situation so I could preach my 'dependants' not to do that (sorry jfry!).

---

### Post by PauleyX88 on 2012-06-29
> **robsoles said:**
> Welcome to UF.
 
That makes it sound like you are not the primary user of the machine, that is to say that you don't have admin privileges.
 
Please try```
sudo nano /etc/xdg/autostart/gnome-screensaver.desktop
```
System will prompt you for a password, enter your regular login password - if it is rejected then you don't have admin privileges for this system and you need to talk to the person that does.
 
If it opens a text editor with content then look for ```
X-GNOME-Autostart-Delay=5
``` and change the 5 to an 8, press [CTRL]+[X] and type [Y], [Enter] - log out and log back into your desktop and open the 'screensaver' item off 'System'->'Preferences' again to check that it is changed to 8.
 
How's that? Hello,,,New to Ubuntu,,,Thank you, your post worked great! Now I can look at the screen for a while! :)

---

### Post by ubudog on 2012-06-29
Old thread closed.

---

