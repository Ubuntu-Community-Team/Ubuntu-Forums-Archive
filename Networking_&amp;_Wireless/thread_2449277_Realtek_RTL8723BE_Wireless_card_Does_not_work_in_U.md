---
title: "Realtek RTL8723BE Wireless card Does not work in Ubuntu18.04"
date: 2020-08-24
forum: Networking &amp; Wireless
---

### Post by tushar321 on 2020-08-24
I am having HP laptop (Hp 15R250Tu) with **Realtek RTL8723BE**  WIFI card. The WIFI connection keeps getting Dropped after some time  like 15-20 minutes and then it won't connect no matter what I do expect  the only option left is to restart. To solve this I tried several  solutions but NO Success. I am left further with No Clue what shall be done. Please any help would be appreciated.

Solutions Tried:
[HTML]sudo apt update
sudo apt install git dkms
git clone https://github.com/lwfinger/rtw88.git
sudo dkms add ./rtw88
sudo dkms install rtlwifi-new/0.6

[/HTML]

[HTML]
$ make
$ sudo make install
$ sudo modprobe -rv rtl8723be
$ sudo modprobe -v rtl8723be ant_sel=2
$ echo "options rtl8723be ant_sel=2" | sudo tee /etc/modprobe.d/50-rtl8723be.conf


[/HTML]

---

