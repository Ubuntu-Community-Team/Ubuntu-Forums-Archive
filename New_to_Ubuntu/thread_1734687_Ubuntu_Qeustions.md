---
title: "Ubuntu Qeustions"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by mrob184 on 2011-04-20
Hi everybody I'm new here and new to Ubuntu.
I've been test driveing Ubuntu 10.10 on my laptop and now my desktop and I have some software instalation qeustons.
Useing the Ubuntu software center to get and install software seems to work pretty good. However installing some software that I need or want is not available at the software center and installs in the terminal.
I do not mean to upset or offend anyone but messing around in the terminal is a nightmare.
I would say who understands that stuff? But spending many days and countless hours of searching this forum I understand that alot of you do. But where is the love for the dumb beginer such as myself?

Do not get me wrong I am loveing Ubuntu but it is this issue with software and driver instalation  that is preventing me from building a new desktop PC to run Ubuntu Studio on for my guitar room.
I have not been able to get any real answers as to what hardware is compatable and be able to use all of studio's features. I have spent days searching this subject and have come up with nothing solid.
Any help would be appreciated.
Thanks for reading and hopefully nobody will want to set me on fire.:P

---

### Post by josephmills on 2011-04-20
> **mrob184 said:**
> Hi everybody I'm new here and new to Ubuntu.
I've been test driveing Ubuntu 10.10 on my laptop and now my desktop and I have some software instalation qeustons.
Useing the Ubuntu software center to get and install software seems to work pretty good. However installing some software that I need or want is not available at the software center and installs in the terminal.
I do not mean to upset or offend anyone but messing around in the terminal is a nightmare.
I would say who understands that stuff? But spending many days and countless hours of searching this forum I understand that alot of you do. But where is the love for the dumb beginer such as myself? have you tried using **synaptic package manager?** I also feel your pain when it comes to the cli as I am dyslectic so typing for me is a nightmare. I wish that there where software for speech to text.  
> 
Do not get me wrong I am loveing Ubuntu but it is this issue with software and driver instalation  that is preventing me from building a new desktop PC to run Ubuntu Studio on for my guitar room.what software are you talking about what drivers?> 
I have not been able to get any real answers as to what hardware is compatible and be able to use all of studio's features. I have spent days searching this subject and have come up with nothing solid.
Any help would be appreciated.
Thanks for reading and hopefully nobody will want to set me on fire.:P
if you would like to use it for just you "guitar room"
then I would say  check out other programs like gtkguitune and kguitar,lingot,tux guitar,**rakarrack**well I hope this helps please give us some more info about your hardware and software issues and we will see if we can fix it up for you. OHH and Welcome to ubuntuforums

---

### Post by BertN45 on 2011-04-20
Download the ".deb" file of the program you want and double click on it and the program will be installed. I think in 10.xx, it was already using the software center for it.

For the guitar room and the drivers you need to be more specific, if you need help. I know that most of this type of audio equipment is connected to the PC using USB. You are right, sometimes it will be difficult to find the drivers. If it is connected through USB, you could check, whether your laptop installs the right drivers if your equipment is connected to it.

If not, you have to know one command from the terminal to detect what chipset is used by the USB equipment and that command is: lsusb. Use the name displayed by lsusb to find the drivers. If it is a deb file double click it, else you have to follow the instructions or type (a part o)f that chip set name in the search box of the synaptic package manager and take it from there.

Often the box is produced by another company as the electronics (chip set). For the driver the chip set is important. Note that the chip set is often used by more then one box manufacturer.

---

### Post by GWBouge on 2011-04-20
Terminal can be a real put-off for a beginner, but believe it or not, it's also one of the easiest, most efficient ways for someone to give help and to do certain things.  A lot of times there are point-and-click methods to do the same thing, but given the amount of desktop environments and endless configuration options, the terminal is pretty much the only 'standard' you can rely on to tell someone exactly what to do.  On the other hand, if it's software you're trying to install that you need to compile from source (ie: ./configure, make, make install) ... my advice would be to find some other software in .deb format, lol.

Just a note:  three things that tend to get overlooked by beginners that help immensely in the terminal:

1)  Cut'n'paste / drag'n'drop.
2)  TAB key auto-completion.  Don't type a 25-character file name, just type the first few and hit TAB, it will fill in the rest.
3)  File/directory names are CASE SENSETIVE.

As for hardware, MANY things work out of the box, but yeah, sometimes it can take a bit of research to find out what those things are since a lot of manufactures are a bit slow on their Linux support.  Something I've found myself doing lately is checking out the 'Feedback' tab on Newegg.com on something I like and searching for 'Linux' or 'Ubuntu' ... it's quite helpful.  If you spend enough time just skimming through the support forums, you'll notice trends on which hardware manufactures have shoddy Linux support, and which products to avoid.  But if you build your Studio PC right, everything will work out of the box, or with point and click driver installation through 'Additional Drivers'.

For instance, nVidia video cards tend to have little to no problems (except for one of their laptop video architectures I believe), and most HT Omega and M-Audio sound cards seem to be supported straight out of the box.

