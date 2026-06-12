---
title: "Considering replacing windows xp with Ubuntu"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by jeff1981 on 2011-02-25
Hi,
First a bit about myself. I'm the IT person for a small farm. We have about 8 individuals on computers, and a total of 10 machines.  currently  I have a core i3 laptop with 4gigs ram running Windows 7, and one other individual is using a core2duo, 1gb ram with windows XP. I also have an old p4 laptop with only 512mb ram running xp. The remaining 6 machines are dell pentium 4 desktops @ 2.8ghz with 1gb ram running windows xp.

As the end of security updates for windows xp is in april 2014, I've been starting to consider what to do about our aging hardware. While it is old, it is very well cared for, and I have tons of spare parts, and spare machines. I work on  a very limited budget, and the cost of new machines, and windows and office licenses is HUGE for our small operation. That said, computers and internet sales are a big part of our business. 

Over the last year, I've moved our productivity programs from office 2003 to a combination of OpenOffice and Google Apps. While I prefer Google Apps, we are unable to use it exclusively, but have found OpenOffice a great suite of programs.

Essentially, my question is this: Would it be reasonable to set our machines up to dual boot Ubuntu, with a goal of going to that as our primary operating system over the next few years? Am I crazy for wanting to run a business on Ubuntu rather than upgrading to Windows 7? (I have 7 on my laptop, and dislike it. I was also very unhappy with the new user interface in office 2007, which was part of the reason for going to open office)

Does anybody have experience with transitioning people from windows xp to ubuntu?

Thoughts on keeping the older hardware going by using ubuntu? We are not power users, and are doing great with this equipment and xp- in fact the limiting factor in our speed is the internet connection rather than the computer.

Thanks in advance for any thoughts,
Jeff

---

### Post by mikechant on 2011-02-25
All your hardware is high enough spec to run 'Standard' Ubuntu although the 512K Laptop would probably benefit from an upgrade to 1Mb if it's not too expensive.

You should test each machine with a LiveCD or LiveUSB of Ubuntu to check that the hardware and any peripherals work OK before installing.**

I'd recommend try the long-term support version (10.04, aka Lucid) since that has 3 years support but is quite up to date at present.

The big question is what your software requirements are beyond OpenOffice/Google Apps/Browser/Email etc - do you have any Windows-specific software you need to run. It may be possible to get it to run in Ubuntu directly (in some cases) but not always, and the hardware is probably a bit low spec (too little memory) for using WinXP VMs (Virtual Machines) under Ubuntu.

**If you haven't come across LiveCDs/USBs before it's a safe way to test Ubuntu (or other  Linux) with your hardware without making any permanant changes. It's alway best to try this before doing a proper install. You can create a LiveCD/USB under Windows and just set your BIOS to boot from it instead of the hard drive.

---

### Post by HermanAB on 2011-02-25
Howdy,

Make them dual boot and set Ubuntu as the default.  That should eventually wean people off Windows, as it gets strangled by crudware and viruses.

---

### Post by snowpine on 2011-02-25
Welcome to the forums, Jeff. Like a lot of others here, I am a Windows-to-Linux success story. :) I now use Linux 99% of the time (I keep one Windows machine around for Adobe Creative Suite and Netflix.)

I think that dual boot is definitely the way to go. Best of both worlds.

One thing to keep in mind is that Ubuntu has much higher minimum hardware requirements than XP, and these requirements seem to rise with each new release. Therefore it may be unreasonable to expect a performance *boost* by switching from XP to Ubuntu; you'd have to give it a trial run on the actual hardware to see for yourself. Pentium 4 is adequate in my experience, but other factors such as video card can have a big effect. And of course there are "lightweight" alternatives such as Xubuntu or Lubuntu for older hardware.

On a more general note, I think Microsoft will have a huge mess on their hands when Windows XP reaches its end of life. It is going to be a security and support nightmare for millions of users. I would not be surprised if they further extend support at least on some limited basis.

---

