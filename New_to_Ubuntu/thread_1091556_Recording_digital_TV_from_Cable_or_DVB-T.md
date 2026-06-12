---
title: "Recording digital TV from Cable or DVB-T"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by RichardCL on 2009-03-09
Hi Forum,

I'm looking to replace my almost useless DVD/HDD recorder with an older laptop that has HDMI output. The plan is to interface the PC direct to my network and take sound and video from my NAS.

All I need to now is a good way to record TV programs from cable or DVB-T to the network. Ideally, I'll use my desktop for the recording rather than the media centre PC.

Can anyone help me with the best route? I started to research mythbutu but just want to check whether there are any sensible alternatives. Which cards are compatible or have drivers?

Thanks in advance.


Richard

---

### Post by lovinglinux on 2009-03-09
I have recently released a media center extension for Firefox/Linux, which has an EPG with xmltv support, TV recorder with scheduler (including weekly series), playlist manager with tagging support and more stuff. This extension is a lightweight option for those machines which struggle with MythTv CPU requirements.

The only problem is that I don't know if it will work with your TV card, because the extension requires TVTime to change channels before each recording and I have tested it only with an analog TV card. Nevertheless, you can record from RF, AV input and SVHS input if TVTime works for you.

The extension also has an option to configure the destination folder for TV recordings, so if you setup a shared folder between your machine and the media center PC, you could use the extension on your desktop, but access the files from other computers on your network.

Please give it a try and tell what you think. 

Download and user guide are available at [http://fmc.isgreat.org/](http://fmc.isgreat.org/)

Please read the "Important Notes" and "Requirements" before installing the extension.

---

### Post by RichardCL on 2009-03-09
Thanks for the post. I just had a look at the website and the extension certainly looks nice. I'll have to give it a go at the weekend when I've more time to spare.

How to I find out the name of my TV card? I'll post it here.

I should have the CPU and database power for mythTV etc but I'm not sure I need all the setup and running hastle it seems to bring with it.

---

### Post by lovinglinux on 2009-03-09
> **RichardCL said:**
> Thanks for the post. I just had a look at the website and the extension certainly looks nice. I'll have to give it a go at the weekend when I've more time to spare.

How to I find out the name of my TV card? I'll post it here.

I should have the CPU and database power for mythTV etc but I'm not sure I need all the setup and running hastle it seems to bring with it.

You are welcome.

To get your card model run  

```
sudo lshw -C multimedia
```

MythTV is great. I have tried myself but I have to agree that it has too many features and options. That's why I wrote FoxMediaCenter. I wanted a simple way to record TV, to follow up TV schedules and to watch videos. Since Firefox is open almost all the time in my machine, making an extension for it was the best way to go. Now I'm sharing it with the community.;)

---

### Post by RichardCL on 2009-03-10
> **lovinglinux said:**
> You are welcome.

To get your card model run  

```
sudo lshw -C multimedia
```



```
       description: Multimedia controller
       product: SAA7134/SAA7135HL Video Broadcast Decoder
       vendor: Philips Semiconductors
       physical id: 3
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=saa7134 latency=64 maxlatency=32 mingnt=84 module=s
```


> **lovinglinux said:**
> 
MythTV is great. I have tried myself but I have to agree that it has too many features and options. That's why I wrote FoxMediaCenter. I wanted a simple way to record TV, to follow up TV schedules and to watch videos. Since Firefox is open almost all the time in my machine, making an extension for it was the best way to go. Now I'm sharing it with the community.;)

That's certainly great spirit. I wouldn't mind having enough knowlege of programming to have the simple way just to write the script!

---

### Post by lovinglinux on 2009-03-10
> **RichardCL said:**
> ```
       description: Multimedia controller
       product: SAA7134/SAA7135HL Video Broadcast Decoder
       vendor: Philips Semiconductors
       physical id: 3
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=saa7134 latency=64 maxlatency=32 mingnt=84 module=s
```!

Looks like we have similar cards. Does it already work with TVTime? If yes, all you have to do is configure the recorder settings in the extension. If haven't been able to use it with TVTime or any other program, then you will have to configure the driver. It would be interesting if you could get the card model. I don't know a command for this (it probably exists), but you could open the machine and see if it is printed on the card.

> **RichardCL said:**
> That's certainly great spirit. I wouldn't mind having enough knowlege of programming to have the simple way just to write the script!

It's not that complicated. You must have patience to research and to solve puzzles. I'm not a programmer and I started using Linux 6 months ago, so I had to read a lot, ask questions a lot and think a lot. But was well worthy. My code is probably not elegant, but is works :mrgreen:

---

### Post by RichardCL on 2009-03-10
> **lovinglinux said:**
> Looks like we have similar cards. Does it already work with TVTime? If yes, all you have to do is configure the recorder settings in the extension. If haven't been able to use it with TVTime or any other program, then you will have to configure the driver. It would be interesting if you could get the card model. I don't know a command for this (it probably exists), but you could open the machine and see if it is printed on the card.

Duh, I've been so into this Linux stuff that I'm looking for a command to tell me what card I have in my latop. The joke is that the card is sitting in front of me in my laptop.

Pulling it out and reading the bottom gives the following info.

Creatix
TV-tuner 7134
Rev. CTX921_V2 DVB-T/TV/FM
P/N 40012547
DV in: 3.3V 350mA
5v 300mA


There you go! Amazing what one can do when one forgets to use the computer.

---

### Post by lovinglinux on 2009-03-10
> **RichardCL said:**
> Duh, I've been so into this Linux stuff that I'm looking for a command to tell me what card I have in my latop. The joke is that the card is sitting in front of me in my laptop.

Pulling it out and reading the bottom gives the following info.

Creatix
TV-tuner 7134
Rev. CTX921_V2 DVB-T/TV/FM
P/N 40012547
DV in: 3.3V 350mA
5v 300mA


There you go! Amazing what one can do when one forgets to use the computer.

Definitively not the same as mine. I forgot that your card is DVB-T while mine is analog. Anyways, can you watch TV right now? If yes, which program do you use? Can you watch TV with TVTime? 

Unfortunately, I know nothing about digital cards, because there is no DTT in my city yet and I don't have a digital card, but if you can watch it with TVTime is a good start.

---

### Post by lovinglinux on 2009-03-10
Is this your card?

[http://www.creatix.com/produkte/multimedia/datenblatt/CTX921_V2_DVBT%20neutral.pdf](http://www.creatix.com/produkte/multimedia/datenblatt/CTX921_V2_DVBT%20neutral.pdf)

I guess it has both digital and analog.

---

### Post by RichardCL on 2009-03-12
Just installed TVtime and tried with the card. I seem to be recognising the card but no channels are found. I need to play around some more.

---

