---
title: "Can't play any video-DVD in ubuntu 10.04 lucid"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by Suranjandeo on 2010-07-21
Hello brothers and sisters,
I have installed Ubuntu 10.04 lucid. I have also fin ished download all upgrades showing in upgrade manager. 

But, when i try to play any video file, wmv file, any CD or DVD from removable drive-- means, any video file in any formate in movie player then computer shuts down. 

Then one person suggested me to download gxine. Then i downloaded it through synaptic manager. But when i start gxine computer shuts down. 

Audio is playing well in Rhythmicbox music player. But i am unable to play video. Pls help
waiting....

:(

---

### Post by spydeyrch on 2010-07-21
in the ubuntu program manager (I can't remember the exact name of the program but it allow you to install new programs, kind of like an ubuntu store. Sorry I am having a brain fart right now.) You need to search for the ubuntu-restricted. Install that. Also install VLC. One other thing that I would recommend is installing the medibuntu repo.

[Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

That should get you up and running. If you have questions, come back to this thread and post your issues/concerns/questions/success. :D

-Spydey:KS

P.S. On the Medibuntu site, read everything through at least twice so that you grasp what is going on. If you don't understand something or are unsure of how your system will be affected, please please please ask before you do anything. It is better to ask 1000 times and succeed then try once and fail.

---

### Post by Suranjandeo on 2010-07-21
I am waiting. This will be the great help if someone will help me about my problem with playing video file. I can't play any video file. Not the file from the harddisk or not from any CD or DVD. Whenever try then computer shuts down. 

But on same computer i have XP windows also. And i can play videos on it.

waiting for help....

---

### Post by Thryn on 2010-07-21
> **spydeyrch said:**
> in the ubuntu program manager (I can't remember the exact name of the program but it allow you to install new programs, kind of like an ubuntu store. Sorry I am having a brain fart right now.) You need to search for the ubuntu-restricted. Install that. Also install VLC. One other thing that I would recommend is installing the medibuntu repo.

[Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

That should get you up and running. If you have questions, come back to this thread and post your issues/concerns/questions/success. :D

-Spydey:KS
It's Synaptic Package Manager.

Although I have no idea why your computer would shut down when you try to play a file. All mine did before I installed ubuntu-restricted was give me an error message.

---

### Post by spydeyrch on 2010-07-21
I know about synaptic package manager but that is not the one that I was refering to. Thanks though.

It is under appliations -> right at the bottom. It has an icon like a paper grocery bag full of apps. Man I hate it when I have something right no the tip of my tongue and can't remember it! :(

This program has categories and very clean. I will see if I can find it really quick and post back.

-spydey

---

### Post by spydeyrch on 2010-07-21
It is called the Ubuntu Software center. Something sooooo obvious yet for the life of me I couldn't get it to work properly. but oh well.

Oh, also, I would make sure that you have your GPU drivers installed correctly via system -> admin -> hardware. Let me know if you need more details.


-Spydey :KS

---

### Post by Suranjandeo on 2010-07-21
Hello, 
Brother Spydey,
Do you mean "Ubuntu software Center" which right bottom under applications.

---

### Post by Suranjandeo on 2010-07-21
Yes pls, tell me in detail about System-adm-hardware. I went there and it is written- "No proprietary drivers are in use on this computer."

---

### Post by spydeyrch on 2010-07-21
ok, are you using a laptop or a desktop? What model is your GPU?

-Spydey

---

### Post by Suranjandeo on 2010-07-21
I am using Dell Latitude D-400 laptop.

---

### Post by vivek40 on 2010-07-21
Buddy .. go to the top left corner.. click on applications.. then click on accessories.. click on terminal
once the terminal appears type :-
```

sudo apt-get install ubuntu-restricted-extras

```
it will ask your password.. type the password... dont worry as you type you wont see any stars or anything appearing just type it .. press enter.. the system will install all that is needed... run the videos have fun

---

### Post by spydeyrch on 2010-07-21
Have you tried to install the ubuntu-restricted package from the Ubuntu software center yet? What about VLC and medibuntu? I would recommend that you try those first. Then let me know how it went.


-Spydey:KS

---

### Post by Suranjandeo on 2010-07-22
Brother Vivek,
Namaskar.
I did it. I went in terminal and pasted it -- (sudo apt-get install ubuntu-restricted-extras) I am in India and it took several hours to download. But even then problem is persisting. Whenever i play any audio, video, DVD files in movie player computer shuts down. Yes, i can play audio in Rhythemic box.

Pls help

---

### Post by Suranjandeo on 2010-07-22
Brother Vivek,
Namaskar.
I did it. I went in terminal and pasted it -- (sudo apt-get install ubuntu-restricted-extras) I am in India and it took several hours to download. But even then problem is persisting. Whenever i play any audio, video, DVD files in movie player computer shuts down. Yes, i can play audio in Rhythemic box.

Pls help

---

### Post by vivek40 on 2010-07-22
Cool .. chalo that means you are able to get the sound now...:-).. do one thing install vlc player too.. it could be some codec problem or something and vlc wil definitely be able to handle this. However computer shutting down is a mystery which we might want to handle if vlc does not work... 
Please install vlc like this:
1. goto ubuntu software centre(applications>Ubuntu Software centre)
2. When it opens , type vlc in the search box on the top right corner
3. select vlc and click on the install button.
4. once it is installed .. you can access the player by going to applications>sound and video>vlc player
5.now play the video file in vlc player and not movie player.

It should work now

---

### Post by Suranjandeo on 2010-07-22
I could play audio file in Rhythemic box before. I was not the problem. But whenever i play either audio or video in movieplayer then computer shuts down. When i try audio then for one second it play then shut down. and with video straight way it shuts down.

According to you guideline now i am downloading VLC. I will inform after installing. It will take time b/c of slow connection.
Thank you for giving your valuable time to me.

---

### Post by Suranjandeo on 2010-07-22
Namaskar brother,

According to your suggestion i went to Ubutu software under application and downloaded VLC media player. Now it is showing under Application > sound and video > VLC media player.

When i try to play one movie CD then error message came.First i right click on the volumelabel and opened it with VLC player. Then following message came------

File reading failed:
VLC could not read the file.
File reading failed:
VLC could not read the file.
VLC can't recognize the input's format:
The format of 'file:///media/VolumeLabel/cdi/cdi_font.fnt' cannot be detected. Have a look at the log for details.
File reading failed:
VLC could not read the file.
---------------

Then i opened the volume label > mpegav > avseq01.dat
And opened it with VLC media player then following message came----

File reading failed:
VLC could not read the file.

Pls. help

---

### Post by vivek40 on 2010-07-22
Have you tried any other cds

---

### Post by Suranjandeo on 2010-07-22
I have tried Audio Mp3 cd and it is playing well in VLC media player. When i try video Cd then error message comes what i have sent half an hour ago. It is not reading file.
And when i try to play DVD then computer shuts down. 
I have tried many audio, video and DVDs. 

In movie player trying to play any audio video file then computer was sutting down. ATleast in VLC audio is playing well, video is giving error and only DVD is shutting down the computer.

Thanks a lot for your kind help

---

### Post by vivek40 on 2010-07-22
Suranjan please try this, go to vlc player and:-

Tools->Preferences->Video->Output to X11 Video Output.

save it close it, and then try using it again.. let us see

---

### Post by anewguy on 2010-07-22
Also, via Synaptic Package Manager, do the following:

- mark the gstreamer good, bad and ugly sets for installation

- be sure libdvdcss2 (it's something like that) is installed.  If not, mark it for installation.  At one point in time you executed a shell script from a downloaded package to activate this - I don't know if that's the case yet or not.

- click the green check mark for "Apply" and wait for everything to install and finish, then exit the package manager.

Put a DVD in your drive and wait for it to spin up, then see if it will play.

Being in India, I don't know if region codes might be biting you or not as well.

Dave ;)

---

### Post by SunnyRabbiera on 2010-07-22
Yes install libdvdcss, it might help with your issue.
Though there are some dvd's and disks that dont get along with linux, it all goes down to codecs as most of the codecs you install for ubuntu are reverse engineered

---

### Post by spydeyrch on 2010-07-22
As I previously mentioned, I would recommend that you add the mediubuntu repo to your software sources.

[Medibuntu]("http://medibuntu.org/")

If you want, you could just copy and paste the following in a terminal:

1.) ```
 sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update 
```2.) ```
 sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu 
```3.) ```
 sudo apt-get install libdvdcss2 
```4.) Depending on if your version of ubuntu is x32 or x64 (32 bit or 64 bit) you will either need 32 bit codecs or 64 bit codecs.

