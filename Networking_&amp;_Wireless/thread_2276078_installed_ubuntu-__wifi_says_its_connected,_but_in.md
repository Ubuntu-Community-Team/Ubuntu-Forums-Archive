---
title: "installed ubuntu-  wifi says its connected, but internet doesnt work"
date: 2015-04-30
forum: Networking &amp; Wireless
---

### Post by john397 on 2015-04-30
So I successfully installed the latest version of Ubuntu on my PC because I was fed up with Windows 8.1. The ubuntu install officially wiped out the win8 os off my hard drive. Unfortunately, my wireless adapter seems to be connected with full bars and says I'm connected, but Firefox and browser are not getting me to the internet with pages not responding,ect. My internet was working just fine an hour before I had installed Ubuntu. I'm currently using my phone to type this and I'm looking for a solution. I'm stuck with an OS that won't connect me to the internet...which blows. Not a happy camper and hoping someone can assist me.

Interface: 802.11 Wifi (wlan0)
realtek WiFi adapter

---

### Post by kc1di on 2015-04-30
Hi John397 and welcome to Ubuntu nice to have you aboard,

Could you go to a terminal and type the following commands and list the outputs here - Thanks
```
lspci
```
```
lsmod
```
```
rfkill list all
```

These may help us to help you. 
Do you have a hardwire internet connection that you can use temporarily?
Sounds like you may need to install another driver

Also you could run this wireless script it give more information about your wireless connection ```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
``` 

Good Luck

---

### Post by john397 on 2015-04-30
Okay I took pics with my phone and posted attachments below. Can't copy/ paste since my computer internet is not working. :( 

I really really hope I can fix this problem....also I have CD for WiFi adapter that has the Linux drivers. However I'm not sure which driver to unpack and not sure how to this. I'm using a wireless pci - e adapter from netis if that helps as well.

---

### Post by kc1di on 2015-04-30
Your Realtek card is problematic in Ubuntu, but the fix on[ this web page]("https://sites.google.com/site/easylinuxtipsproject/reserve-7") may be of help. looks complicated but it really isn't, 
you do not have to remove the card as suggested either. But you will need a temporary Ethernet connection.

---

### Post by john397 on 2015-04-30
Thanks for replying.

Ethernet connection ? The box is on the other side of house far from computer...also I Followed the instructions in the link you provided , but after entering lsusb command I don't see any bus Device that lists anything from realtek semconductor Corp. I mostly see Linux foundation 1.1 root hub. so it's frustrating and hard to follow  when article tells me what I should be seeing when it's not what I'm seeing on my computer.

I'm beginning to think I really messed my computer up. no going back to Windows because it never came with os disk since I bought PC refurbished.

---

### Post by john397 on 2015-04-30
Ok I give up. Biggest mistake downloading ubuntu. Every time I try to follow commands I just get .."unable to locate package" ect ect . 

I totally messed my computer up. G
so frustrating.

---

### Post by wildmanne39 on 2015-04-30
Because you do not have an internet connection. The driver comes with ubuntu and changing some settings in the router and setting some driver parameters may help, I will help you the best I can but you need to take a breath and relax please. If we have to compile a new driver you will need an internet connection. Please click on wireless script in my signature and follow the directions for running it without an internet connection.
Thanks

---

### Post by john397 on 2015-04-30
Thanks wild man I will try the no internet method tomorrow And use my school computer to save necessary files via flash drive. Hope to God it works...

---

### Post by wildmanne39 on 2015-04-30
Me too, I have had to take my laptop in the past and plug it in to be able to get wireless to work but hopefully it will not come to that.

---

### Post by john397 on 2015-04-30
Wish I could to that..I use desktop. Also how will the no internet method work out...am I actually compling something or just collecting data?

---

### Post by wildmanne39 on 2015-04-30
The wireless script just collects data, if we have to compile a new driver then you would need a wired connection or borrow an usb adaptor that work with ubuntu. Without an internet connection it is almost impossible to get all the needed dependencies to compile and install the driver. Some devices it is easy to install the driver without an internet connection but yours in my opinion.

---

### Post by john397 on 2015-04-30
Ok so you think it's a problem with my specific adapter ...I didn't think of doing usb

---

### Post by wildmanne39 on 2015-04-30
This driver is problematic but there are a few things we can do to help it work better usually.

First in your router change `802.11bgn` to `802.11bg`.

Second change the wpa/wpa2 encryption to just wpa2 (CCMP)(AES) not (TKIP) if you have that option it will work best.

Third set your wireless channel in the router to 1 or 11 then save the router configuration and reboot it.

Fourth go into network manager at top right corner of the screen and click on edit connections>wireless tab and set IPV6 to ignore.

Fifth open the terminal CTRL+ALT+_T then copy and paste the following code one line at a time for accuracy:

```
echo "options rtl8192ce swenc=1 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce
```

---

### Post by chris382 on 2015-05-23
This is quite similar to what i'm going through. I'm not going to give up just yet.

---

