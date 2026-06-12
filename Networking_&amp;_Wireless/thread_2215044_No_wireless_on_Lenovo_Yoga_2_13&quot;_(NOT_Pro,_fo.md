---
title: "No wireless on Lenovo Yoga 2 13&quot; (NOT Pro, for once!)"
date: 2014-04-04
forum: Networking &amp; Wireless
---

### Post by yangmusa on 2014-04-04
I've seen a lot of people with the Yoga 2 Pro seeking help here, but for some reason the solution (blacklist ideapad_laptop) doesn't work on my Yoga 2 non-Pro - even though as far as I can tell it has the same wireless card. I'm running 14.04 Beta 2, maybe that's it?

Some of the suggestions I've tried: 
[LIST]
[*]blacklisted ideapad_laptop
[*]reset BIOS to default
[*]removed battery and pressed power button for at least 30 seconds
[/LIST]

Here are the outputs of commands that are usually requested:

**uname -a**
Linux Lenovo-Yoga-2-13 3.13.0-20-generic #42-Ubuntu SMP Fri Mar 28 09:56:33 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

**dmesg | grep iwl**
[   10.436518] iwlwifi 0000:01:00.0: irq 61 for MSI/MSI-X
[   10.721909] iwlwifi 0000:01:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[   10.736824] iwlwifi 0000:01:00.0: Detected Intel(R) Wireless N 7260, REV=0x144
[   10.736882] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
[   10.737092] iwlwifi 0000:01:00.0: RF_KILL bit toggled to disable radio.
[   10.737113] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
[   10.750553] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'

**lsmod | grep iwl**
iwlmvm                189774  0 
mac80211              626489  1 iwlmvm
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm

**rfkill list all**
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

Any suggestions much appreciated!

Starting to seriously wish I hadn't blitzed the Windows install so I could return this laptop and get the Pro! I was going to put in a spare ssd, but it turns out Lenovo have used Western Digital's proprietary mini-SATA connector :-(

---

### Post by chili555 on 2014-04-04
Is it ideapad_laptop that needs blacklisting or ideapad_wlan? What's loading now?```
lsmod | grep -e idea -e wmi
```[http://ubuntuforums.org/showthread.php?t=2212048](http://ubuntuforums.org/showthread.php?t=2212048)> 

---

### Post by yangmusa on 2014-04-04
It doesn't look like ideapad_wlan is loading. 

**lsmod | grep -e idea -e wmi**
snd_rawmidi            30144  1 snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd                    69238  11 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi

---

### Post by yangmusa on 2014-04-05
So, nobody has any other ideas? I'm still stuck without wifi.. 

One of my colleagues used to work at Best Buy and thought they wouldn't care if the laptop had Linux on it. Well, it turns out he was wrong, they refused to take the laptop back. Now I have 1 week to either work out the wireless problem on Ubuntu, or to find a Windows install disk and try to return the Yoga to factory settings. Very disappointing that the Yoga 2 and the Yoga 2 Pro don't share the same networking hardware, and strange that nobody else has reported the wifi problem with the non-pro version. Of course it's my own fault for rashly nuking the Windows install, I know that... :-(

---

### Post by maucu on 2014-04-06
Some other people seem to have faced the same problem:
[https://forums.lenovo.com/t5/Linux-Discussion/Yoga-2-13-not-Pro-Linux-Warning/m-p/1491698](https://forums.lenovo.com/t5/Linux-Discussion/Yoga-2-13-not-Pro-Linux-Warning/m-p/1491698)
[https://forums.lenovo.com/t5/Idea-Windows-based-Tablets-and/Yoga-2-13-non-pro-wifi-always-off/td-p/1497482](https://forums.lenovo.com/t5/Idea-Windows-based-Tablets-and/Yoga-2-13-non-pro-wifi-always-off/td-p/1497482)

I wonder if yoga_laptop kernel module helps:
[https://github.com/pfps/yoga-laptop](https://github.com/pfps/yoga-laptop)

There's a comment in its README that it does not setup any physical RF kill switches.

---

### Post by chili555 on 2014-04-06
@yangmusa--

If you'd like to compile this and would like some guidance, please post back.

Thank you for a great find, jukka-partanen!

---

### Post by yangmusa on 2014-04-06
@[**[COLOR=#000000]jukka-partanen[/COLOR]**]("http://ubuntuforums.org/member.php?u=1915234") - thanks for the tip about yoga_laptop, that looks promising (and the links with warnings about the Yoga 2 non-Pro. Boy, I wish I'd seen those before getting into this... The forums are flooded with info about the *Pro*, so it's hard to find stuff about the non-Pro!)

@[**[COLOR=#000000]chili555[/COLOR]**]("http://ubuntuforums.org/member.php?u=35909") - thanks for the offer, yes I would appreciate a pointer or two. I haven't done anything quite like this before.

---

### Post by chili555 on 2014-04-06
Please get a temporary wired ethernet connection. You can safely copy and paste these commands to the terminal:```
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/pfps/yoga-laptop.git
cd yoga-laptop/yoga_laptop
```Note that it both looks funny and is correct! ```
make
sudo make install
sudo modprobe ideapad-laptop
```Now does it work as expected? If so, we'll have a bit of housekeeping to do, so don't cry yippee and go away just yet.

-------------

Reference from README:> Airplane Mode (F7) produces ACPI Notify 0x2000, which is correctly handled
by the ideapad_laptop module.  The Novo button on the side produces ACPI
Notify 0x0008, which is reasonably handled by the ideapad_laptop module.
ACPI Notify 0x0040 is done during lid close when AC power is connected (and
sometimes when it is not).  The ideapad_laptop module handles this
reasonably.  [COLOR="#FF0000"][I]However, ideapad_laptop assumes that the laptop has an RF kill
switch and breaks WiFi on Yogas.  There is a patched version of
ideapad_laptop in the yoga_laptop directory.[/I][/COLOR]

---

### Post by yangmusa on 2014-04-07
I followed the instructions and inserted the new ideapad-laptop. Didn't make a difference, but it occurred to me that since the problem happens during boot it might help to unblacklist the ideapad_laptop module and reboot - didn't make any difference. Do we need to do any housekeeping to undo this test, or can it be left as is?

I also noticed from looking at the output of **dmesg | grep iwl** that the firmware version of the Intel 7260 wireless card was not the most up to date, so I downloaded the right version from kernel.org and installed it. Rebooted and confirmed that the new version was registered in dmesg, but it didn't make the card work either...

---

### Post by chili555 on 2014-04-07
> I followed the instructions and inserted the new ideapad-laptop. Didn't make a difference,And repeatedly pressing the wireless button (F8) makes no difference? Please press and check:```
rfkill list all
```And try again. Is there no change at all? Then unload ideapad-laptop and try again:```
sudo modprobe -r ideapad-laptop
```Pres F8 and then:```
rfkill list all
```Any change?

---

### Post by yangmusa on 2014-04-07
**rfkill list all**
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

On my keyboard the airplane mode button is on F7, but anyway - it doesn't seem to have any effect, either before or after removing ideapad-laptop. Would a key press effect a hard block though? My impression from other threads was is either a physical switch or (as in this case) a stubborn software error.

---

### Post by chili555 on 2014-04-07
> Would a key press effect a hard block though? Why, absolutely! That's the whole intent of ideapad_laptop or asus-wmi or hp-wmi or, in my case, thinkpad_acpi; to translate key presses into action. In your case, we are trying to translate a press of F7 to 'please turn on the wireless, Mr. Kernel.'

Please execute and report on the tests I suggested.

---

### Post by yangmusa on 2014-04-07
> **chili555 said:**
> And repeatedly pressing the wireless button (F8) makes no difference? Please press and check:```
rfkill list all
```And try again. Is there no change at all? Then unload ideapad-laptop and try again:```
sudo modprobe -r ideapad-laptop
```Pres F8 and then:```
rfkill list all
```Any change?    

Sorry my last reply was unclear - I tried several times unloading ideapad-laptop, listing with rfkill, reloading, listing with rfkill.   I got the same result in either case:   
```
rfkill list all 
```  
0: hci0: Bluetooth  
Soft blocked: yes  
Hard blocked: no  
1: phy0: Wireless LAN 
 Soft blocked: no  
Hard blocked: yes

---

### Post by michal6 on 2014-04-07
Hi, I just want to say that I have absolutely the same problem with same Lenovo. I have been trying to fix it for almost week with no success. I hope that direct help from someone will make difference in results.
Well, my observations: doesn't matter what linux (even installation of debian with 4 of their 4GB dvd didn't help) and what is more frustrating.. installing windows (so I can at least virtualizing linux) won't make any difference. Wireless card is probably working (radio on) only under original windows with Lenovo "trash".
Will come to this thread as much as possible and help diagnosing..

---

### Post by chili555 on 2014-04-07
I'm sorry. We have tried everything I know to try in this case. All I can further suggest is to get an inexpensive fully supported USB wireless and wait for improvements in ideapad-laptop sometime in the future.

I wish the answer could be better.

---

### Post by yangmusa on 2014-04-07
> **chili555 said:**
> All I can further suggest is to get an inexpensive fully supported USB wireless and wait for improvements in ideapad-laptop sometime in the future.


Hah, I already tried that! But it was hard blocked, just like the built in wifi...

At this point I think my best strategy is to find/borrow/buy a Windows install dvd, reinstall Windows, and return the laptop (I have until Friday, and Best Buy refused to accept it as a return on Saturday - they booted it up and saw the horror that is Linux ;-) ) I think it's worth the extra $400 to have a fully functioning laptop, so I'll get the pro. 

Thanks for all your help chili555 - much appreciated!

---

### Post by kainz on 2014-04-11
This happened to me on my Yoga 2 13" as well.  I managed to fix it by hacking up and rebuilding the ideapad-laptop.c to do the following:

write_ec_cmd(ideapad_handle, VPCCMD_W_RF, 1);
write_ec_cmd(ideapad_handle, VPCCMD_W_BT, 1);
write_ec_cmd(ideapad_handle, VPCCMD_W_WIFI, 1);

That will tweak the Phy0 WLAN block off.  After that, rmmod the ideapad-laptop module and keep it blacklisted!

Source: my askubuntu answer via: [http://askubuntu.com/questions/434547/wireless-hard-block/446459#446459](http://askubuntu.com/questions/434547/wireless-hard-block/446459#446459)

Cheers!

---

### Post by chili555 on 2014-04-11
I'm not quite sure how modifying the .c code for the ideapad_laptop module but then blacklisting it so it *never* loads can do, well, anything.

---

### Post by kainz on 2014-04-11
The trick is that I'm telling the module to enable the RF in general (that might be readonly tho), the BT, and the WIFI, irregardless of the 'soft' logic around it.  That tweaks the wifi card somewhere to unblock itself.

I suspect that its the same EC chip and probaly a similar DSDT but with no actual hardware switch wired, which would always make the hardware switch read return null.

---

### Post by chili555 on 2014-04-11
I understand that; however, blacklist says to *never*, *ever* load it. How, exactly, does the tweak take effect if the module is locked up in prison for life with no possibility of parole, even for good behavior and religious epiphany? 

If you had some script, perhaps in /etc/rc.local, that loaded it, turned off rfkill at the device and then unloaded it, I might understand. 

I am not at all saying you are incorrect; I am saying that I don't yet understand the process. By the way, I am aware of and have used several tricks that work well that I can't for the life of me understand. That's a perfectly valid answer: I don't know why it works, I just know it works.

---

### Post by kainz on 2014-04-11
Ah.  You can always manually insmod or modprobe a blacklisted module by name.  aka i'm suggesting using the modded module to force the wifi bits in the EC to be turned back on.

---

### Post by yangmusa on 2014-04-11
Mini-update: after exhausting the patience of all my Windows-using computer literate friends and the IT guys at work, I finally took the Yoga 2 to a local computer shop yesterday. They are going to (try to) reinstall Windows. If that succeeds (everyone else failed so far..), it's going back to Best Buy. If it fails, I'm stuck with it... So I'm encouraged that there seems to be a fix now. Thanks,** @kainz**!

[EDIT: just to be clear - my 15 day return period runs out today. Otherwise I'd try the fix first. However, I won't have time to try it and still return the laptop if the fix doesn't work for me.]

---

### Post by kainz on 2014-04-11
Best of luck either way.  I count myself damn lucky that I discovered that, since the linux 3.11 ideapad-laptop basically bricked my wifi (reinstalling windows didnt help).

---

### Post by chili555 on 2014-04-11
> **kainz said:**
> Ah.  You can always manually insmod or modprobe a blacklisted module by name.  aka i'm suggesting using the modded module to force the wifi bits in the EC to be turned back on.So you blacklisted the native version and insmod the patched version? That's clearer; thanks.

---

### Post by yangmusa on 2014-04-11
Mini-update 2: Central Computers was successful in reinstalling Windows, and Best Buy finally accepted the machine back. Phew, a weight off my mind.

I'm going to mark the thread "SOLVED" in deference to kainz' solution - if anyone else uses the fix on a non-Pro Yoga 2 please add your experiences.

---

### Post by haohe on 2014-04-24
I followed the hack that kainz described and successfully unblocked the wireless on my Yoga 2 13''. I am running Ubuntu 14.04. Here are the detailed steps to share:

(1) Download the kernel source

$ sudo apt-get install build-essential linux-headers-$(uname -r)
$ cd ~/workspace
$ git clone git://kernel.ubuntu.com/ubuntu/ubuntu-trusty.git
$ cp ~/workspace/ubuntu-trusty/drivers/platform/x86/ideapad-laptop.c ~/workspace/ideapad/
$ cd ~/workspace/ideapad/

(2) Change the function ideapad_rfk_set(void *data, bool blocked) in ideapad-laptop.c to

static int ideapad_rfk_set(void *data, bool blocked)
{
        struct ideapad_rfk_priv *priv = data;

/* hack to unblock wireless by sending 1 to these bits */
        write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_RF, 1);
        write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_BT, 1);
        write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_WIFI, 1);
        return 0;
/* */

        return write_ec_cmd(priv->priv->adev->handle, priv->dev, !blocked);
}

(3) Create a file named Makefile:

obj-m += ideapad-laptop.o
 
all: 
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean: 
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

(4) Build the new module

$ cd ~/workspace/ideapad/
$ make

(5) Load the module

$ cp /lib/modules/3.13.0-24-generic/kernel/drivers/platform/x86/ideapad-laptop.ko ~/ideapad-laptop.ko.backup
$ sudo cp ~/workspace/ideapad/ideapad-laptop.ko /lib/modules/3.13.0-24-generic/kernel/drivers/platform/x86/
$ sudo modprobe -r ideapad-laptop
$ sudo modprobe ideapad-laptop
$ sudo rfkill unblock all
$ sudo modprobe -r ideapad-laptop
$ sudo mv ~/ideapad-laptop.ko.backup /lib/modules/3.13.0-24-generic/kernel/drivers/platform/x86/ideapad-laptop.ko

(6) Blacklist the ideapad module
$ cd /etc/modprobe.d/
$ sudo echo 'blacklist ideapad-laptop' > blacklist-ideapad.conf

(7) Reboot the Yoga 2 laptop

---

### Post by Liviane on 2014-05-04
I want to say a BIG THANK YOU to kainz and haohe. I`ve followed the step-by-step described by haohe and my wireless became fully functional again! It is so good that I managed to fix it by myself, even with my small knowledge of Linux. Thanks!!

---

### Post by denis20 on 2014-05-10
Hi haohe and kainz

I just registered in this forum just for say to you BIG THANK YOU !!!!!!! You are The best , Can i share with lenovo comunnity ?

---

### Post by joe108 on 2014-05-26
> **haohe said:**
> I followed the hack that kainz described and successfully unblocked the wireless on my Yoga 2 13''. I am running Ubuntu 14.04. Here are the detailed steps to share:

(1) Download the kernel source

$ sudo apt-get install build-essential linux-headers-$(uname -r)
$ cd ~/workspace
$ git clone git://kernel.ubuntu.com/ubuntu/ubuntu-trusty.git
$ cp ~/workspace/ubuntu-trusty/drivers/platform/x86/ideapad-laptop.c ~/workspace/ideapad/
$ cd ~/workspace/ideapad/

(2) Change the function ideapad_rfk_set(void *data, bool blocked) in ideapad-laptop.c to

static int ideapad_rfk_set(void *data, bool blocked)
{
        struct ideapad_rfk_priv *priv = data;

/* hack to unblock wireless by sending 1 to these bits */
        write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_RF, 1);
        write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_BT, 1);
        write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_WIFI, 1);
        return 0;
