---
title: "A Worthwhile Task?"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by merlin_ie on 2010-06-18
Ok, I hope I can explain this correctly. I bought a new passport hard-drive today and used the cp command to transfer things to it from my other (soon to fail) hard-drive, Now, it's working great, but it just sits there as it works. I was wondering if it would be at all possible to come up with a script that can show the progress of the copying (like cdparanoia for abcde) (also shown in screenshot from Google) . I know as much about quantum physics as I do about scripting so any suggestions would really help. And please don't give me a hard time, it's a shot in the dark really :)

---

### Post by ikt on 2010-06-18
Heya,

[http://chris-lamb.co.uk/2008/01/24/can-you-get-cp-to-give-a-progress-bar-like-wget/](http://chris-lamb.co.uk/2008/01/24/can-you-get-cp-to-give-a-progress-bar-like-wget/)

copy the text to a file, and save that file, preferably as cp_p, then in terminal run cp_p instead of cp, and that should work afaik.

[http://www.cyberciti.biz/tips/cp-command-with-a-progress-bar.html](http://www.cyberciti.biz/tips/cp-command-with-a-progress-bar.html)

Hope this helps.

---

### Post by jms1989 on 2010-06-18
Hi, there is this thing called verbose. You can find it on nearly all commandline programs. just append -v to the command and it will output what its doing. So do "cp -v source destination"

Hope that helps, jms1989.

---

### Post by merlin_ie on 2010-06-18
thanks for the replys, this is why I love Linux, the freedom to do as you wish. Saying that, I'm a bit confused. jms1989, your solution is good, but it doesn't show the full progress bar moving, it just says what file is moving. that's good, but it doesn't give how long is left. ikt, your solution is equally good, but there's something I don't understand. I've ran script a few times but to no avail. let me explain what I did

1) copied that text you said to a document in /home/user/scripts/ and named it cp_p (and did chown/chmod as I usually do)
2) I did cd /home/user/scripts
3) in terminal I did cp_p.sh /media/ELEMENTS/hmm/* /media/PASSPORT/
and that spits out : cp_p.sh: command not found
4) then i did sh cp_p.sh /media/ELEMENTS/hmm/* /media/PASSPORT/
and that gives me the result : Last Command Was Successfully Executed (custom PS1 files in .bashrc)

but the thing is, that last result came up instantly, yet no files were moved. so, just looking at that, can you see what I'm doing wrong?

---

### Post by mikewhatever on 2010-06-18
If you want to run the script from your current location, use ./, for example ./cp_p.sh .... If you don't want that, put it in the path, presumably /usr/bin.

---

### Post by merlin_ie on 2010-06-18
> **mikewhatever said:**
> If you want to run the script from your current location, use ./, for example ./cp_p.sh .... If you don't want that, put it in the path, presumably /usr/bin.

well, I just did ```
./scripts/cp_p.sh '/media/ELEMENTS/Music/Albums/ABBA/1992_Gold_-_Greatest_Hits/*' /media/PASSPORT/Music/Albums
``` and it ended up like number 4 above...just said it was successful but nothing happened

---

### Post by jms1989 on 2010-06-18
I don't believe cp can show the progress. You'll need some python code that can actively check the source and destination file sizes, do some math, and spit out a moving bar. But don't know any code other than some bash so I can't help you there.

---

### Post by llamabr on 2010-06-18
gentoo has the -g flag to do just this.  Why is it missing on ubuntu?  For the same reason that my ctrl-alt backspace no longer works?

---

### Post by merlin_ie on 2010-06-18
well, I'd like to thank you all for your suggestions/help but at the end of it all, I've decided to run with Midnight Commander. Will take getting used to, but looks really good. Again, thanks to one and all :)

---

### Post by andrew.46 on 2010-07-05
Hi llamabr,

> **llamabr said:**
> gentoo has the -g flag to do just this.  Why is it missing on ubuntu?

I believe that is [a patch]("http://bugs.gentoo.org/attachment.cgi?id=226591") which gentoo uses but which was not accepted by the coreutils developers and hence is not found in most releases.

Andrew

---

