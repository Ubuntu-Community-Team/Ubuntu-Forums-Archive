---
title: "MP3 Link but how do you save it?"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by WubiAR on 2011-07-14
Hello there,

I click "Save Link as" on an mp3 pop-up window that plays a recitation, but it comes as a .php file. I checked the source of the pop-up window through "View Source", and I found the direct link of the mp3. Now, what I am having trouble with is how do I get it saved on my computer from the internet? Whenever I paste the link into my address bar and press ENTER, it plays it on the browser.

**How do I save the .mp3 to my computer? Or, where is it hiding (I was thinking somewhere in the temporary files, but I don't know where)..**

---

### Post by wolfen69 on 2011-07-14
You could use aria2 to download it.

```
sudo apt-get install aria2
```
then as an example,:
```
aria2c http://address_to_.mp3
```
then it will be downloaded to your home folder.

---

### Post by WubiAR on 2011-07-14
> **wolfen69 said:**
> You could use aria2 to download it.

```
sudo apt-get install aria2
```then as an example,:
```
aria2c http://address_to_.mp3
```then it will be downloaded to your home folder.

Thank you very much. Will it download regardless of the type of extension (is it able to do .mp4, videos etc.)?

---

