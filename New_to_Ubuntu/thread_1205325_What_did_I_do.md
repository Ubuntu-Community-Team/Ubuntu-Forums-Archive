---
title: "What did I do?"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by Duffman3 on 2009-07-05
I was having problems earlier today with flash in firefox. So I decided to start fresh and uninstall/ reinstall firefox. After the unistall it was giving me grief about 2 dependecies that wouldn't install. So I went into the SPM and manually selected the 2. Now when I start my computer I login in and the mouse comes on the screen, but nothing ever loads.

So i'm not sure where to begin to go to even give you guys more information, I need help.

Thanks.

---

### Post by Sef on 2009-07-05
How did you uninstall and reinstall Firefox?

---

### Post by SunnyRabbiera on 2009-07-05
It might have removed GDM, the log in manager, firefox is a majopr key in the ubuntu desktop package so removing it might have removed other things.
if you have a console login only try the command sudo apt-get install ubuntu-desktop

---

### Post by Duffman3 on 2009-07-06
I uninstalled Firefox using synaptics package manager.

I also tried using sudo apt-get install ubuntu-desktop from the shell in recovery mode, which is the only shell I can geto, and returned a whole bunch of dependencies followed by an E message saying incomplete packages or something to that effect.

---

### Post by Duffman3 on 2009-07-06
/bump please help!

---

### Post by nothingspecial on 2009-07-06
Can you post the exact error message?

Try ```
sudo apt-get -f install
```

```
sudo dpkg --configure -a
```

Then try to install ubuntu-desktop again

```
sudo apt-get update
```

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Duffman3 on 2009-07-06
I guess like an idiot I was running these all from the shell with no networking on... *bangs head on table...

So I just tried:

sudo apt-get install update

It gets to about 99% and times out saying not all packages were installed.

And: sudo apt-get install ubuntu-desktop returns about 100 python realated dependency errors and then says "E Broken Packages."

Im gonna try your suggestions right now nothingspecial

---

### Post by Duffman3 on 2009-07-06
So, I'm still having problems with sudo apt-get update, I feel like my problem is now a combination of the firefox unistallation and the apt-get update connecting to the wrong servers, but I'm not sure how to correct it from timing out everytime.

---

### Post by Duffman3 on 2009-07-07
--Update *FIXED*

I'm so ******* proud of myself, I fixed it all by myself.
Turns out I was right about the apt-get sources list being borked.
I put in my Ubuntu install cd and ran it without changes and used it to view the sources.list file on my current installation to find out that all my update sites werent for jaunty.
Switched to the back.
Ran sudo apt-get update install ubuntu-desktop and all is well.

---

