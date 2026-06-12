---
title: "Wifi card not detected - Lubuntu minimal"
date: 2017-11-01
forum: Networking &amp; Wireless
---

### Post by gglo2 on 2017-11-01
Hello, I installed Lubuntu minimal on an old acer aspire 3100. On the same laptop i used before "normal" Lubuntu, &#1084;y wifi worked well as well as my wired connection (without using any router, i pluged the ethernet cable directly in the ntb and I entered the IP manualy). Now, my wired connection works only with a router and my wifi doesn t work.

After installing Lubuntu minimal I installed "network manager" and i updated the system through the terminal. 

My wifi card is Invilink.
I attached the wirless info scrip.

Thank you for any help!

---

### Post by chili555 on 2017-11-01
Is this your wireless script? Please, in the future, give us the actual link, not a tiny, hard to read screenshot.

[http://paste.ubuntu.com/25864811/](http://paste.ubuntu.com/25864811/)

Please run and post:```
lspci -nnk
dmesg | grep sdio
```

---

### Post by mörgæs on 2017-11-01
Thanks for the wireless info output but better to copy the text and insert it in CODE tags (or post the link - ninja'ed by Chili). A picture is not searchable.

The minimal ISO is, as the name suggests, minimal. It supports a minimum of hardware and most likely no wifi cards. 

Just install with a wired connection.

---

### Post by gglo2 on 2017-11-02
Thank you for replying!

Here is "[COLOR=#000000][FONT=&quot]lspci -nnk" code :
[/FONT][/COLOR]https://pastebin.com/bG459RAb

"dmsg "  together with " grep sdio" doesn´t give anything

 Here is [COLOR=#000000][FONT=&quot]dmesg :[/FONT][/COLOR]
[https://pastebin.com/DQWkaPKb](https://pastebin.com/DQWkaPKb)

This is the wirless info script:
[http://paste.ubuntu.com/25864811/](http://paste.ubuntu.com/25864811/)


I hope this time I posted it correctly.

---

### Post by chili555 on 2017-11-02
So far, we see no wireless devices at all. Is it enabled or disabled in the BIOS? 

I'm sorry, but unless it appears in the BIOS and can be enabled, I don't have further suggestions.

---

### Post by gglo2 on 2017-11-03
I will check it.
Thank you for your time.

---

### Post by praseodym on 2017-11-03
Hi, 16.10 is end of life. Please install 16.04 Long Term Support or the latest 17.10

---

