---
title: "Dell Inspiron Connected to router, no internet"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by dasajed on 2008-11-27
I'm home for thanksgiving at my uncle's house. My ubuntu has NEVER had any issues with routers before. My uncle is running a linksys router which is (now) set to factory defaults. The internet work perfectly on his laptop. On mine, I connect to the network, and can connect to the router 192.168.1.1, but I get no internet. 

I haven't mucked around with my ubunto wireless configuration, so that should all be pretty default.

---

### Post by Bucky Ball on 2008-11-27
Try:

sudo /etc/init.d/networking restart

in a terminal. Let us know. You have the correct ESSID and security details in System->Administration->Network?

In there, make sure 'Enable Roaming' is unticked (for now), 'Configuration' is set to 'Automatic Configuration (DHCP)' and post the result of

iwconfig

... please.

---

### Post by dasajed on 2008-11-27
Oh, I'm running moblock, but I believe that I disabled it by running kill with the process id. 

Also, my uncle seems to think that there's a firewall issue, but I don't believe that I have a firewall... unless ubuntu comes default with one up.

---

### Post by dasajed on 2008-11-27
I did the restart.

I unticked roaming, and changed to dhcp. The essid field had a drop down menu for less than a second, and then it disappeared, and wouldn't return. I just typed in linksys (because that's the network name). Is this correct? Also, it's not a secure network, so I don't know if if matters what I put for password type. After this, I could no longer connect to the router via 192...

for iwconfig
i will paraphrase to the best of my ability.

lo - no wireless ext
eth0 - no w e
wmaster0 - no w e

wlan0 
IEEE 802.11g essid:"" nickname:""
mode:managed frequency:2.437 GHz Access Point : 00:14:BF...
Bet Rate 11 MB/s tx-power=27 dBm
Retry min limit:7 RTS thr:off Fragment thr:2346 B
Power Management: off
link quality=79/100 signal level=-55dBm Noise:.93
Rx invalid weid:0 Rx invalid crypt:0 Rxinvalid fra 0
tx excessive retries 0 invalid misc 0 missed beacon 0

---

### Post by dasajed on 2008-11-27
I ticked enable roaming, and reconnected, and the only thing that changed in iwconfig:

essid="linksys"

bit rate = 54 Mb/s

---

### Post by dasajed on 2008-11-27
...thanks.

---

### Post by Bucky Ball on 2008-11-27
You're welcome. Is that working now? Did you figure it out or still having problems?

essid="linksys"

That part appears to be correct now.

---

### Post by dasajed on 2008-11-27
no, it's still not working. I was just thanking for the help.

---

### Post by rlzyoner on 2008-11-27
What are the results of a trace router to a webpage, take google for instance.
Also, one thing that I needed to do with some hardwired connections, was manually enter the dns server addys and assign a static ip, as opposed to dhcp.
Its been a while since i've used a linksys router, but go to the configuration webpage interface and check that its own firewall is not acting up.

---

### Post by jre on 2008-11-27
> **dasajed said:**
> Oh, I'm running moblock, but I believe that I disabled it by running kill with the process id. 

Also, my uncle seems to think that there's a firewall issue, but I don't believe that I have a firewall... unless ubuntu comes default with one up.
moblock uses the Linux firewall (iptables). If you simply kill moblock its iptables rules are still there (and all traffic sent to moblock (NFQUEUE) just gets dropped because it doesn't get processed). "moblock-control stop" is the correct solution instead.

There are several options to allow traffic to the router.

---

### Post by dasajed on 2008-11-29
It was in fact the moblock. The command you gave me fixed it.

Wonderful! I am now ecstatic. Thank you everyone for your help.

---

### Post by Dareajoe on 2008-11-29
I have an old dell inspiron, and it looks bulky. like the icons toolbar and what not. and i just got this new computer and on this one i went to desktop properties and then to settings and i could change the SCREEN RESOLUTION and that makes everything smaller or bigger (to your pereference) but i cant for some reason on my old inspiron? how can i change it?!?!?

---

### Post by Bucky Ball on 2008-11-29
> **Dareajoe said:**
> I have an old dell inspiron, and it looks bulky. like the icons toolbar and what not. and i just got this new computer and on this one i went to desktop properties and then to settings and i could change the SCREEN RESOLUTION and that makes everything smaller or bigger (to your pereference) but i cant for some reason on my old inspiron? how can i change it?!?!?

Start a new thread with a descriptive title  in the appropriate forum (this is Networking and Wireless) and you will get more help. No one will find your problem here.

---

