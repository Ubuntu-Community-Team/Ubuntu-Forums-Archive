---
title: "Aspire R7-572-6637 Wifi"
date: 2014-12-28
forum: Networking &amp; Wireless
---

### Post by Glancealot on 2014-12-28
[FONT=arial]There is a 74 page thread about how poor the wifi is here:

[http://community.acer.com/t5/2013-Archives/Poor-Wifi-on-new-Aspire-R7-571/td-p/94855](http://community.acer.com/t5/2013-Archives/Poor-Wifi-on-new-Aspire-R7-571/td-p/94855)

I wanted to see if booting into ubuntu would fix the problem (i.e., it could be software based instead of hardware based)

Ubuntu doesn't even recognize the wifi card, so I googled around and found the answer here:

[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

which is a two step fix:

lspci -nn -d 14e4:

which returns 14e4:4359

then simply:

sudo apt-get install bcmwl-kernel-source

and the wifi was on!

then I upgraded drivers and packages and etc according to this post here:

[http://howtoubuntu.org/things-to-do-after-installing-ubuntu-14-04-trusty-tahr](http://howtoubuntu.org/things-to-do-after-installing-ubuntu-14-04-trusty-tahr)

Then I went on [http://www.speedtest.net/](http://www.speedtest.net/)

and the download speed is still only 20% of a 6 year old sony laptop.

So ubuntu is not the magic fix here (neither is win 7 nor the win 8 that comes with the laptop).

Does this mean this is a hardware problem? If so, I would probably just do what this thread here says, which is, replace the wifi card:

[http://community.acer.com/t5/Notebooks-Netbooks/Acer-Aspire-R7-Wifi-Fix/td-p/222375](http://community.acer.com/t5/Notebooks-Netbooks/Acer-Aspire-R7-Wifi-Fix/td-p/222375)

I am just posting here to see if anyone else managed to fix the wifi problem within ubuntu.
[/FONT]

---

### Post by Glancealot on 2014-12-30
Just a quick update, this is ridiculous.

Since booting the laptop into Ubuntu/win 7/win 8 does not solve the problem, you would think that this problem is hardware based.

So I opened up the laptop and replaced the wifi adapter with a Qualcomm Atheros AR9285 Wireless Network Adapter from my 6 year old Sony.

Nope, no improvement whatsoever, in fact, the wifi performance is even worse now. :shock:

So there must be something wrong with the motherboard of this Acer because my 6 year old Sony had very fast wifi connection.

---

### Post by weatherman2 on 2014-12-30
How are you measuring wireless performance?  Please remember that "wireless signal strength" indicators between operating systems may vary greatly.  To measure real-world wireless performance, I would use the same operating system (so boot the same Ubuntu version on both laptops) and copy large files over your location network and compare the actual download rate a few times for each and average them.

I doubt the motherboard would have anything to do with wireless performance, unless it is an interference issue.  I suppose it's possible the antenna has an issue or that one of the antenna wires was even cut off (I assume you re-connected the antenna wires correctly).

---

### Post by jeremy31 on 2014-12-30
> **Glancealot said:**
> Just a quick update, this is ridiculous.

Since booting the laptop into Ubuntu/win 7/win 8 does not solve the problem, you would think that this problem is hardware based.

So I opened up the laptop and replaced the wifi adapter with a Qualcomm Atheros AR9285 Wireless Network Adapter from my 6 year old Sony.

Nope, no improvement whatsoever, in fact, the wifi performance is even worse now. :shock:

So there must be something wrong with the motherboard of this Acer because my 6 year old Sony had very fast wifi connection.

Does the Aspire have 2 antennas?  Have you tried swapping them between the Main and Aux connection on the wifi card?

---

### Post by Glancealot on 2014-12-30
> **weatherman2 said:**
> How are you measuring wireless performance?

[http://speedtest.net/](http://speedtest.net/)

> **jeremy31 said:**
> Does the Aspire have 2 antennas?  Have you  tried swapping them between the Main and Aux connection on the wifi  card?

Interesting suggestion. I am not 100% sure but I don't think the left antenna(of the laptop) is long enough to reach the right connection point (of the wifi card, shown below).

[IMG]http://i.imgur.com/6lxXfcY.jpg[/IMG]

I do have another laptop that has an Intel(R) Centrino(R) Wireless-N 2230, I will switch that into the acer and will report back. Will also look into switching the antennas when I am there.

---

### Post by Glancealot on 2014-12-30
I tried switching the two antennas, doesn't make a difference.

I have ruled out the following causes:

1, "win 8 driver conflict". because the performance is equally bad under ubuntu 14/win7/win8.

2, hardware issue. because the performance is bad even with Qualcomm Atheros AR9285 Wireless Network Adapter which was working fine in a sony laptop.

3, antenna connection backwards. switching the antenna does not improve the performance.

4, loose connection, as the performance is sometimes good, i.e., 15mb/s download, but then the next speed test could be 2mb/s download, whereas all other laptops have a relatively stable speed.

I think there is something wrong with the motherboard. I am very frustrated as this is the best laptop I have owned: quiet fan, amazing form factor, amazing screen. stupid wifi problem ruining everything.

---

### Post by Glancealot on 2014-12-31
Anyone here _fixed _their acer R7?

---

### Post by Glancealot on 2015-01-01
Update: I turned on the Sony and it works very well with the Broadcom adapter that came out of the Acer R7.:mad:

---

### Post by jeremy31 on 2015-01-01
> **Glancealot said:**
> Update: I turned on the Sony and it works very well with the Broadcom adapter that came out of the Acer R7.:mad:

Definitely an issue internal to the Acer, whether motherboard or antenna is at fault might be hard to figure out

---

### Post by Glancealot on 2015-01-01
> **jeremy31 said:**
> Definitely an issue internal to the Acer, whether motherboard or antenna is at fault might be hard to figure out

I think so too, but people reported that they see dramatic increase when they replace the adapter with "INTEL|7260"

[http://community.acer.com/t5/Notebooks-Netbooks/Acer-Aspire-R7-Wifi-Fix/td-p/222375/page/2](http://community.acer.com/t5/Notebooks-Netbooks/Acer-Aspire-R7-Wifi-Fix/td-p/222375/page/2)

what is going on...

---

### Post by jeremy31 on 2015-01-02
> **Glancealot said:**
> I think so too, but people reported that they see dramatic increase when they replace the adapter with "INTEL|7260"

[http://community.acer.com/t5/Notebooks-Netbooks/Acer-Aspire-R7-Wifi-Fix/td-p/222375/page/2](http://community.acer.com/t5/Notebooks-Netbooks/Acer-Aspire-R7-Wifi-Fix/td-p/222375/page/2)

what is going on...

I have 2 different versions of the Intel 7260 and can't complain about the wifi

---

### Post by Glancealot on 2015-01-03
> **jeremy31 said:**
> I have 2 different versions of the Intel 7260 and can't complain about the wifi

I am not doubting Intel 7260's wifi capability, but rather, the problem is **not **the wifi adapter!

---

### Post by Glancealot on 2015-01-18
Well, just a quick update, thought I'd put a closure to this:

I upgraded the laptop with an ultraplus SSD, here is the benchmark

[http://www.passmark.com/baselines/V8/display.php?id=35089512184](http://www.passmark.com/baselines/V8/display.php?id=35089512184)

Right now I am running win 7 and the wifi problem seems to be gone. Yes, it is using the Qualcomm Atheros AR9285 Wireless Network Adapter from the old Sony. So I have no idea which step fixed the problem, but it should be one or a combination of the following:

[LIST=1]
[*]Network Adapter Change: From original to Qualcomm Atheros AR9285. if you followed this thread and are curious as to why I didn't put the original wifi card back: I am too lazy (as it is already inside the Sony laptop) and I have no need for bluetooth. Right now both laptops function well and you know the old saying "don't fix it if it's not broken"
[*]Hard Drive: From Original to SSD
[*]Operating System: From Win 8 to Win 7
[*][COLOR=#ff0000]Number of Screws: 2 bottom screws from the lower corners (corners close to the left ctrl key and the right arrow key) have been removed due to being [/COLOR]_[[COLOR=#ff0000]stripped[/COLOR]]("http://www.wikihow.com/Remove-a-Stripped-Screw")_[COLOR=#ff0000] (I opened the laptop up too many times I guess) You might ask, how could this possibly affect the wifi performance...Well, the removal of the screws *_**released some of the pressure of the bottom cover pressing up against the inner parts**_*. Now thinking back, I wouldn't be surprised if this is what fixed the problem, as I clearly remember that the wifi performance (with the original wifi card) was actually pretty good when I took off the bottom cover at the beginning.[/COLOR]
[/LIST]

---

