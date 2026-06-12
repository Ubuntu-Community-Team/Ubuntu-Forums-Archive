---
title: "SmartLink modem drives not working under Hoary"
date: 2005-04-12
forum: Networking &amp; Wireless
---

### Post by danj205 on 2005-04-12
Hi,
I have been trying to get the SmartLink modem drivers to work under Hoary. I have been using them for a while under Warty, and so I thought it would be a straight-forward process to get my modem to work. Alas, no.

Anyway, I downloaded the source, installed the kernel headers just like many times I've done for Warty. I make, OK, make install, fine.

Then I try "modprobe slamr":
FATAL: Error inserting slamr (/lib/modules/2.6.10-5-386/extra/slamr.ko): Unknown symbol in module, or unknown parameter (see dmesg)

So, I type "dmesg | grep slamr":
slamr: module license 'Smart Link Ltd.' taints kernel.
slamr: Unknown symbol get_device
slamr: Unknown symbol put_device
slamr: Unknown symbol device_release_driver
slamr: Unknown symbol get_device
slamr: Unknown symbol put_device
slamr: Unknown symbol device_release_driver

I have no idea what to do. I really want my internet + Hoary!

Any help is greatly appreciated.

Daniel

---

### Post by az on 2005-04-12
There is a prebuilt modules package here, let me know if it works:

[http://ubuntuforums.org/showpost.php?p=117356](http://ubuntuforums.org/showpost.php?p=117356)

---

### Post by burlap on 2005-04-12
Is this prebuilt package any different than custom package built with module-assistant? I have only 2.6.10-686 kernel so I can't test your package now. 

BTW - my package built with module assistant doesn't work either (same error).

And one more question: there is a new version of "sl-modem-daemon" in apt, but it requires "sl-modem-modules-new", which does not exist (at least in the repositories I have, i.e. main, restricted, universe, multiverse). What's that?

---

### Post by az on 2005-04-12
"Is this prebuilt package any different than custom package built with module-assistant? I have only 2.6.10-686 kernel so I can't test your package now. "

There is no prebuilt official package.  I built it for my own fun and make it available.  I only built the 386 so that people could use it with the out-of-the-box Hoary kernel.

"BTW - my package built with module assistant doesn't work either (same error)."

It would seem that the problem lies elsewhere.  What version of the linux-image 
and linux-headers do you have?  What about the module-assistant and sl-modem-source?  Are you using the hoary version?  

"And one more question: there is a new version of "sl-modem-daemon" in apt, but it requires "sl-modem-modules-new", which does not exist (at least in the repositories I have, i.e. main, restricted, universe, multiverse). What's that?"

The built sl-modem-modules provides sl-modem-modules-new.  No, they are not in the repositories.  I asked on ubuntu-MOTU irc.  Maybe for Breezy...

---

### Post by burlap on 2005-04-12
Thinking is bad for your health: this is the second time today I made critical stupid mistakes on Ubuntu. I had to "--rebuild tree" and do other awful things to my drives after careless experiments with hibernating and randomly adding "resume=*swap*" to my kernel options... Nevermind, back to the point. 

Actually the sentence "The built sl-modem-modules provides l-modem-modules-new" was enlightening. I could not upgrade the daemon even with my package installed, but you say it should work. Why? The package was not built right. There were things left after Warty so module-assistant must have packaged them instead of compiling (or something). I deleted all the instances of "sl-modem" (debs, directories and all) in /usr/src, reinstalled sl-modem-source and compiled it again: the module is ok!

I'll have to get slmodemd running (I don't need the modem now, but might in the future), but the problem of danj205 is solved... 

My solution again:
1. Delete all remains of sl-modem from Warty.
2. Reinstall source (for example from package) or install prebuilt package prepared by azz if you are on default kernel (and go to 4). 
3. Run module-assistant or compile by yourself (I would recommend package)
4. modprobe


Just for the record:
linux-image-2.6.10-5-686, version 2.6.10-34
linux-headers-2.6.10-5, version 2.6.10-34
linux-headers-2.6.10-5-686, version 2.6.10-34
module-assistant 0.6.8ubuntu1
sl-modem-source 2.9.9a-1ubuntu4
sl-modem-daemon 2.9.9a-1ubuntu4
Ubuntu: upgraded from Warty (ubuntu-base and ubuntu-desktop present)

---

### Post by az on 2005-04-12
The dependancies of the sl-modem packages built in Warty are screwey.

---

