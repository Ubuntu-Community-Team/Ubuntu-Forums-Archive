---
title: "Lenovo Legion y530 WiFi adapter not found"
date: 2019-04-23
forum: Networking &amp; Wireless
---

### Post by cookieninja2 on 2019-04-23
Good evening, so I bought a Lenovo Legion y530 with window pre-installed, but I dual booted Ubuntu 18.04.2 LTS on my HDD (my windows is on my SSD). But everything works except my wifi adapter, I have tried a lot of solutions I could find online but not one of them have worked yet.
I also tried the solution mentioned in a other thread [https://ubuntuforums.org/showthread.php?t=2415845&highlight=Lenovo+Legion+y530+Wifi+Adapter](https://ubuntuforums.org/showthread.php?t=2415845&highlight=Lenovo+Legion+y530+Wifi+Adapter) it also didn't work for me. I also tried to install windows drivers using the .inf method. I also disabled secure boot and my wifi adapter is enabled in my BIOS. According to lspci my network controller is 00:14.3 Network controller: Intel Corporation Wireless-AC 9560 [Jefferson Peak] I don't know what else I can give you to help me solve this problem. But if you need any more information feel free to ask and I'm running Gnome 3.28.2

---

### Post by jeremy31 on 2019-04-23
See the wireless script link in my signature and post results

---

### Post by cookieninja2 on 2019-04-25
[URL="http://paste.ubuntu.com/p/6SMtkmdhrM/"]Sorry about that

This is the results i get, Hope it helps. I also updated ens

http://paste.ubuntu.com/p/6SMtkmdhrM/[/URL]

---

### Post by jeremy31 on 2019-04-25
There was no chance ndiswrapper would help, remove with ```
sudo apt purge ndiswrapper && sudo rm /etc/modprobe.d/ndiswrapper.conf
```
Reboot then do ```
./wireless-info
```
Post new script results

---

### Post by cookieninja2 on 2019-05-01
[https://pastebin.com/j1cXm0DC](https://pastebin.com/j1cXm0DC)

I forgot how to use that other pastebin, so I found one online. Hope it still helps

---

### Post by jeremy31 on 2019-05-01
That is the wireless-info file not the wireless-info.txt

---

### Post by cookieninja2 on 2019-05-01
xD Sorry, heres the .txt

[https://paste.ubuntu.com/p/D5SjkDmKM4/](https://paste.ubuntu.com/p/D5SjkDmKM4/)

---

### Post by jeremy31 on 2019-05-01
Try ```
rfkill unblock wifi
``` or use the FN combo to turn wifi on

---

### Post by cookieninja2 on 2019-05-19
Awesome, for some reason it started working about a week ago before I read this post. But I think the previous code did something right. So thank you very much for the help. And how do i change this thread to solved?

---

