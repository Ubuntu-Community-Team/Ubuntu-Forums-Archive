---
title: "Appallingly New at Ubuntu and wifi dropping 17.04"
date: 2018-01-09
forum: Networking &amp; Wireless
---

### Post by dcparkin on 2018-01-09
Hi forum users;
I just bought an Acer PC from someone, I'm happy with the purchase.  But I have never used Linux at all and I'm literally into day 3 of Ubuntu Studio 17.04.  So imagine that I know less than nothing as I've always relied on Windows.  I don't even know the basics other than turn it on, go online, cut and paste into a terminal (and that's questionable).  I'd like to give this a go and become an Ubuntu guy and say no to Windows but I'm not sure I can.  Lots of questions, but to start with I am having connectivity problems.  I can get online but my wifi drops every 5-10 minutes.  Anyone want to muster the gall to not talk in computer language when talking a Linux peasant newbie like me through this?

---

### Post by chili555 on 2018-01-09
Welcome to Ubuntu. We have a lot of fun here!

In my experience, the main reasons that wireless drops can be down to three reasons. First is power saving. When you haven’t used the wireless for a few minutes, the driver decides to have a short nap. Often, the wireless will not awaken gracefully and reconnect. To help solve this, we simply disable wireless power saving.

I work in the terminal because it’s fast, easy and instantaneous. Moreover, if you simply copy and paste, it’s very difficult to go wrong. Please open the terminal Ctrl+Alt+t and do:

```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```We need super-powers, that is, sudo, to change system-wide files. You will be asked for your password. As you type it in, it will not be echoed back; not even *****. Just type it in and press Enter.

The second reason is that often we set up our routers to use both 2.4 gHz and 5gHz bandwidth using the same network name (SSID). Then our wireless cards are always roaming to find a better signal. When they leave the 2.4 gHz segment to try out the 5 gHz segment, they, of course, drop.

If this is your case, I recommend that you rename the segments to different names such as dcpark24 and dcpark5. Then experiment connecting to each to see which is most stable and fastest.

Third, there are a number of suggestions that I have found that help connectivity. 

Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router.

---

