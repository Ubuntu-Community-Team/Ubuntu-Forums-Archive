---
title: "arrow key desktop navigation"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by MichaelBurns on 2009-12-03
How can I enable the use of arrow keys to select file icons on the desktop?  The arrow keys do nothing, even when a desktop icon is already highlighted.  Ideally, I want the arrow keys to select desktop icons even when they are not yet highlighted.

---

### Post by MichaelBurns on 2009-12-14
bump

---

### Post by Sir Jasper on 2009-12-15
Hi,

If you view your Desktop via Places or Thunar you could use the arrow keys, but someone may know a better way to do exactly what you want.

May I enquire if your cursor device is faulty or if you just prefer not to use it?

My regards

---

### Post by MichaelBurns on 2009-12-15
Thanks for the reply, noble Jasper.

> **Sir Jasper said:**
> May I enquire if your cursor device is faulty or if you just prefer not to use it?Frankly I don't understand why use of the touchpad is so desirable to so many people.  Icons and menu items are discrete objects, and so a continuous cursor position is just a distraction.  If I use the touchpad, I have to also use my eyes (which are not the best).  The keyboard provides a precise repeatability that frees my eyes for other tasks.  I rarely used the touchpad with Windows XP, unless of course I was using paint or Anvil studio or clicking buttons on some annoying webpage that won't let me just press enter.

That reminds me, I also would like to pull down the applications menu without the touchpad.

---

### Post by KIAaze on 2009-12-15
> **MichaelBurns said:**
> That reminds me, I also would like to pull down the applications menu without the touchpad.

Alt+F1
More shortcuts: [http://ubuntufan.wordpress.com/2006/12/29/hot-keysget-your-hot-keys/](http://ubuntufan.wordpress.com/2006/12/29/hot-keysget-your-hot-keys/)
[http://www.cyberciti.biz/faq/using-the-keyboard-to-navigate-the-desktop/](http://www.cyberciti.biz/faq/using-the-keyboard-to-navigate-the-desktop/)

I can't test the desktop icon navigation in Gnome right now, but in KDE 3 it works without any problems. ;)

edit:
[http://library.gnome.org/users/gnome-access-guide/stable/keynav-4.html.en](http://library.gnome.org/users/gnome-access-guide/stable/keynav-4.html.en)
ctrl+alt+D and then arrow keys?

---

### Post by MichaelBurns on 2009-12-15
> **KIAaze said:**
> Alt+F1

I can't test the desktop icon navigation in Gnome right now, but in KDE 3 it works without any problems.Thanks, KIAaze.  There must be something wrong with my setup, then.  Alt+F1 does not work, either.  In fact, the first thing that I tried was Alt+everything.

> **KIAaze said:**
> ctrl+alt+D and then arrow keys?Still no love.

---

### Post by KIAaze on 2009-12-15
Have you tried deactivating desktop effects?

---

### Post by MichaelBurns on 2009-12-15
> **KIAaze said:**
> Have you tried deactivating desktop effects?How do I do that?

---

### Post by Sir Jasper on 2009-12-15
Hi,

If you right click on a blank area of your desktop do you get the Applications menu?

On your main question, do the items you want to arrow to change rarely, never or frequently? I only ask because there may be alternative methods that might suit.

There are lots of gifted helpers on this forum, but they may occasionally post non-working solutions as not so many of them use Xubuntu in general (or 9.04 in particular).

My regards

---

### Post by MichaelBurns on 2009-12-16
> **Sir Jasper said:**
> If you right click on a blank area of your desktop do you get the Applications menu?Yeah.  But that still requires use of the touchpad.  

> **Sir Jasper said:**
> On your main question, do the items you want to arrow to change rarely, never or frequently?The desktop has only changed twice since I've been running Xubuntu (a month, I guess).  So, That's probably rarely.

---

### Post by Agent9 on 2009-12-16
I have the same question for xUbuntu. Alt+F1 does not do anything. Is that only for gnome? Under Application Shortcuts only Alt+F2 is set up. Does Alt+F1 need to be manually configured?

---

### Post by Agent9 on 2009-12-17
> **MichaelBurns said:**
> Thanks, KIAaze. There must be something wrong with my setup, then. Alt+F1 does not work, either. In fact, the first thing that I tried was Alt+everything.

Found it. It's **Ctrl + Esc** in xUbuntu. I've also mapped it to the windows key by adding the following setting in the Application Shortcuts tab.

**xfce4-popup-menu = Super_L**

Let me know if it works for you too.

---

### Post by MichaelBurns on 2009-12-17
> **Agent9 said:**
> It's **Ctrl + Esc** in xUbuntu.

Let me know if it works for you too.No, it didn't.  Thanks for the suggestion, though.

---

### Post by Agent9 on 2009-12-18
> **MichaelBurns said:**
> No, it didn't.  Thanks for the suggestion, though.
Add the following to the Application Shortcuts tab:

**xfce4-popup-menu = Alt + F1**

---

