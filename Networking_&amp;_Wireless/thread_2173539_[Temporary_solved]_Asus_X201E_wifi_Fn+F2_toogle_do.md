---
title: "[Temporary solved] Asus X201E wifi Fn+F2 toogle doesn't work"
date: 2013-09-10
forum: Networking &amp; Wireless
---

### Post by dupont2 on 2013-09-10
Hi,

I've just install Ubuntu 13.04 in dual boot beside W8 on a Asus X201E netbook.
I noticed that the wifi Fn+F2 toogle doesn't work.
The wifi is always active and I can't switch it off.
The wifi led is off even if wifi connection is on.
I looked on the net and it seem's to be an old bug with asus laptop.

Notes : I installed yesterday 3.11 kernel but it has not solved the issue.
It is fine with W8.

Any workaround ?

---

### Post by chili555 on 2013-09-10
Perhaps there is a workaround. Please open a terminal and run and post:```
rfkill list all
lsmod | grep asus
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Thanks.

---

### Post by dupont2 on 2013-09-10
Hi Chili 555, This is what I get,

```
rfkill list all
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

```
lsmod | grep asus
asus_nb_wmi            16990  0 
asus_wmi               24794  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
wmi                    19256  1 asus_wmi
video                  19574  2 i915,asus_wmi
```

```
lspci -nn | grep 0280
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
```

---

### Post by varunendra on 2013-09-10
Welcome to the forums dupont2 !

You might wish to use 'Code' tags instead of 'Quote' tags for posting command outputs. It preserves the formatting of the output, thus making it more readable.

Please follow the "Using Code tags" link in my signature below to see how to use it. You may then wish to edit your above post to change the tags. :)

