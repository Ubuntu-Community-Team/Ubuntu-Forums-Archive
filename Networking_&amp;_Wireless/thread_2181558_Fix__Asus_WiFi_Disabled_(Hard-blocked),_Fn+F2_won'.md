---
title: "Fix : Asus WiFi Disabled (Hard-blocked), Fn+F2 won't work"
date: 2013-10-18
forum: Networking &amp; Wireless
---

### Post by varunendra on 2013-10-18
[CENTER][SIZE=3][COLOR="#800000"]**_Applicable Only to Asus Laptops/Netbooks_**[/COLOR][/SIZE] that use "**asus_nb_wmi**" driver.[/CENTER]

[COLOR="#0000CD"]**_Symptoms_ :**[/COLOR]
[LIST]
[*]The Wireless is disabled (hard-blocked) despite having a correct driver loaded for it.
[*]The Fn+F2 key to enable it won't work.
[*]Either it will get enabled only momentarily, or not at all.
[*]Usually (but not necessarily) a suspend --> resume cycle makes it active and it remains active for most (but not all) people afterwards.
[/LIST]

[COLOR="#0000CD"]**_Verification_ :**[/COLOR]

[INDENT]**1)** Check if a driver is available for the card (open a terminal with Ctrl-Alt-T and enter the following command in it) :
```
lspci -nnk | grep -A2 0280
```
Notice the last line that says "Kernel driver in use:".
[COLOR="#800000"]Is there a module name in front of it?[/COLOR] (e.g. "Kernel driver in use: ath9k")

**2)** Check if the driver is loaded and if "asus_nb_wmi" driver is also in use :
```
lsmod | grep -e ath9k -e asus
```
(replace "ath9k" with whatever driver is used by your wireless)
[COLOR="#800000"]Do you see the driver for your card, and "asus_nb_wmi" both in the above output?[/COLOR]

**3)** Check the "Hard blocked" state of wifi -
```
rfkill list all
```
Note the state of the "phy0" interface.
[COLOR="#800000"]Does it show as "Hard blocked: yes" ?[/COLOR]

**4)** Suspend the notebook by pressing Fn+F1 (or any other way) --> then resume it again.
[COLOR="#800000"]Does the wireless become active now?[/COLOR]

If the answer to all four checks above is yes (no.4 may be an exception for a few), then your system has this bug and the workaround is as follows -[/INDENT]



[SIZE=3][COLOR="#0000CD"]**_Workaround_[/COLOR] *[/SIZE](Thanks to my respectable senior Mr. chili555 for [post=12785026]finding this fix[/post] and guiding me through it)* :**

[INDENT]Please open a terminal (Ctrl-Alt-T) and run the following command in it (you may copy-paste it) -
```
echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf
```
It will create a file *"asus_nb_wmi.conf"* in *"/etc/modprobe.d"* directory that will load the driver *"asus_nb_wmi"* with a parameter *"wapf=4"* since next boot.

Reboot and the wifi should be active now. Unfortunately, Fn+F2 still won't work. A workaround, until it gets fixed, is given in the next post below. I'll update this post if (and when) found a fix to that.[/INDENT]




If the above trick works for you, [s]I would STRONGLY recommend you to add yourself to the "Affected" users list of the following two bug reports to help getting more attention to the problem so that it gets fixed quickly :[/s] (please read the Update below)

_Bug Report against the "asus_nb_wmi" driver_ : [https://bugs.launchpad.net/bugs/1173681](https://bugs.launchpad.net/bugs/1173681)
_Bug Report against the "Fn+F2" key disability_ : [https://bugs.launchpad.net/bugs/1277959](https://bugs.launchpad.net/bugs/1277959)

**[Update 11 Oct 2016 :** The above two bug reports are now obsolete since they have been marked, rightly or wrongly, either fixed or expired. Therefore **it is best to file a new report**. If someone does so, feel free to subscribe me to it and let me know (a PM is welcome). I'd be glad to update this post, if I could, to point to the new bug report.**]**

_How to Report a Bug Effectively_ : [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

[COLOR="#FF0000"]**EDIT : If this workaround works for you, please also post the output of -**[/COLOR]
```
cat /sys/class/dmi/id/product_name
```
..in this thread _to help fixing the bug permanently for your laptop model_. Please read posts **[post=13063772]#19[/post]** and **[post=13063866]#21[/post]** for details. Thanks to ***HansdeGoede*** for coming to the rescue. :)

_[COLOR="#0000CD"]**Cleanup[/COLOR]_ (if the above workaround doesn't work for you) :**

[INDENT]Just delete the "asus_nb_wmi.conf" file we created above, and everything will be back to defaults -
```
sudo rm /etc/modprobe.d/asus_nb_wmi.conf
```[/INDENT]


[COLOR="#0000CD"]**_Alternative to the Fn+F2 switch[/COLOR]_ to toggle WiFi on/off :**

[INDENT]Please see next post below[/INDENT]

---

### Post by varunendra on 2013-10-18
[CENTER][SIZE=3][COLOR="#800000"]**_Setting a HotKey to Toggle the WiFi On/Off_[/COLOR][/SIZE] (Alternative to the Fn+F2 switch)**[/CENTER]

Until this issue is fixed with newer updates, you may use "xbindkeys" tool to set a hotkey (can be a single key or a key-combination) of your choice to toggle the WiFi enabled/disabled.

This is how -

[COLOR="#0000CD"]**A. _Create a Script to do it smartly_ :**[/COLOR]

[INDENT]**1)** First, we create a script (for ease of use, and so that we can toggle it on/off using the same hotkey) -
```
#!/bin/bash
# Script to toggle the wireless blocked/unblocked

# index no. of phy interface
IFACE=`rfkill list all | grep phy | cut -c 1`

# WiFi block state 0=active, 1=blocked
BLOCKED=`rfkill list all | grep -iA1 phy | grep -ic soft.*yes`

if [ $BLOCKED -eq 1 ]; then
	rfkill unblock $IFACE

else
	rfkill block $IFACE
fi
```
Copy-paste the contents of the above box in a text file and save this file in your Home directory with the name - "**[COLOR="#0000CD"]wifitoggle.sh[/COLOR]**". Make sure the first line is (without double quotes) "[COLOR="#0000CD"]**#!/bin/bash**[/COLOR]" and last one is "[COLOR="#0000CD"]**fi**[/COLOR]".

**2)** Make the script executable by running the following command in a terminal -
```
chmod +x wifitoggle.sh
```

**3)** Run the following command to Create a symlink to this script in /bin directory -
```
sudo ln -s $HOME/wifitoggle.sh /bin
```[/INDENT]

Now proceed to binding it with a hotkey as follows -

[COLOR="#0000CD"]**B. _Bind the Script with a HotKey of your choice_ :**[/COLOR]

[INDENT]**1)** Install ***xbindkeys-config*** (a GUI frontend to xbindkeys - the program that captures and binds hotkeys with commands) -
```
sudo apt-get install xbindkeys-config
```

**2)** Create a default config file for it (else it would crash on key capture step) -
```
xbindkeys --defaults > ~/.xbindkeysrc
```

**3)** Run the program from terminal or "Alt+F2" (because it does not create a launcher in Unity dash) -
```
xbindkeys-config
```
let the terminal running in the background..
In the GUI box that opens, 3 example shortcuts are already present. You may leave them.

**4)** Click on "[COLOR="#0000CD"]**New**[/COLOR]" button at the bottom of the GUI.

**5)** In the right hand pane of the GUI, fill in a suitable name in the "[COLOR="#0000CD"]**Name**[/COLOR]" field, e.g. "**Toggle Wifi**"

**6)** Click on "[COLOR="#0000CD"]**Get Key**[/COLOR]" button. This will open a tiny blank box doing nothing but waiting for your input.

**7)** Press the desired key (or key combination) that you want for toggling Wifi on/off. For example, "F3" key (as it remains mostly unused). The tiny box will disappear and the key will be recorded.

**8)** In the "[COLOR="#0000CD"]**Action**[/COLOR]" field, type this -
```
/bin/bash /bin/wifitoggle.sh
```

**9)** Click on "[COLOR="#0000CD"]**Apply**[/COLOR]" button and test the hotkey to see if it works as expected.

**10)** Click on "[COLOR="#0000CD"]**Save & Apply & Exit**[/COLOR]" to save the new hotkey to the default file and exit.[/INDENT]

From now on, as soon as you will press this key or the key-combination, the wifi will change its state from On to Off, or Off to On.

The Fn key doesn't seem to be noticed by any key capture program I could find (probably that's why it is considered "Hardware Switch"), so it's not possible to use it yet.


Once more, I'd request anyone who needs this workaround to **submit a bug report** against the problem, **or** add themselves to the "**Affects Me**" list, and point to this thread as a possible workaround.

The stronger it gets reported, the sooner we'll get it fixed, thus not requiring such crude workarounds.

