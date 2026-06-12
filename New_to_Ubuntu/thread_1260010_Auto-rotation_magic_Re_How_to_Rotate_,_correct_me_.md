---
title: "**Auto-rotation magic** Re: How to Rotate , correct me if i am wrong but............."
date: 2009-09-07
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-09-07
not sure how to do this. never did a "makefile before" could someone explaine a bit? got this from [http://ubuntuforums.org/showthread.php?t=996830&page=11](http://ubuntuforums.org/showthread.php?t=996830&page=11) post #106

                                  [B]
Re: How to Rotate the Screen for a TX2000 Tablet PC[/B]             
                                                                I haven't gotten any response from the bezel buttons yet. As to whether it will work for the TCs, I'm not sure. ill this get are two non-functioning bezel buttons working also? And would the modified module work for other HP tablets, like the TC4200? Not sure. Worth a shot though.

Alrighty then. Here we go. 

**REMEMBER!!** Apply the attached patch to 2.6.30-rc sourced hp-wmi. I used 2.6.30-rc2. 

The makefile here uses the headers for your current kernel. This is something intended to be used in a separate directory ie, /home/whoever/blah. Just take it and stick it into a text file in the same directory as your hp-wmi.c and call it Makefile.

          ```
obj-m := hp-wmi.o
 all:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
```Now the fun part. The FDI file. I have killed way to much time trying to track this information down. :smile: And I'm not even sure if it works yet.

          ```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="info.udi" contains="/org/freedesktop/Hal/devices/computer_logicaldev_input_3">
    <append key="input.switch" type="strlist">0x05:TABLET_MODE</append>
    </match>
  </device>
</deviceinfo>
```Make sure you have input-utils, so you can see if your hal device may be something different.

Using input-event(s?) shows that the tablet swivel is a switch. Although in some fdi files, I've seen switches, such as the regular tablet lid switch referred to as a button. 

That should be about everything. If I've forgotten anything, I'll be back.

Later.

---

### Post by R3fr4cti0n on 2009-09-07
bump

---

### Post by R3fr4cti0n on 2009-09-07
bump

---

