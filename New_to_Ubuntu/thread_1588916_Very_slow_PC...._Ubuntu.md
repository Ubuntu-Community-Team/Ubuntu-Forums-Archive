---
title: "Very slow PC.... Ubuntu?"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by ghostly606 on 2010-10-05
Hello,

I have an old Windows Vista laptop that is in a sorry state. The CD/DVD drive has fallen out and various things have been installed on it and uninstalled, and installed again and now everything is running very slowly.

I want to delete everything and start afresh, only problem is I don't have a Windows install DVD anymore and besides the DVD drive doesn't work anyway. I was thinking of installing Ubuntu on it and I have done a fair bit of research and one thing is not clear to me, can I completely replace windows with Ubuntu? If not, am I going to notice any noticeable improvement in performance by installing Ubuntu on a partition?

As you may be able to tell, I am a bit clueless when it comes to computers on this level so please help!

Thanks,
G

---

### Post by davidmohammed on 2010-10-05
Hi there and welcome to ubuntu and the forums.

You can certainly install ubuntu from a usb stick - [see here]("https://help.ubuntu.com/community/Installation/FromUSBStick") for more information.  If you dont want to wipe your vista install then, when installing, just choose the install side-by-side option rather than to erase the entire disk.

... and you will immediately notice the speed differences over vista.  Good luck - post back here if you have any issues.

---

### Post by snowpine on 2010-10-05
Welcome to the forums! Ubuntu is a wonderful operating system. :) It is also very different from Windows--at least as different as PC vs. Mac. So the question you need to ask yourself is, which software applications do you need for work/school/play, and are these applications available for Ubuntu? 

The best advice I can give you is to [download Ubuntu]("http://www.ubuntu.com/desktop/get-ubuntu/download") and burn it to a [Live CD]("https://help.ubuntu.com/community/LiveCD") or [USB thumb drive]("https://help.ubuntu.com/community/Installation/FromUSBStick"). Then, you can reboot and try it "with no change to your computer." This will allow you to evaluate it and see if it will work for your needs.

Personally, I have not completely replaced Windows in my life. There are certain Windows applications I need for work (Adobe Creative Suite) or enjoy as entertainment (Netflix Instant Viewing, games). Therefore I use a "dual boot" setup that allows me to choose between Linux or Windows each time I boot.

A final thought, you mention your computer is "very slow." If it is slow due to hardware problems (bad ram, failing hard drive, outdated processor, etc.) installing Ubuntu will not solve the hardwdare problems. You should take a look at the [Ubuntu System Requirements ]("https://help.ubuntu.com/community/Installation/SystemRequirements")to see if your computer is up to the task, and replace/upgrade any failing hardware. 

Welcome and good luck!

---

### Post by ghostly606 on 2010-10-05
Hey guys, thanks for the warm welcome and great advice! I am not sure why the computer is running so slowly, I think it might be just overloaded with stuff, various vintages of virus checking software that slow things up, etc which is why I am looking to wipe the drive completely if I can. It is a couple of years old, single core, 2GB RAM, 80GB HD, 2MHz processor, certainly should be up to the task. It is used as strictly a web browsing computer with the odd requirement to view PDFs and create basic  docs and spreadsheets as I also have a mac that I used for other more complex tasks (music sequencing and 3D modelling). If it ran a bit better I might consider using it for other things too!

Great idea to try it out first though! :)

---

### Post by new__buntu on 2010-10-05
Also, you should be aware that if Ubuntu isn't lightweight enough of an operating system for your hardware there are lighter version - namely Xubuntu and Lubuntu.

Edit: and on the other end, if you're looking for something a little more featured I'm told Kubuntu is quite nice.

---

### Post by TCHebb on 2010-10-05
> **ghostly606 said:**
> Hey guys, thanks for the warm welcome and great advice! I am not sure why the computer is running so slowly, I think it might be just overloaded with stuff, various vintages of virus checking software that slow things up, etc which is why I am looking to wipe the drive completely if I can. It is a couple of years old, single core, 2GB RAM, 80GB HD, 2MHz processor, certainly should be up to the task. It is used as strictly a web browsing computer with the odd requirement to view PDFs and create basic  docs and spreadsheets as I also have a mac that I used for other more complex tasks (music sequencing and 3D modelling). If it ran a bit better I might consider using it for other things too!