---

### Post by Mr.Kappa on 2013-12-28
Thank you very much this solved my issues with an ASUS X551C computer. :guitar::guitar::guitar:
BTW don't by this machine it's awful.

---

### Post by varunendra on 2013-12-28
You're welcome ! :)

We'd appreciate if you could let us know 'Why' the machine is awful, in the thread dedicated for this : [Laptop INCOMPATIBILITY List]("http://ubuntuforums.org/showthread.php?t=1543009")
It is the correct place for letting us know what works and what not with your machine, and it helps users making a decision on what to buy. :)

---

### Post by Bao2 on 2014-03-09
That line:
echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf

solved the problem with my Asus laptop F550C and the Atheros card inside. Once rebooted after that order it works now perfect.
Many thanks.

---

### Post by varunendra on 2014-03-10
You're welcome! Please consider adding yourself to the "Affects Me" list of the linked bug reports. Thanks. :)

---

### Post by jerry_hernandez on 2014-04-11
thanks, my wireless is working now .,   :D  thanks, and thanks again . !!!!

---

### Post by varunendra on 2014-04-11
Welcome to the forums Jerry! Always so pleasant to see someone's first post being a thanks for a successful fix. :)

---

### Post by kmdude344 on 2014-05-03
Ermagerd much thx :d :d :) :)

---

### Post by varunendra on 2014-05-03
> **kmdude344 said:**
> Ermagerd much thx :d :d :) :)

You're welcome! :)

Please consider the request regarding the bug reports.

---

### Post by erotavlas on 2014-05-07
Hi,
I followed the procedure. Now I can use wifi by enabling it with enable wifi button into the connection menu of applet indicator. The trick for the key does not work. I have a asus F550C notebook and I already reported the bugs.

---

### Post by varunendra on 2014-05-07
> **erotavlas said:**
> The trick for the key does not work..

Do you mean binding the "rfkill" command with xbindkeys? Please post the output of -
```
rfkill list all
```
..so that I can suggest the exact command to try. If the command works, binding it should also work, unless it is the "xbindkeys" program itself that is not working for some reason.

---

### Post by ghiwani on 2014-05-20
Tnx, dude ;). This workaround works just fine on my Asus R510C.
I posted a bugreport on the links you mentioned.
):P

---

### Post by varunendra on 2014-05-20
Welcome to the forums ghiwani, :)

Found email notifications about your comments on bug report pages, thanks for taking time to do that!

I wonder how much heat it is going to take for the developers to finally address the bug on urgent basis and finally fix it :-k

---

### Post by adam60 on 2014-05-25
Hey, I just joined the forums to say thank you soooooo much for this work around. 

This same wireless problem has been bugging me for months. This is the first solution that worked. =d>

---

### Post by varunendra on 2014-05-26
> **adam60 said:**
> Hey, I just joined the forums to say thank you soooooo much for this work around. 

This same wireless problem has been bugging me for months. This is the first solution that worked. =d>

That is so nice of you Adam! :)

Thank you for the feedback, and Welcome to Ubuntu Forums !! :popcorn:

---

### Post by domestitus on 2014-06-24
Thaks a lot worked perfectly with brand new ASUS x550cc
Juat after installing Kubuntu 13.01

:-)

Thanks!

---

### Post by varunendra on 2014-06-24
I'm glad the post could help so many, and Welcome to the forums domestitus ! :)

By the way, all credits go to my guru dr. chili555 who originally dug up the magic parameter, I just wrote down the steps in the post.

---

### Post by HansdeGoede on 2014-07-02
Hi All,

I'm an upstream kernel developer who happened to stumble over this forum thread. The proper solution here is to add a dmi based quirk to the asus-nb-wmi driver to use wapf=4 by default. Note the wapf=4 not wapf=1 which everyone has been testing with sofar.

I would like to add a proper fix for this to the upstream kernel (which should then eventually find its way to the ubuntu kernels when ubuntu switches to a newer kernel).

I need your help for this. First of all please adjust the workaround with the /etc/modprobe.d/asus_nb_wmi.conf file to set wapf to 4. Then reboot and test that wifi still works, and if you've bluetooth and that that also works.

Once you've confirmed that everything is fine with wapf=4, run the following command:

cat /sys/class/dmi/id/product_name

From a terminal and add a post here with the output of this command. Then I can add a quirk for your model to asus-nb-wmi.c and send a patch upstream.

Thanks,

Hans

---

### Post by varunendra on 2014-07-02
Hello Hans,

If this proves to be of any help, I'd love to edit my instructions to use wapf=4 instead of 1, plus the additional recommendation to provide the dmi id here for permanent solution per model. But I would like you to please confirm first how value 4 is better than value 1. Does it enable the Fn+F2 key combo? Is it to make sure that bluetooth works too which you think doesn't work with value '1'? Or is there some other advantage that is going to help you behind the scenes?

I'm asking this because before posting this thread, we had tested the variations 0-9 many times with different users (all the way knowing that officially supported values are 0, 1 and 4, where they respectively mean hardware/hardware, hardware/software and software/software for bluetooth/wireless interfaces), and in all the tests (no less than 4 different machines), anything but 0 made the wireless work, but never enabled the 'Fn+F2' function. Bluetooth was never blocked (as per "rfkill list" output) with any value, if I remember correctly.

So if you are concerned that value 4 is required to ensure bluetooth functionality, I would be curious to know why you think so. Do you have some evidence/feedback that bluetooth is blocked with value 1 and not with 4? I may try to look back at some posts myself if you wish, although I can't guarantee due to lack of time.

So please answer these questions if you have time to -

[indent]**1)** If it doesn't make Fn+F2 work, then why do you want value 4 instead of 1 in the patch?

**2)** Do you have some evidence to support whatever reason you have to prefer value 4 over 1?

**3)** Since both bug reports so far direct to this thread (first post) for a workaround, can I help the cause in any way? (except blindly changing posts without knowing 'Why')[/indent]

Thanks for taking time to look into this, it's very encouraging to interact directly with a developer regarding the issue. :)

---

### Post by HansdeGoede on 2014-07-02
> **varunendra said:**
> 
Hello Hans,

If this proves to be of any help, I'd love to edit my instructions to use wapf=4 instead of 1, plus the additional recommendation to provide the dmi id here for permanent solution per model. But I would like you to please confirm first how value 4 is better than value 1. Does it enable the Fn+F2 key combo? Is it to make sure that bluetooth works too which you think doesn't work with value '1'? Or is there some other advantage that is going to help you behind the scenes?

I'm asking this because before posting this thread, we had tested the variations 0-9 many times with different users (all the way knowing that officially supported values are 0, 1 and 4, where they respectively mean hardware/hardware, hardware/software and software/software for bluetooth/wireless interfaces), and in all the tests (no less than 4 different machines), anything but 0 made the wireless work, but never enabled the 'Fn+F2' function. Bluetooth was never blocked (as per "rfkill list" output) with any value, if I remember correctly.

So if you are concerned that value 4 is required to ensure bluetooth functionality, I would be curious to know why you think so. Do you have some evidence/feedback that bluetooth is blocked with value 1 and not with 4? I may try to look back at some posts myself if you wish, although I can't guarantee due to lack of time.

So please answer these questions if you have time to -

**1)** If it doesn't make Fn+F2 work, then why do you want value 4 instead of 1 in the patch?


Because the kernel already has a large list of quirks for other Asus models and they all use 4, not 1, so for consistency I would like to use 4 for the new models too.

> **varunendra said:**
> 
**2)** Do you have some evidence to support whatever reason you have to prefer value 4 over 1?


The relevant kernel code says:

/*
 * WAPF defines the behavior of the Fn+Fx wlan key
 * The significance of values is yet to be found, but
 * most of the time:
 * Bit | Bluetooth | WLAN
 *  0  | Hardware  | Hardware
 *  1  | Hardware  | Software
 *  4  | Software  | Software
 */

So going from 0 (the default) to 1, changes the wlan setting from hardware to software. Since modern wifi cards often are combined wifi+bt cards, it makes sense to do the same for bluetooth, which means we end up with a setting of 4, as is already used by many quirk table entries. This is also why I ask people to test bt, to ensure that this change does at least not break bt.

> **varunendra said:**
> 
**3)** Since both bug reports so far direct to this thread (first post) for a workaround, can I help the cause in any way? (except blindly changing posts without knowing 'Why')


In this case I don't see anything you can do specifically but for similar cases in the future, if a user ever needs to specify a special kernel commandline parameter to get things to work that is considered a bug, and the commandline parameter should be seen as a work-around. In the end we want things to just work ootb, rather then have users search google for workarounds. So in the future please make sure these kind of bugs get the attention from upstream developers. If all else fails drop me a mail at [email]hdegoede@redhat.com[/email] and I'll see what I can do.

---

