---
title: "Installing my internet"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by 711Savior on 2010-08-22
Hey everyone.
Brand new to Ubuntu here, just installed last night.
Basically, I use Netgear WPN111 and use a wireless USB adapter.
I viewed a guide on how to install it ([http://ubuntuforums.org/showthread.php?t=652910](http://ubuntuforums.org/showthread.php?t=652910))

Now for the problem:
All the files I'm told to download in that thread I put on my flash drive, which Ubuntu finds just fine. :KS

It's downhill from there. If I type say the first thing (In the terminal) ```
sudo apt-get install build-essential
```
say it will only tell me the package can't be found. Is there some specific place I should have put it? Thanks so much all.

---

### Post by Paul820 on 2010-08-22
If you are not on the internet with your ubuntu box then it can't download and install build-essential. Have you got an RJ45 cable you can plug in until you get the wireless working?

---

### Post by 711Savior on 2010-08-22
> **Paul820 said:**
> If you are not on the internet with your ubuntu box then it can't download and install build-essential. Have you got an RJ45 cable you can plug in until you get the wireless working?
Alas I do not. I am on a different level of my house than my router. Is there any way I could download build-essential on windows and copy that to my flash drive?

---

### Post by LinuxHead on 2010-08-22
> **711Savior said:**
> Alas I do not. I am on a different level of my house than my router. Is there any way I could download build-essential on windows and copy that to my flash drive?

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by Paul820 on 2010-08-22
Do you have the ubuntu installation disc? If you do, the put the disc in your drive, then go to System->Administration->Software Sources, on the first screen at the bottom, click the little box next to 'CD-ROM with Ubuntu'. Go to the terminal and type
> sudo apt-get install build-essential
It should now load it from the cd. When you have your internet up and running, unclick the box in the software sources again as you won't need it.

---

### Post by bkratz on 2010-08-22
> **711Savior said:**
> Alas I do not. I am on a different level of my house than my router. Is there any way I could download build-essential on windows and copy that to my flash drive?

Perhaps this thread can help you esp. the links in it

[http://ubuntuforums.org/showthread.php?p=9035543#post9035543](http://ubuntuforums.org/showthread.php?p=9035543#post9035543)

Good Luck

---

### Post by J V on 2010-08-22
What you are looking for: [http://keryxproject.org/](http://keryxproject.org/)

This program will let you give it an order (In this case, install build essentials) then let it perform the download from another computer (The windows computer) and install it when you bring it back. Very handy package manager...

But yes, I also suggest figuring out how to get it to work without resorting to recompiling something...

---

### Post by Paul820 on 2010-08-22
> **J V said:**
> What you are looking for: [http://keryxproject.org/](http://keryxproject.org/)

This program will let you give it an order (In this case, install build essentials) then let it perform the download from another computer (The windows computer) and install it when you bring it back. Very handy package manager...

But yes, I also suggest figuring out how to get it to work without resorting to recompiling something...

That is a handy tool to have, i have never heard of that.

---

### Post by bkratz on 2010-08-22
> **Paul820 said:**
> That is a handy tool to have, i have never heard of that.

That is the same link I was referring to.  It also has a Windows version I just downloaded the zip.

---

### Post by 711Savior on 2010-08-22
Thanks everyone, I'll give it all a shot and post back with results, hopefully from Ubuntu ^_^

---

### Post by coffeecat on 2010-08-22
> **711Savior said:**
> Hey everyone.
Brand new to Ubuntu here, just installed last night.
Basically, I use Netgear WPN111 and use a wireless USB adapter.
I viewed a guide on how to install it ([http://ubuntuforums.org/showthread.php?t=652910](http://ubuntuforums.org/showthread.php?t=652910))

Whoa! Just one moment. That thread dates from 2007 and describes how to compile ndiswrapper from source - which is what you need build-essentials for. But ndiswrapper is in the repositories now for current versions of Ubuntu, together with a GUI Gtk front-end. You don't need to compile it. You'll still have to use the methods others describe to download the ndiswrapper packages, but that howto is obsolete as far as ndiswrapper is concerned.

It might also be obsolete as far as your wireless device is concerned. 2007 is ancient history in Linux-land. Wireless support out of the box is far better now. You might not even need ndiswrapper.

Is the WPN111 the Netgear USB device? If so, open a terminal (Applications > Accessories) and post the output of:

```
lsusb
```... with the device plugged in. That'll give us more information.

Last thing. Have you tried seeing if your machine is seeing a wireless signal, because if it is you won't need ndiswrapper? Click on the network manager icon near the top right of screen.

Which version of Ubuntu are you using?

---

### Post by 711Savior on 2010-08-22
An update: I got the devince installed just fine. It see's it and everything ! :KS
Problem: It now demands a password for netgear, which I've typed perfectly, and it still takes me back to the same thing: Demanding a password )=

---

### Post by Paul820 on 2010-08-22
Are you sure that's not the keyring password?

---

### Post by 711Savior on 2010-08-22
> **Paul820 said:**
> Are you sure that's not the keyring password?
Quite honestly, I probably wouldn't know the difference. When you say "keyring password" are you reffering to the password I use to log into my linux account?

---

### Post by Paul820 on 2010-08-22
Did you get a box pop-up asking you to enter a password for your default keyring like this one [http://blog.up-link.ro/how-to-reset-keyring-password-in-ubuntu/]("http://blog.up-link.ro/how-to-reset-keyring-password-in-ubuntu/")

---

### Post by 711Savior on 2010-08-22
> **Paul820 said:**
> Did you get a box pop-up asking you to enter a password for your default keyring like this one [http://blog.up-link.ro/how-to-reset-keyring-password-in-ubuntu/](http://blog.up-link.ro/how-to-reset-keyring-password-in-ubuntu/)
Never seen that one before. It's on about a Netgear password, which again, I have entered perfectly. Hmm.

---

### Post by Paul820 on 2010-08-22
If you haven't seen that, then it must be your router password.

---

