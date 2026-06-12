---
title: "updating to Firefox4"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by natman on 2011-03-22
Hi,
How to I update to Firefox 4? is it safe to do it without waiting for the normal update package manager to tell me?
Any idea when the repo's will have firefox 4 ready?

---

### Post by beew on 2011-03-22
> **natman said:**
> Hi,
How to I update to Firefox 4? is it safe to do it without waiting for the normal update package manager to tell me?
Any idea when the repo's will have firefox 4 ready?


FF4 will not appear in the official Ubuntu repository (unless you are using 11.04, which is alpha) To get ff4 you have to add this ppa to your sources list.

[https://launchpad.net/~mozillateam/+archive/firefox-stable]("https://launchpad.net/~mozillateam/+archive/firefox-stable")

Once it is added you would be able to update to ff4 like you would update any software from the repository.

---

### Post by el_koraco on 2011-03-22
> **beew said:**
> FF4 will not appear in the official Ubuntu repository (unless you are using 11.04, which is alpha) To get ff4 you have to add this ppa to your sources list.

[https://launchpad.net/~mozillateam/+archive/firefox-stable]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable")

if you're using firefox 3,16, open a terminal and type: 

```

sudo add-apt-repository ppa:mozillateam/firefox-stable 

sudo apt-get update && sudo apt-get upgrade
```

fcource, if you wanna add the ppa

---

### Post by Vege 4wd on 2011-03-24
I have loaded firefox 4 in lucid. Noticeably faster.

---