### Post by HansdeGoede on 2014-07-02
About the Fn+F2 key combo not working that is (sort-of) an orthogonal problem. I expect the Fn+F2 key combo to generate key press events, which then gets handled by the desktop environment, which then toggles the rfkill settings. The wapf parameter is about getting the rfkill code to do the right thing.

Still the Fn+F2 key ought to work too. For starters can someone with an affected laptop try the following:

1) Boot with the following added to the kernel commandline: "atkbd.softraw=0"
2) Once booted switch to a text-console, using CTRL+ALT+F2
3) As root run: "showkey -s"
4) Press the wireless hotkey key-combo

And let me know if any output gets generated at step 4) ?

---

### Post by webbonet on 2014-07-13
> **hansdegoede said:**
> hi all,

i'm an upstream kernel developer who happened to stumble over this forum thread. The proper solution here is to add a dmi based quirk to the asus-nb-wmi driver to use wapf=4 by default. Note the wapf=4 not wapf=1 which everyone has been testing with sofar.

I would like to add a proper fix for this to the upstream kernel (which should then eventually find its way to the ubuntu kernels when ubuntu switches to a newer kernel).

I need your help for this. First of all please adjust the workaround with the /etc/modprobe.d/asus_nb_wmi.conf file to set wapf to 4. Then reboot and test that wifi still works, and if you've bluetooth and that that also works.

Once you've confirmed that everything is fine with wapf=4, run the following command:

Cat /sys/class/dmi/id/product_name

from a terminal and add a post here with the output of this command. Then i can add a quirk for your model to asus-nb-wmi.c and send a patch upstream.

Thanks,

hans

x75vd

---

### Post by HansdeGoede on 2014-07-14
Hi,

> **webbonet said:**
> x75vd

dmi strings are case sensitive and typically Asus uses all uppercase are you sure this is correct, and that this should not be X75VD ?

Thanks,

Hans

---

### Post by 530000693 on 2014-07-31
Oh. I am so happy that my ASUS X550C is fixed by what you have say!

---

### Post by green.jon on 2014-08-01
I have an Asus X550C as well and my wifi now works thanks to this workaround. My Fn+F2 doesn't work, but I don't feel the need to try the workaround at this point in time. Thanks!

---

### Post by roberto21 on 2014-08-06
Hi to all. I have the same issue solved by the workaround.
The output of cat /sys/class/dmi/id/product_name is:
[INDENT]**X551CAP**[/INDENT]

Thanks bye
  R

---

### Post by varunendra on 2014-08-08
Welcome to Ubuntu Forums roberto21! :)

Glad it worked for you. I just keep waiting for post that can confirm an update fixed the Fn+F2 issues as well..

---

### Post by Wishy2009 on 2014-08-19
> **HansdeGoede said:**
> Hi All,

Once you've confirmed that everything is fine with wapf=4, run the following command:

cat /sys/class/dmi/id/product_name

From a terminal and add a post here with the output of this command. Then I can add a quirk for your model to asus-nb-wmi.c and send a patch upstream.

Thanks,

Hans

Works for my U32U thanks. Has been an issue from Mint 14 (IIRC) to the current 17.

---

### Post by neanro on 2014-08-20
> **HansdeGoede said:**
> Hi All,

I'm an upstream kernel developer who happened to stumble over this forum thread. The proper solution here is to add a dmi based quirk to the asus-nb-wmi driver to use wapf=4 by default. Note the wapf=4 not wapf=1 which everyone has been testing with sofar.

I would like to add a proper fix for this to the upstream kernel (which should then eventually find its way to the ubuntu kernels when ubuntu switches to a newer kernel).

I need your help for this. First of all please adjust the workaround with the /etc/modprobe.d/asus_nb_wmi.conf file to set wapf to 4. Then reboot and test that wifi still works, and if you've bluetooth and that that also works.

Once you've confirmed that everything is fine with wapf=4, run the following command:

cat /sys/class/dmi/id/product_name

From a terminal and add a post here with the output of this command. Then I can add a quirk for your model to asus-nb-wmi.c and send a patch upstream.

Thanks,

Hans

I'm on ASUS U32U.. please send the patch on my email: [email]neanro@gmail.com[/email] Thanks! Kudos guys!

---

### Post by dompro11 on 2014-08-24
This workaround was successful for me on my Asus **X551CA**.

Thanks so much!

---

### Post by ratheeshp on 2014-08-24
this worked for me on my X551CAP

---

### Post by monrealis on 2014-08-24
Worked for me, thanks.
[FONT=courier new]cat /sys/class/dmi/id/product_name
X550CL[/FONT]

---

### Post by iolapiu on 2014-09-08
Hi all and thank you for the workaround!

Asus **N73SV**

---

### Post by gowrishankar2 on 2014-09-20
Press Fn + f1 , this will power off the screen, you can again switch on by holding the power button, then enter password to login. This would do so. It worked for me well. However everytime i login i have to do this step. I haven't got any permanent solution yet.

---

### Post by varunendra on 2014-09-20
> **gowrishankar2 said:**
> Press Fn + f1 , this will power off the screen....

Hello Gowrishankar, Welcome to the forums! :)

Did you read the first post of this thread? Fn+F1 on Asus laptops in fact suspends the laptop, so what you described is precisely an indication of the problem that this thread and its workaround is about.

Please read the first post carefully, and if the symptoms match, try the workaround mentioned in it and let us know the result.

---

### Post by flaktron on 2014-09-23
Thank you that solved my problem. Was very simple when you described it. Much appreciated.

---

### Post by varunendra on 2014-09-23
You're welcome flaktron! Hope you will enjoy your OS now, as well as the forums here. :)

---

### Post by gt-oostrum on 2014-10-04
Thanks! Works for me: X550CL

---

### Post by varunendra on 2014-10-04
Welcome to the forums gt-oostrum! :)

---

### Post by mithunh111 on 2014-10-31
thanks man..... it really helped . i cant express how much happy i am . thanks again. 

i tried many things, finally ended up here .... yahooo ... ):P\\:D/=d>

---

### Post by fernandofreamunde on 2014-11-02
Hi guys in my Laptop the ASUS X450JN, the output of the rfkill list all

is as follows:

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no


I don't get why it says acer, but I dont have wireless and I would love to get your help in this...

BTW the output of the 
lspci -nnk | grep -A2 0280

03:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:0652]
    Kernel driver in use: ath9k


and the output of 
lsmod | grep -e ath9k -e asus

asus_nb_wmi            16990  0 
asus_wmi               24094  1 asus_nb_wmi
sparse_keymap          13948  2 acer_wmi,asus_wmi
ath9k                 136984  0 
ath9k_common           25638  1 ath9k
ath9k_hw              446568  2 ath9k_common,ath9k
ath                    29052  3 ath9k_common,ath9k,ath9k_hw
mac80211              660592  1 ath9k
cfg80211              510218  4 ath,ath9k_common,ath9k,mac80211
video                  20128  4 i915,acer_wmi,nouveau,asus_wmi
wmi                    19193  4 acer_wmi,mxm_wmi,nouveau,asus_wmi



the workaround don't work and I don't have a clue why

Thank you in advance :)

EDIT:

it is easy to solve my problem, just use:

sudo modprobe -r acer-wmi

now all I need is to put thisnin the start of the system so I can have internet when I turn the PC on :)

---

### Post by rune3 on 2014-11-27
I don't know if this is the correct place, but I have a ASUS WIFI problem too. Fn+F2 doesn'r work, and in general WIFI doesn'twork.

I have a AsusSonicMaster with a just installed Ubuntu 14.10, dual booting on aWindows 8.1 Everything works in Windows. The WIFI light on thecomputer doesn't light up either in Ubunto (it does in Windows). Itdid light up in Ubuntu at some point, but WIFI didn't work theneither.

Here are thecommands:

cat/sys/class/dmi/id/product_name
S301LP

rfkill list all
0: asus-wlan:Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth:Bluetooth
    Soft blocked: no
    Hard blocked: no

lspci -nnk | grep-A2 028003:00.0 Network controller [0280]: MEDIATEK Corp. MT7630e802.11bgn Wireless Network Adapter [14c3:7630]
    Subsystem: FoxconnInternational, Inc. Device [105b:e074]
04:00.0 VGAcompatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI]Mars LE [Radeon HD 8530M / R5 M240] [1002:6607] (rev ff)


There are no driver?But in System Settings : Software & Updates : Additional Drivers,there are only three Radeon graphics drivers to choose from.


In the NetworkManager menu, accessable from the top right icon, there are no WIFIentries. There is no WIFI in System Settings : Network (only wired)


The other FN keysfunctions properly.

I have tried 
echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf

And rebooting, etc.

---

### Post by chili555 on 2014-11-27
> I have tried 
echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf

