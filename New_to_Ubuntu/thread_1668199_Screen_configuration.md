---
title: "Screen configuration?"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by newlinuxlady on 2011-01-16
I have a TV connected to the computer- I can't seem to get the screen size to line up- i am missing the top, bottom and sides- cut off. How do I get it configured properly? It has a 21.53 diagonal viewing area.

---

### Post by taseedorf on 2011-01-16
The problem is usually with your tv OR with your video card. :)

First off, do you have an overscan option on your tv? If so, can you tune it and change it? Also, my tv has options for stretch, wide fit, etc.... make sure it is set to "Just scan"...

ON the video card side....if you're using an nvidia chipset....there is sometimes and overscan option you can tune, or you can set the correct resolution too....  I have no idea about ATI

---

### Post by newlinuxlady on 2011-01-16
oh- can I not just do it through settings or something like that on the computer?

---

### Post by taseedorf on 2011-01-16
Oh you certainly can! It just depends on what kind of video card you have.  I have absolutely no experience with ATI video cards....but if you have an nvidia card I can help.  I believe it is an "overscan" problem.  Do you know which card you have? try typing 'lspci' into terminal if you don't know...

If it happens to be nvidia, install the settings manager
sudo apt-get install nvidia-settings
(type that into a terminal window)
and then run
gksu nvidia-settings
and go to the last option at the bottom, i believe...maybe second to last.... and look for an option for adjusting overscan. :)

---

### Post by newlinuxlady on 2011-01-16
Good News- it is Nvidia and I ran the first command and it gave me the nvidia window but then it went away and this message in the terminal was there- what does this all mean?


goodwill@Multimedia1:~$ gksu nvidia-settings
The program 'nvidia-settings' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 214 error_code 2 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by newlinuxlady on 2011-01-16
And I could not find this when the nvidia window was open.  How do I get the nvidia window to open again with the penguin on it?

---

### Post by Perfect Storm on 2011-01-16
What happen if you run it without gksu
```
nvidia-settings
```

---

### Post by taseedorf on 2011-01-16
In my experience, that has happened with outdated software causing a gliche.  Could be gksu, could be nvidia-settings.  if the above code doesn't work, try this...
```

sudo apt-get remove nvidia-settings
sudo apt-get update
sudo apt-get install nvidia-settings



```

Then try the code I told you about first again.

Also, you could try finding out what specific video card you have and install the latest drivers from nvidia at their website as the ones that get installed by default are slightly older.  This problem could be corrected by itself, but it still seems like an overscan issue.

---

### Post by taseedorf on 2011-01-16
Here is a link with some solutions to a similar problem, they may help you.

[http://ubuntuforums.org/showthread.php?t=671065]("http://ubuntuforums.org/showthread.php?t=671065")

---

