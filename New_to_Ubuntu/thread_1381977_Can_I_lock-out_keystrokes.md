---
title: "Can I lock-out keystrokes?"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by Javelin Dan on 2010-01-15
Is there a way to require an authorization before any accidental key-stroke command is immplimented? I keep inadvertantly entering keystroke commands and disabling important stuff - so far menu bar, wireless network. I need protection from self inflicted injury!

---

### Post by Hospadar on 2010-01-15
I think this is what you are looking for:
[http://www.linuxscrew.com/2008/09/15/faq-how-to-disableremap-a-keyboard-key-in-linux/](http://www.linuxscrew.com/2008/09/15/faq-how-to-disableremap-a-keyboard-key-in-linux/)

I believe it's possible to do combinations as well as single keys with that program, but I'm not sure, you can do "mod xmodmap" or google around and see.

It's a command line thing, and it's something that'll need to get run at startup every time, the easiest way to make that happen is make a script, save it in your home directory somewhere, then add that script (/home/yourname/wherever-you-put-it/yourscript.sh) to the gnome startup programs (System->Preferences->Startup Programs)

---

### Post by Javelin Dan on 2010-01-15
Thanks for the get-back but all that seems a little beyond me at this time. I'm still dragging my knuckles on the ground.

---

