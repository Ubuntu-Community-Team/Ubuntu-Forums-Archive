---
title: "Since v9. I'm still finding it hard to use Ubuntu"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by LFX64 on 2011-05-23
I remember years back trying Ubuntu 9 on an ancient PC. The reason primarily being that the PC was far too slow and too low on RAM to be of any real use. Sadly, I was using wireless back then and it was a complete an utter nightmate. Eventually, I gave up.

I tried Xubuntu and Kubuntu, as well as Puppy Linux and some other... version. No difference.

I've had Windows 7 Home Premium (OEM) 64 bit since October 2009 (after using Vista for 2 months). It's pretty good, but I like to explore changes because to be honest, Windows 7 lacks some things I'd call basic, such as more in-depth theme controls, better right click functionality with Aero Peek, better support for video formats, a decent media player (WMP12 is awful), etc. It definitely seems as if they have purposly limited the visual design element for future versions. I also dislike how icons on the taskbar must be left justified.

Very early this morning, I installed Linux via wubi, on Windows 7. Surprinsingly easy I thought, very nice. Chose Ubuntu, 30GB installation, an away we go. Booted up Ubuntu and I was a little disappointed with the huge moave (?) coloured screen. When I got past that and onto the actual desktop, I *sort* of liked what I saw. The interface of prior versions was better, but this was still pleasing to the eye. I was happy that it was more user friendly than other older versions of Ubuntu and surprisingly enough my Belkin Wireless N network adapter worked --for a short while-- and I managed to download updates.

What I disliked about Linux in the past was that, as a Windows user for many years, I was not fond of command promts. I hate them, very much, but I dislike the way Windows handles some things as well, an I've actually been wanting to use Linux for a few years. Sadly, after downloading the updates, the system gradually slowed down and things started to lack response. Clicking on things took over 60 seconds to open, but many more things would frequently freeze. Restarting, changing settings, etc made no difference.

Support for wireless it seems hasn't improved as much as I'd hoped. As one person put it, until Linux has the ability to support a wide variety of hardware (wireless hardware especially), an allows one to wander into *any* coffee shop and surf the web, then Linux will trail behind. That being said, I can't connect to the Internet wirelessly. I can't download drivers for my video card either, which is a shame. It really did look promising, that it was becoming a much more friendly experience. I understand many Linux users like the technical aspect, but why can't it be both?

The main things to point out is Wireless not working at all well and requires driver downloads or command promts to successfully work, which cannot be done unless you have another OS, an ethernet cable or the drivers on a USB flash drive. This is somewhat inconvenient --not as much for me since I possess that but it's still a hassle for beginners or those who just want things to work straight off the bat. The other main problem is performance, which is extremely poor and is undoubtedly, the most important thing for any OS these days.

My system specs are as follows:
ASUS Crosshair III Formula Motherboard - bios 1105
AMD Phenom II X4 955BE @ 3.2Ghz - Quad Core AM3 (C2 Stepping / 125watt TDP)
Xigmatek Dark Knight S1283V - Exhausting Vertically - MX-4 TIM
4GB Corsair Dominator 1600Mhz DDR3 RAM @ 1333Mhz
1GB XFX Radeon HD 4870 GDDR5 (Stock Cooling)
52-in-1 Media Card Reader
LG DVD-RAM/DVD-CD Reader/Re-Writer/
**Belkin F5D8053UK Wireless N USB Adapter**
Hitachi Desktop 7,200RPM S-ATA 500GB HDD (465GB via OS Read)
1010Watt FSP Modular PSU

My intention was to dual boot, because I don't want to part with my Windows roots, mostly because I've spent a lot of money investing in Windows stuff, buying games, other programs and the OS itself. Of course it also makes very good use of my Quad Processor and my Direct-X 10 Video card.

After Googlin' around, I noticed that many people were complaining of very similar performance issues. Generally very slow. I have no doubt some of you are fortunate enough to experience it on a somewhat faster scale?

Does Ubuntu make use of Quad Cores? When I downloaded the package (iso) via wubi, it said for AMD64, which is good, but I thought it best to share. Any ideas roughly as to when the speed issue will be fixed up? It seems rather common.

Aside from that I'm glad I've installed it and that I've registered here. My only hope now is the issues I'm currently having improve quite a bit.

Thanks.

---

