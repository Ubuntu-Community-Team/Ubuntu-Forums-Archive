---
title: "4:3 resolutions span only part of display on netbook"
date: 2011-08-29
forum: New to Ubuntu
---

### Post by resander on 2011-08-29
This is for a Fujitsu FMV-BIBLO LOOX T70X netbook obtained in Japan and used by wife and younger family members in UK. It has English Windows Vista Home Premium. However, for some reason the Vista has three partitions (c:, d: and e:) that are now becoming too small and make the netbook awkward to use. I have never used Vista and do not want to learn how to repartition the disk. There is no Vista install CD for a reinstall, so would like to install Ubuntu instead.

I downloaded Ubuntu 10.04 and I found WIFI Internet did not work from the Live CD, but worked from the Live CD for Ubuntu 11.04. From Live CD everyone found screen resolution 1280x768 too small and changing to preferred resolution 800x600 came out with unused left and right margins. 

However, for Vista all resolutions 1280x768, 1024x768, 800x600 and 640x480 completely span the whole screen, i.e. there are no unused left and right margins and this is what the family members want.

Can I make Ubuntu 11.04 do this too?

---

### Post by sffvba[e0rt on 2011-08-31
From this thread ([http://ubuntuforums.org/showthread.php?t=1334211](http://ubuntuforums.org/showthread.php?t=1334211)) it seems there is a way using a utility called xrandr.

In the thread they discus a way to add the bars (as opposed to getting rid of them) so I am sure with the correct command the reverse can be achieved.

I am not near a Linux machine at the moment, and I couldn't find a suitable command searching online so perhaps the man page for xrandr will assist you in finding the right command. (At the very least maybe someone else more clued up in it could see and respond :))

Hope you get it sorted out :popcorn:


404

---

### Post by JC Cheloven on 2011-08-31
> **resander said:**
> This is for a Fujitsu FMV-BIBLO LOOX T70X netbook obtained in Japan and used by wife and younger family members in UK. It has English Windows Vista Home Premium. However, for some reason the Vista has three partitions (c:, d: and e:) that are now becoming too small and make the netbook awkward to use. I have never used Vista and do not want to learn how to repartition the disk. There is no Vista install CD for a reinstall, so would like to install Ubuntu instead.
If you plan to use only ubuntu, you don't need to learn anything. Simply save your data to an external disk, and install ubuntu. Whenthe installer gives you the option, choose "use the entire disk". This will erase any existing partition and re-partition the whole disk for you.

> I downloaded Ubuntu 10.04 and I found WIFI Internet did not work from the Live CD, but worked from the Live CD for Ubuntu 11.04.  
Go for 11.04 then. Perhaps you could consider a lighter flavour of Ubuntu, as XUbuntu or LUbuntu, if you prefer fast over eye candy.

> From Live CD everyone found screen resolution 1280x768 too small  You mean the desktop elements and text are small? 
> and changing to preferred resolution 800x600 came out with unused left and right margins. However, for Vista all resolutions 1280x768, 1024x768, 800x600 and 640x480 completely span the whole screen, i.e. there are no unused left and right margins and this is what the family members want.
Can I make Ubuntu 11.04 do this too?
It sounds like a video driver issue that will be solved by itself when installed and connected to the internet. Anyway, to use a resolution of 800x600 seems too sad when your card and screen are capable of 1280x768. Wouldn't be better to keep this high resolution and using a larger font for desktop elements? It can be configured in system-> admin -> preferences, fonts tab.

Cheers
JC

---

### Post by resander on 2011-09-03
Many thanks for the kind advice...

Started 11.04 Live CD and issued xrandr from the Terminal to view the the commands supported. Also issued man xrandr for explanations of the xrandr commands and options. 

From what I could see the 'xrandr --scale <xfactor>x<yfactor> command would scale x and y, but I was not sure how to use it, so first changed the screen resolution to 800x600 and then issued xrandr --scale 1.5x1.5 and xrandr --scale 0.5x0.5 to see what would happen. Both attempts had no effect, i.e. the unused left and right margins remained.

Googled on 'xrandr --scale' and some of the matches reported that the scale command had no effect (it should have changed the display), i.e. that this is a bug.

Some other google matches mentioned that xrandr --output LVDS1 --mode <resolution> --scale <xfactor>x<yfactor> could be used to remap a screen resolution to another resolution that would not be supported by the hardware, but I do not know how to use this to get rid of the unused margins at 800x600. Anyone?

I also tried 1280x768 with larger fonts, but those that would be comfortably readable overflowed (vertically) the top window border. How do I fix this? What about other visual dialog elements like buttons? Would the text overflow these too or would the size of the visual element scale with the size of the font?

I have googled on netbooks and most that I found use/support 1280x768 resolution. Our Fujitsu netbook shows the lower 4:3 resolutons with unused left and right margins when using the Live CD.

Q1.  Do other netbooks also do this for the Live CD?

JC Cheloven mentions that a full install may find a display driver that stretches the 4:3 resolutions to cover the full display.

Q2.  Is that so? Or are there still 4:3 resolutions that come out with unused side margins on some netbooks?

Ken

---

### Post by JC Cheloven on 2011-09-06
> **resander said:**
> 
JC Cheloven mentions that a full install may find a display driver that stretches the 4:3 resolutions to cover the full display.
Q2.  Is that so? Or are there still 4:3 resolutions that come out with unused side margins on some netbooks?

It happened to me once, a similar problem with a screen disappeared when installing and updating. No guarantee though.

Please from your live session, with internet connection, run the hardware drivers utility (was it presented as "additional drivers" or something similar?). It's in the system menu. See if some drivers are offered for instalation. This would be a sign of probable better behaviour when installed.
Note.- don't install it from live. It requires a restart to take effect, and would be lost.

Anyway, in my opinion, you are taking more care than necessary to make everything work from the live session. In a fraction of the time you're thinking about it, you might have the whole thing installed. So you could see whether actually the screen issue is solved "automagically" or not, and also it would be easier for people here to help you with an eventual issue. Worst scenario would be to overrite everything installing some other OS, which AFAI-understand would be not worse than your present situation. 

In the meanwhile, if you want, please open a terminal from the live session and run ```
lspci
``` Please post back the output here so that we can see which video card your computer has. Thank you.

---

### Post by Vaphell on 2011-09-07
you prefer distorted image (stretched horizontally because that's what happens when you force widescreen display to show 4:3 image) to greater resolution? wth man?

Find settings responsible for DPI, bump it higher to achieve global zoom in effect

---

### Post by scruffyeagle on 2011-09-07
I don't know about Fujitsu, but I'm using a Dell Inspiron 9400 laptop running Ubuntu v10.04. It's screen is relatively wider than a standard monitor, and from what you said it sounds like your is too. When I first started using this, I experimented with my display settings in the BIOS. One setting resulted in a display that used the full height, but didn't use the entire width of the screen. The other setting stretched the display sideways to use the entire width. Perhaps your machine has a similar toggle switch setting in the BIOS? Windows & Ubuntu v11.04 might both have been compensating, correcting for the current setting whereas v10.04 doesn't.

---

### Post by resander on 2011-09-10
Thanks for advice...

JC Cheloven:
No drivers were offered for installation when clicking Additional Drivers in the System Settings Hardware section on the Live CD.

Here is the output from lspci issued from Live CD
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 14)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:03.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
08:03.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
08:03.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
08:03.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
08:03.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 03)  

```

and here is system information produced by Vista Control Panel System:
```

Processor:  Intel(R) Core (TM) CPU U7600 @ 1.20GHz 1.20GHz
  RAM:        2GB
  Type:       32 bit OS
  Device Manager
   Batteries
    Microsoft AC Adapter
    Microsoft ACPI-compliant Control methods battery
   Bluetooth
    Bluetooth RFBUS
    USB Bluetooth Driver*V2.0 EDR)
   Computer
    ACPI x86-based PC
   Disk Drives
    Toshiba MK8007GAH ATA Device
   Display adapters
    Mobile Intel(R) 945 Express Chipset Family
   DVD/CD ROM drives
    Matsushita DVD-RAM UJ-8525 ATA device
   IDE ATA/ATAPI controllers
    ATA Channel 0   
    ATA Channel 0
    ATA Channel 1
    Intel(R) 82801G (ICH7 Family) Ultra ATA Storage controllers - 27df
    Intel(R) 82801GBM/GHM (ICH7-M Family) Serial ATA Controller - 27c4
    Ricoh Memory Stick Host Controller
    Ricoh xD-Picture Card Controller
   IEEE 1394 Bus Host Controllers
    Ricoh OHCI Compliant IEEE 1394 Controller
   Imaging devices
    OEM camera
   Keyboard
    Japanese PS2 keyboard (106/109 key)
   Mice and other pointing devices
    PS2 compatible mouse
   Modems
    Agere Systems HDA modem
   Monitors
    Generic PnP monitor
   Network adapters
    Intel(R) PRO/Wireless 3945ABG Network connection
    Marwell Yukon 88E8055 PCI-E Gigabit Ethernet controller
   Other devices
    Toshiba Bluetooth
   PCMCIA adapters
    Ricoh R/RL/SC476(II) or compatible cardbus controller
   Processor
    Intel(R) Core (TM) CPU U7600 @ 1.20GHz
    Intel(R) Core (TM) CPU U7600 @ 1.20GHz
   SD host adapters
    SDA Standard Compilant SD Host controller
   Sound, video and game controllers
    High Definition Audio device
   Storage controllers
    Microsoft iSCSI Initiator
   System devices
    ACPI Fixed Feature Button
    ACPI Lid
    ACPI Power button
    ACPI Thermal zone
    ACPI Thermal zone
    DMA controller
    Fujitsu FUJ02E3 device driver
    High definition audio controller
    Intel(R) 82801 PCI bridge - 2448
    Intel(R) 82801 (ICH7 Family) PCI Express Root port - 27d0
    Intel(R) 82801 (ICH7 Family) PCI Express Root port - 27d2
    Intel(R) 82801 (ICH7 Family) SMBus controller - 27da
    Intel(R) 82801 (ICH7-M/U) LPC Interface controller - 27b9
    Microsoft ACPI compliant embedded controller
    Microsoft ACPI compliant system
    Microsoft ACPI composite battery
    Microsoft system management BIOS driver
    Mobile Intel(R) 945GM/GU/PM/GMS/940ML and Intel 945GT EXpress processor DRAM controller
    Numeric data procesor
    PCI bus
    Plug and Play Software device enumerator
    Programmable interrupt controller
    System CMOS real time clock
    System speaker 
    System timer
    UMBus enumerator
    UMBusRoot Bus enumerator
   Universal Serial Bus controllers
    AutenTec Inc AES2501
    Intel(R) 82801G (ICH7 Family) USB Universal Host controller - 27C8
    Intel(R) 82801G (ICH7 Family) USB Universal Host controller - 27C9
    Intel(R) 82801G (ICH7 Family) USB Universal Host controller - 27CA
    Intel(R) 82801G (ICH7 Family) USB Universal Host controller - 27CB
    Intel(R) 82801G (ICH7 Family) USBs Enhanced Host controller - 27CC
    USB Composite device
    USB Root hub  
    USB Root hub  
    USB Root hub  
    USB Root hub  
    USB Root hub  

