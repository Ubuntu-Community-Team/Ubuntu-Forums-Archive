---
title: "Lubuntu 14.04 - Wifi not working - Atheros AR242x / AR542x"
date: 2014-04-25
forum: Networking &amp; Wireless
---

### Post by artur-ze-alves on 2014-04-25
Hello everyone,

I installed Lubuntu 14.04 on my Acer Aspire One ZG5, and I can't figure out why the wifi is not working.
I run the [ 						 							]("http://ubuntuforums.org/member.php?u=1043629")[**[COLOR=#DD4814][B]varunendra**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1043629")'s wireless script and this is my output:
[http://pastebin.com/PCRSvnj9](http://pastebin.com/PCRSvnj9)

Can anyone help me?
Thanks

---

### Post by varunendra on 2014-04-27
Welcome to Ubuntu Forums!

For starters, could you please change the encryption type in your router/access-point to pure WPA2-PSK with AES (CCMP)? Currently it is using WPA/WPA2 mixed mode with TKIP, which should be avoided.

Also try changing the channel in the router to 1 or 11. Currently it seems to be set at channel 6. Reboot the router after saving the changes.

Apart from the above changes in the router, please try a temporary parameter in Ubuntu -

Open a terminal (Ctrl-Alt-T) and run the following commands -
```
sudo modprobe -rv ath5k
sudo modprobe -v ath5k nohwcrypt=Y
```
This will be a temporary change that will be lost at next boot. If it seems to help, we can make it permanent.

If this doesn't help connecting, please post a description of the problem you are having, along with a fresh report of the wireless_script. Also mention which of the listed access-points is the one you are trying to connect.

**PS:**
The script is not mine by the way. It is *Wild Man*'s, I am just using it. :)

---

