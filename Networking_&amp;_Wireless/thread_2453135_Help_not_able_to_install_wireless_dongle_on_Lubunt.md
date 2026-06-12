---
title: "Help not able to install wireless dongle on Lubuntu fresh install please?"
date: 2020-11-03
forum: Networking &amp; Wireless
---

### Post by cliff-bjazz on 2020-11-03
Hi,
I am totally new to Linux, and I have just installed the 'Lubuntu distro' along side my WindowsXP installation. The installation/dual boot was a success and I am able to get into both systems.
But in Lubuntu, I am not able to connect using my USB wireless dongle because it is not being picked up by the operating system. 
I have a mini drivers CD which contains specific drivers for Linux, the drivers come in two flavours (it appears),and are in seperate folders they are:


1/ RTL8811CU_8821CU_WiFi_linux_v5.2.5.3
2/ RTL88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044


I thought I could pick a set of drivers, then find the .exe file and install, but that was not the case. I searched online and found the method to install the (install.sh) script file in the Linux Terminal using the commands: (chmod +X install.sh), and then (sudo ./install.sh).

In the end, I did this with both drivers and both failed with different errors, the first one being err 127. The most successful attempt came when I tried to install driver number two, except that this too failed with an err 2 message. So I then plugged in an Ethernet cable (which I can only use temporarily), this was recognised and connected.  I was able to download a massive update file.
 After the installation I thought that my wireless dongle would be picked up after restarting, But the operating system still couldn't even see it, and the driver still fails to install from the script showing err 2.
can anyone help with this please.
My motherboard is a 32bit version Foxconn, and there does not appear to be any conflicts with any of the few peripherals that are plugged into the tower.


Thank you for reading,


cliff.

---

### Post by morrownr on 2020-11-03
General rule of thumb: If a wifi adapter comes with a cd that has Linux drivers, do not use them. The Linux kernel is under constant development and requires that drivers be constantly updated to keep pace with changes in the kernel. Certain Linux kernels are designation as Long Term Support kernels so we can enjoy stability for periods of time. Ubuntu 20.04 LTS and its children use LTS kernel 5.4. Ubuntu 20.10 uses kernel 5.8. I recommend that new users stick with the LTS versions of Ubuntu until such time as they are more experienced.

To help with your problem:

We need to know what version of Lubuntu you are using?

We need to know what version of the kernel you are using. From a terminal (Ctrl+Alt+T) type:

```
uname -a
```

We also need to know which wifi adapter chipset you have. Type:

```
lsusb
```

Please post the results.

FYI: here is a site with current drivers, one of which will probably work for you:

[https://github.com/morrownr](https://github.com/morrownr)

---

### Post by cliff-bjazz on 2020-11-03
Hello Morrownr,

Thank you so much for your feedback and timely help, I really appreciate it. I have to tell you that my understanding of Ubuntu is zero right now, but I did do as you instructed.
I booted up Linux and went into the Terminal. With the first code you gave me ([COLOR=#000000][FONT=&amp]uname -a),[/FONT][/COLOR] I got a string result, I hope that the operating system version is contained in the part which I copied down here:

OEM 4.15.0-122generic #124-Ubuntu SMP.  

I did try the next command regarding the chipset of the adaptor, and I don't think it is being recognised at all by the system. I got this string back in response:

command 'lsusb' not found, did you mean:command 'lsusb' from deb usbtils
try: sudo apt install <deb name>

The adapter is called, Wi-Fi Nano 11ac adapter, Dual Band, AC600 Dual Band,  2.4GHz+5.8GHz

That is all I have right now and I really hope you know what it means. I have not checked the url for the driver site which you have kindly provided yet. I will wait for any advice you might have first.

thanks again,
cliff.

---

### Post by praseodym on 2020-11-03
Please check the product and vendor IDs from that device
```

lsusb
```
This is how it looks like

```
Bus 001 Device 001: ID [COLOR="#FF0000"]1d6b:0002[/COLOR] Linux Foundation 2.0 root hub
```
Can you temporarily hook up via cable?

---

### Post by morrownr on 2020-11-03
> **cliff-bjazz said:**
> 

I booted up Linux and went into the Terminal. With the first code you gave me ([COLOR=#000000][FONT=&amp]uname -a),[/FONT][/COLOR] I got a string result, I hope that the operating system version is contained in the part which I copied down here:

OEM 4.15.0-122generic #124-Ubuntu SMP.  

I did try the next command regarding the chipset of the adaptor, and I don't think it is being recognised at all by the system. I got this string back in response:

command 'lsusb' not found, did you mean:command 'lsusb' from deb usbtils
try: sudo apt install <deb name>

The adapter is called, Wi-Fi Nano 11ac adapter, Dual Band, AC600 Dual Band,  2.4GHz+5.8GHz

That is all I have right now and I really hope you know what it means. I have not checked the url for the driver site which you have kindly provided yet. I will wait for any advice you might have first.

thanks again,
cliff.

We all started without experience at some point. Just hang in there. It is a fun ride.

We are making progress:

Based on the two sets of driver were on the cd and your info that it says it is an AC600 Dual Band adapter, it is highly likely that the chipset you have is either 8811cu or 8821cu. The driver for both of these chipsets is the RTL8821CU. A modern version of this driver can be found here:

[https://github.com/morrownr/8821cu](https://github.com/morrownr/8821cu)

However, before we can proceed, I recommend we discuss the version of Lubuntu you have installed. The 4.15 kernel is somewhat dated so you have installed an older version of Lubuntu... maybe 16.04? My recommendation is to start with the most recent LTS version that your computer can do well with. You can download Lubuntu from this site:

[https://lubuntu.me/](https://lubuntu.me/)

To determine if Lubuntu 20.04.1 LTS will work well on your system, can you tell use what CPU and amount of RAM your system has?

---

### Post by cliff-bjazz on 2020-11-03
Hi,
I really appreciate that. My problem with your last piece of advice is that I got this version of Ubuntu from eBay, and it came on a preinstalled, bootable usb drive. I have not the knowledge to do a new install from a downloaded file, nor do I know how to config a bootable CD or USB drive. My thought is to try to get these drivers to work with this version of Ubuntu although outdated. Then maybe would it be possible to update the operating system from within the present one?

I have the updated 8821cu drivers and I am going to follow the procedure for installing them now, I'll reboot after that into windows to get the details of the CPU and RAM either way, and I'll let you have them, and the results of this dongle installation attempt in a bit.

Thank you very much,
cliff.

---

### Post by mastablasta on 2020-11-04
well if you have 32 bit CPU, you will have to move away from Ubuntu as 32 bit CPU support is phased out. 32 bit applications are still supported.

> **cliff-bjazz said:**
>  Then maybe would it be possible to update the operating system from within the present one?


bad idea. Lubuntu moved from LXDE desktop to LXQT. an update could bring all sorts of issues. a fresh start is a much better option. wi-fi drive might even work out of the box on it.

you don't nee dmuch knowledge. you donlnoad the OS image and either burn it to DVD as an image file or if you have a free usb you use something like balena etcher: [https://www.balena.io/etcher/](https://www.balena.io/etcher/) (there are others like linuxliveUSB creator, unetbootin,  yumi...). then the application will guide you to burn the image to usb. basic process is:

1. download image file
2. start selected application
3. select USB drive you will put the linux on
4. let it do it's job
5. reboot and boot from USB

if you use CD/DVD process is similar.
1. download the image file
2. insert CD into drive and burn the file as image to it.
3. let it do it's job
4. reboot and boot from CD/DVD

there are a bunch of freeware or opensource XP apps that will do this:
you can use [http://www.freeisoburner.com/](http://www.freeisoburner.com/)
of this one: [https://cdburnerxp.se/help/Data/burn-iso](https://cdburnerxp.se/help/Data/burn-iso)
or [https://www.imgburn.com/](https://www.imgburn.com/)

to download you go here (after you figure out what CPU you have:
[https://lubuntu.net/](https://lubuntu.net/) - they are still at 19.10 :O

It wozul dbe best to use an LTS as they get longer support time, so no need to upgrade for 3 years (in case of Ubuntu 5 years)

Xubutnu is also quite light and has the latest 20.04 LTS version available: [https://xubuntu.org/](https://xubuntu.org/) 

Ubuntu Mate is light as well as it uses the old Gnome interface known for it's simplicity towards the users: [https://ubuntu-mate.org/](https://ubuntu-mate.org/)

and i say give Kubutnu a go as well while you are testing which one suits you the most. Kubuntu uses KDE and has a graphical interface for almost anything. in my opinion is is quite similar to XP in how it is managed. so we in family switched to this one and no one had any issues finding things they need: [https://kubuntu.org/](https://kubuntu.org/)

---

### Post by morrownr on 2020-11-04
Cliff,

I doubt you get very far installing the driver. In order for us to help you, we really need you to answer some of our questions:

What CPU do you have? We need to know if it is 32 bit or 64 bit and how much horsepower it has?

How much ram do you have?

Do you have an ethernet port and can you connect it to something to get internet access, at least temporarily?

With this basic information we can likely come up with a plan to get you going.

---

### Post by cliff-bjazz on 2020-11-04
Hi,
Thank you Mastablasta for your detailed guidance, I appreciate it very much.

Morrownr,
 Thank you also. your guidance did work in the end despite my machine being on the old side with not much ram and not a super fast CPU. I followed these steps thanks to you:

1/ I downloaded the latest Lubuntu distro and using Rufus, I burned the ISO onto the original USB Drive that came from ebay.
2/ I updated the operating system from the boot menu and it installed great, still giving me the option to boot windows XP as an alternative.
3/ I then downloaded the updated wireless drivers which you pointed me too and I followed the instructions to install them, they failed to install because of the absence of dkms.
4/ I connected an Ethernet cable to the same machine and updated to install dkms and all its dependencies.
5/ After that I followed the process to install the wireless drivers again and it worked. 

I now how a wireless connection and a working Lubuntu operating system on a dual boot.

Thank you very much for your time and concern, even though I may have got lucky this time, I do appreciate all of the technical information which so many of you have taken the time to share with me, I will read all of it and make notes.

Thanks again,
cliff.

---

### Post by grahammechanical on 2020-11-04
There are ways to get system information without using the command line but as I do not use Lubuntu I cannot give you directions. So, if you want to find out the version of Lubuntu that is installed run this command

```
cat /etc/os-release
```

This is the printout from my machine as a comparison

> NAME="Ubuntu"
VERSION="20.04.1 LTS (Focal Fossa)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 20.04.1 LTS"
VERSION_ID="20.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=focal
UBUNTU_CODENAME=focal


If you are using Lubuntu 16.04 then you should know that the developers stopped supporting Lubuntu 16.04 in April 2019. The good news is that Lubuntu 18.04 comes in  32bit (i386) version

> Please do note that we will continue to support Lubuntu 18.04 LTS i386  users as a first-class citizen until its End of Life date in April of  2021.

[https://www.phoronix.com/scan.php?page=news_item&px=Lubuntu-No-More-32-Bit](https://www.phoronix.com/scan.php?page=news_item&px=Lubuntu-No-More-32-Bit)

Where to get a Lubuntu 18.04 32 bit ISO image

[http://cdimage.ubuntu.com/lubuntu/bionic/daily-live/current/ ]("http://cdimage.ubuntu.com/lubuntu/bionic/daily-live/current/")

It is possible to upgrade from 16.04 to 18.04. There are risks involved but there are also risks involved in doing a fresh install. As this is a recent install of Lubuntu and you did it yourself without deleting MS Windows you should be a bit more confident. Online upgrades become more risky the more we customize the desktop. If you have a default install the risk is a lot less. Just so you have sufficient information to make your decision.

Regards.



[URL="http://cdimage.ubuntu.com/lubuntu/bionic/daily-live/current/"]
[/URL]

---

### Post by cliff-bjazz on 2020-11-04
Hi Grahammechanical,
Hope I spelled your ID correctly, Thank you for the code to get the release version. Luckily I did download the latest supported version from the Ubuntu main site, and I got it in the 32bit version as well. Like I said before, I did kind of get lucky with this issue as I am well aware of how it can spiral into a headache very fast.

Thanks again,
cliff
[[COLOR=#000000]grahammechanical[/COLOR]]("https://ubuntuforums.org/member.php?u=1087323")[COLOR=#000000] [/COLOR]

---

### Post by morrownr on 2020-11-05
Good job Cliff. Not having dkms and the other requirements installed do require you to temporarily hook up to an alternative source of internet... or at least that is generally the easier solution. One thing I do is keep handy at least one usb wifi adapter that is supported by an in-kernel driver. We can make suggestions if you want and these devices are generally very cheap. It seems you are well on your way so good luck.

Nick

---

