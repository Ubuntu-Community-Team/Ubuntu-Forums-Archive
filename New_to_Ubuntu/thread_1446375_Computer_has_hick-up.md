---
title: "Computer has hick-up"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by revlimit7000 on 2010-04-04
I don't understand it just decides hang and every thing lags I don't know its a fresh format on Great hardware. 2.4 duo 4gb ram fast as crap HD. Don't know where to start please help tell me where to start looking for the problem?

---

### Post by SnickerSnack on 2010-04-04
> **revlimit7000 said:**
> I don't understand it just decides hang and every thing lags I don't know its a fresh format on Great hardware. 2.4 duo 4gb ram fast as crap HD. Don't know where to start please help tell me where to start looking for the problem?

What version of ubuntu (8.10, 9.04, ...) do you have?

Have you looked at resource usage?  I don't know how to find the graphical resource monitor in kde, but you can run top from the terminal to see usage.  So,

1. open a terminal
2. run top, and leave it running
3. go about your normal usage
4. when it slows down again, consult the top readout to see if anything looks unusual

---

### Post by NightwishFan on 2010-04-04
As the above said, also what is the model of your graphics card?

---

### Post by bhmildy on 2010-04-04
Did you check the integrity of the file after you downloaded it?
> Before burning a CD, it is *highly recommended* that you verify  the md5 sum or sha256 sum (hash) of the .iso file. [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Read this too:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Me, I'd just try re-install with new cd from verified new download, rather than trying to solve a problem with a new install from dubious install media. Esp. if you have confidence in the hardware.

---

### Post by revlimit7000 on 2010-04-04
> **SnickerSnack said:**
> What version of ubuntu (8.10, 9.04, ...) do you have?

Have you looked at resource usage?  I don't know how to find the graphical resource monitor in kde, but you can run top from the terminal to see usage.  So,

1. open a terminal
2. run top, and leave it running
3. go about your normal usage
4. when it slows down again, consult the top readout to see if anything looks unusual

When i use the command top it returns this bit that bash /use/bin/top: input/output error

---

### Post by Sef on 2010-04-04
> Me, I'd just try re-install with new cd from verified new download,  rather than trying to solve a problem with a new install from dubious  install media. Esp. if you have confidence in the hardware.

+1. With this post: > When i use the command top it returns this bit that bash /use/bin/top:  input/output error 	, I suspect a bad install.

---