**PS:**
As mentioned in this thread : [http://ubuntuforums.org/showthread.php?t=2172434](http://ubuntuforums.org/showthread.php?t=2172434) , does your wifi get enabled if you send the laptop to sleep, then wake it up again? Just confirming, can't dare to step over Dr. Chili's approaches :)

---

### Post by dupont2 on 2013-09-10
> **varunendra said:**
> Welcome to the forums dupont2 !

**PS:**
As mentioned in this thread : [http://ubuntuforums.org/showthread.php?t=2172434](http://ubuntuforums.org/showthread.php?t=2172434) , does your wifi get enabled if you send the laptop to sleep, then wake it up again? Just confirming, can't dare to step over Dr. Chili's approaches :)

Thanks Varunendra,

Wifi is always enable even after waking up.

---

### Post by chili555 on 2013-09-10
Oh, boy! New, unknown problems! We are pioneers! I love it!

I notice this module is loaded:> lsmod | grep asus
[COLOR="#FF0000"]asus_nb_wmi  [/COLOR]          16990  0 
asus_wmi               24794  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
wmi                    19256  1 asus_wmi
video                  19574  2 i915,asus_wmimodinfo for that module says:```
$ modinfo asus_nb_wmi
filename:       /lib/modules/3.11.0-4-generic/kernel/drivers/platform/x86/asus-nb-wmi.ko
alias:          wmi:0B3CBB35-E3C2-45ED-91C2-4C5A6D195D1C
license:        GPL
description:   [COLOR="#FF0000"] Asus Notebooks WMI Hotkey Driver[/COLOR]
author:         Corentin Chary <corentin.chary@gmail.com>
srcversion:     67514DF02FC4A206C47D0F5
depends:        asus-wmi
intree:         Y
vermagic:       3.11.0-4-generic SMP mod_unload modversions 686 
parm:           [COLOR="#FF0000"]wapf[/COLOR]:WAPF value (uint)

```And the C code says:> 43 /*
 44  * WAPF defines the behavior of [COLOR="#FF0000"]the Fn+Fx wlan key[/COLOR]
 45  * The significance of values is yet to be found, but
 46  * most of the time:
 47  * Bit | Bluetooth | WLAN
 48  *  0  | Hardware  | Hardware
 49  *  1  | Hardware  | Software
 50  *  4  | Software  | Software
 51  */Wow! Just what we are looking for, hopefully. Let's see what we can do. Please open a terminal and do:```
sudo -i
echo "options asus_nb_wmi wapf=0" > /etc/modprobe.d/asus.conf
exit
```Since the writers of the C code are not sure the exact correct value, we will have to experiment a bit. Now do:```
sudo modprobe -rf asus-wmi
sudo modprobe -rf asus-nb-wmi
sudo modprobe asus-nb-wmi
```Any improvement? If not, we'll try another value for wapf.

---

### Post by dupont2 on 2013-09-11
Hi Chili555, It says :

```
fred@fred-X201EP:~$ sudo -i
[sudo] password for fred: 
root@fred-X201EP:~# echo "options asus_nb_wmi wapf=0" > /etcmodprobe.d/asus.conf
-bash: /etcmodprobe.d/asus.conf: Aucun fichier ou dossier de ce type
root@fred-X201EP:~# 
```
[I]
_Aucun fichier ou dossier de ce type_[/I] in French which means not such file found.

You forgot the / after etc => ```
echo "options asus_nb_wmi wapf=0" > /etc/modprobe.d/asus.conf
```

```
root@fred-X201EP:~# echo "options asus_nb_wmi wapf=0" > /etc/modprobe.d/asus.conf
root@fred-X201EP:~# exit
déconnexion
fred@fred-X201EP:~$ sudo modprobe -rf asus-wmi
[sudo] password for fred: 
FATAL: Module asus_wmi is in use.
fred@fred-X201EP:~$ ^C
```

Fatal, so I stopped here.

---

### Post by varunendra on 2013-09-11
> **dupont2 said:**
> 
```

root@fred-X201EP:~# echo "options asus_nb_wmi wapf=0" > **[COLOR="#FF0000"]/etcmodprobe.d[/COLOR]**/asus.conf
```
...in French which means not such file found.

Because there is a minor typo in the command. It is /etc/modprobe.d. Please correct to that and try again -
```
echo "options asus_nb_wmi wapf=0" > **/etc[COLOR="#FF0000"]/[/COLOR]modprobe.d**/asus.conf
```

**EDIT:**
So you already got it before I could post and take the credit :D

---

### Post by varunendra on 2013-09-11
You should post the updates in new posts, otherwise people can't notice there is an update, and thus may not reply (I revisited for another reason and noticed your 2nd update) -
> **dupont2 said:**
> 
```
fred@fred-X201EP:~$ sudo modprobe -rf asus-wmi
[sudo] password for fred: 
FATAL: Module asus_wmi is in use.
fred@fred-X201EP:~$ ^C
```

Fatal, so I stopped here.

..because asus-wmi is being used by asun-nb-wmi. Just go ahead with the second command
```
sudo modprobe -rfv asus-nb-wmi
sudo modprobe -v asus-nb-wmi
```
*(I added -v just out of habit. It makes the command verbose, so you can see what is happening in the background)*

It will automatically remove-reload asus-wmi as well, since it is a dependency. Go ahead and let us know if there's a progress. I'm just filling in until dr.chilli comes back.

---

### Post by dupont2 on 2013-09-11
Varunenedra,

the result,

```
fred@fred-X201EP:~$ sudo modprobe -rfv asus-nb-wmi
[sudo] password for fred: 
rmmod asus_nb_wmi
rmmod asus_wmi
rmmod wmi
rmmod sparse_keymap
fred@fred-X201EP:~$ sudo modprobe -v asus-nb-wmi
insmod /lib/modules/3.11.0-031100-generic/kernel/drivers/platform/x86/wmi.ko 
insmod /lib/modules/3.11.0-031100-generic/kernel/drivers/input/sparse-keymap.ko 
insmod /lib/modules/3.11.0-031100-generic/kernel/drivers/platform/x86/asus-wmi.ko 
insmod /lib/modules/3.11.0-031100-generic/kernel/drivers/platform/x86/asus-nb-wmi.ko wapf=0 
fred@fred-X201EP:~$ 
```

---

### Post by varunendra on 2013-09-11
Outputs are as expected. So is there any change in behaviour? If not, the other values to try for parameter **wapf** are **1** and **4**.
Means the line "**options asus_nb_wmi wapf=[COLOR="#FF0000"]0[/COLOR]**" may be changed to "**options asus_nb_wmi wapf=[COLOR="#FF0000"]1[/COLOR]**" or "**options asus_nb_wmi wapf=[COLOR="#FF0000"]4[/COLOR]**" - whichever (if) works.

I am using the same driver myself (I have an Asus X54C laptop), but I have blacklisted the asus-nb-wmi driver due to some other kind of issue (with bluetooth). I may try the parameters myself but since your problem is different, you may have to try these values yourself.

So, to be extra sure, reboot if just unloading-loading the module (what you just did above) doesn't work, and see if there is a change in behaviour. If not, change the parameter to "1" and try again. To quickly change it from "0" to "1" from terminal -
```
sudo sed -i 's/0/1/' /etc/modprobe.d/asus.conf
```
Similarly, to change again (if "1" didn't work either) from "1" to "4" -
```
sudo sed -i 's/1/4/' /etc/modprobe.d/asus.conf
```

**EDIT:** Repeat the "modprobe -rfv" and "modprobe -v" commands after each change, followed by a reboot if behaviour doesn't change. Check Fn+F2 after moprobe, after reboot.

Try these and keep the fingers crossed, I already am here.. ;)

---

### Post by dupont2 on 2013-09-11
Results

```

fred@fred-X201EP:~$ sudo sed -i 's/1/4/' /etc/modprobe.d/asus.conf
[sudo] password for fred: 
fred@fred-X201EP:~$ sudo modprobe -rfv asus-nb-wmi
rmmod asus_nb_wmi
rmmod asus_wmi
rmmod wmi
rmmod sparse_keymap
fred@fred-X201EP:~$ sudo modprobe -v asus-nb-wmi
insmod /lib/modules/3.8.0-31-generic/kernel/drivers/platform/x86/wmi.ko 
insmod /lib/modules/3.8.0-31-generic/kernel/drivers/input/sparse-keymap.ko 
insmod /lib/modules/3.8.0-31-generic/kernel/drivers/platform/x86/asus-wmi.ko 
insmod /lib/modules/3.8.0-31-generic/kernel/drivers/platform/x86/asus-nb-wmi.ko wapf=4 
fred@fred-X201EP:~$ 

```

Same trial but with 
```
sudo sed -i 's/0/1/' /etc/modprobe.d/asus.conf 
```
Before and after reboot => Fn+F2 not OK

---

### Post by chili555 on 2013-09-11
> fred@fred-X201EP:~$ sudo sed -i 's/1/4/' /etc/modprobe.d/asus.conf
[sudo] password for fred: 
fred@fred-X201EP:~$ sudo modprobe -rfv asus-nb-wmi
rmmod asus_nb_wmi
rmmod asus_wmi
rmmod wmi
rmmod sparse_keymap
fred@fred-X201EP:~$ sudo modprobe -v asus-nb-wmi
insmod /lib/modules/3.8.0-31-generic/kernel/drivers/platform/x86/wmi.ko 
insmod /lib/modules/3.8.0-31-generic/kernel/drivers/input/sparse-keymap.ko 
insmod /lib/modules/3.8.0-31-generic/kernel/drivers/platform/x86/asus-wmi.ko 
insmod /lib/modules/3.8.0-31-generic/kernel/drivers/platform/x86/asus-nb-wmi.ko wapf=4 
fred@fred-X201EP:~$

Same trial but with
Code:

sudo sed -i 's/0/1/' /etc/modprobe.d/asus.conf

You did them out of order. Varun's first command was, roughly, 'replace 0 with 1.' However, you ran 'replace 1 with 4.' Since there was no 1 in there, I'm sure the first command did nothing. Let's take a step back and see what the file says now:```
cat /etc/modprobe.d/asus.conf
```Then we will probably amend the file by hand rather than by sed. Also, let's see if there is any clue here:```
dmesg | grep -i dmi
```
> Because there is a minor typo in the command. It is /etc/modprobe.d. Please correct to that and try again -Sorry about that.

---

### Post by dupont2 on 2013-09-11
Hi Chili,

reply below,

```
fred@fred-X201EP:~$ cat /etc/modprobe.d/asus.conf
options asus_nb_wmi wapf=4
fred@fred-X201EP:~$ dmesg | grep -i dmi
[    0.000000] DMI: ASUSTeK COMPUTER INC. X201EP/X201EP, BIOS X201EP.209 02/04/2013
[   13.893884] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
fred@fred-X201EP:~$ 
```

---

### Post by chili555 on 2013-09-11
I suggest you do:```
gksudo gedit /etc/modprobe.d/asus.conf
```Change the 4 to a 1. Proofread, save and close gedit. Reboot and let us have a report.> DMI: ASUSTeK COMPUTER INC. X201EP/X201EP, BIOS X201EP.209 02/04/2013No help, really.

---

### Post by dupont2 on 2013-09-11
OK,

```
gksudo gedit /etc/modprobe.d/asus.conf

```
Edit value to 1 within gedit
```

options asus_nb_wmi wapf=1
```

Save, reboot, still no wifi Fn+F2 on/off.

---

### Post by chili555 on 2013-09-11
We are running low on ideas. Please try:```
sudo modprobe -r asus-wmi
```Any improvement? If so, we'll need to write one file to make it persistent.

---

### Post by varunendra on 2013-09-11
dupont2,

Do other Fn+ key combos work in Ubuntu? Does F2 work? F2 is shortcut for 'Rename', so just select a file in your home, desktop etc. and hit F2. Does it go to 'Rename' mode? Sounds a stupid question to myself, since you clearly said it works in Win8, but.... just curious.

---

### Post by dupont2 on 2013-09-12
> **chili555 said:**
> We are running low on ideas. Please try:```
sudo modprobe -r asus-wmi
```Any improvement? If so, we'll need to write one file to make it persistent.

Result :

```
fred@fred-X201EP:~$ sudo modprobe -r asus-wmi
[sudo] password for fred: 
FATAL: Module asus_wmi is in use.
fred@fred-X201EP:~$ 
```

No improvement.

---

### Post by dupont2 on 2013-09-12
> **varunendra said:**
> dupont2,

Do other Fn+ key combos work in Ubuntu? Does F2 work? F2 is shortcut for 'Rename', so just select a file in your home, desktop etc. and hit F2. Does it go to 'Rename' mode? Sounds a stupid question to myself, since you clearly said it works in Win8, but.... just curious.

Other combos work
Fn+F1 => sleep mode
Fn+F3,F4 => not allocated
Fn+F5,F6 => luminosity
Fn+F7 => black screen
Fn+F8 => change screen
F9 => disable trackpad
Fn+F10,F11,F12 => sound volume and mute

F2 work => alt+F2 open Ubuntu dash, works also for rename file shortcut.

---

### Post by chili555 on 2013-09-12
I have only two suggestions left. The first is to try numbers other than 0, 1 and 4 in our conf file. You can try temporarily with:```
sudo modprobe -r asus-wmi
sudo modprobe -r asus-nb-wmi
sudo modprobe asus-nb-wmi wapf=2
```Check to see that both modules re-loaded:```
lsmod | grep asus
```If there is no error when you loaded 2, see if the Fn+F2 combination are now working. If not, repeat with 3, 5, 6, 7, 8 and 9.

If none of this works, run:```
rfkill list all
```Find out which entry is wireless. Here is a sample from my machine:```
[COLOR="#FF0000"]0[/COLOR]: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```Then see if you can turn off the wireless with:```
sudo rfkill block [COLOR="#FF0000"]0[/COLOR]
```Of course, substitute the index number, in this example 0, for the index number you found. If this works, Varun and I will try to work out how to map 'sudo rfkill block 0' to Fn+F2 and, since it is unallocated, 'sudo rfkill *un*block 0' to Fn+F3.

Sounds ambitious, doesn't it? Desperation is the mother of invention.

---

### Post by varunendra on 2013-09-12
My problem, due to which I blacklisted asus-nb-wmi, was that I couldn't turn bluetooth on. As soon as I blacklisted it, the BT started functioning as it should (but volume and touchpad controls have disabled, which is okay for me). The wifi combo Fn+F2 have to be pressed four times now to turn it off, else either the wifi, or its LED remains on.

All the Fn+ combinations are same as dupont2 mentioned in post #20.

If I now load the asus-nb-wmi module manually with modprobe, the system becomes confused and none of the key combos work as expected. However, if I unblacklist it, so that it loads at startup, everything works as it should (only bluetooth becomes non-functional again).

So what I'm trying to suggest is - why not try blacklisting asus-nb-wmi just for a test, and see what breaks what works. Also checking lsmod thereafter. But this AFTER trying what is already suggested above..

---

### Post by dupont2 on 2013-09-12
Hi,

```
fred@fred-X201EP:~$ sudo modprobe -r asus-wmi
[sudo] password for fred: 
FATAL: Module asus_wmi is in use.
fred@fred-X201EP:~$ sudo modprobe -r asus-nb-wmi
fred@fred-X201EP:~$ sudo modprobe asus-nb-wmi wapf=2
fred@fred-X201EP:~$ lsmod | grep asus
asus_nb_wmi            16990  0 
asus_wmi               24794  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
wmi                    19256  1 asus_wmi
video                  19574  2 i915,asus_wmi
```

I tried with other values where x is was 3, 5, 6, 7, 8 and 9 and tried to activate wifi with Fn+F2 but it didn't help

(only by entering this line)

```
 sudo modprobe asus-nb-wmi wapf=x
```

at last :

```
fred@fred-X201EP:~$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

So 
```

sudo rfkill block 1
```

Wifi disabled.
I had to activate wifi with the wifi menu but did not activate with F2+Fn.

---

### Post by chili555 on 2013-09-12
Very good! We are now making some progress. Temporarily, you can activate wireless with:```
sudo rfkill unblock 1
```...and disable with:```
sudo rfkill block 1
```Now Varun and I will put our heads together and see what we can do about translating those to key presses.

Calling Varun!!

---

### Post by varunendra on 2013-09-12
[COLOR="#FF0000"]**_EDIT_: Posted a slightly better and smarter way to do this [post=12819607][COLOR="#0000CD"]_Here_[/COLOR][/post]**[/COLOR]

Okay, just wording here what Dr. Chili suggested and I tested (partially, since I've disabled my Wifi in BIOS and haven't rebooted to re-enable it) -

dupont2,

Just as a temporary workaround, can you please try binding keys **F3** and **F2** to commands "**rfkill block**" and "**rfkill unblock**" respectively (or any other keys/key-combinations that are mostly unused)?

This is how I've done it here and it seems to work fine -

[INDENT]**1)** Install ***xbindkeys-config*** (a GUI frontend to xbindkeys - the program that captures and binds hotkeys with commands) -
```
sudo apt-get install xbindkeys-config
```

**2)** Create a default config file for it (else it would crash on key capture step) -
```
xbindkeys --defaults > ~/.xbindkeysrc
```

