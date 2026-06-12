---
title: "Toshiba fan not working"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by CBR_Rob on 2010-03-02
I am trying desperately to make Ubuntu work on my laptop. I want to use windows as little as possible. The fan on my Toshiba laptop never comes on. Once I get into processor heavy stuff my laptop overheats and shuts itself off. I have a screen shot from a device manager program and it appears to me that there is no driver for the fan. Now is there anyway to get a driver to make my fan work?

---

### Post by Ozymandias_117 on 2010-03-02
Have you looked at all in BIOS? I've seen some that you can tell BIOS to take care of it (I assume without help from your Operating System) Or as a temporary fix you may be able to turn it to always on so you don't get shut off.

---

### Post by chaanakya_chiraag on 2010-03-02
Try ```
sudo toshset -fan auto
``` in a terminal (Applications-> Accessories-> Terminal). Important: if it asks you for password, you WILL NOT see the password being entered.

---

### Post by CBR_Rob on 2010-03-02
I checked the bios and did not see any fan options. The fan works perfectly fine in Windows Vista.

---

### Post by CBR_Rob on 2010-03-02
> **chaanakya_chiraag said:**
> Try ```
sudo toshset -fan auto
``` in a terminal (Applications-> Accessories-> Terminal). Important: if it asks you for password, you WILL NOT see the password being entered.
I get a message stating "required kernel toshiba support not enabled" I attached a screenshot of this message.

---

### Post by QIII on 2010-03-02
Ah, the "Toshiba fan with Linux issue" again.
 
 Toshiba apparently has a distaste for Linux.  The fan control works just fine in Windows, since Toshiba wanted it that way...
 
 I still see this as an active discussion on launchpad.

I'll see if I can find a resolution for the kernel.

---

### Post by CBR_Rob on 2010-03-03
I just tried this after searching for some more solutions on my fan problem.

"[COLOR=black][FONT=Verdana]Add the following to your /etc/modules: (sudo gedit /etc/modules)[/FONT][/COLOR][COLOR=black][FONT=Verdana]
battery
ac
thermal
processor
acpi-cpufreq
cpufreq-userspace
Restart after adding."

Now my fan seems to be slowly working but when I get into cpu heavy programs (converting video with handbrake, which I will be doing a lot) the temp jumped up from 55 deg c to 90 deg c within minutes. The pc did not shutdown since I stopped the encode at that point. Now after stopping the encode the temp dropped back down to 55 within 1.5 mins. I felt the pc physically get hotter and cool back off. What exactly did I do and can I use this to change the speed of the fan? 
[/FONT][/COLOR]

---

### Post by CBR_Rob on 2010-03-04
> **QIII said:**
> Ah, the "Toshiba fan with Linux issue" again.
 
 Toshiba apparently has a distaste for Linux.  The fan control works just fine in Windows, since Toshiba wanted it that way...
 
 I still see this as an active discussion on launchpad.

I'll see if I can find a resolution for the kernel.

Does the Toshiba fan have this issue with earlier releases of Ubuntu? I am thinking of taking 9.10 off and running 8.4 until the next LTS comes out, at least if the fan issue is solved.

---

### Post by QIII on 2010-03-05
As I recall, this has been a long-standing issue.

