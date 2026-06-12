---
title: "[SOLVED] Bad problem with network, posibly a virus or worse"
date: 2008-10-12
forum: Networking &amp; Wireless
---

### Post by alejo0823 on 2008-10-12
Hi
Today my internet stopped working, when i open the system monitor it shows that is sending at a speed of 190 KB/s but I only have a 2MB connection and its only capable of sending 55 KB/s, so I boot into windows and find my internet working ok.
what could it be and how can I fix it?
I did a ping as instructed in the help page and I get results from 20% to 60%, and the cpu seems to be all over the place.
if I disable the connection the speed drops to 0 as it should and the modem's lights stop blinking, but when I enable it it jumps at 200MB.
Here is a picture of the monitor just if anyone sees something I don't.

---

### Post by iponeverything on 2008-10-12
First off what distro/version are you running.

Second, its very unlikely that you have a virus, considering that there are no known linux viruses in the wild. 
To see what process it is do a:

lsof |grep -i tcp

or you can watch the traffic with tcpdump.

---

### Post by alejo0823 on 2008-10-12
I'm using ubuntu 8.10 updated til yesterday, lsof |grep -i tcp only shows 1 process listening and a warning that the information may be incomplete, the tcpdump command did nothing.

---

### Post by iponeverything on 2008-10-12
Tell tcpdump to listen on a specific interface:

sudo tcpdump -n  -i eth0

where "eth0" is your network interface.

also run:

sudo ps auxwww > /tmp/outfile
sudo netstat -n >> /tmp/outfile
sudo lsof >> /tmp/outfile

and upload /tmp/outfile with your next post and I'll take a look at it.

---

### Post by lswb on 2008-10-12
Have you by some chance recently run some p2p (torrent) software?

---

### Post by iponeverything on 2008-10-12
> **lswb said:**
> Have you by some chance recently run some p2p (torrent) software?

This just came to mind with me as well.. It could be running in the background.

---

### Post by alejo0823 on 2008-10-12
No just transmision the ubuntu install is recent and that would not explain the supernatural speed.

---

### Post by iponeverything on 2008-10-12
the screen cap does not show the interface. For all we know it could be the loopback. Without more information, all your going to get is pure speculation.

do a "killall -v -9 transmision"

---

### Post by alejo0823 on 2008-10-12
what is a loopback?
from what I understand its like a local network in the machine, but if that was the case it would not go to 0 KB when I disable the eth.

---

### Post by alejo0823 on 2008-10-12
"killall -v -9 transmision"  didn't find any process.

---

### Post by iponeverything on 2008-10-12
> **alejo0823 said:**
> "killall -v -9 transmision"  didn't find any process.

Once again. Post the output of the commands requested above - Or no one without physic abilities is going to be able to tell you what is going on.

---

### Post by alejo0823 on 2008-10-12
here are the outputs
lsof |grep -i tcp
> lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/alejo/.gvfs

      Output information may be incomplete.

cupsd     4935       root    2u     IPv4      15160                 TCP localhost:ipp (LISTEN)

tcpdump
> tcpdump: no suitable device found

killall -v -9 transmission
> transmission: ningún proceso eliminado

BTW thanks for helping

---

### Post by iponeverything on 2008-10-12
:) ok -- run the commands below. They will provide a lot of information to work from.  you can upload the file "/tmp/outfile" from the "Additional Options" Section of the screen where your responding to this post.

The "Reply to Thread" screen.

```

sudo ps auxwww > /tmp/outfile
sudo netstat -n >> /tmp/outfile
sudo lsof >> /tmp/outfile

```

and upload /tmp/outfile with your next post and I'll take a look at it.

---

### Post by alejo0823 on 2008-10-12
ok I made a mess with that file I hope it gets ok

---

### Post by iponeverything on 2008-10-12
```
pulseaudi 5718      alejo   30u     IPv4      17608                 UDP cable201-233-73-51.epm.net.co:55656->224.0.0.56:46890 
pulseaudi 5718      alejo   31u     IPv4      17609                 UDP cable201-233-73-51.epm.net.co:47781->224.0.0.56:9875 

```

Are you streaming audio?

---

### Post by alejo0823 on 2008-10-12
ohh I now know the problem thanks a lot for your help, I installed this pulse audio program hoping it wold copy the sound output to the input jack.

---

### Post by Genixoid on 2011-11-06
> **alejo0823 said:**
> ohh I now know the problem thanks a lot for your help, I installed this pulse audio program hoping it wold copy the sound output to the input jack.

what it was a program? ;)
It looks like I have the same problem

---

### Post by robert shearer on 2011-11-06
> what it was a program?
It looks like I have the same problem 

Even if you do posting in a 3 year old thread will not help you.
You should start a **new** thread and outline  the problem and your hardware and Ubuntu version.

This will get you many more viewers and helpers than you will get in **this old thread**.

This link may be of use...
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