**3)** Run the program from terminal (because it does not create a launcher in Unity dash) -
```
xbindkeys-config
```
let the terminal running in the background..
In the GUI, 3 example shortcuts are already present. I didn't touch them.

**4)** Click on "[COLOR="#0000CD"]**New**[/COLOR]" button at the bottom of the GUI.

**5)** In the right hand pane of the GUI, fill in a suitable name in the "[COLOR="#0000CD"]**Name**[/COLOR]" field, e.g. "***Unblock Wifi***"

**6)** Click on "[COLOR="#0000CD"]**Get Key**[/COLOR]" button. This will open a tiny blank box doing nothing but waiting for your input.

**7)** Press the desired key (or key combination) to be recorded for unblocking Wifi. The tiny box will disappear and the key will be recorded.

**8)** In the "[COLOR="#0000CD"]**Action**[/COLOR]" field, type in the desired command, which is "***rfkill unblock [COLOR="#FF0000"]1[/COLOR]***" in your case. *[COLOR="#800000"](**NOTE:** Others following this method, change "**[COLOR="#FF0000"]1[/COLOR]**" with whatever is the index number for your "**[COLOR="#FF0000"]phy0[/COLOR]**" interface in the output of "**rfkill list**". See **posts #21 and #23** above)[/COLOR]*

