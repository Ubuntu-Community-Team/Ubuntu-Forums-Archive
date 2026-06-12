---
title: "connection problem on my router but not on public hotspots"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by jakethesnake on 2006-11-10
Well I seem to be able to connect to the wireless system at the university just fine, but connecting to my wireless network at home is another matter? 

Can anyone shed some light on this for me. Hopefully it's something simple. 

FYI I have configured my network settings with the proper essid and my wep key.

Also if I disable my protection on my network ubuntu runs perfectly fine.

---

### Post by FrodoB on 2006-11-10
"Also if I disable my protection on my network ubuntu runs perfectly fine."

I take it that this means that your wireless works without WEP?

---

### Post by jakethesnake on 2006-11-10
No I am running WEP encryption.

---

### Post by FrodoB on 2006-11-10
What are you trying to convey with your statement?

"Also if I disable my protection on my network ubuntu runs perfectly fine."

Disable what protection, and exactly what happens?

---

### Post by FrodoB on 2006-11-10
At any rate, just remove WEP temporarily on your home setup and see if it works without it. If it does, then put the Key backup using Hex numbers on both sides.

---

### Post by jakethesnake on 2006-11-10
OH, I misunderstood. With the WEP disabled I can start up firefox and go, I do obviously have to pick my network (essid) from the network menu. But other than that it runs fine.

---

### Post by FrodoB on 2006-11-10
Then it is likely that re-entering the WEP key as hex numbers on both the access point and the Ubuntu computer will fix it.  Some access points and wireless devices have issues with anything but hex numbers.

A good WEP Key generator/translator is at:

[http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)

Best of luck, sounds like you are close.

---

### Post by jakethesnake on 2006-11-10
.

---

### Post by jakethesnake on 2006-11-10
> **FrodoB said:**
> Then it is likely that re-entering the WEP key as hex numbers on both the access point and the Ubuntu computer will fix it.  Some access points and wireless devices have issues with anything but hex numbers.

A good WEP Key generator/translator is at:

[http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)

Best of luck, sounds like you are close.

OK, I gotcha. This link you provided though if my passphrase is the same the key should work reguardless right?
my links router generated 4 wep keys for me I was under the impression that I had to use one of those keys?
thanks for your help by the way!

---

### Post by FrodoB on 2006-11-10
Well, I can't say, but usually you can just enter any valid keys that you want to.  If the keys are in HEX format already maybe you could just cut and paste them into Ubuntu and that might work.

On the other hand, sometimes the router is converting these things or sometimes it insists on using a unique way of displaying them.

See how it goes.

---

### Post by jakethesnake on 2006-11-10
I'm playing with it right now, hopefully I'll get it running today. It's been a long road trying to get my wireless connection up and running. Hopefully I'm at the finish line.

---

### Post by FrodoB on 2006-11-10
Yes it can be a true pain. Some manufacturer should take advantage of this and provide good Linux kernel modules at fair price and advertise the fact. A lot of us would buy and recommend their products. I am hopeful that Ralink and Atheros/Zydas are those companies.

It seems like that whenever a good card comes available that the manufacturer changes chipsets quickly out from under us. I have some good devices that work on my Linux systems, but 75% of them are no longer available on the open market. Very sad.

---

