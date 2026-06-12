---
title: "understanding internet speeds"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by hellomoto on 2010-04-01
So i have hopfully a simple question.

When I down load something (for example a podcast, an ubuntu iso) from what i think are local servers, I get an avaerage download speed of about 
60 KiB/s.

However when I go to a website and test my internet speed, it shows up at 480 Kbps

There is no one else on our network when I download.

Is this something to do with bandwidth and what is that anyway?!

thanks!

---

### Post by cascade9 on 2010-04-01
Because your 'download speed' is in 'bytes' (kB) and your speed tester, like ISPs, uses 'bits'. 

8bits to the byte...so 480kbit = 60kB

---

### Post by MAMIDIPALLI on 2010-04-01
simple 8 bits =1 byte
60KB/s=480Kb/s.........;)

---

### Post by QIII on 2010-04-01
There is also some overhead, so what you are seeing is a little skewed.

Some testers account for that overhead, some don't.

All things being equal, one might be slightly less than another if it shaves off the overhead in its calculation.

---

### Post by undecim on 2010-04-01
Internet speed capacity is measure in bits/second or bps (i.e. the number of 1s and 0s you can get in a second)

But when you download stuff, you see Bytes/second (i.e. number of sets of 8 1s and 0s, such as 00101100 that you get in a second)

The lowercase b means bits. Uppercase means Bytes. 8 bits is the same as 1 Byte. So take your internet speed - 480kbps and divide by 8

480/8=60

60kB/s

And this problem is compounded even further you start to talk about kB (1000 bytes) vs kiB (1024 bytes)

---

### Post by hellomoto on 2010-04-01
ahh brilliant thankyou everyone. I guess i need to read up on my units of measurement more!

---

### Post by lisati on 2010-04-01
Don't forget that internet traffic (not just on your home network) can sometimes confound measurement as well.

---