Toshiba expects that Windows will be installed (It's a good bet that it will be, so do you blame them?), and defers fan control to Windows.

---

### Post by CBR_Rob on 2010-03-05
Well for the foreseeable future I will need to keep a windows machine around so I've taken Ubuntu off of this machine. Once I get a new hard dive for my Dell I'll give Ubuntu another go.

---

### Post by Djalmahal on 2010-03-05
Sliglthy off topic:
I had a Toshiba, fan worked, then after years the fan broke down. As a very temporay fix you can direct a normal fan into where  the laptop fan normally blows out the heat, that keeps the temperature down.
Sorry, that's all I have to contribute.

Andreas

---

### Post by CBR_Rob on 2010-03-07
Well I got the fan to finally work with a different distribution of Linux (using Linux Mint 8 live cd right now). It is kinda odd because from what I have read this distribution is a variation of Ubuntu. I was able to watch movies, surf the net, and convert a dvd to digital file without having the laptop overheat and shut itself down. It got up to 85 during the last 1/3 of the movie but never went above that. Once the movie was done converting it dropped back down to 51 within 5 mins.

---

### Post by seymur on 2010-03-08
> **Djalmahal said:**
> Sliglthy off topic:
I had a Toshiba, fan worked, then after years the fan broke down. As a very temporay fix you can direct a normal fan into where  the laptop fan normally blows out the heat, that keeps the temperature down.
Sorry, that's all I have to contribute.

Andreas 

My Toshiba fan broke in half a year, they replaced it, now it is again having some problems. Also overheating is always a problem with toshiba.

---

### Post by mörgæs on 2010-03-08
> **CBR_Rob said:**
> Well I got the fan to finally work with a different distribution of Linux (using Linux Mint 8 live cd right now). It is kinda odd because from what I have read this distribution is a variation of Ubuntu. I was able to watch movies, surf the net, and convert a dvd to digital file without having the laptop overheat and shut itself down. It got up to 85 during the last 1/3 of the movie but never went above that. Once the movie was done converting it dropped back down to 51 within 5 mins.

Congratulations.

In general, trying various releases of Ubuntu (8.04 - 9.04 - 9.10 - 10.04 alpha) is by far the best way to solve problems. It is a waste of time to force a given Ubuntu to obedience, if one has not tried alternative releases first.

---

### Post by finito on 2010-04-29
I have a toshiba U505-S2960 I am running the 64-bit 9.10 Ubuntu.

I was amazed to see Ubuntu didn't pick up my driver immediately. I have been using Ubuntu for my desktop for a while now, just love the OS so simple and yet so effective anyway.

I had problems with the wifi drivers and the fan.

The Wifi driver was easy, the Fan was the problem, but I figured a way to make it work, its kinda annoying tho.

basically FN+F3 seems to make the machine go into stand by or something, when I press the power button again to wake it out of this state. the fan starts to work. The highest I can get the temp to goto is 45 C. I had a few browsers open, burning a CD and compiling something in virtual box running Windows XP to get it to 45C. idle is around 35~38C

I am not sure what the FN+F3 does, as closing the lid and pressing power button to wake it up doesn't have the same effect.

The annoying part is every time I restart I have to do it. The simple solution is don't shut down or restart just close the lid and let it go to stand by.

I have added a picture of the icon on F3 button looks like a bios chip.

---

### Post by HermanAB on 2010-04-29
I have a Toshiba U500 and the fan mostly works, but sometimes I have to reboot to get it to work.  There doesn't seem to be any method in the madness.  I would like to just run a power wire and a 200 Ohm resistor to the damn fan, but at present I'm living in an area where electronics parts are hard to come by.

---

### Post by finito on 2010-04-29
You aren't very far from the Middle East's biggest electronic market.

---

### Post by c00lwaterz on 2010-04-29
i have the same issue regarding fan problem and high temperature.

I am still stuck with this issue. 

im using toshiba m900

---

### Post by mörgæs on 2010-04-29
> **HermanAB said:**
> I would like to just run a power wire and a 200 Ohm resistor to the damn fan, but at present I'm living in an area where electronics parts are hard to come by.

Rather than using a resistor I would recommend a series of diodes, for example 1N4001. The voltage drop over a resistor depends on the current through it, but there is always 0,7 V over a diode. 

I use this sometimes when I have a noisy fan. Making it running a little slower through a voltage drop of x * 0,7 V often makes the fan noiseless.

But again - one should expect Ubuntu to take care of this.

---

### Post by finito on 2010-04-29
too bad Ubuntu 10.04 LTS has not fixed this issue. :(

---

### Post by c00lwaterz on 2010-04-29
> **finito said:**
> too bad Ubuntu 10.04 LTS has not fixed this issue. :(

did you try other distro? CBR_Rob did solve the prob on linuxmint?

---

### Post by c00lwaterz on 2010-04-29
> **QIII said:**
> Ah, the "Toshiba fan with Linux issue" again.
 
 Toshiba apparently has a distaste for Linux.  The fan control works just fine in Windows, since Toshiba wanted it that way...
 
 I still see this as an active discussion on launchpad.

I'll see if I can find a resolution for the kernel.

Hi,

I have also problem with fan not running in ubuntu/linux. Will the dev help us with this issue? Toshiba want windows only for their machine?

If you have resolution, I appreciate it in advance. I want linux but High temp due to fan (not working on linux) issue, I can't use ubuntu. :confused:

---

### Post by ethos101 on 2010-04-29
I have the same problem with Acer Aspire 5720z.  I was hoping they would fix this with 10.04.  I had the same issue on 9.10.  I don't think the devs know about our issue.  I don't know how to submit bug reports through proper channels.

---

### Post by ashima on 2010-04-29
This was almost doing my head in.
Thought about having to run Windows or sell my new laptop.
Same fan problems with Fedora, PClinuxOS
Here is what works for me. Toshiba L500. 64bit Ubuntu 10.04

                                 first. sudo apt-get install sensors-applet
next. sudo sensors-detect

next. answer yes to everything.

exit then restart computer.

next. sudo gedit /etc/default/grub and then change

GRUB_CMLINE_LINUX_DEFAULT="quiet splash"

to read

..."quiet splash acpi_osi=Linux"

next. sudo update-grub to update /boot/grub/grub.cfg

exit then restart computer.


MY FAN NOW STOPS AND STARTS WHEN IT SHOULD



Hope this helps.

---

### Post by CBR_Rob on 2010-04-29
> **c00lwaterz said:**
> did you try other distro? CBR_Rob did solve the prob on linuxmint?Actually I ended up not solving this issue. It worked awesome on the live cd but did not work again once installed to the hd. I ended up taking Linux off the Toshiba and am loving Mint on my Dell. I am thinking of trying a non Debian distro or the 10.4 Ubuntu on the Toshiba but from everything I have read it is a kernel issue. This does seem like a pretty common issue for a large group of people so I would hope a fix is in the works or coming soon. Unfortunately I do not know any programming yet so I'd have no clue about creating a solution. But I would not mind installing and testing a possible solution.

---

### Post by c00lwaterz on 2010-04-29
Most of us having issue with high temperature/overheat are toshiba owners? I notice that most cases are toshiba. I have installed ubuntu but no luck in fixing the prob. I just use windows and if there is new help, I try again and again but no luck again. :confused:

I hope the next version or update will help us all with this issue.

I also tried the following with no luck:

Ubuntu 9.1
Ubuntu 10.04 final release
LinuxMint 8
PCBSD
debian 5.04

All of them I have issue in high temperature

---

### Post by monkeyshine on 2010-05-01
Have just followed Ashima's advice and fan noticeably quieter.  Watching cpu temps - seem ok around 50 deg C on both.  CPU's not thrashing themselves either.  If this continues to hold I owe you a BIG THANKS!! as I have spent hours researching how to stop my Toshiba Laptop from thrashing its fan and powering off at will.

---

### Post by monkeyshine on 2010-05-01
Bugger - CPU's within minutes shot up to around 80 deg C.  Fan not compensating.  Back to square one.  Oh well.  Will continue to watch for fix.

---

### Post by c00lwaterz on 2010-05-01
> **monkeyshine said:**
> Bugger - CPU's within minutes shot up to around 80 deg C.  Fan not compensating.  Back to square one.  Oh well.  Will continue to watch for fix.

I have been searching for 6 months already for the fix. I have tried many solution but it doesn't work. I try many distros. Maybe it's toshiba. I mean when i am for linux and toshiba in google or alike, I don't see much. The results are just old and maybe toshiba is not good on support (not sure)? I have seen toshiba linux forum but it doesn't help. I also posted in their normal forum in toshiba, and no one replied. I keep looking for their customer service using email but they don't have any email. They only have numbers but maybe it will cost just to ask something if they support linux.

I am tired of hoping :confused:

---

### Post by CBR_Rob on 2010-05-01
> **c00lwaterz said:**
> I have been searching for 6 months already for the fix. I have tried many solution but it doesn't work. I try many distros. Maybe it's toshiba. I mean when i am for linux and toshiba in google or alike, I don't see much. The results are just old and maybe toshiba is not good on support (not sure)? I have seen toshiba linux forum but it doesn't help. I also posted in their normal forum in toshiba, and no one replied. I keep looking for their customer service using email but they don't have any email. They only have numbers but maybe it will cost just to ask something if they support linux.

I am tired of hoping :confused:
Exactly why my Toshiba is staying with Vista. All future pc's I buy will be capable of running Linux. I am surprised with all the problems I have read about Toshiba fans not working that no developers have come up with a solution.

---

### Post by turvyc on 2010-05-01
> **ashima said:**
> This was almost doing my head in.
Thought about having to run Windows or sell my new laptop.
Same fan problems with Fedora, PClinuxOS
Here is what works for me. Toshiba L500. 64bit Ubuntu 10.04

                                 first. sudo apt-get install sensors-applet
next. sudo sensors-detect

next. answer yes to everything.

exit then restart computer.

next. sudo gedit /etc/default/grub and then change

GRUB_CMLINE_LINUX_DEFAULT="quiet splash"

to read

..."quiet splash acpi_osi=Linux"

next. sudo update-grub to update /boot/grub/grub.cfg

exit then restart computer.


MY FAN NOW STOPS AND STARTS WHEN IT SHOULD



Hope this helps.

I can confirm this solution. I have a Toshiba Satellite L300. I'd been having the same problems and had tried a couple fixes, but **this one worked!** What a relief. Thank you ashima!

---

### Post by c00lwaterz on 2010-05-02
> **CBR_Rob said:**
> Exactly why my Toshiba is staying with Vista. All future pc's I buy will be capable of running Linux. I am surprised with all the problems I have read about Toshiba fans not working that no developers have come up with a solution.

Maybe Toshiba does not support linux. How can we contact them via email? so we can request. since this toshiba laptop is not low value. it is expensive so we deserve some support. they should give us support.

---

### Post by cis.ash on 2010-05-02
i have Toshiba L300 but when the fan start, it never stops so i found that downloading a packages called "toshutiles" and "toshset" will fix the issue :D

---

### Post by CBR_Rob on 2010-05-02
> **c00lwaterz said:**
> Maybe Toshiba does not support linux. How can we contact them via email? so we can request. since this toshiba laptop is not low value. it is expensive so we deserve some support. they should give us support.
[http://www.tacp.toshiba.com/customersupport/contact.asp](http://www.tacp.toshiba.com/customersupport/contact.asp)
You could try emailing them with this link.

---

### Post by 2dvisio on 2010-05-02
Hi guys,

Same problem here with a Sony VAIO.

The problem seems to be the same. I have installed sensors and pwmconfig. The first command give me just three temperatures (VIDEO and 2 CPUs I guess) and the second one tells me it is not allowed to regulate FAN speed.

So... I tried your solution (rebooting with the new option) but it did not work.

Any other ideas/suggestios are really welcome.

I can continue working but at 800Mhz.

And since I passed to linux since more than 5 years I need you guy not to go back to Win again :)

I am obviously read other responses from other forums but unsuccessfully.


Thank you in advance!

---

### Post by c00lwaterz on 2010-05-02
> **2dvisio said:**
> Hi guys,

Same problem here with a Sony VAIO.

The problem seems to be the same. I have installed sensors and pwmconfig. The first command give me just three temperatures (VIDEO and 2 CPUs I guess) and the second one tells me it is not allowed to regulate FAN speed.

So... I tried your solution (rebooting with the new option) but it did not work.

Any other ideas/suggestios are really welcome.

I can continue working but at 800Mhz.

And since I passed to linux since more than 5 years I need you guy not to go back to Win again :)

I am obviously read other responses from other forums but unsuccessfully.


Thank you in advance!


we have common problems? most of us have new laptops that has issues regarding high temperature.? is it the manufacturers responsibility or only some prob or bugs with linux kernel or bios? i am confused who is responsible. :confused:

---

### Post by c00lwaterz on 2010-05-02
> **CBR_Rob said:**
> [http://www.tacp.toshiba.com/customersupport/contact.asp](http://www.tacp.toshiba.com/customersupport/contact.asp)
You could try emailing them with this link.


Thanks for the link. I have emailed them and hope for response. If they ignore it then this will give me bad impression towards Toshiba company.

---

### Post by pricorp on 2010-05-03
> **turvyc said:**
> I can confirm this solution. I have a Toshiba Satellite L300. I'd been having the same problems and had tried a couple fixes, but **this one worked!** What a relief. Thank you ashima!

Ashima's solution is not working on my U500-11C.

So far, only 2 "annoying" solutions are working:

1- sudo pm-suspend
or
2- Fn+F3

"Annoying" because each solution requires to suspend the system.

---

### Post by c00lwaterz on 2010-05-03
> **pricorp said:**
> Ashima's solution is not working on my U500-11C.

So far, only 2 "annoying" solutions are working:

1- sudo pm-suspend
or
2- Fn+F3

"Annoying" because each solution requires to suspend the system.

nothing works for me. toshiba m900

---

### Post by dresnu on 2010-05-03
> **ashima said:**
> This was almost doing my head in.
Thought about having to run Windows or sell my new laptop.
Same fan problems with Fedora, PClinuxOS
Here is what works for me. Toshiba L500. 64bit Ubuntu 10.04

                                 first. sudo apt-get install sensors-applet
next. sudo sensors-detect

next. answer yes to everything.

exit then restart computer.

next. sudo gedit /etc/default/grub and then change

GRUB_CMLINE_LINUX_DEFAULT="quiet splash"

to read

..."quiet splash acpi_osi=Linux"

next. sudo update-grub to update /boot/grub/grub.cfg

exit then restart computer.


MY FAN NOW STOPS AND STARTS WHEN IT SHOULD



Hope this helps.

This solved it for me on a 64-bit installation too.

Thanks

---

### Post by c00lwaterz on 2010-05-03
> **dresnu said:**
> This solved it for me on a 64-bit installation too.

Thanks

what is your laptop brand and model? I have problem and until now now fix.

---

### Post by armoftheland on 2010-05-04
Just followed Ashima's Advice. What a life saver! For my Toshiba A200 MR4, anyway. Also the FN+F3 and log in work around also worked to get the fan on.

Thanks again :) :) :)

