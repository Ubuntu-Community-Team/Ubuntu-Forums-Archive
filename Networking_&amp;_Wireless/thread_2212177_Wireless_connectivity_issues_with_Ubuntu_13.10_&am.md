---
title: "Wireless connectivity issues with Ubuntu 13.10 &amp; rtl8192ce driver"
date: 2014-03-19
forum: Networking &amp; Wireless
---

### Post by dapope13 on 2014-03-19
I am sorry to post such a similar thread as a number of other users, but I have spent ~two weeks of time trying to get this to cooperate using other thread responses. Not to mention trying everything else including usb wifi dongles. No matter what I use/how I configure things I keep getting disconnected every five minutes, if I even stay connected that long. I'm running out of ideas..

[http://pastebin.ubuntu.com/7122562/](http://pastebin.ubuntu.com/7122562/) 
(all the generally needed info put together with [varunendra]("http://ubuntuforums.org/member.php?u=1043629")'s [Wireless Script]("http://ubuntuforums.org/showthread.php?p=12350385#post12350385"))

I thank any and all of you for any help you give now. Seriously. I've been dealing with this since Ubuntu 12.04. If you need any more info, let me know.

EDIT: I'm also using Wicd, because it seems to cooperate at least marginally better than NetworkManager ever did.

---

### Post by dapope13 on 2014-03-19
Well, after some more digging, and finally convincing my friend to change some of the router settings, I seem to be on stable 'footing' now. Changed the router from WPA/WPA2 Personal with TKIP encryption, to WPA2 with AES. 

Still had the disconnection issue, even if my down and up were drastically improved. I tried a couple things from [http://ubuntuforums.org/showthread.php?t=2180314](http://ubuntuforums.org/showthread.php?t=2180314) and 
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -rv rtl8192ce
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -v rtl8192ce swenc=1[/FONT][/COLOR]
``` 
seems to have done the job of stabilizing it the rest of the way. Hopefully this will continue to work for me. And if not, I'll just come back to this post and see if anyone else has any ideas. 

Since it seems to work, at least in my situation, I went ahead and did this; 
```
[COLOR=#000000][FONT=Ubuntu Mono]echo "options rtl8192ce swenc=1" | sudo tee /etc/modprobe.d/rtl8192ce.conf[/FONT][/COLOR]
```

[http://pastebin.ubuntu.com/7123446/](http://pastebin.ubuntu.com/7123446/)
The same wireless info test as earlier, with new setup. 

If anyone needs any other info/has any questions, let me know. And if anyone sees anything else I could possibly do to better my wireless in the future, I'd welcome it. 

Thanks again.

---

