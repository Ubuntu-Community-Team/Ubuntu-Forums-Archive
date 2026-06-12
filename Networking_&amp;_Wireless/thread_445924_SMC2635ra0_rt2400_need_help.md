---
title: "SMC2635/ra0 rt2400 need help"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by acidblue on 2007-05-16
Runninf Feisty 7.04
I have a SMC2635w pccard that i'm trying to get working.
iwconfig gives me 'ra0 rt2400pci, it sees the card but doesn't turn it on, little led
light never comes on and can't connect to anything.
ifconfig dosn't see the card and 'Network Tools doesn't see it either just iwconfig.
any help would make my day.

---

### Post by horkoser on 2007-07-10
Although I have adquired a conceptronics pc-card (rt61 based), I have tried to make work (just for playing) my old smc2635w card (rt2400). Although I was only trying for less than half an hour, I can say you my results with live cds.

I remembered that it did not work in ubuntu feisty.

In Linux Mint Cassandra (ubuntu 7.04 derived) the led get flashing, even connect to the router (with iwconfig it tells the channel, and signal quality), but I am not able to navigate. Instead the ping delay is very short. So must be someting estupid, but I have checked the ssid, dissabled the mac access, etc, but without result.

in PclinuxOS  it works perfectly and  only in one minute I have able to configure with static ip address, etc.). Actually I am writing this in the laptop with the card inserted.

One strange thing is that with the conceptronic card (rt61 chip based), I obtain the reverse results. The card works perfectly in Mint Linux (in ubuntu freezes the computer), but although the card is apparently detected by PclinuxOS, I could not make it work.

It is the reason why I have changed to mint linux, plus I have the advantages of ubuntu with even easier installation (codecs, beryl just installed out the box), and the rt61 card works (wep only).

Horkoser.

---

### Post by t4thfavor on 2007-07-10
If that card is 802.11b only then I believe I have one at home, I will test it with feisty tonight, and post back.

---

### Post by horkoser on 2007-07-10
Have in mind that there are at least 2 versions of this pc-card (yes it is only 11.b not 11.g):
     - One with the ralink rt2400 chipset.
     - Other with the adm8211 chipset.

So, check which one you have.

Regards,

Horkoser.

---

### Post by t4thfavor on 2007-07-11
I only have a 2632W which is prism I believe. Sorry for the false hope.

---

### Post by blendenzo on 2007-07-15
I'm also a Linux Mint Cassandra user (for a lot of the same reasons horkoser mentioned... I've been using Mint since v2.1 Bea), and I had similar results with the SMC2635.  When I hot-plugged the card, it flashed that there was activity, but it didn't detect any of the networks in the area.

However, when I plugged the card in before booting, it seemed to work better.  It detected one of the local networks but not the other, and it wouldn't connect because the network it detected required security settings that the card doesn't support (I expected that... the IT lady was getting rid of the card because it didn't work with the office network anymore).

Perhaps you should try plugging the card into your laptop and booting from a Mint Cassandra Live CD to see if you can get it to connect.  It seems like it's worth a try.

---

### Post by horkoser on 2007-07-17
This post is only to say that I have got have my network perfectly working with wpa. I am using the pcmcia conceptronic card (ralink rt61). This results are under Linux MInt, but this distribution is a clone of Ubuntu 3.0 the results obtained will be the same. By default ubuntu and MInt have the rt2x00 modified legacy drivers by serialmonkey.

Before I was only able to make work the card with wep encryption, but not with wpa. The method to follow to make work wpa is the previously described by amniarix:
[http://ubuntuforums.org/showthread.php?t=419709](http://ubuntuforums.org/showthread.php?t=419709)

Furthermore, I installed rutilt (the utility that can manage wireless cards -specially designed for ralink ones-. With this utility the configuration gets easier. The installation of this utility is very easy and only is necesary unpack the file and compile it. The clue is that the changes (manually or by rutilT) is to switch the card off by the following command: sudo ifconfig ra1 down (in my case linux mint installed the card as ra1, not ra0 as usually, although it really does not matter at all).

After that you can enter the parameters through rutilt or directly by iwconfig and iwpriv commands.
The next thing is that connect to the wireless network everytime the computer is booting. I follow the instructions given by amniarix, typing them in the interfaces file.

Horkoser.

Hope that is helpfulf (in some way) to make work the smc card

---

