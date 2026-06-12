---
title: "Can't connect to specific wifi network in Ubuntu 16.04"
date: 2018-03-18
forum: Networking &amp; Wireless
---

### Post by rnalon on 2018-03-18
[COLOR=#111111][FONT=Ubuntu]I'm using Ubuntu 16.04 on my laptop and I can't connect to a specific WiFi network. I tried other wifi networks and it worked perfectly. Also, I tried to connect other devices to this wifi network that my laptop can't connect and they managed to connect without any problems. So, the problem seems to be just between my laptop and this particular WiFi network. I've seen several similar questions in the forum but the solutions didn't worked as they seem to depend on specific cases. [/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Any hint about what may be happening?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Should I run the script in the link below?
[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

Thanks in advance!

Edit:
[/FONT][/COLOR][http://paste.ubuntu.com/p/pMNPZm3YPg/]("https://www.google.com/url?q=http://paste.ubuntu.com/p/pMNPZm3YPg/&sa=D&source=hangouts&ust=1521512962246000&usg=AFQjCNHeV1s_weimdr6oTkiVZPGKSXlpOw")

---

### Post by wildmanne39 on 2018-03-18
Hello and welcome to the forum! yes run the wireless script.

Thanks

---

### Post by rnalon on 2018-03-18
Hi wildmanne39, thanks for the quick answer. I edited the post with the link to the pastebinit containing the script output.

---

### Post by rnalon on 2018-03-19
Any help on that, please?

---

### Post by wildmanne39 on 2018-03-19
You are connected to:
> Moto G (4) 2462
but at 1 Mb/s, it says:

The network that you want to connect to is it the one I quoted above? If so you should remove all special characters and spaces in your router settings, that may help I believe it is casing issues. Linux does not like spaces and special characters. 

Go into network manager and change the settings to match the screenshots also please.

Looks like you have 2.4 and 5ghz capabilities,  please rename one of them so your device will not roam every few seconds from one to the other. 

I think these recommendations will help a lot, if you still have problems after making all the changes I recommend run the wireless script again and post the results so we can make sure the changes stuck and see how everything looks.

Thanks

---

### Post by rnalon on 2018-03-20
Hi wildmanne39,

I've connected to that network (which is my mobile phone) only to run the wireless script. Forgot to mention that, sorry. The specific network I couldn't (still can't) connect is the one with SSID
> Enes

Should I run the script again from a wired connection?

Thanks again!

---

### Post by wildmanne39 on 2018-03-20
No you do not need to run the script again. Do everything I asked in post 5, where it is specific to the network name perform the tasks on the network in question, then in your router settings change the WPA1/WPA2 to just WPA2 then save before you close the browser tab. If after you make all the changes you can not connect then run the script again but you do not need to download it again so run it without an internet connection by doing:
```
chmod +x wireless-info
./wireless-info
```
The kernel you are using has caused issues for a lot of people are you sure the computer will connect and has good internet on all other networks?

The error in dmesg suggests a network manager issue but I think that is because you need to change the settings in network manager to match the screenshots for the network you are having trouble connecting too.

I have to be out of town tomorrow and again on Friday so hopefully someone will step in and help you if this does not solve the issue.

Also according to iwlist scan it shows the device not working at all at the moment.

---

### Post by rnalon on 2018-03-25
Hi wildmanne39,

sorry for the delayed answer.

I applied all the changes you asked. However my laptop still can't connect to the network. I ran the wireless script again, without internet connection, as you suggested:
[https://paste.ubuntu.com/p/76pxcFY5B7/](https://paste.ubuntu.com/p/76pxcFY5B7/)

---

### Post by wildmanne39 on 2018-03-25
Right now you have a softblock so you should not be able to connect to any network at this time, please do:
```
echo "blacklist dell_laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot if you still can not connect please run and post the script again so we can make sure the blacklisting of the module above stuck.

Thanks

---

### Post by jeremy31 on 2018-03-25
rnalon, see [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)
This might be caused by power management and wifi router encryption settings

---

### Post by rnalon on 2018-03-25
Hi wildmanne39,

Looks like the blacklisting worked, but I still can't connect to the network :(
I ran the script again: [http://paste.ubuntu.com/p/d6SykgB7zS](http://paste.ubuntu.com/p/d6SykgB7zS)

Edit: Just an additional detail that may be relevant. I can connect to the network "[COLOR=#000000]VIVO-E368" but not to the network "Enes"[/COLOR]

---

### Post by wildmanne39 on 2018-03-25
The 4.4.0-116-generic kernel has a bug, I suggest you reboot and go into the grub menu choose advance options then choose the next newest kernel and I imagine it will work.

---

### Post by rnalon on 2018-03-25
Hi jeremy31,

thanks for the answer. By reading the post it seems to be a different problem. My internet does not disconnects internmittently, rather I can't connect at all to some networks while I have no trouble connecting to other networks. Do you think those steps can help anyway?

---

### Post by rnalon on 2018-03-25
Hi wildmanne39,

I changed the kernel to [COLOR=#000000]4.4.0-83-generic, which was the next newest, however the problem persists.
I ran the script again: [/COLOR]http://paste.ubuntu.com/p/422g54rwTV/

Any other options I can try? Thanks for all the help

---

### Post by rnalon on 2018-03-30
All the hope is gone? :(

---