```

The two hardware feature dumps look fairly similar to me, but don't have enough knowledge. Comments would be appreciated.

If this was my netbook I would have installed Ubuntu 11.04 on day one, but it is used by wife, her friends and children. I don't have a Vista install CD for Fujitsu and cannot easily get one as the Fujitsu&Siemens only carry spare parts for models sold in Europe. I may have to reinstall Vista if the Ubuntu install goes wrong or if the unused margins are still visible on the full install.  

Vaphell:
True, stretching 800x600 to fill the netbook display would cause distortion with circles coming out slightly elliptical, but the users of the netbook have not noticed this when watching action-filled overseas news and playing facebook. However, they immediately noticed and were disturbed by the unused margins when I ran Firefox from the Live Ubuntu CD!
 
    
Scruffyeagle:
The Fujitsu netbook has Phoenix BIOS. There are two options in video settings: Auto and Compensating, Auto is default. Tried the Compensating setting but this did not have any effect.


So, I need Ubuntu to stretch the image for the 4:3 resolutions.

A last resort would be to learn how to edit partitions on Vista, but...

Ken

---

### Post by JC Cheloven on 2011-09-10
Hi again Resander, the relevant part of your lspci output is

> 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

So you have an intel 945 intel graphics card. I did a little search, and from [this page]("http://hardware4linux.info/component/17142/") I found, it seems that your should be using a resolution of 1400x900 (which is of the type 16:10=1.6). The resolution that vista and ubuntu pick automatically, 1280x768, is = 1.666, which is close to 1.6 and should be the better option among the ones you report. The rest, 1024x768, 800x600 and 640x480 are all 4:3 =1.333, and thus not optimal for your display.

NOTE.- The link says we should use a command called "915resolution" to set the resolution. This command is nowadays deprecated, but don't worry, we should be able to get things done using some other method. 

So... if I have to answer your exact question (which if I at all understood is to set a resolution of 800x600 and stretch it to fill the whole screen), here you are (please copy-paste as every detail matters):

```
xrandr --output LVDS1 --mode 800x600
```then
```
xrandr --output LVDS1 --set 'scaling mode' 'Full'
```

OK, now you have your answer, you may even be happy with it, [SIZE="3"][COLOR="Red"]but[/COLOR][/SIZE] I don't think you actually have an apropriate solution to your problem. In normal circumstances, the only thing making sense is using the biggest resolution supported by both your card and screen. Then, if things are seen too small, we can adjust the font size, the scale of the monitor, or something else. If you want to dive into this, please post the output of ```
xrandr -q
```
Also, when you said > I also tried 1280x768 with larger fonts, but those that would be comfortably readable overflowed (vertically) the top window border. How do I fix this? What about other visual dialog elements like buttons? Would the text overflow these too or would the size of the visual element scale with the size of the font?
I don't figure out what you're getting. Could you please post a screenshot? (It's done pressing the PrintScreen key).
Thanks

---

### Post by no2498 on 2011-09-11
? does it do it on the desk top screen/laptop
or in fire fox if in fire fox drag the the top/bottom /left and right
to fit the screen

---

### Post by scruffyeagle on 2011-09-12
What you said about "overflowing" puzzles me, too. I'm wondering what method you used for setting font sizes...

The way I did it (which worked well) was to use System/Preferences/Appearance. Then, clicking on the "Fonts" tab, followed by changing/adjusting the various items on that page.

---

### Post by resander on 2011-09-14
Thanks for input...

The following commands indeed stretch the screen data horizontally to span the physical display:

xrandr --output LVDS1 --mode 800x600
xrandr --output LVDS1 --set 'scaling mode' 'Full'

which is what wife et al want. The horizontal distortion is not noticeable when watching (streaming) video, so this will do for the netbook.

However, I would like to learn more about changing fonts attributes for maximum resolution 1280x768 to get larger text. Here are the settings produced by xrandr - q:
```

