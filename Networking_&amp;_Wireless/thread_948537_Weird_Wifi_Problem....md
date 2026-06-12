---
title: "Weird Wifi Problem..."
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by floydian_slip on 2008-10-15
Hello all,

I'm currently in France and having weird problems with my wifi on Ubuntu (Hardy Heron). My roommate and I are sharing wifi with our neighbor, who gave us his password a couple days ago, She has a Mac and has been connecting fine from the start. I, on the other hand, had to try about 10 times before finally I connected. From that point on, all was fine...

...until yesterday. My wireless suddenly cut out, and I haven't been able to get online since. My roommate's Mac, however, still connects just fine. Now there are two problems: 1) obviously, not being able to re-connect to my neighbor's wifi no matter what I do. I see his wifi in my network list, with good strength, but it simply will not connect.

2) possibly more importantly, earlier today I clicked on a different wifi network--"Neuf Wifi"--which is a wifi service all throughout France for which you must pay. I connected just fine to that, although I cannot surf because I haven't paid--it simply brings me to the registration page. So I connected there just fine. BUT: since then, I've been able to "connect" every so often back to my neighbor's network, but when I try to surf, I get thrown back to the Neuf Wifi registration page! So it seems, even though my network manager says I'm connected to my neighbor's wifi, I'm actually on Neuf. Weird, right?

I did some searches and found that quite a number of people in France have had problems with Ubuntu and the AliceBox (my neighbor's router), but after messing around a bit, I still haven't fixed anything. So I'm wondering: does anyone have any ideas about what's going on, or is there a way I can completely reset all my wireless settings? And why am I seeing Neuf everywhere?? :) Perhaps if this Neuf network were not intruding so much, I could still connect to my neighbor's wifi...

Thank you in advance.

---

### Post by iponeverything on 2008-10-15
> **floydian_slip said:**
> Hello all,

I'm currently in France and having weird problems with my wifi on Ubuntu (Hardy Heron). My roommate and I are sharing wifi with our neighbor, who gave us his password a couple days ago, She has a Mac and has been connecting fine from the start. I, on the other hand, had to try about 10 times before finally I connected. From that point on, all was fine...

...until yesterday. My wireless suddenly cut out, and I haven't been able to get online since. My roommate's Mac, however, still connects just fine. Now there are two problems: 1) obviously, not being able to re-connect to my neighbor's wifi no matter what I do. I see his wifi in my network list, with good strength, but it simply will not connect.

2) possibly more importantly, earlier today I clicked on a different wifi network--"Neuf Wifi"--which is a wifi service all throughout France for which you must pay. I connected just fine to that, although I cannot surf because I haven't paid--it simply brings me to the registration page. So I connected there just fine. BUT: since then, I've been able to "connect" every so often back to my neighbor's network, but when I try to surf, I get thrown back to the Neuf Wifi registration page! So it seems, even though my network manager says I'm connected to my neighbor's wifi, I'm actually on Neuf. Weird, right?

I did some searches and found that quite a number of people in France have had problems with Ubuntu and the AliceBox (my neighbor's router), but after messing around a bit, I still haven't fixed anything. So I'm wondering: does anyone have any ideas about what's going on, or is there a way I can completely reset all my wireless settings? And why am I seeing Neuf everywhere?? :) Perhaps if this Neuf network were not intruding so much, I could still connect to my neighbor's wifi...

Thank you in advance.

Network Manager stores the information it knows about wireless networks in Gnome Gconf.  Its a bit like the windows registry. You can edit it with a tool call gconf-editor -- run it as root with "gksu gconf-editor"

Once in the application look under "Apps -> System -> Networking"

From there you could delete the references to Neuf.

Another option might be to re-install Network Manager --

Or try the other application that so many people on this forum swear by ---

wicd

---

### Post by floydian_slip on 2008-10-16
Hi iponeverything, thanks for your response. I tried gconf but could not find Networking. Under "Apps" there is no "System" (or "Networking"), and under "System" (which is a separate folder in the same general folder as "Apps") there is no "Networking."

So what I did was completely remove the networking stuff, download the debs onto this computer and transfer manually onto my computer, and reinstall. See [here]("http://ubuntuforums.org/showthread.php?t=813941").

But I'm basically back where I was before. I can connect to Neuf Wifi--which does me no good--and when I try connecting to Alice (my neighbor's wifi), it seems I'm still connected to Neuf.

Perhaps it has something to do with DNS? Perhaps something is changed so that no matter which wifi I try to connect to, I always get thrown onto Neuf?

Or is there maybe a way I can connect to Alice manually, using the terminal, thus avoiding any network managers? If that's successful, it would prove that it's a problem with my network manager...

---

### Post by floydian_slip on 2008-10-16
**Update:** I brought by laptop to an internet cafe with free wifi and was able to connect successfully. So I suppose that localizes the problem a bit: it must have something to do with the AliceBox router. The odd thing is, again, that I was able to connect fine for an entire day until I was suddenly disconnected and could no longer reconnect. And again, my friend (whose computer I'm now using) has had no problems.

I did a search for wifi problems with AliceBox (all in French of course) and basically found this: [http://forum.ubuntu-fr.org/viewtopic.php?id=192437](http://forum.ubuntu-fr.org/viewtopic.php?id=192437). I tried all that (not really knowing exactly what it was supposed to do) but with no luck. Problem persists.

I can read French fine but can't really write it, so that's why I'm still asking here. Does anyone have any idea what all that code was supposed to do and why the problem is still here? Or any idea what else I should be doing? Thanks again. :)

---