---

### Post by mrob184 on 2011-04-20
WOW! replies already?
Thanks for the attention.:D
Let me try to cliarify my dilema if possable.
I want to build a desktop to run Studio on so that I can work with my pictures, work with videos like vacation stuff and of course play with all the audio stuff with my guitars and eqiupment. I went to the Studio website and did alot of reading as well as viewed many videos at youtube on Studio. I LOVE it and it appears to do everything I want to do.
However I cannot find a list of video chipets that tell me if they are supported or not. I have found a list of soundcards but not video. Maybe I'm not looking in the right place?
Are the ATI video chips the nightmare they appear to be on the forum?
There seems to be lots of threads complaining of nightmarish problems with drivers for ATI chips.
I'm not really sure if anything from ATI will work or not unless I go into terminal and now how to compile and package and maybe even make my own driver.
I am so confused because it seems like I need to know a bunch of code righting just to get something to work, like video.
What about the onboard video chips like ATI 4250 or 4290? Are they supported? Are they good enough to run studio?
Thanks alot and I oppologise for the greenness fo my beans.:oops:

---

### Post by K_45 on 2011-04-20
That distro has some heavy apps so I would install an 8GB RAM kit, a Phenom x4 955 w/ an additional heatsink and for the GPU, something like this is sufficient:  [http://www.newegg.com/Product/Product.aspx?Item=N82E16814131355](http://www.newegg.com/Product/Product.aspx?Item=N82E16814131355)    Motherboard would be an Asrock 890GX Extreme 4.

---

### Post by mrob184 on 2011-04-20
> **K_45 said:**
> That distro has some heavy apps so I would install an 8GB RAM kit, a Phenom x4 955 w/ an additional heatsink and for the GPU, something like this is sufficient:  [http://www.newegg.com/Product/Product.aspx?Item=N82E16814131355](http://www.newegg.com/Product/Product.aspx?Item=N82E16814131355)    Motherboard would be an Asrock 890GX Extreme 4.

Thanks for the input. I really do appreaciate it but I need to say this.
I do not want to build a computer that sounds like a jet going down the runway with all those fans wizzing away. maybe thats not the case with that video card but my experiance with those types of cards is they are loud. I hope I'm wrong about that.

My days of OC'ing are over.
A 4 core processor? really? a Dual core not enough?
I'm not doubting you I just do not understand your reasons for such highend parts.
I will not be gameing, if that makes a difference.
Thanks.

---

### Post by K_45 on 2011-04-20
> **mrob184 said:**
> Thanks for the input. I really do appreaciate it but I need to say this.
I do not want to build a computer that sounds like a jet going down the runway with all those fans wizzing away. maybe thats not the case with that video card but my experiance with those types of cards is they are loud. I hope I'm wrong about that.

My days of OC'ing are over.
A 4 core processor? really? a Dual core not enough?
I'm not doubting you I just do not understand your reasons for such highend parts.
I will not be gameing, if that makes a difference.
Thanks.

 Blender models 3D, so the more cores the better, that GPU is a low end card as you can see by the price, and the PC will be quiet as I've suggested to replace the stock heatsink. For anything multimedia, the more cores the better.

---

### Post by mörgæs on 2011-04-20
As a beginning, try to get some used gear and get some experience with Ubuntu Studio. You might risk building too big a system if you are trying to solve all problems from first day.

As for the command line: By all means, try to learn using it. After a while you will see that it makes tasks many times easier. There is a good beginner's book in my signature.

---

### Post by kaldor on 2011-04-20
> There seems to be lots of threads complaining of nightmarish problems with drivers for ATI chips.
I'm not really sure if anything from ATI will work or not unless I go into terminal and now how to compile and package and maybe even make my own driver.

Seems a bit intense :)

From my experience, ever since 2009 (around Karmic) AMD/ATI open source drivers work awesomely and out of the box on Ubuntu and most other mainstream distros. It's the Official drivers that may be causing issues, but you can install them with Jockey (System > Administration > Additional Drivers).

If you aren't gaming or doing 3d-intensive work, AMD Open source drivers are very very stable and should work by default.

---

### Post by mrob184 on 2011-04-20
> **K_45 said:**
> Blender models 3D, so the more cores the better, that GPU is a low end card as you can see by the price, and the PC will be quiet as I've suggested to replace the stock heatsink. For anything multimedia, the more cores the better.

OK point well taken! 
Those parts are on my consideration list.
Thank you.

---

### Post by alphacrucis2 on 2011-04-20
> **mrob184 said:**
> WOW! replies already?
Thanks for the attention.:D
Let me try to cliarify my dilema if possable.
I want to build a desktop to run Studio on so that I can work with my pictures, work with videos like vacation stuff and of course play with all the audio stuff with my guitars and eqiupment. I went to the Studio website and did alot of reading as well as viewed many videos at youtube on Studio. I LOVE it and it appears to do everything I want to do.
However I cannot find a list of video chipets that tell me if they are supported or not. I have found a list of soundcards but not video. Maybe I'm not looking in the right place?
Are the ATI video chips the nightmare they appear to be on the forum?
There seems to be lots of threads complaining of nightmarish problems with drivers for ATI chips.
I'm not really sure if anything from ATI will work or not unless I go into terminal and now how to compile and package and maybe even make my own driver.
I am so confused because it seems like I need to know a bunch of code righting just to get something to work, like video.
What about the onboard video chips like ATI 4250 or 4290? Are they supported? Are they good enough to run studio?
Thanks alot and I oppologise for the greenness fo my beans.:oops:

Those ATI cards should be fine. You will need to install the proprietary driver for best performance. I would try the fglrx in the ubuntu repos first (install via system administration hardware drivers). This is fglrx 8.780 IIRC which is a little old. If you have any trouble with it, just install the latest version from AMD. AMD release a new Catalyst/fglrx version every month and the bug fixes and other improvements are definitely worth it. If you do this look up the ubuntu ati binary driver howto and install it via the buildpkg method they talk about.

---

### Post by K_45 on 2011-04-20
I'd use a Thermaltake Contac 29 for a heatsink; the stock AMD heatsink sounds like D-Day in your case.

---

### Post by mrob184 on 2011-04-20
> **mörgæs said:**
> As a beginning, try to get some used gear and get some experience with Ubuntu Studio. You might risk building too big a system if you are trying to solve all problems from first day.

As for the command line: By all means, try to learn using it. After a while you will see that it makes tasks many times easier. There is a good beginner's book in my signature.

Well I've already tried that.
The PC I'm on right now has Ubuntu desktop on it and the ATI card in it will not work. I am haveing to use the onboard VIA graphics chipset to have a moniter to look at. THE ATI card is an old card (I think a 8500?) but its a no go once the descktop tries to load. The combination of my card not working and reading all the problems with ATI made me backup. But it is an old card and maybe thats the problem.

Command line: 
WOW is all I can say. I have done it....BUT only when I found the exact commands I needed for something so I could cut and paste them in. I have no idea what any of it meant or what it did. I do not like doing things and not understanding why or what for, but at that point I did not care if the computer blew up and launched itself into space infact I would have probably cheered it on and saluted.:p
I'll have a look at the book you suggest...Hopefully it will help me.
Thanks.

---

### Post by kaldor on 2011-04-20
> **mrob184 said:**
> Well I've already tried that.
The PC I'm on right now has Ubuntu desktop on it and the ATI card in it will not work. I am haveing to use the onboard VIA graphics chipset to have a moniter to look at. THE ATI card is an old card (I think a 8500?) but its a no go once the descktop tries to load. The combination of my card not working and reading all the problems with ATI made me backup. But it is an old card and maybe thats the problem.

Command line: 
WOW is all I can say. I have done it....BUT only when I found the exact commands I needed for something so I could cut and paste them in. I have no idea what any of it meant or what it did. I do not like doing things and not understanding why or what for, but at that point I did not care if the computer blew up and launched itself into space infact I would have probably cheered it on and saluted.:p
I'll have a look at the book you suggest...Hopefully it will help me.
Thanks.

The reason you hate the command line is because you don't understand it. I recommend you learn what the commands are instead of just pasting them :)

Click [here]("https://help.ubuntu.com/community/UsingTheTerminal") for a basic overview of how commands work on Linux.

---

### Post by mrob184 on 2011-04-20
> **alphacrucis2 said:**
> Those ATI cards should be fine. You will need to install the proprietary driver for best performance. I would try the fglrx in the ubuntu repos first (install via system administration hardware drivers). This is fglrx 8.780 IIRC which is a little old. If you have any trouble with it, just install the latest version from AMD. AMD release a new Catalyst/fglrx version every month and the bug fixes and other improvements are definitely worth it. If you do this look up the ubuntu ati binary driver howto and install it via the buildpkg method they talk about.

Boy I'm probably gonna get into trouble here but here goes.
First let me say that I do appreciate your willingness to help and I in no way mean to offend you (honestly) but what did you just say?:P
I've been to ATI's site to check the driver situation but from what I read there is no click on and its installed drivers. Instead there's this endless session of command prompts and well if that did'nt work here change the files to this or that oh and by the way you might want to throw a few deb files in there as well just incase you have any hair left that you have'nt already snatched out and dont forget Tarballs. LOL!!!!!

This is the absolute Beginer forum and I just feel like there's no hope for me because I do'nt speak Linuxese.
I do appreciate your input but I'm as lost as an Easteregg.:oops:

---

### Post by mrob184 on 2011-04-20
> **kaldor said:**
> The reason you hate the command line is because you don't understand it. I recommend you learn what the commands are instead of just pasting them :)

Click [here]("https://help.ubuntu.com/community/UsingTheTerminal") for a basic overview of how commands work on Linux.

I completely and 110% agree with what you just said.
I do thank you for the info and am going to take some time now to go through the material that has been recomended so far.
I will return later......probably with more qeustions than ever.
I have a feeling I'm gonna end up being the most hated person on this forum before its over with.

---

### Post by alphacrucis2 on 2011-04-20
> **mrob184 said:**
> Boy I'm probably gonna get into trouble here but here goes.
First let me say that I do appreciate your willingness to help and I in no way mean to offend you (honestly) but what did you just say?:P
I've been to ATI's site to check the driver situation but from what I read there is no click on and its installed drivers. Instead there's this endless session of command prompts and well if that did'nt work here change the files to this or that oh and by the way you might want to throw a few deb files in there as well just incase you have any hair left that you have'nt already snatched out and dont forget Tarballs. LOL!!!!!

This is the absolute Beginer forum and I just feel like there's no hope for me because I do'nt speak Linuxese.
I do appreciate your input but I'm as lost as an Easteregg.:oops:

You normally install AMD/ATI's proprietary driver under Ubuntu by using the Ubuntu Menu -- System Administration Hardware Drivers. It will tell you if it thinks there are any proprietary drivers available for your graphics card. Ubuntu doesn't install proprietary/closed source drivers by default, you have to tell it to do that. If the ATI driver isn't listed but you have an ATI card, it means that your card is one of those that AMD dropped support for a year or so back. The HD 2/3/4000 series and newer are definitely supported but the old 8500 you mentioned will not be suppported by the proprietary driver that Ubuntu offer as AMD dumped support for those older cards.

The AMD/ATI driver Ubuntu have in their repositories for Maveric (Ubuntu 10.10) is several months old. You definitely want to install the latest from AMD if you have a HD 4290. The [Ubuntu binary driver howto]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") explains how to download the latest driver from AMD and install. 

Your other option is to wait till the Natty version of Ubuntu Studio comes out as that will have the latest AMD driver available.

---

### Post by mrob184 on 2011-04-20
> **alphacrucis2 said:**
> You normally install AMD/ATI's proprietary driver under Ubuntu by using the Ubuntu Menu -- System Administration Hardware Drivers. It will tell you if it thinks there are any proprietary drivers available for your graphics card. Ubuntu doesn't install proprietary/closed source drivers by default, you have to tell it to do that. If the ATI driver isn't listed but you have an ATI card, it means that your card is one of those that AMD dropped support for a year or so back. The HD 2/3/4000 series and newer are definitely supported but the old 8500 you mentioned will not be suppported by the proprietary driver that Ubuntu offer as AMD dumped support for those older cards.

The AMD/ATI driver Ubuntu have in their repositories for Maveric (Ubuntu 10.10) is several months old. You definitely want to install the latest from AMD if you have a HD 4290. The [Ubuntu binary driver howto]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") explains how to download the latest driver from AMD and install. 

Your other option is to wait till the Natty version of Ubuntu Studio comes out as that will have the latest AMD driver available.

OK I followed the link you posted and it seems that as long as there install works as it should the driver will not be a problem. However if it does'nt I'm screwed because its off to terminal I go.
I hate to say this(I really do) because its certainly not gonna get me any friends here........But I never have had to do anything even remotely like DOS in windoze. 
There... I said it and I hate myself for it, but its done.
I have tried to understand the info in the Wiki link that was posted and have read most all of the other such info in that site about Ubuntu. But anything talking about terminal gives me a big headache and I understand NONE of it. None of it makes any sense to me at all. Command prompt seems like some strange computer language that I do not understand because I'm not a computer. Just as I do not understand Chinese because I'm not Chinese.
I'm not gonna give up unless you guy's ban me from being here but I am gonna have have to run to the drugstore for more Advil because my head is pounding!
My latest aggrivation is that my movie player does not play DVD's. I just found that out.
Any suggestions where I should start a thread about that?
There are so many forums here I'de like to put it into the appropriet place.
Thanks for the help.:)

