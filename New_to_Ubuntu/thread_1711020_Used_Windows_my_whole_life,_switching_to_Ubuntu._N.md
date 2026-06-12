---
title: "Used Windows my whole life, switching to Ubuntu. Need help."
date: 2011-03-20
forum: New to Ubuntu
---

### Post by koolaidz83095 on 2011-03-20
Hi everyone, 

I am a long-time Windows user, I've actually used XP my whole life. I'm building a new PC and I didn't have the cash to buy Windows 7 so I decided to try out a Linux distro for the first time. Keeping in mind that I have NEVER used any Linux OS before, please help me out with some of my questions. 

1.) I have a Linksys WRT54GS v6 router that I plan to use to connect the new PC to the internet; will I have any troubles doing so? Is there a chance that my router might not be compatible with Ubuntu 10.10?

2.) I'll be using a Logitech EX100 wireless keyboard and mouse for my PC and I have the same question as before; will it be compatible with Ubuntu 10.10?

3.) Is it anymore difficult to install drivers and codecs in Ubuntu compared to Windows?

4.) Is it true that Ubuntu only works with a VGA out? I hope not because my monitor (which is actually a small HDTV) only has HDMI and DVI inputs. 

5.) What is this forum's advice when it comes to making the switch from Windows to Linux? Meaning, is there anything that is significantly different that I'll have to get used to? This question is kinda vague but hopefully someone will get what I mean.

That's all my questions for now but I'm sure I will have more later. Thanks in advanced for any help and sorry for being a Linux n00b.

---

### Post by abyrne on 2011-03-20
Welcome to Ubuntu Forums!

First off, can I request that a mod move this thread to Absolute Beginner Talk.

> 1.) I have a Linksys WRT54GS v6 router that I plan to use to connect the new PC to the internet; will I have any troubles doing so? Is there a chance that my router might not be compatible with Ubuntu 10.10?
The router is not the thing you should be worrying about. It's the wireless/Ethernet card.

> 2.) I'll be using a Logitech EX100 wireless keyboard and mouse for my PC and I have the same question as before; will it be compatible with Ubuntu 10.10?
I'm pretty sure it does.

> 3.) Is it anymore difficult to install drivers and codecs in Ubuntu compared to Windows?
Drivers: It's actually easier. If their not already installed out of the box, then they should be picked up by Ubuntu's proprietary hardware detector.
Codecs: It depends on which ones you are talking about. Flash, MP3, MPEG, and other popular codecs have Linux packages available.

> 4.) Is it true that Ubuntu only works with a VGA out? I hope not because my monitor (which is actually a small HDTV) only has HDMI and DVI inputs. 
I think it depends on your video card.

> 5.) What is this forum's advice when it comes to making the switch from Windows to Linux? Meaning, is there anything that is significantly different that I'll have to get used to? This question is kinda vague but hopefully someone will get what I mean.
Read [this]("https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows"). It should hopefully answer most of your questions. If not, the forums are always here.

> sorry for being a Linux n00b.
Don't be sorry. We all have to start somewhere.

---

### Post by koolaidz83095 on 2011-03-20
> **abyrne said:**
> The router is not the thing you should be worrying about. It's the wireless/Ethernet card.
I am also kind of a networking n00b as well. When it comes to software and hardware, I'm fine but networking...I have no clue:confused:. Could you please explain more? Or if you don't want to explain, could you just say if I'd be okay or not using the router I have? I have a verizon fios modem if that helps. 
 
> I think it depends on your video card.Gonna use a GTS450, so do you think that would be okay to use HDMI as my output?

> Read [this]("https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows"). It should hopefully answer most of your questions. If not, the forums are always here.Thanks, this is what I was looking for.

---

### Post by abyrne on 2011-03-20
I assume your building a desktop, right? In that case, your desktop is probably connected to your router through an ethernet cable (the heads on ethernet cables look like over-sized phone lines). In that case, all networking is handled by your network card, which is either built-in to your motherboard or added in as a PCI card. The network card passes information to your router through the ethernet cable. From there, router to modem, modem to FiOS, FiOS to the Internet.

Ubuntu works with almost all Ethernet network cards, so it should also work with your router out of the box.