/* */

        return write_ec_cmd(priv->priv->adev->handle, priv->dev, !blocked);
}

(3) Create a file named Makefile:

obj-m += ideapad-laptop.o
 
all: 
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean: 
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

(4) Build the new module

$ cd ~/workspace/ideapad/
$ make

(5) Load the module

$ cp /lib/modules/3.13.0-24-generic/kernel/drivers/platform/x86/ideapad-laptop.ko ~/ideapad-laptop.ko.backup
$ sudo cp ~/workspace/ideapad/ideapad-laptop.ko /lib/modules/3.13.0-24-generic/kernel/drivers/platform/x86/
$ sudo modprobe -r ideapad-laptop
$ sudo modprobe ideapad-laptop
$ sudo rfkill unblock all
$ sudo modprobe -r ideapad-laptop
$ sudo mv ~/ideapad-laptop.ko.backup /lib/modules/3.13.0-24-generic/kernel/drivers/platform/x86/ideapad-laptop.ko

(6) Blacklist the ideapad module
$ cd /etc/modprobe.d/
$ sudo echo 'blacklist ideapad-laptop' > blacklist-ideapad.conf

(7) Reboot the Yoga 2 laptop


Hi haohe,

I'm desprite for help. I tried what you posted but ran into an issue with a missing ideapad-laptop.ko file. Here are my steps...

