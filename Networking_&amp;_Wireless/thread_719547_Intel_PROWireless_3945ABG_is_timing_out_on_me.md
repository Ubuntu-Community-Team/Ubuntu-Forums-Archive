---
title: "Intel PRO/Wireless 3945ABG is timing out on me"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by MakLeod on 2008-03-09
The Intel PRO/Wireless 3945ABG chipset I am using works great under Gutsy in terms of connecting and overall use.  However, when I am downloading a large file that takes up to an hour to complete, the connection times out (and thus ceases to connect to anything) on me and I have to restart the computer.  It never times out from browsing the internet for hours or even leaving the computer on for days at a time.  Downloading a torrent file or grabbing something from another computer on my network will eventually time it out.

Anyone have any ideas as to what is going on here?  I've searched the forums and could not find any issues related to timing out, but I do seem to remember it being listed as a possible bug?  I am using the ipw3945 wireless driver.  Thanks in advance.

---

### Post by raul_ on 2008-03-09
Not really a fix, but I'm having no problems whatsoever with the new iwl3945 driver. Maybe you should give it a try

---

### Post by MakLeod on 2008-03-09
Hmm that could work.  How would I go about switching the drivers?

---

### Post by raul_ on 2008-03-09
I think this thread is about your problem

[http://ubuntuforums.org/showthread.php?t=686726]("http://ubuntuforums.org/showthread.php?t=686726")

---

### Post by sojusnik on 2008-05-04
This problem is still occuring under Hardy 64-Bit version.

My hardware: [http://www.box.net/shared/d0rfuonkck](http://www.box.net/shared/d0rfuonkck)
> Not really a fix, but I'm having no problems whatsoever with the new iwl3945 driver. Maybe you should give it a try 
How can I update my iwl3945 driver?

---

### Post by Zorael on 2008-05-04
> **sojusnik said:**
> How can I update my iwl3945 driver?

I didn't manage to get it to compile, spouted out errors about missing symbols in dmesg instead (mac80211 or ieee80211 modules didn't compile, I guess).

My problem was that the interface couldn't scan at all (and, by extension, couldn't connect to anything at all), which was solved by creating a file in /etc/modprobe.d/.

```
zorael@sunspire:~$ cat /etc/modprobe.d/iwl3945
[B]alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1 hwcrypto=1[/B]
```
(File content in bold)

---