And rebooting, etc.Since your wireless isn't blocked:> rfkill list all
0: asus-wlan:Wireless LAN
Soft blocked: no
Hard blocked: no
1: asus-bluetooth:Bluetooth
Soft blocked: no
Hard blocked: no
Then that parameter will do nothing. You may as well remove it:```
sudo rm /etc/modprobe.d/asus_nb_wmi.conf
```The real problem is that your wireless hasn't a driver. I suggest that you get a temporary internet connection by ethernet, tethered or however is available. Open a terminal and do:

```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/lwfinger/mt7630.git
cd mt7630
make
sudo make install
sudo modprobe rt2800pci
```
Your wireless should now be working.

---

### Post by Etrygan on 2014-11-30
Thanks so much, this worked for me. My laptop: Asus X45U

---

### Post by kmdude344 on 2014-12-05
> **varunendra said:**
> [CENTER][SIZE=3][COLOR=#800000]**_Applicable Only to Asus Laptops/Netbooks_**[/COLOR][/SIZE] that use "**asus_nb_wmi**" driver.[/CENTER]

[COLOR=#0000CD]**_Symptoms_ :**[/COLOR]
[LIST]
[*]The Wireless is disabled (hard-blocked) despite a correct driver being loaded for it.
[*]The Fn+F2 key to enable it won't work.
[*]Either it will get enabled only momentarily, or not at all.
[*]Usually (but not necessarily) a suspend --> resume cycle makes it active and it remains active for most (but not all) people afterwards.
[/LIST]

[COLOR=#0000CD]**_Verify_ :**[/COLOR]
[INDENT]**1)** Check if a driver is available for the card (open a terminal with Ctrl-Alt-T and enter the following command in it) :
```
lspci -nnk | grep -A2 0280
```
Notice the last line that says "Kernel driver in use:".
[COLOR=#800000]Is there a module name in front of it?[/COLOR] (e.g. "Kernel driver in use: ath9k")

**2)** Check if the driver is loaded and if "asus_nb_wmi" driver is also in use :
```
lsmod | grep -e ath9k -e asus
```
(replace "ath9k" with whatever driver is used by your wireless)
[COLOR=#800000]Do you see the driver for your card, and "asus_nb_wmi" both in the above output?[/COLOR]

**3)** Check the "Hard blocked" state of wifi -
```
rfkill list all
```
Note the state of the "phy0" interface.
[COLOR=#800000]Does it show as "Hard blocked: yes" ?[/COLOR]

**4)** Suspend the notebook by pressing Fn+F1 (or any other way) --> then resume it again.
[COLOR=#800000]Does the wireless become active now?[/COLOR]

If the answer to all four checks above is yes (no.4 may be an exception for a few), then your system has this bug and the workaround is as follows -[/INDENT]



[SIZE=3][COLOR=#0000CD]**_Workaround_**[/COLOR][/SIZE]***(Thanks to my respectable senior Mr. chili555 for [post=12785026]finding this fix[/post] and guiding me through it)* :**
[INDENT]Please open a terminal (Ctrl-Alt-T) and run the following command in it (you may copy-paste it) -
```
echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf
```
It will create a file *"asus_nb_wmi.conf"* in *"/etc/modprobe.d"* directory that will load the driver *"asus_nb_wmi"* with a parameter *"wapf=4"* since next boot.

Reboot and the wifi should be active now. Unfortunately, Fn+F2 still won't work. A workaround, until it gets fixed, is given in the next post below. I'll update this post if (and when) found a fix to that.[/INDENT]




If the above trick works for you, I would STRONGLY recommend you to add yourself to the "Affected" users list of the following two bug reports to help getting more attention to the problem so that it gets fixed quickly :

_Bug Report against the "asus_nb_wmi" driver_ : [https://bugs.launchpad.net/bugs/1173681](https://bugs.launchpad.net/bugs/1173681)
_Bug Report against the "Fn+F2" key disability_ : [https://bugs.launchpad.net/bugs/1277959](https://bugs.launchpad.net/bugs/1277959)

_How to Report a Bug Effectively_ : [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

[COLOR=#FF0000]**EDIT : If this workaround works for you, please also post the output of -**[/COLOR]
```
cat /sys/class/dmi/id/product_name
```
..in this thread _to help fixing the bug permanently for your laptop model_. Please read posts **[post=13063772]#19[/post]** and **[post=13063866]#21[/post]** for details. Thanks to ***HansdeGoede*** for coming to the rescue. :)

_[COLOR=#0000CD]**Cleanup**[/COLOR]_** (if the above workaround doesn't work for you) :**
[INDENT]Just delete the "asus_nb_wmi.conf" file we created above, and everything will be back to defaults -
```
sudo rm /etc/modprobe.d/asus_nb_wmi.conf
```[/INDENT]


[COLOR=#0000CD]**_Alternative to the Fn+F2 switch_**[/COLOR]** to toggle WiFi on/off :**
[INDENT]Please see next post below[/INDENT]

This worked the first two times I installed Ubuntu (I keep swapping OS's with manjaro and ubuntu) but now when I do it, it completely disables my wifi on any Linux OS, even though its a whole new fresh install. Do you have an updated workaround?

---

### Post by chili555 on 2014-12-05
> **kmdude344 said:**
> This worked the first two times I installed Ubuntu (I keep swapping OS's with manjaro and ubuntu) but now when I do it, it completely disables my wifi on any Linux OS, even though its a whole new fresh install. Do you have an updated workaround?I would try changing the parameter to 1:```
echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf
```For the benefit of the searchers and coders out there, tee without the -a for append option, overwrites the original file. Therefor, we needn't edit the file directly.

Reboot and tell us if it's working.

---

### Post by NyteRukh on 2014-12-05
thankyou it worked for me...going to do the script and the keybind part too. thanks alot....

---

### Post by g-john-i on 2014-12-10
> **hansdegoede said:**
> hi all,

i'm an upstream kernel developer who happened to stumble over this forum thread. The proper solution here is to add a dmi based quirk to the asus-nb-wmi driver to use wapf=4 by default. Note the wapf=4 not wapf=1 which everyone has been testing with sofar.

I would like to add a proper fix for this to the upstream kernel (which should then eventually find its way to the ubuntu kernels when ubuntu switches to a newer kernel).

I need your help for this. First of all please adjust the workaround with the /etc/modprobe.d/asus_nb_wmi.conf file to set wapf to 4. Then reboot and test that wifi still works, and if you've bluetooth and that that also works.

Once you've confirmed that everything is fine with wapf=4, run the following command:

Cat /sys/class/dmi/id/product_name

from a terminal and add a post here with the output of this command. Then i can add a quirk for your model to asus-nb-wmi.c and send a patch upstream.

Thanks,

hans

x551ca

---

### Post by NyteRukh on 2014-12-11
hi this workaround was working...and now this morning..after having reset my wifi cable modem it doesnt work...wifi works on my windows desktop but not on my laptop..and since i got ubuntu the way i want it..i really dont want to reinstall ubuntu...any ideas on how to fix?

---

### Post by chili555 on 2014-12-11
> it doesnt workThat doesn't tell us much. Does the wireless see and try to connect to your modem? Does it not see it at all? Is it hard blocked again? Does the key combination for wireless respond to key presses? Or...what?```
rfkill list all
```

---

### Post by NyteRukh on 2014-12-11
sorry ..yes it does try to connect...and it see's it and its not hardblocked again...when i reinstalled ubuntu and the wireless was working, i forgot to reinstall the xkeybind part. i even tried switching the option from 4 to one and it doesnt work. i just ran rfkill list all and heres the results

0: phy0: Wireless Lan
        Soft blocked: no
        hard blocked: no
1: asus-wlan: Wireless LAN
       soft blocked: no
       hard blocked: no

---

### Post by chili555 on 2014-12-11
Your wireless isn't hard-blocked, the subject of this thread. There is no need to go further in that area, or, as we say in the US south, don't fix what ain't broke. *Takes another sip of moonshine.*

I suggest you start a new thread along the lines of 'Wireless tries and fails to connect.' Please give us plenty of details, in particular:```
lspci -nn | grep 0280
sudo iwlist wlan0 freq
sudo iwlist wlan0 scan
```If I don't catch it right away, feel free to send me a private message with the link.

---

### Post by NyteRukh on 2014-12-11
ok ty

---

### Post by vanessa4 on 2014-12-30
Hey everyone!

I followed the instructions from posts #1 and #2. After completing the process described in #1, my laptop finally started to recognize my bluetooth mouse (a Microsoft Sculpt Comfort Mouse).

Here is the output I got for my laptop:

```
$ cat /sys/class/dmi/id/product_name
UX301LAA
```

I have noted that the first time my laptop starts, the light in the f2 key is turned on, bluetooth is disabled and WiFi is working. At this point, it is useless to try to activate the bluetooth from the System Settings. Then, I have to recreate the asus_nb_wmi.conf file with the wapf=4 thingy and restart. After I restart, the light in the f2 key is turned off and everything works as expected.

I've found a way to make the bluetooth work without having to restart, but I'm not sure if this will bring more problems... Here is what I've done:

Open a console and run:

```
$ sudoedit /etc/init.d/rc.local
``` 

Add the following lines to *rc.local*, right after the comments:

```
echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf
sudo service bluetooth restart
```

Save the changes made in *rc.local*.

Shutdown or restart.

It seems that just restarting the bluetooth service can replace a complete restart and make the wapf=4 trick work.

---

### Post by chili555 on 2014-12-30
> **vanessa4 said:**
> Hey everyone!

I followed the instructions from posts #1 and #2. After completing the process described in #1, my laptop finally started to recognize my bluetooth mouse (a Microsoft Sculpt Comfort Mouse).

Here is the output I got for my laptop:

```
$ cat /sys/class/dmi/id/product_name
UX301LAA
```

I have noted that the first time my laptop starts, the light in the f2 key is turned on, bluetooth is disabled and WiFi is working. At this point, it is useless to try to activate the bluetooth from the System Settings. Then, I have to recreate the asus_nb_wmi.conf file with the wapf=4 thingy and restart. After I restart, the light in the f2 key is turned off and everything works as expected.

I've found a way to make the bluetooth work without having to restart, but I'm not sure if this will bring more problems... Here is what I've done:

Open a console and run:

```
$ sudoedit /etc/init.d/rc.local
``` 

Add the following lines to *rc.local*, right after the comments:

```
echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf
sudo service bluetooth restart
```

Save the changes made in *rc.local*.

Shutdown or restart.

It seems that just restarting the bluetooth service can replace a complete restart and make the wapf=4 trick work.It is unlikely that re-creating the same file over and over again and one that already exists when you boot is helpful. Also, the usual place to create these files is /etc/rc.local and not /etc/init.d/rc.local. I might also try the wapf=1 thingy instead of =4.

Care to do some cleanup and experimentation??

---

### Post by chili555 on 2014-12-30
Duplicate.

---

### Post by lpnow on 2015-01-08
Hi,

I followed the steps and created the wifitoggle.sh script and used xbindkeys and mapped my F2 

I ran xbindkeys -k then pressed F2 and this is what I placed in my .xbindkeysrc

#turn wifi on and off
"~/.config/wifitoggle.sh"
     m:0x0 + c:68
     F2

Here's the wifitoggle.sh
-------------------
#!/bin/bash
# Script to toggle the wireless blocked/unblocked

# index no. of phy interface
IFACE=`rfkill list all | grep phy | cut -c 1`

# WiFi block state 0=active, 1=blocked
BLOCKED=`rfkill list all | grep -iA1 phy | grep -ic soft.*yes`

if [ $BLOCKED -eq 1 ]; then
    rfkill unblock $IFACE

else
    rfkill block $IFACE
fi

When I press F2 it turns the Wifi off, so I am getting some success, and if I run, iwlist wlan0 scan it shows me this;

wlan0     Interface doesn't support scanning : Network is down

So it's working and turning off, but if I press the F2 again it's not turning back on...

So I don't know how to make it turn back on, I thought the wifitoggle.sh when you press the F2 twice it will turn on and off?

My Wifi is now on and this is what rfkill list all shows;

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

Now I press F2 and it shows;

rfkill list all

0: phy0: Wireless LAN
--->    Soft blocked: yes
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

If I now press F2 again it still shows; Soft blocked: yes

How can I fix this?

THANKS

---

### Post by lpnow on 2015-01-08
Sorry I must of been a sleep, not sure what I was looking at or thinking but when I press F2 twice I see the soft block changing from yes to no :)    

Something I noticed, when I press F2 and it's now on; Soft blocked: no and I then run iwlist wlan0 scan it gives me this;    

wlan0     Interface doesn't support scanning : Network is down 

   I don't understand why it won't show any wifi when it's not blocked and on?    

Here's something nice too, for those that want to map the F2 to xbindkeys with zenity to give you a nice little popup showing you the status... ;)   
Just be sure to change the 'unblock 0' & 'block 0' to the number you need, by checking, running; 'rfkill list' and using your number. 

   ----------------------------------- 

#!/bin/bash

if [ $(rfkill list wifi | grep "Soft blocked: yes" | wc -l) -eq 1 ] ; then
     rfkill unblock 0
     zenity --info --title="WiFi Status" \
     --text="\nWireless Device Enabled" 
else
     rfkill block 0
     zenity --info --title="WiFi Status" \
     --text="\nWireless Device Disabled"
fi

---

### Post by chili555 on 2015-01-08
> **lpnow said:**
> Sorry I must of been a sleep, not sure what I was looking at or thinking but when I press F2 twice I see the soft block changing from yes to no :)    

<snip>May I assume you tried and failed with the asus_nb_mi parameter?

---

### Post by lpnow on 2015-01-08
I'm assuming you mean this?

echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf

My wifi works, I thought that is only if you have hard lock and can't get it to work?

What I'm asking now is if it's 'Soft blocked:no' shouldn't I be able to run 'iwlist wlan0 scan' and have it show the wifi networks?

Because when I press F2 to turn the wifi back on and it's showing 'Soft blocked:no' and I run 'iwlist wlan0 scan' I'm seeing this;

wlan0     Interface doesn't support scanning : Network is down

---

### Post by chili555 on 2015-01-08
If it is blocked in any way, hard(ware) or soft(ware, usually rfkill), it will not scan. > echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.confOr =3 or =1. Many other users report that, after finding the correct parameter for their laptop, F2 works as expected.

---

### Post by jeremy31 on 2015-01-08
Can you post the results of ```
cat /sys/class/dmi/id/product_name
```
the answer might be in the asus_nb_wmi in linux-next

---

### Post by lpnow on 2015-01-08
I'm also not using the networkmanager or Unity, I'm using only Openbox  and wicd.  What's odd is if I press F2, with it as a zenity script I  showed above, I also changed the script to use notify-send so I get a  nice OSD, it does show it's enabled and disabled.  

Isn't running rfkill unblock 0 & rfkill block 0, just doing a softblock, by the script that was posted here for the F2 key to turn on and off? If it is, then playing back and forth between the F2 key and wicd-gtk, shutting the wifi on and off with wicd-gtk, sometimes it's creating a hardblock too  when using the F2 key or wicd...

When I click F2 to enable it and it shows nothing blocked like the  rfkill list below, IF I then open up wicd-gtk it does a scan and shows all the  wifi networks, THEN if I run iwlist wlan0 scan it works, BUT if I don't  open up wicd-gtk, and I first run  iwlist wlan0 scan it shows nothing.  So I don't get how wicd is tied into this since rfkill list shows no  blocks, I'm assuming I should be able to get  iwlist wlan0 scan to show  something, but it won't unless I open up wicd-gtk first...

There is no block when I run iwlist wlan0 scan  

rfkill list  
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


cat /sys/class/dmi/id/product_name 
G75VW  


Hmm

P.S. 

I also just noticed when clicking the Switch Off button in wicd-gtk it changes soft & hardblock, at times it's not consistently the same if I play with it over and over.

Sometimes when I switch it off it's changing being blocked on soft and hard, I'm assuming because of a lack of hardware support.


0: phy0: Wireless LAN
 Soft blocked: yes
 ---> Hard blocked: yes

0: phy0: Wireless LAN
Soft blocked: yes
--> Hard blocked: no

1: asus-wlan: Wireless LAN
 --> Soft blocked: yes

1: asus-wlan: Wireless LAN
 ---> Soft blocked: no

---

### Post by Soyud on 2015-01-08
Hello.

Very silly of my I have opened a new thread and I think my problem must be related with this issue, since my netbook is an ASUS X200M recently purchased here in India.

I have been trying to solve this without result, even with the instruction:  [COLOR=#000000][I]echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf

changing the parameter to 1, 2 and 3.

The nm-applet doesn't work, neither is possible to connect to wifi network, although I can see the networks avaliable.

As far as I know there is no hard or soft block.

I attach the out from the network check script to help.

Thank you for your help




[/I][/COLOR]

---

### Post by Mauro_Miatello on 2015-01-20
Hi
I solved wifi problem, my "cat /sys/class/dmi/id/product_name" output is X550CC
I've problem with shutdown, Ubuntu 14.10 start shutting down and stop with logo, now hardware power off

---

### Post by chili555 on 2015-01-20
> **Mauro_Miatello said:**
> Hi
I solved wifi problem, my "cat /sys/class/dmi/id/product_name" output is X550CC
I've problem with shutdown, Ubuntu 14.10 start shutting down and stop with logo, now hardware power offIf you need help with your shutdown problem, please post here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

### Post by dougkenyon34 on 2015-01-23
Thank you so much for this workaround. I am refurbishing a crashed ASUS X551C laptop for a needy family and I have been driven nuts by this problem. Thank you, thank you, thank you!

As suggested, I added myself to the affected list. My product_name is X551CAP.

---

### Post by Vu_Hoang on 2015-02-08
When i restart pc, it don't work.
Only when I login xbindkeys was running, killing xbindkeys & restarting xbindkeys would it work again.

---

### Post by chili555 on 2015-02-08
> **Vu_Hoang said:**
> When i restart pc, it don't work.
Only when I login xbindkeys was running, killing xbindkeys & restarting xbindkeys would it work again.What, exactly are the commands you issue to stop and start xbindkeys? Maybe we can simply drop them into rc.local.

---

### Post by AllesLuge on 2015-03-27
Worked for me. Thanks! X550VB

---

### Post by ehood2 on 2015-04-01
I have asus D552C , at first i didnt have a driver for my NIC , i installad a driver, and now I have an hard block.
wiil the soultion work for me?
althogh that the the answer to Q3 is no, asus_nb_wmi is appearing but the driver doesnt.
[ATTACH=CONFIG]261029[/ATTACH]

---

### Post by praseodym on 2015-04-01
Try the solution and install the driver according to this:

[http://ubuntuforums.org/showthread.php?t=2250569&highlight=mediatek+mt7630e](http://ubuntuforums.org/showthread.php?t=2250569&highlight=mediatek+mt7630e)

---

### Post by ehood2 on 2015-04-07
thanks it worked.

---

### Post by samuelnevesmarques on 2015-04-29
X550JK
My connection stops working randomly. Before, after stopping, the network I was using would even disappear and not appear again until I rebooted or came back from sleep mode. After using jeremy31's fix from [here]("http://ubuntuforums.org/showthread.php?t=2245164&p=13222964#post13222964") now it continues to stop working but without the network ever disappearing or notifying the connection is down.
I've added "options asus_nb_wmi=4" to the asus_nb_wmi.conf file even though when running "rfkill list all" it doesn't show any "Hard blocked: yes", and sadly this wifi random disconnects persist.

---

### Post by jeremy31 on 2015-04-29
> **samuelnevesmarques said:**
> X550JK
My connection stops working randomly. Before, after stopping, the network I was using would even disappear and not appear again until I rebooted or came back from sleep mode. After using jeremy31's fix from [here]("http://ubuntuforums.org/showthread.php?t=2245164&p=13222964#post13222964") now it continues to stop working but without the network ever disappearing or notifying the connection is down.
I've added "options asus_nb_wmi=4" to the asus_nb_wmi.conf file even though when running "rfkill list all" it doesn't show any "Hard blocked: yes", and sadly this wifi random disconnects persist.

I would try ```
[COLOR=#545454][FONT=arial]echo "[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**options <driver-name>**[/FONT][/COLOR][COLOR=#545454][FONT=arial] fwlps=N ips=N" | sudo tee /etc/modprobe.d/<driver-name>.[/FONT][/COLOR][COLOR=#545454][FONT=arial]conf
```

[/FONT][/COLOR]Replace <driver-name> with whatever module your wifi is using and reboot

---

### Post by samuelnevesmarques on 2015-05-08
> **jeremy31 said:**
> I would try ```
[COLOR=#545454][FONT=arial]echo "[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**options <driver-name>**[/FONT][/COLOR][COLOR=#545454][FONT=arial] fwlps=N ips=N" | sudo tee /etc/modprobe.d/<driver-name>.[/FONT][/COLOR][COLOR=#545454][FONT=arial]conf[/FONT][/COLOR]
```[COLOR=#545454][FONT=arial]

[/FONT][/COLOR]Replace <driver-name> with whatever module your wifi is using and reboot

Meanwhile made update to ubuntu 15. Tried this and gave it some time.
The random disconnects still occur but seem to be less frequent. It's solvable by using the key to toggle off and on the wifi.

---

### Post by bartek-zdanowski on 2015-06-10
Hi.
It helped for Ubuntu 14.04 LTS, Asus B451JA

---

### Post by afibanez on 2015-06-30
Hi!

Didnt work for Asus B551LA. My rfkill output:

rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

---

### Post by jeremy31 on 2015-06-30
Yours just shows a soft block so ```
rfkill unblock wifi
``` or using the FN combo should enable it

---

### Post by praseodym on 2015-06-30
Obviously, there is an acer module loaded:
```

lsmod
```
If it shows "acer-wmi" blacklist it
```

echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
and reboot

---

### Post by lazarus3 on 2015-12-04
Hello , 
Does this work on Acer laptop as well or only for Asus

Thank you

---

### Post by lazarus3 on 2015-12-04
Hello again,
 
And then I mean the part "setting a hot key "

Greetings

---

### Post by lazarus3 on 2015-12-04
Hello, 

My problem with wifi-switch on Acer Aspire 5715Z laptop not working under Lubuntu was solved by installing :
bcmwl-kernel-source
b43-fwcutter
firmware-b43-installer
firmware-b43legacy-installer
After doing so the switch was lighting up as it should and I was able to connect to wifi .

Thanks anyway and greets .

---

### Post by SoftVision on 2015-12-08
Setting options asus_nb_wmi wapf=4 works for me and gets rid of the only major issue with my Asus ZenBook - it hangs on resume if I let it suspend overnight. The downside to this fix/workaround is that when I resume after the overnight suspend, I lose about 15% battery charge. Would it be better to set it to 0 instead? I'm not sure which option would be best in this case.

---

### Post by chili555 on 2015-12-08
> **SoftVision said:**
> Setting options asus_nb_wmi wapf=4 works for me and gets rid of the only major issue with my Asus ZenBook - it hangs on resume if I let it suspend overnight. The downside to this fix/workaround is that when I resume after the overnight suspend, I lose about 15% battery charge. Would it be better to set it to 0 instead? I'm not sure which option would be best in this case.Not to be too blunt, but you are the one with the device and so you are the one best qualified to try it and report back to us.

Please try it and let us know. 

Here is what the sparse documentation says:```
/*
   * WAPF defines the behavior of the Fn+Fx wlan key
   * The significance of values is yet to be found, but
   * most of the time:
   * Bit | Bluetooth | WLAN
   *  0  | Hardware  | Hardware
   *  1  | Hardware  | Software
   *  4  | Software  | Software
   */
```I think that suggests that the verified values are 0, 1 and 4. Being a bit of a tinkerer, I'd try 2, 3 and 5 just because I could, if I had the device. I'd keep notes and find the best value and then report my findings here for the benefit of the searchers.

We look forward to your report.

---

### Post by SoftVision on 2015-12-08
I read the driver code [here]("http://lxr.free-electrons.com/source/drivers/platform/x86/asus-nb-wmi.c") and I think I understand what's happening and why there are compatibility issues. If it cannot identify the laptop model, it defaults to 0. If it can identify the laptop model based on the entries listed, it sets a value of 4 which allows for software control for both bluetooth and wireless. This driver essentially can be extended to other laptops as long as we have the system vendor and product name for each laptop. The real meat of the code is [here]("http://lxr.free-electrons.com/source/drivers/platform/x86/asus-wmi.c") in the asus-wmi driver, which handles the actual switching. 1, 2 and 4 seem to be values chosen by the author of the code to handle certain cases in asus-nb-wmi but it would still accept 2, 3 and 5 from what I can read. It just wouldn't do anything with it.

I'm going to try setting the value to 1 tonight so as to see whether the bluetooth or wireless is causing the drain. I think the wireless isn't going to sleep because I saw some notifications on a Chrome tab already present after the resume in the few seconds before my wireless re-connected. I'm also going to try blacklisting asus-wmi. All this time I've blacklisted asus-nb-wmi which doesn't really do anything by default to my laptop to begin with.

**Update (12/09):** I just blacklisted asus-wmi and rebooted my laptop a few times. I turned bluetooth off by toggling the applet in the notification area, but after each reboot the bluetooth was back on again. This means that disabling the driver is as good as applying the 0 value and giving control to the hardware. I'm not familiar with how to contribute to kernel code. I'll look into it and contact the author to see if I can help reorganize that code a bit. It might be worth having a case '3' which enables software bluetooth control and hardware wireless control. This would essentially solve my problem and remember my bluetooth settings. I don't think the actual toggle of Fn+F2 is working for me as well. To fix that one would probably have to look at the asus-wmi code I linked above.

**Update (12/10):** Unfortunately even with a value of 4 I got the resume problem again and my wireless stopped working until I messed around with the BIOS to get it to work.

---

### Post by arn02 on 2015-12-09
I test these solutions but nothing fix my problem.
I can activate/deactivate Wifi with hot key (F3) but no networks...
I open a thread with my wireless script: [http://ubuntuforums.org/showthread.php?t=2305816](http://ubuntuforums.org/showthread.php?t=2305816)

Thanks you :-)

---

### Post by Thedy_Skld on 2016-02-22
My laptop model is: X75VC

---

### Post by Ruben_Marques on 2016-04-02
Thank you so much for this fix! Output of cat /sys/class/dmi/id/product_name is

B451JA

The complete model is a

ASUS B451JA-FA074G

---

### Post by eiricur on 2016-04-10
I'm struggling with this, and would appreciate advice on what to try next.

I'm running Linux on an ASUS N61JQ Notebook, and cannot use my WiFi network.  Airplane Mode is on, and the option to disable it is greyed out.

When I run *rfkill list* I can see that "phy0: Wireless LAN" has these settings:
  
[LIST]
[*]Soft blocked: no 
[*]Hard blocked: yes
[/LIST]
 On the ASUS Notebook I should supposedly be able to disable the hard block by using *Fn+F2*. However for some reason, this only toggles the soft block.

I've tried *rfkill unblock all*, but it doesn't have an effect.

As you can see in the code below, the driver "asus_nb_wmi" isn't loaded.

```

root@eiricur:~# rfkill list
 0: phy0: Wireless LAN
     Soft blocked: no
     Hard blocked: yes
 root@eiricur:~# lspci -nnk | grep -A2 0280
 03:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
     Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
     Kernel driver in use: ath9k
 root@eiricur:~# lsmod | grep -e ath9k -e asus
 ath9k                  94208  0
 ath9k_common           32768  1 ath9k
 ath9k_hw              446464  2 ath9k_common,ath9k
 ath                    32768  3 ath9k_common,ath9k,ath9k_hw
 mac80211              626688  1 ath9k
 cfg80211              540672  4 ath,ath9k_common,ath9k,mac80211
 asus_laptop            32768  0
 sparse_keymap          16384  1 asus_laptop
 rfkill                 24576  6 cfg80211,asus_laptop,bluetooth
 input_polldev          16384  1 asus_laptop
 video                  36864  1 asus_laptop

```

I tried Mr chili555's suggestion of running this code:
```
echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf
```

This generated the file "asus_nb_wmi.conf" in the correct directory. I rebooted, but there wasn't any noticable change. I tried using different values for the wapf parameter (0 and 1) and rebooting, but that didn't work as well.

**The driver still doesn't show when I run lsmod | grep -e ath9k -e asus.**

I've tried updating the BIOS and restoring default settings, but that doesn't work either.

Thanks for your time.

---

### Post by chili555 on 2016-04-10
> As you can see in the code below, the driver "asus_nb_wmi" isn't loaded.
Because of that, this technique will be ineffective, as you saw:> I tried Mr chili555's suggestion of running this code:
Code:

echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf

This generated the file "asus_nb_wmi.conf" in the correct directory. I rebooted, but there wasn't any noticable change. I tried using different values for the wapf parameter (0 and 1) and rebooting, but that didn't work as well.Let's remove it:```
sudo rm /etc/modprobe.d/asus_nb_wmi.conf
```We see that the module asus_laptop *IS* loaded. Let's try a parameter on it:```
sudo -i
echo "options asus-laptop wlan_status=1"  >  /etc/modprobe.d/asus-laptop.conf
modprobe -r asus-laptop
modprobe asus-laptop
exit
```If there is no change, please try a reboot.

---

### Post by eiricur on 2016-04-10
Thanks for the suggestion. I used your exact commands, and rebooted, though unfortunately the problem persists.

I've verified that the "asus_nb_wmi.conf" document was removed, and that the "asus-laptop.conf" document has the parameter "options asus-laptop wlan_status=1".

P.S. The wireless network worked when I was running Windows 7, but it has never worked on either Ubuntu or Kali. I find it particularly weird that Fn+F2 toggles the soft lock, and not the hard lock.

---

### Post by chili555 on 2016-04-10
May I see:```
modinfo asus-laptop | grep parm
uname -r

```Thanks.

---

### Post by eiricur on 2016-04-10
```
root@eiricur:~# modinfo asus-laptop | grep parm

 parm:           wapf:WAPF value (uint)
 parm:           wled_type:Set the wled type on boot (unknown, led or rfkill). default is unknown (charp)
 parm:           bled_type:Set the bled type on boot (unknown, led or rfkill). default is unknown (charp)
 parm:           wlan_status:Set the wireless status on  boot (0 = disabled, 1 = enabled, -1 = don't do anything). default is -1  (int)
 parm:           bluetooth_status:Set the wireless  status on boot (0 = disabled, 1 = enabled, -1 = don't do anything).  default is -1 (int)
 parm:           wimax_status:Set the wireless status on  boot (0 = disabled, 1 = enabled, -1 = don't do anything). default is -1  (int)
 parm:           wwan_status:Set the wireless status on  boot (0 = disabled, 1 = enabled, -1 = don't do anything). default is -1  (int)
 parm:           als_status:Set the ALS status on boot (0 = disabled, 1 = enabled). default is 0 (int)
 root@eiricur:~# uname -r
 4.3.0-kali1-amd64
```

---

### Post by chili555 on 2016-04-10
Please try this:```
sudo -i
echo "options asus-laptop wapf=4"  >  /etc/modprobe.d/asus-laptop.conf
exit
```Reboot.

This may take some experimentation, unfortuneately.

- - - - - - - - 

Possible reference: [http://lxr.free-electrons.com/source/drivers/platform/x86/asus-laptop.c?v=4.3](http://lxr.free-electrons.com/source/drivers/platform/x86/asus-laptop.c?v=4.3)> 71 /*
 72  * WAPF defines the behavior of the Fn+Fx wlan key
 73  * The significance of values is yet to be found, but
 74  * most of the time:
 75  * Bit | Bluetooth | WLAN
 76  *  0  | Hardware  | Hardware
 77  *  1  | Hardware  | Software
 78  *  4  | Software  | Software
 79  */

---

### Post by eiricur on 2016-04-10
I set wapf=4, then rebooted. Used rfkill list to confirm that there was still a hard block. Hit Fn+F2 followed by another rfkill list to check that it still only toggled the soft block.

I then set wapf=1, rebooted, etc. Fn+F2 still only toggled the soft block.

I then set wapf=0, rebooted, etc. Fn+F2 still only toggled the soft block.

Bizarre. Incidentally, the WiFi LED is always activated, never responding to Fn+F2.

Thanks for your advice so far!

---

### Post by chili555 on 2016-04-10
Arrrghh!!!

Let's try:```
sudo -i
echo "options asus-laptop wapf=4 wlan_status=1"  >  /etc/modprobe.d/asus-laptop.conf
exit
```Of course, also try wapf=0 and =1; in all cases with a reboot.

We might also try simply removing the module altogether:```
sudo modprobe -r asus-laptop
sudo rfkill unblock all
rfkill list all
```Fingers crossed!

---

### Post by eiricur on 2016-04-11
If you don't want to hate me, dear chili555, you should stop reading this post and consider the issue resolved. O:)



Turns out the ASUS N61JQ Notebook has *two* physical WiFi switches. In addition to Fn+F2, there's a well-camouflaged tiny slider on the left-hand side.

So... feel free to rage at me. Aside from that, thanks for all the advice, I definitely learned from it.

> **chili555 said:**
> Arrrghh!!!

Indeed!

---

### Post by chili555 on 2016-04-11
I don't hate you nor will I rage. Everyone, even me, makes an occasional understandable mistake. I am just happy that it is now working as expected.

Have fun!

---

### Post by wesley21 on 2016-05-10
Hi, I am new to linux and I have problem using the wifi in my Asus computer k450j series. The wifi card model is atheros AR9485WB-EG. I tried the methods in the forum and it isn't working.
when I type rfkill list in the terminal, this is the output.


0 : hci0 : bluetooth
      Soft blocked : no
      Hard blocked : no
1: phy 0: wireless lan
     Soft blocked : no
      Hard blocked : no
2: Acer-wireless : wireless lan
     Soft blocked : yes
      Hard blocked : no

hope you can help me solve this problem

---

### Post by jeremy31 on 2016-05-11
> **wesley21 said:**
> Hi, I am new to linux and I have problem using the wifi in my Asus computer k450j series. The wifi card model is atheros AR9485WB-EG. I tried the methods in the forum and it isn't working.
when I type rfkill list in the terminal, this is the output.


0 : hci0 : bluetooth
      Soft blocked : no
      Hard blocked : no
1: phy 0: wireless lan
     Soft blocked : no
      Hard blocked : no
2: Acer-wireless : wireless lan
     Soft blocked : yes
      Hard blocked : no

hope you can help me solve this problem

Please post results for ```
lsmod | grep acer
```  If it is an Asus laptop, I doubt an acer module is doing any good

---

### Post by wesley21 on 2016-05-13
> **jeremy31 said:**
> Please post results for ```
lsmod | grep acer
``` If it is an Asus laptop, I doubt an acer module is doing any good


I am guessing the Acer module is the problem but I have no idea how to fix it. The output is as followed

[IMG]http://ubuntuforums.org/webkit-fake-url://e560dfed-c993-4858-b1d3-44a953d68a62/imagejpeg[/IMG]


acer_wmi         20480 0
sparse_keymap 16384 2   acer_wmi, asus_wmi
wmi                 20480 4   acer_wmi,mxm_wmi, nouveau, asus_wmi
video               40960  4  i915, acer_wmi, nouveau, asus_wmi



this forum need to have a insert photo function (without the use of URL). 

Anyway thanks for your prompt reply!! :D

---

### Post by jeremy31 on 2016-05-13
> **wesley21 said:**
> I am guessing the Acer module is the problem but I have no idea how to fix it. The output is as followed

[IMG]http://ubuntuforums.org/webkit-fake-url://e560dfed-c993-4858-b1d3-44a953d68a62/imagejpeg[/IMG]


acer_wmi         20480 0
sparse_keymap 16384 2   acer_wmi, asus_wmi
wmi                 20480 4   acer_wmi,mxm_wmi, nouveau, asus_wmi
video               40960  4  i915, acer_wmi, nouveau, asus_wmi



this forum need to have a insert photo function (without the use of URL). 

Anyway thanks for your prompt reply!! :D
You just need to ```
echo "blacklist asus_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Reboot

---

### Post by wesley21 on 2016-05-13
I tried using this method. It is still the same.

---

### Post by jeremy31 on 2016-05-13
Sorry, wrong command,

You can edit with ```
sudo gedit /etc/modprobe.d/blacklist.conf
```
And change the blacklist asus_wmi to ```
blacklist acer_wmi
```

Save, exit program and reboot

---

### Post by wesley21 on 2016-05-14
It's working!! Thank you so much! I have a problem with watching video using firefox. Is there a driver for it?

---

### Post by kuramot on 2016-08-18
The two methods provided: ```
echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf
``` and Setting a HotKey to Toggle the WiFi On/Off do not work for me.

The hotkey method requires sudo and only affects soft blocked.

---

### Post by chili555 on 2016-08-19
> **kuramot said:**
> The two methods provided: ```
echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf
``` and Setting a HotKey to Toggle the WiFi On/Off do not work for me.

The hotkey method requires sudo and only affects soft blocked.This is an old, long thread with several posters and it's sometimes hard to keep up with whose details are whose. Please start a new thread and include the data here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by kuramot on 2016-08-19
> **chili555 said:**
> This is an old, long thread with several posters and it's sometimes hard to keep up with whose details are whose. Please start a new thread and include the data here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)
I have posted it here. Thanks. [https://ubuntuforums.org/showthread.php?t=2334369](https://ubuntuforums.org/showthread.php?t=2334369)

---

### Post by worm359 on 2016-09-28
This workaround helped for me. 
Output for 
cat /sys/class/dmi/id/product_name
is "K501UX"

---

### Post by ivodvb on 2016-10-06
Thanks for the help!

Suspending Ubuntu helped and the workaround permanently fixed it!
Workaround used: > echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf

Laptop model: X302UA

---

### Post by mrrednas on 2016-10-08
Thank you very much!!!!!! I was searching forums for a while now.

My product name: K401UQ

---

### Post by k1ana on 2016-10-11
The suspend/resume solution worked for my Asus K501U with Ubuntu 16.04 installed on it. Thank you.

Any insight as to why a simple suspend/resume cycle toggles the "Hard blacked" flag back off?

---

### Post by visualsilence on 2016-10-14
[COLOR=#000000]Thanks! This workaround solved my issue!
[/COLOR]
[COLOR=#000000]Output for [/COLOR]
```
[COLOR=#000000]cat /sys/class/dmi/id/product_name[/COLOR]
```
[COLOR=#000000]is "K501UW"[/COLOR]

---

### Post by kuramot on 2016-10-24
This workaround did not work for me.
Model: Asus X450CC

---

### Post by chili555 on 2016-10-24
> **kuramot said:**
> This workaround did not work for me.
Model: Asus X450CCPlease start a new question and we'll be happy to try to help. Please include:```
rfkill list all
lsmod | grep -e asus -e wmi
```Thanks.

---

### Post by leizmonk on 2016-11-03
Hey just wanted to add to this thread, this fix worked like a charm for my K501UW

---

### Post by lamino144 on 2017-01-19
> **varunendra said:**
> [CENTER][SIZE=3][COLOR=#800000]**_Setting a HotKey to Toggle the WiFi On/Off_**[/COLOR][/SIZE]** (Alternative to the Fn+F2 switch)**[/CENTER]

Until this issue is fixed with newer updates, you may use "xbindkeys" tool to set a hotkey (can be a single key or a key-combination) of your choice to toggle the WiFi enabled/disabled.

This is how -

[COLOR=#0000CD]**A. _Create a Script to do it smartly_ :**[/COLOR][INDENT]**1)** First, we create a script (for ease of use, and so that we can toggle it on/off using the same hotkey) -
```
#!/bin/bash
# Script to toggle the wireless blocked/unblocked

# index no. of phy interface
IFACE=`rfkill list all | grep phy | cut -c 1`

# WiFi block state 0=active, 1=blocked
BLOCKED=`rfkill list all | grep -iA1 phy | grep -ic soft.*yes`

if [ $BLOCKED -eq 1 ]; then
    rfkill unblock $IFACE

else
    rfkill block $IFACE
fi
```
Copy-paste the contents of the above box in a text file and save this file in your Home directory with the name - "**[COLOR=#0000CD]wifitoggle.sh[/COLOR]**". Make sure the first line is (without double quotes) "[COLOR=#0000CD]**#!/bin/bash**[/COLOR]" and last one is "[COLOR=#0000CD]**fi**[/COLOR]".

**2)** Make the script executable by running the following command in a terminal -
```
chmod +x wifitoggle.sh
```

**3)** Run the following command to Create a symlink to this script in /bin directory -
```
sudo ln -s $HOME/wifitoggle.sh /bin
```[/INDENT]

Now proceed to binding it with a hotkey as follows -

[COLOR=#0000CD]**B. _Bind the Script with a HotKey of your choice_ :**[/COLOR][INDENT]**1)** Install ***xbindkeys-config*** (a GUI frontend to xbindkeys - the program that captures and binds hotkeys with commands) -
```
sudo apt-get install xbindkeys-config
```

**2)** Create a default config file for it (else it would crash on key capture step) -
```
xbindkeys --defaults > ~/.xbindkeysrc
```

**3)** Run the program from terminal or "Alt+F2" (because it does not create a launcher in Unity dash) -
```
xbindkeys-config
```
let the terminal running in the background..
In the GUI box that opens, 3 example shortcuts are already present. You may leave them.

**4)** Click on "[COLOR=#0000CD]**New**[/COLOR]" button at the bottom of the GUI.

**5)** In the right hand pane of the GUI, fill in a suitable name in the "[COLOR=#0000CD]**Name**[/COLOR]" field, e.g. "**Toggle Wifi**"

**6)** Click on "[COLOR=#0000CD]**Get Key**[/COLOR]" button. This will open a tiny blank box doing nothing but waiting for your input.

**7)** Press the desired key (or key combination) that you want for toggling Wifi on/off. For example, "F3" key (as it remains mostly unused). The tiny box will disappear and the key will be recorded.

**8)** In the "[COLOR=#0000CD]**Action**[/COLOR]" field, type this -
```
/bin/bash /bin/wifitoggle.sh
```

**9)** Click on "[COLOR=#0000CD]**Apply**[/COLOR]" button and test the hotkey to see if it works as expected.

**10)** Click on "[COLOR=#0000CD]**Save & Apply & Exit**[/COLOR]" to save the new hotkey to the default file and exit.[/INDENT]

From now on, as soon as you will press this key or the key-combination, the wifi will change its state from On to Off, or Off to On.

The Fn key doesn't seem to be noticed by any key capture program I could find (probably that's why it is considered "Hardware Switch"), so it's not possible to use it yet.


Once more, I'd request anyone who needs this workaround to **submit a bug report** against the problem, **or** add themselves to the "**Affects Me**" list, and point to this thread as a possible workaround.

The stronger it gets reported, the sooner we'll get it fixed, thus not requiring such crude workarounds.

Actually, you can enable Fn+F2 by telling acpi to run a command like **rfkill. **In my case Ubuntu was, in fact, capturing the event, but the action was a useless script.

So here's a fix to that:

```
 
sudo apt-get install rfkill #make sure you've got rfkill installed  
sudo sed "s/action=.*/action=rfkill block wifi/" /etc/acpi/events/asus-wireless-off
sudo sed "s/action=.*/action=rfkill unblock wifi/" /etc/acpi/events/asus-wireless-on 
```

---

### Post by senapskaptenen on 2017-11-02
Thank you for a solution that finally worked, and for a very well-written tutorial!

My product id: B451JA
Using Linux mint 18.2

---

