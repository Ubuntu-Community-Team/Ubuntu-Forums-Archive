---
title: "PS3 Media Server &amp; Ubuntu 10.04 LTS"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by psychx on 2010-07-14
I am having trouble streaming to my PS3 using Ubuntu 10.04 LTS and PS3 Media Server. I got PMS working fine, but when I go to stream a video to my PS3, it plays for a few seconds then starts to freeze up. I am running the video off of a 1TB external hdd. The computer and the PS3 are both wired to my Cisco router. This post was originally for something else, but I just changed it around to ask for help about this. Any help is appreciated!

Edit:

I'm actually wondering if it could be the external hard drive's sleep mode that is causing this. Is there a way to prevent it from going into sleep mode? I can't determine at this point if it goes into sleep mode after already streaming, or if it was doing it before the stream began. Either way, I'd like to explore this option. The only thing I have found so far is for Windows.

Edit #2:

I found an option for Linux. I found a thread here: [http://ubuntuforums.org/showthread.php?t=744073](http://ubuntuforums.org/showthread.php?t=744073)
The program is called sdparm. But I'm not sure how to find out what the location of the external is. An example on how to use the program is listed here:
```
1. install sdparm
2. find location (e.g. /dev/sdc1)
3. enter "sudo sdparm -a /dev/sdc1"
4. enter "sudo sdparm --command=start /dev/sdc1"
5. enter "sudo sdparm --clear STANDBY -6 /dev/sdc1"
```

Anyone got an idea?

I get the following when I try to run the first command:
```
mike@mike-desktop:~$ sudo sdparm -a '/media/FreeAgent Drive'
expected /media/FreeAgent Drive to be a block or char device

```

---

