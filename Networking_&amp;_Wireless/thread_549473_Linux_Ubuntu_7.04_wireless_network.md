---
title: "Linux Ubuntu 7.04 wireless network"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by Desireful on 2007-09-12
How do I set up and configure a netgear wireless card on a laptop hosting the Linux Ubuntu server edition 7.04? Thanks! :D

---

### Post by mojoman on 2007-09-13
> **Desireful said:**
> How do I set up and configure a netgear wireless card on a laptop hosting the Linux Ubuntu server edition 7.04? Thanks! :D

Well, how far have you gotten? Is the card in the laptop? Does it light up at all on startup? What type of netgear card? Do you know if it's supported or if other people had problems with it. You have to give more detailed information if people is to be able to help out.

If you can answer 'yes' to at least the second question I'd like you to post the output of the following two commands:
```

ifconfig
```
```
iwconfig
```

Do that for starter and we'll see what we have to work with.

/mojoman

---

### Post by Desireful on 2007-09-15
The card is in the laptop, it does light up on startup, I'm pretty sure it's supported. 
iwconfig:

lo - no wireless extensions. 
irda0 - no wireless extensions. 
wnaster0 IEEE 802.11g   Frequency:2.412 GHz
RTS thr:off     Fragment thr=2346 B

wlan0 IEEE 802.11g  ESSID:"--Blocked--"
          Mode: Managed  Frequency:2.412GHz  Access Point: Not-Associated
RTS thr:off    Fragment thr=2346 B
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid: 0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retrieves:0  Invalid misc:0   Missed beacon:0

if config has a lot more stuff, but a lot of it, actually all of it has something:0.

---

### Post by mojoman on 2007-09-16
Ok, I assume that you're running a wireless lan and that wlan is that device. If so, the OS is at least aware that the hardware is in place. Now, I've never configured one of those myself but I think I can contribute with a few tips and tricks.

Now, link quality and signal level show that you're not connected in any way and I must say that ESSID --Blocked-- and the access-point not-associated bugs me abit but let's start off with the network you're trying to connect to. Does it show up?

```
iwlist scan
```

If it shows up, fine, then the card is definitly up and running and we probably don't have a drivers issue. If not, we have to find out if the fault is on the sender or reciever side before moving on (unless you by any chance now for a fact that the network is up, e.g. through dualboot or another computer connected to it, in which ccase that's settled).

You could use the ifcommand to try to bring the card up as well, preferably together with whatever other information the network requires. My wireless pc-card, called ra0, is brought up by the following command
```

ifconfig ra0 up
iwconfig ra0 essid xxx channel x key xxx
```

(of course, I substitute the x part for my essid, channel and wep-key)

You could try that as well, using wlan0 instead of ra0. (I'm assuming that they are controlled in a similar fashion, but like I said, I have no experience with wireless lan.) In fact, if you don't get a signal with iwlist scan, try to bring the card up and then do another scan. 

Try this and get back.
/mojoman

---

### Post by kevdog on 2007-09-16
Lets see what kind of driver you have and chipset you have for the device.  You are going to have to post the following:

lshw -C network
lspci -nn

---

### Post by Desireful on 2007-09-16
Okay, I got it up and working. Now, I wanted to test to make sure I can change some of the servers site files. For example index.html. I found out how to access it and change it, but not how to save it. Can someone offer me some help on this? Also thanks for helping me on the other part. :D

Also, I get an "Operation not permitted" error when I type those codes in. Do I have to use Root?

---

### Post by mojoman on 2007-09-16
> **Desireful said:**
> Okay, I got it up and working. Now, I wanted to test to make sure I can change some of the servers site files. For example index.html. I found out how to access it and change it, but not how to save it. Can someone offer me some help on this? Also thanks for helping me on the other part. :D

Also, I get an "Operation not permitted" error when I type those codes in. Do I have to use Root?

I think that lshw requires root privileges but lspci doesn't.

How do you open the server files? When I muck around on my server I log in via ssh, open the files I want to edit with an editor (I prefer nano, it's a really good cli-editor) do my editing and then save the changes when I exit the editor. To open them with nano, just type 'nano filename' (with sudo if that is required).

/mojoman

---

### Post by Desireful on 2007-09-17
Oh my gosh! Thanks a lot! :D This can be closed.. if it's possible. :P

---

### Post by mojoman on 2007-09-18
Yup. Just click on 'thread tools' at the top of the post, there is an option called 'marked as solved'. Glad to hear that everything worked out for you.

Cheers
mojoman

---