### Post by LFX64 on 2011-05-23
According to this : [http://linux-wless.passys.nl/query_part.php?brandname=Belkin](http://linux-wless.passys.nl/query_part.php?brandname=Belkin)

My USB Belkin device (v3000x) is not even there.

Not cool :(

---

### Post by LFX64 on 2011-05-23
Is version 3000 of the wireless adapter going to see any sort of support for Linux? Or will I need abandon it again until future versions?

Peace

---

### Post by beew on 2011-05-23
Well it seems that your experience of Ubuntu is either installing it on an old crappy machine that windows probably wouldn't work  at all or installing it with WUBI which is a kind of diminished version living in  Windows so what to you expect? Since you always give your best resources and operating environment to WIndows it isn't a surprise that you find more problems with Ubuntu.

I can say that 11.04 is the most buggy release I experience so far but even that performs well on all machines I test on. I boot it off an external hard disk on a laptop with VIsta and it works much better than Vista even in this relatively early day of release.

For all my Ubuntu installs (10.04, 10.10, 11.04)WIFI either works out of the box or after installing proprietary driver(broadcom) I have a dual boot between XP and Ubutu 10.10,--I need windows for one program for work,-- and wifi works much better in Ubuntu than in XP, most of the time I can't even connect in XP (athero wifi card)

---

### Post by LFX64 on 2011-05-23
I was under the impression that wubi did something for partitioning, because each time I boot up I get the Windows boot menu, allowing me to pick Windows 7 or Ubuntu. I didn't know it physically ran through it. I didn't see any Windows-like surroundings to suggest I was running in Windows.

What did I expect? A more friendly approach and some helpful advice would have been nice.

Can a mod delete this account and all the private-data with it, since I won't be needing it.

Peace

---

### Post by sanderd17 on 2011-05-23
Problems with hardware are sometimes a real pain and difficult to solve. And Wubi is not that bad (it runs Ubuntu on a cripled virtual hdd, but doesn't take other resources).

But it seems that you have some problems of your own. Why don't you like the CLI? Say I have a lot of files in a directory, and I need to copy the ones which end on "01" but with all possible extensions. It's easy when you know the CLI:

```

cp *01.* /path/where/they/should/go

```

So maybe it would be good if you tried to learn the CLI. Here is a great tutorial for it: [http://linuxcommand.org/](http://linuxcommand.org/)

It's explained clearly in a few pages. Maybe, if you start to like the CLI, you will be able to set up your wireless card.

And for the record: 11.04 is a quite bad release. Try 10.04 (LTS) or 10.10, those were fantastic releases.

---

### Post by jerome1232 on 2011-05-23
I believe some of your problems come from just being more familiar with Windows than Ubuntu.

I'm personally am the opposite and I have alot more issues with getting things to work correctly in Windows than I do in Ubuntu. 

Did you have a specific support question, I don't think I really gleaned what your asking about out of that rather large post.

If your wireless card isn't supported well then there's not much you can do except go wired or purchase one better supported by Ubuntu.

---

### Post by Paqman on 2011-05-23
> **LFX64 said:**
> I was under the impression that wubi did something for partitioning, because each time I boot up I get the Windows boot menu, allowing me to pick Windows 7 or Ubuntu. I didn't know it physically ran through it. I didn't see any Windows-like surroundings to suggest I was running in Windows.


What Wubi does is install the system into a virtual partition that's located on your Windows NTFS partition. When you boot into Ubuntu Windows is not running, although Ubuntu is running off the same part of the disk as Windows does. It's a clever bit of trickery that removes the need to partition your drive.

As for your wifi woes, the best thing to do is hook up an ethernet cable and open the Additional Drivers tool. Hopefully that will allow you to download and install the driver you require.

Extreme slowness of the interface could be due to you not having your graphics drivers installed. Additional Drivers should be able to help you out there, although AMD cards can be troublesome (most experienced Linux users stick to Nvidia as they're traditionally better supported). Until you get your GPU running as it should you could try opening the Appearance tool and turning all the desktop effects off, which should give you a much more responsive desktop.

Hopefully you'll be able to sort all this out without having to touch the command line, which is the way it should be.

---

### Post by Mark Phelps on 2011-05-24
While I'm personally not a fan of Wubi, to give it credit, it does perform nearly as well as a separate install.  You really should not notice any slowdown simply due to a Wubi install.

I'm not using 11.04 myself because (1) I have a strong dislike for Unity, and (2) have read are unhappy with it, my suggestion is to remove it and install 10.10 instead.

As to the performance degradation, yeah, I've been reading about that as well.  I've been installing and upgrading Ubuntu versions since 7.04 -- and have only been seeing reports on this kind of performance degradation with 11.04 (maybe that's a THIRD reason to not install it).

As to the wireless drivers, as already mentioned, you'll need to use the same approach as you would in MS Windows -- connect via wired ethernet cable and get the drivers that way.

---

### Post by LFX64 on 2011-05-26
Hmmm. Shame that. An ethernet having to trail across my room because Wireless doesn't work. I figured the video card not having it's drivers installed may cause a problem, but it's a shame there aren't any drivers already pre-loaded to take advantage of it.

As for those saying that me being used to Windows is the reason I am not for Ubuntu, is true. But as I've pointed out to others way back, when using Version 9, the majority of people don't use Linux because they wan't to avoid putting in a load of code.

Point + Click beats

/sda /blah /blah /blah

Tutorial of code, to revise and remember Vs ease of use? Anybodying seeing what I'm getting at?

I really like open source software, but if it's monumentally hard to use, then what's the point?

Say for example there was no tutorial. How then would you know all the mumbo-jumbo to install a package?

It seems very counter-productive. It is an awful shame there aren't drivers for my wireless device too. :(

I think I might leave it until Version 43, when Linux has evolved enough to be more friendly for those who don't have a PhD in computer science.

Thanks for your help.

---

### Post by jerome1232 on 2011-05-26
While I'll admit not all of our gui's are the prettiest, we pretty much have gui's for every task that needs to be done.
The command line tends to get used in tutorials due to that fact that it's 10x easier to say copy and paste the next 10 lines than it is to give a point and click description for 20 buttons.

I also dare you to try and get a bare self installed version of Windows up and running on supported hardware as easily or quickly as getting Ubuntu running on supported hardware.

All of that aside, every one likes different OS's for different reasons. That's what we call choice and I'm glad we have that. There are things I miss about Windows when using Ubuntu and there are things I miss about Ubuntu when using Windows. I hope you have better luck with future versions as Ubuntu is always improving!

---

### Post by Mark Phelps on 2011-05-26
> **LFX64 said:**
> Hmmm. Shame that. An ethernet having to trail across my room because Wireless doesn't work. I figured the video card not having it's drivers installed may cause a problem, but it's a shame there aren't any drivers already pre-loaded to take advantage of it.
Only mean to use a wired connection to be able to download the drivers you need.  Once they are installed, you would then be able to remove the wired connection and go wireless.

> As for those saying that me being used to Windows is the reason I am not for Ubuntu, is true. But as I've pointed out to others way back, when using Version 9, the majority of people don't use Linux because they wan't to avoid putting in a load of code.

Point + Click beats

/sda /blah /blah /blah
Except ... that you now generally only need to resort to terminal commands to fix setup or config problems.  And, in all fairness, you sometimes have to resort to the Safe Mode with Command Line situation in MS Windows -- to fix setup or config problems.

For routine daily use, you should not have to resort to using the terminal.

> Tutorial of code, to revise and remember Vs ease of use? Anybodying seeing what I'm getting at?
Yeah ... we ALL see what you're getting at ... and while the Linux community is working HARD to build GUI's for doing everything routinely, there's liable to always be some setup/config/diagnostic stuff that either only works in the terminal mode, or works better in the terminal mode.

> I really like open source software, but if it's monumentally hard to use, then what's the point?
I don't see how having to enter a handful of commands, and only then during setup/config/diagnostic work, is making Linux "monumentally" hard to use.

> Say for example there was no tutorial. How then would you know all the mumbo-jumbo to install a package?
Easy -- you don't!  Use the Software Center -- that's what it's for.  If you resort to using source code, then you are forcing the difficulties on yourself through your choice.

> It seems very counter-productive. It is an awful shame there aren't drivers for my wireless device too. :(
Lack of hardware drivers, while really a hardware vendor problem, is the bane of Linux distros in general.  Until more hardware vendors decide to step up to supporting Linux in general, unfortunately, that's a problem that's not going to get any better.

> I think I might leave it until Version 43, when Linux has evolved enough to be more friendly for those who don't have a PhD in computer science.

I don't have a PhD in Computer Science and find it quite easy to use ... but if you're waiting until you NEVER have to use the terminal to do setup/config/diagnostic work and/or hardware vendors will provide Linux drivers for ALL the stuff they sell -- Version "43" is probably going to be too soon for that.

---

### Post by Anuovis on 2011-05-26
You are wrong about command line interface.

For one, it is not required to install or use Ubuntu at all. You can add and remove software via Ubuntu Software Center (friendlier than Windows setups and Add/Removes...). All applications you need probably have graphical interfaces for daily use. All relevant system settings can also be reached with point-and-click.

I was a Windows user for around 10 years and still know next to nothing about the command line. I have been using Ubuntu daily for a past few years and feel no need to get back to Windows. And while we are at it, the graphical interface is probably better in Ubuntu as well, I found it much more customizable and intuitive.

If you need to do some advanced tasks you are not familiar with, usually it's just copy-pasting something you find on the forums. Granted, it may feel weird when you don't know what you are inputting but there is code under every graphical button as well, you just don't see it.

Another thing is that command line is really a handy tool **if** you want to use it. It is powerful, fast and sometimes better than graphics. The few commands I know come in handy. But again, it is not necessary any more to master it.

And you are right about hardware. Some things are not that well supported or need tweaking. But Ubuntu supports a lot of things extremely well, I have some devices that run better here than on my Windows XP. It really depends and is often fixable.

---

### Post by lightstream on 2011-05-26
Personally I think it only confuses the matter to compare everything to Windows.

People - especially those who are not computer savvy - can have problems installing and configuring hardware and software, and this is true regardless of what OS they use.

I have friends who really know very little about computers, and constantly encounter problems like this.

What I do find very strange is that when they encounter the problem on Windows, they blame the hardware/software that they are trying to install, but when they encounter a similar problem on Linux, they would blame Linux.

I don't really understand how that situation has come about but I would love to know how come Windows is so rarely held responsible by these sorts of people.

---

### Post by sanderd17 on 2011-05-26
> **jerome1232 said:**
> While I'll admit not all of our gui's are the prettiest, we pretty much have gui's for every task that needs to be done.
The command line tends to get used in tutorials due to that fact that it's 10x easier to say copy and paste the next 10 lines than it is to give a point and click description for 20 buttons.


100% true. Imagine that you have to take screenshots of every button you have to click. And every release, the UI changes, so all that work would be worthless. 

copy-paste ready code is the best for tutorials, and I was able to set up 10.10 on my computer without command line at all (but I did use the CLI for copying some music files). 11.04 worked also without touching the commandline, but I needed to go back to the CLI when Unity did some weird things.

---

### Post by uRock on 2011-05-26
You may want to start a new thread stating your wireless problem and the wireless problem only. Include what you have and haven't tried, as well as the output of lspci(run in terminal), which will tell us the chipset of the USB. :P

One of the most important things to keep out of a thread is personal feelings. Quite often folks reply with their own personal feelings/opinions instead of replying to the facts of the problem. This is just human nature.

There are a lot of bright folks here who can help with your Ubuntu problems.

Regards,
uRock

PS, If you decide to start a new thread, then please PM me and I will close this thread.:)

---

### Post by wildmanne39 on 2011-05-26
Hi, I agree with about everything that was said here, it is not ubuntu's fault the the people that make wireless cards and such only provide drivers for windows,and ubuntu people work very hard to backwards engineer drivers for hardware that does not have a driver provided for by the vendor, so really a big thank you is in order.

---

### Post by LFX64 on 2011-05-26
Whilst I like Ubuntu, it is extremely extremely rare to have to use Safe Mode. In years of using Windows, I've only ever had to use Safe Mode once. Of the several times I've used/tried Ubuntu, I've had people tell me to use commands.

The reason people blame Linux is because it is, no offense to those who adore it, but these things are naturally compatible with Windows, not Linux, an unless a driver has been released for it, you either have to use your hardware in a lower state without all its features, or not at all. Unless of course, you're very fortunate and there is drivers. Sadly, I have no drivers for my wireless N USB adapter.

I agree, since using Ubuntu 9, I've not needed the CLI at all, but I have been told since installing 11.04, "type in these", which is usually the first piece of advice a Linux junkie gives someone from a Windows background, who has barely used it.

I already know about the software centre, I've used similar things on older versions of Ubuntu, but at some point or another, if I go to a website for example which says it's available for Linux, and I check the package thing and notice it isn't there, then I'm sort of screwed. It'll usually say you must install this and that first, an then install this through that to get this running. Highly inconvenient and will inevitably end up requiring the use of the CLI. The software in question was OpenHardwareMonitor by the way, when I'd managed to maintain a connection for a very short while, before never being able to get it back.

Mark, regarding wireless. If there are no drivers available I'd rather not go through using 54mbps mode through ndiswrapper, when installing whatever I need via Ethernet. The problem is, no driver exists for proper functionality on my adapter, therefore I will always have connectivity problems until I either change to a more popular device, get an adapter which has support for ubuntu, or continue to use an Ethernet cable - which I'd rather not since I'd prefer to have that on the PS3.

I do want to use Ubuntu, it's always been the first place I've gone to for Linux distros, specially the first time, after reading up about it, but the main problem at the moment which has always been the number one problem, is wireless support. :(

Would really like to have a solid (as solid as Windows) connection to my router between the usual 150-300mbps transfer rate, sadly that's unlikely to happen.

If I do manage to get round problems, I'll have to properly partition my drive and Install Ubuntu properly, unless of course the performance is as slow as it was before.

Peace, n thanks for the help.

---

### Post by Allavona on 2011-05-26
Your wireless N USB adapter more than likely uses the Ralink Chipset. Most likely the 2870 or 3070 series. I would say the 2870 is probably it, try it first.

Both drivers from Ralink are here:

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

I think these are self installing after making the file an executable. Right click, properties, permissions, and you see the check box.

---

### Post by pablo180 on 2011-05-26
I'm certainly not an expert, but surely if your Wireless adapter was working at some point on Ubuntu, then there are drivers?

You don't seem to be getting much help, so I had a quick search. Apparently, [according to this post]("http://ubuntuforums.org/showpost.php?p=9231093&postcount=3"), you most likely have the drivers on your system (I have them), which is why it most likely worked in the first place, and so won't need to download or hunt around for them. The instructions in that post do involve using the command line, but it is literally just copy and paste once you open a terminal (CTRL + ALT + T, or Applications > Terminal), and only needs to be done once. 

Regarding your speed issues, no, that is not normal, I can't speak for 11.04 but on 10.04 Ubuntu is very fast. Once you have the internet up and running you'll perhaps want to try and update your card's drivers too, firstly be going to System > Administration > Hardware Drivers (on 11.04 you should just be able to search for Hardware Drivers) with any luck that should pick up some drivers and sort out your problems. If not, as someone else said go to Appearance > Visual Effect > None to turn off effects for the time being.

---

### Post by LFX64 on 2011-05-28
I was actually thinking about the chipset for the wireless the other day, since some of them use the same one, which is, as you say, probably why it worked in the first place.

I'll keep Ubuntu 11.04 on my Windows partition to get practice. When I finally get awesome enough to use Ubuntu frequently, I'll make proper partitions for Windows 7 64 and Ubuntu. Unfortunately, I'll probably have to call up Microsoft because I've installed Windows 7 Home Premium 64 several times already, but that's if I ever get round to another fresh install. I do like fresh installs.

I'll go turn visual effects off soon, try to get wireless working and then download the additional drivers for my 1GB XFX Radeon HD 4870. Hopefully it'll allow me to properly use all the available effects without any slow down.

Grand Prix Qualifying first... it's almost finished ;)

Thanks again. I'll check back.

---

### Post by LFX64 on 2011-05-28
OK, so I'm writing this from Ubuntu 11.04 via Wubi on my Windows partition, which will remain that way until I'm convinced it's a common dual boot option deserving of it's own partition. Since attaching the Ethernet cable and installing the "additional drivers" for my video card, the GPU fan got noticably quieter, which means there isn't as much GPU strain or at least, better fan control. Performance has been improved as a result.

Wireless, is still awful, an similarly may briefly - but rarely - connect and then disconnect. Clicking disconnect doesn't actually work after it requests the authentication required to connect, which is silly. The same thing happens since v9 whereby I look at my wireless adapter and the light is just clean off, looking as if it's dead.

Java applets do not work according to the System Testing, even though I went into the Ubuntu Software Centre and downloaded a Java update (I checked the date).

Some things insist they are still being used once canceled. System test in particular, because I'd rather not use Empathy (yet) to access my Facebook (I'm very cautious of these things, even though I know of Linux's good security/privacy). When I go into System Monitor and look for the process which is apparently running, I cannot find the process, according to Linux, is still running and requires me to close it before I can open another one.

Power management? How is it for CPU? Does it have the ability to downclock my 3.2Ghz Quad (955BE C2/125w TDP)?

DVD playback doesn't appear to work, but I'll retry.

Currently using 1680x1050, an like Windows, some programs have tiny text, which is of course not an issue with the OS but simply the program. I changed the minimum font size to 12 in Firefox which will hopefully be good for all pages/instances. I thought I needed to hold down alt, turns out I don't. Just running the cursor above the top works lol. Still working it all out. Unusual approach to displaying the menu, but that's okay. Still have some problems with zoom in Firefox though.

Quite enjoyable at the moment, as it has been in the past, but hopefully I can get many Java applets to run flawlessly, as well as allowing for DVD playback. My top priority is getting my usual 120-150-180-300mbps (varies of course) wireless transfer rates, so I can put this Ethernet cable back in my PS3. I could run the PS3 via wireless G, but I hate being a money waster, which is why I want to use my wireless N adapter, an continue to use Windows 7.

I'd like to get all necessary updates for good functionality of Java, Flash, Audio, Video, and wireless functionality so I don't have to keep changing between wireless and wired. Once it's sorted, I'd like to be able to just leave the wireless adapter in and have my PS3 use Ethernet.

According to Ubuntu and Firefox, I am American. Hate to annoy folks, but English is English, therefore I would appreciate a Great British English language. Does Ubuntu have one, does Firefox? I know Firefox has awful language support for proper English on the Windows version, so I guess it is the same here? I thought I'd picked English UK for Ubuntu, unless I am mistaken and has somehow imagined it lol. :)

Thanks again for the help, I'd appreciate it if folks could continue to help.

I'll check back.

---

### Post by LFX64 on 2011-05-28
Downloaded VLC, tried to play the DVD but unfortunately it doesn't work. Clicking on English to start the film in that language simply stops it but with Totem it just freezes instead.

Wireless doesn't work. I just reconnected my wireless adapter, an it took about 60 seconds to ask for my WPA/WPA2 encryption key, which is usually how long it takes. It then simply does the flashy bar thing, indicating that it is trying to connect, but with the LED indicator being totally off on the adapter itself. Fortunately it disconnects most of the time when I tell it to. Wireless still not an option, even if it runs on the same chip, I'm getting no where fast.

As for Java, complete nightmare. I've managed to install Flash and get Youtube working, which is always nice but Java is simply not going to work. I wanted to install the Minecraft client, because I did indeed buy that game earlier this year, but it's a jar file, an I have no idea how to deal with those in regards to Linux.

Xsensors doesn't work very good, it simply reported the stuff I wished to see before going dim/dark and then freezing. Clicking the X button simply said that it wasn't responding so I had to force quit.

I would appreciate some decent hardware monitoring software which can read my sensors and support my AMD K10 (Phenom II X4 955BE 3.2Ghz C2 Stepping / 125watt TDP) Quad Core CPU. It's always useful to have software just to see how things go each day.

Peace

---

### Post by jerome1232 on 2011-05-28
> **LFX64 said:**
> 
As for Java, complete nightmare. I've managed to install Flash and get Youtube working, which is always nice but Java is simply not going to work. I wanted to install the Minecraft client, because I did indeed buy that game earlier this year, but it's a jar file, an I have no idea how to deal with those in regards to Linux.


For java search synaptic for sun-java6-jre, install that, then you should be able to run the jar file by double clicking it. Actually you could install the package called ubuntu-restricted-extras and it will get you lots of goodies you need (like flash, java, mp3 playback, ms fonts and etc...)

For dvd playback you may need libdvdcss2 to decrypt them, add the medibuntu repository and install it. A guide can be found here

[http://medibuntu.org/repository.phpu](http://medibuntu.org/repository.phpu)
and install libdvdcss2, just search synaptic for it after adding their repo

note: They give you a copy and paste code to add their repo, it could be easily done via gui, but most tutorials will give you commandline instructions so they don't have to stay up to date with what the latest gui looks like.

---

### Post by pablo180 on 2011-05-28
I know what you mean about UK English, it's the first thing that I have to do on every OS too. It's pretty simple though, just to to System > Administration > Language Support (on 11.04 you may just be able to search for language support), on the list under language you should find English UK, just drag that to the top. On the next tab (Text) select English United Kingdom from the drop down menu at the top, you'll know it is done as your Deleted items bin becomes a Rubbish Bin. If your keyboard is working OK (i.e. symbols like " and @ are in the right place) you may want to leave it at that but if not then you will need to set up the keyboard. 

To set up the keyboard you apparently have to: Click the icon at the very right of the panel and select System Settings. In the Hardware section, click Keyboard. Switch to the Layouts tab. Click the Add button, select a layout, and click Add. Then select United Kingdom. You can also select the keyboard model as well. 

For Firefox you just need to go to there language page and download the UK (or British) language pack: [https://addons.mozilla.org/en-US/firefox/language-tools/]("https://addons.mozilla.org/en-US/firefox/language-tools/")

Stuff like DVD playback isn't included in Ubuntu out of the box. For DVD and MP3 etc you'll need to add the restricted extras as jerome1232 pointed out from [http://medibuntu.org/repository.php]("http://medibuntu.org/repository.php") you just literally open a terminal and copy that whole block into the terminal and press enter and it does all the rest. You'd then need to open Synaptic Package manager and install libdvdcss2 as jerome said. 

If you've installed Java you should just literally be able to right click on a jar file and select open with Sun Java 6 Runtime (or something like that. If Java isn't there, you'll have to install it as jerome said. 

For your wireless, open a terminal (I know you don't like the terminal, nor do I really, but for some things it is just faster) and paste the following code into it (CTRL+SHIFT+V):

```
sudo modprobe -l | grep rt28[67].*
```

Do you get the following back?

```

kernel/drivers/staging/rt2860/rt2860sta.ko
kernel/drivers/staging/rt2870/rt2870sta.ko
```

---

### Post by beew on 2011-05-28
> **jerome1232 said:**
> For java search synaptic for sun-java6-jre, install that, then you should be able to run the jar file by double clicking it.


OP has to enable the Canonical partners repo to install that, he should install sun-java6-plugin and it will then pull in other packages including jre. But Ubuntu by default uses openjdk, so to enable sun-java op would have to open the terminal and enter the command (@OP sorry, can't avoid the command line)
```

sudo update-java-alternatives -s java-6-sun
```

---

### Post by Swagman on 2011-05-28
> Say for example there was no tutorial. How then would you know all the mumbo-jumbo to install a package?

I have a question for you.

Can you remember the address that you consider you were born at ?

I'll lay a bet you can and you'll remember it till your dying day. It wont matter if that address has been bulldozed and is now called something else, you will still remember that address.

The same is for the install command here in Ubuntu, which is...

```
 **sudo apt-get install** *program name*
```

Only the program name will change. Of course, others will probably use dpkg. That's the beauty.. More than one way to skin a cat.. so to speak.

And.. As others have pointed out, You don't even need to use the CLI although it's **FAR** simpler to copy/paste any help commands into the CLI when people are helping you fix things rather than a wall of text with click this... click that etc.

As for multiple cores.... I'm running a Phenom II 965 (quad)

[img]http://img9.imageshack.us/img9/1843/ubuntu191.jpg[/img]

All cores are at 100% because I run Rosetta and Seti

---

### Post by jerome1232 on 2011-05-28
> **beew said:**
> OP has to enable the Canonical partners repo to install that, he should install sun-java6-plugin and it will then pull in other packages including jre. But Ubuntu by default uses openjdk, so to enable sun-java op would have to open the terminal and enter the command (@OP sorry, can't avoid the command line)
```

sudo update-java-alternatives -s java-6-sun
```

That's right I forgot! To do that in unity you would click the shutdown button, click system settings, click Synaptic Package Manager, Click settings, click repositories, put a check next to the cannonical partner repos as in my screenshot, click close, click reload. You should then be able to install sun-java6 and then run the update alternatives command.

In Ubuntu Classic it's similar but you goto System-Administration-Synaptic Package manager.

---

### Post by pablo180 on 2011-05-28
> **Swagman said:**
> 
The same is for the install command here in Ubuntu, which is...

```
 **sudo apt-get install** *program name*
```

Only the program name will change. Of course, others will probably use dpkg. That's the beauty.. More than one way to skin a cat.. so to speak.

I understand what you're saying, and why you think that it will help those new to Ubuntu, but I don't agree that the install command is all that useful, after all, that is the easy part - it's the EXACT package name of every package you wish to install, that you must know by heart. Easy enough with something like docky:

```
sudo apt-get install docky
```

Not so easy with Java

```
sudo apt-get install sun-java6-jre
```

New users should be encouraged to use, and get used to installing software via, the Software Centre and Synaptic. At least in Synaptic not only does it have a GUI, it also has a search and is much safer. 

For me the command line is something that should be avoided, unless absolutely necessary, and any commands just picked up along the way, rather than learned by heart. That said, I do sometimes use it myself, and I agree that it is invaluable on places like this for enabling people to solve problems by copying and pasting commands that they'd have no chance of knowing on their own and also far, far quicker.

---

### Post by LFX64 on 2011-05-29
I've installed the extras package, including the add ons one which  automatically selected that after I selected the Ubuntu extras. I've  copied and pasted the medibuntu repository stuff into the Terminal and  installed a bunch of things. I also did that crash report line and the  one to remove this "non free stuff".

An to whoever said it has to  be the EXACT name of the program is exactly right. I've always been  fine with using the terminal to install a program, so long as it wasn't  too complex, by typing in sudo apt-get blah blah monkey balls... the  only problem is, I don't know new programs which come out with funky  names. If it was as simple as "Java", then I'd of been done.

Downloading  the Minecraft.jar doesn't seem to work. If I try to open the jar with  Java 6 runtime it says a load of crap about how it isn't running and  then a lil something about an executable bit.

As for the wireless adapter, the codes you said came back as - 
kernel/drivers/staging/rt2860/rt2860sta.ko 
kernel/drivers/staging/rt2870/rt2870sta.ko

DVD playback works  now, although it is a little disappointing that Java, Flash and DVD  playback isn't supported out of the box. I understand Ubuntu are trying  to make things simpler and are helping those who are less savvy with the  CLI to use things such as the Software Centre, but to install Java and  actually get it running is a lot more hassle than it should be in my  opinion.

I have ran into a problem. Going to Minecraft's website  and trying to play the game in the browser, downloads Linux stuff  automatically, but has a grey screen with "applet started" in the bottom  right of the browser. Still not functional with websites.

I'm  also looking to securely erase Internet data, as I frequently check bank  statements online as well as making online purchases. I know this may  not be as necessary as it is within Windows, but I like to put my mind  at ease even if it is out of habit on Windows. I don't think Firefox's  clear-private-data is sufficient enough.

Ubuntu was already in  Great British English, which is good, but Firefox isn't. Quite annoying  when words want to immediately be replaced with z's or miss out u's. The  dictionaries for Firefox seem to suck, which has always been the case  since the localised versions are run by those naff libraries.

Again,  I'll use Ubuntu 11.04 through my Windows partition, which, since  authorising the proper drivers for my video card has increased  performance 10 fold, means it runs just as fast as if on it's own  partition, which is fantastic. This will allow me to get practice with  Ubuntu. I've bookmarked LinuxCommand.org, but it'll take me quite a  while to learn and re-learn everything.

It did say something about being root. It says you should never install as a superuser... whatever that is. Why?

Note:  not overly keen with window dragging, it's not fluid, likewise animated  bars for updates are not either. This isn't a slowdown, it's simply the  animation since I know my CPU and GPU are running well. The video card  is about as quiet as it is on Windows, meaning it's probably idling  around 64-65c which is normal for this card.

:D

Peace - GB English Linux should be called Rubbish Bin, not Wastebasket lol. ;)

---

### Post by LFX64 on 2011-05-29
Scrolling isn't smooth in Firefox, even though Smooth-Scrolling is enabled.

Video isn't smooth, through BBC iPlayer and other flash videos. Freezing in video can occur, including repeating of the same video section, whilst the audio continues, thus causing an out of sync issue.

Currently using wireless. Before I rebooted earlier, I noticed the wireless adapter was on... "odd" I thought, so I checked the Connection Information tab and noticed both were actually connected to the Internet. I disconnected the Ethernet cable and I was still online. Tried a speed test and [www.speedtest.net]("http://www.speedtest.net") - which is what I usually use - and it crept up to 9.88mbps but was incredibly slow to start, by the time it had finished it had dropped to 1.94mbps, my upload was quicker to start, an was about 1.03mbps, which is about right.

Wireless is still iffy, things are slower to load wirelessly. Looking up the address takes quite a while, page loading is significantly slower than Windows. Wireless transfer rate is around 108mbps-120-150mbps, which is pretty good.

Java still not working properly.

Logitech X-230 speakers not working overly well either. The min-sub included with it, doesn't produce any bass unless maxed whereby it is extremely quiet. The result is very flat audio. It's quite annoying. :(

---

### Post by LFX64 on 2011-05-29
Wireless disconnected whilst watching the same show on BBC iPlayer. Constant freezes in the video, rebuffering etc, connection held out for quite a while but eventually gave out. Back using Ethernet for the time being. At least it's a step up from 54mbps in Ubuntu 9 although I have just installed ndiswrapper to how it has evolved since then.

Retried Speedtest.net via Ethernet - results

9.74 Down
1.02 Up

Ping 26

Wireless N (hybrid mode b/g/n on router) on Windows 7:

typical ping 5ms

9.80+ Down
1.02+ Up

Similarity between Linux Wired and Windows Wireless, but the ping is a bit more, but that might just be to do with the speed of this browser, since it isn't as fast compared to FF4 on Windows 7.

Edit: Didn't realise that permissions had to be changed to run .jar files. Opened the program, seemed to work, didn't actually run Minecraft though because I don't have a world there, but I do on Windows :(, any way of getting that across? :(

As for flat audio, I know there wouldn't be any drivers for my sound card but I got the System Wide Pulse Audio Multiband Equaliser, which has helped. Audio is still naturally quieter both on the desktop and by audio/video sources as well as the bass being lower anyway, but this program definitely helps.

No paint.net for Ubuntu? If not, I'll stick with GIMP, even though I've never used it before. Sorry for the excessive posting, I'm just keeping people up to date with what I've managed to do and what I may need help with.

Edit 2: Using the circle, spinny volume thing on my Logitech 300 Media Keyboard shows the Ubuntu Volume Panel, which is good, causes a slight slow down with video playback (on DVD) and some skipping.



Peace

---

### Post by pablo180 on 2011-05-29
Ubuntu don't offer MP3, Flash, DVD playing etc by default because they are not open source. Whilst I understand their principles, I do agree that using a hobbled system, without a clear way for the user to install all that functionality, is a little silly and putting principles before users a tad naive. There should at least be a simple option in the menu to add such functionality, as with restricted drivers. 

It looks as though you do have the right drivers for your wireless then, but your system may not be set up to use them. If you enter the following into the terminal:

```
sudo lsmod | grep rt28*
```


Do you get 'rt2800usb' back?

Glad that you have Java working, you should just be able to copy your files from your Windows into a folder on Ubuntu for it to work. I've done similar things with Java programs in the past. Although I didn't agree with swagman about using the terminals commands to install things, he's right about learning some commands - the one I use most often is: 

```
gksudo nautilus
```

This opens the file explorer as root. You should be able to hit ALT+F2 and then type it there (if that still works on 11.04), or enter it into the terminal. You should then be able to copy and paste files from your Windows partition into Ubuntu and change permissions in the file explorer for files (Right Click > Properties > Permissions). 

For cleaning your internet history, there a program called [BleachBit]("http://bleachbit.sourceforge.net/download/linux"), I don't think it is in the repositories. But [you can download the .deb file here]("http://bleachbit.sourceforge.net/download/linux"). when you save it in Firefox you should have an option to open with GDebi Package Installer (if not save it, then Right Click and select it), then just follow the instructions. It's not normally good practice to just go around downloading and installing things from the net, but BleachBit is a good piece of software, clearing out more than just internet history and also allows the shredding of folders, and this is the only way to get it. 

Root and a superuser are basically the same as Administrator in Windows. In Windows, or at least in XP, all users were super users, so when they were infected a virus could basically do whatever it wanted to the system. In Ubuntu (and Linux in general) you're installed as a standard user and don't have access to system files, just in case, so an infection shouldn't be able to take over the whole machine. It basically just makes it safer. You should avoid being root or entering sudo into the command line (and use the above gksudo nautilus sparingly, e.g. when you need to move files, gain permissions etc). It is also why the password pops up all the time, it needs this to be allowed to install updates, software etc, so also helps protect you against yourself. 

Not sure about the sound. In 10.04 I know you can adjust the settings, select the output device, balance etc, but I think they have changed things around a bit on 11.04. [This may be of help, but you may already have set all of that up]("https://help.ubuntu.com/11.04/ubuntu-help/sound-volume.html"). 

The problems with video, drag and drop and stuttering sound like you still have a problem with your graphics drivers, have you tried turning off desktop effects to see if that makes a difference? If so, you still may not have the best drivers for your card.

---

### Post by el_koraco on 2011-05-29
> **LFX64 said:**
> 
Note:  not overly keen with window dragging, it's not fluid, likewise animated  bars for updates are not either. This isn't a slowdown, it's simply the  animation since I know my CPU and GPU are running well. 

Go to the "ATI Catalyst Control Center", and under Display Options, Tear Free Desktop, click to enable the tear-free feature. This should help some, but ATI cards and Linux are not the best of friends, so it's unlikely to be as smooth as in Windows.

---

### Post by el_koraco on 2011-05-29
With regard to video quality, first install the compizconfig-settings-manager. Just type "ccsm" in the Software Center. Then open it and go to the "OpenGL" tab. Find a checkboy next to "Sync to Vblank" and untick it. See if the video quality has improved. If it didn't, you need to try issuing a command

```
aticonfig --sync-video=off
```

---

### Post by LFX64 on 2011-05-29
rt2870sta             450556  0 
rt2800usb              18235  0 
rt2800lib              45181  1 rt2800usb
crc_ccitt              12667  2 rt2870sta,rt2800lib
rt2x00usb              20330  1 rt2800usb
rt2x00lib              49235  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              294370  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              178528  2 rt2x00lib,mac80211

That came back when I typed in the code you said.

In regards to the video card, the additional drivers are installed properly, it's not necessarily a slow down but dragging windows is not fluid. If ATI and Linux don't go well together then that is simply another reason not to use Linux. it's another non-user friendly situation. Nvidia is hugely expensive, partly because of the name I believe, so I don't understand why people insist on going for it all the time. :(

I know my graphic card isn't slow, if it is on Ubuntu then something is very wrong. That being said, I'd of thought tear-free would be V-sync,  an that it'd perform better with it off - which is as it is now.

Except for the brief moments today, where I've used Windows 7, I've pretty much used Ubuntu all day. I've got a webcam app, but yet to try it out. I'm also using Pidgin now, which is a bit iffy, but functional. The whole Ubuntu deal has not been as straight forward running as I'd of liked. Java should have definitely worked out of the box though, it seemed like an unnecessary hassle.

I know coming from a Windows background may alter my opinions on what I'd like to see in Ubuntu, but based on what I'm looking at now, with the side bar and some similar behavior between the two Operating Systems, if you click on an application and it opens, clicking on it should minimize it as well - which it doesn't do. It's counter productive opening it with a tab on the left and then having to go across the screen (depending on the window location of course) to minimise/close it off. If you want to briefly look at the window, click, then click again to open and hide, is a much faster, more efficient way of seeing relevant info. I thought I'd just point that out.

As for bar placement. I like it on the side, because Windows 7 handles it horribly. Although an auto-hide option for the right bar would of been nice. Small improvements for a bit more desktop space (specially for 1680x1050) and better productivity.


Thanks for the help folks.

Edit. I like this Evolution e-mail thing at the top right of the screen... rather handy for my Google Mail account. Much better than Gmail Notifier and the way it handles it. Nice to see the user friendly aspect too, putting in all the essential stuff for POP3 to work. However there is a problem, the mouse is out of sync on that particular piece of software. My cursor will have to be one option above the clicking point. Doesn't appear to happen anywhere else except there. So far...

---

### Post by el_koraco on 2011-05-29
> **LFX64 said:**
> If ATI and Linux don't go well together then that is simply another reason not to use Linux.

Well, don't use it then :D
You're never gonna get the same performance out of ATI in Linux as you're gonna get in Windows, so it's a take it or leave it. 

I gave you some options you can try. Btw, how do you know what the card temperature is in Linux?

---

### Post by wolfen69 on 2011-05-29
I know you may not want to hear this, but as a PC tech, and someone who has done countless installs of linux on many different machines, the reality is that some computers are very proprietary and will not run linux properly no matter what you try. They were made for windows. Period.

If you really want to use linux, I suggest buying one with linux preinstalled from a vendor such as System76 or Zareason. The hardware configurations offered by these companies have been thoroughly tested and are guaranteed to work well. This is all I can offer, good luck.

---

### Post by uRock on 2011-05-29
Asus is going to be selling systems with Ubuntu on then as well.

---

### Post by LFX64 on 2011-05-29
This PC cost me £916, after it had replacement upgrades from the vendor (not a crap one with a **** ton of third party software, but clean installs and picked parts from PC Specialist), but I'm not going to waste the value of this PC, the OS, the windows based software, the programs I paid for to specifically run on Windows etc.

I wasn't looking for something perfect, but I want to dual boot. Windows will be my primary and always will be, an Ubuntu (Linux) will always be my secondary, and it'll run when I fancy a change.

I realise some systems run better than others... I've always known that. All I was saying in regards to the video cards and Linux, is that if these folks want people to use their open source developments then they obviously need better support. I don't know who's more at fault, ATI/AMD's contribution to Linux functionality or Linux / Ubuntu for helping support it in their way, but I was simply stating what I think. I'm just saying that limitations will naturally make others think twice about their use. It doesn't mean to say that, OH NO, non-fluid window dragging, I must quit NOW or shell out £600 for an overpriced piece of kit lol. It's not a major problem, therefore it's not going to deter me from using this.

As for PulseAudio, it has added a bit of kick. The presets are awful but Techno seems to give the most natural sound. Bass is very heavy at times but it's nice to have more than none at all.

Cheese Webcam Booth doesn't seem to pick up my Logitech C510 720p Webcam. Other than that, everything apart from wireless seems to be ok. I turned wireless on, on my PS3. PC currently using Ethernet until I can be assed to deal with the problems.

Thanks folks.

---

### Post by wog on 2011-05-29
One reason Java isn't working right in Linux is because the version in the repositories is the previous version to the one available at the Sun site. If I knew how to install Sun Java from the files they give on the site I could tell you.

The minecraft world should be a straight copy from the "world" directory in your windows minecraft install to the directory minecraft creates for the saves in Linux.

On Windows, that directory is: 
"c:\Users\$USER\AppData\Roaming\.minecraft\saves\"

where $USER is your user name. It'll be named the same as when you select it within the minecraft client program.

In Linux the directory you'll be copying to is:
"/home/$USER/.minecraft/saves/"

I'd suggest you copy the world directory from windows to a thumb drive and then copy it from the thumb drive to your linux install.

Just so you know, the first character dot in the .minecraft name hides the directory in linux. In windows, it of course does nothing. To see the .minecraft directory in the graphical user interface (GUI), you may have to select "View >> Show Hidden Files". As soon as you get into the .minecraft directory in Linux, you might unselect that as it can be distracting.

Last but not least, you can create a shortcut to the .minecraft directory by clicking on the .minecraft directory (after selecting "Show Hidden Files") and drag it to the list of directories on the lower left side of the window, where it shows "Documents", "Music" and "Pictures".

If you have questions, be sure to ask for clarification.

---

### Post by pablo180 on 2011-05-29
> **LFX64 said:**
> rt2870sta             450556  0 
rt2800usb              18235  0 
rt2800lib              45181  1 rt2800usb
crc_ccitt              12667  2 rt2870sta,rt2800lib
rt2x00usb              20330  1 rt2800usb
rt2x00lib              49235  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              294370  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              178528  2 rt2x00lib,mac80211

That came back when I typed in the code you said.



Apparently that means that it is using the wrong driver, but it is easy to fix. 

Open a terminal and enter:

```
sudo gedit /etc/modprobe.d/blacklist.conf
```

That will open a file. Scroll down to the bottom of the file and create new line and add:

```
blacklist rt2800usb
```

Save the file, exit and restart. On the next boot it *should* use the right driver and sort out your wireless problem.

---

### Post by el_koraco on 2011-05-30
> **LFX64 said:**
>  use their open source developments then they obviously need better support. I don't know who's more at fault, ATI/AMD's contribution to Linux functionality or Linux / Ubuntu for helping support it in their way, but I was simply stating what I think. I'm just saying that limitations will naturally make others think twice about their use. It doesn't mean to say that, OH NO, non-fluid window dragging, I must quit NOW or shell out £600 for an overpriced piece of kit lol. It's not a major problem, therefore it's not going to deter me from using this.


It's a non-issue for the majority of users on Intel cards, which make what, 60-80 percent of the market, but that's beside the point, we can talk about it in the Cafe if you're so inclined. If you want, we can try to make your ATI card behave a little better, the Catalyst driver does have some options, but the Control Center sucks, so one has to resort to the command line, which has a lot more switches.

---

### Post by LFX64 on 2011-05-30
I forgot about the hidden folders. I didn't realise Linux did the same. Windows does, but that's with it's appfolder. 

Just tried the world I have on Windows. About 90-130fps. Stuttery as hell. I think I'll delete Minecraft and either play it in a browser, if and whenever Java works on Firefox, or leave it to Windows. People keep saying to others, get sun-java6-jre blah blah, yeah, that's all well and good when it is exists. Unfortunately I can't find that in any package manager, on the Internet or any sort of Firefox extensions! :(

As for the wireless thing...

(gedit:3374): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.H6JFWV': No such file or directory

(gedit:3374): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

That happened when I copied and pasted in what you told me.

:D

---

### Post by LFX64 on 2011-05-30
> **el_koraco said:**
> It's a non-issue for the majority of users on Intel cards, which make what, 60-80 percent of the market, but that's beside the point, we can talk about it in the Cafe if you're so inclined. If you want, we can try to make your ATI card behave a little better, the Catalyst driver does have some options, but the Control Center sucks, so one has to resort to the command line, which has a lot more switches.

Yes. That's rather like the one-sided stuff I always hear about. Linux being better suited to Intel kinda sucks :(. I don't see what the dealio is with AMD anyway? I think AMD/ATI are great, not just because I use it, but price/performance wise at least. Just a shame AMD/ATI don't offer further support.

I like CCC, but it's missing a few options because it doesn't have CCC2 which Windows has. I think it'd benefit a bit more from a more up-to-date driver as well.

Things are going 100x better than Ubuntu 9, that's for certain, so I'm happy to see it is more user friendly than a few years back.

I'll check back...

---

### Post by el_koraco on 2011-05-30
> **LFX64 said:**
> I don't see what the dealio is with AMD anyway? I think AMD/ATI are great, not just because I use it, but price/performance wise at least. Just a shame AMD/ATI don't offer further support.

I like CCC, but it's missing a few options because it doesn't have CCC2 which Windows has. I think it'd benefit a bit more from a more up-to-date driver as well.



ATI has not been working as much on making their proprietary drivers function on the X Windows system as Nvidia has. On the other hand, they've started publishing specs for their cards, which Nvidia isn't doing, and this has led to a significant improvement of the open source driver stack. On my Mobility Radeon HD 4xxx series, as an example, the open source driver is very good, just doesn't handle temperature control as Catalyst. ATI has also put out a call for two more developers to work on the open source driver stack, and I'm kinda guessing that in two years time the open source drivers should be up to par with Catalyst. The market is just not very big, so they haven't had much incentive to do more serious work, not least because they have to make the drivers work with every version of the Xserver that's being pushed out.

You've installed the driver from the Additional Drivers utility, which gives you Catalyst 11.4. The latest version is 11.5, which i'm using right now, and it does have some improvements. You could install the new version manually, but that entails going to the command line, and you have to uninstall it and reinstall it any time there's a kernel upgrade. So it might be more than you're willing to handle. If you wanna dabble with CLI switches, run the command 

```
aticonfig
``` 

in the Terminal, and you'll see a large number of confusing commands :D

---

### Post by el_koraco on 2011-05-30
@java
Open the Software center, go to Edit, and Software sources. Then to the "Other software" tab, and tick the "Canonical partners" box. Close the software sources dialog, SC will reload the info, and then you can look for sun-java.

---

### Post by SeijiSensei on 2011-05-30
> **pablo180 said:**
> Ubuntu don't offer MP3, Flash, DVD playing etc by default because they are not open source. Whilst I understand their principles, I do agree that using a hobbled system, without a clear way for the user to install all that functionality, is a little silly and putting principles before users a tad naive. There should at least be a simple option in the menu to add such functionality, as with restricted drivers.

Not distributing libdvdcss2, MP3 codecs, and the like isn't a matter of "principles" but legality. The restricted-extras packages include software that cannot be legally shipped into some jurisdictions, most notably the US.  In some cases like MP3 and H.264, Canonical could stump for the patent royalties on each copy of Ubuntu shipped into those countries where such patents are enforceable.  Of course, since no one's paying for Ubuntu, this just takes money out of Canonical's coffers for no good reason.  When it comes to software like libdvdcss2, which is strictly illegal in the US under the "anti-circumvention" provisions of the Digital Millenium Copyright Act, shipping it could expose Canonical to legal prosecution.

I think Ubuntu comes as close to edges of the law as one can possibly expect under such circumstances.  The installer in 11.04 now includes the option to install the restricted packages at the time.  Software like K3b prompts you to install the restricted extras as well.

By the way, being "open source" or not has nothing to do with this.  You can easily obtain the source code for libdvdcss2.  That doesn't make bundling that software and shipping it into the US any less of a crime. mplayer is open source, but its libavcodec library includes an H.264 decoder that infringes patents in the US.

---

### Post by Markmental on 2011-05-30
if you really think ubuntu is hard switch to linux mint it comes with everything you will need installed

---

### Post by pablo180 on 2011-05-30
> **SeijiSensei said:**
> Not distributing libdvdcss2, MP3 codecs, and the like isn't a matter of "principles" but legality. The restricted-extras packages include software that cannot be legally shipped into some jurisdictions, most notably the US.  In some cases like MP3 and H.264, Canonical could stump for the patent royalties on each copy of Ubuntu shipped into those countries where such patents are enforceable.  Of course, since no one's paying for Ubuntu, this just takes money out of Canonical's coffers for no good reason.  When it comes to software like libdvdcss2, which is strictly illegal in the US under the "anti-circumvention" provisions of the Digital Millenium Copyright Act, shipping it could expose Canonical to legal prosecution.

I think Ubuntu comes as close to edges of the law as one can possibly expect under such circumstances.  The installer in 11.04 now includes the option to install the restricted packages at the time.  Software like K3b prompts you to install the restricted extras as well.

By the way, being "open source" or not has nothing to do with this.  You can easily obtain the source code for libdvdcss2.  That doesn't make bundling that software and shipping it into the US any less of a crime. mplayer is open source, but its libavcodec library includes an H.264 decoder that infringes patents in the US.

I understand the ins and outs of it and was being general, e.g. there are no copyright/legal issues with Flash, or Adobe Reader, Microsoft Core Fonts, yet Canonical choose not to include them. They don't include any proprietary software, even if the best piece of software in a particular field is free. 

As for the legality of some aspects, that may be an issue, yet many distributions do include them, including the Ubuntu based Linux Mint and yet haven't faced any legal problems. libdvdcss2, as far as I know, isn't illegal, but if it is the possibility of legal action that puts Canonical off, they could always have different discs for different regions. Canonical is London based, and as far as I am aware, there are no legal issues libdvdcss2 in the UK, certainly not in most countries.

As I said, I understand the reasoning behind it, I just don't agree with it. To the end user, having a Movie Player that cannot play their DVDs, and a music player that cannot play their collection of MP3s, and no clear way of getting them to play, isn't really acceptable - they aren't really going to care about patents/legality etc when other software had no problems. I was lucky my laptop came pre-installed with Ubuntu from Dell, so included DVD and MP3 playback. 

Also, this is going to be an even bigger problem, when Ubuntu moves into the portable device field, which Canonical clearly intend to do.

---

### Post by uRock on 2011-05-30
> **Markmental said:**
> if you really think ubuntu is hard switch to linux mint it comes with everything you will need installed

So does Ubuntu. Just tick the Fluendo package during the install.

---

### Post by createdcreature on 2011-05-30
Wireless support was never designed for the Linux Kernel, and it is flaky at best:(.

---

### Post by pablo180 on 2011-05-30
> **LFX64 said:**
> 
As for the wireless thing...

(gedit:3374): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.H6JFWV': No such file or directory

(gedit:3374): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

That happened when I copied and pasted in what you told me.

:D

Sorry, I didn't explain that very well. 

Open a terminal and enter:

```
sudo gedit /etc/modprobe.d/blacklist.conf
```

That will open a file in gedit (similar to Windows Notepad), away from the terminal, you may have to ALT+TAB to find it. Once it has opened you can ignore the terminal (but don't close it) till you're finished. 

Scroll down to the bottom of the file in gedit and create new line and add:

```
blacklist rt2800usb
```

Once you've added the line, save the file, exit gedit and the terminal and restart the PC.

---

### Post by jerome1232 on 2011-05-30
> **pablo180 said:**
> To the end user, having a Movie Player that cannot play their DVDs, and a music player that cannot play their collection of MP3s, and no clear way of getting them to play, isn't really acceptable - they aren't really going to care about patents/legality etc when other software had no problems. I was lucky my laptop came pre-installed with Ubuntu from Dell, so included DVD and MP3 playback.

my offtopic 2 cents.

Windows comes with none of that preinstalled either. The only reason it usually has it is vendors that pre-installed it for you, have included these shiny extra's. When you install Windows yourself, you have a much more barren operating system than a default Ubuntu install.

The last time I setup my own Windows computer, it involved visiting many different websites installing drivers and various peices of software and rebooting each time. Ubuntu takes a visit to the software center and installing extra packages.

If you don't like setting up your own computer, buy it with the os preinstalled and setup for you. Like most users do.

edit: I wasn't really directing the last sentance at you, just saying it in general. My post looked a bit rude towards the end when I re-read and I didn't not intend it to be that way.

---

### Post by pablo180 on 2011-05-30
> **jerome1232 said:**
> my offtopic 2 cents.

Windows comes with none of that preinstalled either. The only reason it usually has it is vendors that pre-installed it for you, have included these shiny extra's. When you install Windows yourself, you have a much more barren operating system than a default Ubuntu install.

The last time I setup my own Windows computer, it involved visiting many different websites installing drivers and various peices of software and rebooting each time. Ubuntu takes a visit to the software center and installing extra packages.

If you don't like setting up your own computer, buy it with the os preinstalled and setup for you. Like most users do.

True, Windows is a nightmare to set up yourself from scratch, especially a re-install when the person you're doing it for replies with "What discs?" and you have to track down the motherboard type, specific sound chip etc download and install the drivers and then the constant restarting. Ubuntu is simple in comparison, most things just work. An off the shelf version of Windows is, as you say, bare. Not even an office suite, but Windows users have the option of heading to the shops and buying software (or even buying it online) - we don't. If you installed a DVD player from the software centre, you'd still be unable to play DVDs and probably not understand why, like the OP. 

And let's be honest, other than people like us, how many ordinary users go out buy a PC (or even the parts and assemble them) and install their own OS? Not many. Most buy a PC with everything pre-installed and set-up, so when Ubuntu is billed as a complete replacement OS and doesn't do out of the box what pretty much every other OS can (save the OEM versions), you can understand why people are disappointed or think Ubuntu isn't up to much. You can't just straight out compare Windows with Ubuntu, because that isn't what a user does, they compare their preinstalled PC with Ubuntu. 

I do build my own PCs, I've built hundreds over the years, but the reason that I bought this laptop was to support Ubuntu on Dell, and so that I didn't have the usual hassle of solving problems with sounds, video, sleep, hibernate etc as I have had on Ubuntu over the years. It just worked. I'd probably do it again.

---

### Post by ramadasan7@gmail.com on 2011-05-30
The 32-bit version of ubuntu is stable.  I started with kubuntu but switched over to ubuntu 64-bit version.  However, I have now settled with ubuntu 11.04 32-bit.  My usb data card also works with the 32-bit version ubuntu and not the 64-bit.

Those using ubuntu on a commercial or semi-commercial scale should use the latest available Long Term Support version which I think is the ubuntu 10.04 version.

---

### Post by LFX64 on 2011-05-31
> **pablo180 said:**
> Sorry, I didn't explain that very well. 

Open a terminal and enter:

```
sudo gedit /etc/modprobe.d/blacklist.conf
```That will open a file in gedit (similar to Windows Notepad), away from the terminal, you may have to ALT+TAB to find it. Once it has opened you can ignore the terminal (but don't close it) till you're finished. 

Scroll down to the bottom of the file in gedit and create new line and add:

```
blacklist rt2800usb
```Once you've added the line, save the file, exit gedit and the terminal and restart the PC.

I did notice gedit open up and I did put the line of code in, can't remember if I saved it though, damnit! lol :(

Those of you talking about Windows being bare bones when you install it, I agree, but if the whole thing works anyway, if I stick a DVD in, it will work, it will play MP3s instantly, if I want my drivers, Windows update helps, but if I want the most up to date ones, I find it very simple to go to their website, get a beautiful EXE and click. Done.

I don't have to type random code. For example.

[http://uk.asus.com/](http://uk.asus.com/) - Services - Support - Crosshair III Formula - all necessary drivers, available for my motherboard / chipsets - download - click - install

Yes, exes aren't the safest.

If I want to do something similar on Linux, it'll involve going sudo apt-g-sg- --g || fheb blah

Of course, this is fine by me, except I must learn the code for the CLI, which is a hassle. I will continue to use Ubuntu, an to those suggesting other distros, I'd rather not, because they never are as simple as you'd make out. I've had people say that in the past, so I'd rather stay here and learn the ways of Ubuntu.

As for Wireless. If Linux actually wants to be better for most users, it'll have to face facts and evolve beyond the flaky stage of wireless. Wireless, to me, is mandatory. It gives me the freedom to move even my 30kg (feels like it) PC to a different area, and free up the Ethernet for other devices.

Audio wise, if I change volume by my control bar (keyboard) or drop down menu, there is static.

CCC looks ancient if this is apparently 11.04 driver updates. Did they not update the interface. Ever?

Also, I've been looking for Ubuntu Classic. Something more akin to the likes of 9 or 10. Problem is, at the login panel there is NO bar at the bottom, which I keep seeing on screenshots to change the looks of it. Access and the panel to shut the OS down, is all that is there. No, Ubuntu Classic, or no effects! Any particular reason why?

Nexius is awesome haha, reminds me of Unreal Tournament 3. Ahhh, good times.

Peace

---

### Post by jerome1232 on 2011-05-31
> **LFX64 said:**
> 
Also, I've been looking for Ubuntu Classic. Something more akin to the likes of 9 or 10. Problem is, at the login panel there is NO bar at the bottom, which I keep seeing on screenshots to change the looks of it. Access and the panel to shut the OS down, is all that is there. No, Ubuntu Classic, or no effects! Any particular reason why?


Click on your user first, then the bar should appear at the bottom (bad design imho, it used to be there before you clicked your user)

---

### Post by LFX64 on 2011-06-01
Yes indeed, that's why I didn't notice it. I'd of thought that a username was just to represent who you wanted to login in, I didn't realise it hid extra options, presumably on a per-user basis.

By the way... OH DAMN, this is good! This layout is beautiful. It's very similar to something I used a few years back, an yes, although it's a bit Windows-like, so what, right? It's functionality is far better IMO. Better menu layout for starters, an when I click on applications in the bar, they actually close when I click on it again! That's what annoyed me about the Unity bar, it opened things, but clicking again didn't close it. That, an the unity bar was about the width of the road.

Also love the hide all windows button on the bottom left, to me, since Windows 7 included it, it's essential. No Operating System, whether Windows, Linux, old or new should be without it. It should be mandatory.

This is perfect. I hope Ubuntu realise that Ubuntu Classic is the way to go. I also like how the workspace switcher and the bin are nicely tucked away in the bottom right, not to big, not to small. With those things being there, I'm more likely to use other workspaces. It also looks better having two smaller bars, one top and one bottom than a small one and a very large one on the side.

I don't think I'm ever going to use Unity again. The applications drop down menu is perfectly placed, likewise Places and System, it's much quicker to use, much cleaner, neater and has everything I need in it. Wine even has it's own section which is pretty cool.

:D YAY!

Get rid of Unity Ubuntu, keep Classic! :)! It's the only way!

Now that my joy of the rather sickly GUI has been replaced by the Classic look, I'll continue to bang on about my Java and Audio and some apps that I feel are necessary.

Java, for instance, will load in my browser, but unfortunately not properly functional, in the sense that if I scroll down, a big trail of imagery will follow. I'm sure you all know how that looks. As for audio, it is still super quiet in some instances/videos, an rather loud in another. I feel the Pulse Audio thing is perhaps too bassy in some instances, but without it the sub is not used at all. It is pretty much discarded. The speakers are Logitech X-230 2.1 Stereo 30watt (I think) RMS. Very nice audio, served me for many years. If I turn the techno preset off in Pulse Audio, it is flat like before, but if I pick anything else from the presets the audio doesn't even sound comfortable in any respect. it'll sound alien, empty, tinny or distant, or simply too bassy with a real lack of treble. It's difficult to strike a good balance, but until I can think of something or get some more help, I'll have to stick with it on the current preset.

Apps. Since getting my computer in September 2009, I've always wanted to keep an eye on it. Temps, accurate readings, etc are essential to me. On Windows 7, I use the very clear, very basic, but very accurate OpenHardwareMonitor. It's a great creation and my sensor chip is supported as well as my CPU, so it's about as accurate as it's ever going to get. Unfortunately, I can't find anything anywhere near as good for Ubuntu. 

Any ideas?

Just to remind folks. I'm using this for the sake of it, just to get used to it, and perhaps learn a few basic commands here and there. I'm quite savvy with Windows and that's all natural after years of using it, so it's very basic to me, so I don't really expect to know everything straight away. 

Thanks for your help. :)

(Seriously, Games > all my games. Sounds & Video > Media Players & Editors... don't ever get rid of Classic, it's perfect as is)

---

### Post by jerome1232 on 2011-06-01
> **LFX64 said:**
> 

Get rid of Unity Ubuntu, keep Classic! :)! It's the only way!


Just so you know it's not Ubuntu that's getting rid of that classic look, it's gnome that is moving to gnome3 which is very similar to Unity. Unity btw is kind of still in it's testing throes and has actually come a very long way in a short time.

One app that people like to use to monitor their computer is conky, it's a highly configurable program and you can find many pre made configurations online, it comes with a decent one preinstalled.

Here are some screenshots of what it can look like

[http://ubuntuforums.org/showpost.php?p=10890370&postcount=17911](http://ubuntuforums.org/showpost.php?p=10890370&postcount=17911)

---

### Post by sanderd17 on 2011-06-01
> **jerome1232 said:**
> Just so you know it's not Ubuntu that's getting rid of that classic look, it's gnome that is moving to gnome3 which is very similar to Unity. Unity btw is kind of still in it's testing throes and has actually come a very long way in a short time.

One app that people like to use to monitor their computer is conky, it's a highly configurable program and you can find many pre made configurations online, it comes with a decent one preinstalled.

Here are some screenshots of what it can look like

[http://ubuntuforums.org/showpost.php?p=10890370&postcount=17911](http://ubuntuforums.org/showpost.php?p=10890370&postcount=17911)

conky is a very good tool, but also a bit geeky. If you try conky for the first time, i would install it with the conky-colors script. That script offers you a normal conky file on which most parameters can be seen (including ram, hdd space, music playing, temperature of CPU and hdd, weather and some other things).

instead of conky, you could also use apps to put in the gnome panel.

---

### Post by el_koraco on 2011-06-01
> **LFX64 said:**
> CCC looks ancient if this is apparently 11.04 driver updates. Did they not update the interface. Ever?


Nope, and I don't think there are much plans to do so in the near future. ATI cards have most of their switches in the CLI utility aticonfig, which is kinda not really self explanatory. If you wanna set your fanspeeds you gotta type in some serious mumbo jumbo. Etc.

---

### Post by el_koraco on 2011-06-01
> **LFX64 said:**
> I feel the Pulse Audio thing is perhaps too bassy in some instances, but without it the sub is not used at all. It is pretty much discarded. The speakers are Logitech X-230 2.1 Stereo 30watt (I think) RMS. Very nice audio, served me for many years. If I turn the techno preset off in Pulse Audio, it is flat like before, but if I pick anything else from the presets the audio doesn't even sound comfortable in any respect. it'll sound alien, empty, tinny or distant, or simply too bassy with a real lack of treble. It's difficult to strike a good balance, but until I can think of something or get some more help, I'll have to stick with it on the current preset.


Pulseaudio is... not the highest quality sound service you're gonna find. It's designed for intermediate use, has some nice options, but most sound buffs hate the very name of it. There are other options, one is to go with bare ALSA (Advanced Linux Sound Architecture), the principal sound server for Linux, or with the low-latency JACK server. None of the options are easy to accomplish at the beginning, so you're probably better off sticking with the poor sound quality until you're ready to do some serious tweaking. 

btw, from what you've been writing, you actually might have a better time using the KDE desktop. The Ubuntu derivative coming with KDE is called Kubuntu. Google it, it might tickle your fancy.

---

### Post by pablo180 on 2011-06-01
> **LFX64 said:**
> 
By the way... OH DAMN, this is good! This layout is beautiful. It's very similar to something I used a few years back, an yes, although it's a bit Windows-like, so what, right? It's functionality is far better IMO. Better menu layout for starters, an when I click on applications in the bar, they actually close when I click on it again! That's what annoyed me about the Unity bar, it opened things, but clicking again didn't close it. That, an the unity bar was about the width of the road.

Also love the hide all windows button on the bottom left, to me, since Windows 7 included it, it's essential. No Operating System, whether Windows, Linux, old or new should be without it. It should be mandatory.

This is perfect. I hope Ubuntu realise that Ubuntu Classic is the way to go. I also like how the workspace switcher and the bin are nicely tucked away in the bottom right, not to big, not to small. With those things being there, I'm more likely to use other workspaces. It also looks better having two smaller bars, one top and one bottom than a small one and a very large one on the side.

I don't think I'm ever going to use Unity again. The applications drop down menu is perfectly placed, likewise Places and System, it's much quicker to use, much cleaner, neater and has everything I need in it. Wine even has it's own section which is pretty cool.

:D YAY!

Get rid of Unity Ubuntu, keep Classic! :)! It's the only way!

(Seriously, Games > all my games. Sounds & Video > Media Players & Editors... don't ever get rid of Classic, it's perfect as is)

I couldn't agree more. This is why I am still using 10.04, I have tried Unity and Gnome 3 and after nearly 30 years of using computers, I can honestly say I have never used anything less intuitive. 

Ubuntu don't have to re-invent the wheel, especially when it is a new, less efficient one, and it is foolhardy when you are already a niche product. But it seems that Ubuntu are determined to capture the 'tablet' market, even if it comes at the expense of the desktop market.

I don't think you will find a more divisive issue than Unity in the Ubuntu community. Yet in the next version of Ubuntu, the option of having the classic desktop will be removed! And so I think, will many users. 

Conky, as suggested is great for what you're looking for (I use it myself) but pretty complicated. Another simpler option may be screenlets (it should be in the repositories), Screenlets are basically like widgets. Once installed you can add some to the desktop that will monitor temperature, CPU use etc. Some examples are [here]("http://screenlets.org/images/a/ab/SionDesktop.jpg"), and [here]("http://screenlets.org/images/f/fc/Nvidiascreenlet.jpg").

---

### Post by stracky on 2011-06-01
Unity could be great.  There are only about 2 things i can't stand.  Lack of applets, and the inability to move application bar thingy

Hopefully by 11.11 or 12.04 they will have worked all the bugs out.


When I first started Linux, i was scared stiff about all that command line stuff.
I was familiar with the ineptness of the windows command promt, and nervous of a OS that was completely dependent on it.
I labored through complicated tutorials, only to discover that you really only need to know the basic file commands ([FONT=Arial Narrow][SIZE=1]cd[/SIZE][/FONT], [FONT=Arial Narrow][SIZE=1]cp[/SIZE][/FONT], [FONT=Arial Narrow][SIZE=1]mv[/SIZE][/FONT], [FONT=Arial Narrow][SIZE=1]rm[FONT=Verdana][SIZE=1], etc[/SIZE][/FONT][/SIZE][/FONT]) and how to use [FONT=Arial Narrow][SIZE=1]apt-get
[/SIZE][/FONT]
Personally, I like the CLI more the GUI.  To solve problems, you can just copy code from the forums. NO navigating menus that change with each release.

And plus, you can update ALL your programs at once. :P

I still can't compile from source, but this has never seriously crippled me.



I loved reading this thread and seeing someone who was ready to quit Linux forever brought back.

I am also amazed this didn't turn into a Linux/ Windows flame war:)

---

### Post by LFX64 on 2011-06-02
I remember years back, when trying a bunch of distros, I really liked Kubuntu. The cool blue interface was also very nice and very well laid out, much more so than the orange GUI - a colour I am not keen on.

What are the real differences between KDE and Gnome? Terminal commands? Speed? Resources? Support for programs? etc?

I'll obviously want something speedy, not to heavy, like this I suppose, but I don't wish to ever see Unity again, I think it is a step in the wrong direction and it looks very ugly. The big bars works on Windows, but it seriously fails on Ubuntu. Accessing applications is rather daft and slower than it needs to be on Unity. So the tablet influences Ubuntu now? Wow, that's lame.

Looks like I might end up going back to Kubuntu then. So long as the differences aren't massive, an it isn't too complicated. Although I did hear how Kubuntu is the most user-friendly. Hopefully it's layout is similar to this/Windows, an it keeps it's blue-looks. Also can't stand the nasty purple colour on the Ubuntu start up (recovery mode screen).

Advice? Opinions?

Thanks peeps!

---

### Post by Paqman on 2011-06-02
> **LFX64 said:**
> 
What are the real differences between KDE and Gnome? Terminal commands? Speed? Resources? Support for programs? etc?


Terminal commands would generally be the same, as the desktop is just a layer on top of the underlying OS. The difference is the actual interface you see, the default set of applications, and the set of libraries they depend on.

You can install and run KDE apps on Gnome, and vice versa. However, to launch an app from a different DE it first has to load up all the requisite libraries before it can launch. On the native DE for that app these would be loaded already. So apps from another DE launch a bit slowly, and obviously they don't fit in with the look of the desktop.

It really is just a matter of preference. KDE is traditionally considered a bit more "bling" and more resource-intensive, but I don't believe benchmarks on recent versions of KDE and Gnome support this any more.

---

### Post by Mariane on 2011-06-02
> **LFX64 said:**
> 
I already know about the software centre, I've used similar things on older versions of Ubuntu, but at some point or another, if I go to a website for example which says it's available for Linux, and I check the package thing and notice it isn't there, then I'm sort of screwed. It'll usually say you must install this and that first, an then install this through that to get this running. Highly inconvenient and will inevitably end up requiring the use of the CLI. 


One advantage of packages is that they usually take care of dependencies. If something else is required the solftware will know about it and install it for you. Whether you use CLI or GUI. 

The problem you mention seems to me to be more likely related to repositories. Not every program is stored in the same repository, sometimes you have to add a repository to your "sources.list" (sorry, I only know how to do this by CLI). Finding the repository is like finding the web site, you cannot tell your computer "download blabla", you have to start by finding the blabla web site and going there. 

> **LFX64 said:**
> 
What are the real differences between KDE and Gnome? Terminal commands? Speed? Resources? Support for programs? etc?

Looks like I might end up going back to Kubuntu then. So long as the differences aren't massive, an it isn't too complicated. Although I did hear how Kubuntu is the most user-friendly. Hopefully it's layout is similar to this/Windows, an it keeps it's blue-looks. Also can't stand the nasty purple colour on the Ubuntu start up (recovery mode screen).


I think KDE (Kubuntu) is easier to use but maybe this is just because I'm used to it. Sometimes you need Gnome (Ubuntu's default), though. There is also one called Xfce, which is the one which consumes the least amount of resources, so everything you run on it goes faster, or so I've heard. 

IMHO it's better to have them all installed. They won't use resources unless you use them :). Activating a proprietary driver instead of the default one is trivial in Gnome, while I don't even know if it can be done in KDE. And for other things too, mostly related to trouble-shooting, things are easier in gnome. 

Mariane

---

### Post by el_koraco on 2011-06-02
> **LFX64 said:**
> Looks like I might end up going back to Kubuntu then. So long as the differences aren't massive, an it isn't too complicated. Although I did hear how Kubuntu is the most user-friendly. Hopefully it's layout is similar to this/Windows, an it keeps it's blue-looks. Also can't stand the nasty purple colour on the Ubuntu start up (recovery mode screen).


It's much more simliar to Windows, that's why I think it might be a better way to enter the Linux world anew. Kubuntu 11.04 is also not nearly as buggy as Ubuntu 11.04. It has a different set of applications, a better sound management framework, and is more stable. 

Yuu might have problems with your card, though. The KDE window manager, Kwin, sometimes accepts ATI cards, and sometimes it doesn't :D

Burn a live CD and give it a go.

---

### Post by sanderd17 on 2011-06-02
> **el_koraco said:**
> Kubuntu 11.04 is also not nearly as buggy as Ubuntu 11.04. 

Really?

The last time a gave KDE a real chance (not next to gnome since that makes the OS heavy), I had a bad experience. But I think that was just after KDE 4 released. I'll have to try Kubuntu again.

---

### Post by LFX64 on 2011-06-02
> **el_koraco said:**
> It's much more simliar to Windows, that's why I  think it might be a better way to enter the Linux world anew. Kubuntu  11.04 is also not nearly as buggy as Ubuntu 11.04. It has a different  set of applications, a better sound management framework, and is more  stable. 

Yuu might have problems with your card, though. The KDE window manager,  Kwin, sometimes accepts ATI cards, and sometimes it doesn't :grin:

Burn a live CD and give it a go.

Actually, no I won't bother since Live CDs are evil, an want all  humans to die. I actually think wubi was the quickest, most user  friendly thing ever, since it simply requires a trip to Windows to  install or uninstall.

After learning of the differences between  Gnome and KDE, I think with it being largely similar, there really isn't  any point in switching to KDE at all, other than the blue interface.  Waste of time, right?

Anyway, when I heard about Ubuntu Classic  being dropped, I was pretty annoyed at that, but looking at Windows 7  and Ubuntu Classic, I did immediately notice some dislikes with classic,  that I hadn't really noticed before with my smaller resolution. The  workspace switcher, which I was initially pleased with, requires  marksmanship skills with a mouse (exaggerated). I figured a pop up may  show increased workspace sizes to click on, instead they remain like  mini dots. The minimise all windows button is miniscule. The one on the  right hand side next to the system tray in windows is a vertical bar,  about 3x the size of the one in Ubuntu Classic. I don't necessarily want  something like Windows, because I have Windows, but I want something  comfortable for my needs and my 1680x1050 resolution - something which  isn't overly friendly in Ubuntu Classic. Like Windows, the larger bar  works and the larger close, minimise, maximise and menu buttons help,  including the decent fonts. According to some others, font rendering  isn't as good on KDE and it's a tad slower, an bluetooth isn't overly  great. I'm not too bothered with that but the more that works the  better.

Now on to Gnome. What I've seen has immediately made me  love Unity. Quite a change in tune, yes? So what the hell is this?  [http://www.youtube.com/watch?v=ALCUPp-5UwE](http://www.youtube.com/watch?v=ALCUPp-5UwE), I want mine to look like  THAT. Now that looks GOOD. This... Ubuntu 11.04, looks purple and  orange, two colours I don't like very much.

I want Unity to look  and behave like in that video. The plus side to Unity is larger buttons,  suitable for larger desktops, the negative to Classic is obviously the  smallness of everything, although in my opinion the layout and the  behaviour of it is generally far better. Like, by 1000x.

---

### Post by sanderd17 on 2011-06-02
> **LFX64 said:**
> 

Now on to Gnome. What I've seen has immediately made me  love Unity. Quite a change in tune, yes? So what the hell is this?  [http://www.youtube.com/watch?v=ALCUPp-5UwE](http://www.youtube.com/watch?v=ALCUPp-5UwE), I want mine to look like  THAT. Now that looks GOOD. This... Ubuntu 11.04, looks purple and  orange, two colours I don't like very much.

I want Unity to look  and behave like in that video. The plus side to Unity is larger buttons,  suitable for larger desktops, the negative to Classic is obviously the  smallness of everything, although in my opinion the layout and the  behaviour of it is generally far better. Like, by 1000x.

This video is not Unity but Gnome-shell. Gnome shell is not ready yet, it should be in a few months and Gnome3 (the base of gnome-shell) will be in Ubuntu 11.10. For the moment, if you install gnome3 in Ubuntu, you will break gnome2 (the classic) and unity and there is no easy way to return.

I'm currently using gnome3 on opensuse, it is really handy and intuitive, but I've had to use the terminals more than once because gnome didn't want to boot after I changed something. Just wait until Octobre if you want a stable system with gnome-shell.

For switching the workspaces: I always use the hotkeys CTRL+ALT+LEFT/RIGHT/UP/DOWN. In gnome-shell, you also have to use the hotkeys a lot (since gnome-shell doesn't display a taskbar by default).

---

### Post by pablo180 on 2011-06-02
> **LFX64 said:**
> 
Now on to Gnome. What I've seen has immediately made me  love Unity. Quite a change in tune, yes? So what the hell is this?  [http://www.youtube.com/watch?v=ALCUPp-5UwE](http://www.youtube.com/watch?v=ALCUPp-5UwE), I want mine to look like  THAT. Now that looks GOOD. This... Ubuntu 11.04, looks purple and  orange, two colours I don't like very much.

I want Unity to look  and behave like in that video. The plus side to Unity is larger buttons,  suitable for larger desktops, the negative to Classic is obviously the  smallness of everything, although in my opinion the layout and the  behaviour of it is generally far better. Like, by 1000x. 

That is Gnome3, the newest version of the Gnome desktop, Ubuntu went a different way and created Unity instead. In my opinion, although they both suffer the same flaws, Gnome3 is superior, far more polished and nicer to use. 

Not sure if you can install Gnome3 on Ubuntu (at least not easily) but Gnome3 is also on Fedora 15 and they do a LiveCD! Well worth a look.

---

### Post by jerome1232 on 2011-06-02
Hit window key + s to get a nice view of your workspaces.

Also colors aren't set in stone, if you don't like purple, then change it. Gnome is highly customizable. While I'm nowhere near done with customizing my desktop this is what it looks like. It's definitely not purple.

Look at some of the Unity guides before you completely ditch it.

[http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)


The screen shot in your link is Gnome3 using gnome-shell, it's what gnome is moving towards. Currently Unity is build on Gnome2 but it will move to Gnome3 shortly. 

There is a ppa available for gnome3, however it will break unity as unity is built on gnome2 currently and gnome3 replaces gnome2.

---

### Post by LFX64 on 2011-06-02
So what are these guys aiming for then? Something awesome like in that video, I hope? :D

I'm hoping the guys making this head towards Gnome 3 or Shell or whatever it is... similar to that in the video there. The left hand bar is far greater looking, an the top bar and weird alternating menu thing on the desktop look great. That's the sort of desktop I can see myself using. As it stands, Unity on 11.04 is awful. Why have a button to open the application, when clicking it again doesn't close it? I don't like making frequent trips back and forth across the screen just for the sake of previewing a window.

I do have a problem folks. Quiet audio. For the past couple of days, I've noticed that audio is a tad quiet in some videos (unsure if it's the source, but the X230s are really turned up, enough to make an ear bleed if someone signed in on Pidgin) and I'm in serious need of a good, simple, effective equaliser. 

Java still doesn't work, for the same reason someone pointed out. :(

:) Thx ppl

---

### Post by LFX64 on 2011-06-02
Also getting flashing black or white boxes or weird shapes overlaying the video in some flash instances as well. Not cool :(

---

### Post by LFX64 on 2011-06-02
Ahh, another thing. Since uninstalling PulseAudio and installing ALSA, which turned out to be a complete waste of time... the audio icon has disappeared from the top right (using Unity again) and whenever I click Sound in System Settings, it just says waiting for sound system to respond. Sit there for about 3 years and it'll continue to say the same thing. The audio never changed back to the flatness I expected from uninstalling Pulse although prior to uninstalling that I did download a parametric LADSPA plugin thing, which I've just removed.

Quite disappointed by the way sound and video is going on here. :(

---

### Post by el_koraco on 2011-06-02
> **LFX64 said:**
> After learning of the differences between  Gnome and KDE, I think with it being largely similar, there really isn't  any point in switching to KDE at all, other than the blue interface.  Waste of time, right?
According to some others, font rendering  isn't as good on KDE and it's a tad slower, an bluetooth isn't overly  great. I'm not too bothered with that but the more that works the  better.


It's not just the blue interface. KDE pushed their new desktop three and a half years ago and they've had a lot of time to improve their desktop performance. They also have the best window manager, and the desktop is much more stable than Unity. The font rendering is dreadful out of the box, but that can be changed with five clicks and a reboot.

It's your show, though, I'm certainly not gonna try to convince you to do something that's you think is not worth the effort.

---

### Post by wolfen69 on 2011-06-02
@LFX64 I admire your tenacity at trying to get ubuntu working on your incompatible computer, but maybe you should try using it in virtualbox instead. Just a thought.

---

### Post by el_koraco on 2011-06-02
> **LFX64 said:**
> Ahh, another thing. Since uninstalling PulseAudio and installing ALSA, which turned out to be a complete waste of time

Aaaaaah, why? I told you it's not an easy thing to accomplish. Gnome and Ubuntu have tied the whole desktop to Pulseaudio tightly, so removing it removes other things that tend to bork your system. The panel icon for sound is called an "indicator applet", and is tied to the neck with Pulseaudio, meaning it won't work without it. And you cant' put a Gnome panel applet on Unity. I gotta check this one, as I'm not sure how to get you back on your feet without reinstalling PA.

---

### Post by jerome1232 on 2011-06-02
> **LFX64 said:**
> 

Java still doesn't work, for the same reason someone pointed out. :(

:) Thx ppl

If you goto about:plugins in your firefox address bar, what plugin is it using for java?

---

### Post by LFX64 on 2011-06-03
It says Java 1.6.0_24 and has a bunch of 1.1, 1.2, 1.3, 1.4, 1.5, 1.6s

As for virtual box, hell no. No offense guys, but what's the point if Linux's issues lead me to recommendations about using it in less ideal ways? These issues aren't OS breaking, they're just annoying. If I want to watch videos I feel I must go to Windows, due to the silly black and white flickering boxes over the players, or Java not running properly etc. I would appreciate being able to solve that issue, or have Ubuntu work on it so it works out of the box in the future. Flash wasn't hard to set up, it just doesn't work very well. It works good on some websites for sure, but not all of them, but with Java on the other hand, I believe that should have worked with Ubuntu straight away, because it's a hassle. Java programs (from the desktop, such as Minecraft) have such dreadful performance, I don't quite understand why 120fps feels stuttery.

About Pulse... why don't I just reinstall it? :D I'll try it now, hopefully I'll get missing icons back.

---

### Post by el_koraco on 2011-06-03
> **LFX64 said:**
> 
About Pulse... why don't I just reinstall it? :D I'll try it now, hopefully I'll get missing icons back.

Yeah, I googled around today, and didn't really find anything useful. There is a PPA that you can add if you wanna go pure ALSA, and it may or may not work, but since removing Pulse didn't give you any performance gain, it's best to just reinstall.

---

### Post by LFX64 on 2011-06-03
Reinstalling Pulse didn't work, partly because I couldn't find the System Wide PulseWidth Audio thing, which I installed before.

I reinstalled Ubuntu 11.04. Windows - Add/Remove, ping! Gone. Wubi - Ubuntu 11.04 AMD64.iso.torrent, etc etc. Installed.

I'm not going to mess around with the sound now until Java is sorted and some Flash players stop flickering black and white boxes in the videos.

I already installed the restricted Ubuntu extras.

I might have a stab at getting WINE and installing some Windows stuff.

:D

---

### Post by jerome1232 on 2011-06-04
I've been having the same issue with flash since upgradeing to 11.04, I've found this add-on made by a member of these forums called flash aid which seems to have remedied it for me.

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)


My thanks goes out to LovingLinux for this add-on!

---

### Post by LFX64 on 2011-06-08
I uninstalled Ubuntu. That Java thing didn't get rid of the flickering, it was exactly the same.

Overall, I think I'll stay with Windows because I have all my games on there. I'm considering selling this PC though and getting a laptop, hopefully powerful enough to run all of my games, but unfortunately if that was an option it'd cost more than what this PC would sell as. That being said, unfortunately that'd mean another 100+ on Windows 7 again, because at the moment I have shitty OEM software. :(

Thanks for the help anyway folks.

Peace

---

### Post by el_koraco on 2011-06-08
> **LFX64 said:**
>  That being said, unfortunately that'd mean another 100+ on Windows 7 again, because at the moment I have shitty OEM software. 

I think you can get rid of all that OEM bloatware. Might have to fire up RegEdit to destroy it completely, though. Plus, you're not likely to find a high end gaming laptop without Windows preinstalled.

---

### Post by LFX64 on 2011-07-01
Actually, not for the sake of Linux because it isn't actually installed at the moment, but I'm going to sell my PC and my screen, due to uncertainties of where I am going to be living in the next 4-5 months and/or how often I'll be moving about. I really don't fancy taking a 30kg computer, a 5kg monitor, 2.1 stereo speakers which weigh about 5k, a mouse and a keyboard... oh and not to forget a desk too ;) lol.

I'll be getting a Toshiba L755 Laptop, preinstalled with Windows 7 64 bit. Fine with me. I can always sort of dual boot that using wubi. I might give it another spin when I get the Laptop, in a month or so. No idea what the wireless adapter is going to be like, but bleh? ^^

Peace

---

### Post by linuxgeekalex on 2011-07-01
Am I the only one that's never (in my 6ish years of using Ubuntu) had any driver issues? It's always worked "out of the box" for me. Even with the 4 laptops and 3 desktop computers I've used.

---

### Post by jtarin on 2011-07-01
No offense to the OP but starting a separate thread for each issue is much easier on you and the ones that help. The flow of information can be overwhelming on you and the ones that help coming from 20 different directions on as many subjects as you have raised. Hint...I for one have been with Linux for many years and I don't even want to trouble with 11.04 yet.

---

