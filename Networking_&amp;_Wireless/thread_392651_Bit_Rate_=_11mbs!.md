---
title: "Bit Rate = 11mbs?!"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by .oops on 2007-03-24
When I type **iwconfig** I get this output:

```
RT61 Wireless  ESSID:"Wireless-G"
          Mode:Ad-Hoc  Frequency:2.462 GHz  Cell: 0A:D2:DD:6B:69:D1
          **Bit Rate=11 Mb/s**
          RTS thr:off   Fragment thr:off
          Link Quality=80/100  Signal level:-53 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Those 11mb/s are the reason my connection is so slow. How can I increase them? I'm using GTKWiFi. How can can I change settings like RTS and Fragment Threshold?

---

### Post by dawv on 2007-03-24
you cant make it higher unless you buy a new router or gateway or whatever your doing...

You are using a B... G or N is recommended if you want it higher... 11 mbs is good though... so dont worry about it..

---

### Post by chili555 on 2007-03-24
Try sudo iwconfig <your_wireless_interface> rate auto. Your card and router will go as fast as they can safely do, depending on wireless reception conditions and, I guess sun spots. Also, I notice your mode is ad-hoc. That's usually used for connections computet-to-computer, not computer-to-router. Unless this is a special situation, you might also sudo iwconfig <your_wireless_interface> mode managed.

---

### Post by insane_alien on 2007-03-25
could be a computer-router-computer connection. any way, does the router support g? just cos you have a g card doesn't mean that you'll get the full 54Mbps everywhere. i'm on a g card and router just now but i'm only getting a measly 1 Mbps . thats due to distance though. and for the internetits fine because its only a 256 kbps connection any way.

---

### Post by .oops on 2007-03-25
Well on Windows I get 54Mb/s all the time, so I should get them in Ubuntu too. I tried **iwconfig ra0 rate auto** and this was what I got.

```
oops@desktop:~$ iwconfig ra0 rate auto
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device ra0 ; Operation not permitted.
oops@desktop:~$ sudo iwconfig ra0 rate auto
Password:
oops@desktop:~$ sudo iwconfig ra0 rate auto
oops@desktop:~$ iwconfig
lo        no wireless extensions.

ra0       RT61 Wireless  ESSID:"Wireless-G"
          Mode:Ad-Hoc  Frequency:2.462 GHz  Cell: 0A:D2:DD:6B:69:D1
          Bit Rate=11 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=81/100  Signal level:-57 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

oops@desktop:~$
```

Apparently it did nothing. I then tried **rts**.

```
oops@desktop:~$ sudo iwconfig ra0 rts auto
Error for wireless request "Set RTS Threshold" (8B22) :
    SET failed on device ra0 ; Invalid argument.
oops@desktop:~$ sudo su
root@desktop:/home/oops# iwconfig ra0 rts auto
Error for wireless request "Set RTS Threshold" (8B22) :
    SET failed on device ra0 ; Invalid argument.
root@desktop:/home/oops#

```

I believe if I changed those settings I'd get a better bit rate. I'm on a computer-router-computer connection. Would Infra or Managed be better?

---

### Post by Kobalt on 2007-03-25
What's your card brand/model ? 
I have a broadcom 4311 and using the bcm43xx drivers I also was stuck at 11mb/s. Now I use win drivers+ndiswrapper and I have a 54mb/s...

---

### Post by .oops on 2007-03-25
I have a CNet CWP-854 PCI. I'm using GTKWiFi. Isn't ndiswrapper used only when you can't find ra0 (in my case) in the network manager?

---

### Post by Kobalt on 2007-03-25
It's used if you don't have opensource or don't find suitable opensource drivers.
You shouldn't need this with your Ralink chipset based card then... the problem comes from somewhere else.

---

### Post by .oops on 2007-03-25
Bummer. :( Thanks Kobalt. 
Does anyone have any ideas?

---

### Post by chili555 on 2007-03-25
A couple of other things you might try:```
sudo iwconfig ra0 mode Managed
sudo iwconfig ra0 rate 54M auto
```This next command won't work if you are associated with the router, so we will bring ra0 down first:```
sudo ifdown ra0 
sudo iwpriv ra0 network_type g
sudo dhclient ra0
```Not all cards can do all things, so success is not guaranteed on your Ralink.

---

### Post by .oops on 2007-03-25
```
sudo iwconfig ra0 rate 54M auto
```

It worked like a charm apparently. :D Thank you very much.

```
oops@desktop:~$ iwconfig
lo        no wireless extensions.

ra0       RT61 Wireless  ESSID:"Wireless-G"
          Mode:Ad-Hoc  Frequency:2.462 GHz  Cell: 02:EB:4A:E6:D9:CD
          Bit Rate=54 Mb/s
          RTS thr=2346 B   Fragment thr=2344 B
          Link Quality=74/100  Signal level:-69 dBm  Noise level:-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

oops@desktop:~$

```

---

### Post by chili555 on 2007-03-25
If your desktop connects to a router wirelessly, and the router also is connected to other computers forming a network, as well as connecting to the outside world for internet connectivity, then I recommend your mode be Managed, and not Ad-Hoc.

---

### Post by .oops on 2007-03-25
I would use:

```
sudo iwconfig ra0 mode Managed
```

Do I have to make changes in the router configuration itself?

---

### Post by chili555 on 2007-03-25
No changes to router, in my opinion, without seeing what its configuration pages look like or even knowing the brand!

Your command is correct.

FWIW, unless you have a T3 line at your router, I doubt you will see any difference between 11 Mbps and 54 Mbps, as few ISP's are delivering data in excess of 11 mbps. If, however, you are streaming video from your media server to your HTPC, 11 Mbps probably won't be fast enough.

---

### Post by .oops on 2007-03-25
That command doesn't work. Strange. However, I have 54mb/s now and I'm downloading at the same speed I was downloading in Windows (~200kb/s). I do notice a huge difference from 11 to 54, especially when downloading packages. I'm no longer using GTKWifi, I removed it and now I'm just configuring through iwconfig. Thanks chilli555, you were very helpfull. :)

---

