---
title: "f-spot photo manager"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by nilsolaris on 2009-01-01
Each time i try to open f-spot photo manager, i get this error:

[Info  19:49:10.647] Initializing DBus
[Info  19:49:10.778] Initializing Mono.Addins
[Info  19:49:11.027] Starting new FSpot server

(f-spot:13349): Gtk-CRITICAL **: gtk_window_resize: assertion `width > 0' failed
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 324 error_code 1 request_code 159 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
 
Would anyone happen to know how to get around this?

---

### Post by nilsolaris on 2009-01-01
bump.

---

### Post by nilsolaris on 2009-01-01
Alright so if no one can help me with this problem, could i please get a recommendation on another program to import photos?

---

### Post by mkvnmtr on 2009-01-01
Someone may see this and be able to help you but I could never get F-spot to work. I installed digikam and everything worked. It is a KDE app but just added a few things.

---

### Post by nilsolaris on 2009-01-01
Thank you mate, ill give it a go:D

---

### Post by RomeReactor on 2009-01-01
Hi. This problem seems to be directly related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/297406"). Which version and architecture of Ubuntu are you running?
```
lsb_release -a
```
```
uname -m
```

Is your system regularly updated? [This thread]("http://ubuntuforums.org/showthread.php?t=977870") discusses the same problem.

As for other software to import pictures, you could try [Digikam]("http://www.digikam.org/"); to install it:
```
sudo aptitude install digikam
```
or press [here]("apt:digikam").

---

### Post by chrisod on 2009-01-01
Picasa for Linux works great.

---

### Post by cariboo on 2009-01-01
It is forum policy that you should wait at least 24  hours before bumping a thread. THe person that may be able to answer your question is out there, but just hasn't seen your post yet.

If you go to System-->Administration-->Synaptic Package Manger and click the search button and enter photo in the search, you shlould be able to find a photo manager that suits you.

Jim

---

### Post by girard on 2010-06-06
I was away from using ubuntu for a while, and now that I'm back, I noticed that the default photo manager still lags behind. I had to install Picasa.

I find Fspot's interface to be problematic, the way it handles images both within the system and during import, the lack of uploading tools (this is what prompted me to look for another one). 

Just putting in my 5 cents and hoping developers will see this as an issue in terms of Ubuntu, (well Fspot) standing up against competition. A good, well "web" integrated multimedia manager is essential in desktops nowadays.

For now, I'm still enjoying my install and well... Picasa

---

