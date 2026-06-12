---
title: "Unknown error (http/404) from clive in youtube"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by mmasroorali on 2010-12-18
Dear All,
Whenever I try to download any video from youtube using clive, I get this error, 

masroor@rafid-hamiz:/tmp$ clive  -f best "http://www.youtube.com/watch?v=B9lt-JI86k4"
fetch [http://www.youtube.com/watch?v=B9lt-JI86k4](http://www.youtube.com/watch?v=B9lt-JI86k4) ...done.
verify video link ...
error: Unknown error (http/404)


This happens all the time. Could you please tell me what might be wrong here?

Any suggestions?

---

### Post by I'mGeorge on 2010-12-18
> **mmasroorali said:**
> Dear All,
Whenever I try to download any video from youtube using clive, I get this error, 

masroor@rafid-hamiz:/tmp$ clive  -f best "http://www.youtube.com/watch?v=B9lt-JI86k4"
fetch [http://www.youtube.com/watch?v=B9lt-JI86k4](http://www.youtube.com/watch?v=B9lt-JI86k4) ...done.
verify video link ...
error: Unknown error (http/404)


This happens all the time. Could you please tell me what might be wrong here?

Any suggestions?

for you tube you could try youtube-dl. When you try to download the clip with clive without specifying the format "-f best" do you get the same error ?

---

### Post by mmasroorali on 2010-12-18
> **I'mGeorge said:**
> for you tube you could try youtube-dl. When you try to download the clip with clive without specifying the format "-f best" do you get the same error ?

Thanks for the reply.

The error occurs irrespective of the -f best option.

youtube-dl gives the following error,

```
masroor@rafid-hamiz:~/tmp/Nusrat Fateh Ali Khan$ youtube-dl http://www.youtube.com/watch?v=B9lt-JI86k4
[youtube] Setting language
[youtube] B9lt-JI86k4: Downloading video webpage
[youtube] B9lt-JI86k4: Downloading video info webpage
[youtube] B9lt-JI86k4: Extracting video information
ERROR: unable to download video (format may not be available)
```

---

### Post by I'mGeorge on 2010-12-18
Okey this it's what you need. If you're using firefox, if not install it, go here [https://addons.mozilla.org/en-US/firefox/addon/10137/](https://addons.mozilla.org/en-US/firefox/addon/10137/), use the link inside firefox. Download the add-on and after the download in firefox a message will pop-out asking you if you wanna install the add-on which of course you do. After instalation go to your you tube clip and below the clip's display you would see the following buttons  +Add to , Share, Embed and a Download as button. Use that button to download any clip from you tube using firefox

By the way if you're using chrome or chromium install this extension [https://chrome.google.com/extensions/detail/digmndkfkmmlinclbhjhagocnccbikdn?hl=en-US](https://chrome.google.com/extensions/detail/digmndkfkmmlinclbhjhagocnccbikdn?hl=en-US) and restart chromium browser with the --enable-extensions flag

```

chromium-browser --enable-extensions

```

and a similar button should appear as the one from firefox bellow the clip on you tube.

---

### Post by mmasroorali on 2010-12-18
> **I'mGeorge said:**
> Okey this it's what you need. If you're using firefox, if not install it, go here [https://addons.mozilla.org/en-US/firefox/addon/10137/](https://addons.mozilla.org/en-US/firefox/addon/10137/), use the link inside firefox. Download the add-on and after the download in firefox a message will pop-out asking you if you wanna install the add-on which of course you do. After instalation go to your you tube clip and below the clip's display you would see the following buttons  +Add to , Share, Embed and a Download as button. Use that button to download any clip from you tube using firefox

By the way if you're using chrome or chromium install this extension [https://chrome.google.com/extensions/detail/digmndkfkmmlinclbhjhagocnccbikdn?hl=en-US](https://chrome.google.com/extensions/detail/digmndkfkmmlinclbhjhagocnccbikdn?hl=en-US) and restart chromium browser with the --enable-extensions flag

```

chromium-browser --enable-extensions

```

and a similar button should appear as the one from firefox bellow the clip on you tube.

Thanks, I use Firefox and another addon got added to the lot I use.

It is working fine. You loose the power and flexibility of command line but it will suffice for the time being. 

Thanks again.

---

### Post by I'mGeorge on 2010-12-19
sometimes clive or youtube-dl standard formats quality doesn't match the video's quality you wanna download and you should try to decrease it like in this tutorial [http://www.khattam.info/howto-modify-youtube-dl-to-make-it-bandwidth-friendly-by-adding-option-to-download-lowest-quality-video-2010-08-17.html](http://www.khattam.info/howto-modify-youtube-dl-to-make-it-bandwidth-friendly-by-adding-option-to-download-lowest-quality-video-2010-08-17.html) But it's a little bit of work that involves a lot of guessing or scripts modification while an add-on in these cases it's far more practical.

---

### Post by mmasroorali on 2010-12-19
> **I'mGeorge said:**
> sometimes clive or youtube-dl standard formats quality doesn't match the video's quality you wanna download and you should try to decrease it like in this tutorial [http://www.khattam.info/howto-modify-youtube-dl-to-make-it-bandwidth-friendly-by-adding-option-to-download-lowest-quality-video-2010-08-17.html](http://www.khattam.info/howto-modify-youtube-dl-to-make-it-bandwidth-friendly-by-adding-option-to-download-lowest-quality-video-2010-08-17.html) But it's a little bit of work that involves a lot of guessing or scripts modification while an add-on in these cases it's far more practical.

Agreed. From youtube I download mostly entertainment things and modifying scripts will simply eat up the time to enjoy them.

I will stick the addon until the bug in clive is remedied.

---