edit: Sorry for the referance to a Wiki site that was incorrect. I meant the Ubuntu documentation. Sorry.

---

### Post by BertN45 on 2011-04-21
You are completely right, command lines are something from the past. I know it, since I was there, using  main frames (the age of the dinosaurs). A desktop where you have to use the command line is incomplete and  a driver that need pages to explain how to install it, is incomplete too. 

On the other hand all work is done by volunteers in their spare time and maybe they found a nice girlfriend or a new job and had no time to gift-wrap everything.  But the community as a whole should pay more attention to the gift wrapping. For many new users (non-PC hobbyists) a driver is not usable without the gift-wrap.

---

### Post by K_45 on 2011-04-21
At least Linux doesn't dumb down the whole OS. The command line is also far more efficient than any GUI. Who needs a resource intensive OS, when you can do all your work (if your choose) at the command line?

---

### Post by mrob184 on 2011-04-21
> **BertN45 said:**
> You are completely right, command lines are something from the past. I know it, since I was there, using  main frames (the age of the dinosaurs). A desktop where you have to use the command line is incomplete and  a driver that need pages to explain how to install it, is incomplete too. 

On the other hand all work is done by volunteers in their spare time and maybe they found a nice girlfriend or a new job and had no time to gift-wrap everything.  But the community as a whole should pay more attention to the gift wrapping. For many new users (non-PC hobbyists) a driver is not usable without the gift-wrap.