As for your video card, yes. The HDMI output should work fine for video. I have heard of problems when sending audio through HDMI, though. But I think that issue was fixed in a software update. It should be noted that the Nvidia driver is proprietary, and it probably won't work out of the box. Ubuntu's proprietary driver detector should pop up with the correct driver though.

---

### Post by koolaidz83095 on 2011-03-20
I'll be using the RJ-45 LAN port on my motherboard so I won't have to worry about network cards. Do you still think I'll be fine using my Linksys router though? It doesn't work on Windows without installing the software it comes with so I'm afraid I might have to install software for the router to work. Problem is, Linksys only makes software for my specific router for Windows and Macs only.

---

### Post by abyrne on 2011-03-20
That software that Linksys had you install is only required to set up the router. Actually, you don't really even need the software for that purpose, as routers often have a web-based setup interface.

If you just want to connect to the router, Ubuntu should work with it out of the box.

---

### Post by tordeu on 2011-03-20
[abyrne]("http://ubuntuforums.org/member.php?u=777742") already answered your questions, but I just wanted to add something:

> **koolaidz83095 said:**
> 
2.) I'll be using a Logitech EX100 wireless keyboard and mouse for my PC and I have the same question as before; will it be compatible with Ubuntu 10.10?


Normally, keyboard and mouse should not make much problems. Sometimes with Linux, newer hardware is more problematic, because hardware vendors often do not offer drivers for Linux, so "the community" has to provide them, which takes some time.

While I do not have the EX100, I do have a Logitech Keyboard (K800) and a Logitech mouse (MX Revolution) and the K800 is a pretty new model. Both devices work great with Ubuntu.
The only problem is, that Logitech (as far as I know) still does not officially support Linux, so there is no official tool to configure various mouse keys, although there is a Linux alternative (btnx). But this is probably not an issue for the EX100. 

> **koolaidz83095 said:**
> 
 4.) Is it true that Ubuntu only works with a VGA out? I hope not because my monitor (which is actually a small HDTV) only has HDMI and DVI inputs. 

As [abyrne]("http://ubuntuforums.org/member.php?u=777742") said, it depends on your graphics card. But in general, it should work. There are just a few cards where I encountered some problems with. The GTS450 should work. NVidia offers pretty good linux drivers.

> **koolaidz83095 said:**
> 
  5.) What is this forum's advice when it comes to making the switch from Windows to Linux? Meaning, is there anything that is significantly different that I'll have to get used to? This question is kinda vague but hopefully someone will get what I mean.


Read the link provided by abyrne. You should not be afraid of just trying. There are a things you need to get used to and sometimes people that switch from Windows from Linux are overwhelmed, because there seem to be so many different things. But once you know where to put your files and how the names for the programs are you will use to listen to music or watch videos etc. you will get more comfortable.

---

### Post by koolaidz83095 on 2011-03-20
> **abyrne said:**
> That software that Linksys had you install is  only required to set up the router. Actually, you don't really even need  the software for that purpose, as routers often have a web-based setup  interface.

If you just want to connect to the router, Ubuntu should work with it out of the box.

Yeah, that is what happens on Windows. The router is detected and my computer will connect to the router but it won't let me actually decide what network to connect to without the software. 

Does Ubuntu connect to a network automatically once it is connected to a router? Like, will Ubuntu detect my router and then ask me for my modem's WEP key?
> **tordeu said:**
> there is no official tool to configure various  mouse keys, although there is a Linux alternative (btnx). But this is  probably not an issue for the EX100
The mouse included with the EX100 only has left and right click along with the scroll wheel so I think I will be fine.

---

### Post by abyrne on 2011-03-20
WEP keys are only used in wireless situations. Also, modems do not use WEP keys at all. If I'm understanding your situation correctly, once you're connected to the router (which is already connected to the modem), your're connected to the Internet.

---

### Post by tordeu on 2011-03-20
> **koolaidz83095 said:**
> The mouse included with the EX100 only has left and right click along with the scroll wheel so I think I will be fine.

I know, I just wanted to you assure you that hardware compatibility in linux is not such a big issue anymore (in most cases) as it once was. It's still not a bad idea to check the compatibility, but a lot of things work right out of the box (even my wireless gamepad worked out of the box, without installing a driver).
Most hardware compatibility problems I encountered are from new stuff, especially when it is not something commong like a mouse or a graphics card. Webcams or scanners are probably more problematic.

---

