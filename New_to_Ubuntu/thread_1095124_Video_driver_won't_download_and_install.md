---
title: "Video driver won't download and install"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-13
Hi,
I've installed Ubuntu on some other machines.

When it says it has video drivers for me to install, in the list it says the driver name and [Recommended]

so I choose it and click on activate, a box comes up saying "Downloading drivers" or something, then after a few seconds it just disappears and nothing has installed. The computers are connected to the net.

Is this a bug? why does it just disappear?

---

### Post by taurus on 2009-03-13
Was it really disappeared or was it working (downloading and installing) in the background?  When you clicked to install a driver for your graphic card, did you have update manager, add/remove, or synaptic open?

---

### Post by avtolle on 2009-03-13
I've had the same problem as the OP; it seems that if I try it again, and again sometimes, eventually it downloads and installs.

---

### Post by Gp. on 2009-03-13
> **taurus said:**
> Was it really disappeared or was it working (downloading and installing) in the background?  When you clicked to install a driver for your graphic card, did you have update manager, add/remove, or synaptic open?

It really disappears.

The box comes up for a few seconds, then dismisses.

No other package managers open. :S

---

### Post by avtolle on 2009-03-13
> **Gp. said:**
> It really disappears.

The box comes up for a few seconds, then dismisses.

No other package managers open. :S
I can confirm that it just disappears. This has happened to me on multiple occasions. However, eventually I was able to get it installed.

I did notice that while I had the problem on a wired connection once or twice, trying to use a wireless internet connection seemed to always fail the first time (and sometimes more than one subsequent time), so if you are trying this wirelessly, may I suggest getting the cable out and plugging in directly to see if this gets you past the problem.

---

### Post by avtolle on 2009-03-13
FWIW, the reason I have encountered this as often as I have is the installation of 8.10 and Linux Mint 6 (in various releases, 32-bit; 64-bit; XFCE "edition") on separate occasions on my computer and a few others. Again, I've been able to get the driver installed eventually, after many attempts in one case; but it did take more than one attempt, and in the multiple attempt case, more than one day.

---

### Post by bailbath on 2009-03-13
Without hardware details we can't help
Ian

---

### Post by avtolle on 2009-03-13
> **bailbath said:**
> Without hardware details we can't help
Ian
Cannot speak for anyone else; in the cases I've cited, nvidia card (sorry, don't recall the model right now, and not around that computer to check), "activating" the 177 driver. Again, I've been able to get the driver downloaded and installed, just not on the first attempt most of the time.

---

### Post by bailbath on 2009-03-13
Which Nvidia card?
Ian

---

### Post by kidux on 2009-03-13
I've had this same problem lately with the 177 recommended driver for my 8400 GS. It acted like it was going to work this morning, but I had to leave for work, so I'll find out when I get home tonight.

---

### Post by rotwang888 on 2009-03-13
I think you're having this problem because you don't have the proper software sources selected.  There's no reason you would have known this, so I'd call it a bug.  Go to system>administration>software sources and click "restricted".  Wouldn't hurt to click "universe" and "multiverse" while you're there.  Hope this helps.

---

### Post by avtolle on 2009-03-13
> **bailbath said:**
> Which Nvidia card?
Ian
GEForce 7000M.

Again, I've not had any problems installing the driver, and having it work, **once it downloads*. ***As was the case with the OP, the first time I tried to activate, after authenticating, etc., the pop-up box appeared, with the text "Downloading" and sat at 0% for a very short bit, then "disappeared" each and every time I've tried to activate the driver when the attempt was the first one made with reference to the computer/release installed. 

I've considered this a problem with the server from which I was trying to download the driver. After one or more additional attempts, it downloads, and the rest is gravy. The fundamental frustration of the OP, as I understand it, is that the driver is selected for activation, the aforesaid cited message appears, and it then disappears without the driver being downloaded. The question posed by him/her is why the described behavior occurs; in light of a subsequent post by another, I merely confirmed it does, in fact, occur as described, and in a later post, suggested that a wired network connection be tried (as it is my hypothesis that trying this on a wireless connection causes a time out or something similar, if there is heavy traffic on the server from which the driver is downloaded).

---

### Post by avtolle on 2009-03-13
> **rotwang888 said:**
> I think you're having this problem because you don't have the proper software sources selected.  There's no reason you would have known this, so I'd call it a bug.  Go to system>administration>software sources and click "restricted".  Wouldn't hurt to click "universe" and "multiverse" while you're there.  Hope this helps.
I cannot speak for the OP; I thought that might be an issue on 8.10, when I first encountered the issue, and did exactly what you suggest. After reloading, tried it again, and again, the same behavior was exhibited.

**I suggest it is more a problem with the server hosting the driver, and heavy traffic creating delays**. It has been my experience that trying again after a few hours usually works. Unlike some other situations, it seems to make no difference whether one tries to activate the driver *ante* or *post* updates that are ready for download on a new installation.

---

### Post by kidux on 2009-03-13
> **rotwang888 said:**
> I think you're having this problem because you don't have the proper software sources selected.  There's no reason you would have known this, so I'd call it a bug.  Go to system>administration>software sources and click "restricted".  Wouldn't hurt to click "universe" and "multiverse" while you're there.  Hope this helps.
That was the first thing I checked, so that's not the issue. Like the previous poster said, I think it's a problem with the server hosting it.

---