Well at least I do not feel so lonely now. Way back in the day I also attempted command lines, I could not get it then and I still cannot. This is so depressing.  
You are right about the incompleteness of some things. I just do not understand why I can install and uninstall things useing the Ubuntu software center just like any other comercial software. But the things that are not there of which I usually need a couple of need all that command line stuff.
I'm not sure how to ask this but I'll try.
Are those programs and drivers just missing some kind of install package that would make them click and install? Are there programs made to build those install packages?
I do not mean to sound ungratefull as I know and understand that all of this is done by volunteers and I do appreciate there efforts. But if this install problem was fixed Mr Gates would have to sell his mansion. I know alot of people who are wanting to jump off of his ship but will not all because of this 1 problem.

---

### Post by mrob184 on 2011-04-21
> **K_45 said:**
> At least Linux doesn't dumb down the whole OS. The command line is also far more efficient than any GUI. Who needs a resource intensive OS, when you can do all your work (if your choose) at the command line?

Hey I agree with you and I'm no lover of windows, thats why I'm here in the first place.
Let me throw this out there.
Computers have become so neccesary in everyday life that they are everywhere and involved in everything, much like cars. 
However owning and driveing that car does not require that the owner know how to tear down the engine and transmission and completely reassemble everything everytime you change the radio station just to drive it.
I'll be honest, I would much rather sit in the drivers seat useing the steering wheel and gas pedal to drive to the store rather than sit in the engine compartment working the throttlebody by hand to gas it and pulling and tugging on the tierods to steer it.:P
That is what command line is like for me, driveing a car in the engine compartment.
I understand that command line is faster and very easy to alot of people. But not if you do not understand it, infact it takes way longer and people like me end up not makeing any friends and getting banned from forums.
I really hope I'm not makeing anyone mad as thats not my intention. I do appreciate the input and if nothing else maybe something I've said will make sense at some point and cause a solution to the problem.