---

### Post by dresnu on 2010-05-04
> **c00lwaterz said:**
> what is your laptop brand and model? I have problem and until now now fix.

It is a Toshiba A100-912

---

### Post by ahmadz1991 on 2010-05-09
> **ashima said:**
> This was almost doing my head in.
Thought about having to run Windows or sell my new laptop.
Same fan problems with Fedora, PClinuxOS
Here is what works for me. Toshiba L500. 64bit Ubuntu 10.04

                                 first. sudo apt-get install sensors-applet
next. sudo sensors-detect

next. answer yes to everything.

exit then restart computer.

next. sudo gedit /etc/default/grub and then change

GRUB_CMLINE_LINUX_DEFAULT="quiet splash"

to read

..."quiet splash acpi_osi=Linux"

next. sudo update-grub to update /boot/grub/grub.cfg

exit then restart computer.


MY FAN NOW STOPS AND STARTS WHEN IT SHOULD



Hope this helps.
THANKS A MILLION.... U JUST SAVED MY LAPTOP :) 

Thanks again... worked like a charm :D

---

### Post by Brown_ on 2010-05-09
> **ahmadz1991 said:**
> THANKS A MILLION.... U JUST SAVED MY LAPTOP :) 

Thanks again... worked like a charm :D

I'm trying to make every things to work properly in a VM before install in my hard drive. so far so good, except for that fan issue. my laptop is a Toshiba A215 S7437.
after running sensors-detect, i got:
"...Do you want to probe the I2C/SMBus adapters now? (YES/no): yes
Using driver `i2c-piix4' for device 0000:00:07.0: Intel 82371AB PIIX4 ACPI
Module i2c-dev loaded successfully.

Sorry, no sensors were detected."

so.... another disappointed toshiba owner :(

---

### Post by c00lwaterz on 2010-05-10
> **Brown_ said:**
> I'm trying to make every things to work properly in a VM before install in my hard drive. so far so good, except for that fan issue. my laptop is a Toshiba A215 S7437.
after running sensors-detect, i got:
"...Do you want to probe the I2C/SMBus adapters now? (YES/no): yes
Using driver `i2c-piix4' for device 0000:00:07.0: Intel 82371AB PIIX4 ACPI
Module i2c-dev loaded successfully.

