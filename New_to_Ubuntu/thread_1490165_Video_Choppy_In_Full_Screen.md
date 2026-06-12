---
title: "Video Choppy In Full Screen"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by prettymess on 2010-05-21
I just clean installed 10.04 and am pretty pleased with it; however, whenever I watch videos in full screen on YouTube, the video kind of skips/is choppy.  

I seem to remember having this problem when I first installed 9.04 a while back and all I had to do was install some package, but I cannot remember exactly. 

Any suggestions?

---

### Post by prettymess on 2010-05-21
Oh, I'm stupid.  I just searched through my past posts and saw that I actually made this exact thread almost a year ago, but for 9.04, haha.  The solution suggested then works now, as well!

For anyone that might have this problem: System > Administration > Hardware Drivers, and install the recommended graphics driver (in my case it was NVIDIA accelerated graphics driver).

---

### Post by djinnkeeper on 2010-05-21
Is it possible that you have more visual effects enabled than before, or is that a total non-issue?

*Edit: Nevermind then.. :D*

---

### Post by nxhefner on 2010-06-17
That solution worked for me also BUT the problem is using nvidia drivers causes my laptop to NOT return from suspend or hibernate. Any other thoughts to try?

---

### Post by Linuxforall on 2010-06-17
If using nvidia, add xswat ppa which comes with improved mesa and latest nvidia beta 256 series that fixes the suspend issue.

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

In terminal, sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update
sudo apt-get upgrade

---

### Post by mapes12 on 2010-06-17
Streaming video (YouTube and the likes) kept getting interrupted by network traffic making the viewing experience a pain in the butt. Then I discovered the FF addon [downloadhelper]("http://www.downloadhelper.net/") so now I download stuff I want to watch onto my HDD and can then watch it without the network traffic slowing everything down.

Full screen is also better for me this way.

---