### Post by koolaidz83095 on 2011-03-20
> WEP keys are only used in wireless situations. Also, modems do not use  WEP keys at all. If I'm understanding your situation correctly, once  you're connected to the router (which is already connected to the  modem), your're connected to the Internet. 	
The modem Verizon gave me is also a router so whenever I connect something wirelessly to it, for example a Laptop, I have to use the WEP number on my modem/router.

The router I'm using for my new PC is an old, spare router I kept from when I use to have Comcast internet which included just a modem. I think I'll have to reconfigure the connection on the router to work with my current modem/router from Verizon.

---

### Post by abyrne on 2011-03-20
> **koolaidz83095 said:**
> The modem Verizon gave me is also a router so whenever I connect something wirelessly to it, for example a Laptop, I have to use the WEP number on my modem/router.

The router I'm using for my new PC is an old, spare router I kept from when I use to have Comcast internet which included just a modem. I think I'll have to reconfigure the connection on the router to work with my current modem/router from Verizon.

I think you are misunderstanding how routers are used. In your setup, your new PC should be wired directly to the Verizon router. 

Unless you are going for a much more complex setup, that old router doesn't need to be used.

---

### Post by idoitprone on 2011-03-20
> **koolaidz83095 said:**
> Hi everyone, 

I am a long-time Windows user, I've actually used XP my whole life. I'm building a new PC and I didn't have the cash to buy Windows 7 so I decided to try out a Linux distro for the first time. Keeping in mind that I have NEVER used any Linux OS before, please help me out with some of my questions. 

