---
title: "Couple of beginner issues - mail + wifi panel icon &amp; restart feature"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by wombatvvv on 2010-06-02
Just a couple of things.

1 - I use Thunderbird, so I removed the mail icon from the top panel, but when I did, it also seemed to remove several other things, including the sound controller. Why is this? and how do I get it back (the sound controller and other things that were removed along with the mail icon)?

2 - I accidentally removed the networking icon from that top panel as well. Now I have no idea how to select wifi networks. How do I get that back?

I've searched through the "Add to panel..." options, but I can't see anything relating to sound or networking in there.

3. When I choose restart, the computer seems to shut down but then just hang with a black screen. In order to power-off the PC, I have to hold my finger on the power button for a few seconds. It doesn't actually go off or reboot. If I choose shut-down, it logs out and then switches off properly. Is there any reason that restart doesn't work? Is there anything I can do to get it to work properly?

Thankyou.

---

### Post by nhasian on 2010-06-02
1) add to the panel the applet called "notification area" that is what you removed before.

2) see #1

3) make sure you have all the latest updates.  In a terminal enter:

```
sudo apt-get update && sudo apt-get upgrade
```

with any luck that will solve your restarting problem...

---

### Post by sb5551 on 2010-06-02
There should be one that mentions notifications. That is the wireless network and battery and such under that add to panel. 

I use Thunderbird too but I haven't found the solution to the email notification one. Try searching I have heard off one though.

---

### Post by nhasian on 2010-06-02
[How to add Thunderbird to the Ubuntu messaging menu]("http://www.omgubuntu.co.uk/2010/05/how-to-add-thunderbird-to-messaging.html")

---

### Post by wombatvvv on 2010-06-02
> **nhasian said:**
> 1) add to the panel the applet called "notification area" that is what you removed before.

2) see #1

3) make sure you have all the latest updates.  In a terminal enter:

```
sudo apt-get update && sudo apt-get upgrade
```with any luck that will solve your restarting problem...


Thanks this is great. I got most of the things back, and I'm running the update now.

What does apt-get stand for? Just for my own education? (I find these things easier to remember if I know what they're short for - apt?)

Last thing - the sound controller is still missing. Any idea how to get that back?

Thanks very much for everyone's willingness to help a complete newb fumbling around. :-)

---

### Post by sb5551 on 2010-06-02
Add to panel > Indicator Applet. I just deleted mine to figure out the name of it.

---

### Post by wombatvvv on 2010-06-02
> **sb5551 said:**
> Add to panel > Indicator Applet. I just deleted mine to figure out the name of it.


Thanks very much! Perfect.

How odd that it's called "Indicator Applet" with a very vague description instead of "Sound Controller" with a very definite description! ;)

Thanks anyway, fixed.

Edit: it's not even a "vague" description, it's a totally misleading one!

---

### Post by sb5551 on 2010-06-02
I know I created the same thread last week.

---

### Post by nhasian on 2010-06-03
I'm the same way.  it's easier for me to remember the commands if i know what they mean.  APT is the Advanced Packaging Tool that Debian and Ubuntu use.

more information about that [here]("https://help.ubuntu.com/8.04/serverguide/C/apt-get.html")

a good command to know is:

```
sudo apt-get update && sudo apt-get upgrade
```

the first command updates the list of software from your repositories, and the second command tells apt-get to upgrade any available software.  its the same as doing System-> Administration-> Update Manager.

> **wombatvvv said:**
> What does apt-get stand for? Just for my own education? (I find these things easier to remember if I know what they're short for - apt?)

---

### Post by wombatvvv on 2010-06-03
Very helpful. I'm learning a lot here!

Thanks very much.

---

