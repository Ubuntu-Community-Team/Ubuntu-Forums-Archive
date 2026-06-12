---
title: "F-Spot Crashes when clicked"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by andreasdelpaso on 2010-03-25
When i click F-Spot it starts to load and suddenly it crashes.
I run f-spot on terminal and i get :
(/usr/lib/f-spot/f-spot.exe:2559): GLib-WARNING **: g_set_prgname() called multiple times
[Info  10:52:13.704] Initializing DBus
[Info  10:52:14.047] Initializing Mono.Addins
[Info  10:52:14.531] Starting new FSpot server (f-spot 0.6.1.5)

** (/usr/lib/f-spot/f-spot.exe:2559): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:2559): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:2559): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:2559): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:2559): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  10:52:16.618] Starting BeagleService
[Info  10:52:16.668] Hack for gnome-settings-daemon engaged

(/usr/lib/f-spot/f-spot.exe:2559): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
The program '/usr/lib/f-spot/f-spot.exe' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 3711 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)



Any suggestions??
Thanks in advance!

---

### Post by s.fox on 2010-03-25
Hello,

Which gtk theme do you use?  I have seen people having trouble with fspot because of the theme (see below for links)  If you were to change it do you get the same error?

-Silver Fox

[1]  [https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/411941](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/411941)
[2]  [https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/486418](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/486418)

---

### Post by derekeverett on 2010-03-25
I know this isn't much help... but I've never been able to get f-spot working either.

My wife has been able to get it to import directly from her camera on her computer, but neither of us can get it to import existing .jpgs on either machine. It just crashes like you indicate yours does.

I've just uninstalled it completely and I'm looking for a better option. 

Hope you have better luck than I did. I'll be watching to see if you get a decent answer, but in my opinion F-spot is junk.

---

### Post by philinux on 2010-03-25
I use gthumb and gimp. Camera is just a usb mass storage device. I put my pics in folders named by date, Simples. ;)

---

### Post by derekeverett on 2010-03-25
> **philinux said:**
> I use gthumb and gimp. Camera is just a usb mass storage device. I put my pics in folders named by date, Simples. ;)

Gthumb seems to be exactly what I was looking for. Thank you.

Gimp is great too, I use it often but it's not much of an organizer.

---