### Post by danj205 on 2005-04-12
Thanks, the modem drivers work - hoorah!

But, is the Gnome dial-up tool supposed to be flashing up the fact that it is connecting. It seems to be pretty dodgy how it connects.

---

### Post by N8MAN1068 on 2005-08-22
i wasn't able to get these to work, as i'm on a 686 kernel, and these packages are for the 386.

---

### Post by burlap on 2005-08-23
Read all posts. There are some hints in post no 5...

Basically you need linux headers and module assistant. Build package, install, run daemon, check if your device is working (maybe you need to change it from hw:0 into hw:1 in /etc/default/sl-modem-daemon).

---

### Post by N8MAN1068 on 2005-08-23
doh...i did read right over it! :-# 
brain wasn't functioning after spending the better half of the day reading Gentoo install docs...

I got module-assistant installed, but could you point me to the sources for the sl-modem files?
I checked in synaptic, and the only one I show is sl-modem-daemon. when i try to install it, it gives a 'has no available version, but exists in the database' error...sounds like what is also mentioned in i believe post 3

for the 'pci=routeirq' to be entered in grub, which file should that go in, or is that not needed with this?

---

### Post by az on 2005-08-23
sl-modem-source is in multiverse.  (If not, look in universe)

---

### Post by N8MAN1068 on 2005-08-23
ah.
excellent.

got them downloaded, used module assistant to build+install.

step 4: modprobe


lost on that one. i've tried $sudo modprobe sl-modem-source 2.9.9a-1ubuntu4

please tell me i'm doing something wrong and the right way to do it.
\ :-|

---

### Post by az on 2005-08-23
The module is called slamr, I think.  Anyway, sl-modem-daemon should load the module by itself.

sudo /etc/init.d/sl-modem-daemon restart

If it is lookig for the alsa module, make it switch by running
sudo dpkg-reconfigure sl-modem-deamon

That should toggle the daemon from trying to use the alsa module to the (binary-only) slamr module.

If the alsa module is already loaded and has initialised the device, you may need to reboot to get the slamr module to initialize the modem.

---

### Post by burlap on 2005-08-23
Well, I should have been more clear....

(I am surprised that module-assistant did not fetch sources itself, but maybe something got wrong. Unless you configured it off-line...)

Some more hints:

