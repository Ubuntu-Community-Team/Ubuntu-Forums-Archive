---
title: "Can't upload files above about 1 MB using Firefox or Chrome"
date: 2013-11-28
forum: Networking &amp; Wireless
---

### Post by Peter_Heft on 2013-11-28
SOLVED!!!!My slow upload connection needed a smaller buffer size. I'm going to see if I can get a better handle on this with Wireshark, probably should have started there but didn't know it existed. See details below.  Using Frontier's cheap DSL download about 100KiB/s up max of 30KiB/s according to Network Monitor.  Trying to upload 2.2 MB file to dropbox.  Network Monitor shows uploading for at most 50 seconds then stops will retry for short bursts until message that server reset.  Have same problem with Thunderbird at about same file size, message is that server times out.  I have logged both Thunderbird and Firefox and today used Web Monitor which shows a lot of subscribe (requests?).  I will attach a log and jpg of Web Monitor in next post, lost the whole thing last try. Thanks for the help.

---

### Post by Peter_Heft on 2013-11-28
Attachments for above. Couldn't upload the png file of 800 some KB either so I'll try it as a jpg of 410, that worked.  The 13.1 MB log is going to have to go from XP. Doesn't that exceed the size limit?  I'll wait 'till I hopefully hear something from someone. Maybe I should log uploading to the forum.

---

### Post by Peter_Heft on 2013-12-01
Thunderbird has same problem. Tried using Filelink with Ubuntu One, didn't work either.  Wondershaper no help.

---

### Post by Peter_Heft on 2013-12-02
Looking long enough some of the things I was seeing started to make sense and fit together. One of the items that fit was about excessive buffer size causing packet loss. The most help came from [http://ubuntuforums.org/showthread.php?t=872346](http://ubuntuforums.org/showthread.php?t=872346). I slowly worked my way through it and the following statement fit together with the ecxessive buffer size. "The values in net.ipv4.tcp_wmem should be the same as net.ipv4.tcp_rmem since both sending and receiving use the same internet connection." That was definitely not true in my case. wmem is for outgoing and rmem is for incoming and is Linux version of buffer. The values being used, based purely on memory available were "net.ipv4.tcp_wmem = 4096 16384 779744". I calculated what they should be for my isp and put in 4096 4096 15000, and it worked. The server stayed hooked up even though it took 4 minutes to upload the 3.2 MB file. I repeated it 5 times to make sure, all with Thunderbird. For some reason I have less trouble with gmail's smtp than frontier's.  I am hoping it also works for Firefox.  It doesn't seem to, still having problems uploading to dropbox.  It still needs some tweaking to get the speed closer to the advertised.  I'm going to see if I can get a better handle on this with Wireshark, probably should have started there but didn't know it existed.  Wireshark did confirm the packet losses, but I haven't dug much further.  This old clunker just needs to be replaced.  I could use some help interpreting some lines in the log. My interpretation involved packet loss, but I was guessing.    nsSocketOutputStream::Write [this=a4a4c068 count=32768] calling PR_Write [count=32768] PR_Write returned [n=1440]  What do those statements mean?

---

