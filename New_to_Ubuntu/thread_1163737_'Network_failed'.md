---
title: "'Network failed'"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by sarum on 2009-05-19
Hi,whenever I turn off my computer a paragraph of writing flashes by - too quick for me to read - but mentions something about network failure. But nothing is wrong with Xubuntu, I can get on the internet and all else seems fine. Except; when I want to use Puppy4.1.1. I've used this same CD on this computer for over a year. I've a pup-save file of 1GB on the HD. Puppy works alright but suddenly no internet. Eth0 is recognised, monitor icon is in the tray but no connection. I have moved the computer recently and am using another monitor. This might seem like a puppy question, but the above mentioned paragraph makes me think that perhaps that is the fault.
My thanks to those who are kind enough to assist............sarum

---

### Post by superprash2003 on 2009-05-19
post an output of ifconfig from the puppy OS

---

### Post by sarum on 2009-05-19
Thanks for your reply ifconfig results:-
# ifconfig
lo	Link encap:Local Loopback
	inet addr:127.9.9.1 Mask 255.0.0.0
	UP LOOPBACK RUNNING MTU:16436 Metric:1
	RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:0
	RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

#
I hope this helps. Also do you know of a way of copying the printout of the consol in Puppy. I had to type this into Abiword.
Thanks again, I enjoyed your tutorial link..............sarum

---

### Post by JKyleOKC on 2009-05-19
I suspect that the paragraph that flashes past too rapidly for you to read is actually four messages indicating that Network Manager failed to respond to a message sent it ordering it to disconnect. At least that's what I see on this system whenever it's re-booting, just before the shutdown for the reboot.

If that's what it is, there's no connection between it and your Puppy problem. Apparently the system sends two sets of disconnect messages to Network Manager; the first one shuts it down, so the second one creates these error messages. It's a side effect of a changeover in system operation that started in the 7.10 version and has gotten a little more complete with each subsequent release; the change has created a few "race conditions" in which superfluous messages get sent to various modules, causing a bit of confusion to those of us who see the warnings -- but since they don't cause any real problem, they have very low priority for getting fixed!

---

### Post by superprash2003 on 2009-05-20
well puppy doesnt seem to have recognized your LAN card , cause your ifconfig output has only loopback and nothing else.. you can save the output of ifconfig to a file by typing **ifconfig > output.txt**

---

### Post by sarum on 2009-05-21
Thankyou for your replies JKyle you're right there are four messages. And thanks again Superprash for your help. Changes I recently made to the computer came about because I could only get 800x600 resolution(seems a common problem) and there seem to be more and more problems with recent releases. Maybe Ubuntu would do well to postpone the 6 monthly upgrade and catch up a bit. Puppy's lack of 'net is no big deal as I have another computer, but it'd be nice to have things working like they did with 6.06 and 7.10.
Thanks for your help.............sarum.

---

