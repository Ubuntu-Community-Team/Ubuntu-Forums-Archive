---
title: "Problems with Agfa SnapScan 1212 scanner"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by guadaatenea on 2010-06-03
Hi everyone,

  I've drifted through help page after help page, and I still can't get my scanner to work. I bought this used scanner because it was the only thing listed among the supported scanners I could afford nowadays. I really need it, so it would be awful if I couldn't get it to work.

  General problem: XSane keeps giving me the "no devices available" error. (Just in case, I've double-checked that the scanner is on and properly connected).

  What I've done so far: I've copied the firmware file from the scanner's Windows CD and edited the snapscan.conf file. I'm not sure what I'm supposed to write in line 8, so after the change in line 5 didn't work out, I've given the general suggestion a try. so far, it looks like this:

```

# Change to the fully qualified filename of your firmware file, if
# firmware upload is needed by the scanner
firmware /myusername/SnapScan 1212P_2.bin

# If not automatically found you may manually specify a device name.
/dev/sg0

```

Well, what else can I try?

Thanks!

---

### Post by bumanie on 2010-06-03
This [page may]("http://snapscan.sourceforge.net/") help - not sure, but have a look.

---

### Post by guadaatenea on 2010-06-03
I've been there and downloaded a backend file, but since I don't know what a backend is I'm not very sure whether I downloaded the right one nor how to use it (newbie ignorance)

---

