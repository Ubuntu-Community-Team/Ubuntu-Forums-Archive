---
title: "Google Chrome"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by Iknownothing on 2010-10-03
Hi

I have downloaded Googles web brower but now can not find it on my netbook anywhere, I have now got 3 copies, ideas where to start looking, its got to be here somewhere!

---

### Post by Paqman on 2010-10-03
The best way to install Chrome is to [add Google's repository]("http://www.google.com/linuxrepositories/ubuntu1004.html") to your list of sources. That way you'll receive security updates automatically. If you install it manually like you've tried to do, then you'll have to keep on top of updates manually.

After adding the Google repo, you can get Chrome through Ubuntu Software Centre just like all your other software, and the updates will come through Update Manager.

Generally speaking, downloading software direct from a website is not the best way to get software on Linux.

---

### Post by aeronutt on 2010-10-03
Look in "places->downloads". (The downloads directory is located in your home directory.  You can also get there by opening a terminal, and typing "cd ~/Downloads"

---

### Post by slakkie on 2010-10-03
> **Paqman said:**
> The best way to install Chrome is to [add Google's repository]("http://www.google.com/linuxrepositories/ubuntu1004.html") to your list of sources. That way you'll receive security updates automatically. If you install it manually like you've tried to do, then you'll have to keep on top of updates manually.

After adding the Google repo, you can get Chrome through Ubuntu Software Centre just like all your other software, and the updates will come through Update Manager.

Generally speaking, downloading software direct from a website is not the best way to get software on Linux.

Google adds the repo to your sources.list.d directory when you download Chrome from their site. And they install the .deb package.

@TS: could you do the following:

```

apt-cache policy google-chrome-{beta,stable,unstable}
dpkg -l | grep google-chrome

```

---

### Post by amjjawad on 2010-10-03
I just installed it few hours ago and I'm using it now.

I assume you have Firefox browser. Have you chosen Save or Run when you were on the Chrome's website?

A) If you have chosen "Save", you'll find it in: Places > Downloads.

B) In case you have chosen "Run", most likely it's installed already and you'll find it in: Applications > Internet > Google Chrome. 


I love Chrome, it's so fast.

---