**9)** Click on "[COLOR="#0000CD"]**New**[/COLOR]" again and **repeat steps 4-8** for "***Block Wifi***" this time, with a new key or key-combination. The "[COLOR="#0000CD"]**Action**[/COLOR]" for this one would be "***rfkill block [COLOR="#FF0000"]1[/COLOR]***". *[COLOR="#800000"](**NOTE:** Again, change "1" with your phy0 index)[/COLOR]*

**10)** Click on "[COLOR="#0000CD"]**Apply**[/COLOR]" button and test the hotkeys to see if they work as expected (they do here).

**11)** Click on "[COLOR="#0000CD"]**Save & Apply & Exit**[/COLOR]" to save the new hotkeys to the default file.[/INDENT]

I have tested above with F3 and F2 keys, and it works nicely here. The Alt+F2 combination is NOT affected by this setting.

Fn key doesn't seem to be noticed by any key capture program (probably that's why it is considered "Hardware Switch"), so not possible to use it yet.

[s]The xbindkeys program by default runs in daemon mode in the background. But since I haven't rebooted yet, I can't say if it will autorun at startup *[COLOR="#696969"](I do that only once or twice a month ;), but will be doing this shortly this time to do further testing)[/COLOR]*. If it doesn't autoload on next boot, you may have to run "xbindkeys" command manually.[/s] ***EDIT:** Not required, confirmed that it autostarts at each boot.*