Great idea to try it out first though! :)
Ubuntu is quite capable of browsing the web and editing documents, and comes with programs pre-installed for both. If your computer came pre-installed with Vista, Ubuntu should run quite fast as long as it isn't a hardware failure that's slowing Vista down.

---

### Post by cgroza on 2010-10-05
> **new__buntu said:**
> Also, you should be aware that if Ubuntu isn't lightweight enough of an operating system for your hardware there are lighter version - namely Xubuntu and Lubuntu.

Ubuntu should be a race car on that system. :D

---

### Post by snowpine on 2010-10-05
I think Ubuntu sounds perfect for your needs, and should be faster than Vista on your hardware specs. :)

Since you are already a Mac user I assume you are comfortable switching between operating systems.

---

### Post by ghostly606 on 2010-10-06
Wow, installed on USB stick and it is really snappy! Only one small glitch, can't get ubuntu to recognise my USB wifi adaptor (screen broke a while back and took the internal wifi aerial with it).

Can any of you clever peeps offer any advice?

---

### Post by davidmohammed on 2010-10-06
excellent.

See if there is a wireless driver offered in System --> Administration --> Hardware Drivers.  If there is, activate it.

If there isn't, open a terminal session and type

lsusb

copy and paste the output here using "CODE TAGS" in your reply.

Also, what would be useful is to plugin your usb wireless.  Immediately, type in

dmesg

copy and paste the last dozen or so lines - hopefully the last few lines will indicate how the linux kernel is recognising your device, and if there is any errors during the recognition.

---

### Post by halitech on 2010-10-06
open a terminal and with the adapter plugged in, run
```
lsusb
```
and post the results here

---

### Post by ghostly606 on 2010-10-06
> **davidmohammed said:**
> excellent.

See if there is a wireless driver offered in System --> Administration --> Hardware Drivers.  If there is, activate it.

If there isn't, open a terminal session and type

lsusb

copy and paste the output here using "CODE TAGS" in your reply.

Also, what would be useful is to plugin your usb wireless.  Immediately, type in

dmesg

copy and paste the last dozen or so lines - hopefully the last few lines will indicate how the linux kernel is recognising your device, and if there is any errors during the recognition.

output to lsusb:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 18e8:6229 Qcom RT2573
Bus 001 Device 003: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 002: ID 058f:6364 Alcor Micro Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I forgot the last bit of your reply (dmesg), will do that now! (having to restart computer each time to switch from windows (internet access) to ubuntu!).

Thanks again for all the responses guys, I am almost overwhelmed with how helpful you are!

g

---

### Post by ghostly606 on 2010-10-06
As promised, here are the last few lines after typing dmesg:

[   95.364094] usb 1-5: new high speed USB device using ehci_hcd and address 5
[   95.513558] usb 1-5: configuration #1 chosen from 1 choice
[   95.550728] phy2: Selected rate control algorithm 'minstrel'
[   95.551569] Registered led device: rt2800usb-phy2::radio
[   95.551589] Registered led device: rt2800usb-phy2::assoc
[   95.551610] Registered led device: rt2800usb-phy2::quality


Thanks,
g

---

### Post by davidmohammed on 2010-10-06
Your issue is mentioned  in this [thread]("http://ubuntuforums.org/showthread.php?t=1378782&highlight=148f:3070&page=2") - at the start of the thread it mentions your ralink adapter.  Towards the end of the thread it mentions the results in Lucid.

What encryption are you connecting to?  Can you try first setting your router with no encryption.  If you can connect wirelessly, then your adapter is working, but maybe it doesnt like the encryption you are using.  Try WPA2 as mentioned in the thread.

---

### Post by davidmohammed on 2010-10-06
... just read your comment about switching....


you should be able to connect using a wired link (direct ethernet into your router) - that should help you from having to switch operating systems.

---

