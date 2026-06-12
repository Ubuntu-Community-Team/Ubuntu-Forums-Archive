---
title: "Need help - strange problem, annoying"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by Harlequin. on 2009-08-31
When I use the apostrophe key it doesn´t actually write an apostrophe, it makes it so the next key I hit looks weird eg: &#314;óó&#7729; <-- I pressed the apostrophe key between each letter.

It also does the same for the ` key (whatever it&#347; called). It is a huge annoyance as I tend to punctuate, and like this I am forced to press the apostrophe key twice. 

I would like this to stop, please let me know how to do this.

---

### Post by LewRockwell on 2009-08-31
you might use these as food for thought as they reference keyboard mapping:

[http://ubuntuforums.org/showthread.php?t=34135](http://ubuntuforums.org/showthread.php?t=34135)

[http://www.petersblog.org/node/878](http://www.petersblog.org/node/878)

keep us posted on your progress!

.

---

### Post by TeoBigusGeekus on 2009-08-31
Go to System->Preferences->Keyboard and check your installed layouts.

---

### Post by Harlequin. on 2009-08-31
> **TeoBigusGeekus said:**
> Go to System->Preferences->Keyboard and check your installed layouts.

I´ve played around with all that stuff already.

---

### Post by Harlequin. on 2009-08-31
I need to know what to do please I don´t have much time to get this done.

---

### Post by LewRockwell on 2009-08-31
are you able to test this with a different keyboard?

.

---

### Post by gldearman on 2009-08-31
This is a laptop, right?

What is the manufacturer and model?  Is it a Dell, by any chance?

I had this problem some time ago with a Dell Latitude C310.  Changing the keyboard layout didn't help.  I think it's something funny with the way the keyboard is set up so that they can have fewer keys on it than a desktop keyboard.

It mostly bugged me in the terminal -- it became very difficult to type a string inside single quotes.

If it's any help, you can get the ' character by typing <'> then <Spacebar>.

---

### Post by gldearman on 2009-08-31
Oh, and what is your current keyboard layout?  USA, USA International, or something else?

---

### Post by Harlequin. on 2009-08-31
> **gldearman said:**
> This is a laptop, right?

What is the manufacturer and model?  Is it a Dell, by any chance?

I had this problem some time ago with a Dell Latitude C310.  Changing the keyboard layout didn't help.  I think it's something funny with the way the keyboard is set up so that they can have fewer keys on it than a desktop keyboard.

It mostly bugged me in the terminal -- it became very difficult to type a string inside single quotes.

If it's any help, you can get the ' character by typing <'> then <Spacebar>.

Thanks for your help, however it is a desktop computer and this did not happen when windows xp was running on it.


It is usa:intl

---

### Post by gldearman on 2009-08-31
Have you considered changing it to USA:English?

[US International keyboards]("http://en.wikipedia.org/wiki/Keyboard_layouts#US-International") are configured to type critical marks and accents, so that it is easier to type characters that do not appear in English.

If that fails, you could try the solution arrived at in [THREAD=341545]this thread[/THREAD].

You may also want to make sure that your keyboard model is correct.  To what model is it currently set? (That should be displayed in the same window as keyboard layout, under System>Preferences>Keyboard, in the "Layouts" tab.)  Is that correct?

---

### Post by Harlequin. on 2009-08-31
> **gldearman said:**
> Have you considered changing it to USA:English?

[US International keyboards]("http://en.wikipedia.org/wiki/Keyboard_layouts#US-International") are configured to type critical marks and accents, so that it is easier to type characters that do not appear in English.

If that fails, you could try the solution arrived at in [thread=341545]this thread[/thread].

You may also want to make sure that your keyboard model is correct.  To what model is it currently set? (That should be displayed in the same window as keyboard layout, under System>Preferences>Keyboard, in the "Layouts" tab.)  Is that correct?


There was no us english selection, canada english seems to work fine though, thankyou.

By the way, '''''''''''''' :] '`'`'`

---

### Post by gldearman on 2009-08-31
Glad it's working, but you still may run into some trouble with a Canada-English keyboard layout.

If you use the command line at all,you are going to end up typing "|" and "~" a fair bit.  If you have a US keyboard, but the layout is set to Canada-English, try typing those characters, and you'll see what I mean about having problems.

---

### Post by Harlequin. on 2009-09-14
> **gldearman said:**
> Glad it's working, but you still may run into some trouble with a Canada-English keyboard layout.

If you use the command line at all,you are going to end up typing "|" and "~" a fair bit.  If you have a US keyboard, but the layout is set to Canada-English, try typing those characters, and you'll see what I mean about having problems.

Works fine. I know what you're talking about though and I had to change TO canada layout to fix it.

---

