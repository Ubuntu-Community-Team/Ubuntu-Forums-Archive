---
title: "hulu. running 8.04. os not supported?"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by randancing on 2010-04-24
I am running version 8.04 ubuntu. When I log on to hulu videos, I get the message:---

 "Express install not supported on this operating system. To upgrade ;etc;etc.". ---

When I click on the link to update, nothing happens.

Has Hulu ceased to support linux, or is this a flash problem. I don't know what version of flash I am running, but I have installed every update offered, so I should be up to date.
I am not a computer guy and I don't care what o/s I run. I use ubuntu because (for me) it is easier to use than windows. I hope that linux support is not being dropped from the various websites. 

1. hulu and fancast are both broken.

2. Youtube works fine.

3. hulu, fancast, and youtube all work when I re-boot into windows xp.

4. I booted into a copy of ubuntu 10.04RC and got the same response from hulu and fancast. It says that express install is not supported in this o/s.

I have searched the forum and found several people with the same problem, but no one seems to have an answer.

Can anyone point me to a post that gives an answer.

---

### Post by empty_spaces on 2010-04-24
The Hulu website has stopped working for people running 64bit flash. The Hulu Desktop app still works fine though.

---

### Post by -humanaut- on 2010-04-24
I don't use hulu but I'd geuss it's a flash problem you could try enabling backports and updating the flash plugin (i'm on lucid so im not sure what version hardy was using)

---

### Post by niteshifter on 2010-04-24
Hi,

It is a Flash problem: Hulu no longer works with flash version 9. You need to install flash version 10. 

Follow the instructions [here]("http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html") (ubuntugeek.com) - to upgrade from flash 9 to 10 on Hardy.

---

### Post by randancing on 2010-04-24
I want to thank everyone for the replys. I followed the instructions and installed the version 10 flash, but the hulu site still says that the hulu player does not support this operating system. I guess I am stuck with windows for a while if I want hulu, (not an imperative). I am just disappointed that the only way I will be able to use hulu after they start charching is to use a proprietary os.

---

### Post by empty_spaces on 2010-04-24
As I mentioned in my previous post, if you install the **Hulu Desktop** application, you should be able to view Hulu videos on Linux.
[http://www.hulu.com/labs/hulu-desktop-linux](http://www.hulu.com/labs/hulu-desktop-linux)

---

### Post by niteshifter on 2010-04-24
Hi,

Important part of that guide (and easy to overlook): Removal of the old flash plugin. That bit me when I upgraded some months ago.

Check the version of flash Firefox is using by typing into FF's address bar this:
```
about:plugins
```
Scroll down and in the section Shockwave Flash you should see:
```
    File name: libflashplayer.so
    Shockwave Flash 10.0 r42

```

I've 8.04 running on a couple of machines here, Hulu works in the browser for me.

---

### Post by randancing on 2010-04-25
[QUOTE=niteshifter;9170363]Hi,

Important part of that guide (and easy to overlook): Removal of the old flash plugin. That bit me when I upgraded some months ago.

Check the version of flash Firefox is using by typing into FF's address bar this:
```
about:plugins
```
Scroll down and in the section Shockwave Flash you should see:
```
    File name: libflashplayer.so
    Shockwave Flash 10.0 r42

```

This was a great help. I did uninstall the old plugin, or so I thought. When I used the above method of checking (thank you for that. I had never heard of it before) I found that I still had version 9 installed. I am not sure why. I used the terminal to uninstall, but I simply used the code that someone gave me. The message afterwards told me that it was uninstalled and then later told me I had installed new plugin, but it still shows version 9. 
I guess I will have to try again. 

Thanks.

---

### Post by randancing on 2010-04-25
You people are the best. I followed the above link to the hulu website and downloaded the hulu desktop app. It worked fantastic. Thank you all so very much. I think the reason I didn't catch it the first time around was because I didn't realize that it was a video app. Thanks empty_spaces. I will read the replys a little more closely in the future.

---

