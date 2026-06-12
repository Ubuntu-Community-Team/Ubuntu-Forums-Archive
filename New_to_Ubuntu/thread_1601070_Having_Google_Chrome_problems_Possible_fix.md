---
title: "Having Google Chrome problems? Possible fix"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by oregonbob on 2010-10-19
I have been having Google Chrome problems for around a month. I just hit on a possible solution and thought others might want to try it. Here is what I did on my 64bit Ubuntu 10.04 with stable Chrome installed (that constantly crashed):

- Disabled the built-in "Shockwave flash" plugin, 

- Downloaded [Adobe Lab's "Square" flash plugin from here]("http://labs.adobe.com/downloads/flashplayer10.html"). On that page are versions for 32 and 64 bit.

- Made a folder /opt/google/chrome/plugins. That download extracts two files, libflashplayer.so and libffmpegsumo.so . I placed both of those files in that new plugins folder. 

- Started Chrome, version 6.0.472.63, I shuffled around in plugins options, found two entries with no titles or descriptions, I selected **Details** and it showed those two were my new plugins. I enabled them both.

Then I tried to break Chrome. I tried to have another Ah Snap, I opened pages in GMail , played youtube in another tab, played a flash website with audio in a third page. It has been running PERFECT so far!!!!

---

### Post by TBABill on 2010-10-19
Are you running the daily PPA? I have the most current which is .62. You listed .63. Or did you download manually? My flash in Chromium is working great and hasn't crashed in quite some time.

---

### Post by oregonbob on 2010-10-19
I downloaded it manually from the link I gave above. But I spoke too soon because I just broke Chrome again. It worked so perfectly for a while but now it crashes every time, even using option --disable-plugins . Downloaded from this site:
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

I had such hope because it was perfect for a time.

Oh I see you mean Chrome version. .63 was from the standard linux stable download page, not PPA.

---

### Post by oregonbob on 2010-10-19
I have it working great again. When it crashed I also had Picasa open (Wine). It must have used Picasa's flash. After I closed Picasa it all started to work great again, but I'll shut up and keep testing it.

---

### Post by TBABill on 2010-10-19
No problem and my apologies. Some people say Chrome when they mean Chromium, but I realized too late you are using Google Chrome. Sorry I couldn't assist.

---