### Post by jeff1981 on 2011-02-25
[

The big question is what your software requirements are beyond OpenOffice/Google Apps/Browser/Email etc - do you have any Windows-specific software you need to run. It may be possible to get it to run in Ubuntu directly (in some cases) but not always, and the hardware is probably a bit low spec (too little memory) for using WinXP VMs (Virtual Machines) under Ubuntu.

The only software we use at this point is open office, and of course the os and firefox. Everything else is done in the cloud- our accounting is done through a system called Farmigo, which is driven by the google app engine. 

How often is Ubuntu updated, and how much continuity is there from one version to the next in terms of the user experience? Another reason I'm considering making this move now is that Windows 7 is so different from xp that  I am going to have to retrain people regardless- why not go open source?

Do new versions of Ubuntu typically have major increases in the specs required to run it?

---

### Post by jeff1981 on 2011-02-25
And of course there are "lightweight" alternatives such as Xubuntu or Lubuntu for older hardware.

I just went and read some on Xubuntu. Am I correct in thinking that it's also a current and updated OS, but will lower system requirements? Would it be reasonable to use Ubuntu on the better spec machines, and Xubuntu on the lower spec hardware? Would the user experience for web browsing be similar?

---

### Post by josephmills on 2011-02-25
Hi there Jeff welcome to the ubuntu forums I was looking over your  machines and vmware might be the ticket. But if you would like to get the &quot;feel&quot; of ubuntu or any of its &quot;flavors/distros&quot; you could go with a virtual box and if you dont like just delete the version/flavor that you are using and try a new one. There is also the option of linux mint which is based on beginners switching over to linux for windows or mac. here are some links to look at in the mean time.
 _**vmware**_---------------------------------------------http://www.vmware.com/        
_**virtual box**_------------------------------------http://www.virtualbox.org/       
_**linux mint**_--------------------------------------http://www.linuxmint.com/         
well I hope that this helps in some sort of way.

---

### Post by snowpine on 2011-02-25
Xubuntu is very nice. It is simply Ubuntu with a different "desktop environment" (Xfce instead of Gnome); the core experience is the same.

Ubuntu has a new release every 6 months, and each release is supported only 18 months.

Every 2 years there is a Long Term Support (LTS) release that is supported 36 months. 10.04 (April 2010) is the current LTS and will be supported through April 2013.

Release upgrades often bring major changes in the user experience (for example the upcoming switch to Unity) and are problematic for a sizable minority of users, who have better luck with a fresh reinstall of the new release rather than a seamless upgrade.

If you are looking for an operating system where you can use the same release for 10+ years (like XP) you will not get it with Ubuntu. That being said, I would choose Ubuntu over XP any day. :)

---

### Post by oldfred on 2011-02-25
Open Office & Firefox are the heavier apps.

Lighter weight Versions often use with Chromium browser as it is lighter than firefox.
Xubuntu, a "lightweight" distribution based on the Xfce desktop environment or add LXDE desktop (is not lubuntu)
        with Gnumeric and AbiWord by default
 
 I do not think the specs have changes a lot.
[https://help.ubuntu.com/10.10/installation-guide/i386/minimum-hardware-reqts.html](https://help.ubuntu.com/10.10/installation-guide/i386/minimum-hardware-reqts.html)

Since accounting and other major business related apps are in the cloud, you should have little trouble converting. 

I retired 5 years ago and had XP at home since we only used windows at work. But I know I eventually wanted to change, so I started with Firefox, Thunderbird & Open Office in windows. Then when I went to Ubuntu my wife had almost no problem as the applications were essentially identical.

---

### Post by SEisch on 2011-02-25
If you are going to try Ubuntu, I suggest, try it on the computer you personally use the most, first.   If you like it, then go from there.
Your older computers have similar hardware to my own computer, and I am running Ubuntu 10.10 just fine.  You might want to check your hardware compatibility first though.  The oldest laptop you have might run a lighter version better.  Even though Lubuntu and Xubuntu are "lighter", they still take up about the same amount of space on your hard drive as Ubuntu.  I think it takes up about 3 gigabytes on my hard drive.  Something to consider if you are dual-booting and have limited hard drive space left.  
That's my 2 cents.

---

### Post by YesWeCan on 2011-02-25
Hi. I would be careful with non-tech savvy users. Linux is much more flexible than XP and it is much less forgiving and generally not as hand-holding as Windows.

I wanted to add that the KDE desktop version of Ubuntu has a more MS style than Gnome. It has a more professional feel and new users may prefer it. OpenSuSE, for example, uses KDE as standard. Unlike XP, with linux you can have different desktop types installed and select which one you want at boot. How good is that! :)

On the subject of VirtualBox, this is a good method but is a resource-hungry way of running Ubuntu. You risk users being put off by the potential sluggishness and details of managing hardware devices.

---

### Post by eriktheblu on 2011-02-25
> **jeff1981 said:**
> 
The only software we use at this point is open office, and of course the os and firefox. Everything else is done in the cloud- our accounting is done through a system called Farmigo, which is driven by the google app engine.  OO.o (switching to Libre?) is default for Ubuntu, as is Firefox. If Farmigo requires any custom plugins that may give you trouble. Flash and Java should work fine, but don't expect to be using .net stuff.

