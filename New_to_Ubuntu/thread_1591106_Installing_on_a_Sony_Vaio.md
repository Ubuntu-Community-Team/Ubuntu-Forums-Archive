---
title: "Installing on a Sony Vaio"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by comeback-of-the-year on 2010-10-08
More specifically a PCG-61511M. 

Could someone show me how to check compatibility with ubuntu? 

I've had it on several older desktops before which had windows on them for years, but this is the first time putting it on a brand new laptop. 

The plan is to dual boot along side windows 7 :popcorn:

---

### Post by lbrty on 2010-10-08
Download Ubuntu by going [here]("http://www.ubuntu.com/desktop/get-ubuntu/download")
Burn the .iso to a CD or make a bootable USB flash drive
Insert the CD/USB flash drive in the machine
Reboot the computer
Go into BIOS and change the boot order to boot from CD drive or the USB flash drive
Click Try Ubuntu
When you get to the Ubuntu desktop, goto System>Administration>System Testing and follow the prompts

---

### Post by comeback-of-the-year on 2010-10-08
> **lbrty said:**
> Download Ubuntu by going [here]("http://www.ubuntu.com/desktop/get-ubuntu/download")
Burn the .iso to a CD or make a bootable USB flash drive
Insert the CD/USB flash drive in the machine
Reboot the computer
Go into BIOS and change the boot order to boot from CD drive or the USB flash drive
Click Try Ubuntu
When you get to the Ubuntu desktop, goto System>Administration>System Testing and follow the prompts

Thanks for the reply

I can't seem to get the sound working. It is picking up my sound driver, and shows the choice for HDMI output, but nothings coming through the speakers on any settings. 

Also, I couldn't use my mousepad? I think its because i booted the live cd with an external mouse connected. Will this go away with a full install or do i need to install the drivers for the mousepad after installation? :(

---

### Post by MisterGaribaldi on 2010-10-08
A lot of this depends on what Sony did in hardware.

Sony laptops actually have been pretty well supported in the past (though it's been a while since I've dealt with putting Linux on a Sony). Maybe Sony's decided to go with some really obscure touchpad and sound controller. That's just odd.

---

