---
title: "Problem with Zonet Zew2500p"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by NNG on 2007-06-30
Well, I recently built a new computer and everything has gone pretty much fine so far except for I can't get my wifi adapter to work.

I spent about 3 hours working on it last night and I found these two guides for reference

[Guide 1]("http://ubuntuforums.org/showthread.php?t=403139")

[Guide 2]("http://ubuntuforums.org/showthread.php?t=205026")

Now, after 3 hours I finally got most that the guides said to work right. The adapter sees and connects to the network alright according to Linux but I still don't have any internet or anything else that would show that I am online. I also get no response when pinging a website as root. 

I am fairly sure that the problem lies in configuring the wireless adapter although I am not sure. I believe this because when I type this command:

```
sudo iwconfig wlan0 essid "AP" mode Managed
```
I get the following error
> SET failed on device wlan0 ; no such device
Now, I originally assumed that for some reason that the wireless adapter wasn't wlan0 (although that's the only wireless adapter) so I tried the same command except with wlan1 and wlan2. Neither worked and I don't know how to verify what the Id is of my wifi adapter. But for all I know, I can be completely wrong.

I would appreciate any help because there's not much on Ubuntu that I can do without the internet :p

---