> How often is Ubuntu updated,
Every 6 months in April and October. Every 2 years is a LTS (long term support) release.
> how much continuity is there from one version to the next in terms of the user experience?
Quite a bit. I've skipped several releases and still had no problem adjusting. The worst changes are made by moving or redesigning configuration files; a problem for administrators but not really for users.
> Am I correct in thinking that it's also a current and updated OS, but will lower system requirements?
Yes. Different desktop environment; not as pretty. Xubuntu has a reputation for bloat; in my experience it used comparable resources to Ubuntu (but still uglier). For light weight (laptop with 384 MB RAM), I used the minimal install, then manually added LXDE. Works great.

> Would the user experience for web browsing be similar? They all have Firefox, so the experience will be almost identical to what you're seeing now with XP. There are differences, but they are minor.

---

### Post by houseworkshy on 2011-02-25
The servor lts edition has longer support, five years.  
If Ubuntu then for system critical machines the long term support releaces would be the best option. When it comes to upgradeing wait for the last squeek of the old lts as by then any bugs in the new version will have had time to be ironed out, sadly fresh .0's have been buggy recently.  This would also give hardware drivers time to catch up.
Fresh installs are more reliable than upgrades.  One can make this process far easier by having /home on its own partition, in this way one keeps all ones work unaltered whilst installing the clean new op around it  (do backups anyway though).
Ubuntu is a fast mover, I think that gnome is about to be abandoned in favour of gnome-panels so, bearing in mind training, Kubuntu which uses the kde destop gui may be a better choice in the long term.  Debian is also worth a look as stability is as important as development of new features for it's developers; they actually separate the two and only allow migrations from the development branch to the stable branch when a feature is rock solid.   This means that the stable branch is a little behind the wave as far as new features is concerned but for a working office I'd guess that stability is the bigger deal.  

That said Ubuntu lts without extra PPA's added and once it is at .1 or so has been solid enough for me.

---

### Post by whistlerspa on 2011-02-25
I think that the biggest practical hurdle to replacing software in an organisation is the current mindset that IT users have. Whilst you may be ready and willing to change, it's not just about the software. People are used to Windows and you could have a lot of resistance to different looking desktops and alternative productivity software. 

Linux, whilst excellent functional software does limit choices a little. For instance in my organisation we run some Windows only software (and there are no Linux alternatives) and Macs, and often have to find complex workaraounds for the people who use the latter, in order for them to be able to do tasks on Windows only sofware (via remote desktop and the like). 

Whilst Linux distros can be more customised, there could still be those sorts of issues for you as well. 

Also XP is now on version 4 and has become pretty good solid software in my opinion (pity it took a decade for this though). 

If you are not planning any hardware upgrades then is there any real reason to change? The crunch will come when you do because my experience is that new hardware coming out now is not very XP compatible and then the choice will be Windows 7 or Linux.

---

### Post by mastablasta on 2011-02-25
i would just add another thing here. you said you have slow connection. most programmes are loaded from internet through software center. and system updates provide all programme updates as well. so sometimes these can be quite big (200-350MB).

Otherwise this post is written on regular Ubuntu on very old Athlon 1.2Ghz with 229 MB ram running Ubuntu.

Check the graphics card (some have crappy manufacturer support or underdeveloped opensource drivers) & compatibility before deciding to go for it.


as others mentioned you can even choose lighter desktop environment, but they casn still run Firefox.

Kubuntu (KDE Desktop) is like Windows. Especially if you right click the K and select classic menu style.

