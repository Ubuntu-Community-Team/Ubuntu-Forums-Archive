---
title: "Problem with web provider"
date: 2017-02-08
forum: Networking &amp; Wireless
---

### Post by yokelns on 2017-02-08
Hi,

I have signed a 2 year contract with wi-fi web provider but internet goes out on daily basis during afternoon when their usage peaks. They always dis me with "check your router" story. 
I have since talked with others that use their services and the situation is more or less the same. 

Is there a way to monitor network connection so to prove that problem is coming from them so I could have some proof of this ill doing? Threat with court?

---

### Post by Bucky Ball on 2017-02-08
Check your router, as in keep an eye on the network light on the router. ;) Identify which light indicates you are connected to the internet and online. If your internet is dropping out often, then if the one goes out you have a faulty router or they are dropping you offline somewhere along the line at their end. 

Take a video of the router light going out if that's what it is doing but this is a support forum for Ubuntu rather than for legal advice. :)

---

### Post by geeksmith on 2017-02-08
You could also run two continuous pings: one to the router's internal interface and one to a system on the Internet. If your pings start dropping to the Internet, but work to the router's interface, then you can show them that the router is up but the upstream path is down.

---

### Post by yokelns on 2017-02-09
Hey guys, thanks for advice. It turns out that the main reason why wi-fi breaks of is because there is a lot of wi-fis in the building and hence a lot of overlapping and sharing of the same wi-fi channels which causes signal to go down. Once I connected via network cable to the router all of the problems went away :)
However, now I am confronted with another issue. Since most, if not all, of the routers in the building are 2.4GHz I got the idea of maybe purchasing a 5GHz router which would make me sole user of that end of the spectrum.
Will this purchase be enough or do the devices that connect to wi-fi (laptops, phones...) have to actually support 5GHz wireless?

---

### Post by yokelns on 2017-02-09
> **geeksmith said:**
> You could also run two continuous pings: one to the router's internal interface and one to a system on the Internet. If your pings start dropping to the Internet, but work to the router's interface, then you can show them that the router is up but the upstream path is down.

Hey geeksmith,how do you ping router?I know that ping command pings websites but I have no idea how to ping router...

---

### Post by yokelns on 2017-02-09
> **Bucky Ball said:**
> Check your router, as in keep an eye on the network light on the router. ;) Identify which light indicates you are connected to the internet and online. If your internet is dropping out often, then if the one goes out you have a faulty router or they are dropping you offline somewhere along the line at their end.

Oh yeah ,totally forgot about the lights! Thanks for the advice Bucky Ball! :)

---

### Post by chili555 on 2017-02-09
> do the devices that connect to wi-fi (laptops, phones...) have to actually support 5GHz wireless?They certainly do.

Check yours from the terminal:```
sudo iwlist chan
```Here is a snip of the result from my machine:```
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
          Current Frequency:5.745 GHz (Channel 149)

```

---

### Post by Bucky Ball on 2017-02-09
For what it's worth, channels 1, 6 and 11 don't overlap with any of the other actual *channels* so best to go for one of them, but that doesn't tell you how congested each channel is. Do a hunt and you should be able to find a terminal command that shows how many are using what channel. Choose the channel that is least congested (you will be setting the channel on the router, not the computer). I used such a command I found online the other day as I was having a few issues myself.

---

### Post by yokelns on 2017-02-10
Thanks for the awesome replies guys! This was very helpful :)

---