I made a new file called "Makefile" which only contains the following...
obj-m += ideapad-laptop.o

all:
make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean:
make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

... and saved it in ~/workspace/ideapad/

When, while in that folder via terminal, I enter "make" I get...
make: Nothing to be done for `all'.

Should this "make" command be creating the ideapad-laptop.ko file? No such file is being created for me and thus the later copy command in (5) gives an error.

If haohe or anyone can help it would be greatly appreciated. I have little use for this Lenovo Yoga 2 13 59408082 if I can't get the wireless working. :(

- Joe

---

### Post by gbonics on 2014-05-28
Joe

You will need to change the Kernal version.  Do the uname -r command and find your version.  It may be 3.13.0-27.  I followed the same steps and it worked.  Try this:

(1) Download the kernel source

$ sudo apt-get install build-essential linux-headers-$(uname -r)
$ cd ~/workspace
$ git clone git://kernel.ubuntu.com/ubuntu/ubuntu-trusty.git
$ cp ~/workspace/ubuntu-trusty/drivers/platform/x86/ideapad-laptop.c ~/workspace/ideapad/
$ cd ~/workspace/ideapad/

(2) Change the function ideapad_rfk_set(void *data, bool blocked) in ideapad-laptop.c to

static int ideapad_rfk_set(void *data, bool blocked)
{
struct ideapad_rfk_priv *priv = data;

/* hack to unblock wireless by sending 1 to these bits */
write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_RF, 1);
write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_BT, 1);
write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_WIFI, 1);
return 0;
/* */

return write_ec_cmd(priv->priv->adev->handle, priv->dev, !blocked);
}

(3) Create a file named Makefile:

obj-m += ideapad-laptop.o

all:
make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean:
make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

(4) Build the new module

$ cd ~/workspace/ideapad/
$ make

(5) Load the module

$ cp /lib/modules/3.13.0-27-generic/kernel/drivers/platform/x86/ideapad-laptop.ko ~/ideapad-laptop.ko.backup
$ sudo cp ~/workspace/ideapad/ideapad-laptop.ko /lib/modules/3.13.0-27-generic/kernel/drivers/platform/x86/
$ sudo modprobe -r ideapad-laptop
$ sudo modprobe ideapad-laptop
$ sudo rfkill unblock all
$ sudo modprobe -r ideapad-laptop
$ sudo mv ~/ideapad-laptop.ko.backup /lib/modules/3.13.0-27-generic/kernel/drivers/platform/x86/ideapad-laptop.ko

(6) Blacklist the ideapad module
$ cd /etc/modprobe.d/
$ sudo echo 'blacklist ideapad-laptop' > blacklist-ideapad.conf

(7) Reboot the Yoga 2 laptop

---

### Post by joe108 on 2014-05-29
Still no luck

---

### Post by joe108 on 2014-05-29
Hi gbonics,

Thanks for the reply but regardless of the version number I'm still getting stuck at the second line under 5...

sudo cp ~/workspace/ideapad/ideapad-laptop.ko /lib/modules/3.13.0-27-generic/kernel/drivers/platform/x86/
cp: cannot stat ‘/home/tron/workspace/ideapad/ideapad-laptop.ko’: No such file or directory

The file ideapad-laptop.ko does not exist. Should this have already existed or should that have been created when running "make" ins tep 4?

It may be important to note that the folder ~/workspace and thus ~/workspace/ideapad did not exist and I had to create them via mkdir.

Thanks in advance!

- Joe

---

### Post by kaitlin2 on 2014-05-29
I have the same problem as Joe, and I also don't have permission to blacklist ideapad-laptop.
There is probably a quick fix to this. Any help is appreciated.

---

### Post by gbonics on 2014-05-29
I used the sudo -s command before starting.  I executed everything as root to bypass the sudo command.  The [COLOR=#000000] ideapad-laptop.ko file should be in the same directory as the Makefile.[/COLOR]

---

### Post by chili555 on 2014-05-29
> **kaitlin2 said:**
> I have the same problem as Joe, and I also don't have permission to blacklist ideapad-laptop.
There is probably a quick fix to this. Any help is appreciated.Please try:```
sudo-i
echo "blacklist ideapad-laptop"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r ideapad-laptop
exit
```When you do *sudo -i*, you will be asked for your password. If you provide the correct password, the system assume you are permitted to make system changes and proceed.

---

### Post by chili555 on 2014-05-29
> It may be important to note that the folder ~/workspace and thus ~/workspace/ideapad did not exist and I had to create them via mkdir.In the original post, the folder 'workspace' was used to extract the files and build the module. The more correct sequence is:```
$ sudo apt-get install build-essential linux-headers[COLOR="#FF0000"]-generic[/COLOR]
$ [COLOR="#FF0000"]mkdir ~/workspace[/COLOR]
$ cd ~/workspace
$ git clone git://kernel.ubuntu.com/ubuntu/ubuntu-trusty.git
$ cp ~/workspace/ubuntu-trusty/drivers/platform/x86/ideapad-laptop.c ~/workspace/ideapad/
$ cd ~/workspace/ideapad/
```...and so forth.

Both of you please try again.

---

### Post by kaitlin2 on 2014-05-29
Ok, I am in the process of trying it again. Thanks for your help!

---

### Post by kaitlin2 on 2014-05-29
Ok, it still can't find the ideapad-laptop.ko file. Maybe it's an issue of where I put the Makefile. I put it in the ideapad directory. Is that right, or is there some other default place for Makefiles to go?

---

### Post by kaitlin2 on 2014-05-29
I also just don't know where this ideapad-laptop.ko file is supposed to come from. Am I supposed to create it?

---

### Post by chili555 on 2014-05-29
> **kaitlin2 said:**
> I also just don't know where this ideapad-laptop.ko file is supposed to come from. Am I supposed to create it?It should get created at the 'make' step. Didn't it?

---

### Post by kaitlin2 on 2014-05-29
No. I think the 'make' didn't quite work because it said "make: Nothing to be done for 'all'." Maybe it  just didn't do anything.

---

### Post by kaitlin2 on 2014-05-29
Ok, I realized that I needed to have a tab before the "make" lines in the Makefile. The making worked this time, but the overall process didn't work so I'm going to try it again. Sorry for posting so many times. This is my first time installing Linux and my first time really using Linux, so I am trying to get used to everything.

---

### Post by chili555 on 2014-05-29
> **kaitlin2 said:**
> Ok, I realized that I needed to have a tab before the "make" lines in the Makefile. The making worked this time, but the overall process didn't work so I'm going to try it again. Sorry for posting so many times. This is my first time installing Linux and my first time really using Linux, so I am trying to get used to everything.No problem at all; call on us any time.

---

### Post by kaitlin2 on 2014-05-29
Well now all parts of the process seemed to have worked and I rebooted my computer, but the Wireless LAN is still hard-blocked. Is there anything else I need to do to make this work? If I can't figure anything out I guess I'll just have to send the laptop back.

---

### Post by chili555 on 2014-05-29
> **kaitlin2 said:**
> Well now all parts of the process seemed to have worked and I rebooted my computer, but the Wireless LAN is still hard-blocked. Is there anything else I need to do to make this work? If I can't figure anything out I guess I'll just have to send the laptop back.Aside from just getting and trying a USB wireless, I haven't any other suggestions. Sorry.

---

### Post by kaitlin2 on 2014-05-29
So it turns out that gbonics was right about changing the kernel version. Sometime during my attempts today my kernel changed from version 24 to 27, so changing that in my code fixed it and now I have wifi access again! Hopefully this helps Joe too because it seems like we ran into many of the same issues.

---

### Post by joe108 on 2014-05-31
> **chili555 said:**
> Aside from just getting and trying a USB wireless, I haven't any other suggestions. Sorry.

Using a USB wireless adapter will not work if wireless is hardblocked. I tried that too and just ended up with two wirelss devices that were hardblocked.

---

### Post by joe108 on 2014-05-31
> **kaitlin2 said:**
> So it turns out that gbonics was right about changing the kernel version. Sometime during my attempts today my kernel changed from version 24 to 27, so changing that in my code fixed it and now I have wifi access again! Hopefully this helps Joe too because it seems like we ran into many of the same issues.

Thanks for the hopeful thoughts. And a big THANKS to everyone else that helped. I finally got my wifi working. I retired all this many times and re-intalled Ubuntu each time just to have a clean start. I don't know if either of these did anything but last time I tried (when it worked) I was logged in as root while doing everything and befor turning the laptop back on after the re-boot I unplugged the Ethernet cable.

Again, THANK YOU to all. I've been on Ubuntu for the past 3 years and couldn't go back to Windows or a Mac.

---

### Post by Jayan_Menon on 2014-06-16
> **joe108 said:**
> Using a USB wireless adapter will not work if wireless is hardblocked. I tried that too and just ended up with two wirelss devices that were hardblocked.

I had this problem too, but if you unload the iwlmvm and iwlwifi (in that order - sudo rmmod iwlmvm; sudo rmmod iwlwifi), the external USB wifi will work. Having the iwlwifi driver loaded seems to block the wireless feature altogether, not just for itself.

Also, I bought a replacement 7260N card online for about $14 (used) and replaced the card in the laptop, that did not fix the problem with the hard block - so either the hard block is elsewhere on the laptop, not on the firmware/settings on wifi card - or the (used) card I ended up buying was from someone who was trying to rid of a blocked card like mine :-) so much for that experiment..

---

### Post by ilwheeler84 on 2014-06-17
When I run the make command it tells me this...

make -C /lib/modules/3.13.0-29-generic/build M= modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-29-generic'
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf --silentoldconfig Kconfig
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-29-generic'
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-29-generic'
make[2]: *** No rule to make target `/usr/src/linux-headers-3.13.0-29-generic/arch/x86/syscalls/syscall_32.tbl', needed by `arch/x86/syscalls/../include/generated/uapi/asm/unistd_32.h'.  Stop.
make[1]: *** [archheaders] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-29-generic'
make: *** [all] Error 2
veritas@Machina:/workspace/ideapad$ ls
ideapad-laptop.c  Makefile
veritas@Machina:/workspace/ideapad$ sudo make
make -C /lib/modules/3.13.0-29-generic/build M= modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-29-generic'
make[2]: *** No rule to make target `/usr/src/linux-headers-3.13.0-29-generic/arch/x86/syscalls/syscall_32.tbl', needed by `arch/x86/syscalls/../include/generated/uapi/asm/unistd_32.h'.  Stop.
make[1]: *** [archheaders] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-29-generic'
make: *** [all] Error 2

