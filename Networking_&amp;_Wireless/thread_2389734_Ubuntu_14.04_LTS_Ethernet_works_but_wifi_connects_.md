---
title: "Ubuntu 14.04 LTS Ethernet works but wifi connects but does not work"
date: 2018-04-20
forum: Networking &amp; Wireless
---

### Post by frodyteen on 2018-04-20
I downloaded ubuntu 14.04 server then installed the desktop GUI. My problem is the following:
1. wifi icon does not show up on the top right corner, however, if I connected to the ethernet, then the icon comes back.
2. Once the icon comes back and I tried to connect it to wifi, it shows it connects, but there is no internet access.
3. While the ethernet is connected, I only can go on certain websites, for example, it cannot connect to the ubuntu website, shown in this link: [https://drive.google.com/file/d/1H3jNQ8IhRAH1hKZpT7Ye-RGkSBQjDKlp/view?usp=sharing](https://drive.google.com/file/d/1H3jNQ8IhRAH1hKZpT7Ye-RGkSBQjDKlp/view?usp=sharing).
[IMG]https://drive.google.com/file/d/1H3jNQ8IhRAH1hKZpT7Ye-RGkSBQjDKlp/view?usp=sharing[/IMG]
I googled a lot of different methods but none of them worked. I also followed this link: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

but i didn't really get an output when I executed the script, shown below.
[ATTACH=CONFIG]279381[/ATTACH]

I also tried to use the ping 8.8.8.8 command when I connected to ethernet and wifi:
With ethernet:
[ATTACH=CONFIG]279382[/ATTACH]

with Wifi:
[ATTACH=CONFIG]279383[/ATTACH]

It seems like with wifi, it pings 8.8.8.8 for a few times, then it just hangs.

I also ran this command > [COLOR=#000000][FONT=&amp]lspci -n | egrep '0200|0280' | awk '{print$3}'[/FONT][/COLOR]
and the output is :
> 8086:1502
> 8086:0085

So, can anyone help me with my wifi problem?
Thank you.

---

### Post by praseodym on 2018-04-21
Please show
```

lspci -nnk
lsusb
pccardctl info
```

---

### Post by SeijiSensei on 2018-04-21
Choose one interface, wifi or wired (probably the latter), and disable the other one.

---

### Post by frodyteen on 2018-04-21
[ATTACH=CONFIG]279390[/ATTACH]
[ATTACH=CONFIG]279391[/ATTACH]

[ATTACH=CONFIG]279387[/ATTACH][ATTACH=CONFIG]279388[/ATTACH]

---

### Post by frodyteen on 2018-04-21
[ATTACH=CONFIG]279393[/ATTACH][ATTACH=CONFIG]279392[/ATTACH]

[ATTACH=CONFIG]279394[/ATTACH][ATTACH=CONFIG]279395[/ATTACH]

---

### Post by frodyteen on 2018-04-21
if I choose one interface, which is wifi, will I still get internet access if I use ethernet?

---

### Post by SeijiSensei on 2018-04-24
If you choose to use the wifi connection, you would disable the Ethernet interface, so I don't understand the question.

If the machine sits on a desk, use Ethernet. When that's not available, use wifi. Choose the appropriate interface for the situation and disable the other.

---

### Post by frodyteen on 2018-04-26
Can you post the code to disable wifi interface? i tried
```
sudo ifconfig wlan0 down
```

ethernet still can't open some websites, for example, ubuntuforums.org.

I get a
```
Unable to connect, firefox can't establish a connection to the server at ubuntuforums.org
```

---

### Post by SeijiSensei on 2018-04-26
Show us the results of  
```
ifconfig -a
route -n
```

You'll probably need to install the **net-tools** package first.

---

### Post by frodyteen on 2018-04-26
[ATTACH=CONFIG]279452[/ATTACH]
[ATTACH=CONFIG]279451[/ATTACH]

[ATTACH=CONFIG]279450[/ATTACH]

Here it is, Thanks for following up with me!

---

### Post by SeijiSensei on 2018-04-27
Why do you have the "bridged" adapter, br0?

---

