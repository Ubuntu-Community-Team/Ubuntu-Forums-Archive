---
title: "Removing programs from start up!"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by vasiauvi on 2009-08-11
Hello all,
I want to remove from my startup programs Ktorrent but it doesn't appear in any of this:*Startup Applications* or *rcconf* or *Services*.
Can I use an other programs or config files? I know that are programs like this but i don't know how are named.
I have Ubuntu 9.04.
Can anyone want to tell me about some of this programs?
Thanks!

---

### Post by realzippy on 2009-08-11
if you close ktorrent in the terminal:

**sudo killall -9 ktorrent**

and restart session,is it running again?

---

### Post by vasiauvi on 2009-08-11
> **realzippy said:**
> if you close ktorrent in the terminal:

**sudo killall -9 ktorrent**

and restart session,is it running again?

Yes, it's still running! Also Pidgin is behaving in the same way: i don't find a instance of those 2 programs in the Preferences/Startup Applications or Administration/Services.

---

### Post by realzippy on 2009-08-11
You use KDE ?

---

### Post by vasiauvi on 2009-08-11
> **realzippy said:**
> You use KDE ?

Sorry for not mentioning ! I am using GNOME!
But what could I try is to close Pidgin and ktorrent and all the programs and after that to check in System/Preferences/Startup Applications the *Automatically remember running applications when logging out *.
Let's see what happens!

---

### Post by realzippy on 2009-08-11
...is there an advantage in the use of ktorrent instead of transmission?

---

### Post by vasiauvi on 2009-08-11
> **realzippy said:**
> ...is there an advantage in the use of ktorrent instead of transmission?
I am using ktorrent because it's more easy for me! With Transmission I can download but the upload doesn't work.
If i could manage the upload to work i will use Transmission or even rtorrent. But until then ktorrent is much easy!

I have restarted the PC and no ktorrent or pidgin appeared. 
I hope that it will stay like this in the future!

Thanks!

---

### Post by realzippy on 2009-08-11
...just installed ktorrent (also use gnome) to face your problem.Restarted,
no ktorrent running.Sorry for stupid question ;-),but did you hit "quit"
in ktorrents panel icon before closing session?

---

### Post by vasiauvi on 2009-08-11
> **realzippy said:**
> ...just installed ktorrent (also use gnome) to face your problem.Restarted,
no ktorrent running.Sorry for stupid question ;-),but did you hit "quit"
in ktorrents panel icon before closing session?

I remember that some time ago i have put ktorrent and also pidgin in the startup but after that i have removed them from Startup Applications but this had no influence. Because of that i was looking after a program to see ALL the programs loaded on startup. I have used rcconf but ktorrent and pidgin ware not there and I was wondering how this programs are loaded.

:) I have hit Quit on ktorrent and also pidgin and now after a restart and after I checked *Automatically remember running application when logging out* this 2 programs were not loaded anymore.
Hope that on the next restart will stay the same!

---

