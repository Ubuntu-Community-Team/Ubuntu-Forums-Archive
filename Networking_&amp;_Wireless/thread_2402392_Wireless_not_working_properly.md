---
title: "Wireless not working properly"
date: 2018-09-29
forum: Networking &amp; Wireless
---

### Post by mrvorgoth on 2018-09-29
Hello,

I know there are ton of posts like this, but trust me I'm struggling to connect to WiFi since Ubuntu 14, 16 and now 18 :P While I'm using cable everything is fine, but when I'm trying to connect with WiFi it doesn't work. On my latest try I installed Ubuntu 18.04.1 and  didn't even have listed all possible WiFi connections. I tried to use this commang from this post [https://askubuntu.com/questions/1049129/wifi-not-working-on-ubuntu-18-04-lts-lenovo-legion-y520](https://askubuntu.com/questions/1049129/wifi-not-working-on-ubuntu-18-04-lts-lenovo-legion-y520)
sudo tee /etc/modprobe.d/blacklist-ideapad.conf <<< "blacklist ideapad_laptop"but it didn't work out, I made some more changes and then I figured out that installing specific driver for my laptop did show me connections, but as I enterd password for my WiFi network it didn't work out -> it prompts for password everytime and I'm sure it's correct one, because I checked on other devices.

I was wondering if someone can help me get WiFi to work, but because I'm not working with terminal and commands you need to write it down and explain what it does for me. Please send help :)

Thanks in advance

---

### Post by krooknews on 2018-09-30
Hello mrvorgoth

You need to install Broadcom wl driver. Run

 sudo apt[-]("http://krooknews.com")get install bcmwl-kernel-source

---

### Post by mrvorgoth on 2018-10-06
Thanks krooknews, now it's working. It turned out my WiFi was the problem here and I couldn't connect to WiFi, because of that.

What helped?
1) Reinstalling Ubuntu (withour anything alongside like Windows)
2) Using your command: sudo apt get-install bcmwl-kernel-source
3) Fixing my WiFi options

Thank you :)

---

