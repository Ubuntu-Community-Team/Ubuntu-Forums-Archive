---
title: "no wifi unbuntu 16.04 and rtl8723be"
date: 2016-09-03
forum: Networking &amp; Wireless
---

### Post by goysachamje on 2016-09-03
Hi!
I am completely new to ubuntu and so far my friends help me to get it installed and helped me to get started with it.
My laptop runs both windows 10 and ubuntu 16.04 and my wifi works fine with I use windows, yet I can't even access wifi networks with ubuntu (I have added images to make illustrate what I mean).

Yesterday, I had access to wifi with ubuntu, but it didn't work when when I suspended my session and logged in again. So I ask my friend to help me fix this problem, but now I the situation is even worse (as I described in the last sentence).
I have a RTL8723BE wireless network adapter.

As i have mentioned I am completely lost and I have absolutely no idea what to do since I am on my own. My computer skills are also underdeveloped so please keep that in mind! :)

Thank you for your help!

---

### Post by chili555 on 2016-09-03
What is the result of these two terminal commands:```
sudo modprobe rtl8723be
rfkill list all
```Thanks.

---

### Post by goysachamje on 2016-09-03
When I do 'sudo modprobe rtl8723be' I have the following error message 'modprobe: ERROR: could not insert 'rtl8723be': Required key not avaiable'. 
When I do 'rfkill list all' I get the following:
0: hci0: Bluetooth
            Soft blocked: no
            Hard blocked: no 
[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]

---

### Post by chili555 on 2016-09-03
> **goysachamje said:**
> When I do 'sudo modprobe rtl8723be' I have the following error message 'modprobe: ERROR: could not insert 'rtl8723be': Required key not avaiable'. 
When I do 'rfkill list all' I get the following:
0: hci0: Bluetooth
            Soft blocked: no
            Hard blocked: no 
[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]Ah, haaaa!!

[http://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](http://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules)

---

### Post by goysachamje on 2016-09-03
If I understand your link correctly I must disable my Secure Boot.... But if I do that, does it mean my computer will be "unsercure"? I am afraid to get virus if I disable my secure boot...
I think my issue is that I don't really understand what's a secure boot :P

---

### Post by chili555 on 2016-09-03
You needn't necessarily disable secure boot, although that is the easiest method. Please refer to the mokutils method in the link I gave.

Please see: [https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Secure_boot](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Secure_boot) and also: [http://www.informationweek.com/software/productivity-collaboration-apps/microsoft-leaks-secure-boot-key-raises-security-concerns/d/d-id/1326582](http://www.informationweek.com/software/productivity-collaboration-apps/microsoft-leaks-secure-boot-key-raises-security-concerns/d/d-id/1326582)

The best way to avoid a virus is the old fashioned way. Don't download from or even visit sketchy websites, don't open attachments to emails unless you are very sure about from whom they were received, etc.

[http://www.wikihow.com/Avoid-Getting-a-Computer-Virus-or-Worm](http://www.wikihow.com/Avoid-Getting-a-Computer-Virus-or-Worm)

---

