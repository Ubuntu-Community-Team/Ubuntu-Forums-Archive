---
title: "Unresponsive internet"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by Neikius on 2007-05-06
I think something similar happens to others too, but my net aint exactly slow. It is unresponsive. Like a new connection needs a few seconds to be established. Like I must wait 15 sec for the web page to display at all. My connection speed is 100mbit optics and the thing runs like 10x faster in windows.

for example the ping : 
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=1 ttl=48 time=35.8 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=2 ttl=48 time=35.8 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=3 ttl=48 time=35.9 ms

--- ubuntuforums.org ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 6121ms
rtt min/avg/max/mdev = 35.843/35.887/35.922/0.158 ms

As you see ping is nice, but the total time for pinging was 6 seconds!

Same when I ssh to my debian router - takes 5 seconds, maybe 10 for it to display "password:" prompt, while putty on windows takes <1 sec. Really annoying.

And no, I don't wanna remove ipv6. My router should be ipv6 capable (debian), I think its even set up, thought I doubt any ipv6 traffic is taking place. Noob in ipv6 matters. Any advice?

---

### Post by Rui Pais on 2007-05-06
> **Neikius said:**
> 
And no, I don't wanna remove ipv6. My router should be ipv6 capable (debian), I think its even set up, thought I doubt any ipv6 traffic is taking place. Noob in ipv6 matters. Any advice?

it's not the question of you want or not remove ipv6. 
It's, if you remove ipv6 did it work? or not - and then the problem is something else.

If the problem is in fact ipv6 i don't see much alternatives then not use it. 
(Not that matters much... it's like remove the parachutes you have in your car cause in 50 or 100 yers all cars will flying... )

---

### Post by Neikius on 2007-05-06
Oh yeah. It is not ipv6 it seems.

And I am 90% positive it aint the router either (remember the stuff works ok in windows). Only in ubuntu it doesn't work (talking about 7.04 here).

Maybe wouldn't be wrong to mention that terminals are kinda sluggy too when opening (3-5 sec to open a simple terminal window is a bit much).

edit: to elaborate a bit, I've removed the module from aliases file, so ipv6 doesnt show on lsmod and ifconfig doesn't have ipv6 addresses anymore.

---

### Post by Rui Pais on 2007-05-06
> **Neikius said:**
> Oh yeah. It is not ipv6 it seems.

And I am 90% positive it aint the router either (remember the stuff works ok in windows). Only in ubuntu it doesn't work (talking about 7.04 here).
router are hard to broken... and since it work on Window, not a problem there for sure
> Maybe wouldn't be wrong to mention that terminals are kinda sluggy too when opening (3-5 sec to open a simple terminal window is a bit much).

edit: to elaborate a bit, I've removed the module from aliases file, so ipv6 doesnt show on lsmod and ifconfig doesn't have ipv6 addresses anymore.

Yes with that ipv6 is not loaded and your net work is using a ipv4 address. If its slow then the problem should be somewhere else.

The 3-5 sec to start a terminal could be something. Not normal definitely.

Did something appears if, from a gnome-terminal, you start/run another gnome terminal? 
(e.g.: something like 'Vte-WARNING **: Can not find appropiate font for character U+ac00.')

Did you have any weird errors on .xsession-errors?

Try [this suggestion here]("http://ubuntuforums.org/showthread.php?t=388765"), to see if that helps.

good luck.

---

### Post by Neikius on 2007-05-06
.xsession-errors is full of errors... 

and I tried the other thing suggested;

I will report tomorrow coz I have to go to bed now.

---

### Post by Neikius on 2007-05-07
This message seems to repeat itself: 
```

(process:7142): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:7142): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `GDK_IS_DISPLAY (display)' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to call gtk_init(0,0);

```
There are some others too, I could upload the file(s) somewhere if it helps.

Anyway since I've changed that localhost thingy things did get more responsive, but still takes helluva time to ssh, ping and opening webpages lags (I swear web pages are a bit faster now! but still not ok).

---

