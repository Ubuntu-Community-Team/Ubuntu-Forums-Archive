---
title: "Wireless Network Disabled"
date: 2014-10-07
forum: Networking &amp; Wireless
---

### Post by gadidi on 2014-10-07
Hi, Hallo

I am a new ubuntu user and i'm having trouble with connecting to my wireless network.
It worked just fine untill a week ago.
I tried reading the troubleshooting guide but it's Chinese for me.

I can't enable my wireless connection in the Network Manager app.
This is what i see when i use the command lshw -C network:

*-network DISABLED
discription: Wireless interface
Product: AR9285 Wireless Network Adapter (PCI-Express)
....

There is a driver mentioned in the Configuration line (ath9k)


Can anyone help me understand what i have to do to enable my wireless network?

---

### Post by kc1di on 2014-10-07
HI gadidi and welcome to Ubuntu,

could you go to a terminal and type the following commands and list the outputs it gives here?
Then may be able to help.

```
rfkill list all
```
```
lsmod
```

---

### Post by varunendra on 2014-10-08
For a detailed diagnostics report, please follow the instructions in this post to download and run 'wireless_script' (alternative version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

