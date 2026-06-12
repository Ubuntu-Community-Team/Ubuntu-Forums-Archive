---
title: "Cannot detect/connect to 5GHz band after dual boot"
date: 2019-03-04
forum: Networking &amp; Wireless
---

### Post by ragnarokv on 2019-03-04
Hi,

I'm very new to Ubuntu 18.04 (just dual-booted it on a Mac Pro 2015). Everything went smoothly, but now I'm not able to see my 5G band on the laptop. I can still see and use it when I boot into macOS. Also, the 2.4G band seems very unstable and keeps getting disconnected (the router is placed in another room, and it appears my connection is stable if I'm near it, but I never had this issue while on my macOS. It always gave me a stable connection even if I was in the other end of the house).

I did just quick searches, and then did *sudo iwlist scan*. It showed 32 channels, half of them 2.4G and half of them 5G, but only my 2.4G band was there. I couldn't find my 5G band.

*iwlist channel* gives the following: 
```
wlp3s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 144 : 5.72 GHz
          Current Frequency:2.437 GHz (Channel 6)

lo        no frequency information.
```

None of the 5G channels are mine.
Sorry if this is a silly question, but I have no clue what to do, and would appreciate any help!

---

### Post by him610 on 2019-03-05
You need to be connected to the 5G channel for it to show as Current Frequency.
This shows the 2.4G listing while connected to 2.4G source followed by the 5G listing while connected to 5G on same router 
```
$ iwlist wlp4s0 chan
wlp4s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 144 : 5.72 GHz
          Channel 149 : 5.745 GHz
          Current Frequency:2.462 GHz (Channel 11)

$ iwlist wlp4s0 chan
wlp4s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 144 : 5.72 GHz
          Channel 149 : 5.745 GHz
          Current Frequency:5.22 GHz (Channel 44)


```

---

### Post by ragnarokv on 2019-03-06
Thanks for your reply,

That's my problem though, I don't see the 5G channel at all when I go to 'Select Network'. I can see other 5G channels (neighbours'), but not mine. I can see and connect to our university's 5G channel though.

---

### Post by jeremy31 on 2019-03-06
Moved to networking
I would check ```
iw reg list
```
See if it matches your country code, there is a list at [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)
If you live in Iceland you would set the country code with ```
sudo iw reg set IS
```
Replace IS with your country code

---

### Post by ragnarokv on 2019-03-08
It matched my country code, no issues with that.

It seems that I can't connect only to my home network's 5G channel. I can connect to my friend's 5G network though. I'm thinking there's some issue with the router, but I'm not sure how to fix this.

Thanks for your help!

---

### Post by him610 on 2019-03-08
Recommend you refer to this permanent post, [https://ubuntuforums.org/showthread.php?t=370108]("https://ubuntuforums.org/showthread.php?t=370108")
Do what is necessary to download and install the wireless info script, run it, and post the results.

---

### Post by jeremy31 on 2019-03-09
Is the 5GHz channel the router is on, match one from the list ```
iwlist chan
```

---