---

### Post by SgtHamburger on 2014-06-17
hello to you all, i feel like i know you guys because i have been reading and re-reading your posts for about the last 5 hours! you have saved me from losing my mind but i am in the same boat at this point as ilwheeler! i am just dipping my toes into the linux world, so i am sure i am just ignorant but i would very much appreciate any help/advice?

chili, kaitlin, joe, original poster, seriously thank you guys you don't even know how much your posts helped me in getting this far. :)

---

### Post by chili555 on 2014-06-18
> veritas@Machina:/workspace/ideapad$ sudo make
make -C /lib/modules/3.13.0-29-generic/build M= modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-29-generic'
make[2]: *** No rule to make target `/usr/src/linux-headers-3.13.0-29-generic/arch/x86/syscalls/syscall_32.tbl', needed by `arch/x86/syscalls/../include/generated/uapi/asm/unistd_32.h'. Stop.
make[1]: *** [archheaders] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-29-generic'
make: *** [all] Error 2I suspect something is wrong with your Makefile. May we see it?```
cd ~/workspace/ideapad
cat Makefile
```You should get this. ```
chili@T410:~/workspace/ideapad$ cat Makefile
obj-m += ideapad-laptop.o	

all: 
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean: 
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```The long space before each 'make' is created with the Tab key. Please correct it and try again. If successful, you will see:```
chili@T410:~/workspace/ideapad$ make
make -C /lib/modules/3.13.0-29-generic/build M=/home/chili/workspace/ideapad modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-29-generic'
  CC [M]  /home/chili/workspace/ideapad/ideapad-laptop.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/chili/workspace/ideapad/ideapad-laptop.mod.o
  LD [M]  /home/chili/workspace/ideapad/ideapad-laptop.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-29-generic'
```In other words, no errors, warnings, smoke, sparks, etc.

---

### Post by ilwheeler84 on 2014-06-18
veritas@Machina:/workspace/ideapad$ cat Makefile
obj-m += ideapad-laptop.o

all:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

This is what my Makefile looks like. It looks right to me, but I wouldn't claim to have a trained eye.

---

### Post by ilwheeler84 on 2014-06-18
```
veritas@Machina:/workspace/ideapad$ cat Makefile
obj-m += ideapad-laptop.o

all:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean


```

Sorry, there is actually the TAB space. When I posted it, it took away the space.

---

### Post by chili555 on 2014-06-18
> **ilwheeler84 said:**
> ```
veritas@Machina:/workspace/ideapad$ cat Makefile
obj-m += ideapad-laptop.o

all:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean


```

Sorry, there is actually the TAB space. When I posted it, it took away the space.Something is still wrong. You get:> make -C /lib/modules/3.13.0-29-generic/build [COLOR="#FF0000"]M= modules[/COLOR]And I got:> make -C /lib/modules/3.13.0-29-generic/build [COLOR="#FF0000"]M=/home/chili/workspace/ideapad modules[/COLOR]Please check if you have build-essential installed:```
sudo dpkg -s build-essential
```If not, install it:```
sudo apt-get install build-essential
```And then try again, this time without sudo:```
cd ~/workspace/ideapad
```Verify that the only things there are ideapad-laptop.c and Makefile:```
ls
```If correct, then:```
make
```Post any errors.

Also, double-check the changes to the .c file. Here is my version that compiles as expected. I omitted the explanatory /*comments*/.[ATTACH=CONFIG]254051[/ATTACH]

---

### Post by ilwheeler84 on 2014-06-18
I noticed a couple of problems with my ideapad-laptop.c 

It now looks like this.

```
static int ideapad_rfk_set(void *data, bool blocked)
{
    struct ideapad_rfk_priv *priv = data;

    write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_RF, 1;
    write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_BT, 1;
    write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_WIFI, 1;
    return 0;

    return write_ec_cmd(priv->priv->adev->handle, priv->dev, !blocked);
}
```

I only have the Makefile and ideapad-laptop.c in the ideapad folder.

When I run sudo make it shows:

```
veritas@Machina:/workspace/ideapad$ sudo make
make -C /lib/modules/3.13.0-29-generic/build M= modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-29-generic'
make[2]: *** No rule to make target `/usr/src/linux-headers-3.13.0-29-generic/arch/x86/syscalls/syscall_32.tbl', needed by `arch/x86/syscalls/../include/generated/uapi/asm/unistd_32.h'.  Stop.
make[1]: *** [archheaders] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-29-generic'
make: *** [all] Error 2


```

I checked to make sure build-essential was installed. And it said it was up to date.

```
veritas@Machina:/workspace/ideapad$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.


```

Chili, Thank you for your help. I really appreciate your time.

---

### Post by chili555 on 2014-06-18
> static int ideapad_rfk_set(void *data, bool blocked)
{
    struct ideapad_rfk_priv *priv = data;

    write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_RF, 1;
    write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_BT, 1;
    write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_WIFI, 1;
    return 0;

    return write_ec_cmd(priv->priv->adev->handle, priv->dev, !blocked);
}Not quite; please try:> static int ideapad_rfk_set(void *data, bool blocked)
{
	struct ideapad_rfk_priv *priv = data;
        
        write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_RF, [COLOR="#FF0000"]1);[/COLOR]
        write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_BT, [COLOR="#FF0000"]1);[/COLOR]
        write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_WIFI, [COLOR="#FF0000"]1);[/COLOR]
        return 0;

	return write_ec_cmd(priv->priv->adev->handle, priv->dev, !blocked);
}
Reference: post #26.

---

### Post by ilwheeler84 on 2014-06-18
This is what ideapad-laptop.c now looks like.

```
static int ideapad_rfk_set(void *data, bool blocked)
{
    struct ideapad_rfk_priv *priv = data;

    write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_RF, 1);
    write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_BT, 1);
    write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_WIFI, 1);
    return 0;

    return write_ec_cmd(priv->priv->adev->handle, priv->dev, !blocked);
}


```

I had the same error.

```
veritas@Machina:/workspace/ideapad$ sudo make
make -C /lib/modules/3.13.0-29-generic/build M= modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-29-generic'
make[2]: *** No rule to make target `/usr/src/linux-headers-3.13.0-29-generic/arch/x86/syscalls/syscall_32.tbl', needed by `arch/x86/syscalls/../include/generated/uapi/asm/unistd_32.h'.  Stop.
make[1]: *** [archheaders] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-29-generic'
make: *** [all] Error 2


```

This is what my Makefile looks like, in case I am overlooking something.

```
obj-m += ideapad-laptop.o

all:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```

---

### Post by chili555 on 2014-06-18
I love problems like this! It looks perfect but doesn't work!!

Please try changing your Makefile to:```
obj-m += ideapad-laptop.o	

all: 
	make -C /lib/modules/$(shell uname -r)/build M=$([COLOR="#FF0000"]shell pwd[/COLOR]) modules
clean: 
	make -C /lib/modules/$(shell uname -r)/build M=$([COLOR="#FF0000"]shell pwd[/COLOR]) clean
