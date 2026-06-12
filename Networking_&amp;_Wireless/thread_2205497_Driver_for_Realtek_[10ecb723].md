---
title: "Driver for Realtek [10ec:b723]"
date: 2014-02-14
forum: Networking &amp; Wireless
---

### Post by hyunil227 on 2014-02-14
Hi all,

I just bought a new laptop, and installed Ubuntu. Everything works well except the Wireless network card.
Since I am new to setting up hardware drivers not provided by default, your help is very much appreciated.

```
lscpi -nn | grep 0280
```

gives me

```
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:b723]
```

Any idea where / how I can install the right driver for this specific device and get elegantly connected without Ethernet cable hanging around?

Much is appreciated.

From Seoul, with Love.

---

### Post by westie457 on 2014-02-14
Welcome to UF.

You have a relatively new chip that is not currently fully supported.

Try the first answer provided at this link. [http://askubuntu.com/questions/389268/no-wifi-connection-on-ubuntu-13-10](http://askubuntu.com/questions/389268/no-wifi-connection-on-ubuntu-13-10)

---

### Post by hyunil227 on 2014-02-14
Thank you for a warm welcome.

Yes indeed the laptop is quite new and I wasn't exactly expecting everything to work out of the box.
I will try the solution in the link and post the result after.

Appreciate your help a lot.

Cheers.

---

### Post by hyunil227 on 2014-02-14
> **westie457 said:**
> Welcome to UF.

You have a relatively new chip that is not currently fully supported.

Try the first answer provided at this link. [http://askubuntu.com/questions/389268/no-wifi-connection-on-ubuntu-13-10](http://askubuntu.com/questions/389268/no-wifi-connection-on-ubuntu-13-10)

Running make command gave me following errors:

```
make -C /lib/modules/3.11.0-12-generic/build M=/home/tony/rtl8723be modules
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-12-generic'
  CC [M]  /home/tony/rtl8723be/regd.o
In file included from /home/tony/rtl8723be/regd.c:31:0:
/home/tony/rtl8723be/regd.c: In function ‘_rtl_reg_apply_beaconing_flags’:
/home/tony/rtl8723be/regd.h:37:32: error: ‘IEEE80211_CHAN_NO_IR’ undeclared (first use in this function)
 #define IEEE80211_CHAN_NO_IBSS IEEE80211_CHAN_NO_IR
                                ^
/home/tony/rtl8723be/regd.c:200:20: note: in expansion of macro ‘IEEE80211_CHAN_NO_IBSS’
      ch->flags &= ~IEEE80211_CHAN_NO_IBSS;
                    ^
/home/tony/rtl8723be/regd.h:37:32: note: each undeclared identifier is reported only once for each function it appears in
 #define IEEE80211_CHAN_NO_IBSS IEEE80211_CHAN_NO_IR
                                ^
/home/tony/rtl8723be/regd.c:200:20: note: in expansion of macro ‘IEEE80211_CHAN_NO_IBSS’
      ch->flags &= ~IEEE80211_CHAN_NO_IBSS;
                    ^
/home/tony/rtl8723be/regd.c: In function ‘_rtl_reg_apply_active_scan_flags’:
/home/tony/rtl8723be/regd.h:34:37: error: ‘IEEE80211_CHAN_NO_IR’ undeclared (first use in this function)
 #define IEEE80211_CHAN_PASSIVE_SCAN IEEE80211_CHAN_NO_IR
                                     ^
/home/tony/rtl8723be/regd.c:237:19: note: in expansion of macro ‘IEEE80211_CHAN_PASSIVE_SCAN’
   if (ch->flags & IEEE80211_CHAN_PASSIVE_SCAN)
                   ^
/home/tony/rtl8723be/regd.c: In function ‘_rtl_reg_apply_radar_flags’:
/home/tony/rtl8723be/regd.h:37:32: error: ‘IEEE80211_CHAN_NO_IR’ undeclared (first use in this function)
 #define IEEE80211_CHAN_NO_IBSS IEEE80211_CHAN_NO_IR
                                ^
/home/tony/rtl8723be/regd.c:312:8: note: in expansion of macro ‘IEEE80211_CHAN_NO_IBSS’
        IEEE80211_CHAN_NO_IBSS |
        ^
/home/tony/rtl8723be/regd.c: In function ‘_rtl_regd_init_wiphy’:
/home/tony/rtl8723be/regd.h:40:38: error: ‘REGULATORY_CUSTOM_REG’ undeclared (first use in this function)
 #define WIPHY_FLAG_CUSTOM_REGULATORY REGULATORY_CUSTOM_REG
                                      ^
/home/tony/rtl8723be/regd.c:410:18: note: in expansion of macro ‘WIPHY_FLAG_CUSTOM_REGULATORY’
  wiphy->flags |= WIPHY_FLAG_CUSTOM_REGULATORY;
                  ^
/home/tony/rtl8723be/regd.h:43:38: error: ‘REGULATORY_STRICT_REG’ undeclared (first use in this function)
 #define WIPHY_FLAG_STRICT_REGULATORY REGULATORY_STRICT_REG
                                      ^
/home/tony/rtl8723be/regd.c:411:19: note: in expansion of macro ‘WIPHY_FLAG_STRICT_REGULATORY’
  wiphy->flags &= ~WIPHY_FLAG_STRICT_REGULATORY;
                   ^
/home/tony/rtl8723be/regd.h:46:41: error: ‘REGULATORYks!_DISABLE_BEACON_HINTS’ undeclared (first use in this function)
 #define WIPHY_FLAG_DISABLE_BEACON_HINTS REGULATORY_DISABLE_BEACON_HINTS
                                         ^
/home/tony/rtl8723be/regd.c:412:19: note: in expansion of macro ‘WIPHY_FLAG_DISABLE_BEACON_HINTS’
  wiphy->flags &= ~WIPHY_FLAG_DISABLE_BEACON_HINTS;

```

Any idea what I should do to make this work?

Thanks!

---

### Post by chili555 on 2014-02-14
Sorry to barge in, but this is what I think happened. Please check here: [https://github.com/lwfinger/rtl8723be](https://github.com/lwfinger/rtl8723be)

Please notice that several files were modified 9 days ago: 'rtl8723be: Modify for API changes in kernel 3.14' You are using a 3.11-xx kernel, so it won't compile properly; 10 days ago, it did. I am trying to work out a solution.

I have emailed the author.

---

### Post by hyunil227 on 2014-02-14
Ouch that hurts. Please let me know if there's any updates.

Cheers!

> **chili555 said:**
> Sorry to barge in, but this is what I think happened. Please check here: [https://github.com/lwfinger/rtl8723be](https://github.com/lwfinger/rtl8723be)

Please notice that several files were modified 9 days ago: 'rtl8723be: Modify for API changes in kernel 3.14' You are using a 3.11-xx kernel, so it won't compile properly; 10 days ago, it did. I am trying to work out a solution.

I have emailed the author.

---

### Post by hyunil227 on 2014-02-15
> **chili555 said:**
> Sorry to barge in, but this is what I think happened. Please check here: [https://github.com/lwfinger/rtl8723be](https://github.com/lwfinger/rtl8723be)

Please notice that several files were modified 9 days ago: 'rtl8723be: Modify for API changes in kernel 3.14' You are using a 3.11-xx kernel, so it won't compile properly; 10 days ago, it did. I am trying to work out a solution.

I have emailed the author.

Checking out the earlier version by

```
git checkout 604aa9058fb9e5bb1cf571c99989d081f8fc8b9
```

has solved the problem. It's a git repository afterall. ;)

---

### Post by chili555 on 2014-02-15
> **hyunil227 said:**
> Checking out the earlier version by

```
git checkout 604aa9058fb9e5bb1cf571c99989d081f8fc8b9
```

has solved the problem. It's a git repository afterall. ;)Wow! Awesome. Glad it's working. 

Just for the benefit of the searchers out there, would you please tell us in detail the process to git the older version?

---

### Post by hyunil227 on 2014-02-16
> **chili555 said:**
> Wow! Awesome. Glad it's working. 

Just for the benefit of the searchers out there, would you please tell us in detail the process to git the older version?

Of course. Git is a Version Control System, meaning every single version of the source code can be retrieved when needed.
The checkout method described in the solution you've linked basically is a command to pull the latest code from the repository.
I just added one more line to that.

```

sudo apt-get install linux-headers-generic build-essential git
git clone http://github.com/lwfinger/rtl8723be
cd rtl8723be
git checkout [COLOR=#000000][FONT=Ubuntu Mono]604aa9058fb9e5bb1cf571c99989d081f8fc8b9[/FONT][/COLOR]
make
sudo make install
sudo modprobe rtl8723be

```[COLOR=#222222][FONT=Verdana]

And that's about it![/FONT][/COLOR]

---

### Post by hyunil227 on 2014-02-16
I was actually able to get the Wireless Card working, but since my laptop is very new to the market, so many of the parts inside are missing drivers.
For example, the touchpad. Therefore I guess I am kind of stuck with Windows for now, until there are drivers available for these parts. :(

---

### Post by chili555 on 2014-02-16
> **hyunil227 said:**
> I was actually able to get the Wireless Card working, but since my laptop is very new to the market, so many of the parts inside are missing drivers.
For example, the touchpad. Therefore I guess I am kind of stuck with Windows for now, until there are drivers available for these parts. :(First of all:> git checout 604aa9058fb9e5bb1cf571c99989d081f8fc8b9I believe it is chec[COLOR="#FF0000"]k[/COLOR]out. I suggest you edit your post above for which we thank you. > For example, the touchpad. Therefore I guess I am kind of stuck with Windows for now, until there are drivers available for these parts. There may well be, however I am not the person to ask. I suggest you search and then ask over here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

### Post by hyunil227 on 2014-02-16
> **chili555 said:**
> First of all:I believe it is chec[COLOR=#FF0000]k[/COLOR]out. I suggest you edit your post above for which we thank you. There may well be, however I am not the person to ask. I suggest you search and then ask over here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

Done the editing. Thanks for the heads up!

---

### Post by themaninthewoods on 2014-04-28
I had this same problem with on a new computer with 14.04 Trusty Tahr installed on it and this solution worked.  I also had to checkout the older version of the driver to get it working.

Unfortunately the wireless will stop working periodically.  The only way to fix is a reboot.  I've tried ```
sudo modprobe -r rtl8723be
``` and then ```
sudo modprobe rtl8723be
``` as this worked for someone else with a similar problem, but it doesn't work for me.

Any ideas?

---

### Post by eduardo14 on 2014-05-14
> **hyunil227 said:**
> Of course. Git is a Version Control System, meaning every single version of the source code can be retrieved when needed.
The checkout method described in the solution you've linked basically is a command to pull the latest code from the repository.
I just added one more line to that.

```

sudo apt-get install linux-headers-generic build-essential git
git clone http://github.com/lwfinger/rtl8723be
cd rtl8723be
git checkout [COLOR=#000000][FONT=Ubuntu Mono]604aa9058fb9e5bb1cf571c99989d081f8fc8b9[/FONT][/COLOR]
make
sudo make install
sudo modprobe rtl8723be

```[COLOR=#222222][FONT=Verdana]

And that's about it![/FONT][/COLOR]


I tried this but after i type the 'git clone' line a request for username/password comes up from github.
I went and registered there and verified my email.
After i input my username and password i get:

error: the requested URL returned error: 403 while accessing [http://github.com/lwfinguer/rtl8723be/info/refs](http://github.com/lwfinguer/rtl8723be/info/refs)
fatal: HTTP request failed

any ideas?

i also went directly to [http://github.com/lwfinger/rtl8723be](http://github.com/lwfinger/rtl8723be) and downloaded the files.
Then I navigated to the folder and used the 'make' command suggested. But when i tried the following 'sudo make install' command i got a 'not found' error. And now I'm stuck there too.

Any advice on how to get past these 2 roadblocks would be greatly appreciated. Or other possible solutions to the issue.

---

### Post by chili555 on 2014-05-14
> after i type the 'git clone' line a request for username/password comes up from github.Please show us. Here is what I get and what is ordinarily expected:```
chili@T410:~$ git clone http://github.com/lwfinger/rtl8723be
Cloning into 'rtl8723be'...
remote: Reusing existing pack: 84, done.
remote: Total 84 (delta 0), reused 0 (delta 0)
Unpacking objects: 100% (84/84), done.
Checking connectivity... done.

```

---

### Post by eduardo14 on 2014-05-15
Well... I tried it again so I could copy my error as you requested. Except this time it actually worked with no problem and my wifi is working now. So thanks! haha :)

---

### Post by chili555 on 2014-05-15
> **eduardo14 said:**
> Well... I tried it again so I could copy my error as you requested. Except this time it actually worked with no problem and my wifi is working now. So thanks! haha :)Awesome! Glad it's working. I'm sure that a threat to call Dr. Chili was persuasive to git!

---

### Post by freechelmi on 2014-05-28
Hi I'm not sure I understand the status of the Wifi card on Lastest trusty.

Kernel 3.13-27.50 in trusty seems to have the necessary backport from utopic to support this card however it's not load at all.

When compiling the driver for 3.13 the connection is unstable .

Do we have a page that sumup how to make it work on trusty ? I guess this will be impossible in precise ?

---

### Post by chili555 on 2014-05-28
> Kernel 3.13-27.50 in trusty seems to have the necessary backport from utopic to support this card What is utopic? What do you see in the kernel that helps?

---

### Post by gilbertstuart on 2014-06-22
I got my wireless card to work continously by preventing auto sleep (look at the last step), in summary this are the steps I followed in a terminal (minus the hashtag comments):

```
[COLOR=#000000][FONT=Arial]sudo apt-get install linux-headers-generic build-essential git[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    # needed only if you don't have yet that package[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]git clone[/FONT][/COLOR][COLOR=#1155cc]_[http://github.com/lwfinger/rtl8723be](http://github.com/lwfinger/rtl8723be)_[/COLOR]
[COLOR=#000000][FONT=Arial]    # needed only if you don't have yet downloaded rtl8723be[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]cd rtl8723be[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]git checkout 604aa9058fb9e5bb1cf571c99989d081f8fc8b9[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] # because of older kernel issues[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]make clean[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]make[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo make install[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo modprobe rtl8723be[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]echo "options rtl8723be fwlps=0" | sudo tee /etc/modprobe.d/rtl8723be.conf[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]   # Prevents the WiFi card from automatically sleeping and halting connection[/FONT][/COLOR]
```



from:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1320070](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1320070)    post # 29

related post:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1240940](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1240940)

I'm on a clevo W740SU / Sager NP2740 / Galago UltraPro with rtl8723be wireless card Ubuntu 14.04 64bit

---

### Post by chili555 on 2014-06-22
Thanks for the tip! I am certain you've helped quite a few searchers.

---

### Post by svm2 on 2014-12-28
```

sudo apt-get install linux-headers-generic build-essential git
git clone http://github.com/lwfinger/rtl8723be
cd rtl8723be
git checkout [COLOR=#000000][FONT=Ubuntu Mono]604aa9058fb9e5bb1cf571c99989d081f8fc8b9[/FONT][/COLOR]
make
sudo make install
sudo modprobe rtl8723be

```[COLOR=#222222][FONT=Verdana]
[/FONT][/COLOR]
After all, we must add this : 
```
sudo update-grub
```
Without it, I got : Kernel panic

---

### Post by bruns-jeremy on 2015-02-11
> **hyunil227 said:**
> I was actually able to get the Wireless Card working, but since my laptop is very new to the market, so many of the parts inside are missing drivers.
For example, the touchpad. Therefore I guess I am kind of stuck with Windows for now, until there are drivers available for these parts. :(

Hey if u have an elantech touchpad check out this:
 [http://www.evilcodingmonkey.com/2014/01/23/ubuntu-activate-multi-touch-on-elantech/](http://www.evilcodingmonkey.com/2014/01/23/ubuntu-activate-multi-touch-on-elantech/)

Thx for the wifi card tips works now.
Preventing auto sleep did the trick for me.
This is also good:
[http://forum.ubuntuusers.de/topic/kein-internet-seit-ubuntu-13-10-auf-lenovo-b54/#post-6266182](http://forum.ubuntuusers.de/topic/kein-internet-seit-ubuntu-13-10-auf-lenovo-b54/#post-6266182)

My laptop is an Lenovo Y50-70 Ubuntu 14.04

---

### Post by tencars2 on 2015-02-17
Hello,
I have the same wlan-adapter (rtl8723be). I followed the described steps (install git, checkout, make install, modprobe).
All steps run without errors and the wlan-adapter (rtl8723be) is now recognized as 'wlan1'.
Still I can't connect to my wlan-router (avm fritz-box 7270). 
Connecting with a wlan-usb-stick to the same wlan-router is possible without problems.

Any idea why the rtl8723be does not connect to wlan-router?

---

### Post by serdar132 on 2015-05-06
Hello there,
After many years I am back in the community. Actually not for myself, but for my mom. We bought a new laptop for her, and I tought she could use Ubuntu now it is much more user friendly and easy to use. Everything look good until we have this problem. Anyways, long story short, when I use the codes given below, I have 2 errors :

gonul@gonul-Lenovo-B50-30:~/rtl8723be$ make
make -C /lib/modules/3.16.0-37-generic/build M=/home/gonul/rtl8723be modules
make[1]:`/usr/src/linux-headers-3.16.0-37-generic' dizinine giriliyor
  CC [M]  /home/gonul/rtl8723be/base.o
/home/gonul/rtl8723be/base.c: In function ‘_rtl_init_mac80211’:
/home/gonul/rtl8723be/base.c:368:4: error: ‘struct ieee80211_hw’ has no member named ‘channel_change_time’
  hw->channel_change_time = 100;
    ^
/home/gonul/rtl8723be/base.c: In function ‘rtl_beacon_statistic’:
/home/gonul/rtl8723be/base.c:1180:2: error: implicit declaration of function ‘compare_ether_addr’ [-Werror=implicit-function-declaration]
  if (compare_ether_addr(hdr->addr3, rtlpriv->mac80211.bssid))
  ^
cc1: some warnings being treated as errors
make[2]: *** [/home/gonul/rtl8723be/base.o] Hata 1
make[1]: *** [_module_/home/gonul/rtl8723be] Hata 2
make[1]: `/usr/src/linux-headers-3.16.0-37-generic' dizininden ç&#305;k&#305;l&#305;yor
make: *** [all] Hata 2
gonul@gonul-Lenovo-B50-30:~/rtl8723be$ sudo make install
make -C /lib/modules/3.16.0-37-generic/build M=/home/gonul/rtl8723be modules
make[1]:`/usr/src/linux-headers-3.16.0-37-generic' dizinine giriliyor
  CC [M]  /home/gonul/rtl8723be/base.o
/home/gonul/rtl8723be/base.c: In function ‘_rtl_init_mac80211’:
/home/gonul/rtl8723be/base.c:368:4: error: ‘struct ieee80211_hw’ has no member named ‘channel_change_time’
  hw->channel_change_time = 100;
    ^
/home/gonul/rtl8723be/base.c: In function ‘rtl_beacon_statistic’:
/home/gonul/rtl8723be/base.c:1180:2: error: implicit declaration of function ‘compare_ether_addr’ [-Werror=implicit-function-declaration]
  if (compare_ether_addr(hdr->addr3, rtlpriv->mac80211.bssid))
  ^
cc1: some warnings being treated as errors
make[2]: *** [/home/gonul/rtl8723be/base.o] Hata 1
make[1]: *** [_module_/home/gonul/rtl8723be] Hata 2
make[1]: `/usr/src/linux-headers-3.16.0-37-generic' dizininden ç&#305;k&#305;l&#305;yor
make: *** [all] Hata 2
gonul@gonul-Lenovo-B50-30:~/rtl8723be$ sudo modprobe rtl8723be
gonul@gonul-Lenovo-B50-30:~/rtl8723be$ echo "options rtl8723be fwlps=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
options rtl8723be fwlps=0



I know it is Turkish, but I am not sure if this would be any problem for you guys to understand whats going on with the wireless card

Thank you very much

---

### Post by chili555 on 2015-05-06
> After many years I am back in the community.Welcome back! We're glad to see you.> make: *** [all] Hata 2This translates, in English, to 'make: ***[all]Error 2.'  For your benefit, as well as the searchers out there, when you see that, it means, in plainer words, 'STOP! All further steps will also be errors, don't waste any more key strokes nor CPU cycles.'

Please try this instead, with a working internet connection:```
git clone https://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
sudo make install 
```Reboot and tell us how delighted Mom is with her wireless. I will have one more step.

---

### Post by Eugenio_Cunha on 2015-06-15
> **hyunil227 said:**
> Of course. Git is a Version Control System, meaning every single version of the source code can be retrieved when needed.
The checkout method described in the solution you've linked basically is a command to pull the latest code from the repository.
I just added one more line to that.

```

sudo apt-get install linux-headers-generic build-essential git
git clone http://github.com/lwfinger/rtl8723be
cd rtl8723be
git checkout [COLOR=#000000][FONT=Ubuntu Mono]604aa9058fb9e5bb1cf571c99989d081f8fc8b9[/FONT][/COLOR]
make
sudo make install
sudo modprobe rtl8723be

```[COLOR=#222222][FONT=Verdana]

And that's about it![/FONT][/COLOR]


It Works! with ubuntu 12.04.  Thanks for help.

---

### Post by Jayakrishnan_Menon on 2016-03-27
> **hyunil227 said:**
> Of course. Git is a Version Control System, meaning every single version of the source code can be retrieved when needed.
The checkout method described in the solution you've linked basically is a command to pull the latest code from the repository.
I just added one more line to that.

```

sudo apt-get install linux-headers-generic build-essential git
git clone http://github.com/lwfinger/rtl8723be
cd rtl8723be
git checkout [COLOR=#000000][FONT=Ubuntu Mono]604aa9058fb9e5bb1cf571c99989d081f8fc8b9[/FONT][/COLOR]
make
sudo make install
sudo modprobe rtl8723be

```[COLOR=#222222][FONT=Verdana]

And that's about it![/FONT][/COLOR]


When i run make ,, i get the following error .

make -C /lib/modules/4.2.3-040203-generic/build M=/home/user/rtl8723be modules
make[1]: Entering directory `/usr/src/linux-headers-4.2.3-040203-generic'
  CC [M]  /home/user/rtl8723be/base.o
/home/user/rtl8723be/base.c: In function ‘_rtl_init_mac80211’:
/home/user/rtl8723be/base.c:321:12: error: incompatible types when assigning to type ‘long unsigned int[1]’ from type ‘int’
  hw->flags = IEEE80211_HW_SIGNAL_DBM |
            ^
/home/user/rtl8723be/base.c:334:13: error: invalid operands to binary | (have ‘long unsigned int[1]’ and ‘int’)
   hw->flags |= IEEE80211_HW_SUPPORTS_PS |
             ^
/home/user/rtl8723be/base.c:368:4: error: ‘struct ieee80211_hw’ has no member named ‘channel_change_time’
  hw->channel_change_time = 100;
    ^
/home/user/rtl8723be/base.c: In function ‘rtl_beacon_statistic’:
/home/user/rtl8723be/base.c:1180:2: error: implicit declaration of function ‘compare_ether_addr’ [-Werror=implicit-function-declaration]
  if (compare_ether_addr(hdr->addr3, rtlpriv->mac80211.bssid))
  ^
/home/user/rtl8723be/base.c: In function ‘rtl_store_debug_level’:
/home/user/rtl8723be/base.c:1714:2: error: implicit declaration of function ‘strict_strtoul’ [-Werror=implicit-function-declaration]
  ret = strict_strtoul(buf, 0, &val);
  ^
cc1: some warnings being treated as errors
make[2]: *** [/home/user/rtl8723be/base.o] Error 1
make[1]: *** [_module_/home/user/rtl8723be] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-4.2.3-040203-generic'
make: *** [all] Error 2


HOw can i fix this ??

---

### Post by Hadaka on 2016-03-27
Hi. you are posting and using a thread thats 2 years old
is probably why it isnt working,you really should have started your own thread.
here is an up to date working method for your driver rtl8723be. If for some reason
you still have problems please start a new thread and mention that you tried this link.
[http://askubuntu.com/questions/71768.../722904#722904]("http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904")
you should not have any problems with this.
thanks

---

### Post by chili555 on 2016-03-27
Also, the driver rtl8723be already exists in your kernel version 4.2.3-040203-generic. There is no reason to compile a two-year-old driver to solve a problem. When you start your own new thread, please tell us what your issue is that you are trying to correct. Chances are, we have heard of it and can recommend a better solution.

---

### Post by agsrivaths on 2016-07-21
This really helped me to install Ubuntu and connect WLAN in HP Laptop HP 15-BA025AU which came without OS. Thank you.

---

### Post by DuckHook on 2016-07-21
Most of the solutions in this thread are now outdated and the instructions rendered obsolete.

If you have further questions, please start a new thread.

*Thread Closed.*

---

