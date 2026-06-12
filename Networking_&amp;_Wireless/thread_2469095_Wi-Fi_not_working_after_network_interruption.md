---
title: "Wi-Fi not working after network interruption"
date: 2021-11-19
forum: Networking &amp; Wireless
---

### Post by regabrielexv on 2021-11-19
[COLOR=#101010][FONT=Ubuntu]Hello everyone,
First of all, I am a total Ubuntu newbie and English is not my mother tongue, so I apologize if I say something obscure or incorrect . I have a dual-boot HP 255 G7 laptop with Windows 10 and Ubuntu 20.04.3 LTS and I have a problem with the Wi-Fi when using Ubuntu: when my laptop is connected to Wi-Fi network and this network crashes or otherwise abruptly cuts the connection, the Wi -Fi of my laptop cannot connect to any other network: it keeps trying, but never establishes the connection; even if the original network works again after a very short time, the Ubuntu Wi-Fi fails to reconnect. Other users simultaneously connected to the network and using Ubuntu do not have the problem; my laptop has no problems when using Windows. The problem persists even restarting the Wi-Fi, the only remedy is to restart Ubuntu. Normally it happens with the university network, which has very short but daily blackouts: however, to test the problem I also tried to use my smartphone as a router and suddenly turn it off and the problem is identical.[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]
I imagine I need to update the wireless driver, but I can't find the folder where it's located.
My laptop's network card is RTL8821CE 802.11ac PCIe Wireless Network Adapter from Realtek, the driver is RTL8821CE. I don't know if I'm using the proprietary driver or the open source one - I believe the latter though, judging by the informations showed by Software & Updates, which you can see in the attached screenshot:

[/FONT][/COLOR]
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289495&stc=1[/IMG]
[COLOR=#101010][FONT=Ubuntu]
However, since I was not sure, I searched for the driver on the realtek website, yet this page ( [/FONT][/COLOR][https://www.realtek.com/en/component/zo ... e-software]("https://translate.google.com/website?sl=it&tl=en&nui=1&u=https://www.realtek.com/en/component/zoo/category/rtl8821ce-software")[COLOR=#101010][FONT=Ubuntu]) does not report updated versions of the proprietary driver.[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]Instead, following this guide, which is in Italian ( [/FONT][/COLOR][https://lorenzomillucci.it/posts/2019/0 ... ntu-18-04 /]("https://translate.google.com/website?sl=it&tl=en&nui=1&u=https://lorenzomillucci.it/posts/2019/07/2019-07-16-installare-i-driver-per-la-scheda-di-rete-rtl8821ce-su-ubuntu-18-04/")[COLOR=#101010][FONT=Ubuntu] ), I installed this driver ( [/FONT][/COLOR][https://github.com/tomaspinho/rtl8821ce]("https://translate.google.com/website?sl=it&tl=en&nui=1&u=https://github.com/tomaspinho/rtl8821ce")[COLOR=#101010][FONT=Ubuntu]), but I haven't removed the old driver because I don't know the folder where it's located. 

If I run dkms status I get:[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]
```
rtl8821ce, 5.5.2.1, 5.11.0-38-generic, x86_64: installed
rtl8821ce, 5.5.2.1, 5.11.0-40-generic, x86_64: built
rtl8821ce, 5.5.2.1, 5.4.0-90-generic, x86_64: installed
rtl8821ce, v5.5.2_34066.20200325, 5.11.0-40-generic, x86_64: installed
```
[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]Maybe I need to disable or uninstall one of these drivers?[/FONT][/COLOR]

[COLOR=#101010][FONT=Ubuntu]I also point out another problem that perhaps can help you to understand the previous one: if a new network appears when I'm already using the Wi-Fi, it can't find it unless I do not restart it first; if for example I turn on the router of the mobile phone, the ubuntu Wi-Fi does not see it if I do not restart it first, then it sees it and connects perfectly. This problem too is absent on Windows.[/FONT][/COLOR]

[COLOR=#101010][FONT=Ubuntu]Thanks a lot for the help.[/FONT][/COLOR]

---