```Then try 'make' again. It compiles on my system just fine.

---

### Post by ilwheeler84 on 2014-06-18
Okay that worked! Now new problem at the blackllist step.

```
veritas@Machina:/etc/modprobe.d$ sudo echo 'blacklist ideapad-laptop' > blacklist-ideapad.conf
bash: blacklist-ideapad.conf: Permission denied


```

Thoughts?

---

### Post by ilwheeler84 on 2014-06-19
The WIFI is in fact working! Major victory! So is reseting my computer without blacklisting it (I still haven't gotten that to work), will the wifi no longer work?

---

### Post by chili555 on 2014-06-19
> **ilwheeler84 said:**
> The WIFI is in fact working! Major victory! So is reseting my computer without blacklisting it (I still haven't gotten that to work), will the wifi no longer work?Only one way to find out, reboot! As for the proper way to undertake the blacklist, see post #35.

---

### Post by ilwheeler84 on 2014-06-19
Chili, it works on reset! Thank you for your time. I realize that it is valuable. I hope that our conversation helps others in the future.

---

### Post by chili555 on 2014-06-19
Awesome! Glad it's working.

---

### Post by HansdeGoede on 2014-06-20
Hi all,

I've been working on various rfkill problems with the
Lenovo Yoga 2 series, and after my initial patch to disable
the rfkill driver for the Lenovo Yoga 2 11, I now have what I
believe to be a better fix, which should also help with the
problem people have been having with the Lenovo Yoga 2 13.

For those interested in the details here is the patch:
[http://people.fedoraproject.org/~jwrdegoede/ideapad-laptop/0001-ideapad-laptop-Change-Lenovo-Yoga-2-series-rfkill-ha.patch](http://people.fedoraproject.org/~jwrdegoede/ideapad-laptop/0001-ideapad-laptop-Change-Lenovo-Yoga-2-series-rfkill-ha.patch)

I've made a stand-alone version of the ideapad-laptop module
for testing this:

1) Make sure you've the prerequisites installed for building
kernel modules for your distro
2) Download ideapad-laptop.c and Makefile from here:
[http://people.fedoraproject.org/~jwrdegoede/ideapad-laptop/](http://people.fedoraproject.org/~jwrdegoede/ideapad-laptop/)
3) Put them both in the same directory
4) In this directory do:
make
sudo rmmod ideapad-laptop
sudo insmod ideapad-laptop.ko
rfkill list

Please write down the output of the rfkill list command.

Now disable wifi in your network control panel applet,
and run "rfkill list" again, again please write down
(copy paste) the output.

Now re-enable wifi in your network control panel applet,
and run "rfkill list" again, again please write down
(copy paste) the output. Check that your wifi still
works as expected.

Please let me know if this works for you, and what
the output of the 3 "rfkill list" commands is.

Thanks & Regards,

Hans

---

### Post by madls05 on 2014-06-20
I have done all the steps, in order without errors and then rebooted. My wifi is still disabled though. I don't know what else to do.

---

### Post by HansdeGoede on 2014-06-21
> **madls05 said:**
> I have done all the steps, in order without errors and then rebooted. My wifi is still disabled though. I don't know what else to do.

Which steps, there are multiple sets of instructions in this thread, can you please try with my version of the ideapad-laptop driver, see 2 posts above this one. Also please let us know which model laptop you exactly have.

Thanks,

Hans

---

### Post by madls05 on 2014-06-21
> **HansdeGoede said:**
> Which steps, there are multiple sets of instructions in this thread, can you please try with my version of the ideapad-laptop driver, see 2 posts above this one. Also please let us know which model laptop you exactly have.

Thanks,

Hans

I have a Yoga 2 13.

For the most part I used Hoahe's original post. For the parts I wasn't understanding/ getting errors at, I referred to some of Chili's post later on in the thread. Seemed fine, no errors anywhere. 

I attempted to use your patch yesterday, but it confused me. Am I just supposed to create blank ideapad-laptop.c & a Makefile and then just copy/paste your patches into said files?

---

### Post by HansdeGoede on 2014-06-21
> **madls05 said:**
> I have a Yoga 2 13.

For the most part I used Hoahe's original post. For the parts I wasn't understanding/ getting errors at, I referred to some of Chili's post later on in the thread. Seemed fine, no errors anywhere. 

I attempted to use your patch yesterday, but it confused me. Am I just supposed to create blank ideapad-laptop.c & a Makefile and then just copy/paste your patches into said files?

The code I've made available is not a patch, but it is a standalone version of the module, just download ideapad-laptop.c and Makefile from the link, then do make, rmmod and insmod and you've
my version installed.

---

### Post by madls05 on 2014-06-21
ok. Done. 
Here are the outputs of the 3 rfkill lists: Still blocked.
matt@Lenovo-Yoga-2-13:~/wifi$ rfkill list
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
4: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
5: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

After disabling wifi:
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
4: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
5: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

After reenabling wifi:
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
4: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
5: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by HansdeGoede on 2014-06-21
> **madls05 said:**
> ok. Done. 
Here are the outputs of the 3 rfkill lists: Still blocked.
matt@Lenovo-Yoga-2-13:~/wifi$ rfkill list
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
4: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
5: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

After disabling wifi:
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
4: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
5: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

After reenabling wifi:
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
4: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
5: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

This actually looks good, you should be able to unblock things now and get wifi working, try running "rfkill unblock wifi" and then "rfkill list" again, all wifi should then show as unblocked and then you should be able to connect to your wifi using the network control applet.

---

### Post by madls05 on 2014-06-21
Results from rfkill unblock wifi and then rfkill list:
matt@Lenovo-Yoga-2-13:~/wifi$ rfkill unblock wifi
matt@Lenovo-Yoga-2-13:~/wifi$ rfkill list
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
4: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
5: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

At first, the enable wifi box is able to be checked, and is no longer greyed out. But the control panel still says that wifi is disabled and when I go to wireless settings in the network app, I can't turn it on. Furthermore, if I unplug my wired connection, wifi goes back to being disabled again.

---

### Post by HansdeGoede on 2014-06-21
> **madls05 said:**
> Results from rfkill unblock wifi and then rfkill list:
matt@Lenovo-Yoga-2-13:~/wifi$ rfkill unblock wifi
matt@Lenovo-Yoga-2-13:~/wifi$ rfkill list
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
4: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
5: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

At first, the enable wifi box is able to be checked, and is no longer greyed out. But the control panel still says that wifi is disabled and when I go to wireless settings in the network app, I can't turn it on. Furthermore, if I unplug my wired connection, wifi goes back to being disabled again.

Hi,

Ok we're making progress, but the "Hard blocked: yes" is bad news. I've created a new version of ideapad-laptop.c, please redownload it from: [http://people.fedoraproject.org/~jwrdegoede/ideapad-laptop/ideapad-laptop.c](http://people.fedoraproject.org/~jwrdegoede/ideapad-laptop/ideapad-laptop.c)  then do "ls -l ideapad-laptop.c" and ensure that it is is 23585 bytes large now. After that do make, rmmod, insmod again, and then "rfkill unblock wifi" and "rfkill list" and check that the Hard Blocked is no now.

Thanks for testing!

Regards,

Hans

---

### Post by madls05 on 2014-06-21
It worked! Then I restarted my system and it was disabled again until I redid rmmod, insmod. Any way to make it stay for good/autostart?

2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
6: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
7: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by HansdeGoede on 2014-06-21
> **madls05 said:**
> It worked! Then I restarted my system and it was disabled again until I redid rmmod, insmod. Any way to make it stay for good/autostart?

Hi,

If you do:

cp ideapad-laptop.ko /lib/modules/$(uname -r)/kernel/drivers/platform/x86/

Things should stay working after a reboot.

Note that once you install a kernel update you will need to do a "make"
and then the above cp command again.

Regards,

Hans

---

### Post by madls05 on 2014-06-21
This worked!!! Thank you for all your help Hans, I appreciate it greatly.

---

### Post by o0larry0o on 2014-06-24
HI all,
I just received my Yoga 2 13 this morning, and I've been reading this thread for a while before purchasing it.
So now it's my turn to dig in the wifi problem.
I just booted with a 14.04 live USB.

On question though ....the most stupid and silly one .....how the hell do you get a wired connexion ????? Usb ethernet adapter ? ....

thx

---

### Post by chili555 on 2014-06-24
> **o0larry0o said:**
> HI all,
I just received my Yoga 2 13 this morning, and I've been reading this thread for a while before purchasing it.
So now it's my turn to dig in the wifi problem.
I just booted with a 14.04 live USB.

On question though ....the most stupid and silly one .....how the hell do you get a wired connexion ????? Usb ethernet adapter ? ....

thxThat's a possibility. As well, you could download the necessary parts on some other computer and transfer them on a USB key.

---

### Post by o0larry0o on 2014-06-24
ok, I prefere to buy an adapter, in case of later use.

---

### Post by o0larry0o on 2014-06-24
ahh everything is working perfectly so now I'm taking care of the wifi problem.
Can you tell me what are the prerequisite for compiling etc ? I'm very new to this :)
many thx

EDIT:,
I facing this issue, could you give me a hand ?

$make

-C /lib/modules/3.13.0-29-generic/build M=/home/larry/Downloads/wifi yoga modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-29-generic'
/usr/src/linux-headers-3.13.0-29-generic/arch/x86/Makefile:113: CONFIG_X86_X32 enabled but no binutils support
make[1]: *** No rule to make target `yoga'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-29-generic'
make: *** [all] Error 2

