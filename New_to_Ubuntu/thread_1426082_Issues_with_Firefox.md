---
title: "Issues with Firefox"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by John Z on 2010-03-09
I just switched from Windows XP to Ubuntu a few days ago and I've been having a few issues.

Everything runs fine until I open up Firefox. Once I have FF open it will sometimes start lagging the computer to the point where it because nearly impossible to use.

It will also start breaking up and lagging any music I have running.

I downloaded and installed the adobe flash player, and videos play choppily and without sound.

I disabled all extra visual features but it hasn't helped. Under XP my computer never had any problems running Firefox, so I'm wondering if it's just something I haven't configured correctly.

Thanks.

---

### Post by NT4usB on 2010-03-10
You're on the right track. Flash is a bugaboo in Firefox. 
You running 32 or 64 bit? 
A couple Firefox add-ons might help.
[Adblock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865") and [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433").

---

### Post by ubudog on 2010-03-10
64-bit is known to have problems with flash.  Let us know if you have 32 or 64 bit installed so I can give some instructions on how to fix.

---

### Post by John Z on 2010-03-11
I have a 32bit processor.

I installed both addons, not much difference unfortunately.

I'm not even sure if it's strictly an issue to do with Flash. Sometimes even loading a new page in FF (flash free) or downloading updates causing my computer to start lagging and any music I have playing to become choppy.

---

### Post by wojox on 2010-03-11
You could have a look here: [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by John Z on 2010-03-11
I scanned through the Firefox troubleshooting guide. I think I can use it to solve the no sound issue; however, I don't think it covers my lag problem.

I've been trying a bunch of different things. There isn't any lag when loading cached pages, or when the specific video has completely buffered. 

Also, even without Firefox running I'll still get occurrences of lag when I download anything (torrents, updates, etc.)

So if it only happens when I'm downloading, what could be causing it?

---

### Post by John Z on 2010-03-13
Would I have more success getting an answer if I asked this question in another category?

I really need to get this issue fixed. If I can't I'll probably need to switch back to windows, and I'd rather not have to do that.

Thanks.

---

### Post by baddnady23 on 2010-03-13
I think compiz sometimes causes Firefox issues if I'm not mistaken... are you running the Compiz Settings Manager?

---

### Post by John Z on 2010-03-13
I solved the issue. Ubuntu was limiting my download speed.

All I had to do was put:
```
sudo iwconfig wlan0 rate 11M
```

---

