---
title: "Remote desktop app suggestions"
date: 2014-10-24
forum: Networking &amp; Wireless
---

### Post by Only1KW on 2014-10-24
I have recently moved my desktop at work from Windows 7 to Ubuntu 14.04, and am liking it better for the most part.  However, an issue I continue to struggle with is accessing my desktop remotely (either from my laptop while at meetings or from home when working after hours).  While I've found plenty of applications that allow this, I can't find any that meet these two needs of mine:


[LIST=1]
[*]I need to actually view the window session running on my terminal rather than starting a new remote X-session.  There are several running applications that I use locally on the desktop that I'd like to view its current state when connected remotely (e.g. status on a compile or code test run), and there are some applications that I can't run multiple instances simultaneously (e.g. 2 Eclipse sessions using the same workspace).
[*]I prefer to not have to view the entire desktop at once.  My desktop uses 3 24" monitors for its setup, and trying to fit them all on a single small laptop screen or having to constantly scroll around on the screen to find the window I need (including where a new windows has decided to randomly pop up) wastes a lot of time.
[/LIST]

With Windows 7, Remote Desktop Connection would automatically resize my desktop to fit the remote screen size which was *very* helpful, but I can't find anything that will do the same on Linux.  I don't necessarily require this solution though.  Any solution that will meet my two needs would be fine.  For example, if there was a way for me to x-forward individual windows that already exist locally, that would also be good, though I haven't found a way to do this either.

---

### Post by TheFu on 2014-10-24
I don't know of any method to do what you want.  The terrible security of X/Windows prevents connecting an x-client to a different x-server.

However, if you always ran the applications under a remote X/session (perhaps x2go?), then reconnecting to that same session from anywhere in the world is possible. I do this with a virtual machine desktop running in a private cloud.

The resolution issue is workable with good understanding of X/Windows.  Just set the screensize to what you need after the connection is made.

So - run everything in x2go always, then you can connect from anywhere, securely, assuming ssh-server is available from the remote location. Honestly, I hope your work doesn't allow that. It would be terrible security practice.

---

### Post by Only1KW on 2014-10-29
Thanks for the response.  I've spent the past few days trying your suggestions when I had some free time.

I gave x2go a try, which seemed to allow for changing the resolution after the session was started (unlike pre-existing VNC sessions).  However, it didn't work for me for a variety of reasons:


[LIST=1]
[*]It was unreliable for me.  Sometimes I could connect, but sometimes I would try and connect but the start would just hang at the "connecting" step.  Immediately retrying would sometimes cause the connect to complete successfully.  Other times, it would connect immediately but then I'd just get a blank screen with no windows or icons.  Note that this was tested on 14.04 with xfce on the desktop, and I had my laptop (used for client testing) sitting right next to the desktop on the same network.
[*]It is an entire virtual desktop rather than individual application windows, and that desktop has to be a strict rectangle in size.  I couldn't create one virtual desktop and display it on all monitors on my local desktop without there being area on the virtual desktop that didn't show up on my physical desktop due to being outside the range of my monitors (which combined are not a contiguous rectangle), or wasting space on my physical monitors.  Just creating a virtual desktop that fits on one monitor meant I had to make sure that I opened all applications I may want to share in that one virtual desktop and can't fully utilize the benefit of multiple monitors.  If I created a different virtual desktop for each virtual monitor, this means that if I then want to access these applications on a single-monitor system, I'd have to first switch between all the virtual desktops to find the correct one containing the application I wanted and then pull up the correct application on that virtual desktop, which is a pain and involves a lot of guess work.
[/LIST]

However, I really liked your base idea of creating "remote" application windows on my local desktop, which could then be pulled to other remote desktops as needed.  I played around with that, and long story short, I am trying WinSwitch.  So far it seems to be working well enough for me though it is a little flaky.  I can pull individual windows from local machine to remote machine and back again as needed as long as local machine stays running.

P.S. The SSH server on my work PC is available to my home PC via a VPN connection which is (hopefully) secure

---

### Post by Brandon121 on 2014-11-21
You could try this [windows remote desktop]("https://www.apponfly.com/en/"). You do not need to download or install anything, just register your email and you receive the RMD file immediately. You can simply run it afterwards. It works on any device as it is compatible with Windows, Mac and even Android (I tried only once, actually + I dont wanna claim it was primarily made for android, but it does work). The trial version is free of charge for one month!

---

