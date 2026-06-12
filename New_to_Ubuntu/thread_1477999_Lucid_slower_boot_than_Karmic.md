---
title: "Lucid slower boot than Karmic"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by vivek40 on 2010-05-09
Hii! I have a clean install of Lucid on my system ... but the boot time is in fact much higher than when I had Karmic on this.. i am sure there is something wrong and I would definitely want to resolve it, only if someone could tell me where to start.. lspci gives me this:-

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

---

### Post by SKhan on 2010-05-09
on my system sometimes it hangs during boot up. it also hanged during installation.

---

### Post by laidback on 2010-05-09
I got a copy last weekend and installed it on a separate HD (I use a caddy system) and was really looking forward to the fast boot times, but no it's much the same as my regular 9.04 installation.

It also failed to install my internet with DHCP which 9.04 and 9.10 have both done automatically, so I was back to using DNS. 

I intend to try again with another copy when things have settled down a bit as I like the idea of the LTS.

---

### Post by jrothwell97 on 2010-05-09
@the OP

Install Bootchart from the repositories (you can do this in the Synaptic Package Manager in the administration menu.) Reboot, and then use the file browser to go to /var/log/bootchart and find an image file. It *should* be called something along the lines of "*computer-name*-lucid-2010*mmdd-x*.png"

Copy that file to your home folder and attach it in a reply to this message: then we should have a better chance of working out what's taking so long.

---

### Post by laidback on 2010-05-09
Tried attaching the boot chart but it appears so small I'm not sure it's any help.

---

### Post by norm7446 on 2010-05-09
I guess we will just have to wait for SP1 to be released, to sort it. 

:P:)::P

---

### Post by sadaruwan12 on 2010-05-09
Yes, There are some hiccups along the way so it's better hold up till the SP1 of this LTS to be released.

I also have a big issue with my wireless that doesn't work in this release.

---

### Post by jrothwell97 on 2010-05-09
> **laidback said:**
> Tried attaching the boot chart but it appears so small I'm not sure it's any help.
Try it anyway, and attach the .tar.gz file of the same name. I'm sure we'll manage. :)

---

### Post by vivek40 on 2010-05-09
Hii Jrothwell! sorry for the late reply.. the file was a little huge to be attached here.. have attached it in a rapidshare link given below... did not know any other way.... would be great if some help arrives... if you would want me to attach it in some other manner.. I would be happy to do so..

[http://rapidshare.com/files/385371439/vivek-desktop-lucid-20100509-1.tgz.html]("http://rapidshare.com/files/385369715/vivek-desktop-lucid-20100509-1.tgz.html")

---

### Post by stevedes on 2010-05-09
Yes, Lucid Does seem noticeably slower than karmic (boot time especially is longer; so much for the 10 second boot-up!)

---

### Post by jrothwell97 on 2010-05-09
OK. Try uploading the image again, don't bother with the .tar.gz file. We should be able to read it.

---

### Post by philinux on 2010-05-09
Karmic boot was 1min 5 secs. Lucid is 18 seconds and that is to a usable desktop. Clean install. 
See the sticky in general help for boot issues.

---

### Post by laidback on 2010-05-09
jrothwell97,

.tgz and .png files attached

Sorry the .tgz upload says invalid file, tried the individual files but it's sooo slow as to be silly.

---

### Post by vivek40 on 2010-05-09
hii Jrothwell.. thanks for your support.. have uploaded the png file for your reference....hope this would work.. the image is also here on this link

[http://img188.imageshack.us/img188/2571/vivekdesktoplucid201005.png](http://img188.imageshack.us/img188/2571/vivekdesktoplucid201005.png)

---

### Post by vivek40 on 2010-05-10
bump!

---

### Post by vivek40 on 2010-05-12
Bump! someone please help with this.... I use the same CD of Lucid which everyone else has downloaded, why is my boot time higher than others...I agree that hardware plays a major role but then my system does not use much outdated hardware either!

---

### Post by norm7446 on 2010-05-12
He is my boot-chart .png. Now if you look at my time you will notice that I am only getting 25 Seconds, which is slower than yours. I am quite happy with this as when I had was using Vista & Windows7 they both took about between 1.30 to 2 min's to boot to desktop, then maybe another min to settle down with all the Anit-Virus and Windows network manager and all the other paraphernalia that must start up on boot. So my question would be. 

How have you got 24 seconds and I can only get 25 and that is with a Western Digital Raptor as my main H/Drive..  

No seriously, every computer is in essence different so everyone's times will be different. Lucid has now another couple of years to mature, it's only been out for 13 Days give it some chance to settle and the last few bug's to get ironed out. 

PS: Do what I do bug everyone I know that still runs Windows by asking them how long does it takes to boot Windows. Then Laugh at them and say " try 24 Seconds.. :twisted: "

---

### Post by jrothwell97 on 2010-05-13
> **vivek40 said:**
> hii Jrothwell.. thanks for your support.. have uploaded the png file for your reference....hope this would work.. the image is also here on this link

[http://img188.imageshack.us/img188/2571/vivekdesktoplucid201005.png](http://img188.imageshack.us/img188/2571/vivekdesktoplucid201005.png)

Yikes, sorry for not getting back to you sooner...

This is damned peculiar. I can't see any particular bottleneck in that bootchart (although I'm no expert: perhaps someone else will succeed in spotting something there that is blindingly obvious but I'm missing.) Do you have a concrete figure for your boot time in Karmic? There is a chance (a small chance, I stress) that difference may, in fact, be perceptive rather than real.

---

### Post by laidback on 2010-05-13
The figure at the top of my chart says 59:38s

---

### Post by vivek40 on 2010-05-14
Thanks Jrothwell for looking into this..After I had installed Karmic I used a stop watch to check the boot time , from the system being set on to the login screen(20 seconds) and from login to a functional desktop(4-5 seconds)....

In lucid my problem here is from start on to the login screen it takes close to 45 seconds(that is a little too much), from the login screen to the desktop it takes very less time(2-3 seconds now.. this is after I uninstalled Gwibber, pulseaudio and the indicator applet)

---

### Post by dagrat on 2010-05-14
I think that I'm having the same issue as you. From the login screen to the desktop seems rather long.  I haven't timed it 10-15 seconds maybe but longer than it was with 9.10.

---

### Post by vivek40 on 2010-05-14
No dagrat.. I guess there is some misunderstanding here.. In my case the time taken to reach the login screen is more. I am perfectly fine with the time from login screen to the desktop

---