### Post by ghostly606 on 2010-10-06
> **davidmohammed said:**
> Your issue is mentioned  in this [thread]("http://ubuntuforums.org/showthread.php?t=1378782&highlight=148f:3070&page=2") - at the start of the thread it mentions your ralink adapter.  Towards the end of the thread it mentions the results in Lucid.

What encryption are you connecting to?  Can you try first setting your router with no encryption.  If you can connect wirelessly, then your adapter is working, but maybe it doesnt like the encryption you are using.  Try WPA2 as mentioned in the thread.

I tried blacklisting rt2800usb as suggested but I was not allowed to save the file 
etc/modprobe.d/blacklist.conf
Permission denied. Could this be because I am running on USB or because I have insufficient privileges?

I am now running up and down between my laptop upstairs and my mac downstairs (long story, laptop has no screen, hooked up to screen so more like a desktop, ie not portable; mac has rubbish battery retention so needs to stay near power outlet, none spare near laptop upstairs!). Much quicker than trying to boot windows!

My router has no encryption.

---

### Post by davidmohammed on 2010-10-06
try editing files using "sudo" e.g.

sudo nano /etc/modprobe.d/blacklist.conf

alternatively - if you like GUI type editors try

gksudo gedit /etc/modprobe.d/blacklist.conf

---

### Post by ghostly606 on 2010-10-06
I typed sudo nano /etc/modprobe.d/blacklist.conf and added the new blacklist. However I was not allowed to save over the original blacklist.conf file. Am I doing something wrong?

---

### Post by davidmohammed on 2010-10-06
hmmm, not sure.  Those commands should work.

When you say you are running from USB - are you using the boot option "try without installing"?  That could explain your issue.  You might have to actually install it onto the hard-disc, either as a dual boot - or install it as a wubi installation into your vista ([http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer) and click option 3 Show me how)

I've personally no experience of wubi - all my ubuntu installations are clean wipes of the HDD or as a dual boot.

---

### Post by ghostly606 on 2010-10-06
Ok, I think that is it, can't change the blacklist.conf file as a try without installing USB boot. I am loathe to do a clean wipe unless I know it will work so will try a dual boot. Have to look into how to do that now!

Thanks for all your help!

---

### Post by Kixtosh on 2010-10-06
> **ghostly606 said:**
> Ok, I think that is it, can't change the blacklist.conf file as a try without installing USB boot. I am loathe to do a clean wipe unless I know it will work so will try a dual boot. Have to look into how to do that now! ...That is very simple:

- First and foremost, back up everything you cannot afford to loose from your Vista system.
- Then defrag Vista, about three times consecutively (the first time will take the longest, hopefully the third time will be quite fast).
- Boot back into Ubuntu with the USB drive, and choose "install" instead of "try".
- After choosing time zone and keyboard options, you will come to "Step 4 of 7" that will ask you if you want to "Install them side by side", or "Erase and use the entire disk". 
- Choose the "side by side" option to keep Vista for now. The top bar graphic shows all your Vista stuff, as currently installed, including any recovery partitions and a small "loader" partition.
- If you want to allocate more space to Ubuntu (probably not necessary at this point), you can still slide the slider on the bottom bar graphic, to change that, but do not click the "Specify partitions manually" button.
- Continue installation.
- Run update manager immediately, from the System --> Administration menu (left side of the top panel by default). This may help with any issues.
- To start wireless, if it's working, simply click on the wireless icon (right side of the top panel by default) if it's visible to view available wireless networks.

If everything works the way you want it to (and you get your wireless working) you can even retrieve files from your Vista partition from inside Ubuntu, and copy them into your Ubuntu files.

After that, if you just want to wipe everything clean, you can go back and install Ubuntu again, but this time use the "use entire disk" option to obliterate your Windows partition entirely. It doesn't take that long to install, and it saves you the trouble of figuring out how to delete and add your Windows partition to an existing Ubuntu install (it's a bit daunting at times, as a new user, at least to me it is).

**Regarding performance versus Vista:** I can only offer my example and am currently running Ubuntu on a Toshiba Portégé ultra-portable with:

- A slow, 1.2GHz Pentium M ULV CPU.
- Limited Mobile Intel 915 integrated graphics.
- A maximum allowed 1.280GB of RAM.
- A slow 4,200 RPM hard drive.