I know it is crude and ugly, but I hope it will be just a temporary workaround and we'd be able to find a decent solution soon. Please test, and let us all know how it goes for you.

---

### Post by dupont2 on 2013-09-13
Hi,

I assigned F3 to enable and F4 to disable wifi and it works, the configuration even autoload at startup !!!
Wifi status light on the netbook still off even if wifi is on.
I couldn't assign Fn+F2 toogle 
xbindkeys does not allow.
Is a good workaround and hope this will be solved with the next Ubuntu release.

Thanks for your help chili555 and varunendra.

Do you mind if I put this Thread as temporary solved ?

---

### Post by varunendra on 2013-09-13
> **dupont2 said:**
> Do you mind if I put this Thread as temporary solved ?

Do we mind ??

There are no words to express how much we love that [Solved] prefix :).

...and the [Solved] status isn't going to keep us from posting further suggestions if we came across some. Please go ahead.

---

### Post by chili555 on 2013-09-13
Awesome! Glad it's working. I suspect a few other X201E owners will find and implement the same fix and be grateful that you were willing to experiment with us until a useful solution was found. Please mark Solved.

Great job, Varun!

---

### Post by MadEarThInk on 2013-12-04
I don't believe this is temporarily solved.  My experience after following this entire thread and finally getting to 'modprobe asus-nb-wmi wapf=x' was that I receive an error stating that wapf=x is an invalid option on reboot.  However, wapf=x was the only thing that removed the hard block on phy0

