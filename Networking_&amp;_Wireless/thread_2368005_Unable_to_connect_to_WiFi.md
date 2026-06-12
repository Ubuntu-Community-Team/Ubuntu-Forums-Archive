---
title: "Unable to connect to WiFi"
date: 2017-08-05
forum: Networking &amp; Wireless
---

### Post by wqyeo on 2017-08-05
Hello, I am currently using Ubuntu 16.04.3 which I just installed onto my Lenovo laptop today.
Whenever I startup the system, I am able to connect to the WiFi (or at least try to), for less than a minute. After that, nothing appears on the Wi-Fi network list.

This happened during the installation too.

I'm currently using Lenovo ideapad 310.

Result of ```
sudo lspci -v
``` [https://paste.ubuntu.com/25249001/](https://paste.ubuntu.com/25249001/)
Result of ```
ifconfig
``` [https://paste.ubuntu.com/25249011/](https://paste.ubuntu.com/25249011/)

And also, I do have access to network via my Ethernet cable.

Threads/Answers that I have tried but unsuccessful:
(According to order of which I have tried first, from the top)

[https://ubuntuforums.org/showthread.php?t=1970501](https://ubuntuforums.org/showthread.php?t=1970501)
[https://ubuntuforums.org/showthread.php?t=1309072](https://ubuntuforums.org/showthread.php?t=1309072) (Step 7, link doesn't work to me)
[https://askubuntu.com/questions/567799/cant-connect-to-a-specific-wifi-network-ubuntu-14-04](https://askubuntu.com/questions/567799/cant-connect-to-a-specific-wifi-network-ubuntu-14-04)

---

### Post by deadflowr on 2017-08-05
*Thread moved to **Networking and Wireless***

---

### Post by praseodym on 2017-08-05
Please run the wireless script from the sticky thread and show the outputs here.

---

### Post by wqyeo on 2017-08-05
I have finally found a solution for me:
[https://medium.com/@elmaxx/rtl8821ae-wifi-drivers-in-ubuntu-16-04-4c1286524afa](https://medium.com/@elmaxx/rtl8821ae-wifi-drivers-in-ubuntu-16-04-4c1286524afa)

Apparently this works for me.

---

### Post by vocx on 2017-08-05
> **wqyeo said:**
> Hello, I am currently using Ubuntu 16.04.3 which I just installed onto my Lenovo laptop today.
Whenever I startup the system, I am able to connect to the WiFi (or at least try to), for less than a minute. After that, nothing appears on the Wi-Fi network list.

This happened during the installation too.

I'm currently using Lenovo ideapad 310.
...
[https://ubuntuforums.org/showthread.php?t=1970501](https://ubuntuforums.org/showthread.php?t=1970501)
[https://ubuntuforums.org/showthread.php?t=1309072](https://ubuntuforums.org/showthread.php?t=1309072) (Step 7, link doesn't work to me)
[https://askubuntu.com/questions/567799/cant-connect-to-a-specific-wifi-network-ubuntu-14-04](https://askubuntu.com/questions/567799/cant-connect-to-a-specific-wifi-network-ubuntu-14-04)

This thread reminded me a lot to this other one: [https://ubuntuforums.org/showthread.php?t=2367093](https://ubuntuforums.org/showthread.php?t=2367093)
Also an Ideapad, in that case 510, and in your case 310.

You are linking three threads, please notice that those threads are about different wireless cards than the one you actually have.
[LIST=1]
[*]The first thread is about an Atheros AR928X card. This is not your card.
[*]The second thread is very old, from 2009, and also about an Atheros card. This is not your card.
[*]The third thread is about a Broadcom BCM4313 card. This is not your card.
[/LIST]

It is very important to check which is the card you have and look for threads on that specific model. Only in this way you will find a guide that applies to your problem. The user in the thread I linked above was also searching for solutions installing and removing the Atheros and Broadcom drivers. These will not work, as your card is a Realtek RTL8821AE.

Funny enough, the solution you found is the same as the solution the other user found. The solution is basically to compile the new "rtl8821ae" kernel module as explained in the link.
> **arunavoster said:**
> 
Solution :
[https://medium.com/@elmaxx/rtl8821ae...4-4c1286524afa]("https://medium.com/@elmaxx/rtl8821ae-wifi-drivers-in-ubuntu-16-04-4c1286524afa")


```

sudo apt-get install linux-headers-generic build-essential git
git clone http://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
sudo make install

```

"These commands build and install the drivers for rtl8192ce, rtl8192se, rtl8192de, rtl8188ee, rtl8192ee, rtl8723ae, rtl8723be, and rtl8821ae, all in one go. Just in case the system doesn’t load the appropriate kernel module, you can execute the following command from within your rtlwifi_new directory
```

sudo modprobe rtl8821ae

```

---

### Post by wqyeo on 2017-08-05
> **vocx said:**
> This thread reminded me a lot to this other one: [https://ubuntuforums.org/showthread.php?t=2367093](https://ubuntuforums.org/showthread.php?t=2367093)
Also an Ideapad, in that case 510, and in your case 310.

You are linking three threads, please notice that those threads are about different wireless cards than the one you actually have.
[LIST=1]
[*]The first thread is about an Atheros AR928X card. This is not your card.
[*]The second thread is very old, from 2009, and also about an Atheros card. This is not your card.
[*]The third thread is about a Broadcom BCM4313 card. This is not your card.
[/LIST]

It is very important to check which is the card you have and look for threads on that specific model. Only in this way you will find a guide that applies to your problem. The user in the thread I linked above was also searching for solutions installing and removing the Atheros and Broadcom drivers. These will not work, as your card is a Realtek RTL8821AE.

Funny enough, the solution you found is the same as the solution the other user found. The solution is basically to compile the new "rtl8821ae" kernel module as explained in the link.


```

sudo apt-get install linux-headers-generic build-essential git
git clone http://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
sudo make install

```

"These commands build and install the drivers for rtl8192ce, rtl8192se, rtl8192de, rtl8188ee, rtl8192ee, rtl8723ae, rtl8723be, and rtl8821ae, all in one go. Just in case the system doesn’t load the appropriate kernel module, you can execute the following command from within your rtlwifi_new directory
```

sudo modprobe rtl8821ae

```

I am currently new to linux and I first I didn't knew about the problem with different drivers. Luckily my friend who was also using Linux kinda told me on that issue.

Thanks for elaborating further on it.

---