Another options is also Ubuntu based Linux Mint also very user friendly and their default GNOME (yet enother desktop environment and Ubuntu's default) menu looks also kind of like windows. I think gnome has more applications.

---

### Post by Kixtosh on 2011-02-25
> **jeff1981 said:**
> ... and one other individual is using a core2duo, 1gb ram with windows XP. I also have an old p4 laptop with only 512mb ram running xp. The remaining 6 machines are dell pentium 4 desktops @ 2.8ghz with 1gb ram running windows xp ....

Thoughts on keeping the older hardware going by using ubuntu? We are not power users, and are doing great with this equipment and xp- in fact the limiting factor in our speed is the internet connection rather than the computer. ...Jeff, I have some farming credentials of my own, but I won't detail those here, and a lot of what you said makes sense to me. Anyway, I have some experience which I think is entirely relevant to you.

Firstly, I have also switched from XP to Ubuntu. Secondly, I have tried Lubuntu (not an official distro yet, by the way), Xubuntu, Xubuntu with the LXDE lightweight desktop environment, Peppermint, and a few others along the way. Thirdly, I still use Vista and W7 (so I at least know what they are). Finally, two of my most used Ubuntu machines have very limited capabilities by today's standards. Here are my thoughts.

**(1)** From the usage you describe, mostly internet surfing and e-mail, as well as office applications: I would have no hesitation whatsoever in recommending the switch from XP to Ubuntu. I only keep Windows myself because of certain specialized applications involving TomTom GPS devices. My only hesitation would be any MS Office documents you might receive with complex formating, or PowerPoint presentations, but if you keep just one machine dual booting with Windows, then you won't have any issues there either, and it's probably more of a precaution than a necessity.

**(2)** In my opinion, the transition to W7 and newer versions of MS Office (with the ribbon - 2007 edition and later, I think), would certainly be at least as problematic for many users, even those who are quite proficient today, as the transition to Ubuntu and OpenOffice (or LibreOffice).

**(3-a)** Concerning the ability to run Ubuntu. The machine I am typing on now has a Mobile Pentium M, single core, 1.2 GHz processor, has the maximum possible RAM of 1.28 GB, and a hard drive speed of just 4,200 RPM (it's a very compact notebook weighing just over 2.5 lbs). With Win XP, startup times had slowed from just under two minutes (right after a fresh install) to five whole minutes. It took about thirty seconds to shut down as well. Otherwise, it worked very reliably.

With Ubuntu 10.04 Lucid Lynx (LTS), startup time has been reduced to 55 seconds. Shut down time is under ten seconds. It has been extremely reliable.

**(3-b)** My other Ubuntu machine has a better Centrino 1.2 GHz dual core processor and 2 GB of RAM. Vista Business boots in about seventy-five seconds, and shuts down in about twenty. Lucid Lynx boots in about twenty-five seconds and shuts down in five. These times include the five seconds required for BIOS to finish loading, so Ubuntu is booting in twenty seconds really.

**(4)** On machine 3-a, I did try some lightweight distros, that had worked well for me on even older machines (see signature), but they yielded little improvement with these specifications, so I personally would not advise them for the machines you listed above, although I would try to pick up some extra RAM for the machine with just 512 MB, if possible (just to be on the safe side, more than anything else).

**(5)** For your Office applications, I would stick with OpenOffice, rather than AbiWord or Gnumeric. It will seem more like a full Office suite to users familiar with MS Office in my opinion, whereas the former will seem like dumbed down versions (even if they are faster as well as lighter, and will probably suffice for the majority of casual users).

**(6)** For your browser, consider Chromium instead of Firefox. I did find it faster, and overall, I just prefer it. Some may advise against it though, citing that Firefox is more secure. That's up to you.

**(7)** Since you have to maintain all of this, even though Xubuntu is similar to Ubuntu, there are differences (such as layout, keyboard shortcuts etc.). I would not recommend mixing if I were you, but it's not the end of the world if you do. In fact, one of my laptop-o-saurs (with far more limited abilities than what you describe) worked better with Xubuntu than Ubuntu - some sort of sound card issue that just preferred Xubuntu.

Also, since you do have to maintain all of this, I see no compelling reason to use anything other than LTS (Long Term Support) releases, such as Lucid Lynx 10.04, on so many machines, given your stated goals and usage. That means you don't have to worry about fixing what ain't broke until 12.04, but by then you'll only have a year left to make up your mind on what to do next.

Just some food for thought, I hope, and helpful too, with any luck! The speed improvements on startup and shut down alone should win over some hesitant souls (if there are any). Think ahead and check out compatibility of peripheral devices such as printers and fax machines though!

---

### Post by houseworkshy on 2011-02-25
Just a quick point, printers.  Make sure that they are compatable before switching, it varies a lot with Canon being the worst for linux, many just won't work at all and HP being the best, usually connect and go.

---

### Post by mulacabu on 2011-02-25
Go for it and get yourself a an old pentuim 2 or 3 and install E-SMITH sme server all free 
this will act as secure file and web server easy to set up
good luck 
mulacabu
:lolflag:
ps will also serve a printer

---

### Post by RealBigSwede on 2011-02-25
Hello Jeff,
I'm my Family Tech guy we have a total of 5 computer and I was a window guy and I started with my Table and just change to Ubuntu and will change each of the computer to U (slowly) to try to understand how to change and then I will change them all to O now. I have been building computer since 1992 and working in the Computer business since 1983, But I have tried Linux before but I was never impressed until now!! So,, I will incurage you to jump in. JUST MY 2 CENT.... Hope that will help you to "push you over the edge" hehehe:P
RealBigSwede

---