[http://racketware.info/msdnaa/call-on-students](http://racketware.info/msdnaa/call-on-students)
Umm are you a student? You realize there are programs to get windows for free. Please everyone else dont flame me, since i did get this off the gnu website once -lol. The reason why I suggest this is because of games. No one can live without those proprietary games. And a nice way to rip-off microsoft

> That's all my questions for now but I'm sure I will have more later. Thanks in advanced for any help and sorry for being a Linux n00b.

never say sorry for being a noob. Say sorry for staying a noob lol

---

### Post by walt.smith1960 on 2011-03-20
> **koolaidz83095 said:**
> Hi everyone, 

<snip>

That's all my questions for now but I'm sure I will have more later. Thanks in advanced for any help and sorry for being a Linux n00b.

I'm pretty new myself and here are some things I had to get accustomed to:

One REAL source of frustration initially--capital letters matter in Linux.  In Windows, myfiles.doc and MyFiles.doc are all the same file. With Linux, they are two different files.  Using terminal I'd try to change directories and get "no such file or directory" when I knew it existed.  That was because I was typing "cd desktop"  not "cd Desktop".  It matters.

Re your wireless keyboard, it sort of ties in to the above issue.  There's no caps lock or numlock  indicator installed to the Gnome desktop by default.  My wife has a Logitech mx300 wireless keyboard. It was a bit of a pain not knowing if the Caps Lock or Num Lock was on or off.   Someone here mentioned a little package in Synaptic, an applet called *lock-keys-applet*.  I installed that then right-clicked on a panel and lock-keys-applet was one of the choices to add. You can put the applet in any panel. The applet indicates whether the Capslock or Numlock are on or off.  This assumes you're using Gnome, the default Ubuntu desktop.

Re video you should have no issue there.  I've used VGA in the past and have two monitors connected with DVI cables.  One thing video related that might come into play.  In order to get the most out of your video card, you may need to enable proprietary drivers.  There are found under System -> Administration -> additional drivers.  You may find video and/or network drivers there.

If you can, connect your computer initially with an ethernet cable to your router.  This will enable you to download updates (there'll be a LOT the first time, most likely) and maybe proprietary drivers.  I also check in Synaptic "Ubuntu Restricted Extras".  This will download software that has some licensing restrictions that run contrary to the FOSS philosophy but they get you players and CODECs for common media players, download the Flash installer, Get you Microsoft Times New Roman and Arial fonts and some other goodies.

Just keep in mind that some things are done differently in Linux than they are in Windows.  Now I find working in Windows XP a royal PITA after having used Ubuntu for a few months but they do work differently and take some getting used to.

---

### Post by koolaidz83095 on 2011-03-20
> I think you are misunderstanding how routers are used. In your setup, your new PC should be wired directly to the Verizon router. 

Unless you are going for a much more complex setup, that old router doesn't need to be used.The PC I'm building is gonna be in a different room from the one I'm using right now which is going to be the family computer. The PC I'm building is gonna be for my work and is gonna be far away from my internet modem/router. The family computer I'm using now is about a decade old and can't handle my work which involves a lot of photo and video editing along with some programming. 

Unless I ground-wire an ethernet cable from my "office" (it's the basement lol) to the living room computer, which I really do not want to do, I think I will have to use a router to connect to the Verizon modem/router in the living room. 

> Umm are you a student? You realize there are programs to get windows for  free. Please everyone else dont flame me, since i did get this off the  gnu website once -lol. The reason why I suggest this is because of  games. No one can live without those proprietary games. And a nice way  to rip-off microsoftI am a high school student...so maybe? I still want to try using a Linux OS once in my life though.

---

### Post by idoitprone on 2011-03-20
> The PC I'm building is gonna be in a different room from the one I'm using right now which is going to be the family computer. The PC I'm building is gonna be for my work and is gonna be far away from my internet modem/router. The family computer I'm using now is about a decade old and can't handle my work which involves a lot of photo and video editing along with some programming. 

If you just want any linux experience try this. You dont have install it, just boot from cd and it will load to ram. This will breath new life in ur decade old computer. Just make sure it has the minimum requirements. Your kidding me about programming in a decade old computer. I heard the a programmer brought a very old portable computer to the woods and invented Pascal. You can do amazing things with shitty hardware. Using Linux taught me that
[http://distrowatch.com/table.php?distribution=puppy](http://distrowatch.com/table.php?distribution=puppy)

> I am a high school student...so maybe? I still want to try using a Linux OS once in my life though.

Remember there is alot of distro out there. Each with a different feel. btw Sorry you cannot get the free windows. I believe the program only accept college students from certain schools

Sorry for being off-topic

---

### Post by tordeu on 2011-03-20
So, your Verizon device is probably a WLAN router, so it is a router and wireless access point in one device.

Normally, you choose a wireless network you want to connect to (which would be the wireless network your verizon thing is probably providing) using the WEP key and then you are connected to the internet. But "choosing the network" has nothing to do with your verizon thing then, it is just something you can do with a wireless card/stick and should work without any kind of software installation.

I am, too, still not really sure about the complete setup.

As far as I understand it:
- You have a verizon thing which is modem+router and offers a wireless network (with the wep key)
- You have an old PC which is (wired/wirelessly connected) to the verizon thing
- You will have your new PC, which will be connected to the verizon thing using the wireless network as well.

---

### Post by abyrne on 2011-03-20
Ahh, now I see your dilemma. What you need is a wireless adapter. Laptops already have these built-in. These adapters look like USB flash drives, but they allow you to connect to your router wirelessly. A good one will run you about $50. They also come in the form of a PCI card. If you end up getting one, make sure that its compatible with Ubuntu.

> I am a high school student...
Haha same here! Power to the Young Linux Users!

---

### Post by koolaidz83095 on 2011-03-20
> Your kidding be about programming in a decade old computer. I heard the a  programmer brought a very old portable computer to the woods and  invented Pascal. You can do amazing things with shitty hardware. Using  Linux taught me thatTrue. It's just that 512mb of RAM really isn't good for like...anything:lol:. Running PSD on this computer is a nightmare.

> 
As far as I understand it:
- You have a verizon thing which is modem+router and offers a wireless network (with the wep key)
- You have an old PC which is (wired/wirelessly connected) to the verizon thing
- You will have your new PC, which will be connected to the verizon thing using the wireless network as well.     Pretty much. 

The family PC is connected to the Verizon modem/router via an ethernet cable and is in the living room. The PC I'll be building is gonna be in the basement  (my room lol) and it will have to be wirelessly connected to the Verizon modem/router for convenience because I don't want to have to use a 100ft+ ethernet cable. 

> Ahh, now I see your dilemma. What you need is a wireless adapter.  Laptops already have these built-in. These adapters look like USB flash  drives, but they allow you to connect to your router wirelessly. A good  one will run you about $50. They also come in the form of a PCI card. If  you end up getting one, make sure that its compatible with Ubuntu.I was considering getting one but I don't want to have to buy an additional piece of hardware if I don't need it (I am in high school after all...meaning I have very little money as it is lol). I'm hoping this spare Linksys I have will work but I can't be sure until I actually build my PC.

---

### Post by tordeu on 2011-03-20
Well, but to connect from your new PC to your router, you either need to

[LIST]
[*]use a wire
[*]have a wireless adapter for your pc
[*]have a powerlan adapter for your pc (please don't)
[/LIST]
So, if the PC does not have a wireless adapter already installed, you will not be able to connect to your router without either getting a wire and connecting it or getting a wireless adapter, which start at about $10, although I do not have any idea if they are usable at all. And it depends on the exact situation at your home (how far away router and PC are and how many walls/floors are between them and what kind of walls/floors these are), because even a wireless connection inside a single home can be problematic.

---

### Post by abyrne on 2011-03-20
> **koolaidz83095 said:**
> I'm hoping this spare Linksys I have will work but I can't be sure until I actually build my PC.

The thing is that routers broadcast signals to computers. They cannot receive signals from other routers.

---

### Post by koolaidz83095 on 2011-03-20
Let me just clarify everything. 


[LIST]
[*]Family PC is connected to Verizon modem/router via an ethernet cable
[*]New PC will be in the basement and will most likely have to be connect to the Verizon modem/router wirelessly
[*]I have an old Linksys router that I use to use when I had Comcast internet which included just a modem
[*]That Linksys router came with a sh*tload of ethernet cables
[*]Using the LAN port on the motherboard, new PC will be connected to the Linksys router via an ethernet cable
[*]I'm hoping the Linksys router will connect to the Verizon modem/router and then I will hopefully have internet connection on the new PC
[/LIST]

The problem is, I am not sure if the router will work on Ubuntu because it needs software to connect to other routers/modems. 

Sorry for not being clear guys.

---

### Post by abyrne on 2011-03-20
Thanks for clarifying. 
However, the fact is this: You cannot use that Linksys router in the manner you wish to use it. It is a router, not a wireless adapter. It cannot connect to your Verizon router. You need a wireless adapter.

---

### Post by tordeu on 2011-03-20
Normally, the software is not needed. They just provide the software for Windows, so that people do not need to use the webbased interface. The software then configures everything automagically and the end user does not need to configure either router or computer.

BUT, as abyrne posted just before you: WLAN routers usually do not have the ability to connect to a wireless network. I will try to find out if your Linksys offers something we can use, but I am not sure it does.

---

### Post by koolaidz83095 on 2011-03-20
Aww geez...that sucks.

What wireless PCI cards do you guys recommend to use with Ubuntu 10.10? Hopefully this won't cost me too much....

---

### Post by tordeu on 2011-03-20
It might be possible. I do not know if it supports it natively (I will look further), but you could put dd-wrt on the linksys router and that would allow you to connect your new pc to that linksys and the linksys would act as a wlan bridge, connecting to wireless network the verizon router is providing.

This is what I mean: [http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge](http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge)

---

### Post by koolaidz83095 on 2011-03-20
Like I said earlier, I know near nothing about networking. I could try that but it seems a little difficult. 

What I'm thinking about doing now is connecting the Verizon modem/router to the new PC and using the Linksys router on the family computer...would that work? I'm pretty sure that would work unless I have to install some programs that came with the Verizon modem/router to make it work.

---

### Post by tordeu on 2011-03-20
I don't think that will work and even if it would, you would have the same problem of having to small networks (Verizon+PC) and (Linksys+PC) which would need to be connected via a wireless connection.

The only thing it would change is which PC is connected to which router and which router is connected to the internet.

I am pretty sure we could find an easy tutorial for setting up the linksys as a wlan bridge, but the only other option I see would be to get a wlan adapter for the pc. But before you do that, you could try setting up the linksys anyway, which might save you the money.

Edit: If you choose to try setting up the router, you might be better of in the forum on [http://www.dd-wrt.com/](http://www.dd-wrt.com/), because the people there probably have the best knowledge. And there are some tutorials and a wiki as well. The process might look long, but it might achieve exactly what you want without any extra cost.

Edit2: A tutorial for installing dd-wrt: [http://www.dd-wrt.com/wiki/index.php/Installation](http://www.dd-wrt.com/wiki/index.php/Installation)

---

### Post by koolaidz83095 on 2011-03-22
Seems complicated and it's in a field where I don't know much so I don't think I want to go with that option. 

What wireless adapters do you guys recommend?

---

### Post by tordeu on 2011-03-22
I fully understand that. Unfortunately I can not help you with the question which wireless adapter to choose. I don't use any and I don't know if there are adapters with compatibility issues in Ubuntu.

What might be of some help, if no one can point out a specific product is the following page where you can check if a specific product is supported:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

So, if you don't want to spend too much, you could just look if you find cheap ones (e.g. at Amazon or wherever you want) and then check the device using this link.

When you click on the manufacturer, it will display a table of products and it tells you if it works out of the box and there often is a comment as well, which might indicate how well (or not) it works).

But maybe someone else can suggest a specific product.

---

### Post by SeijiSensei on 2011-03-22
A USB wireless adapter is probably your best choice.  You just plug it into a USB port and away you go.  Newegg.com is a good place to do research on hardware.  There are many Linux users there, so you can ascertain if something will work with Ubuntu.

At under $20, this item looks especially attractive:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833704045](http://www.newegg.com/Product/Product.aspx?Item=N82E16833704045)

Some people there said it didn't work with Linux, but those using it with 10.10 (Maverick) report great success.  

Since you're going to be fairly far away from the router, you may want to pay careful attention to discussions of the adapter's range.  This one gets high marks in that department as well.

---

### Post by albert s on 2011-03-22
Edimax 'EW-7318USg'  USB dongle works perfect for me on 10.04 ,
they also do a PCI version but Im not 100% sure the model, its inside my garage PC, 
I have the USB stick beside me.  :)

---

### Post by tordeu on 2011-03-22
Yeah, I saw that (the TP-Link) on [Amazon]("http://www.amazon.com/TP-Link-TL-WN722N-150Mbps-Wireless-Adapter/dp/B002WBX9C6/ref=sr_1_1?ie=UTF8&s=electronics&qid=1300828692&sr=8-1") before (for about $17), but I was not sure about recommending it, because the comment on the WiFi site indicated that some people might have problems (But that might also be a faulty device). 

But it is also listed as "works out of the box" and the reviews on Amazon are very positive as well.

---

### Post by albert s on 2011-03-22
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833315041](http://www.newegg.com/Product/Product.aspx?Item=N82E16833315041)

this is the pci card, 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833315075](http://www.newegg.com/Product/Product.aspx?Item=N82E16833315075)

and the USB stick

---

### Post by koolaidz83095 on 2011-03-22
> **SeijiSensei said:**
> At under $20, this item looks especially attractive:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833704045](http://www.newegg.com/Product/Product.aspx?Item=N82E16833704045)
I was actually looking at this one earlier. It looks good to me but I would like a little more assurance than Newegg reviews; does anyone have any personal experience? If not, does anyone have any reason to believe it will or will not work with Ubuntu 10.10 64bit?

---

### Post by tryan3131 on 2011-03-22
Sorry to interrupt, but I'm new to the forum and I'm having difficulty locating a relevant thread.  I'd appreciate some help or a redirect.

I have just installed 10.10rc (meerkat) on my HP 8510w (nvidia quadro fx 570M) and cannot enable the extra visual effects or detect my secondary monitor.  When trying to "download and install" the nvidia drivers, which it says you must do to enable "extra" visual effects, I get this error message:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/nvidia-settings/nvidia-settings_260.19.06-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/nvidia-settings/nvidia-settings_260.19.06-0ubuntu1_i386.deb) Connection failed [IP: 91.189.88.40 80]

I have been having some trouble in the past days retrieving packages from some of the sources, but cannot figure out why.

Does anyone have any suggestions?

---

### Post by samcot on 2011-03-22
Koolaidz, have you considered using the "Live" version of Ubuntu - running it from the CD, to see how it works (or doesn't work) on your PC? That's the no-risk way of trying it out ahead of time.
 
Good luck!

---

### Post by tryan3131 on 2011-03-22
I've been running meerkat for a couple days now.  Had quite a bit of trouble installing MATLab because I couldn't get the build-essential to install (needed gcc compiler).  Same issues with retrieving packages and what not.  Finally was able to get it working after fetching some things with wget from the terminal.

It recognizes that there are drivers because when I click "extra" under *system > preferences > appearance > visual effects* it searches for the drivers and tells me that I have to download the Nvidia accelerated graphics driver.  I click "ok" and it starts to "download and install".  When the status bar is at about 10% I get the "failed to fetch" message.

So the drivers exist, I just can't download them for some reason.

---

### Post by tordeu on 2011-03-22
koolaidz83095, have you seen the link I posted?

It lists the device as "works out of the box":
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
That is at least some assurance when it comes to compatibility with Ubuntu.

Also, it has pretty good reviews on [Amazon.com]("http://www.amazon.com/TP-Link-TL-WN722N-150Mbps-Wireless-Adapter/dp/B002WBX9C6/ref=sr_1_9?ie=UTF8&qid=1300835620&sr=8-9"), which has it listed for $17, although it is now temporarily out of stock there.

---

### Post by tordeu on 2011-03-22
@tryan3131:

Please open an own thread for your question to get the best help. Otherwise your problem will not  get the necessary attention, cause your question is hidden inside a thread with an unrelated problem.

---

### Post by SeijiSensei on 2011-03-22
> **koolaidz83095 said:**
> I was actually looking at this one earlier. It looks good to me but I would like a little more assurance than Newegg reviews

Actually I think that Newegg reviews by Linux users are pretty reliable.  I'd rather see reports from people who've actually used a device with a Linux distribution than some marketing material claiming the device is compatible.  Also, as I said before, you should be looking at reports on how well the adapters perform at a distance and through obstructions like walls and metal framing.  Reviewers are probably going to be the only source of decent information about actual performance in real-world settings.

I wish Intel made wifi adapters for desktop PCs.  Their drivers have always been rock-solid for me, and they're open-source.  I only ever see Intel cards for [laptops]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100010074%2050001157&IsNodeId=1&name=Intel").

---

### Post by koolaidz83095 on 2011-03-22
> **tordeu said:**
> koolaidz83095, have you seen the link I posted?

It lists the device as "works out of the box":
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
That is at least some assurance when it comes to compatibility with Ubuntu.

Yeah I saw it, I am just now figuring out how to navigate it...derp. 

It says the model Seiji listed is "a waste of money":confused:

---

### Post by tordeu on 2011-03-22
Yeah, I know. I am not sure about that, because it could be a problem just this specific person has with this device (maybe even a faulty one).

I don't know how Amazon.com/NewEgg etc. handle returns, but maybe it might be possible to get a device and return it, if you experience problems or it just does not work at all. But I am not from the States, so I don't have experience with shops over there.

There is a thread about it for 10.04:
[http://ubuntuforums.org/showthread.php?t=1611537](http://ubuntuforums.org/showthread.php?t=1611537)

And in the link referred to in this thread, it also says that this fix is not needed for 10.10, so that the problem described in the first thread should arise in 10.10:
[http://ubuntuforums.org/showthread.php?t=1564278](http://ubuntuforums.org/showthread.php?t=1564278)

---

### Post by SeijiSensei on 2011-03-22
> **koolaidz83095 said:**
> It says the model Seiji listed is "a waste of money":confused:

I glanced over that document, and it looks quite out-of-date to me.  I looked specifically at the comments about my Linksys adapter, and every reference I saw was to Ubuntu versions older than Karmic.  Considering that I had issues with my adapter in Lucid that were solved by moving to the newer kernel in Maverick, I don't trust any discussions about wifi hardware capabilities that aren't based on the same release version I'm using.  Linux wifi drivers still often seem  like moving targets, even in supposedly stable versions like Lucid.

---

### Post by dmizer on 2011-03-22
Why are you looking at wireless cards if your going to be connected by a LAN cable? There's no need to even think about configuration or settings or anything if you use a LAN cable. 

You seem to be concerned about being able to configure your router once it's connected, but since your Verison modem is also a router I am confused as to why you think you need a dedicated router in the first place.

If there is a free LAN port on your Verison modem, just plug your LAN cable directly to the modem and you will need to do nothing else, no configuration, no searching for the "right" wireless card, no configuring your dusted off router to work correctly on your network.

Plug and go.

---

### Post by tordeu on 2011-03-22
> **SeijiSensei said:**
> I glanced over that document, and it looks quite out-of-date to me. 

Some stuff, yes. But the last update for the TL-WN722N is listed as "2010-11-03", so it should be recent enough.

---

### Post by tordeu on 2011-03-22
@dmizer:

He did not want to use a LAN cable, cause his Verizon router is upstairs and his PC in the basement.

---

### Post by dmizer on 2011-03-22
> **tordeu said:**
> @dmizer:

He did not want to use a LAN cable, cause his Verizon router is upstairs and his PC in the basement.
Ugh, I read the whole thread and completely missed that.

koolaidz83095 had the idea to use the router as a wireless bridge to connect to the modem. I read that there was some concern that the router needs some software for configuration, but the router is a WRT54GS v6 which can definitely be configured without the included software. Just browse to the router's configuration page at 192.168.1.1

However, it doesn't look like the router can be used as a bridge by default, but as was mentioned earlier using dd-wrt firmware is a good option. It may look difficult, but at least it's free. dd-wrt would also eliminate the Linksys software worry.

---

### Post by NCLI on 2011-03-22
I second installing DD-WRT on the router and using it as a bridge. It's pretty damn easy.

---

### Post by ClientAlive on 2011-03-22
Well is he using cable internet and is there a coax jack in the basement? 'IF' that were the case he could just hard wire everything (coax from the outlet in the wall - to - linksys router; then lyknsys router- to new computer via ethernet cable). Everything upstairs (the other computer) statys the same.

Jake

---

### Post by tordeu on 2011-03-23
Yeah, I suggested dd-wrt as well, since the v6 of his router is supported, and posted two links about installing dd-wrt and wireless bridged mode.

But he chose to go the wireless adapter route instead (#29). I also think that the tutorials on installing dd-wrt do look more intimidating than they ultimately are (because they are quite long), so I can understand that one might not want to attempt that. But of course it would be a great option (for free) and when you don't use the router otherwise... what's the harm?

On the other hand, if the wireless adapter is supported "out of the box", I can understand that someone would not like to try fiddling with the router.

@ClientAlive:

Reusing existing wire is an interesting idea. I have not thought of that. Let's see if he has usable wire and if might want to try to go that route. But using a wireless adapter should be the easiest option and there are some affordable adapters (although "affordable" is always a relative term), so I think it is a good route for beginners.

But now you got me an cool idea and I am the one wanting to use existing wire and playing around with it ;)

---

### Post by koolaidz83095 on 2011-03-23
I'm actually okay with trying to configure dd-wrt on my router if it saves me money. As I said earlier, I am fine with handling hardware and software installation, I just don't know anything about networking. I thought dd-wrt was some kind of strange networking thing but if it is just software that I need to program into the router, I'll give it a try. 

The more money I save, the better (hence using a distro instead of buying Windows).

---

### Post by tordeu on 2011-03-23
Yeah, dd-wrt replaces the firmware on the router which is currently on there. So, it is like a software which runs on the thing. And dd-wrt offers a lot more features as (pretty much?) all devices offer without it.

One install tutorial can be found [http://www.dd-wrt.com/wiki/index.php/Installation](http://www.dd-wrt.com/wiki/index.php/Installation).

I am not familiar with it, cause my router unfortunately is not supported, but I am sure that others can help you with it (although those install tutorials are normally a lot easier than they look at first glance) and you might also want to check out the forums over at [http://www.dd-wrt.com]("http://www.dd-wrt.com/"), as this certainly is the best place for support with dd-wrt.

---

### Post by engineer333 on 2011-08-14
> **tordeu said:**
> 

While I do not have the EX100, I do have a Logitech Keyboard (K800) and a Logitech mouse (MX Revolution) and the K800 is a pretty new model. Both devices work great with Ubuntu.


Hey, I am new to these forums, but i've been using my Ubuntu for about 2 years now.  I just bought the K800 and it wont work at all!   What am i doing wrong?  Where can I find the software to support it?  

Thanks for any help in advance, I am about to return it if i can't get it to work.  Much appreciated.

---

### Post by dmizer on 2011-08-14
> **engineer333 said:**
> Hey, I am new to these forums, but i've been using my Ubuntu for about 2 years now.  I just bought the K800 and it wont work at all!   What am i doing wrong?  Where can I find the software to support it?  

Thanks for any help in advance, I am about to return it if i can't get it to work.  Much appreciated.

According to what I've read, your keyboard is supported in Ubuntu so it should work.

Please post a separate thread so you can get more help.

---