Sorry, no sensors were detected."

so.... another disappointed toshiba owner :(

same here. prob using linux on toshiba m900. in windows it has no prob. I will just wait when there is solution. for now I just play cs2d but I got high ping. hehe

---

### Post by Zaizeku on 2010-05-11
> **ashima said:**
> This was almost doing my head in.
Thought about having to run Windows or sell my new laptop.
Same fan problems with Fedora, PClinuxOS
Here is what works for me. Toshiba L500. 64bit Ubuntu 10.04

                                 first. sudo apt-get install sensors-applet
next. sudo sensors-detect

next. answer yes to everything.

exit then restart computer.

next. sudo gedit /etc/default/grub and then change

GRUB_CMLINE_LINUX_DEFAULT="quiet splash"

to read

..."quiet splash acpi_osi=Linux"

next. sudo update-grub to update /boot/grub/grub.cfg

exit then restart computer.


MY FAN NOW STOPS AND STARTS WHEN IT SHOULD



Hope this helps.

Awesome man, I must thank you Ashima, since 9.04 I've had this problem and the only workaround I had was the suspend thing or restarting the computer. I can finally use ubuntu like it should be. Thanks a lot =D>

---

### Post by flyfishingphil on 2010-05-11
Interesting. I have made no adjustments. Did an Update Manager upgrade from 9.10 to 10.04. Have done several other installs and checked out lots of sites, actions, etc. and the fan system on my Toshiba Sat L305 works perfectly. I can hold my hand out several inches from the left side fan vent and feel the warmer air blowing on my hand.

Just wondering if the problem is in Toshiba, the distro used, or adjustments made by the operator, perhaps unknowingly when making choices in updates, etc, when doing the installation of the Ubuntu. When I did mine I just said "Y" to all of the updates and everything seems to work fine.

---

### Post by lazypeterson on 2010-07-14
> **ashima said:**
> This was almost doing my head in.
Thought about having to run Windows or sell my new laptop.
Same fan problems with Fedora, PClinuxOS
Here is what works for me. Toshiba L500. 64bit Ubuntu 10.04

                                 first. sudo apt-get install sensors-applet
next. sudo sensors-detect

next. answer yes to everything.

exit then restart computer.

next. sudo gedit /etc/default/grub and then change

GRUB_CMLINE_LINUX_DEFAULT="quiet splash"

to read

..."quiet splash acpi_osi=Linux"

next. sudo update-grub to update /boot/grub/grub.cfg

exit then restart computer.


MY FAN NOW STOPS AND STARTS WHEN IT SHOULD



Hope this helps.

I did all of this up until the point:

sudo gedit /etc/default/grub

My grub file is completely blank, so I couldn't replace anything. I'm on 9.04, if that helps.

---

### Post by lazypeterson on 2010-07-14
> **lazypeterson said:**
> I did all of this up until the point:

sudo gedit /etc/default/grub

My grub file is completely blank, so I couldn't replace anything. I'm on 9.04, if that helps.

Alrighty, my bad. I updated to Grub2 and was able to change it. Still no dice though :(

---

### Post by corrytonapple on 2010-07-14
Same for me on a L455. I can feel the heat coming out of the keyboard. :-k

---

### Post by mörgæs on 2010-07-15
I know that this is a long shot, but if everything else fails you could try installing 10.10 and see if that works better:

[http://www.ubuntu.com/testing/maverick/alpha2](http://www.ubuntu.com/testing/maverick/alpha2)

All standard warnings apply: This is in development and might change without warning (and so on and so on).

Best is doing a clean install, not an upgrade.


Updating the BIOS is 'another last attempt' that might be worth considering.

---

### Post by lazypeterson on 2010-07-18
bump

---

### Post by lazypeterson on 2010-07-25
bumpppp

---

### Post by NGagnon on 2011-01-01
Instead of "acpi_osi=Linux", try adding only "acpi_osi=" instead.  I tried this on my L305D and the fan and brightness keys work now.  According to a kernel parameter document I found, not specifying an os disables the _osi method, which apparently solved my problem.

I hope this helps someone else!

---

### Post by c00lwaterz on 2011-01-01
> **NGagnon said:**
> Instead of "acpi_osi=Linux", try adding only "acpi_osi=" instead.  I tried this on my L305D and the fan and brightness keys work now.  According to a kernel parameter document I found, not specifying an os disables the _osi method, which apparently solved my problem.

I hope this helps someone else!

are you using toshiba laptop? what machine you use?

---

### Post by NGagnon on 2011-01-02
I'm using a Toshiba Satellite L305D with Ubuntu 10.04

Also, it has the Insyde H2O BIOS

---

### Post by c00lwaterz on 2011-01-04
> **NGagnon said:**
> I'm using a Toshiba Satellite L305D with Ubuntu 10.04

Also, it has the Insyde H2O BIOS

my fan still don't work with bios upgrade 2.4 :confused:

---

### Post by c00lwaterz on 2011-01-04
> **NGagnon said:**
> I'm using a Toshiba Satellite L305D with Ubuntu 10.04

Also, it has the Insyde H2O BIOS

my fan still don't work with bios upgrade 2.4 :confused:

---

### Post by azitizz on 2011-02-16
> **NGagnon said:**
> Instead of "acpi_osi=Linux", try adding only "acpi_osi=" instead.  I tried this on my L305D and the fan and brightness keys work now.  According to a kernel parameter document I found, not specifying an os disables the _osi method, which apparently solved my problem.

I hope this helps someone else!

It Did!!!! Thank you! i have a Satellite L350D and Its been the thorn in my side not having the fan working since I upgraded to 10.01. Awesome!

---

### Post by dadimix1 on 2011-03-24
> **dresnu said:**
> This solved it for me on a 64-bit installation too.

Thanks
5 thumbs for you. Good job. It works just fine. 
I thought my fan is non stop running. Finally it stopped when temperature gets low.

---

### Post by rickNS on 2012-01-21
This thread is old, and took awhile to find, but I am quite new, and it was worth the hunt.

 Ashima THANKS your solution helped me, I may have had to give up otherwise.

 My laptop is not a toshiba, but an acer 5315, and I'm not ubuntu, but mint 9.

Funny the same distro worked fine on my acer netbook and not on this my main computer. Anyway it is fixed now, and running at about 55 degrees C. Cool !

 This is just about the last part of my linux puzzle. Except to download, and try a video editor. Then windows...no more ! Time to make a donation.

 PS, my first post on this forum, Nixie pixel says it's the best.

 Rick

---

### Post by SyniTh on 2012-07-11
I typed sudo gedit /etc/default/grub

Command not found.

---

