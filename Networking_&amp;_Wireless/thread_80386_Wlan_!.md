---
title: "Wlan ?!"
date: 2005-10-22
forum: Networking &amp; Wireless
---

### Post by mots on 2005-10-22
I went to the internet with WLAN and everything worked fine till I restarted my computer some days ago. Now I don' get into the web and my WLAN device doesn't appear in the "Network devices" window anymore. 

Any suggestions?

---

### Post by zugvogel on 2005-10-22
Hi Mots,

What type of wireless card is it?
What did you do to get the wireless card working before? Was it just plug and play?
Can you post the output of the following command in the terminal*:
```
ifconfig
```

so we can double-check and see if it's picked up that you have a wireless card, or not.


* The terminal can be found at Applications > System tools > Terminal

---

### Post by mots on 2005-10-22
OK, im not that dumb (I know where the terminal is)
To make my wireless card work, I only configured it in the "Network Devices"-window and it worked.
if config says:

> mots@Nonsense:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


---

### Post by zugvogel on 2005-10-24
ok, I think you might need to "modprobe" something to get your computer to pick up the card - usually it does it automatically when the card is inserted but for some reason it's not doing that.

What you need to modprobe probably depends on what card you have. I'm not entirely sure how to go from here, but maybe if you search the internet / forums for your card name and the term "modprobe", you might find something of use. Or maybe someone else can help... That's what I had to do with ndiswrapper anyway.

And I didn't mean to imply that you were dumb, but since it was your first post and you gave no technical details, I gathered you were new to this, and I should play it safe, to avoid unnecessary questions. Surely that's the best thing to do?

---

### Post by az on 2005-10-24
Please look in the devce manager for the name of your card (or other wireless device)

---

