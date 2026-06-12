---
title: "slow wifi/internet speed"
date: 2013-12-25
forum: Networking &amp; Wireless
---

### Post by hMeU on 2013-12-25
hey!

I am an inexperienced Ubuntu user.

I am observing different internet connection speeds on Ubuntu and Windows.

I searched the forums, found and read this thread: [http://ubuntuforums.org/showthread.php?t=2191091](http://ubuntuforums.org/showthread.php?t=2191091)

As per suggested by "varunendra": [http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385](http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385)
I downloaded and ran the script. 

Here's the pastebin link to the generated file: [http://pastebin.ubuntu.com/6632975/](http://pastebin.ubuntu.com/6632975/)

The internet connection works fine on Windows and my Android device but not on Ubuntu.

---

### Post by varunendra on 2013-12-28
How are you observing the speed, and what is your basis for determining the average traffic (upload/download) speed?
What are the 'practical' speeds in Windows and Ubuntu as per your observations?

If you are sure you are getting significantly slower speeds in Ubuntu, try the following-

Some driver parameters (temporarily) -
```
sudo modprobe -rv iwldvm
sudo modprobe -v iwlwifi **swcrypto=1 bt_coex_active=N**
sudo modprobe -v iwldvm
```
This will be a temporary change that will be lost at next boot. If this helps improving the speed, we can make it permanent.

If the above doesn't help, try another parameter -
```
sudo modprobe -rv iwldvm
sudo modprobe -v iwlwifi **11n_disable=1**
sudo modprobe -v iwldvm
```
This will disable N-channel support on the driver, means you won't get speed higher than 54Mbps (=6 MB(yte)ps approx.). If your current average speed is already better than this, don't try this parameter. If it is worse, it may help.

**PS:**
There are several UFW block messages every few seconds. I suggest you also try temporary disabling it with -
```
sudo ufw disable
```
..and see if there is any significant improvement in the speed.

---