---

### Post by mörgæs on 2011-04-21
Rather than talking of the problem you should begin doing something about it. 

Try to open a command prompt and run **ls** (it is a lowercase LS). What happens?

Next step: Run **ls -l** (lowercase LS -L). What happens?

Here is the complete list of options belonging to **ls**:
[http://oreilly.com/linux/command-directory/cmd.csp?path=l/ls](http://oreilly.com/linux/command-directory/cmd.csp?path=l/ls)

Don't be blown away by the number of options! Try some and see what is useful for you.

As long as Ubuntu is not asking for the password, you can not damage the system.

People here are more than willing to help about specific commands, but yet another debate of 'writing or clicking' does not benefit any of us.

---

### Post by mastablasta on 2011-04-21
also intended to comment on that. ATI has issue only with latest models of card as drivers are nto ready yet and some older mobility onboard chips and few dedicated ones. bt things are imrpoving. With newer version of the GPU you won't install driver via terminal but you will enable them from hardware drivers menu.
Nvidia is also an option. Some people go only for it. Perhaps they are right...
 
but i owuldn't use an SiS or Intel or VIA

---

### Post by BertN45 on 2011-04-21
> **K_45 said:**
> At least Linux doesn't dumb down the whole OS. The command line is also far more efficient than any GUI. Who needs a resource intensive OS, when you can do all your work (if your choose) at the command line?

Who needs a high level language like C/C++ if you can write everything much more efficiently in assembler. 

Efficiency is not the point, my point is to make the system usable by the average person, with another hobby as computers. I think it is the same goal as the Canonical has with Ubuntu.

If you like to do everything with the command line fine, it is a nice hobby. Linux is not so efficient, because it is only supporting the command line, Linux is so efficient because it is well designed from the start and because is it very open for improvements and new ideas.

---

### Post by Fraoch on 2011-04-21
> **mrob184 said:**
> I do not want to build a computer that sounds like a jet going down the runway with all those fans wizzing away.

They make passively-cooled video cards, no fans.  They are low-end, which also means they're affordable, and they're often low-profile/half height, saving space and improving airflow inside your case.

They're suitable for everything but gaming.  They'll even play HD movies.

I'm using this:

[http://www.sparkle.com.tw/product_detail.asp?id=88&sub_id=247](http://www.sparkle.com.tw/product_detail.asp?id=88&sub_id=247)

New versions use the GT 210:

[http://us.msi.com/index.php?func=proddesc&maincat_no=130&cat2_no=136&prod_no=2082](http://us.msi.com/index.php?func=proddesc&maincat_no=130&cat2_no=136&prod_no=2082)

Mine installed in a few clicks, no terminal usage necessary.  Runs perfectly.  Note these are both NVIDIA cards - not sure about ATI but I have seen a high-end passively-cooled ATI card:

[http://www.gigabyte.com/products/product-page.aspx?pid=3584#ov](http://www.gigabyte.com/products/product-page.aspx?pid=3584#ov)

As for the terminal, obviously user-friendly distros have been working on minimizing its use as much as possible from the beginning as this was always a criticism of Linux from newcomers.  It is getting better.  But when you have to change something pretty low-level or fundamental you appreciate the terminal more and more.  Windows does not let you customize to the extent that Linux does through the terminal, and when it does it's just as difficult (if not more so!) in Windows to do this - ever gotten into the Windows registry?

Also by copying and pasting commands from the forums and elsewhere, you can issue some pretty powerful commands that are incredibly specific and would be hard to do through a GUI - Linux, Windows or Mac.

I honestly don't think anyone will ban you for saying you don't like it.  Lots of newcomers don't.  It is intimidating at first.  I've gotten better and better at it more or less through osmosis - eventually you'll start to notice a pattern.  What's that "sudo"?  Note how many commands go "command -something [filename]"...you will see things like this again and again.  After a while I started remembering what some of these did and it's easy to google the command to find out how to use it.

Yes, in an ideal world a new user shouldn't *have* to use it or understand it.  But Ubuntu and Linux in general is evolving much faster than Windows.  The requirement is lessening all the time.  All the same, it's good to know it's there, and if you ever want to really customize Ubuntu, the terminal will give you unbelievable control over *everything*.

---

### Post by K_45 on 2011-04-21
> **mrob184 said:**
> Hey I agree with you and I'm no lover of windows, thats why I'm here in the first place.
Let me throw this out there.
Computers have become so neccesary in everyday life that they are everywhere and involved in everything, much like cars. 
However owning and driveing that car does not require that the owner know how to tear down the engine and transmission and completely reassemble everything everytime you change the radio station just to drive it.
I'll be honest, I would much rather sit in the drivers seat useing the steering wheel and gas pedal to drive to the store rather than sit in the engine compartment working the throttlebody by hand to gas it and pulling and tugging on the tierods to steer it.:P
That is what command line is like for me, driveing a car in the engine compartment.
I understand that command line is faster and very easy to alot of people. But not if you do not understand it, infact it takes way longer and people like me end up not makeing any friends and getting banned from forums.
I really hope I'm not makeing anyone mad as thats not my intention. I do appreciate the input and if nothing else maybe something I've said will make sense at some point and cause a solution to the problem.

At least if you can strip down the car, just like you strip down Linux right down into the guts of the OS, you'll what to fix and when and will not get ripped off.

---

### Post by K_45 on 2011-04-21
> **BertN45 said:**
> Who needs a high level language like C/C++ if you can write everything much more efficiently in assembler. 

Efficiency is not the point, my point is to make the system usable by the average person, with another hobby as computers. I think it is the same goal as the Canonical has with Ubuntu.

If you like to do everything with the command line fine, it is a nice hobby. Linux is not so efficient, because it is only supporting the command line, Linux is so efficient because it is well designed from the start and because is it very open for improvements and new ideas.

Linux supports more than the command line. With X and a GUI you can have a pretty system if you choose. YOu are right about the openness - the command line will always be there if you wish.

---

### Post by Dutch70 on 2011-04-21
Well I didn't read through this thread to not post my opinion.

Some of you are very confused about the cli. There is a GUI, use it if you don't like using the terminal, but consider this. 3-5 people want help to install Ubuntu Tweak. One is using Ubuntu, one using Xubuntu, another Lubuntu...the list goes on. 

Which is easier, telling one to Open software center, search for this, click that, now select this and click on that. Oh, it's different for other OS's that receive support here. 3-5 different sets of directions or....

Why don't all of you open a terminal, copy/paste this command & hit enter.
```
sudo apt-get install ubuntu-tweak
```

Thank you and...Next! :)

The cli is what makes the support forum work so well & we all started with...
 "what is a terminal and where is it??

Just because you can put the top down on a convertible doesn't mean you have to.

Edit: I really meant for that to help people understand the use of the terminal, not sound sarcastic. I don't think I accomplished that very well. ;)

---

### Post by BertN45 on 2011-04-22
> **Dutch70 said:**
> 
The cli is what makes the support forum work so well & we all started with...
 "what is a terminal and where is it??

If I buy a car, I expect, it works and if the dealer tells me that I  have to understand, how to do some reparations, I go to the competition. 

The cli is what the community has been getting used to, but the community consists largely of computer hobbyist. Ubuntu wants to open the Linux world to the average desktop user. The average desktop user just wants to click around. Their hobby are photos, video, genealogy, stamps, recording their music, selling stuff on Ebay. As soon as you tell them they need to understand the command line, they are out, back to Windows. And the Linux Desktop remains a system of the nerds, by the nerds, for the nerds :) . 

( In the car example I make an exception for tires, fuses and light bulbs, however most car designers seem  to forget, that you have to change the bulbs at night in the rain on the shoulder of a very busy motorway :) )

---

### Post by Dutch70 on 2011-04-22
Again, you miss the point, so I'll say it again. You do not have to learn or use the terminal if you don't want to. It just makes it easier to give/receive support. It doesn't make much sense to complain just because you can use it, or just because it's there.

Speaking of cars, pay particular attention to "Subproblem #3b: New vs. Old" in this thread.
[[COLOR="RoyalBlue"]http://linux.oneandoneis2.org/LNW.htm[/COLOR]]("http://linux.oneandoneis2.org/LNW.htm")

No one is trying to convince you, just trying to help you understand. I think we understand you clearly & I'm not knocking you for the way you think or want to use your computer. I've got a good video for you too, all in good fun. :)
[[COLOR="RoyalBlue"]http://ubergeek.tv/article.php?pid=54[/COLOR]]("http://ubergeek.tv/article.php?pid=54")

---

### Post by rewyllys on 2011-04-22
> **mrob184 said:**
> . . . .I'll be honest, I would much rather sit in the drivers seat useing the steering wheel and gas pedal to drive to the store rather than sit in the engine compartment working the throttlebody by hand to gas it and pulling and tugging on the tierods to steer it.:P
That is what command line is like for me, driveing a car in the engine compartment.
To me, what the command line is like, is driving with a gear shift lever rather than an automatic transmission.  When you drive using a gear shift lever, YOU can exert much more precise control over your car.
> I understand that command line is faster and very easy to alot of people. But not if you do not understand it, infact it takes way longer. . . .It won't take "way longer" if people tell you what commands to issue, and you simply copy-and-paste them into the command line--which is how most advice that involves the command line is intended to be handled.  As to understanding the command-line commands, you'll find that that comes in time, especially if you look up (e.g., by Googling) what the commands mean.

---

### Post by BertN45 on 2011-04-22
> **Dutch70 said:**
> Again, you miss the point, so I'll say it again. You do not have to learn or use the terminal if you don't want to. It just makes it easier to give/receive support. It doesn't make much sense to complain just because you can use it, or just because it's there.

Speaking of cars, pay particular attention to "Subproblem #3b: New vs. Old" in this thread.
[[COLOR=RoyalBlue]http://linux.oneandoneis2.org/LNW.htm[/COLOR]]("http://linux.oneandoneis2.org/LNW.htm")

I still sense some old echoes from the past, when we joked: "It has been hard to write, so it will be hard to use" :smile: .

I always think about some people in my family and the problems they have with their PCs. So if I make a reply to non IT people. I always explain, how to do it using the Gui. It is not really difficult and only a little bit more work. You are right, using the CLI makes it is easier to give support,  it is easier to receive support for IT people or PC hobbyists, but for many of the new users it is just Chinese.

I did read your story some days ago and it is probably valid for most distributions, but for Ubuntu the slogan is:  "Linux for human beings". I think they mean all human beings, also people who have another hobby as computers and don't want to learn Chinese.

If the community wants Ubuntu to grow and used by many more people, some change in culture will be needed, especially when dealing with beginners.

---

### Post by mrob184 on 2011-04-23
> **BertN45 said:**
> I still sense some old echoes from the past, when we joked: "It has been hard to write, so it will be hard to use" :smile: .

I always think about some people in my family and the problems they have with their PCs. So if I make a reply to non IT people. I always explain, how to do it using the Gui. It is not really difficult and only a little bit more work. You are right, using the CLI makes it is easier to give support,  it is easier to receive support for IT people or PC hobbyists, but for many of the new users it is just Chinese.

I did read your story some days ago and it is probably valid for most distributions, but for Ubuntu the slogan is:  "Linux for human beings". I think they mean all human beings, also people who have another hobby as computers and don't want to learn Chinese.

If the community wants Ubuntu to grow and used by many more people, a change in culture will be needed, especially when dealing with beginners.

Bert I like you...you get it dude!
Not that I do'nt like the rest of you because I do. We are all talking and being civil to one another...a rare thing in the world today.
This thread has ended up demostrating the one iratating thing about Linux and that is the geekyness of it.
Myself just like maybe thousands of other people in the world are now trying Linux because of Ubuntu and Gnome. These 2 distro's are the sole reason for people that would not ever try Linux at all, are finally jumping into the Linux pool and splashing around.
Can we all just acknowledge that While that as great as these 2 distro's are they need just a touch more polish? Just a touch?
I do not think anybody thinks it should be 100% perfect....I know I do'nt.
With all of the great things that have come along with Linux's development in the last 5 years or so such as programs and applications why is it that noone has written some software that can take care of these issues with a GUI? I mean Conical is doing it. The person that does that will go down in history as the person that singlehandedly converted more people to Linux than anybody else.
I wish I knew how to do it myself because I would. Problem is I do'nt have that long left in my life.

---

### Post by BertN45 on 2011-04-23
> **rewyllys said:**
> To me, what the command line is like, is driving with a gear shift lever rather than an automatic transmission.  When you drive using a gear shift lever, YOU can exert much more precise control over your car.
It won't take "way longer" if people tell you what commands to issue, and you simply copy-and-paste them into the command line--which is how most advice that involves the command line is intended to be handled.  As to understanding the command-line commands, you'll find that that comes in time, especially if you look up (e.g., by Googling) what the commands mean.

I always used a gear shift lever back in Europe, but now I enjoy using the automatic transmission here. It is easier and safer for the average person, who does not aspire to be a  rally driver.

"As to understanding the command-line commands, you'll find that that comes in time". Well maybe it comes as a surprise to you, but many persons do not want to spend that time. They have other interesting things to do, for them the PC is just a tool.

---

### Post by mrob184 on 2011-04-23
> **Dutch70 said:**
> Again, you miss the point, so I'll say it again. You do not have to learn or use the terminal if you don't want to. It just makes it easier to give/receive support. It doesn't make much sense to complain just because you can use it, or just because it's there.

Speaking of cars, pay particular attention to "Subproblem #3b: New vs. Old" in this thread.
[[COLOR=RoyalBlue]http://linux.oneandoneis2.org/LNW.htm[/COLOR]]("http://linux.oneandoneis2.org/LNW.htm")

No one is trying to convince you, just trying to help you understand. I think we understand you clearly & I'm not knocking you for the way you think or want to use your computer. I've got a good video for you too, all in good fun. :)
[[COLOR=RoyalBlue]http://ubergeek.tv/article.php?pid=54[/COLOR]]("http://ubergeek.tv/article.php?pid=54")

Dutch that video is funny as hell man, and its so true.LOL.
The artical...well I disagree with several things in it.
 
Hey while I have your attention could you give me a hand with a sound problem that I have with the new install I just put on my desktop? An example of the problem would be I just watched the vid that you linked and I closed the link to get back here and the sound starts makeing this loud BRRRRRRRRRRRRRR sound for several seconds before it stops. I'm also haveing a poping and clicking sound when I try to play any audio except the audio in that vid did not do it. Vid audio just made that BRRRRRRRRRRRR sound when I shut it off. Strange.

---

### Post by Dutch70 on 2011-04-23
Hahaa, I'd just ask for a refund!!! 

Seriously though, I'm not that knowledgeable about Linux, or computers in general tbh. 

Maybe one of these days you will be more inclined to work with Linux & appreciate the freedom it gives you. I think it would be nice to have you around if you had more time to spend.


Start a new thread with your sound problem. I don't know much, but I'm more interested in learning Linux than that other OS.

 ps. [[COLOR="RoyalBlue"]http://en.wiktionary.org/wiki/STFW[/COLOR]]("http://en.wiktionary.org/wiki/STFW")

And don't forget Nixie...
[[COLOR="RoyalBlue"]http://www.youtube.com/profile?annotation_id=annotation_201431&user=NixiePixel&feature=iv#p/u/2/NtQH0lpKKhU[/COLOR]]("http://www.youtube.com/profile?annotation_id=annotation_201431&user=NixiePixel&feature=iv#p/u/2/NtQH0lpKKhU")

Damn, I love her...lol.

---

### Post by mrob184 on 2011-04-23
> **Dutch70 said:**
> Hahaa, I'd just ask for a refund!!! 

Seriously though, I'm not that knowledgeable about Linux, or computers in general tbh. 

Maybe one of these days you will be more inclined to work with Linux & appreciate the freedom it gives you. I think it would be nice to have you around if you had more time to spend.


Start a new thread with your sound problem. I don't know much, but I'm more interested in learning Linux than that other OS.

 ps. [[COLOR=RoyalBlue]http://en.wiktionary.org/wiki/STFW[/COLOR]]("http://en.wiktionary.org/wiki/STFW")

And don't forget Nixie...
[[COLOR=RoyalBlue]http://www.youtube.com/profile?annotation_id=annotation_201431&user=NixiePixel&feature=iv#p/u/2/NtQH0lpKKhU[/COLOR]]("http://www.youtube.com/profile?annotation_id=annotation_201431&user=NixiePixel&feature=iv#p/u/2/NtQH0lpKKhU")

Damn, I love her...lol.
LOL!!!!!!
Hey man I'm trying....hell I've got a new attitude today. I figure I'll play and tinker with (yes even in command line) and see what happens. Should I break it oh well I can reinstall and start over.....hey maybe I'll learn something.
My new thread is started and I promise no more complaining about command line. I'll try anything suggested.:D:D

---

### Post by Dutch70 on 2011-04-23
Sweet!!! ;)

It's amazing what Nixie will do for ya huh?
A female, hillbilly linux power user, how can you not love that???  

Ubuntu doesn't need much space & your always one click away from windows. Hate that it doesn't work well with your hardware though, That is something I'll consider when I buy my next system. Hopefully the suppliers will get it right soon.

---

### Post by K_45 on 2011-04-23
Here is a tip, if you really want to learn, force yourself to use the command line for some tasks. I started by using a text editor in the terminal (vim) rather than mousepad, and instead of xarchiver, I used the command line to extract and copy files.

---

### Post by jramshu on 2011-04-23
I am in the process of learning the commands, there are a lot of them. When I first started it was pretty intimidating I must say. The commands weren't so bad, it was the 'flags,' 'options' that threw me off. I went and got a book that has a really good list of commands, the various flags that go with them, and a good explanation on what they do. I still come here to see what the experienced say about how to fix things. 

I use the command line as much and often as I can. I also have an Ubuntu Server with no GUI, so it becomes a necessity to learn commands. By learning a few simple commands you can amaze your friends too. LOL!!!!!!! 

You don't have to learn the command terminal, but if you want to fix things faster it sure helps. 

Just my opinion.

---

