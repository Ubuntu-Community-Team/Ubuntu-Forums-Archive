---
title: "SD Cards"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by aewrfh on 2010-04-17
Would my SD card become damaged if I slide it in and pull it out without manually unmounting the card from the computer? Does it matter whether I was "writing" or performing operations on the card's data, while pulling it out, or not, in terms of corrupting the card to be useless? 

I have a feeling it would break if I did take it out w/o unmounting. I would love to test it some more.

Ubuntu should make it so that this does not happen any more, if it indeed does.

`````````````````````````````````````````````````````````````````````````
4/20/10  4:49 PM
I did some more research into this. It seems that my memory card is dead. I don't know what hardware devices exist that can revive it.

Here are some related sources, I looked at:
1) [http://ubuntuforums.org/showthread.php?t=712602](http://ubuntuforums.org/showthread.php?t=712602)
Recovering data from corrupt SD card (revisited)

2)[http://www.linuxquestions.org/questions/linux-general-1/can-linux-handle-corrupt-sd-cards-693898/](http://www.linuxquestions.org/questions/linux-general-1/can-linux-handle-corrupt-sd-cards-693898/)
Can linux handle corrupt SD cards?

3)[http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html](http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html)
[Recover Data From a dead hard drive using ddrescue]("http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html")

4)[http://pdaphonehome.com/forums/samsung-i730-i830-i830w/91737-2g-micro-sd-card-just-quit.html](http://pdaphonehome.com/forums/samsung-i730-i830-i830w/91737-2g-micro-sd-card-just-quit.html)
2G Micro SD Card just quit!?
```````````````````````````````````````````````````````````````````````````````````
I tested this situation, by inserting a micro SD card in the slot, and not writing/reading. Then I pulled it out without manually unmounting. I slid the card back in and saw if it still works. It did. 

The question now is, does it become corrupt and dead like a brick when you take the card out while it is being modified as in the card's data being used/read, or if the card is having files written onto it?

---

### Post by audiomick on 2010-04-17
Hallo.
As far as I know, disconnecting an SD card, or any other type of storage, whilst it is being written to is likely to cause damage to the file system on the storage medium. Unmounting first is always a good idea.

I also don't believe there is anything to be done to prevent this.

---

### Post by Paqman on 2010-04-17
It won't damage the card, and it shouldn't damage the filesystem, but you run a pretty good chance of corrupting your data.

---

### Post by 2hot6ft2 on 2010-04-17
+1 for what audiomick said.

> **aewrfh said:**
> 
Ubuntu should make it so that this does not happen any more, if it indeed does.
What did you have in mind? Maybe razor blade should slide out and cut your finger or a needle should pop out and stab your finger repeatedly until you learn not to do it.:rolleyes:

How do you propose ubuntu or any OS stop you from doing things that can damage your SD card or its data.
:confused:

---

### Post by ajgreeny on 2010-04-17
And if it should be formatted as ntfs, unlikely, I know, but not impossible, it would not be possible to mount it next time you inserted it without using the force option manually.

I seem to remember that if you do pull a usb disk out without unmounting it first, you will get a notification pop up admonishing you for doing so, and telling you not to do it again.

I don't think a spanking is the next punishment, but you never know- - !!

---