-32bit
```
 sudo apt-get install w32codecs 
```-64bit
```
 sudo apt-get install w64codecs 
```That should make it so that you are able to view videos through VLC. I would recommend that you not use the other video player as it crashes your system.

Let us know if you need anything else. :D

-Spydey:KS

---

### Post by Suranjandeo on 2010-07-22
Copy and pasted all these things in the terminal and downloaded everything. Nothing happened. Pro blem persists.

---

### Post by Suranjandeo on 2010-07-22
Vivek bhai,
 Sorry for delay reply.
I went in Tools->Preferences->Video->Output to X11 Video Output.
I saved and closed and again tried. Nothing happened. I changed output and tried all one by one listed there. Nothing happened. Problem persists.

---

### Post by Suranjandeo on 2010-07-22
Gstreamer, libdvdcss2  is installed. Even then problem persists.

---

### Post by DJohnson1966 on 2010-07-22
I have just followed all the posts and installed all the packages etc.  Mine now works :) Using dual boot with xp pro on a dell inspiron 1545:popcorn:

---

### Post by DJohnson1966 on 2010-07-22
it works with vlc, can i un install movie player or are some files needed for anything else?

---

### Post by spydeyrch on 2010-07-22
Yes, you can uninstall movie player, if you want to. Do it via the ubuntu software center.

