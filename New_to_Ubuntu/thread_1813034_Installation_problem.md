---
title: "Installation problem"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by gxHL on 2011-07-27
Hello there I'm having trouble installing ubuntu. 

I installed ubuntu with wubi . The installation went fine but when i tried to boot Ubuntu i get a screen like this _[http://i.imgur.com/peuF2.jpg](http://i.imgur.com/peuF2.jpg)_[U] . 
[/U]So i tried pressing "ESC" key for more boot options and used the second time the second option (i don't remember it clearly) _fail safe graphic_ mode or something the same screen again.  
I rebooted and tried the 3rd option it was something like " Alternative ... " this time it booted up and started updating the system files and showing me some of the new stuff in Ubuntu. 

When it finished it rebooted and now i only get 3 options when i choose ubuntu, The 1st i assume boot up Ubuntu the 2nd is for recovery and the 3rd is to go back to the loader to boot up windows 7.
My spec is 
> MB M3N78-EM
Onboard Video Adapter NVIDIA GeForce 8300
CPU AMD Athlon 64 x2 3800+
Ram 2Gb
PCI Network Controller D-Link System Inc AirPlus G DWL-G510 Wireless Network Adapter (Rev.C)
PCI Audio Device    Creative Labs    Audigy LS Series    Creative Labs    SB0570 [SB Audigy SE]
2Hard Disks 500GB and 160GB WDAny help is appreciated...

---

### Post by westie457 on 2011-07-27
> **gxHL said:**
> Hello there I'm having trouble installing ubuntu. 

I installed ubuntu with wubi . The installation went fine but when i tried to boot ununtu i get a screen like this _[http://i.imgur.com/peuF2.jpg](http://i.imgur.com/peuF2.jpg)_[U] . 
[/U]So i tried pressing "ESC" key for more boot options and used the second time the second option (i dont remember it clearly) _failsafe graphic_ mode or something the same screen again.  
I rebooted and tried the 3rd option it was someting like " Alternative ... " this time it booted up and started updating the system files and showing me some of the new stuff in ubuntu. 

When it finished it rebooted and now i only get 3 options when i choose ubuntu, The 1st i assume boot up ubuntu the 2nd is for recovery and the 3rd is to go back to the loader to boot up windows 7.
My spec is 


Any help is appreciated...

Hello, welcome to the Forums.

Your problem looks like a graphics card driver issue.

Boot into recovery mode open a terminal and run ```
lspci
```.

Copy the output and then click on new reply. Then click on the # at the top of the message window and paste between the [code] brackets.

---

### Post by gxHL on 2011-07-27
Can not open recovery mode after showing me some commands being executed it shows me about 0.5 seconds the screen that i think its the recovery mode and then it throws me again this screen.
I've attached a video you can watch it for more detail...

---

### Post by amjjawad on 2011-07-27
I suggest NOT to waste your time with Wubi.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

I'd recommend to download Ubuntu, check [MD5SUM]("https://help.ubuntu.com/community/UbuntuHashes")  then burn it to a CD or Create Live USB.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
or you can check download page in [www.ubuntu.com](www.ubuntu.com) which has all the needed steps.

Now, insert your LiveCD or plug your LiveUSB and make sure your BIOS boot first from your CD/DVD Drive (or your USB in case of LiveUSB).

Login to the live session and TRY Ubuntu WITHOUT installation. Make sure Ubuntu works well with your Hardware.

If everything is okay, you can either install Ubuntu on your HDD

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
You also can check my guide - in my signature - or use google :)

or if you don't want to mess with your system, you can install Ubuntu on an External HDD OR USB Drive.

Check my signature: How to avoid Wubi.

---

### Post by gxHL on 2011-07-27
That isn't the case. I forgot to mention that Live cd or usb that i had tried didn't work out , with the same problem appearing. I even downloaded SUSE live cd... the same problem although in SUSE this screen was green... ^^

One more thing, when i boot up my Ubuntu installation it loads and i hear the intro sound of ubuntu but off course i can't see anything....

---

### Post by varunendra on 2011-07-27
> **gxHL said:**
> That isn't the case. I forgot to mention that Live cd or usb that i had tried didn't work out , with the same problem appearing. I even downloaded SUSE live cd... the same problem although in SUSE this screen was green... ^^

One more thing, when i boot up my Ubuntu installation it loads and i hear the intro sound of ubuntu but off course i can't see anything....
Which version of Ubuntu are you using? If it is 11.04, try 10.04. Also, while booting from live CD/USB, press and hold 'shift' key. This should bring up advance boot menu. If you can get to this screen, press F6 and in the popped up menu, check 'nomodeset' to see if it can let you boot normally.

---

### Post by amjjawad on 2011-07-27
> **varunendra said:**
> Which version of are you using? If it is 11.04, try 10.04. Also, while booting from live CD/USB, press and hold 'shift' key. This should bring up advance boot menu. If you can get to this screen, press F6 and in the popped up menu, check 'nomodeset' to see if it can let you boot normally.

+1

Please try that and report back.

Your Graphics Card is nVidia so I'm not surprised!

---

### Post by gxHL on 2011-07-28
yes 10.04 worked fine thank you.... although now i'm having another issue with my WLAN pci card ... can't get it working :P

---

### Post by amjjawad on 2011-07-28
> **gxHL said:**
> yes 10.04 worked fine thank you.... although now i'm having another issue with my WLAN pci card ... can't get it working :P


From Terminal (Applications > Accessories > Terminal )
Run this command please and post the result here but please make sure to wrap up the text with CODE Tags or highlight it and click "#".

```
sudo lshw -C network

```

---

### Post by varunendra on 2011-07-29
> **amjjawad said:**
> From Terminal (Applications > Accessories > Terminal )
Run this command please and post the result here but please make sure to wrap up the text with CODE Tags or highlight it and click "#".

```
sudo lshw -C network

```
I'd rather suggest to post it in a different thread and post a link to it here so that we could follow. The title of this thread doesn't correspond to wifi issue.

@gxHL,
Nice to see that you got it working, but at the same time it's unfortunate that you had to fall back to 10.04 (it's a good version though - my favourite so far). I had impression that Geforce 8300 should have been well supported in 11.04. But anyway, it's all good if you are satisfied.:) Can't say if you should mark it as [solved] or not, it's up to you.

---

### Post by gxHL on 2011-07-29
@[amjjawad]("http://ubuntuforums.org/member.php?u=941822") The info you asked is [here]("http://ubuntuforums.org/showthread.php?p=11097831#post11097831").
@[varunendra]("http://ubuntuforums.org/member.php?u=1043629") Yes you are right i opened a new topic asking for help there.
I'll put it solved cause i don't really care about the edition just wanna do my job.... I hope i don't have any trouble up grating them withing the OS....

Thank you again for your time and efforts.

---