### Post by dino99 on 2020-08-24
try [https://medium.com/devstudio/how-to-install-wifi-driver-of-rtl8723be-in-ubuntu-18-04-1c031e2baf5](https://medium.com/devstudio/how-to-install-wifi-driver-of-rtl8723be-in-ubuntu-18-04-1c031e2baf5)

---

### Post by tushar321 on 2020-08-24
This link is expired which the author has mentioned “gitclone https[://github.com/lwfinger/rtlwifi_new.git]("https://github.com/lwfinger/rtlwifi_new.git")**” **

---

### Post by mastablasta on 2020-08-25
many versions, guides and options. this one make sense (driver might need additional packages to work): [https://chirathr.wordpress.com/2017/12/11/installing-realtek-rtl8723be-driver-for-ubuntu-debian-or-fedora/](https://chirathr.wordpress.com/2017/12/11/installing-realtek-rtl8723be-driver-for-ubuntu-debian-or-fedora/)

second one is to try 20.04 or a newer kernel from mainline  for example: [https://itsfoss.com/upgrade-linux-kernel-ubuntu/](https://itsfoss.com/upgrade-linux-kernel-ubuntu/)
by the way are you using the HWE stack on 18.04? [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

finally if all fails (though it shouldn't) a workaround - wi-fi dongle - they are small and cost about 4 or 5 EUR. raspberrypi shops have plenty of the small models available and tested to work perfectly with linux.

---

### Post by chili555 on 2020-08-25
> Please any help would be appreciated.
Please start here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by ActionParsnip on 2020-08-25
Will this work?
[https://tutorialforlinux.com/2020/02/21/step-by-step-ubuntu-20-04-realtek-rtl8723de-driver-installation-guide/2/](https://tutorialforlinux.com/2020/02/21/step-by-step-ubuntu-20-04-realtek-rtl8723de-driver-installation-guide/2/)

be = de ?

---

### Post by mastablasta on 2020-08-26
yes, but you need to use driver for OP chip. and secure boot should be off. and as i posted sometimes additional libraries might be needed.

---

### Post by tushar321 on 2020-08-26
Hello as per the mentioned link I followed the first two commands.
> 
sudo apt update
sudo apt dist-upgrade


waited for some time the connection got dropped even after that so here I am pasting the link of Wireless link info for further guidance 
[https://pastebin.com/Vfa9nM3a](https://pastebin.com/Vfa9nM3a)

---

### Post by jeremy31 on 2020-08-26
Lets try disabling wifi power management, in terminal
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
echo "options rtl8723be ant_sel=2 ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Reboot

---

### Post by tushar321 on 2020-08-26
Hello sir tried this command but connection dropped "Activation of network connection failed"

---

### Post by ajgreeny on 2020-08-26
*Thread moved to **Networking & Wireless**.* which is more appropriate and a better fit.

---

### Post by jeremy31 on 2020-08-26
Try to connect to wifi again and run this in terminal ```
./wireless-info
```
Then connect with the smart phone and post results

---

### Post by tushar321 on 2020-08-27
Here are the results of Wifi and Mobile tethering 

When connected to wifi jio network
[https://pastebin.com/ED6nsJ5E](https://pastebin.com/ED6nsJ5E)

When connected to redmi mobile using tethering
[https://pastebin.com/t318U6gW](https://pastebin.com/t318U6gW)

---

### Post by jeremy31 on 2020-08-27
Can you change the wifi router to use channel 1 rather than auto or channel 9?
It might also help to go into Network Manager settings for your connection and disable IPv6, and set your country code, in terminal do
```
sudo iw reg set IN
```

---

### Post by tushar321 on 2020-08-28
Hello @jeremy31, I have changed the channel to 1 and have disabled the  IPv6 from network settings(GUI) even set the country via terminal. After  this an improvement has noticed the connection gets dropped but but now  it regains as soon as I turned the wifi Off and then On. The speed of  wifi has become somewhat slow here is the link of wireless txt after  these modifications [https://pastebin.com/YSg3CAB7 ]("https://pastebin.com/YSg3CAB7")

---

### Post by tushar321 on 2020-08-28
I had found some link on internet I want to ask will this work in my case [https://github.com/kelebek333/rtl8188fu/blob/master/README.md](https://github.com/kelebek333/rtl8188fu/blob/master/README.md)

---

### Post by chili555 on 2020-08-28
> **tushar321 said:**
> I had found some link on internet I want to ask will this work in my case [https://github.com/kelebek333/rtl8188fu/blob/master/README.md](https://github.com/kelebek333/rtl8188fu/blob/master/README.md)No, it will not. 

Your device is this: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [[COLOR="#FF0000"]10ec:b723[/COLOR]]

The modalias for the driver you've linked is but a single device:```
version:        v4.3.23.6_20964.20170110
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
firmware:       rtlwifi/rtl8188fufw.bin
srcversion:     41F856D51474AE9E736D905
alias:          usb:v[COLOR="#FF0000"]0BDA[/COLOR]p[COLOR="#FF0000"]F179[/COLOR]d*dc*dsc*dp*icFFiscFFipFFin*

```This is a completely different driver for a completely different device.

---

### Post by tushar321 on 2020-08-29
What shall be done further

---

### Post by tushar321 on 2020-08-31
@chili555 , @jeremy31 or anyone can you please help me further, actually I am having only this laptop to work on moving to a new one I will have to move my entire projects and files to new one that's gone be a tedious task.

---

### Post by chili555 on 2020-08-31
> [ 4926.708419] wlp2s0: send auth to <MAC address> (try 1/3)
[ 4926.711374] wlp2s0: authenticated
[ 4926.713368] wlp2s0: associate with <MAC address> (try 1/3)
[ 4926.726530] wlp2s0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=2)
[ 4926.726816] wlp2s0: associated
[ 4926.735615] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[ 5173.711654] rtlwifi:[COLOR="#FF0000"] AP off, try to reconnect now[/COLOR]
[ 5173.711807] wlp2s0: Connection to AP <MAC address> lost
[ 5183.791097] rtlwifi:[COLOR="#FF0000"] AP off, try to reconnect now[/COLOR]
[ 5190.659162] wlp2s0: [COLOR="#FF0000"]Connection to AP[/COLOR] <MAC address> [COLOR="#FF0000"]lost[/COLOR]In this context, AP refers to Access Point; that is, your router. Could this be a router problem? Could your router be working intermittently? Do other compters on the network ever disconnect and reconnect? 

In my experience, Windows and iOS wireless device and driver combinations seem to recover from such things gracefully. Many Linux drivers do not.

---

### Post by tushar321 on 2020-09-01
May be this might be the issue but other devices connected to wifi works fine. still i'll observe it for one more day. Although I noticed one thing when the connection gets dropped the wifi settings shows no wifi network at all of the vicinity. Finally I want to ask will this thing work [https://github.com/smlinux/rtl8723de](https://github.com/smlinux/rtl8723de)

---

### Post by chili555 on 2020-09-01
> Finally I want to ask will this thing work [https://github.com/smlinux/rtl8723de](https://github.com/smlinux/rtl8723de)

I can't get it to compile but I believe it is for a different device:
```
alias:          pci:v0000[COLOR="#FF0000"]10EC[/COLOR]d0000[COLOR="#FF0000"]D723[/COLOR]sv*sd*bc*sc*i*

```
They are certainly related, however, they are not the same. You can't fit a wheel from your 2020 Ford Focus on to a 1998 Ford Explorer.

---

### Post by tushar321 on 2020-09-03
@chili55, As mentioned by you in one of your answers on ask ubuntu > Quite often, the weak signal is a symptom of the antenna wire being  connected to connection #1 on the card when the default driver is  expecting to see the signal at connection #2. Of course, you could open  the laptop and switch the wire or you could try a driver parameter that  permits antenna selection at the driver level.. I am going to try the #1 option whether this works or not.

---

### Post by plasticdeveloper32 on 2020-09-03
I was facing same issue, after a while this error occurs Activation of network connection failed in ubuntu 18.04 LTS and after some googling and debugging i though it must be my system issue and performed a clean Ubuntu installation and again same thing occurred. I also have same rtl8723de wifi module.

---

### Post by plasticdeveloper32 on 2020-09-03
Is there any quick fix, i don't have any other station to continue my work.

If you want to perform some troubleshoot commands on a fresh ubuntu, i can run them for you as there is no risk of data loss or corruption, i backed up all my data before performing fresh installation.

I would request to be quick with replays.

---

### Post by jeremy31 on 2020-09-03
If you want to try the rtlwifi_new that was removed from github I uploaded what I had to [https://www.dropbox.com/s/yp9ap3022cmx9xb/rtlwifi_new.tar.gz](https://www.dropbox.com/s/yp9ap3022cmx9xb/rtlwifi_new.tar.gz)
You will just have to extract and install it

---

### Post by tushar321 on 2020-09-04
@plasticdeveloper32, You can try this what jeremy31 has mentioned see if it gives you success till then I will try to figure out this antenna's wire swapping on wifi card. If wifi starts working for you test it thoroughly and tell.

---

### Post by plasticdeveloper32 on 2020-09-04
Ok so i downloaded the rtlwifi_new from the above dropbox link, followed this medium for installation [link]("https://medium.com/devstudio/how-to-install-wifi-driver-of-rtl8723be-in-ubuntu-18-04-1c031e2baf5") 
When i trying to run this command on terminal, this error is the output with wifi module disappeared from settings:

sudo modprobe rtl8723de

Output: modprobe ERROR could not insert 'rtl8723be' : Operation not permitted

---

### Post by jeremy31 on 2020-09-04
What result for ```
mokutil --sb-state
```

---

### Post by plasticdeveloper32 on 2020-09-04
Outout: secureboot enabled

---

### Post by jeremy31 on 2020-09-04
You need to get into BIOS settings and disable Secure Boot

---

### Post by plasticdeveloper32 on 2020-09-04
ok so after disabling secureboot, wifi module is up and ran the previous commands 

> sudo modprobe -r rtl8723be

> sudo modprobe rtl8723be

and successfully executed.

As the issue occurs after some time so lets wait. 

when i open logs there is always this error:

> bgscan simple: Failed to enable signal strength monitoring

and can i enable secureboot as the module is up and running ??

---

### Post by plasticdeveloper32 on 2020-09-04
It broke again, it just disconnected and when i turn off the module and turn on again it connect with router but no internet access.

---

### Post by jeremy31 on 2020-09-04
See the wireless script link in my signature and post results

---

### Post by plasticdeveloper32 on 2020-09-04
i think i have put my foot under wrong hood, my signal strength are ok, the issue is after a while or say randomly the wifi disconnect and throws this error in the notification:

Activation of network connection failed

And i have also done the thing you said leading that to disabling secure boot and making thing more worse is it ??

How can i revert the changes, enable secure boot and then tryna find fix of the Activation of network connection failed error through default stuff.

---

### Post by plasticdeveloper32 on 2020-09-04
Result which you asked:

[https://pastebin.com/5qZznvxt](https://pastebin.com/5qZznvxt)

---

### Post by praseodym on 2020-09-04
Change the encryption mode in your router to WPA2-AES (CCMP) only, no mixed mode WPA/WPA2. Reconnect

---

### Post by tushar321 on 2020-09-04
Exactly same problem is with me after some 10-15 minutes the connection gets dropped. To solve this today I opened up the laptop to swap the antenna wire to(aux port/no.2) and to my surprise there is no second antenna port at all given in wifi card. so all and all the antenna depends on just single connection and this leaves no room to swap the antenna port. The only solution left to me is now driver solution.

---

### Post by plasticdeveloper32 on 2020-09-04
Also the results i have posted above are when the wifi was on and running, these are one with wifi sudden off:

[https://pastebin.com/PFKR6xdi](https://pastebin.com/PFKR6xdi)

I have changed the security mode as suggested WPA2-AES and now waiting if error is occuring or not.

---

### Post by tushar321 on 2020-09-04
what is your connection speed

---

### Post by plasticdeveloper32 on 2020-09-04
Around 15 Mbps to 20 Mbps

---

### Post by plasticdeveloper32 on 2020-09-04
Around 15Mbps to 20Mbps, or are you asking for signal strength if you are then the above results i pasted shows Quality 70/70.

---

### Post by plasticdeveloper32 on 2020-09-04
> **praseodym said:**
> Change the encryption mode in your router to WPA2-AES (CCMP) only, no mixed mode WPA/WPA2. Reconnect


Nah man, same error

---

### Post by plasticdeveloper32 on 2020-09-04
> **tushar321 said:**
> Exactly same problem is with me after some 10-15 minutes the connection gets dropped. To solve this today I opened up the laptop to swap the antenna wire to(aux port/no.2) and to my surprise there is no second antenna port at all given in wifi card. so all and all the antenna depends on just single connection and this leaves no room to swap the antenna port. The only solution left to me is now driver solution.

Please share the solution if it works, beginner here don't want to mess with kernel anymore.

---

### Post by tushar321 on 2020-09-04
Even I am beginner, I could have definitely shared the solution to this if I would have known. As you have clean installation and you have backup of the data you having nothing to loose but for me I have lot of projects and software installed on my system and moving that to new thing will be tedious task for me . Keep following the guidance given by others one or other solution will be successful.

---

### Post by plasticdeveloper32 on 2020-09-04
Someone help us, i have work pending i am sitting right by the router with holding Ethernet in my hand. :P

This error occurred by its own, i even did a fresh installation still same error why, Ubuntu worked for months without null errors smooth experience, brought tons of flexibility, automation, and this small error is giving such a pain in the ****. FIX IT, do your MOJO

---

### Post by tushar321 on 2020-09-04
:P Even I am sitting just beside the router

---

### Post by jeremy31 on 2020-09-04
> **plasticdeveloper32 said:**
> Someone help us, i have work pending i am sitting right by the router with holding Ethernet in my hand. :P

This error occurred by its own, i even did a fresh installation still same error why, Ubuntu worked for months without null errors smooth experience, brought tons of flexibility, automation, and this small error is giving such a pain in the ****. FIX IT, do your MOJO

Run the commands I posted at [https://ubuntuforums.org/showthread.php?t=2449277&p=13982059#post13982059](https://ubuntuforums.org/showthread.php?t=2449277&p=13982059#post13982059) and reboot

---

### Post by jeremy31 on 2020-09-04
> **tushar321 said:**
> :P Even I am sitting just beside the router

See the wireless script link and post results

---

### Post by plasticdeveloper32 on 2020-09-04
done, should i wait now or share the wireless script results ??

---

### Post by tushar321 on 2020-09-05
Although I have submitted the results in earlier replies but here are the new results of wireless script [https://pastebin.com/e78kKPLE](https://pastebin.com/e78kKPLE) and journalctl [https://pastebin.com/TfTygk11](https://pastebin.com/TfTygk11)

---

### Post by plasticdeveloper32 on 2020-09-05
Have you run the command by jeremy31 ??

> sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
echo "options rtl8723be ant_sel=2 ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf


Because its been a while i am on WIFI and error seems to be fixed no authentication errors.

I request jeremy31 to guide me to old config with secureboot enabled and still wifi working. Thank you

---

### Post by jeremy31 on 2020-09-05
tushar321 is using the kernel modules, not the ones from [https://ubuntuforums.org/showthread.php?t=2449277&p=13984036#post13984036](https://ubuntuforums.org/showthread.php?t=2449277&p=13984036#post13984036)

---

### Post by plasticdeveloper32 on 2020-09-05
Should i enable secureboot now, or there are some other troubleshoot ??

Or the new kernel module will not work on secure boot ??

---

### Post by jeremy31 on 2020-09-05
The new module will not load with Secure Boot enabled

---

### Post by plasticdeveloper32 on 2020-09-05
Ok Thank you for the support, i guess have to continue with legacy, will there be a proper solution with secure boot enabled later or sooner ?? or because its just me facing it will not get the solution ??

and what seems to be the issue, what that code does ??


> sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
echo "options rtl8723be ant_sel=2 ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf

---

### Post by jeremy31 on 2020-09-05
I am not a kernel developer, so I have no idea if or when the kernels might be fixed or what the actual issue with the kernel module is

That code disables wifi power management in the kernel module and prevents Network Manager from trying to enable it

---

### Post by plasticdeveloper32 on 2020-09-05
Before proceeding, its you taking the risk.

The fix is :

1. Disable Secure boot, check the status through this cmd: mokutil --sb-state
2. Download [this]("https://www.dropbox.com/s/yp9ap3022cmx9xb/rtlwifi_new.tar.gz") new kernel modules and install them by following this guide: [here]("https://medium.com/devstudio/how-to-install-wifi-driver-of-rtl8723be-in-ubuntu-18-04-1c031e2baf5")
3. Disable Wifi Power Management through this cmd:

> sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
echo "options rtl8723be ant_sel=2 ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf


4. Reboot.

Thank you @jeremy31 for the solution, for those who want to know what will happen after disabling the WiFi Power Management : 

WiFi will be keep on whole its in sleep,
Some users may face unstable performance with Power Management enabled, this will hope fix it,
and some Authentication issue fix which i faced.

---

### Post by tushar321 on 2020-09-05
what I have to do further , where my system is faulty any guess from the journalctl and wireless info results. :(

---

### Post by tushar321 on 2020-09-05
yesterday I tried this > To solve this today I opened up the laptop to swap the antenna wire  to(aux port/no.2) and to my surprise there is no second antenna port at  all given in wifi card. so all and all the antenna depends on just  single connection and this leaves no room to swap the antenna port.

---

### Post by tushar321 on 2020-09-05
plasticdeveloper32  I am glad that your system is working properly now thumbs up to you and all the contributors

---

### Post by plasticdeveloper32 on 2020-09-05
Don't know if this is a smart move or not, Boot a USB with Ubuntu 18.04 and dont perform a fresh intallation just try the Live Ubuntu and see if the error is still occurring or not.

---

### Post by tushar321 on 2020-09-05
Strange but even the live boot is not showing wireless option I tried both Linux mint and manjaro on boot up both didn't show wireless option. I think I have messed up with my wifi drivers here is new journalctl from ubuntu "when the wifi was trying to connect to the router" [https://pastebin.com/qBg0gjT5](https://pastebin.com/qBg0gjT5)

---

### Post by plasticdeveloper32 on 2020-09-05
did you try with mobile hotspot ?? could be router issue ?.

i also resetted the router and the security with WPA2/PSK

Also check if this option is on : Settings >> Privacy >> Connectivity Checking >> On

This is something causing the issue, i was having similar code too:

> [COLOR=#000000][FONT=Consolas]Sep 05 17:53:48 tushar-HP-15-Notebook-PC kernel: rtl8723be: Init MAC failed[/FONT][/COLOR]

---

### Post by tushar321 on 2020-09-05
yes I tried it but something fishy I am seeing in  journalctl txt I dont know in much detail but there were some red warnings everywhere hope some senior will clarify this. About router issue now I am thinking to change my ISP that's the only solution left.

---

### Post by tushar321 on 2020-09-05
jeremy31, chili55, can you please clarify what are the issues in wifi driver.

---

### Post by tushar321 on 2020-09-06
Hello jeremy31, 
> sudo tee /etc/modprobe.d/rtl8723be.conf <<< "options rtl8723be ips=N fwlps=N swenc=Y ant_sel=2"
Can I set fwlps and swenc parameter as shown above

---

### Post by jeremy31 on 2020-09-06
You can try it, the dev said a while back that if ips=N, then setting fwlps=N is redundant

---

### Post by tushar321 on 2020-09-06
what about swenc=Y

---

### Post by jeremy31 on 2020-09-06
Try it, reboot and see if there is any improvement

---

### Post by tushar321 on 2020-09-06
Didn't worked,
are there any driver conflicts going on in my system between the ones I have installed and the one came along with kernel updates like with this > sudo apt update
sudo apt install git dkms
git clone [https://github.com/lwfinger/rtw88.git](https://github.com/lwfinger/rtw88.git)
sudo dkms add ./rtw88
sudo dkms install rtlwifi-new/0.6
and  the kernel updates. 
Since yesterday also there were some kernel updates for me and I updated it.

---

### Post by jeremy31 on 2020-09-06
> **tushar321 said:**
> Didn't worked,
are there any driver conflicts going on in my system between the ones I have installed and the one came along with kernel updates like with this 
and  the kernel updates. 
Since yesterday also there were some kernel updates for me and I updated it.

[https://github.com/lwfinger/rtw88.git](https://github.com/lwfinger/rtw88.git) does not support your rtl8723be but it shouldn't cause issues

Run the script again and post results

---

### Post by plasticdeveloper32 on 2020-09-06
[IMG]https://i.imgur.com/vcOD6gu.png[/IMG]

Whole Journal raided with this ??

Script Log: [https://pastebin.com/QcyAXSuJ](https://pastebin.com/QcyAXSuJ)

---

### Post by tushar321 on 2020-09-07
modinfo rtl8723be presents 
> tushar@tushar-HP-15-Notebook-PC:~$ modinfo rtl8723be
filename:       /lib/modules/5.4.0-45-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw_36.bin
firmware:       rtlwifi/rtl8723befw.bin


do we require both rtlwifi/rtl8723befw_36.bin and rtlwifi/rtl8723befw.bin

---

### Post by plasticdeveloper32 on 2020-09-07
I also got some firmware error while installing ubuntu:

[IMG]https://i.imgur.com/kr76GB3.jpg[/IMG]

is @tushar321 right ?? do we need both .bin installed ?? Because my system missing them ??

---

### Post by plasticdeveloper32 on 2020-09-07
@tushar321

They are already under /lib/firmware/rtl_nic/

Seems not reproduce able.

---

### Post by tushar321 on 2020-09-08
@jeremy31 and @chili555 both the geeks can you suggest what are the things which were expected to work but are not available/missing in the system please suggest I am completely clueless why the wifi has stopped working suddenly. or should I start looking for some external adapters now

---

### Post by jeremy31 on 2020-09-08
I would have to dig out an antique laptop that has a rtl8723be with Mint 19 that I used to test some fixes a year or so ago and then find the charger for it

---

### Post by tushar321 on 2020-09-08
All right I am ready to contribute and cooperate to the fullest extent to get this done. I kindly request you to tell how shall we proceed from here onward.

---

### Post by tushar321 on 2020-09-09
Apart from this which USB adapter would you suggest I want to keep them as backup from now on. I even tried looking for tp link 722 model as suggested by you and chili in one of your post but its Version 1 is not available here after some good research about chipsets I came up with these. 

[https://www.amazon.in/CanaKit-Raspberry-Wireless-Adapter-Dongle/dp/B00GFAN498/ref=sr_1_1?dchild=1&keywords=canakit+wifi+adapter&qid=1599676414&sr=8-1](https://www.amazon.in/CanaKit-Raspberry-Wireless-Adapter-Dongle/dp/B00GFAN498/ref=sr_1_1?dchild=1&keywords=canakit+wifi+adapter&qid=1599676414&sr=8-1)

[URL="https://www.amazon.in/Panda-150Mbps-Wireless-N-2-4GHz-Adapter/dp/B003283M6Q/ref=sr_1_12?dchild=1&keywords=panda+150mbps&qid=1599676561&sr=8-12"]https://www.amazon.in/Panda-150Mbps-Wireless-N-2-4GHz-Adapter/dp/B003283M6Q/ref=sr_1_12?dchild=1&keywords=panda+150mbps&qid=1599676561&sr=8-12
[/URL]
[https://www.amazon.in/Leoxsys-150Mbps-Wireless-external-LEO-HG150N/dp/B00IWT1JA6/ref=sr_1_4?dchild=1&keywords=panda+150mbps&qid=1599676561&sr=8-4](https://www.amazon.in/Leoxsys-150Mbps-Wireless-external-LEO-HG150N/dp/B00IWT1JA6/ref=sr_1_4?dchild=1&keywords=panda+150mbps&qid=1599676561&sr=8-4)

---

### Post by tushar321 on 2020-09-10
I have opened up this issue on ask ubuntu as well.

---

### Post by plasticdeveloper32 on 2020-09-10
Also after buying a external WIFI Adapter TL-WN725N:

This error:

> <error> [1599772473.1513] wifi-wext: (wlxc025e91a001e): error setting powersave 0

---

### Post by jeremy31 on 2020-09-10
I fired up the old laptop with the rtl8723be chipset and it still had the old 4.15 kernel on it so I updated to the 5.4.0-47 and it seems that the ant_sel parameter needs to be set to 1 on this kernel where before we needed to set it to 2 with the kernel module, not the one from the github site as I haven't tested that yet

plasticdeveloper32, I am not sure where wifi-wext comes from but it might be outdated

---

### Post by plasticdeveloper32 on 2020-09-10
I ran the Software updates, every thing is updated. Will enabling secure boot will help ??

---

### Post by jeremy31 on 2020-09-10
plasticdeveloper32, post new wireless script results so I can see what the current situation is

---

### Post by plasticdeveloper32 on 2020-09-10
[https://pastebin.com/hPUgcDDN](https://pastebin.com/hPUgcDDN)


Wifi disconnects and when i turn off and turn on the adapter its up and running. IDK whats happening only on error in logs which i stated above.

Info related to Adapter: [https://www.dipolnet.com/wireless_usb_adapter_tp-link_tl-wn725n_nano_150mbps__N3222.htm](https://www.dipolnet.com/wireless_usb_adapter_tp-link_tl-wn725n_nano_150mbps__N3222.htm)

---

### Post by jeremy31 on 2020-09-10
Edit the /etc/modprobe.d/blacklist.conf to remove the blacklist rtl8723be and do
```
echo "options rtl8723be ips=N ant_sel=1" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Reboot
Also post result for ```
modinfo rtl8723be
```

---

### Post by plasticdeveloper32 on 2020-09-10
modinfo rtl8723be:

[https://pastebin.com/AbX9XrfM](https://pastebin.com/AbX9XrfM)

Also i have not installed the new kernel, this is the default kernel, shoud i install the kernel modules you provided ?? or want to test on default ones as you stated above you haven't tested.

---

### Post by jeremy31 on 2020-09-10
> **plasticdeveloper32 said:**
> modinfo rtl8723be:

[https://pastebin.com/AbX9XrfM](https://pastebin.com/AbX9XrfM)

Also i have not installed the new kernel, this is the default kernel.

I might have to test that kernel later and see if it needs the same antenna setting

---

### Post by tushar321 on 2020-09-11
@plasticdeveloper32 the WIFI adapter which you mentioned comes **Realtek chipset** and this chipset are bound to fail. I did some research on this for last to 2 days to know which WIFI adapter to buy and in that I found that most of the people are having issues with Realtek chipsets except 1 or 2 in Linux. I don't know why but this gives me strong feeling that Realtek chipset are the culprit. I am not sure how, but this same chipset don't have any issues in Windows its really interesting to know how they find workaround for this issue. I tried to buy Tp-link 722N but here the V2 is available **not V1**(as suggested by jeremy31 and chili555 in their post ) and V2 comes with Realtek chipset and I am scared to buy. As I mentioned after internet surfing I found those 3 WIFI adapter which found some what trustworthy as they have** Ralink Chipset,** **canakit** and **leoxsys** has **RT5370** and **Panda** has **RT3070** hope this works. jeremy31 and chili555 correct me if I am wrong anywhere since I also a beginner had I do not that vast exhaustive knowledge. Also whether it is good to buy those WIFI adapters.

---

### Post by plasticdeveloper32 on 2020-09-11
Correction it has Atheros chipset, i also did some research and then bought it. Where did you gather that info about Realtek Chipset for my adapter ??

Take a look: [Here]("https://www.dipolnet.com/wireless_usb_adapter_tp-link_tl-wn725n_nano_150mbps__N3222.htm")

But sticking to the topic after settting the ant_sel to 1 seems wifi is not disconnecting.


Edit: Yea there are some sources saying its realtek. The Atheros is for V1, i bought V2 with Realtek. Damn you realtek.

---

### Post by tushar321 on 2020-09-11
@plasticdeveloper32 "Damn you realtek" true indeed. yes I have seen that Tp-link model it was Realtek so cancelled it. if it would have been Atheros AR9271 in such low price then it would have been cherry on the top. About antenna selection 1 can you explain what you did.

---

### Post by jeremy31 on 2020-09-11
With the TP Link plugged in post results from terminal for ```
lsusb
```

---

### Post by tushar321 on 2020-09-11
@jeremy31 how should I proceed any commands for me

---

### Post by plasticdeveloper32 on 2020-09-11
OK so wifi got disconnect with the command jeremy provided, it worked for a while from last nigh till this noon and after waking up from sleep. Crashed

and about lsusb here:

[https://pastebin.com/3y3Nm58Z](https://pastebin.com/3y3Nm58Z)

Right now the internal module is facing the issue and i am connected with external adapter and reminder its default kernel for both internal and external adapters.

and heres the results of wireless script in your signature for more details.

[https://pastebin.com/fQDQwvV3](https://pastebin.com/fQDQwvV3)

---

### Post by plasticdeveloper32 on 2020-09-12
Nothing is working, new external adapter is facing issues too.

---

### Post by jeremy31 on 2020-09-12
Lets do a test on the ant_sel parameter setting
```
sudo rm /etc/modprobe.d/rtl8723be.conf
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be
iwlist scan | egrep -i 'ssid|signal'
sudo modprobe -r rtl8723be
sudo modprobertl8723be ant_sel=1
iwlist scan | egrep -i 'ssid|signal'
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=2
iwlist scan | egrep -i 'ssid|signal'
```
Post results

---

### Post by plasticdeveloper32 on 2020-09-12
[https://pastebin.com/0qJENvZp](https://pastebin.com/0qJENvZp)

is the whole game is with ant_sel ??

---

### Post by jeremy31 on 2020-09-12
Run the commands again with the USB unplugged, I fixed a typo in the commands on the other post.
I checked my old laptop with the rtl8723be with only one antenna wire connected and I had better results with that 4.5.0-117 using ant_sel=2 when in the 5.4 kernel I had to use 1 

I also use a USB adapter with the same ID as your TP Link but mine doesn't have an external antenna and it works ok on the 5.4 kernels.  I think mine is the 725N

---

### Post by plasticdeveloper32 on 2020-09-12
How to confirm that when i reboot the  laptop the internal module is loaded with ant 1 ??

> echo "options rtl8723be ips=N ant_sel=1" | sudo tee /etc/modprobe.d/rtl8723be.conf

I also experience better with ant 1.

---

### Post by jeremy31 on 2020-09-12
You can check ```
cat /sys/module/rtl8723be/parameters/ant_sel
```
to see what it is after a reboot

---

### Post by plasticdeveloper32 on 2020-09-12
when i do uname-r :

it shows this kernel 4.15.0-117-generic as you said you used ant 1 when it was kernel 5.4.

How do i update it ?? or everything is OK i am misunderstanding things

---

### Post by jeremy31 on 2020-09-12
If 1 gives you a better signal in the kernel you want to use, set it to that as I cannot be sure that my antenna is connected to the same one as what HP uses.  Another thing to do is have a terminal open all the time, run ```
tail -f /var/log/syslog
```
When wifi has an issue, check that terminal to see if any relevant errors are there, you can use CTRL + c to stop that in terminal

---

### Post by tushar321 on 2020-09-13
Since I have dual boot of Ubuntu and Mint so yesterday in Ubuntu I had  set the ant=1 and IPS=N as discussed in earlier post and the WIFI  started getting signal but very weak then set it to 2 and then there was  no signal at all the airplane mode became on again I set with 1. After  that I booted into Mint and the signal was strong enough to download  videos as well. Then I did live boot of Manjaro and Zorin OS as well and  the WIFI signals were strong I found a pattern in them except in Ubuntu  everywhere else signal were strong. I checked the the etc/modprobe.d  folder of all other OS there was no "rtl8723be.conf" file but only in  Ubuntu etc/modprobe.d folder the file was present. I deleted that file  and rebooted in Ubuntu the signal became as strong as it was in all  other OS. So setting no parameter at all the the signal is strong I even  turned on the power management so far everything is working normal.  Plasticdeveloper32 you do check it once with same configuration. I  request jeremy31 to check it and make this confirm that is it really the  thing that setting no param in rtl8723be.conf for RTL8723be card works.  I even want to ask is there anyway so that signal strength can be  checked thoroughly.

---

### Post by jeremy31 on 2020-09-13
There isn't a default rtl8723be.conf in Ubuntu or Mint that I know of.  You do want to check
```
cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
you want to see that setting at 2 and not 3 as that keeps Network manager from enabling wifi power management.  You could also do ```
echo "options rtl8723 fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl-power-off.conf
```
So that the power management settings in the driver are in a different file than where you set the ant_sel

The default setting for ant_sel is 0 and that doesn't always work with HP laptops with one antenna

---

### Post by plasticdeveloper32 on 2020-09-13
@tushar321 seems like the wifi is not dropping or not disconnecting after sleep strange though cuz its the ant_sel is set to default(0) and power management ON means we are back to square one.

Any explanation or magic ?? Still under testing phase.

Because it used to happen any time as its intermittent.

If error will happen will set ant_sel to 1 and ask jeremy to tell me how to not disconnect when i put my machine on sleep, becuase after settings Power management to off it seems it still disconnect and connects again when awake from sleep.

---

### Post by plasticdeveloper32 on 2020-09-14
Nah doesn't work with tushar dianostics. But the thing is wifi is not dropping it cannot construct wifi signal see: (infinite loading) only fixes after restart

[IMG]https://i.imgur.com/S3hwl6D.png[/IMG]

and logs are:

[IMG]https://i.imgur.com/AufaOJd.png[/IMG]

Doesnt matter which ant_sel i set or disable power managements, wifi signals are good there something fishy in some other area.

---

### Post by tushar321 on 2020-09-14
"it cannot construct wifi signal" something here to look into

---

### Post by tushar321 on 2020-09-17
plasticdeveloper32 any improvement

---

### Post by plasticdeveloper32 on 2020-09-17
Nah man, nothing.

Why my module keeps disconnecting and connect when my laptop awake from sleep. i have disabled power management still ??

---

### Post by plasticdeveloper32 on 2020-09-20
Ok so wifi is not disconnecting but is facing issues when waking up from sleep. Solution is turn off the module and turn back on.

The settings are on default:

ant_sel=0
secure boot disable
Power managment off
no config file in the modprobe folder

tushar said to delete the conf file and seams this also helped.
Now how to avoid wifi module to not go to sleep when laptop is in sleep status

---

### Post by tushar321 on 2020-09-20
I found this link where this guy got his problem solved [URL="https://bbs.archlinux.org/viewtopic.php?id=239025"]https://bbs.archlinux.org/viewtopic.php?id=239025 
[/URL]the last post where he mentions about openresolv but I have no idea what it is 
Jeremy, chilli you can look into this

---

