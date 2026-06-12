---
title: "Keyboard settings in Natty"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by MadMonkey1966 on 2011-05-19
I have a fresh install on my desktop of Natty.

All of a sudden my keyboard keep changing from UK to USA for no reason. It seems to change depending on what application i am using.

I have tried & tried in setting to sort it, even in preferences at the top, i went in and removed USA, but it comes back.

No idea why it has started doing this, can anyone help.

Many Thanks :)

---

### Post by grahammechanical on 2011-05-19
What utilities did you try to correct this?

There is the one called Keyboard. You can add and remove keyboard layouts. So, you could add an English (UK/GB) layout that fits your keyboard. May be the system is seeing your keyboard as English (US). I have a second USB keyboard that became faulty. If I plug that in as well as my present keyboard it will get a keyboard layout of English (US).

There is also the utility called Language Support. Make sure the language for the operating system is set to English (United Kingdom) and set to apply system wide.

I hope this helps.

Regards.

---

### Post by MadMonkey1966 on 2011-05-19
Thanks for the quick reply :)

I had not tried Keyboard in the Preferences Menu, but it does the same as the link at the top of the page (which has now gone)

I went into Language Support and it said it had not been completely installed, so i followed the instructions, and set it to English (System wide) and also i went into Keyboard and deleted the USA one.  then i re-booted.

This has actually removed the link at the top of the screen, where as it never had before.

So hopefully i think you found the problem.

Many Thanks for your help :)

---

### Post by MadMonkey1966 on 2011-05-19
I dont believe it, just turned computer back on again and the USA is up the top of the page (just left of the Network connection icon) and it is using USA keyboard again !!!!

Now i am confused...... any other ideas anyone ? :)

---

### Post by MadMonkey1966 on 2011-05-20
Turn on this morning, and at top of the screen it says i am using GBr (United kingdom) keyboard.


Yet when i use Shift & 2 i get @ rather than "
and 
when i use Shift ' i get " instead of @

This is getting weirder :( and more annoying

---

### Post by tordeu on 2011-05-20
I have the same problem.

It's a bug and can be found [here]("https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/757370").

Try pressing Shift + CAPS Lock to change the Layout and test if it works in a text editor, for example. 
If it does not work, do the following:

[LIST=1]
[*]open "Keyboard Preferences" (it's called "Keyboard" in Unity)
[*]go to the "Layouts" tab
[*]click on "Options" at the bottom.
[*]look for and click on "Key(s) to change layout"
[*]select a shortcut for changing the layout
[*]use that shortcut to switch the layout back after reboot until the bug is fixed.
[/LIST]

---

### Post by MadMonkey1966 on 2011-05-20
ahhhh most odd i have only just noticed it (well few days ago) :)

I did not know about Shift + CAPS Lock, and that does the trick.

I still can not understand why if you delete a keyboard layout (like the USA one i keep removing) it comes back again after reboot.

Thanks for the Help &  information

---

### Post by tordeu on 2011-05-20
That's is not supposed to be that way. It's a bug. All I know is that I did not have any problems with keyboard layouts in 10.10. Let's hope they fix the issues and the fixes are distributed with an update.

---

