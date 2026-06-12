---
title: "HTPC hardware advice"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by peanutgallery on 2011-04-13
Hi Guys,

I'm new to this LINUX world.  I use Windows at work, I have a macbook and I would like to build a little HTPC for the TV connecting with an HDMI cable.  I'd like to replace my Western Digital Media Player with something where I can do the following.

Main Use will be.

1) Media Player - VLC 
2) Skype - Video Calling
3) Surfing the Web - Firefox

That's about it. 

My question/confusion is Ubuntu/Xubuntu/Lubuntu...which one do I use if I buy this below:

**ASUS AT5IONT-I Intel Atom D525 (1.8GHz, dual-core) BGA559 Intel NM10 Mini ITX Motherboard/CPU Combo**

It's more important that Skype (video chat) work? if so could you also recommend a working webcam please?

If you think an AMD chip would work better could you please advise as well.

One last thing.  32 bit vs 64 bit?

Thanks and I'm sorry for all the questions but searching for the answers just got me more confused with the terminal talk.  I can figure that out later if I have the right hardware first.  I'd hate to have to buy windows.

---

### Post by K_45 on 2011-04-13
Atom is uselessly slow. I would build:

CPU: AMD Athlon x4 645

RAM: 4GB DDR3 Kingston Value Ram 1333MHz

MOBO: Asrock 890GM Pro 3

GPU: Onboard

SOUND: Onboard

HDD: Seagate Barracuda 7200.12 1TB (or bigger, your choice), or an SSD if you will stream the files from a NAS and/or server.

PSU: Antec Earthwatts 380w

Pick a mATX case to save space.

---

### Post by theller on 2011-04-18
I am using a [Jetway MiniTop]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856107072") that has an Atom D525, with 2x2g Gskill and at first I had put in WD scorpio black 500g, then I made that an external and put in a Kingston SSDnowV 30g. Skype, Firefox and VLC all work great. Totem movie player even uses many of the buttons on the remote that came with the computer. HDMI output looks spectacular.

---

### Post by Paqman on 2011-04-18
Your spec depends on what you'll be doing with it. If you'll be outputting HD video I suggest getting a board with an integrated Nvidia chip and using software for playback that supports VDPAU (eg: mplayer, XBMC). 1GB of RAM will be plenty.

You don't want to be using the CPU for rendering video, they're not very good at it and you'd need a much bigger, more expensive and hotter CPU than you should. You don't want to run an HTPC hot, as you'll get lots of fan noise. A low power CPU and an Nvidia GPU using VDPAU is the way to go IMO.

I use a Jetway JNC-62K mini-ITX board. It's got an onboard Nvidia 8200 and will stream video at 720p smooth as butter. I've not tried it at 1080p as I don't have a telly that flash.

---

### Post by Hovik on 2011-05-20
Hi Peanut, 
[LEFT] I just bought the same Asus mobo yesterday for my htpc upgrade project. I  think the board is great and disagree with K_45 that it's uselessly  slow, especially given the list of tasks you have lined up to use it  for.  I could be wrong but it's my impression that most people who have  HTPC's don't use them for gaming or video rendering... i am sure this  board is more than capable of doing what you want it to quite quickly.

I put together the system in a [Silverstone Sugo SG05]("http://www.silverstonetek.com/products/p_contents.php?pno=SG05&area=") case last night. I had ordered 4GB (2GB x 2) of Mushkin DDR3 SODIMM from newegg but that probably won't arrive til early next week and I am hardly that patient, so I raped a 2GB Kingston chip from my wife's VAIO to test in my HTPC. I also grabbed a 160GB 2.5" SATA HD from a laptop in my boneyard to use for now. I'd like to get my hands on a 30-60GB SSD but am willing to wait for that. So anyway I threw in a usb flash drive bootable to Ubuntu 10.04LTS and installed. The system runs very fast in my opinion, it's exactly what I had hoped for. I am sure adding another 2GB of RAM (though only 3GB of the 4GB installed will likely be usable) when it arrives won't hurt performance either.

I too am considering which webcam to use. while browsing at Fry's yesterday I came across the Creative Live! Cam 1080p which claimed on the box to have linux drivers (i then noticed all creative's webcams on the shelf have linux drivers) at $90 it seems a little steep but I'll watch edealinfo.com for a sale... The important thing to me is the audio, if I am Skyping with someone and they cant hear my voice because I am 14' from the mic on my couch then that probably won't work for me. If anyone can suggest a cam w/ linux drivers that DOES have good mic range please speak up...

Good Luck!
[/LEFT]

---

### Post by bonfire89 on 2011-05-25
I'm looking for some information on this myself and would appreciate some more input so I'm bumping this. hehe

I guess the key success factor for me would be being able to play those big mkv files.. big as in 10gb+ or so.

---

