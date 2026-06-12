---
title: "Tunapie crashing... something wrong deeper?"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by Apurva Misra on 2010-01-03
Hi!
I am using Ubuntu 8.04 Hardy on my AMD64 Dual Core.
I installed tunapie on my system.
The problem is that when i try to reload the list of channels, it appears to be "downloading" something and then, it crashes.

running it on terminal, i found the following:

apurva@apurva-laptop:$ tunapie 
Streamripper not installed. Recording will not work
[COLOR="Blue"]
Streamripper not found. Recording will not work.
Please edit preferences manually.

(python:14553): Gtk-CRITICAL **: gtk_window_realize_icon: assertion `info->icon_pixmap == NULL' failed
Waiting for server
Downloading...

python: ../../src/xcb_lock.c:33: _XCBUnlockDisplay: Assertion `xcb_get_request_sent(dpy->xcb->connection) == dpy->request' failed.
Aborted[/COLOR]

Please help!

---

### Post by cariboo on 2010-01-03
Streamripper is in the repositories, you may have to install it before using Tunapie.

---

### Post by lhb1142 on 2010-01-03
> **Apurva Misra said:**
> Hi!
I am using Ubuntu 8.04 Hardy on my AMD64 Dual Core.
I installed tunapie on my system.
The problem is that when i try to reload the list of channels, it appears to be "downloading" something and then, it crashes.

running it on terminal, i found the following:

apurva@apurva-laptop:$ tunapie 
Streamripper not installed. Recording will not work
[COLOR="Blue"]
Streamripper not found. Recording will not work.
Please edit preferences manually.

(python:14553): Gtk-CRITICAL **: gtk_window_realize_icon: assertion `info->icon_pixmap == NULL' failed
Waiting for server
Downloading...

python: ../../src/xcb_lock.c:33: _XCBUnlockDisplay: Assertion `xcb_get_request_sent(dpy->xcb->connection) == dpy->request' failed.
Aborted[/COLOR]

Please help!

I too like to record certain internet radio broadcasts. I am currently using 9.10 and I do not know if my method will work with 8.04 but it's worth a try.

I gave up on Tunapie and Streamtuner due to odd behavior, similar to what you're experiencing.

I now "tune in" to my favored internet radio stations using VLC. In that program is an option to have a "record" button - and this records streams perfectly.

Yesterday I recorded the entire Metropolitan Opera broadcast of "Hansel and Gretel" via WHRO. It came out perfectly.

I hope this helps you.

---

### Post by Apurva Misra on 2010-01-03
> **cariboo907 said:**
> Streamripper is in the repositories, you may have to install it before using Tunapie.

Hey cariboo90
Thanks for the reply :) but if i don't install Streamripper, Recording will not work as i am notified on opening the app. The problem of program crashing seems to be somewhere else..

[B]python: ../../src/xcb_lock.c:33: _XCBUnlockDisplay: Assertion `xcb_get_request_sent(dpy->xcb->connection) == dpy->request' failed.
Aborted[/B]

Any idea??? 
:confused:

---

### Post by Apurva Misra on 2010-01-03
> **lhb1142 said:**
> I too like to record certain internet radio broadcasts. I am currently using 9.10 and I do not know if my method will work with 8.04 but it's worth a try.

I gave up on Tunapie and Streamtuner due to odd behavior, similar to what you're experiencing.

I now "tune in" to my favored internet radio stations using VLC. In that program is an option to have a "record" button - and this records streams perfectly.

Yesterday I recorded the entire Metropolitan Opera broadcast of "Hansel and Gretel" via WHRO. It came out perfectly.

I hope this helps you.
Hey lhb1142 :)
Thanks for the reply. 
I want to use Tunapie because of its ability to find and display channels, so that i don't have to do the **copy url-paste url** thing over and over again...
so until i find something that works better... not giving up :D

---

### Post by Apurva Misra on 2010-01-05
Though seems pretty unreasonable.... :) i installed all the libxcb's through synaptic and :guitar: it worked!!!

PS: please don't ask what worked that was not working earlier - i have no clue... :D

---