Glad to see that it worked. :D

-Spydey :KS

---

### Post by spydeyrch on 2010-07-22
> **Suranjandeo said:**
> Copy and pasted all these things in the terminal and downloaded everything. Nothing happened. Pro blem persists.

Did you do them all one by one and not a huge massive copy paste into the terminal?

They need to be run one by one.

One quick question for you. Do you have any important info in your ubuntu OS? Important files, pictures, videos, music, etc?

Also, are you dual booting your computer? Do you have another OS (OSX, Windows, etc.) on your computer other than Ubuntu?

I ask because Mybe if were to start from scratch and get everything done in the right order, we could better trouble shoot the issue. Just an idea. But I would only recommend it if you either don't have anything on your machine of importance, or have everything backuped. Also, if you have a dual boot system, it helps to know. 


-Spydey :KS

---

### Post by wideyes on 2010-07-22
This worked for me! Thanks to all who contributed helpful suggestions :)

---

### Post by spydeyrch on 2010-07-22
Awesome!! I am glad to hear that you got it working.  :D

-Spydey :KS

---

### Post by vivek40 on 2010-07-22
Well Suranjan, I will go by what spydeyrch said... A reinstall might be helpful here.!

---

### Post by Suranjandeo on 2010-07-23
Brother Spydey,
I am sorry for delay reply. I am in India that's why it happened.

I ran tasks one by one in the terminal not pasted huge stuff.

I have important files on my Ubutu 10.04 lucid.

Yes i have dual booting. other is windows xp2.

---

### Post by anewguy on 2010-07-23
I'm still curious about region codes - it appears the OP is in India and everyone who has posted back getting this working appears at glance not to be.  I'm in Windows right now - can somebody walk the OP through checking region code for the device itself and then for Ubuntu?

Dave ;)

---

### Post by Suranjandeo on 2010-07-23
One other problem has come that now computer is booting well but sometimes while working screen goes black and it gives message---

"Ubuntu is running in low-graphics mode
your screen, graphics card, and input device setting couldnot be detected correctly. You will need to configure those yourself."

On the place of mouse it is showing x.
when i click on "ok" then options comes to restart, shut down or run on low graphic mode for one session.

This problem may help you all to know the cause of my video-DVD not playing problem.

---

### Post by spydeyrch on 2010-07-23
> **Suranjandeo said:**
> One other problem has come that now computer is booting well but sometimes while working screen goes black and it gives message---

"Ubuntu is running in low-graphics mode
your screen, graphics card, and input device setting couldnot be detected correctly. You will need to configure those yourself."

On the place of mouse it is showing x.
when i click on "ok" then options comes to restart, shut down or run on low graphic mode for one session.

This problem may help you all to know the cause of my video-DVD not playing problem.


Could you give us the specs of your computer?

CPU
GPU
Motherboard
RAM
HDD
ODD
OS


Also, give us an idea of how you went about installing ubuntu from start to finish.

-Spydey :KS

---

### Post by Suranjandeo on 2010-07-23
I don't know how to know all about
 CPU
