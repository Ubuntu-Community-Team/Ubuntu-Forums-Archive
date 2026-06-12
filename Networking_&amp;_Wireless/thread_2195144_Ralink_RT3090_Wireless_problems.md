---
title: "Ralink RT3090: Wireless problems"
date: 2013-12-22
forum: Networking &amp; Wireless
---

### Post by darian2 on 2013-12-22
Hey everyone,

I'm having a problem with XUbuntu in which I have just installed it and got it up and running, installed all the updates and all of that.

But the thing is, every couple of minutes the internet disconnects and then reconnects, and keeps repeating this process over and over, which means I can't actually do anything.


Here's the information from running lspci -nn | grep 0280

```
02:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
```

What else do you guys need in order to help me fix this?


Thanks :)

---

### Post by varunendra on 2013-12-23
We need a detailed info of the overall wifi setup. :)

But before that, try this -
```
sudo modprobe -rv rt2800pci
sudo modprobe -v rt2800pci nohwcrypt=Y
```
This will be a temporary change that will be lost at next boot. Does it help stabilizing the connectivity? If not, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by darian2 on 2013-12-23
> **varunendra said:**
> We need a detailed info of the overall wifi setup. :)

But before that, try this -
```
sudo modprobe -rv rt2800pci
sudo modprobe -v rt2800pci nohwcrypt=Y
```
This will be a temporary change that will be lost at next boot. Does it help stabilizing the connectivity? If not, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

[http://pastebin.ubuntu.com/6622859/](http://pastebin.ubuntu.com/6622859/)

That's all I got from the wireless script :)

I also made a video of it disconnecting if that's any help.

The sudo thing made me disconnect a lot more, and I had to turn off my PC to reconnect.

(The reason I really want this to work is one I don't like windows, and 2. Linux is my only option because my windows disk snapped)

thanks :)

---

### Post by darian2 on 2013-12-23
Bump

---

### Post by darian2 on 2013-12-23
Bump :( 

Really trying to get this fixed

---

### Post by varunendra on 2013-12-23
First, please don't bump in less than 24 hrs., it is frowned upon here.

> **darian2 said:**
> 
The sudo thing made me disconnect a lot more, and I had to turn off my PC to reconnect.

Did you run both commands? The first one would remove the driver, thus disconnecting you, the second one would reload it and is supposed to help connectivity. In no case should it make it 'more unstable'.

By the way, there are many things to suggest based on your wireless script report. Try them in order they have been suggested here, stop where the connection becomes stable -

[INDENT]1) Change the encryption type in your router to pure WPA2-PSK with AES (or CCMP, both are same thing). No TKIP, no WPA/WPA2 mixed mode, that doesn't work well with many Linux drivers.

2) Try disabling N-channel in your router if it is supported in it. Set it to use only b/g or g-only mode.

3) Try changing the channel from 6 to 1 or 11 (whichever is least used in your area) in the router. These channels (1 or the highest one available) usually work best with Linux.

4) With the above changes applied, try the "nohwcrypt=Y" parameter again like I suggested earlier. That would still be temporary and we can make it permanent if it now seems to help.[/INDENT]

If you still can't connect after all the above changes, run the wireless_script again and post back the fresh report.

---