### Post by Quackers on 2010-10-09
Everything but the tv card works on my Vaio (and I'm working on the tv card) :-)

---

### Post by coffeecat on 2010-10-09
> **Quackers said:**
> Everything but the tv card works on my Vaio (and I'm working on the tv card) :-)

Ditto here on my VGN-NS20S except I don't have a TV card. :p One minor niggle in Maverick which will probably go away. The Fn key combinations have worked since Jaunty (9.04), but in Maverick the Fn+F5 and Fn+F6 for brightness don't with the Maverick kernel. But they do using the Lucid kernel in Maverick so it must be a kernel bug which might get fixed. I'll try to get around to filing a bug report.

@comeback-of-the-year, next time you reboot into the live session try the Fn keys. Some people report problems with some Vaio models. 

> **comeback-of-the-year said:**
> I can't seem to get the sound working. It is picking up my sound driver, and shows the choice for HDMI output, but nothings coming through the speakers on any settings. 

Double-check it's not muted. Click on the sound icon on the upper panel towards the right.

> **comeback-of-the-year said:**
>  Also, I couldn't use my mousepad? I think its because i booted the live cd with an external mouse connected. Will this go away with a full install or do i need to install the drivers for the mousepad after installation? :(

I've not noticed this as a problem. Try booting without the mouse plugged in. Also, have a look in System > Preferences > Mouse. The driver is pre-installed so there is nothing else to install. If the problem persists I don't know what you can do.

---

### Post by comeback-of-the-year on 2010-10-09
> **coffeecat said:**
> 

@comeback-of-the-year, next time you reboot into the live session try the Fn keys. Some people report problems with some Vaio models. 



All the FN keys work fine apart from brightness, which i can live without.

> **coffeecat said:**
> 
Double-check it's not muted. Click on the sound icon on the upper panel towards the right.


Nope, all volumes are turned fully up. In "sound preferences"  I have a choice of two hardware which are 
"analogue stereo"
"digital stereo (hdmi)"

Yet neither seem to work.


> **coffeecat said:**
> 
I've not noticed this as a problem. Try booting without the mouse plugged in. Also, have a look in System > Preferences > Mouse. The driver is pre-installed so there is nothing else to install. If the problem persists I don't know what you can do.

Booted without the external mouse but the mouse-pad still wouldn't work. Then i stumpled upon this old thread :

[http://ubuntuforums.org/showthread.php?t=1565548](http://ubuntuforums.org/showthread.php?t=1565548)

Followed their instructions for the grub update to the letter, and now it works great. 

(I did a full install just after my last post, problems are made to be solved right :P)

Now, onto the sound..

---

### Post by comeback-of-the-year on 2010-10-10
Sorry for the double post but I thought this would save making a new thread.

I'm still having problems getting the sound to work, after trying several different ideas in older threads on the forum, and several google results, i decided to try using the HDMI output on the laptop. 

It worked immediatly duplicating the screen onto the hdtv, so i changed the sound prefrences from "analogue output" to "HDMI output" and the sound worked straight away through the speakers of the TV. 

Does anyone know why it wont work through the speakers on the laptop??

---

### Post by sandyd on 2010-10-10
> **comeback-of-the-year said:**
> Sorry for the double post but I thought this would save making a new thread.

I'm still having problems getting the sound to work, after trying several different ideas in older threads on the forum, and several google results, i decided to try using the HDMI output on the laptop. 

It worked immediatly duplicating the screen onto the hdtv, so i changed the sound prefrences from "analogue output" to "HDMI output" and the sound worked straight away through the speakers of the TV. 

Does anyone know why it wont work through the speakers on the laptop??
I think you need to set one of the stacks.
post output of
```

sudo lspci | grep Audio
```

---

### Post by comeback-of-the-year on 2010-10-10
> **sandyd said:**
> I think you need to set one of the stacks.
post output of
```

lspci | grep Multimedia
```

Nothing happens, it just jumps down a line and waits for next input, like this: 

```

:~$ lspci | grep Multimedia
:~$ 


```

How do I set a stack?

---

### Post by sandyd on 2010-10-10
> **comeback-of-the-year said:**
> Nothing happens, it just jumps down a line and waits for next input, like this: 

```

:~$ lspci | grep Multimedia
:~$ 


```How do I set a stack?
oops. my bad. fixed.

---

### Post by comeback-of-the-year on 2010-10-10
Output:

```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
01:00.1 Audio device: ATI Technologies Inc RV710/730
```

---

### Post by sandyd on 2010-10-10
> **comeback-of-the-year said:**
> Output:

```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
01:00.1 Audio device: ATI Technologies Inc RV710/730
```
[http://ubuntuforums.org/showpost.php?p=884287&postcount=6](http://ubuntuforums.org/showpost.php?p=884287&postcount=6)

and your using snd_hda_intel I believe. so one of these might work, but ill have to leave it to someone more knowledgable
> 
 780 
 781           Model name    Description
 782           ----------    -----------
 783         ALC880
 784           3stack        3-jack in back and a headphone out
 785           3stack-digout 3-jack in back, a HP out and a SPDIF out
 786           5stack        5-jack in back, 2-jack in front
 787           5stack-digout 5-jack in back, 2-jack in front, a SPDIF out
 788           6stack        6-jack in back, 2-jack in front
 789           6stack-digout 6-jack with a SPDIF out
 790           w810          3-jack
 791           z71v          3-jack (HP shared SPDIF)
 792           asus          3-jack (ASUS Mobo)
 793           asus-w1v      ASUS W1V
 794           asus-dig      ASUS with SPDIF out
 795           asus-dig2     ASUS with SPDIF out (using GPIO2)
 796           uniwill       3-jack
 797           fujitsu       Fujitsu Laptops (Pi1536)
 798           F1734         2-jack
 799           lg            LG laptop (m1 express dual)
 800           lg-lw         LG LW20/LW25 laptop
 801           tcl           TCL S700
 802           clevo         Clevo laptops (m520G, m665n)
 803           medion        Medion Rim 2150
 804           test          for testing/debugging purpose, almost all controls can be
 805                         adjusted.  Appearing only when compiled with
 806                         $CONFIG_SND_DEBUG=y
 807           auto          auto-config reading BIOS (default)
 808 
 809         ALC260
 810           hp            HP machines
 811           hp-3013       HP machines (3013-variant)
 812           hp-dc7600     HP DC7600
 813           fujitsu       Fujitsu S7020
 814           acer          Acer TravelMate
 815           will          Will laptops (PB V7900)
 816           replacer      Replacer 672V
 817           basic         fixed pin assignment (old default model)
 818           test          for testing/debugging purpose, almost all controls can
 819                         adjusted.  Appearing only when compiled with
 820                         $CONFIG_SND_DEBUG=y
 821           auto          auto-config reading BIOS (default)
 822 
 823         ALC262
 824           fujitsu       Fujitsu Laptop
 825           hp-bpc        HP xw4400/6400/8400/9400 laptops
 826           hp-bpc-d7000  HP BPC D7000
 827           hp-tc-t5735   HP Thin Client T5735
 828           hp-rp5700     HP RP5700
 829           benq          Benq ED8
 830           benq-t31      Benq T31
 831           hippo         Hippo (ATI) with jack detection, Sony UX-90s
 832           hippo_1       Hippo (Benq) with jack detection
 833           sony-assamd   Sony ASSAMD
 834           toshiba-s06   Toshiba S06
 835           toshiba-rx1   Toshiba RX1
 836           ultra         Samsung Q1 Ultra Vista model
 837           lenovo-3000   Lenovo 3000 y410
 838           nec           NEC Versa S9100
 839           basic         fixed pin assignment w/o SPDIF
 840           auto          auto-config reading BIOS (default)
 841 
 842         ALC267/268
 843           quanta-il1    Quanta IL1 mini-notebook
 844           3stack        3-stack model
 845           toshiba       Toshiba A205
 846           acer          Acer laptops
 847           acer-aspire   Acer Aspire One
 848           dell          Dell OEM laptops (Vostro 1200)
 849           zepto         Zepto laptops
 850           test          for testing/debugging purpose, almost all controls can
 851                         adjusted.  Appearing only when compiled with
 852                         $CONFIG_SND_DEBUG=y
 853           auto          auto-config reading BIOS (default)
 854 
 855         ALC269
 856           basic         Basic preset
 857           quanta        Quanta FL1
 858           eeepc-p703    ASUS Eeepc P703 P900A
 859           eeepc-p901    ASUS Eeepc P901 S101
 860 
 861         ALC662/663
 862           3stack-dig    3-stack (2-channel) with SPDIF
 863           3stack-6ch     3-stack (6-channel)
 864           3stack-6ch-dig 3-stack (6-channel) with SPDIF
 865           6stack-dig     6-stack with SPDIF
 866           lenovo-101e    Lenovo laptop
 867           eeepc-p701    ASUS Eeepc P701
 868           eeepc-ep20    ASUS Eeepc EP20
 869           ecs           ECS/Foxconn mobo
 870           m51va         ASUS M51VA
 871           g71v          ASUS G71V
 872           h13           ASUS H13
 873           g50v          ASUS G50V
 874           asus-mode1    ASUS
 875           asus-mode2    ASUS
 876           asus-mode3    ASUS
 877           asus-mode4    ASUS
 878           asus-mode5    ASUS
 879           asus-mode6    ASUS
 880           auto          auto-config reading BIOS (default)
 881 
 882         ALC882/885
 883           3stack-dig    3-jack with SPDIF I/O
 884           6stack-dig    6-jack digital with SPDIF I/O
 885           arima         Arima W820Di1
 886           targa         Targa T8, MSI-1049 T8
 887           asus-a7j      ASUS A7J
 888           asus-a7m      ASUS A7M
 889           macpro        MacPro support
 890           mbp3          Macbook Pro rev3
 891           imac24        iMac 24'' with jack detection
 892           w2jc          ASUS W2JC
 893           auto          auto-config reading BIOS (default)
 894 
 895         ALC883/888
 896           3stack-dig    3-jack with SPDIF I/O
 897           6stack-dig    6-jack digital with SPDIF I/O
 898           3stack-6ch    3-jack 6-channel
 899           3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
 900           6stack-dig-demo  6-jack digital for Intel demo board
 901           acer          Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
 902           acer-aspire   Acer Aspire 9810
 903           medion        Medion Laptops
 904           medion-md2    Medion MD2
 905           targa-dig     Targa/MSI
 906           targa-2ch-dig Targs/MSI with 2-channel
 907           laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
 908           lenovo-101e   Lenovo 101E
 909           lenovo-nb0763 Lenovo NB0763
 910           lenovo-ms7195-dig Lenovo MS7195
 911           lenovo-sky    Lenovo Sky
 912           haier-w66     Haier W66
 913           3stack-hp     HP machines with 3stack (Lucknow, Samba boards)
 914           6stack-dell   Dell machines with 6stack (Inspiron 530)
 915           mitac         Mitac 8252D
 916           clevo-m720    Clevo M720 laptop series
 917           fujitsu-pi2515 Fujitsu AMILO Pi2515
 918           3stack-6ch-intel Intel DG33* boards
 919           auto          auto-config reading BIOS (default)
 920 
 921         ALC861/660
 922           3stack        3-jack
 923           3stack-dig    3-jack with SPDIF I/O
 924           6stack-dig    6-jack with SPDIF I/O
 925           3stack-660    3-jack (for ALC660)
 926           uniwill-m31   Uniwill M31 laptop
 927           toshiba       Toshiba laptop support
 928           asus          Asus laptop support
 929           asus-laptop   ASUS F2/F3 laptops
 930           auto          auto-config reading BIOS (default)
 931 
 932         ALC861VD/660VD
 933           3stack        3-jack
 934           3stack-dig    3-jack with SPDIF OUT
 935           6stack-dig    6-jack with SPDIF OUT
 936           3stack-660    3-jack (for ALC660VD)
 937           3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
 938           lenovo        Lenovo 3000 C200
 939           dallas        Dallas laptops
 940           hp            HP TX1000
 941           auto          auto-config reading BIOS (default)
 942 
 943         CMI9880
 944           minimal       3-jack in back
 945           min_fp        3-jack in back, 2-jack in front
 946           full          6-jack in back, 2-jack in front
 947           full_dig      6-jack in back, 2-jack in front, SPDIF I/O
 948           allout        5-jack in back, 2-jack in front, SPDIF out
 949           auto          auto-config reading BIOS (default)
 950 
 951         AD1882 / AD1882A
 952           3stack        3-stack mode (default)
 953           6stack        6-stack mode
 954 
 955         AD1884A / AD1883 / AD1984A / AD1984B
 956           desktop       3-stack desktop (default)
 957           laptop        laptop with HP jack sensing
 958           mobile        mobile devices with HP jack sensing
 959           thinkpad      Lenovo Thinkpad X300
 960 
 961         AD1884
 962           N/A
 963 
 964         AD1981
 965           basic         3-jack (default)
 966           hp            HP nx6320
 967           thinkpad      Lenovo Thinkpad T60/X60/Z60
 968           toshiba       Toshiba U205
 969 
 970         AD1983
 971           N/A
 972 
 973         AD1984
 974           basic         default configuration
 975           thinkpad      Lenovo Thinkpad T61/X61
 976           dell          Dell T3400
 977 
 978         AD1986A
 979           6stack        6-jack, separate surrounds (default)
 980           3stack        3-stack, shared surrounds
 981           laptop        2-channel only (FSC V2060, Samsung M50)
 982           laptop-eapd   2-channel with EAPD (Samsung R65, ASUS A6J)
 983           laptop-automute 2-channel with EAPD and HP-automute (Lenovo N100)
 984           ultra         2-channel with EAPD (Samsung Ultra tablet PC)
 985 
 986         AD1988/AD1988B/AD1989A/AD1989B
 987           6stack        6-jack
 988           6stack-dig    ditto with SPDIF
 989           3stack        3-jack
 990           3stack-dig    ditto with SPDIF
 991           laptop        3-jack with hp-jack automute
 992           laptop-dig    ditto with SPDIF
 993           auto          auto-config reading BIOS (default)
 994         
 995         Conexant 5045
 996           laptop-hpsense    Laptop with HP sense (old model laptop)
 997           laptop-micsense   Laptop with Mic sense (old model fujitsu)
 998           laptop-hpmicsense Laptop with HP and Mic senses
 999           benq          Benq R55E
1000           test          for testing/debugging purpose, almost all controls
1001                         can be adjusted.  Appearing only when compiled with
1002                         $CONFIG_SND_DEBUG=y
1003 
1004         Conexant 5047
1005           laptop        Basic Laptop config 
1006           laptop-hp     Laptop config for some HP models (subdevice 30A5)
1007           laptop-eapd   Laptop config with EAPD support
1008           test          for testing/debugging purpose, almost all controls
1009                         can be adjusted.  Appearing only when compiled with
1010                         $CONFIG_SND_DEBUG=y
1011 
1012         Conexant 5051
1013           laptop        Basic Laptop config (default)
1014           hp            HP Spartan laptop
1015 
1016         STAC9200
1017           ref           Reference board
1018           dell-d21      Dell (unknown)
1019           dell-d22      Dell (unknown)
1020           dell-d23      Dell (unknown)
1021           dell-m21      Dell Inspiron 630m, Dell Inspiron 640m
1022           dell-m22      Dell Latitude D620, Dell Latitude D820
1023           dell-m23      Dell XPS M1710, Dell Precision M90
1024           dell-m24      Dell Latitude 120L
1025           dell-m25      Dell Inspiron E1505n
1026           dell-m26      Dell Inspiron 1501
1027           dell-m27      Dell Inspiron E1705/9400
1028           gateway       Gateway laptops with EAPD control
1029           panasonic     Panasonic CF-74
1030 
1031         STAC9205/9254
1032           ref           Reference board
1033           dell-m42      Dell (unknown)
1034           dell-m43      Dell Precision
1035           dell-m44      Dell Inspiron
1036 
1037         STAC9220/9221
1038           ref           Reference board
1039           3stack        D945 3stack
1040           5stack        D945 5stack + SPDIF
1041           intel-mac-v1  Intel Mac Type 1
1042           intel-mac-v2  Intel Mac Type 2
1043           intel-mac-v3  Intel Mac Type 3
1044           intel-mac-v4  Intel Mac Type 4
1045           intel-mac-v5  Intel Mac Type 5
1046           intel-mac-auto Intel Mac (detect type according to subsystem id)
1047           macmini       Intel Mac Mini (equivalent with type 3)
1048           macbook       Intel Mac Book (eq. type 5)
1049           macbook-pro-v1 Intel Mac Book Pro 1st generation (eq. type 3)
1050           macbook-pro   Intel Mac Book Pro 2nd generation (eq. type 3)
1051           imac-intel    Intel iMac (eq. type 2)
1052           imac-intel-20 Intel iMac (newer version) (eq. type 3)
1053           dell-d81      Dell (unknown)
1054           dell-d82      Dell (unknown)
1055           dell-m81      Dell (unknown)
1056           dell-m82      Dell XPS M1210
1057 
1058         STAC9202/9250/9251
1059           ref           Reference board, base config
1060           m2-2          Some Gateway MX series laptops
1061           m6            Some Gateway NX series laptops
1062           pa6           Gateway NX860 series
1063 
1064         STAC9227/9228/9229/927x
1065           ref           Reference board
1066           3stack        D965 3stack
1067           5stack        D965 5stack + SPDIF
1068           dell-3stack   Dell Dimension E520
1069           dell-bios     Fixes with Dell BIOS setup
1070 
1071         STAC92HD71B*
1072           ref           Reference board
1073           dell-m4-1     Dell desktops
1074           dell-m4-2     Dell desktops
1075 
1076         STAC92HD73*
1077           ref           Reference board
1078           dell-m6       Dell desktops


---

### Post by comeback-of-the-year on 2010-10-11
Thanks for the list, 

I found out that mine is          ALC269. I've tired all the ones in your post but still cant seem to get it working. 

Everytime I try one, I restart, use alsamixer to make sure nothing is muted, and still no success. 

Just to make sure i'm going about this the right way, I use 

```
options snd-hda-intel model=_______
```and put it at the end of the alsa-base file. 

In your list, am i supposed to be trying one word at a time like 

```
options snd-hda-intel model=basic
```or a line like

```
options snd-hda-intel model=basic Basic preset
```That may be a really stupid question but it's one of those things I'd like to rule out :)

Edit: 

Also, someone told me to make sure i have disabled external applications using the mixer, but i cant find out how to do it!

---

### Post by comeback-of-the-year on 2010-10-17
After a few painful, coffee fueled, stressful days I have finally got everything working on my Vaio. 

After trying everything to fix the audio, I gave up. So as a last resort, I backed up all my data and upgraded to 10.10, and everything worked "out of the box".

Finally. :popcorn: (although the boot up sound did scare me half to death)

Thanks to everyone that helped out in this thread, I owe you all a beer :)

---

