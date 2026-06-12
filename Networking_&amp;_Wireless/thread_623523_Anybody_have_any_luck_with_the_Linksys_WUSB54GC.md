---
title: "Anybody have any luck with the Linksys WUSB54GC?"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by Roasted on 2007-11-26
So I decide to bypass the whole wireless issue my Toshiba laptop was having by getting this little linksys usb adapter...

And now it makes my system freeze. Constantly. All...the...time...

WHY?!

---

### Post by kevdog on 2007-11-26
Can you google around and find the chipset or driver of the device.  I think its a ra chipset with a rt2500 driver, but Im not sure.  What driver are you using currently for the device?  ndiswrapper or something else?

---

### Post by Roasted on 2007-11-26
I'm using the netr73 driver. I'm in "Windows network drivers" so I assume that's ndiswrapper. Right? 

I set up all kinds of stuff trying to get my old belkin to work... I believe I'm in ndiswrapper. Everything was set up from before, I just went to install new driver, selected the inf driver from the disk... and bam... 

I can't seem to find the exact chipset. I looked up the ubuntu wiki and found it was listed as rt73usb. *shrug* Don't know if that helps...

---

### Post by kevdog on 2007-11-26
Yes so basically you have two options to set up your device

1. Ndiswrapper and the windows drivers
2. Serial Monkey rt73 drivers -- these are native linux drivers

Both options are a pain to set up, and equally as difficult.  I dont know if one method is better than another.  These forums are full of people who claim one way is better than the other.  Just choose one method, get it working and try it.  If you dont like the performance then switch to the other method.

---

### Post by Roasted on 2007-11-26
Is it possible I can use other drivers with ndiswrapper and yield a different result? I mean, the thing will work flawlessly for 10 minutes or so. Then out of no where I freeze up... my computer just runs like molasses. I have no idea what to do at that point. But if I unplug it and reboot, all is well. It's definitely the adapter.

What can I do? Are there other drivers I can use with ndiswrapper? Or should I try the other method?

Does anybody have any detailed instructions with the other method? I haven't even heard of it until now...


p.s. - does anybody have any good experience with usb wireless g adapters? Like anybody here running gutsy who has had NO issues with their wireless G usb adapter? If so PLEASE post with the name and exact model of what you have. I mean... there's still time to return this thing. I've only owned it for about 5 hours now. So if there's something else out there that's a 100% way to work, I'll consider it. Thanks.

---

### Post by kevdog on 2007-11-26
Did this freezing up problem begin after you installed certain packages recently??  I've read of such problems causes by random installs of certain packages.  Or has this problem been this way from the beginning.

As far as the alternative method -- here is the best thread available:
[http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)

---

### Post by Roasted on 2007-11-26
I did a fresh install yesterday. I installed all of the packages and whatnot to get the system up and running and up to date. This evening I installed the wireless driver. The problems started within about 30-40 minutes of use. At first, it just disconnected. Okay, fine. Reconnect. Ehh... froze... okay... so I reboot. I log back in... freezing up again... and it's just been repeating ever since.

I've had no issues with it in vista, just fyi.

---

### Post by kevdog on 2007-11-26
Why dont you try with the rt73 drivers??  Just a thought.

---

### Post by Roasted on 2007-11-26
> **kevdog said:**
> Why dont you try with the rt73 drivers??  Just a thought.

"I'm using the netr73 driver. I'm in "Windows network drivers" so I assume that's ndiswrapper. Right?"

Post #3. :)

---

### Post by kevdog on 2007-11-26
Yes its the windows version of the driver -- the serial monkey drives are the linux equivalent -- but since you compile them, they are native linux drivers.  Sometimes, but not always, this can make a difference.

---

### Post by Roasted on 2007-11-26
I was just talking with my cousin who's a huge linux guy. He thought I was nuts for trying ndiswrapper when there's a native driver available. But that makes me wonder... if native is so much better, why is ndiswrapper so popular with this product which has native drivers????

---

### Post by Roasted on 2007-11-26
Okay. I did a search for a how-to of how to install sea monkey. I did what the directions said, but it said "no command found" when I was on like the 2nd step.

Can someone walk me through how to install this? Please? I can never seem to install tarballs right... EVER... :(

---

### Post by kevdog on 2007-11-26
Can post the step you are stuck on??

---

### Post by Roasted on 2007-11-26
Put it this way...

I get a tar.gz. What am I to do first? Double click the zipped package, hit extract, and select to desktop. Right? Then what do I type in terminal? I'm just confused over what to do in order, because I always get errors.

---

### Post by kevdog on 2007-11-26
At the terminal make sure you are in the directory where the tar.gz file is loacated.  Then type

tar zxvf ####.tar.gz

That will extract the files.

---

