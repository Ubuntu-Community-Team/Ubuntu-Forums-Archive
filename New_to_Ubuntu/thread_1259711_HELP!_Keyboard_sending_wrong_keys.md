---
title: "HELP! Keyboard sending wrong keys"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by nowhere@cox.net on 2009-09-06
Help,

I'm posting usings hubby's pc because my laptop is almost unusable. I installed Ubuntu a couple weeks ago and all is working fine but yesterday I installed gnome-do and virtual box non-free. It all worked just fine. I shut it down, went to bed and got up today and fired it up.

I type my password at the login and it logs into ubuntu fine. At first, I could not click my mouse and the keyboard shortcuts did nothing. I discover hitting the power brought up the powerdown window and it would automatically shut down. After rebooting, I can log in click on stuff too but when I type (like in text editor) some keys are sending strange characters like ~6 stuff. I can't change anything that requires my password because the keys are wrong, but it DOES let me log in so it's something that messes up after I log in.

Hubby suggest ctrl-alt F1 but it won't let me log in there either (password wrong).

What can I do???

Thanks!
H.

---

### Post by Bodsda on 2009-09-06
> **nowhere@cox.net said:**
> Help,

I'm posting usings hubby's pc because my laptop is almost unusable. I installed Ubuntu a couple weeks ago and all is working fine but yesterday I installed gnome-do and virtual box non-free. It all worked just fine. I shut it down, went to bed and got up today and fired it up.

I type my password at the login and it logs into ubuntu fine. At first, I could not click my mouse and the keyboard shortcuts did nothing. I discover hitting the power brought up the powerdown window and it would automatically shut down. After rebooting, I can log in click on stuff too but when I type (like in text editor) some keys are sending strange characters like ~6 stuff. I can't change anything that requires my password because the keys are wrong, but it DOES let me log in so it's something that messes up after I log in.

Hubby suggest ctrl-alt F1 but it won't let me log in there either (password wrong).

What can I do???

Thanks!
H.

Go to:
System > Preferences > keyboard > Layouts(tab)

and see what is set as default, it may just be a wrong keymap. If not, then try uninstalling gnome-do. It may not help, but that was the main 'strange' thing that changed before things went wrong.

Hope this helps,
Bodsda

---

### Post by nowhere@cox.net on 2009-09-06
Thanks for the reply. There was only one keyboard layout so I am assuming that's what was being used (USA) but the dot in the select thingy wasn't checked. I can't change any of it anyway because I can't type the correct password. Same goes for uninstalling anything.

I did get some advice to delete a folder called .gconf and reboot. It seems to have fixed the problem. Gnome-do seems to be behaving again now too.

I don't have any idea what the problem was or how it got messed up still tho...

Thanks!

---

