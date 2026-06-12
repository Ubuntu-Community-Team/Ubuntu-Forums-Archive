---
title: "How to create a desktop icon for Fortune"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by yeehi on 2009-04-14
It would be nice to click on something and then have Fortune appear with a quotation in a pleasant looking window.

How can I do this? 

Thank you!

---

### Post by Jakey_TheSnake on 2009-04-14
What's fortune? :l

edit: the command is "fortune", too. 

"gedit `fortune`" opens however many tabs of gedit, with each one's header a word from the fortune command, in order. Hmmmm. Hold on a sec.

---

### Post by tj111 on 2009-04-14
Right-click on the desktop, select "Create Launcher".  Name it 'Fortune' (or whatever you want) and select whatever icon you want.  Then under `command`, enter this:

Edit: it works from the terminal but not a launcher.  Hold on while I work it out.
```

zenity --info --text="`fortune`"

```

Edit2: See my fix below

---

### Post by halitech on 2009-04-14
you could install conky and have the fortune show up there

---

### Post by Jakey_TheSnake on 2009-04-14
> **tj111 said:**
> Right-click on the desktop, select "Create Launcher".  Name it 'Fortune' (or whatever you want) and select whatever icon you want.  Then under `command`, enter this:

Edit: it works from the terminal but not a launcher.  Hold on while I work it out.
```

zenity --info --text="`fortune`"

```

So:

```
gedit "`fortune`"
```

Puts the entire fortune into one gedit header...how would I go about putting it inside the file body, or can you not?

---

### Post by aktiwers on 2009-04-14
You can do it with conky too... have it on your desktop. Like I have added it here:

---

### Post by tj111 on 2009-04-14
Ok only way I could get it to work was to stick it in a seperate script then make the launcher execute the script.

To start out, put the following script in a file and save it somewhere in your home directory (i.e. /home/yeehi/fortune)
```

#!/bin/sh
zenity --info --text="`fortune`"

```

Then right click on your desktop, create a launcher, and for the command type in:
```

sh /home/yeehi/fortune

```

That should do the trick

---

### Post by yeehi on 2009-04-14
Thank you for the ideas so far!

I tried the gedit ¨fortune¨, but it launches gedit without a fortune for me, and gedit isn´t so pretty... no nice colours.

---

### Post by yeehi on 2009-04-14
Thank you!

That script works nicely; I can click on it as often as I like, and a nice little information message appears with my fortune.

:) ):P

---