GPU
Motherboard
RAM
HDD
ODD
OS  Pls tell me how to check it.

---

### Post by spydeyrch on 2010-07-23
> **Suranjandeo said:**
> I don't know how to know all about
 CPU
GPU
Motherboard
RAM
HDD
ODD
OS  Pls tell me how to check it.


Ok, so this information would be basic information about your computer. It is the specifications of your computer.

CPU = Central Processing Unit

GPU = Graphical Processing Unit (also known as a video card or graphics card, sometimes integrated with the motherboard)

Motherboard = It is the main large circuit board that all of your peripherals attach to. Your CPU is inserted into it, along with your RAM, GPU, etc. It is also abbreviated as 'mobo'.

RAM = Random Access Memory or in plain terms, your computers memory.

HDD = Hard Disk Drive, or Hard Disk. It is were your OS is installed and all of your files are kept/stored.

ODD = Optical Disk Drive. It is your CD and/or DVD drive.

OS = Operating System. It is the main system that you have, or in your case dual system, installed on your computer. Windows 95/98/MEXP/Vista/7 are all operating systems. Apple's OSX is an operating system. Linux can be used to create operating systems. Ubuntu is an operating system based off of linux.

I will give you an example of how we typically represent the specs of our machines. This one is mine:

CPU - AMD Phenom 9950 2.6GHz oc'd 3.2GHz

GPU - 2 x ATI HD3870 in crossfire mode

Mobo - ASUS M3A79-T Deluxe 790FX/SB750

RAM - 4GB DDR2 PC8500 1066MHz

HDD - 1TB, 3 x 500GB

ODD - CD/DVD Burner

OS - Win7 Pro x64, Mint9 x64, Ubuntu 10.04 x64

---------------

I gave more specifics than what is really needed. But if you could give us an idea of what your machine is made from, that might help us better understand why certain things are happening when they shouldn't.

-Spydey :KS

---

### Post by spydeyrch on 2010-07-23
> **Suranjandeo said:**
> I don't know how to know all about .......
 
OS  Pls tell me how to check it.


I am drawing a blank right now but there is a terminal command that will allow you to see what the components of your machine are. :(

Hopefully someone else will jump in and give us the terminal command to get that info. ;)

-Spydey :KS

---

### Post by vivek40 on 2010-07-23
Hii Suranjan.. sorry for the late reply...
Spydey I guess he can use 

sudo lshw  in the terminal.