1. I have used System -> Administration -> Network Settings to configure my modem. The strange thing is that it did not remember my settings. But as I don't use modem every day, I didn't try to investigate... (I used the modem with manually edited wvdial config). 
2. My modem makes no sounds (alsa issue?), I think it used to under 2.4.x kernel. So if you don't hear any sounds, it doesn't mean anything. To see whether your modem works, open terminal and run```
tail -f /var/log/messages
``` while trying to connect. Modem lights applet used to be better also (until gnome 2.8? it used to blink while calling, now it's static).

---

### Post by N8MAN1068 on 2005-08-24
$ tail -f /var/log/messages
Aug 24 07:54:12 localhost kernel: CSLIP: code copyright 1989 Regents of the University of California
Aug 24 07:54:12 localhost kernel: PPP generic driver version 2.4.2
Aug 24 07:54:12 localhost pppd[8086]: pppd 2.4.2 started by root, uid 0
Aug 24 07:54:15 localhost pppd[8086]: Exit.
Aug 24 07:54:15 localhost pppd[8140]: pppd 2.4.2 started by root, uid 0
Aug 24 07:54:18 localhost pppd[8140]: Exit.
Aug 24 07:54:18 localhost pppd[8143]: pppd 2.4.2 started by root, uid 0
Aug 24 07:54:20 localhost pppd[8143]: Exit.
Aug 24 07:54:20 localhost pppd[8148]: pppd 2.4.2 started by root, uid 0
Aug 24 07:54:22 localhost pppd[8148]: Exit.
---------------

so that would lead me to believe that my modem is working, correct?
however, when I go into system-administration-network and tell it that my modem is configured and then do autodetect, it doesn't find it, and neither does wvdialconf

---

### Post by burlap on 2005-08-25
> so that would lead me to believe that my modem is working, correct?
Well, exactly the opposite...
Your modem is working if you get this:
```
Aug  2 00:36:26 localhost pppd[27552]: pppd 2.4.2 started by root, uid 0
Aug  2 00:36:27 localhost chat[27553]: timeout set to 60 seconds
Aug  2 00:36:27 localhost chat[27553]: abort on (ERROR)
Aug  2 00:36:27 localhost chat[27553]: abort on (BUSY)
Aug  2 00:36:27 localhost chat[27553]: abort on (VOICE)
Aug  2 00:36:27 localhost chat[27553]: abort on (NO CARRIER)
Aug  2 00:36:27 localhost chat[27553]: abort on (NO DIALTONE)
Aug  2 00:36:27 localhost chat[27553]: abort on (NO DIAL TONE)
Aug  2 00:36:27 localhost chat[27553]: abort on (NO ANSWER)
Aug  2 00:36:27 localhost chat[27553]: send (ATZ^M)
Aug  2 00:36:27 localhost chat[27553]: send (AT&FH0L3^M)
Aug  2 00:36:27 localhost chat[27553]: expect (OK)
Aug  2 00:36:27 localhost chat[27553]: ATZ^M^M
Aug  2 00:36:27 localhost chat[27553]: OK
Aug  2 00:36:27 localhost chat[27553]:  -- got it
Aug  2 00:36:27 localhost chat[27553]: send (ATDT0202122^M)
Aug  2 00:36:27 localhost chat[27553]: timeout set to 75 seconds
Aug  2 00:36:27 localhost chat[27553]: expect (CONNECT)
Aug  2 00:36:27 localhost chat[27553]: ^M
Aug  2 00:36:27 localhost chat[27553]: AT&FH0L3^M^M
Aug  2 00:36:27 localhost chat[27553]: OK^M
Aug  2 00:36:27 localhost chat[27553]: ATDT0202122^M^M
Aug  2 00:36:58 localhost chat[27553]: CONNECT
Aug  2 00:36:58 localhost chat[27553]:  -- got it
Aug  2 00:36:58 localhost pppd[27552]: Serial connection established.
Aug  2 00:36:58 localhost pppd[27552]: Using interface ppp0
Aug  2 00:36:58 localhost pppd[27552]: Connect: ppp0 <--> /dev/modem
Aug  2 00:37:03 localhost pppd[27552]: CHAP authentication succeeded
Aug  2 00:37:03 localhost kernel: PPP BSD Compression module registered
Aug  2 00:37:03 localhost kernel: PPP Deflate Compression module registered
Aug  2 00:37:04 localhost pppd[27552]: local  IP address 213.76.88.235
Aug  2 00:37:04 localhost pppd[27552]: remote IP address 1.1.1.1
Aug  2 00:37:04 localhost pppd[27552]: primary   DNS address 194.204.159.1
Aug  2 00:37:04 localhost pppd[27552]: secondary DNS address 217.98.63.164
```
(The date is Aug 2, as I sent this lately to someone asking the same questions.)

Few things to check:
1. Does ```
dmesg | grep modem
``` show anything?

2. What happens when you try ```
sudo /etc/init.d/sl-modem-daemon restart
```

3. What does ```
cat /etc/default/sl-modem-daemon | grep SLMODEM
``` show?

If 1 shows nothing, probably 2 won't work anywany. You could try to change SLMODEM_DEVICE into hw:1 (or also hw:0 or slamr0, hw:1 works for me) and to set your country in SLMODEM_COUNTRY (if it is not there). After each change run 2.

---

### Post by mingus on 2005-08-25
If you use gnome-ppp, there is an activity log as above . . .

Are you sure slamr is loading?  Does it show with a lsmod?  Does modprobe slamr work?  I discovered my system needed the "ungrab" workaround; as I recall it's on the linmodem website where you get scanmodem.  It works with all the 2.9.9x versions, but not with 2.9.10 (the 2.9.9x actually has newer code).  You compile it and put it in front of slamr in /etc/modules.

---

### Post by N8MAN1068 on 2005-08-26
nathan@ewok1:~$ dmesg | grep modem
slamr: SmartLink AMRMO modem.
nathan@ewok1:~$ sudo /etc/init.d/sl-modem-daemon restart
Password:
sudo: /etc/init.d/sl-modem-daemon: command not found
nathan@ewok1:~$ cat /etc/default/sl-modem-daemon | grep  SLMODEM
cat: /etc/default/sl-modem-daemon: No such file or directory
nathan@ewok1:~$ modprobe slamr
nathan@ewok1:~$

i'm getting kind of stubborn now. i was all about putting Ubuntu on my desktop, but i couldn't get the modem to work, so i had to put XP back on cuz the wife was harpin' about it. But on this laptop, i can bork it all i want, as long as i get it running properly.

---

### Post by N8MAN1068 on 2005-08-26
ah...it'd help if the sl-modem-daemon was installed... :-# 
nathan@ewok1:~$ sudo /etc/init.d/sl-modem-daemon restart
Shutting down SmartLink Modem driver normally.
Starting SmartLink Modem driver for: slamr0.
Creating /dev/modem symlink, pointing to: /dev/ttySL0.
nathan@ewok1:~$ cat /etc/default/sl-modem-daemon | grep SLMODEM
#SLMODEMD_DEVICE=slamr0
#SLMODEMD_COUNTRY=GERMANY
SLMODEMD_DEVICE=auto
SLMODEMD_COUNTRY=USA


so it looks ok, gotta tell it i'm not in germany though....

---

### Post by burlap on 2005-08-26
Ok, we are getting closer. You don't have to change anything in lines beginning with "#" - these are comments (examples in this case). 

It seems that the modem was detected, now you have to run network settings (system -> administration -> network settings) and set a phone number, login and password (don't worry if "autodetection" does not give any results, just keep /dev/modem as your device). In the background keep a terminal window open with ```
tail -f /var/log/messages
``` running and activate your connection. 

Later try using modem-lights applet for the panel - I used to use it for modem connections. It's changed, however, so if you have any problems, search the forums, start new threads and so on...

If you want to use gnome-ppp or other apps, I can't really help you. But when the modem works, the rest should be easier.  :^o

---

### Post by N8MAN1068 on 2005-08-26
looks like it'll be working great, albeit no dialtone..heh

thanks to all!
wish i could find out how to give ya'll cups of ubuntu, i guess a clap will have to do.
 =D> 

PM me if you ever find yourselves in the Richmond, VA area. i'll buy you dinner.

---

### Post by burlap on 2005-08-26
If NO DIALTONE issue continues, remember to check if it works with SLMODEMD_DEVICE set to hw:1 or hw:0 (after these changes restart sl-modem daemon). I had some problems with default config, but with hw:1 it works ok.

---

### Post by N8MAN1068 on 2005-08-26
no dialtone would be because it's not plugged into a phone line...don't have an analog/pots line in my office.  ;-)

---

### Post by Arkanoid on 2005-08-27
[QUOTE=azz]There is a prebuilt modules package here, let me know if it works:

[http://ubuntuforums.org/showpost.php?p=117356](http://ubuntuforums.org/showpost.php?p=117356)[/QUOTE]

Hello,

I followed the instructions of this link but I still can't make my modem work (it's a Smart Link).

Below is the last lines in /var/log/messages... any ideas?

```
Aug 27 22:13:47 localhost kernel: CSLIP: code copyright 1989 Regents of the University of California
Aug 27 22:13:47 localhost kernel: PPP generic driver version 2.4.2
Aug 27 22:13:47 localhost pppd[8946]: pppd 2.4.2 started by root, uid 0
Aug 27 22:13:48 localhost chat[8958]: abort on (BUSY)
Aug 27 22:13:48 localhost chat[8958]: abort on (NO CARRIER)
Aug 27 22:13:48 localhost chat[8958]: abort on (VOICE)
Aug 27 22:13:48 localhost chat[8958]: abort on (NO DIALTONE)
Aug 27 22:13:48 localhost chat[8958]: abort on (NO DIAL TONE)
Aug 27 22:13:48 localhost chat[8958]: abort on (NO ANSWER)
Aug 27 22:13:48 localhost chat[8958]: abort on (DELAYED)
Aug 27 22:13:48 localhost chat[8958]: send (ATZ^M)
Aug 27 22:13:48 localhost chat[8958]: expect (OK)
Aug 27 22:13:48 localhost chat[8958]: ATZ^M^M
Aug 27 22:13:48 localhost chat[8958]: OK
Aug 27 22:13:48 localhost chat[8958]:  -- got it 
Aug 27 22:13:48 localhost chat[8958]: send (ATDT30318300^M)
Aug 27 22:13:48 localhost chat[8958]: expect (CONNECT)
Aug 27 22:13:48 localhost chat[8958]: warning: read() on stdin returned 0
Aug 27 22:13:48 localhost chat[8958]: Failed
Aug 27 22:13:48 localhost pppd[8946]: Hangup (SIGHUP)
Aug 27 22:13:48 localhost kernel: e0b58469
Aug 27 22:13:48 localhost kernel: PREEMPT 
Aug 27 22:13:48 localhost kernel: Modules linked in: ppp_generic slhc slamr nls_cp437 ntfs ipv6 powernow_k8 proc_intf freq_table cpufreq_userspace cpufreq_ondemand cpufreq_powersave video sony_acpi pcc_acpi button battery container ac shpchp pci_hotplug amd74xx snd_intel8x0 snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc forcedeth ehci_hcd ohci_hcd usbcore amd64_agp agpgart analog gameport floppy pcspkr rtc md evdev tsdev dm_mod capability commoncap psmouse mousedev parport_pc lp parport ide_generic ide_disk ide_cd ide_core cdrom sd_mod sata_nv libata scsi_mod unix thermal processor fan fbcon font bitblit vesafb cfbcopyarea cfbimgblt cfbfillrect
Aug 27 22:13:48 localhost kernel: CPU:    0
Aug 27 22:13:48 localhost kernel: EIP:    0060:[pg0+545047657/1070015488]    Tainted: P      VLI
Aug 27 22:13:48 localhost kernel: EFLAGS: 00210296   (2.6.10-5-386) 
Aug 27 22:13:48 localhost kernel: EIP is at sysdep_memset+0xd/0x15 [slamr]
Aug 27 22:13:48 localhost kernel: eax: 00000000   ebx: d37f8e00   ecx: 00003000   edx: 00000000
Aug 27 22:13:48 localhost kernel: esi: d11dfe1c   edi: 9dff1ce0   ebp: dac78c00   esp: d11dfdc4
Aug 27 22:13:48 localhost kernel: ds: 007b   es: 007b   ss: 0068
Aug 27 22:13:48 localhost kernel: Process slmodemd (pid: 8813, threadinfo=d11de000 task=d198f540)
Aug 27 22:13:48 localhost kernel: Stack: d11dfdec e0b873f8 9dff1ce0 00000000 00003000 00000000 d1cd8000 00000000 
Aug 27 22:13:48 localhost kernel:        00001000 00000001 00000000 00000001 00000001 00009600 00000010 00000000 
Aug 27 22:13:48 localhost kernel:        00000000 00000000 00000000 00000000 00000000 02600800 00000000 00000001 
Aug 27 22:13:48 localhost kernel: Call Trace:
Aug 27 22:13:48 localhost kernel:  [pg0+545240056/1070015488] FinishModioSetup__13ModemInstanceP18tagMODIOINFOSTRUCT+0x568/0x628 [slamr]
Aug 27 22:13:48 localhost kernel:  [pg0+545237550/1070015488] Enable__13ModemInstanceP18tagMODIOINFOSTRUCT+0x22/0x19c [slamr]
Aug 27 22:13:48 localhost kernel:  [pg0+545083766/1070015488] Start__10VModemLineP18tagMODIOINFOSTRUCT+0xf6/0x128 [slamr]
Aug 27 22:13:48 localhost kernel:  [pg0+545242407/1070015488] CalculateStartParameters__13ModemInstance+0x1f3/0x1fc [slamr]
Aug 27 22:13:48 localhost kernel:  [pg0+545237357/1070015488] ReallyOpenModio__13ModemInstance+0x141/0x1e0 [slamr]
Aug 27 22:13:48 localhost kernel:  [pg0+545242974/1070015488] SetProp__13ModemInstanceUlUl+0xce/0x17c [slamr]
Aug 27 22:13:48 localhost kernel:  [pg0+545244639/1070015488] Start__13ModemInstanceP10STARTPARAM+0x3b/0x54 [slamr]
Aug 27 22:13:48 localhost kernel:  [pg0+545048801/1070015488] amrmo_card_start+0x39/0x44 [slamr]
Aug 27 22:13:48 localhost kernel:  [pg0+545047319/1070015488] amrmo_ioctl+0xa8/0xe7 [slamr]
Aug 27 22:13:48 localhost kernel:  [sys_ioctl+443/472] sys_ioctl+0x1bb/0x1d8
Aug 27 22:13:48 localhost kernel:  [sysenter_past_esp+82/117] sysenter_past_esp+0x52/0x75
Aug 27 22:13:48 localhost kernel: Code: 85 c0 5b 89 c3 75 0d 56 68 60 1e b9 e0 e8 d9 dd 5b df 58 5a 89 d8 5b 5e c3 e9 73 e2 5d df 57 8b 4c 24 10 8a 44 24 0c 8b 7c 24 08 <f3> aa 8b 44 24 08 5f c3 57 56 8b 44 24 14 89 c1 8b 74 24 10 c1 
Aug 27 22:13:49 localhost pppd[8946]: Exit.
```

---