Wireless does start working and it removes the hard block; however, with this option added to /etc/modprobe.d/asus.conf after reboot my ethernet jack doesn't work.  So I can get wifi but not wired.  If I remove that option, I can get wired but not wifi.  I could not find a way to turn wireless on or off without a reboot if the "invalid" option was not set in /etc/modprobe.d/asus.conf.

To recap:
1. After doing
```

echo "options asus-nb-wmi wapf=x" > /etc/modeprobe.d/asus.conf

```
and rebooting.  A boot error occurred saying "wapf=x" is an invalid option and the hard block on wireless was gone.  Wired connection did not work.  It seemed as if the ethernet jack wasn't recognized.
2. After doing 
```

echo "" > /etc/modeprobe.d/asus.conf

```
and rebooting.  Wired connection again worked, but wireless was again hard blocked.

I'm sure there's some output that will help here, but I'm not sure what it is.  Any thoughts on further debugging?

---

### Post by varunendra on 2013-12-04
> **MadEarThInk said:**
> I receive an error stating that wapf=x is an invalid option on reboot.

"x" was just dupont2's way of representing 'Any' numeric value. Which means x has to be replaced by a number, any number between 0-9. 0 is default and other recommended values are 1 and 4, although you can experiment with other values.

Please see this bug report, and if it turns out that you are affected by the same bug too, I'd recommend to add yourself to the list of "Affected Users" so that it gets fixed sooner : [https://bugs.launchpad.net/bugs/1173681](https://bugs.launchpad.net/bugs/1173681)

For a more polished version of the solution, please follow the instructions in this thread : [http://ubuntuforums.org/showthread.php?t=2181558](http://ubuntuforums.org/showthread.php?t=2181558)

---

### Post by MadEarThInk on 2013-12-04
Ha Ha!!! Gotta love it when poor interpretation kinda fixes an issue.  Thanks for the clarification and the links!

---

### Post by chili555 on 2013-12-04
The .c file for the module says, in part:>  /*
 * WAPF defines the behavior of the Fn+Fx wlan key
 * The significance of values is yet to be found, but
 * most of the time:
 * Bit | Bluetooth | WLAN
 *  0  | Hardware  | Hardware
 *  1  | Hardware  | Software
 *  4  | Software  | Software
 */There may be undocumented values, as well, but I suggest you try with the values 0, 1 or 4 to start. Also, for reference, here is a report of a happy customer: [http://askubuntu.com/questions/351594/wireless-disabled-by-hardware-switch/351860#comment492251_351860](http://askubuntu.com/questions/351594/wireless-disabled-by-hardware-switch/351860#comment492251_351860)

I loved the comment:> THANKS THANKS THANKS for preventing us from killing ourselves!

---

### Post by MadEarThInk on 2013-12-04
Yeah, that is a pretty nice comment.  Unfortunately, I tried setting wapf=[0-9] and rebooting, prior to setting it to "x".  Only "x", the invalid option got wireless working.  I suspect because it kept the module from loading all together.

---

### Post by chili555 on 2013-12-04
So is the issue kinda fixed now or fixed? Do you need additional troubleshooting assistance?

---

