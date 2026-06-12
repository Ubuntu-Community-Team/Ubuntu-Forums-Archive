---
title: "F-Spot Photo Manager Problem"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by Noampod on 2010-01-16
I am unable to run f-spot, if I try from the terminal this is the message I get:

[Info  16:28:29.391] Initializing DBus
[Info  16:28:29.514] Initializing Mono.Addins
[Info  16:28:29.673] Starting new FSpot server

(f-spot:26106): Gtk-CRITICAL **: gtk_window_resize: assertion `width > 0' failed
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 416 error_code 1 request_code 135 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Thanks for any help.

---

### Post by ajgreeny on 2010-01-16
Try renaming the two folders in your home:-
/home/*user*/.gnome2/f-spot
/home/*user*/.gconf/apps/f-spot
as backups and see if you can then start f-spot.  If that is not the answer you can delete the new versions of the folders that have been made and restore the originals.

---

### Post by Noampod on 2010-01-16
Thank you for your reply. I was still unable to run f-spot. After renaming the the folders only one showed a new f-spot folder: /home/user/.gnome2/

The /home/user/.gconf/apps/ only had the backup folder.

---

### Post by Noampod on 2010-01-17
Can someone please help me with this? I have tried what the above poster suggests but with out success. Could it be a desktop problem, as I was having trouble changing backgrounds. Also I'm not able to switch visual effects. I tried killall nautilus and I can now change backgrounds again. One other thing when I scroll web pages or documents I get a ripple effect, where as before scrolling was always smooth. 

Cheers

---

### Post by Noampod on 2010-01-18
Please someone out there must have some idea for a solution. I've searched high 'n' low but no joy.

---

### Post by TnTMike on 2010-01-23
There have been a number of posts about this problem. The same thing was happening to me try thread [http://ubuntuforums.org/showthread.php?t=1307641&highlight=f-spot]("http://ubuntuforums.org/showthread.php?t=1307641&highlight=f-spot") suggests a fix that worked for me as well as a few others.
I changed my desktop theme to human from new wave.

---