I checked and I have the binutils package installed, I don't know how to solve this.

EDIT:
Ho and I'm running ubuntu 14.04 x64, kernel is 3.13.0-29-generic

Thx

FINAL EDIT:
got it working (after struggling with the driver for my Realtek RLT8723BE ....)
Thanks for your patch :)

---

### Post by Joel_Van_Auken on 2014-06-25
hello, Im aware im a little late on this comment, but i was wondering if it was possible to load ubuntu on a flashdrive on a computer with internet access and do the steps that require internet first, then switch to my lenovo yoga 2 13 and load ubuntu (again on that flashdrive) and continue to finish the steps?

---

### Post by vanilla2 on 2014-06-27
Yes, I'm 99% sure you can unbrick a yoga2 without installing linux on it by booting from a usb-stick with linux. At least I did so. Today I fixed a yoga2 with intel-wifi (rfkill unblock wifi). This yoga2 has only win8.1-64 on it, but was booted from a live-cd that bricked the wifi. I was able to boot the yoga from a 16gig usb2-stick on which I installed linux-mint-17 while the usb-stick was in a similar UEFI Dell laptop. (Put the stick in the yoga, F12 and booted from usb-stick. (Ran at quite a nice usable speed even from ext4 on usb2 stick!) As always, ymmv, but I'll provide details if you want but want.

BTW, the yoga was able to boot from the stick even while in UEFI-only secure-boot mode ;-) I copied the "ubuntu" folder from Dell to \EFI on yoga. (EasyUEFI on windows shows the file path used is: \EFI\ubuntu\shimx64.efi on yoga.) I also used EasyUEFI to create a winPE.iso (on the dell) which I put on the usbstick, so maybe that helps make the stick show up in F12 boot-device menu as UEFI-usb. Who knows... I'm just starting to figure out UEFI/secure-boot. 

While the yoga was running mint17 with from the usb-stick, I did use a usb2-to-ethernet adapter to get on internet, and it worked out-of-the-box. 

While the yoga was running windows, was using a usb-to-wifi adapter to get on internet while built-in wifi was grayed out. But the usb-wifi adapter was initially not working in linux (since all wifi gets blocked). But somewhere (I can't find it right now) one guy said you can unblock a linux-compatible usb-wifi adapter on the yoga, even while built-in one remains blocked, by something like (don't quote me):
```
sudo rfkill unblock all
```

I can check but I think I had 64-bit generic kernel headers 3.13.0-24 fwiw.  I used the ideapad-laptop.c dated 21-Jun-2014 17:51 from:
[http://people.fedoraproject.org/~jwrdegoede/ideapad-laptop/]("http://people.fedoraproject.org/~jwrdegoede/ideapad-laptop/")

But instead of jwrdgoede's  Makefile I used one below per #59 [http://ubuntuforums.org/showthread.php?t=2215044&p=13053296#post13053296]("http://ubuntuforums.org/showthread.php?t=2215044&p=13053296#post13053296")

```

obj-m += ideapad-laptop.o	

all: 
	make -C /lib/modules/$(shell uname -r)/build M=$(shell pwd) modules
clean: 
	make -C /lib/modules/$(shell uname -r)/build M=$(shell pwd) clean

```

I see the patches to fix this are entering the repos, so in a month or two there may be a live ubuntu/mint and/or fedora dvd that could be used to unbrick the wifi. Until then, in theory, there might be a made usb-stick image that could boot and automatically fix it, for use by newbies and best-buy repair folks that are uncomfortable at linux command line. Probably could be pared down to fit on just 4gig usb-stick. This is left as an exercise for the reader, as they say. I'll be glad to answer any questions but may not get back to this forum for a few days.

---

### Post by Joel_Van_Auken on 2014-07-05
Do you know, if I were to:
1. Load Ubuntu from a live USB drive on a desktop computer
2. Preform the fix above
3. Finally, load the same USB on my Lenovo Yoga 2 13

Would this also fix the issue?

---

### Post by chili555 on 2014-07-06
> **Joel_Van_Auken said:**
> Do you know, if I were to:
1. Load Ubuntu from a live USB drive on a desktop computer
2. Preform the fix above
3. Finally, load the same USB on my Lenovo Yoga 2 13

Would this also fix the issue?Frankly, I don't know. I've never tried. However, it seems pretty easy to find out. Make the change, see if any of the changes are declined because the file system on the USB is read-only and then reboot. 

The searchers and I will be fascinated to hear.

---

### Post by kaitlin2 on 2014-07-14
Is anyone who's dual booting Windows have problems with internet on the Windows partion? I have not been using my Windows partition since I installed Linux, but the internet isn't working on my Windows partition, and that started either when I installed my antivirus or when I installed Linux. (I did both around the same time.) I am wondering if installing Linux possibly messed with my wifi on my Windows partition. It will say I am connected but not go on websites.

---

### Post by Bosse_Iseborn on 2014-07-21
@haohe - Thank you, thank you, thank you!!!

I registered just to say this. This problem was driving me crazy, but following your instructions made it easy to fix.

I had tried other similar solutions, but the instructions were always incomplete - the writers assuming a lot of knowledge about low-level Linux which I don't have (though I've been a professional software engineer for close to 25 years and have a lot of experience with Unix).

Your instructions were spot on except for a slight detail. The last command in step six (creating the blacklist file) yielded a permission denied message. I guess that the echo command runs through sudo, but not the redirect to file. I just created the file locally instead followed by a "sudo cp" to /etc/modprobe.d.

Thanks again!

---

### Post by Joel_Van_Auken on 2014-07-24
I'm still not-so-anxious to try my idea. simply because I have already returned one Yoga laptop to BestBuy because the "wifi card died" (i didnt want to admit it was my fault for fear that they wouldnt replace it). I would be pushing my luck if I tried this fix and it didnt work. 

you mentioned that "the file system on the USB is read-only" but when I created my live boot USB using LinuxLive USB creator, it gave me the option for a Persistent File size. Would this "persistent file" save my blacklisted file (which I'm assuming, once blacklisted, wont let my wifi be disabled again) as blacklisted? In other words, would a persistent file save the fix from another computer and blacklist the file so that my wifi on my Yoga never gets disabled at all?

I would be greatly reassured by even an "in theory, yes" answer :)

---

### Post by chili555 on 2014-07-25
> **Joel_Van_Auken said:**
> I'm still not-so-anxious to try my idea. simply because I have already returned one Yoga laptop to BestBuy because the "wifi card died" (i didnt want to admit it was my fault for fear that they wouldnt replace it). I would be pushing my luck if I tried this fix and it didnt work. 

you mentioned that "the file system on the USB is read-only" but when I created my live boot USB using LinuxLive USB creator, it gave me the option for a Persistent File size. Would this "persistent file" save my blacklisted file (which I'm assuming, once blacklisted, wont let my wifi be disabled again) as blacklisted? In other words, would a persistent file save the fix from another computer and blacklist the file so that my wifi on my Yoga never gets disabled at all?

I would be greatly reassured by even an "in theory, yes" answer :)In theory, yes, probably.

Perhaps I wasn't clear about how easy it is to try. Fire up the persistent live USB, make the needed changes, save and shut down the computer. Take it out. Walk around the room for a few moments. Re-insert it and start up the computer running a live session. Did the change stick? If so, you know the answer and you're all set.

In either case, please report back here so the searchers will know. We may be able to work out another idea.

---

### Post by weschester on 2014-07-28
Hi guys,

Thanks for all the work and information that you have all put into this thread/problem.

Here's my scenario;

Got my yoga 2 13, bought an SSD, installed it, and tried using Gparted to copy the HDD to the SSD and along the lines enabled legacy mode which bricked the 7260. 

Now, I've installed 14.04, but of course I am getting;
    Unable to locate packages: "build-essential" and "linux-headers....."

Is there a way I can transfer/install build-essential and the other necessary prereqs for kernel building over a usb drive that I download from another computer? I cant get a usb-to-ethernet locally and don't want to wait days to order one. I may try building a persistent USB key and doing all the work from there as is suggested by the recent posts.

Thanks,
Wes

Edit: I think I have found a solution and will report back for others shortly

---

### Post by weschester on 2014-07-29
So, thanks to Germar from this post