Suranjan .. just type "sudo lshw" in the terminal .. you will get a long list of output.. copy that, go to [http://pastebin.com/](http://pastebin.com/) , paste everything there in the box, click submit and post the link back here. Well that is my preferred way..!:-)

---

### Post by spydeyrch on 2010-07-23
> **vivek40 said:**
> Hii Suranjan.. sorry for the late reply...
Spydey I guess he can use 

sudo lshw  in the terminal.


Suranjan .. just type "sudo lshw" in the terminal .. you will get a long list of output.. copy that, go to [http://pastebin.com/](http://pastebin.com/) , paste everything there in the box, click submit and post the link back here. Well that is my preferred way..!:-)

Exactly!!! That is what I was looking for. Thanks!

```

sudo lshw

```

-Spydey :KS

---

### Post by Suranjandeo on 2010-07-26
Since two days we had not electricity. Remember i am in India. And this is not unusual here. 

According to your's guideline i have pasted all details of my computer in pastebin. Pls check it and see if something can be done to my computer.

waiting....

suranjan

---

### Post by Suranjandeo on 2010-07-26
Just now i have checked my e-mail ID and one message is there from pastebin.com. Information is that my paste is [http://pastebin.com/qgZXi3TE](http://pastebin.com/qgZXi3TE)

---

### Post by spydeyrch on 2010-07-26
Sorry, I am at work when I check the forum and that pastebin website is blocked by our proxy.  Could you just run that command in the terminal

```

sudo lshw

```and then copy it and paste it in your post?

Let me know if you have any questions.

-Spydey

---

### Post by Suranjandeo on 2010-07-26
Okay, It is here all the details about my computer..

```
baba@baba:~$ sudo lshw
[sudo] password for baba: 
baba                      
    description: Portable Computer
    product: Latitude D400
    vendor: Dell Computer Corporation
    serial: 2ZN1G51
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=44454C4C-5A00-104E-8031-B2C04F473531
  *-core
       description: Motherboard
       product: 0W0328
       vendor: Dell Computer Corporation
       physical id: 0
       serial: .2ZN1G51.CN7016646PA0D5.
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A05 (05/24/2004)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1400MHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.9.5
          slot: Microprocessor
          size: 1400MHz
          capacity: 1700MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 1MiB
             capacity: 1MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 512MiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             physical id: 0
             slot: DIMM_A
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             physical id: 1
             slot: DIMM_B
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-display:0
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:11 memory:f0000000-f7ffffff(prefetchable) memory:faf80000-faffffff ioport:c000(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:e8000000-efffffff(prefetchable) memory:faf00000-faf7ffff
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:bf80(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:bf40(size=32)
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:bf20(size=32)
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:11 memory:faeffc00-faefffff
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:e000(size=4096) memory:fc000000-fdffffff memory:20000000-29ffffff(prefetchable)
           *-network:0
                description: Ethernet interface
                product: NetXtreme BCM5705M Gigabit Ethernet
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 01
                serial: 00:0f:1f:ab:00:50
                capacity: 1GB/s
                width: 64 bits
                clock: 66MHz
                capabilities: pm vpd msi bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=5705-v3.11 latency=32 link=no mingnt=64 multicast=yes port=twisted pair
                resources: irq:11 memory:fcff0000-fcffffff memory:28000000-2800ffff(prefetchable)
           *-pcmcia:0
                description: CardBus bridge
                product: PCI7510 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@0000:01:01.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:11 memory:fc000000-fc000fff ioport:e000(size=256) ioport:e400(size=256) memory:20000000-23ffffff(prefetchable) memory:2c000000-2fffffff
           *-pcmcia:1
                description: CardBus bridge
                product: PCI7510,7610 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1.1
                bus info: pci@0000:01:01.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:11 memory:fc001000-fc001fff ioport:e800(size=256) ioport:1000(size=256) memory:24000000-27ffffff(prefetchable) memory:30000000-33ffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCI7410,7510,7610 OHCI-Lynx Controller
                vendor: Texas Instruments
                physical id: 1.2
                bus info: pci@0000:01:01.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2
                resources: irq:11 memory:fcfef800-fcfeffff memory:fcfe8000-fcfebfff
           *-generic UNCLAIMED
                description: System peripheral
                product: PCI7410,7510,7610 PCI Firmware Loading Function
                vendor: Texas Instruments
                physical id: 1.3
                bus info: pci@0000:01:01.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
                resources: ioport:ecf8(size=8)
           *-network:1
                description: Network controller
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@0000:01:03.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=b43-pci-bridge latency=32
                resources: irq:5 memory:fcfec000-fcfedfff
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:11 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16) memory:2a000000-2a0003ff
           *-disk
                description: ATA Disk
                product: SAMSUNG HM160HC
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: LQ10
                serial: S12TJDQZ109230
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0005b0b0
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 0ecaf970-8a57-044f-8f39-5156c95b8104
                   size: 71GiB
                   capacity: 71GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-05-28 20:39:42 filesystem=ntfs state=clean
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:5 ioport:d800(size=256) ioport:dc40(size=64) memory:faeff800-faeff9ff memory:faeff400-faeff4ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: ioport:d400(size=256) ioport:d080(size=128)
     *-scsi
          physical id: 1
          bus info: usb@1:4
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-cdrom
             description: DVD reader
             product: RW/DVD GCC-4243N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: A102
             capabilities: removable audio cd-r cd-rw dvd
             configuration: status=nodisc
  *-battery
       product: DELL 0006T08
       vendor: Sanyo
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 42000mWh
       configuration: voltage=11.1V
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:96:c4:6e:1f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1
       description: Ethernet interface
       physical id: 3
       logical name: bnep0
       serial: 00:10:c6:4b:7c:13
       capabilities: ethernet physical
       configuration: broadcast=yes ip=10.0.66.2 multicast=yes
baba@baba:~$
```

---

### Post by anewguy on 2010-07-26
There have been problems in the past with ubuntu and the 855 gpu.  There is a parameter you can put in at boot to get around it (I'm in Windows right now but I'll search the forum to see if I can find it).  This may be causing part of your problem.

From there, as hard as it may be for others to understand why, I still think we need to check the region code on the drive.  Might be ok, but it can't hurt to check.

Dave

---

### Post by anewguy on 2010-07-26
You may also want to try this as a test:

when the grub menu comes up, press the "e" key to edit the default selection.

Where you see something like "quiet splash" change it to:

i915.modeset=0 


Then look on the screen for the instructions to boot - I don't remember them off the top of my head.

After that comes up, try a video again.

Dave

---

### Post by spydeyrch on 2010-07-26
> **anewguy said:**
> There have been problems in the past with ubuntu and the 855 gpu.  There is a parameter you can put in at boot to get around it (I'm in Windows right now but I'll search the forum to see if I can find it).  This may be causing part of your problem.

From there, as hard as it may be for others to understand why, I still think we need to check the region code on the drive.  Might be ok, but it can't hurt to check.

Dave


I would agree with the region thing although I don't know how to check it. :p

-Spydey :KS

---

### Post by mc4man on 2010-07-26
> I would agree with the region thing although I don't know how to check it.
While worth checking, -  because the Op can't play any video don't think it's the main cause  - the intel chip seems more likely
(run vlc from a terminal for error messages, if any.

To ck. region setting on a dvd drive
```
sudo apt-get install regionset
```

Then with a disk in the drive, (any disk will do), run 
```
regionset
```
line 4 will tell
type: SET
or
type: NONE

A drive only needs to be set once (some don't ever need to be set), linux players don't enforce region coding.

====================================================================

 Totally OT.

The only common drives that present 'special' issues are Matshita laptop drives which will only allow access to encrypted sectors when there is a region match between the drive and disc.

In that case (**not relevant here**), you pick your region and only play those discs - regions should never be changed to match disc unless there is compelling reason - after 5 changes the drive is locked forever.

Recently a firmware method has developed for some Matshita laptop drives - needs to be done in windows

---

### Post by jtarin on 2010-07-26
Try VLC player first before you start going down the wrong road....if you say it works in XP then it should work with VLC.

---

### Post by cpcpcp on 2010-09-13
I think I have lost the plot. :)
Medibuntu is installed. and somethings I have been told are essential have been loaded but 

Totem opens pauses and then closes.
VLC opens and, without a pause, closes.

I have been here[//https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("http://https//help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")
I have installed libdvdcss2 and the W32 codecs
and I am pretty sure I have the GOOD and the BAD and the UGLY in place.

I[B]s there something I can post by way of output that will let you wiser folks say"dah stupid you have missed out XYZ so do this etc."?
[/B]
The CD I am trying with plays well if I dual boot into Windows Vista - not that I particularly want to.

Chris

---

### Post by andy_g on 2011-01-01
I had this kind of issue with playing DVD's on my HP 2510p running 10.04 dvd's would play on my other 10.04 laptop with the relevant library's and codex no problem, the regionset fixed my HP it was set on Region 1 and I'm in Region 2! Is there a way of playing DVD's from Any Region? thanks for all the advice and comments this DVD issue has been bugging me for ages Happy New year

---

### Post by jtarin on 2011-01-01
> **andy_g said:**
> I had this kind of issue with playing DVD's on my HP 2510p running 10.04 dvd's would play on my other 10.04 laptop with the relevant library's and codex no problem, the regionset fixed my HP it was set on Region 1 and I'm in Region 2! Is there a way of playing DVD's from Any Region? thanks for all the advice and comments this DVD issue has been bugging me for ages Happy New year[libdvdcss available for download.]("http://www.videolan.org/developers/libdvdcss.html")

---

### Post by jtarin on 2011-01-01
> **cpcpcp said:**
> I think I have lost the plot. :)
Medibuntu is installed. and somethings I have been told are essential have been loaded but 

Totem opens pauses and then closes.
VLC opens and, without a pause, closes.

I have been here[//https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("http://https//help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")
I have installed libdvdcss2 and the W32 codecs
and I am pretty sure I have the GOOD and the BAD and the UGLY in place.

I[B]s there something I can post by way of output that will let you wiser folks say"dah stupid you have missed out XYZ so do this etc."?
[/B]
The CD I am trying with plays well if I dual boot into Windows Vista - not that I particularly want to.

ChrisTry starting VLC from the commandline for meaningful output.

---

### Post by Raizen44 on 2011-03-17
Hope someone here can help, I'm having similar problems. I can play vids from the HDD and external drives, but I can't play DVD movies with either Totem and VLC. can't play any DVD's. Used to get an error message, but now it simply keeps on reading and the movie doesn't play. here are my laptop's specs, hope someone can help

acheron                   
    description: Computer
    product: M360S
    vendor: CLEVO Co.
    version: N/A
    serial: None
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31 smp-1.4 smp
    configuration: administrator_password=enabled boot=oem-specific cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=0090F54D-AB74-0000-0000-000000000000
  *-core
       description: Motherboard
       product: M360S
       vendor: CLEVO Co.
       physical id: 0
       version: None
       serial: None
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: 6.00 (11/07/05)
          size: 98KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video usb
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M processor         1500MHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.9.5
          slot: Socket 479M
          size: 1500MHz
          capacity: 3GHz
          width: 32 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts
        *-cache
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: 10
          slot: System board or motherboard
          size: 768MiB
          capacity: 3GiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM1
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM2
             size: 256MiB
             width: 64 bits
        *-bank:2
             description: DIMM DRAM [empty]
             physical id: 2
             slot: DIMM3
     *-pci
          description: Host bridge
          product: 661FX/M661FX/M661MX Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=64
          resources: irq:0 memory:e0000000-e3ffffff
        *-pci
             description: PCI bridge
             product: SiS AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:a000(size=4096) memory:e4100000-e41fffff memory:e8000000-efffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 cap_list
                configuration: latency=0
                resources: memory:e8000000-efffffff(prefetchable) memory:e4100000-e411ffff ioport:a000(size=128)
        *-isa
             description: ISA bridge
             product: SiS963 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 25
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2 SMBus Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0
             resources: irq:0 ioport:8100(size=32)
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_sis latency=128
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:9400(size=16)
           *-disk
                description: ATA Disk
                product: HTS421240H9AT00
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: HACO
                serial: HKA040AHCUDESL
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000e098b
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: a84832e9-5d7f-4615-a7ce-dd3cfab26fae
                   size: 35GiB
                   capacity: 35GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-09-27 11:59:15 filesystem=ext4 lastmountpoint=/S%W&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;p&#65533;-&#65533;ew &#65533;&#65533;x/&#65533;d&#65533;-&#65533;'!&#65533;&#65533;wI&#65533;&#65533;wI&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;-&#65533;&#65533;-&#65533;z modified=2011-03-13 02:53:49 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-03-17 11:37:49 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1610MiB
                   capacity: 1610MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1610MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: CDW/DVD TS-L462C
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: TS01
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-communication UNCLAIMED
             description: Modem
             product: AC'97 Modem Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.6
             bus info: pci@0000:00:02.6
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=173 maxlatency=11 mingnt=52
             resources: ioport:8400(size=256) ioport:9000(size=128)
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=173 maxlatency=11 mingnt=52
             resources: irq:18 ioport:8800(size=256) ioport:9080(size=128)
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:20 memory:e4008000-e4008fff
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:21 memory:e4009000-e4009fff
        *-usb:2
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=80
             resources: irq:23 memory:e400a000-e400afff
        *-network:0
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 91
             serial: 00:90:f5:4d:ab:74
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=173 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10MB/s
             resources: irq:19 ioport:8c00(size=256) memory:e400b000-e400bfff memory:38000000-3801ffff(prefetchable)
        *-network:1
             description: Wireless interface
             product: RT2561/RT61 rev B 802.11g
             vendor: RaLink
             physical id: d
             bus info: pci@0000:00:0d.0
             logical name: wlan0
             version: 00
             serial: 00:08:a1:9c:3a:fb
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=rt61pci ip=192.168.2.103 latency=64 multicast=yes wireless=IEEE 802.11bg
             resources: irq:16 memory:e4000000-e4007fff
        *-pcmcia
             description: CardBus bridge
             product: CB1410 Cardbus Controller
             vendor: ENE Technology Inc
             physical id: e
             bus info: pci@0000:00:0e.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:18 memory:38020000-38020fff ioport:1000(size=256) ioport:1400(size=256) memory:30000000-33ffffff(prefetchable) memory:34000000-37ffffff
  *-remoteaccess UNCLAIMED
       vendor: SiS
       physical id: 1
       capabilities: inbound
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

---

### Post by Raizen44 on 2011-03-17
additional: I have also already installed and verified that I have all the codecs (libdvdcss2 and 4, win32) and I'm still having problems with playing DVD's...

---

