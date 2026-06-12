---
title: "My WIFI is not detected, only my neighboors"
date: 2015-10-29
forum: Networking &amp; Wireless
---

### Post by allg18 on 2015-10-29
So the title explains it.
I can't detect my wifi network on linux, though if I dual boot into windows I can detect and connect to it there. It also works on my Android phone.
I have tried with several Linux distros (all based on ubuntu though, tried with mint, xubuntu and ubuntu) and in neither does my wifi network appear in the list.
Only my neightboors. 


I am quite close to the router.

My laptop is a Toshiba T230-11P.

---

### Post by ian-weisser on 2015-10-30
Please read the [Before posting in Networking & Wireless]("http://ubuntuforums.org/showthread.php?t=370108") sticky.
That sticky will tell you how to obtain the information we need to help you.

---

### Post by allg18 on 2015-10-31
Fixed by accessing the router and changing the Channel selection from Manual to Automatic.
Maybe it was broadcasting in a channel that was too busy. That doesn't explain why Windows and Android still managed to detect it though.

---

### Post by jeremy31 on 2015-10-31
So what channel are you on now?  Do you know what is was before?

---

### Post by allg18 on 2015-11-01
It was on channel 13, and after I changed into Automatic, it set the channel to 6.
Why, does the specific channel matter?

EDIT: Ok, from what I was told, it could be that in the US, channels 12 and 13 are not allowed.
Though I am from Portugal, and I think it is here. At least Windows and Android did detect it with no problem.
Could it be a bug then in Linux? (I had this problem in Ubuntu/Xubuntu and Linuxmint, though I have not tried with any non-Ubuntu-based distros.)

---

### Post by jeremy31 on 2015-11-01
I posted the answer on the linux mint forum and will also post it here

Since you are in Portugal
```
sudo iw reg set PT
```
```
sudo gedit /etc/default/crda
```

Change the last line so it is
```
REGDOMAIN=PT
```
Save file and exit gedit

Reboot

My installs have always been set to the default 00 country code until I change it to US.  There is a chance that if you check
```
iw reg get
```
That it will show country 98 or something other than PT but it should be fine


Other country codes can be found in /usr/share/zoneinfo/zone.tab

---

### Post by allg18 on 2015-11-01
Didn't realize it was you? xD
But shouldn't the OS do it by default (set the regulations according to country)? I mean, it knows in which country you are, right?
How do Windows and Android handle with this?

---

### Post by jeremy31 on 2015-11-01
I don't know why Ubuntu doesn't set it based on time zone or even with the "Where are you?" part of the install.  One possible issue would be travelling to a country that allows more channels than your country and not changing the time zone info.

I am sure some regulatory info is broadcast from wireless routers as I have seen dmesg reports of "Reducing tx power as advertised by (some MAC address)"

---

### Post by allg18 on 2015-11-13
Hi again,

So I reported this issue of not automatically setting country regulations on Ubuntu Launchpad, though they ask me to specify in which package the bug is (which I do not know!). 
Can anyone help me with this, tell me what to do?
[https://bugs.launchpad.net/ubuntu/+bug/1512545](https://bugs.launchpad.net/ubuntu/+bug/1512545)

Thanks in advance

---

### Post by ian-weisser on 2015-11-13
Do you feel that Ubuntu should be magically detecting your country only when you install? Each time you boot? Each time you connect?
The package varies; different packages happen to handle each of those use cases. I would suggest casper (installer), udev or perhaps wpa-supplicant (boot), iw or wireless-tools (each connection). The developers of each of those packages may agree or disagree with your assessment.

There's also a chicken-and-egg problem. Ubuntu cannot guess your country until it gets a network connection (unless you have GPS installed). Expecting the system to know the country before that first connection may, under some circumstances, set up a very nice *race condition* that will completely prevent network access...and perhaps inconvenience many more people than simply allowing Channel 13 to occasionally fail. It's not simply autodetection; it's handling several unknowns at once.

---

### Post by allg18 on 2015-11-14
I am not sure what would be the best option, but we can always check how  it is on other OS for inspiration, probably they have some experience  we can use.

OSX for example seems to change policy according to the router policies.
[http://www.howtogeek.com/211993/how-to-fix-conflicting-country-codes-and-improve-your-macs-wi-fi/](http://www.howtogeek.com/211993/how-to-fix-conflicting-country-codes-and-improve-your-macs-wi-fi/)

What  do you think it would be best? If it would be possible to change  according to location (as opposed to set in installation), that would be  great I think. 
At least, according to what jeremy31 said, it seems like a possibility:
> **jeremy31 said:**
> I don't know why Ubuntu doesn't set it based on time zone or even with the "Where are you?" part of the install.  One possible issue would be travelling to a country that allows more channels than your country and not changing the time zone info.

I am sure some regulatory info is broadcast from wireless routers as I have seen dmesg reports of "Reducing tx power as advertised by (some MAC address)"

If not... Well, anyway, I don't have experience in this, so I will have to trust someone else's wisdom :)

---

### Post by allg18 on 2015-12-24
Duplicate post, please remove.

---

### Post by allg18 on 2015-12-24
Any advise on this? Does someone know how does Windows handle this?

---

### Post by jeremy31 on 2015-12-24
Have you tried Ubuntu 15.10?  Somehow my install set the country code to US and I am not sure yet if the info was from my wifi or from the where are you part of the install

---