[http://askubuntu.com/questions/334136/how-do-i-install-build-essential-without-an-internet-connection](http://askubuntu.com/questions/334136/how-do-i-install-build-essential-without-an-internet-connection)

> [COLOR=#333333][FONT=UbuntuRegular]Open a Terminal by pressing [/FONT][/COLOR]CTRL[COLOR=#333333][FONT=UbuntuRegular]+[/FONT][/COLOR]ALT[COLOR=#333333][FONT=UbuntuRegular]+[/FONT][/COLOR]T[COLOR=#333333][FONT=UbuntuRegular] and type:[/FONT][/COLOR]sudo apt-get -qq --print-uris install build-essential linux-headers-$(uname -r) | cut -d\' -f 2 > urls.txt
[COLOR=#333333][FONT=UbuntuRegular]copy the urls.txt to a thumbdrive and move over to a computer with Internet Access. Download all files from urls.txt (if the other computer is running Linux you can use wget < urls.txt) and save them in a folder called deb on your thumbdrive.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Go back to your Ubuntu machine, plug in the thumbdrive and open a Terminal[/FONT][/COLOR]
sudo cp /media/YOUR_USERNAME/THUMBDRIVE_NAME/deb/* /var/cache/apt/archives/ [FONT=Ubuntu Mono]sudo apt-get install build-essential linux-headers-$(uname -r)[/FONT]

I've tried this but I am still getting 

> E: Unable to locate package build-essential

edit: [COLOR=#000000][FONT=Consolas]apt-get --print-uris install build-essential
[/FONT][/COLOR]
same result, unable to locate package build-essential

---

### Post by chili555 on 2014-07-29
> **weschester said:**
> 
same result, unable to locate package build-essentialDid you first build a package index?```
sudo apt-get update
```

---

### Post by weschester on 2014-07-29
Hi, no I can't do that as it wants to fetch files from a server.

I also tried a persistant Live USB but 

> [COLOR=#7F8384][FONT=Lucida Grande]What you cannot do on a persistent system:[/FONT][/COLOR]
[LIST]
[*]updates core files (kernel, etc...) = no full system updates
[*]install drivers
[/LIST]


So that didnt work. I also found a USB to Ethernet from the GigaWare brand but apparently it isnt supported in linux. Found a 3 page long thread about trying to get it to work and the guy gave up.....

So.... I may have to try a portable USB install or try to find a supported USB/Ethernet adapter. This is so frustrating.

---

### Post by weschester on 2014-07-30
Hans is the man. Thanks to you all, esp Hans, I got wifi back.

Had to buy a different usb-ethernet (syba 24029 with [COLOR=#545454][FONT=arial]ASIX AX88179 chip) [/FONT][/COLOR]to do it, then run Han's patch.

---

### Post by mOrzan90 on 2014-08-07
Hi,

yesterday my friend VF came to my house with his Lenovo Yoga 2 13 just bought on-line (with Windows 8 already inside).
He came to me because he wanted to install for the first time a Linux os. I suggested Linux Mint 17 Mate (based on Ubuntu Trusty Tahr).

Before installing, I showed him the Live version (which runs on RAM, without making changes to the system) with my external CD player. It was fine, faster than Windows and the touchscreen worked. The wi-fi didn't work, but I thought it was because there were no drivers (it was in Live, I thought).

After the Live tour, back on Windows and we note that miss the network devices! Panic ... ](*,)

With my laptop, I looked on the internet and I found this thread. I read all 10 pages of the topic, and you convinced me to try the Haohe's procedure (post #26) ;) .
I installed Linux Mint next to Windows to be able to perform the procedure.

The Lenovo couldn't connect to internet, so I performed step 1 on my computer and then copy packages (and their dependencies) and the *workspace* folder on him computer.

Then I had the problem in step 6, that I solved following the post #35 of chili555.

I ran all the commands and I didn't got no errors.

I reboot (point 7), did access in Mint, but still does not detect network devices!
I try to start Windows and give me error!

So in summary, I installed Linux next to Windows, I followed the steps and now Windows will not start, and on Linux is impossible to connect to the Internet.

Someone can help me, please?
(and sorry for my english)

---

### Post by chili555 on 2014-08-07
Let's take a step back and do some diagnostics and see if we can put this right. Please open a terminal and run and post:```
lspci -nn | grep 0280
rfkill list all
lsmod | grep idea
```Thanks.

---

### Post by mOrzan90 on 2014-08-10
thank you fir answer
here the results

```
ealtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
```
```
0: hci0: Bluetooth 
    Soft blocked: no 
    Hard blocked: no
```


the last don't have answer

---

### Post by chili555 on 2014-08-10
You haven't any hard-blocked issue which is the subject of this thread. I suggest you start your own new thread and I'll be anxious to help you.

---

### Post by mOrzan90 on 2014-08-10
Thank you for your attention chili :)
I open a new thread [here]("http://ubuntuforums.org/showthread.php?t=2238807&p=13094621#post13094621")

---

### Post by aaron52 on 2014-08-17
thank you everyone for your posts in this topic, I'm still stuck, I've tried the following steps, and have an error with using the make file.

> sudo rmmod iwlmvm
sudo rmmod iwlwifi

rfkill list all

sudo modprobe -r ideapad-laptop
rfkill list all


(1) Download the kernel source

sudo apt-get install build-essential linux-headers-generic linux-headers-$(uname -r)
mkdir ~/workspace
cd ~/workspace
git clone git://kernel.ubuntu.com/ubuntu/ubuntu-trusty.git
cp ~/workspace/ubuntu-trusty/drivers/platform/x86/ideapad-laptop.c ~/workspace/ideapad/
cd ~/workspace/ideapad/

(2) Change the function ideapad_rfk_set(void *data, bool blocked) in ideapad-laptop.c to

static int ideapad_rfk_set(void *data, bool blocked)
{
struct ideapad_rfk_priv *priv = data;

/* hack to unblock wireless by sending 1 to these bits */
write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_RF, 1);
write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_BT, 1);
write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_WIFI, 1);
return 0;
/* */

return write_ec_cmd(priv->priv->adev->handle, priv->dev, !blocked);
}

(3) Create a file named Makefile:

obj-m += ideapad-laptop.o

all:
make -C /lib/modules/$(shell uname -r)/build M=$(shell pwd) modules
clean:
make -C /lib/modules/$(shell uname -r)/build M=$(shell pwd) clean

(4) Build the new module

$ cd ~/workspace/ideapad/
$ make

which results in the following error

