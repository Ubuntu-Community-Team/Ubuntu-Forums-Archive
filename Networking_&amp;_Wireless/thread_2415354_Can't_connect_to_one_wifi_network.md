---
title: "Can't connect to one wifi network"
date: 2019-03-24
forum: Networking &amp; Wireless
---

### Post by dariusztu on 2019-03-24
I was using wifi network before and then wasn't home for week and it stopped detecting it when I came back. Connecting through hidden networks fails. It works on windows and android. It has the same settings.
Connecting to another wifi works.
 Did any recent update change something? 
Using 18.04 Lenovo G580.

---

### Post by jeremy31 on 2019-03-24
See the wireless script link in my signature and post results.  Does Windows or Android tell you what channel the wifi is on?

---

### Post by dariusztu on 2019-03-26
[https://pastebin.com/1g5Xn4e4](https://pastebin.com/1g5Xn4e4)
Zhone AF36 is network that makes problems. Yesterday it worked, didn't do anything besides dumb clicking trying to connect to known network that didn't work. Then came from work and it was working. Today doesn't see it again, another devices do.

---

### Post by jeremy31 on 2019-03-26
See chilli555's post here [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)
I would recommend changing the channel the wifi router uses to 11 rather than auto

---

### Post by dariusztu on 2019-03-26
Nothing helps. I don't have access to router. Tried 18.04.1 16.04 live CD and same thing...

---

### Post by jeremy31 on 2019-03-26
I would contact Lenovo and see if they can ship you an Intel wifi card that will work in your laptop or order a TP Link TL WN722N 150 Mbps version 1.1 because I have yet to see a Broadcom wifi device work on a 2.4 GHz channel higher than 11 and since you seem to be in Europe, up to at least channel 13 is allowed.  If your phone is android, try wifi radar and see what channel that router is using when the computer won't connect

---

### Post by dariusztu on 2019-03-28
I checked on android on which channel network is and it is 11 and up. Either it does set it automatically or it was switched. I bet it is automatically because one evening it worked and another evening not.
Will have to do something about that.
Thank you for help.

---

### Post by chili555 on 2019-03-28
Channels 11 and up? Your card won't do channels 12 and 13. > 
wlp2s0b1  11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
This might be caused by your possibly incorrectly set regulatory domain. You appear to be in Europe:> 
Region: Europe/Warsaw (based on set time zone)
However, your driver thinks you are in the USA:> 
global
country US: DFS-FCC
Please set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```
Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

Also, I note that your Broadcom wireless loads both drivers brcmsmac and b43. This device uses the driver combination bcma and brcmsmac. I recommend that you blacklist b43 and ssb:
```
sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit

```After these changes, reboot and tell us if the behavior is improved.

I am quite suspicious the auto channel select in the router is a significant isse.

---

### Post by dariusztu on 2019-04-02
Made all changes and it is showing now global PL but phy#0 is still US.
Still doesn't see network. It must be on 12 channel maybe?

---

### Post by chili555 on 2019-04-02
> **dariusztu said:**
> Made all changes and it is showing now global PL but phy#0 is still US.
Still doesn't see network. It must be on 12 channel maybe?Can you tell what channel it is on from some other device on the network? Phones, iPads, etc.?

---

### Post by dariusztu on 2019-04-02
On android wifi scanner it shows graph from 11 to 13 channel.
Sometimes it jut works, like it was switching channels when other networks show up? I must check what channel it is on when it is working.

---

### Post by chili555 on 2019-04-02
Is it on auto channel select? I suggest that you change it to fixed channel 11.

---

### Post by chili555 on 2019-04-02
Please try one other thing; a sort of grasping at straws thing. From the terminal:```
sudo -i
echo "options cfg80211 ieee80211_regdom=PL"  >  /etc/modprobe.d/cfg80211.conf
exit
```Reboot and let us see: ```
sudo iw reg get
sudo iwlist chan
```

---

### Post by dariusztu on 2019-04-09
```
global
country PL: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

phy#0
country US: DFS-FCC
    (2402 - 2472 @ 40), (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 23), (N/A), AUTO-BW
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS, AUTO-BW
    (5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)
```



```
wlp2s0b1  11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
```

Worked again 2 days straight and today again not working. :P

---

### Post by chili555 on 2019-04-10
> **dariusztu said:**
>  Worked again 2 days straight and today again not working. :PI am quite confident that it is auto channel select changing to channels 12 or 13 which you don't get. If you have no access to the router, then I think Jeremy's suggestion to get a new card is valid.

---

