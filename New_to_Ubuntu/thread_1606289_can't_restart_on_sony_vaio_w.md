---
title: "can't restart on sony vaio w"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by lalahh on 2010-10-26
hi all.
i use ubuntu 10.04, when i restart, the screen close ubuntu and go to frozen black but my lap still runs. i must to force turn off and turn on. now i upgrade to version 10.10, i still have that problem. how can i fix it?

it's same that thread [http://ubuntuforums.org/showthread.php?t=181197](http://ubuntuforums.org/showthread.php?t=181197)
but it's not work with me, i think it's solution for old version.

thanks.
lala

---

### Post by lalahh on 2010-10-27
anyone helps me :(

---

### Post by amjjawad on 2010-10-27
> **lalahh said:**
> hi all.
i use ubuntu 10.04, when i restart, the screen close ubuntu and go to frozen black but my lap still runs. i must to force turn off and turn on. now i upgrade to version 10.10, i still have that problem. how can i fix it?

it's same that thread [http://ubuntuforums.org/showthread.php?t=181197](http://ubuntuforums.org/showthread.php?t=181197)
but it's not work with me, i think it's solution for old version.

thanks.
lala

Hello lala,

Do you have this issue only when you restart? or also when you shutdown as well?

---

### Post by Warren North on 2010-10-27
This may not help but it appears you have a video problem.
By now there got to be driver or something to fix this.
Years ago I had trouble because I had on board ATI and had to get a nvidia video card because my screen would freeze up after a while. It should not be like that now. Anyone know how to help this person

---

### Post by amjjawad on 2010-10-27
Go to
Applications > Accessories > Terminal

```
sudo reboot

```

Please, try that and report back.

It could be a bug. Not sure yet.

---

### Post by lalahh on 2010-10-27
> **amjjawad said:**
> Hello lala,

Do you have this issue only when you restart? or also when you shutdown as well?
  shutdown works normal

> **amjjawad said:**
> Go to
Applications > Accessories > Terminal

```
sudo reboot

```Please, try that and report back.

It could be a bug. Not sure yet.

sudo reboot in terminal, it's work.

whenever i use restart button in menu at top-right screen, it doesn't work.
other problem, when i update or install any software which require restart, i press its restart and the screen is black (i think it's turned off but cpu, hdd... still run).

---

### Post by amjjawad on 2010-10-27
> **lalahh said:**
> shutdown works normal



sudo reboot in terminal, it's work.

whenever i use restart button in menu at top-right screen, it doesn't work.
other problem, when i update or install any software which require restart, i press its restart and the screen is black (i think it's turned off but cpu, hdd... still run).

Lala, I've been searching and searching on google. I got this and hope it will help:

[http://zaidmunir.blogspot.com/2010/07/hiberrnate-and-resume-issues-in-ubuntu.html](http://zaidmunir.blogspot.com/2010/07/hiberrnate-and-resume-issues-in-ubuntu.html)

Sorry for the late response but I'm doing 100 things at the same time :(

---

