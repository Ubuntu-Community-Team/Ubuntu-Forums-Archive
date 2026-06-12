---
title: "Stop Using Network Manager"
date: 2017-07-06
forum: Networking &amp; Wireless
---

### Post by Darth4212 on 2017-07-06
I want to stop using the default Network Manager application supplied with Ubuntu in favor of something better. I would like to know how I would go abut this. Also if there are any programs that you personally think work better than Network Manager. I have read about something called Wicd and was maybe going to check it out.

---

### Post by ian-weisser on 2017-07-06
I'm not sure my "better" is the same as your "better". Are you having some kind of problem with Network Manager?

Uninstalling Network Manager and installing Wicd is a simple matter of telling apt to do so. Both are simply packages.
...of course Wicd is not intended to be a drop-in replacement for NM, so you may find a few differences here and there.

---

### Post by monkeybrain20122 on 2017-07-06
I have read about wicd being "better" but those are from years ago. I have tried it on some kde distros, didn't find it "better", it has more options but also a lot more flaky in my experiments, the show stopper was connection drops off after a while for no reason. So like this guy I had to remove wicd and install NM-manger. But that was also a few years ago so I don't know the current state. The post teaches you how to switch both ways. 


[http://petrkout.com/linux/kubuntu-replace-network-manager-with-wicd/](http://petrkout.com/linux/kubuntu-replace-network-manager-with-wicd/)

---

### Post by monkeybrain20122 on 2017-07-06
> **ian-weisser said:**
> I'm not sure my "better" is the same as your "better". Are you having some kind of problem with Network Manager?

Uninstalling Network Manager and installing Wicd is a simple matter of telling apt to do so. Both are simply packages.
...of course Wicd is not intended to be a drop-in replacement for NM, so you may find a few differences here and there.

You have to install wicd BEFORE you uninstall NM, otherwise you lose your internet connection. Some new users got tripped over on that.

---

### Post by Darth4212 on 2017-07-06
> **ian-weisser said:**
> Are you having some kind of problem with Network Manager?

Yes I have 3 networks nearby with the same essid ,sadly they will remain that way as  there is nothing I can do to change them. So I want to connect via bssid. They have no password for them. So to try to connect with the bssid I run the command:
```
sudo iwconfig wlan0 essid xxxxxxxxxx ap xx:xx:xx:xx:xx:xx
```
I put the x's there for security reasons.
But after I do that Network Manager takes of and does what it pleases and connects me to a different network.

---

### Post by chili555 on 2017-07-06
Have you tried to do the same with NM?

[https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

---

### Post by The Cog on 2017-07-06
I have been using wicd for many months now, because I got frustrated with the unreliability of NM, failing to connect, sometimes even refusing to list any APs at all. I find wicd to be totally reliable. However, I have not tried it in selecting just one of several APs with the same essid. It does have a check box marked "Use these settings for all networks sharing this essid", which suggests that you can treat them differently.

To install wicd, I just install package wicd before removing network-manager, then reboot.
[https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)

I'm not sure if wicd supports IPv6 - there are no configuration fields where I might configure any static IPv6 info (my home router doesn't do IPv6 - Virgin Media are useless, only providing partial internet access).

---