At 2.7lbs, it's a great mobile laptop for web browsing, e-mail and office applications. Start up times on Windows XP Pro had gradually slowed to about five minutes (yes, that' five whole minutes, and I'm not rounding up either), but now that's down to under one minute with Ubuntu. To be fair though, I still dual boot with Windows XP (about once a week), and the clean installation of XP I did from scratch does now start in just under two minutes. I never add anything to XP though, no new applications nor changing virus software provider (I'm using Microsoft Security Essentials, which is free), so that I don't do anything to slow down starting up to five minutes all over again (ugh!).

Compared to mine, you should be doing much better with a faster processor, faster HDD, and more RAM. The only thing that's faster in XP in my case is Office 2003, which does start up much more quickly than the OpenOffice suite on this laptop.

Best of luck!

---

### Post by ghostly606 on 2010-10-06
Ok, like the idiot I am I did a fresh install and my wifi still doesn't work! Can anyone run me through exactly what I should do re blacklist.conf in case I have not done it right... :confused:

Everything else great though! :P

---

### Post by cgroza on 2010-10-06
If that thread indicates a solution with exact same model then it should work. Maybe you missed something. Try looking more careful.

---

### Post by pizza-is-good on 2010-10-06
> **ghostly606 said:**
> Ok, like the idiot I am I did a fresh install and my wifi still doesn't work! Can anyone run me through exactly what I should do re blacklist.conf in case I have not done it right... :confused:

Everything else great though! :P

Well first of all, welcome to Ubuntu! It was a short year and a half ago when I decided to go for it.

I read through the thread, but just in case you forgot. Have you done the System >> Administration >> Hardware Drivers to check to see if there is a driver for your wifi card _after_ you did the full installation?

---

### Post by ghostly606 on 2010-10-06
> **cgroza said:**
> If that thread indicates a solution with exact same model then it should work. Maybe you missed something. Try looking more careful.
When I click my network connection symbol at the top my adaptor is listed by it say that the "wireless disabled"

I have tried every combination in the blacklist.conf file (it is not very clear anywhere what I do after I type gksudo gedit /etc/modprobe.d/blacklist.conf so I tried everything and rebooted):

"blacklist rt2870sta"
"rt2870sta"
"# wifi fix
blacklist rt2870sta"
"# wifi fix
rt2870sta"
"blacklist rt2800usb"
"rt2800usb"
"# wifi fix
blacklist rt2800usb"
"# wifi fix
rt2800usb"

I have even tried adding WPA2 encryption, no luck.

Anyone?

---

### Post by ghostly606 on 2010-10-06
> **pizza-is-good said:**
> Well first of all, welcome to Ubuntu! It was a short year and a half ago when I decided to go for it.

I read through the thread, but just in case you forgot. Have you done the System >> Administration >> Hardware Drivers to check to see if there is a driver for your wifi card _after_ you did the full installation?
Ahhh ok. Not tried this, but then again I have never had an internet connection. I take it I have to hard wire up and do that? Sounds like a job for the morning, it is 2:30am!

Thanks for all the help tonight, much appreciated.

---

### Post by pizza-is-good on 2010-10-06
> **ghostly606 said:**
> Ahhh ok. Not tried this, but then again I have never had an internet connection. I take it I have to hard wire up and do that? Sounds like a job for the morning, it is 2:30am!

Thanks for all the help tonight, much appreciated.

Yes, it would probably be a good idea to be hooked up to Ethernet, so that if there is a driver it can be found. Can you do that?

Wow! I was never enthusiastic enough about an OS as to stay up till 2:30 am working on it!:guitar:

---

### Post by ghostly606 on 2010-10-07
You would if you had the prospect in the morning of an angry wife demanding to know why her silly husband has "broken the internet"!

---

### Post by beew on 2010-10-07
> **ghostly606 said:**
> When I click my network connection symbol at the top my adaptor is listed by it say that the "wireless disabled"

I have tried every combination in the blacklist.conf file (it is not very clear anywhere what I do after I type gksudo gedit /etc/modprobe.d/blacklist.conf so I tried everything and rebooted):

"blacklist rt2870sta"
"rt2870sta"
"# wifi fix
blacklist rt2870sta"
"# wifi fix
rt2870sta"
"blacklist rt2800usb"
"rt2800usb"
"# wifi fix
blacklist rt2800usb"
"# wifi fix
rt2800usb"

I have even tried adding WPA2 encryption, no luck.

Anyone?

I think you need to reboot after you blacklist the driver.

Also, if you are trying with a live usb you should have made it to be persistent or the changes you made will be lost on reboot.

---

### Post by ghostly606 on 2010-10-07
> **beew said:**
> I think you need to reboot after you blacklist the driver.
 
Also, if you are trying with a live usb you should have made it to be persistent or the changes you made will be lost on reboot.
 
Yes, I rebooted after I blacklisted the driver. Do I need to type "blacklist <name of driver here>" or just "<name of driver here>" in the blacklist.conf file? Does it matter if I include statement after the #?
 
Sorry I am a total noob when it comes to ubuntu (if haven't guessed already!), can you clarify what you mean in your second sentence? [EDIT - sorry, understand it now!]
 
Thanks!

---

### Post by ghostly606 on 2010-10-07
> **pizza-is-good said:**
> Yes, it would probably be a good idea to be hooked up to Ethernet, so that if there is a driver it can be found. Can you do that?

The saga continues! Hooked up to ethernet and internet working a treat. Checked for hardware drivers and no propriety drivers on my computer apparently. Wireless still disabled (see picture). I have hit a dead end. :confused:

Can anyone else offer a suggestion?

---

### Post by ghostly606 on 2010-10-07
FOllowing a number of other threads I did the following in the terminal:

lindsay@laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
snd_hda_codec_conexant    22641  1 
snd_hda_intel          22037  2 
snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
rt2870sta             461811  0 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ppdev                   5259  0 
arc4                    1153  4 
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
snd_seq_midi            4557  0 
softcursor              1189  1 bitblit
snd_rawmidi            19056  1 snd_seq_midi
vga16fb                11385  0 
rt73usb                22434  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
vgastate                8961  1 vga16fb
crc_itu_t               1371  1 rt73usb
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rt2800usb              31531  0 
rt2x00usb               9703  2 rt73usb,rt2800usb
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rt2x00lib              27509  3 rt73usb,rt2800usb,rt2x00usb
snd                    54148  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              205402  2 rt2x00usb,rt2x00lib
pcmcia                 30784  0 
joydev                  8708  0 
i915                  286079  3 
drm_kms_helper         29297  1 i915
drm                   162409  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
crc_ccitt               1339  1 rt2800usb
intel_agp              24119  2 i915
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
sdhci_pci               5470  0 
tifm_7xx1               3690  0 
video                  17375  1 i915
soundcore               6620  1 snd
cfg80211              126496  2 rt2x00lib,mac80211
sdhci                  15462  1 sdhci_pci
led_class               2864  2 rt2x00lib,sdhci
agpgart                31724  2 drm,intel_agp
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
tifm_core               6045  1 tifm_7xx1
lp                      7060  0 
output                  1871  1 video
psmouse                63245  0 
parport                32635  2 ppdev,lp
serio_raw               3978  0 
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
sky2                   40807  0 

There seems to be lots of references to rt drivers so I think they are in my OS, I can't get everything to configure properly.

---

### Post by ghostly606 on 2010-10-07
No matter where I look, blacklisting this driver seems to work for this problem (i.e. [https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/114598](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/114598)), so why not mine? Very strange. Think I will have to get some other wireless product to sort this out. Hmmmm

---

### Post by ghostly606 on 2010-10-08
Sorted! I had to blacklist more than one of my RT2** drivers, a case of trial and error got me there in the end. Thanks again to everyone who offered assistance.

---

### Post by Kixtosh on 2010-10-08
> **ghostly606 said:**
> Sorted! I had to blacklist more than one of my RT2** drivers, a case of trial and error got me there in the end. ...Now, doesn't that make you feel so much better? But you'll loose all the benefit of the exercise involved with running up and down the stairs constantly!

Congratulations anyway, and you pretty much worked it all out for yourself in the end, so that's even better!

---

