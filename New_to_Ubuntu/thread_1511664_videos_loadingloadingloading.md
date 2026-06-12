---
title: "videos loadingloadingloading"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by sarum on 2010-06-17
Face Book and other sites(HowTo's especially) offer short videos. Some, I fine useful; but watching a 2 minute video takes 10 minutes because of 'Loading loading loading'
I've just bought a new computer; i3cpu,2GB ram, 500GB HD etc:,installed 10.4 Ubuntu(the sooner we run out of animal names the better imho) thinking that watching videos would improve.
What I'd really like to do is to, copy a video to my hard drive to watch it uninterupted.
I've tried 'video downloader' but get "error 228"
Real Player could not down load "because scource file could not be read"
I wonder if there is a simple way of saving these videos.
Any help will be appreciated................sarum

---

### Post by ronnielsen1 on 2010-06-17
There are a few video downloaders (firefox extensions) or you can go to /tmp after watching the video and copy it

---

### Post by mapes12 on 2010-06-17
I use the FF addon [downloadhelper]("http://www.downloadhelper.net/")and it works great.

With the install to your new machine have you installed the ubuntu-restricted-extras package from Synaptic?

Also, have you got all the video codecs from [http://www.medibuntu.org/](http://www.medibuntu.org/)

If that doesn't work I would check how my new machine is configured to access the internet. Even some new hardware has problems reaching a decent speed. To find out right click your Network Manager icon then "Connection Information" to see your speed. I'm on UK broadband and 11Mbps is more than enough for me. If yours shows anything less (like mine did when I installed 10.04 and the speed dropped to 1Mbps) you can issue this command in Terminal to tell it to speed up ```
sudo iwconfig wlan0 rate 11M
```Replace wlan0 with whatever your adapter name is.

Mark

---

### Post by sarum on 2010-06-18
Thankyou both for your replies. Error 228 seems to be a common problem and one without a universal solution. I had a look at 'network connection,' Speed is 'unknown'  
So I installed "One click video downloader" a beta FF add on, that 228 has allowed. I'll give it a go this evening..........thanks for your help, sarum.
PS> If it works I'll add solved to this thread.

---

