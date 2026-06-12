---
title: "Improving boot speed..."
date: 2009-02-26
forum: New to Ubuntu
---

### Post by Adamantus on 2009-02-26
I've been customizing my desktop a lot lately (installing awn, trying different themes, etc.), and I feel that it has taken a toll on my boot speed. I've made a boot chart, and it says I'm at 25 seconds (I couldn't attach the image though). Although my boot to the login screen is quite short, after login it takes a long time for my desktop to appear (along the lines of 15 seconds). I've done a lot of the tweaks I've found on google (enabled concurrent booting, disabled lots of startup services, and quite a few others), but was wondering if there were any that could speed up the boot after login. Is there anything to do to speed up this section of the boot?

---

### Post by sdennie on 2009-02-27
The only real thing you can do is go to System->Preferences->Session and disable startup programs that you are positive you don't need.  One other possibility is to use preload or the information found here: [http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651).  I'm not sure if any of that will have much effect though.

---

### Post by Ripose on 2009-02-27
I have not tried this myself yet but [Check This]("http://ubuntu-tweak.com/")
They claim their tweaks will work on everything up to and including Ubuntu 9.04 hmmmmmmm.

EDIT: Well I tried Ubuntu Tweak now. Not much to do with speed, but still handy.

---

### Post by Adamantus on 2009-03-02
I had already done the Ubuntu-Tweak and didn't get much out of it.

I tried doing the readahead, but when I push Ctrl-Alt-F8, the prompt goes to "Setting power management..." and then has a flashing cursor below it and nothing happens. I've let it sit for about half an hour with nothing happening. Is their some reason this doesn't go to the GDM prompt?

---

### Post by jmmL on 2009-03-02
I assume you're using intrepid at the moment.

I'm testing jaunty, and my laptop now takes 1/3 less time to boot (30s -> 20s), and takes half the time to log in (50 -> 25 ish). You seem to already have good boot and log-in times compared to me, but I would expect similar improvements when jaunty gets released.

Of course, if you're feeling brave, you can always try it now.. :P

---

### Post by Adamantus on 2009-03-02
Sorry about the last post...I was just being stupider than usual.

All I can say is wow, "Wow". My login time was only about 1/3 of the usual sequence. I was going to get up to get something, thinking it would be logged in by the time I got back, but it finished before I was even able to get up. And I didn't even stop some of the larger files that I could, so I could possibly get even faster. Thank you very much. This is exactly what I was looking for.

jMMl:

I'm actually using Hardy right now because Intrepid was messing with my wireless. I'm planning on upgrading to Jaunty when it comes out. If it is able to speed up my boot + login, I'd be impressed.

---

### Post by lviggiani on 2009-03-03
Hi Guys,
I read almost everywhere that Intrepid has increased the boot time compared to the past but I would like to make sure that my system boot time is within what is expected for Intrepid.
Now it takes about 1 minute from the grub menu to gdm login screen + 15 seconds after login to load the desktop and being ready to accept my inputs.

My computer is a Dell XPS M1330 notebook with Intel Core2Duo T7250 @ 2.00Ghz with 3.0GiB or RAM.
I'm running Intrepid i386 upgraded from Hardy and I also have vmplayer installed (I'm sure that vmware network services takes time to start up)
Kernel is 2.6.27-13-generic

I've been reading that someone is taking 35 seconds to boot with a similar configuration, so I'm wondering if my system is ok or I better format it and restart from a clean install.

I tried also the "concurrency=shell" way but it's even worst... :(
Thanks!

---