screen 0: minimum 320 x 200, current 1280 x 768, max 4096x4096
LVDS1 connected 1280x768+0+0 (normal left inverted right x xaxis yaxis) 0mm x 0mm

  1280 x 768   59.9
  1024 x 768   60.0
   800 x 600   60.3   56.2
   640 x 480   59.9

VGA1 disconnected (normal left inverted right x xaxis yaxis)
TV1 disconnected  (normal left inverted right x xaxis yaxis)

```


For 1280x768 changed font sizes from Live CD Appearance under Personal for 11.04 to:  
```

   application font 22, 
   document font 22, 
   desktop font 22, 
   window title font 22, 
   fixed width 22

```

These sizes made menu and icon texts and the content text of qedit come out correspondingly larger. However, text sizes of Google search results, Youtube and OpenOffice Writer were not affected at all, i.e. came out as the text shown by 1280x768. See screenshots: googlesearch.png, youtube.png and openoff.png.

So google, youtube and openoffice appear to be ignoring the application font value. There are probably other applications that do this too. How to enlarge the font size for these? 

I also have some screen shots at 800x600 resolution for google search results and youtube: google800.png and youtube800.png. The texts are bigger for these and can be read without eye strain.

Some font sizes overflow the available space vertically at 1280x768 resolution. Screenshot overflow.png shows this. The descending parts of letter p in Appearance in the top bar are clipped, but this is only a very minor problem.

Comments welcome...

Ken

---

### Post by JC Cheloven on 2011-09-14
> **resander said:**
> However, I would like to learn more about changing fonts attributes for maximum resolution 1280x768 to get larger text.  Nice Ken, this is the spirit! :)

>  These sizes made menu and icon texts and the content text of qedit come out correspondingly larger. However, text sizes of Google search results, Youtube and OpenOffice Writer were not affected at all, i.e. came out as the text shown by 1280x768. See screenshots: googlesearch.png, youtube.png and openoff.png.

So google, youtube and openoffice appear to be ignoring the application font value. There are probably other applications that do this too. How to enlarge the font size for these? 

This should be pretty simple: press&hold the Ctrl key, and roll the wheel of the mouse: roll up enlarges, roll down shrinks. Also, in the case of firefox (when in youtube or whatever), key combinations Ctrl+ and Ctrl- will have the same effect.

> Some font sizes overflow the available space vertically at 1280x768 resolution. Screenshot overflow.png shows this.

I think you missed that image in your post :) anyway, some ideas:

1) If you'll be using 800x600 anyway, you can correct the distorsion by the following command 
```
xrand --output LVDS1 --scale 1.2x1
``` (try changing 1.2 for something nearby if you want; I'm too lazy right now to compute your exact figure, but it shouldn't be far from 1.2).

2) As an alternative way to see some text and elements larger (don't seem to work consistently with all of them), when you're at maximum resolution, please try
```
xrand --output LVDS1 --dpi 150
```
Then open some windows and see. You can try a number sligltly higher than 150 if you want. Something as 200 should be too much, I think.

Well, you always can ytpe "man xrandr" if you want to learn more about this command.

Finally, an experience to share with you: I've got a 'nettop', or whatever they call it (a small pc connected to your TV, to be used as multimedia center). I installed vanilla Ubuntu 10.04LTS on it, and to see things larger, changing font sizes and using the Ctrl-Wheel thing, was all I needed to get my "ubuntu based multimedia center" up and going. I think it should be the same for you and family. So try to see if you can keep it simple :)

Cheers
JC

---

### Post by resander on 2011-09-25
JC Cheloven, again many thanks! 

This time the missing screenshot overflow.png is attached. It shows the descenders clipped in the top bar. Not a problem if this is the only case.

I changed the font sizes to 22 in Appearance of Ubuntu 11.04 Live CD and noticed the following applications are fetching the application font size from the value (22) I gave: Banshee, Brasero, Disk Usage, Gparted, Login Control, Main Menu, Monitors, Movie Maker, Screen saver. I think most other applications would do too. However, Open Office did not, but offered an inbuilt function set-zoom?? (tried this about week ago and now the netbook is out of the house so may not remember correctly and cannot verify).

Ctrl+ and Ctrl- minus worked fine for youtube and google search results. Is this mechanism offered by Firefox or by the site (youtube, google search)? If the former, do other browsers offer this too?

Regards
Ken

---

### Post by resander on 2011-12-29
Recently I fetched Ubuntu 10.04.03 LTS and found the wifi was working and there were no unused margins for Live CD and full install. However, I still don't know how the screen will come out for a full install of 11.xx.

Ken

---

