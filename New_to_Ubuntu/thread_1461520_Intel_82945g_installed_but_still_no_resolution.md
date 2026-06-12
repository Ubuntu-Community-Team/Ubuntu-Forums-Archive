---
title: "Intel 82945g installed but still no resolution"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by DarkLotuss on 2010-04-24
Installed ubuntu 9.10 have intel 82945g express chipset graphics onboard. After 2 weeks of searching I decided to create my own post...I have ran the apt below to install driver and it says it is already installed. But i can get no more than 800x600 resolution. Before I loaded ubuntu i was running 1280x1024 in my xp load. I want to stick with ubuntu but this is the video card I have tried and still dont have a normal resolution. The other video is/was a Nvidia Geforce 7600gs. If anyone can help get graphics to normal, i would appreciate it. I am VERY NEW to ubuntu and know nothing of its operations.


sudo apt-get update && sudo apt-get install xserver-xorg-video-intel

---

### Post by cap10Ibraim on 2010-04-24
You may want to try Ubuntu 10.04

---

### Post by cogier on 2010-04-24
I can't work out where the Nvidia card is. If it is an option to install that card then there is the Nvidia 173 driver for it in the Ubuntu Software Centre.

---

### Post by DarkLotuss on 2010-04-24
The Nvidia card is a video card that I started with. Took it out cause I thought it might be easier to find onboard video driver(intel). I tried the Nvidia 173 driver(along with 2 others that came with linux) when I had that card installed...could never get more than 640x480. At least with intel(onboard) i get 800x600 by default.

---

### Post by cogier on 2010-04-24
With the Nvidia driver did you go to the System>Administration>NVIDIA X Server Settings. You can change the resolution there (See attached).

---

### Post by DarkLotuss on 2010-04-24
yes and highest resolution was 640x480 only other option was 340x280 or something...

---

### Post by Mark Phelps on 2010-04-25
> **cap10Ibraim said:**
> You may want to try Ubuntu 10.04

NOT with an Intel 8x series chip, you don't.  The latest release notes indicate that Intel still has NOT solved their driver problems for that series of chips.

---