> ubuntu@ubuntu:~/workspace/ideapad$ make
make -C /lib/modules/3.13.0-32-generic/build M=/home/ubuntu/workspace/ideapad modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-32-generic'
scripts/Makefile.build:44: /home/ubuntu/workspace/ideapad/Makefile: No such file or directory
make[2]: *** No rule to make target `/home/ubuntu/workspace/ideapad/Makefile'.  Stop.
make[1]: *** [_module_/home/ubuntu/workspace/ideapad] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-32-generic'
make: *** [all] Error 2



I've checked that I have linux-headers-generic linux-headers-$(uname -r) build essentials, and etc
using ubuntu 3.13.0-32-generic

---

### Post by aaron52 on 2014-08-17
thank you everyone for your posts in this topic
I had a few problems but figured them out, one; the Makefile must be capitalized, and two, I somehow copied and pasted some random stuff into ideapad-laptop.c, touchpad is a bit too sensitive for click and drag without configuring it.

this problem has plagued me for months on 3 separate laptops, I'm so glad to finally fix it.
from start to finish I found this to work perfect:
I used a Ubuntu 14.04 live disk for the entire process

> 

rfkill list all

#to use another wifi card, you must remove the following modules and blacklist
sudo rmmod iwlmvmsudo rmmod iwlwifi


sudo echo "blacklist ideapad-laptop"  >>  /etc/modprobe.d/blacklist.conf
sudo modprobe -r ideapad-laptop




(1) Download the kernel source


sudo apt-get install build-essential linux-headers-generic linux-headers-$(uname -r)
mkdir ~/workspace
cd ~/workspace
git clone git://kernel.ubuntu.com/ubuntu/ubuntu-trusty.git
#I had no working internet at the time, so I went to [http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-trusty.git;a=summary](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-trusty.git;a=summary) and downloaded the snapshot
#extract it to ~/workspace/ubuntu-trusty/
cp ~/workspace/ubuntu-trusty/drivers/platform/x86/ideapad-laptop.c ~/workspace/ideapad/
cd ~/workspace/ideapad/


(2) Change the function ideapad_rfk_set(void *data, bool blocked) in ideapad-laptop.c to


static int ideapad_rfk_set(void *data, bool blocked)
{
struct ideapad_rfk_priv *priv = data;


/* hack to unblock wireless by sending 1 to these bits */
write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_RF, 1);
write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_BT, 1);
write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_WIFI, 1);
return 0;
/* */


return write_ec_cmd(priv->priv->adev->handle, priv->dev, !blocked);
}


(3) Create a file named Makefile: (dont forget to put a tab before the 'make' commands)


obj-m += ideapad-laptop.o


all:
make -C /lib/modules/$(shell uname -r)/build M=$(shell pwd) modules
clean:
make -C /lib/modules/$(shell uname -r)/build M=$(shell pwd) clean


(4) Build the new module


cd ~/workspace/ideapad/
make


(5) Load the module


cp /lib/modules/$(uname -r)/kernel/drivers/platform/x86/ideapad-laptop.ko ~/ideapad-laptop.ko.backup
sudo cp ~/workspace/ideapad/ideapad-laptop.ko /lib/modules/$(uname -r)/kernel/drivers/platform/x86/
sudo modprobe -r ideapad-laptop
sudo modprobe ideapad-laptop
sudo rfkill unblock all
sudo modprobe -r ideapad-laptop
sudo mv ~/ideapad-laptop.ko.backup /lib/modules/$(uname -r)/kernel/drivers/platform/x86/ideapad-laptop.ko


(6) Blacklist the ideapad module
sudo -i
echo "blacklist ideapad-laptop"  >>  /etc/modprobe.d/blacklist.conf
exit


(7) Reboot the Yoga 2 
#I didn't see any notification that wifi was working again, until it rebooted and Windows 8 showed it working


[www.aaronwi.com]("http://www.aaronwi.com")
[https://linuxhatesme.wordpress.com/2015/09/26/lenovo-u310-yoga-2-13-wifi-disabled-in-ubuntu/](https://linuxhatesme.wordpress.com/2015/09/26/lenovo-u310-yoga-2-13-wifi-disabled-in-ubuntu/)

---

### Post by amburridge on 2014-08-17
> **aaron52 said:**
> 
I used a Ubuntu 14.04 live disk for the entire process

Just to clarify (as I don't want to kill my WiFi completely) - Did you need a USB -> Ethernet adapter, or just the live disk?

Thanks,

AMB

---

### Post by amburridge on 2014-08-17
Well now I feel like a complete n00b as it does say in the post that they had to download the files and copy over.

I'm hanging my head in shame...

AMB

---

### Post by aaron52 on 2014-08-17
> **amburridge said:**
> Just to clarify (as I don't want to kill my WiFi completely) - Did you need a USB -> Ethernet adapter, or just the live disk?

Thanks,

AMB

I would recommend a USB to ethernet adapter
but I used a usb wifi card myself, the problem with the usb wifi, is that you first need to use rmmod and disable the faulty modules, then if you usb wifi isn't native compatible, you need to use ndiswrapper and get the windows drivers working in linux. so that was a whole other challenge in itself.

but, it is possible you could download everything you need on a separate computer, I believe earlier in this thread is the command to output what you need from apt to a .txt file

---

### Post by amburridge on 2014-08-25
Got myself a USB-Ethernet dongle, followed the instructions and it worked like a charm.

Many thanks,

AMB

---

### Post by vikram6 on 2014-09-13
> **o0larry0o said:**
> 



FINAL EDIT:
got it working (after struggling with the driver for my Realtek RLT8723BE ....)
Thanks for your patch :)

How did you install the drivers? I'm trying to install drivers for Realtek RTL8188CUS. 
I have the same issue where I'm held up by binutils and gcc not being properly installed

---

### Post by chili555 on 2014-09-13
> **vikram6 said:**
> How did you install the drivers? I'm trying to install drivers for Realtek RTL8188CUS. 
I have the same issue where I'm held up by binutils and gcc not being properly installedIt appears you are trying to install the drivers for rtl8182cu and not fix the 'hard blocked: yes' issue discussed here. If so, please start your own new thread.

---

### Post by vikram6 on 2014-09-13
> **chili555 said:**
> It appears you are trying to install the drivers for rtl8182cu and not fix the 'hard blocked: yes' issue discussed here. If so, please start your own new thread.

I'm trying to install the drivers for rtl8182cu so that I can fix the 'hard blocked' issue (don't have an usb-ethernet adapter). I get stuck when I run make, here is the output: 
make -C /lib/modules/3.13.0-32-generic/build M=/home/user/workspace/ideapad modules
make[1]: Entering directory '/usr/src/linux-headers-3.13.0-32-generic'
/usr/src/linux-headers-3.13.0-32-generic/arch/x86/Makefile:98: stack protector enabled but no compiler support 
/usr/src/linux-headers-3.13.0-32-generic/arch/x86/Makefile:113: CONFIG_X86_X32 enabled but no binutils support 
make[1]: gcc: Command not found............

I think that this means that gcc and a lot of the C compiler files aren't installed. I tried to sideload .deb packages, but they're are so many dependencies and the command listed earlier in this thread didn't work for me. I'm hoping if I can install the realtek drivers that I can get internet and install the necessary files to make the patch work. Thanks for your help.

---

### Post by chili555 on 2014-09-13
The driver rtl8192cu is included in Ubuntu 14.04 by default:```
/lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
```The work you are showing here is for the amended ideapad module and not the device driver. You do, indeed, lack the build tools. You could download elsewhere all the bits and pieces if you are determined and patient. It might take a few days.

If you have a friend or neighbor with an ethernet connection, you could walk your Lenovo over and do:```
sudo apt-get install build-essential
```Done.

---

### Post by stefan_03 on 2014-11-02
I've ordered the notebook online and will try the WiFi fix, thanks for the thread so far ! I really appreciate it and I will tell you about my experience.
BTW (sorry for off topic) - is everything else working fine? Mouse pad, touch gestures,  brightness control, suspend/wake etc? If there is any owner of the notebook who installed Linux on it, please PM me. Would be really nice. Thanks!

---

### Post by Cinderboot on 2014-11-13
I'd like to recognize everyone's effort in solving this annoying problem. 
I started looking at the Lenovo U430 at Best Buy. Everything worked out of the box from a Kubuntu 14.04 live USB stick. I spent 4 hours testing it, went home, came back the next day ready to buy and it was GONE!

So I started looking at the Yoga 2 13 and the Yoga 2 Pro. I'll address them separately.

Yoga 2 13: Kubuntu loaded like a breeze. As you may know, the wireless didn't work. OK, I tethered my android phone and used the bestbuy guest wifi. Awesome. After doing a lot of reading and trying several things I basically used the ideapad_laptop.c hack.
This is the best place I found it because everyone's instructions here are very long and it's a discussion that is not easy to follow.

[http://billauer.co.il/blog/2014/08/linux-ubuntu-yoga-hardware-blocked-wireless-lan/](http://billauer.co.il/blog/2014/08/linux-ubuntu-yoga-hardware-blocked-wireless-lan/)

Basically download the file, apt-get install gcc and you're good to compile the new ideapad_laptop.ko. Then I just copied it over to /lib/modules/blah/blah.... Then rmmod ideapad_laptop, then insmod ideapad_laptop.
AND THE WLAN0 SHOWED UP.
I was amazed.
Note that this particular variant of Yoga 2 13 has the Intel 7260 chip.
This was also done on a live session. No install was required.

So I bought the Yoga 2 13. Came home only to find it has a Broadcom 4352 chip. WTF Lenovo????

01:00.0 Network controller: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter (rev 03)

So I remembered something I did with the Yoga 2 Pro. I simply removed ideapad_laptop (rmmod ideapad_laptop) and the wireless showed up.
I would also like to mention that my bluetooth was a bit buggy until I removed the ideapad_laptop module.

Yoga 2 Pro: Tried this out at Best Buy as well. Everything worked fine, but the screen resolution is like 3000x2000, so everything is super tiny. Wireless didn't work either out of the box, but all I did was remove ideapad_laptop and it started working.
I'm not sure what chip it has but I'd bet it's a Broadcom.

Hope this helps others that are considering getting a Yoga 2.

---

### Post by Cinderboot on 2014-11-14
OK, So I've been testing the wireless all morning. I have the Broadcom 4352 card and I can't connect to WPA2. When the wifi radio is on, my bluetooth connection is VERY sluggish (mouse lags too much to be useful).

I'm considering buying the Intel 7260 for $40.

Has anyone had this problem with the 4352?

---

### Post by cake6 on 2014-12-02
I had same problem for yoga 3 pro, found this [http://ytliu.info/blog/2014/11/19/install-kali-linux-in-lenovo-yoga-3-pro/](http://ytliu.info/blog/2014/11/19/install-kali-linux-in-lenovo-yoga-3-pro/)

---

### Post by Joshua_Pritsker on 2015-08-01
Please help me fast I have to go to DEFCON in 1 week and I need wifi!!! I have tried every distro possible and nothing worked, it seems that I have a different problem from everyone else as my rfkill list shows this:

0: ideapad_wlan: Wireless LAN

Please help me fast I have to go to DEFCON in 1 week and I need wifi!!! I have tried every distro possible and nothing worked, it seems that I have a different problem from everyone else as my rfkill list shows this:

0: ideapad_wlan: Wireless LAN
           Soft Blocked: no
           Hard Blocked: no
Yet still no wifi:confused:

---

### Post by howefield on 2015-08-01
You might be better served starting a new thread, especially when you feel you have a different problem to everyone else in the thread, and this one has been on the ropes for almost a year. :)

You can always reference this thread if you feel the need.

---

