---
title: "Kb2kskype"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by 1numchucks on 2009-03-10
I am up and running with a cordless phone on Ubuntu 8.10. I used Kb2Kskype program. I had already bought a usb phone adapter for use under windows called the telbox.  The only thing that bothers me is that unless I install these programs in Ubuntu inside Windows I can not get it work. I had tried it on a hard drive with only Ubuntu on it but it had problems configuring the usb port.  I am curious if any one has been able to run this program only on Ubuntu not inside of windows as I would like to be MS free on my 2nd hard drive.

---

### Post by altariel on 2009-03-19
sorry to hear about your problems with the kb2kskype ... 
could you please be a little more specific? 

I will try to build the new packages this weekend, and if you'd have time to help me troubleshoot it'd be great! 

some people have reported better audio quality if using an externally powered usb-hub or an usb-pci-card, maybe you could try that?

---

### Post by art_erickson on 2009-03-24
Is there a repository for Synaptic to get kb2kskype?

---

### Post by altariel on 2009-03-29
> **art_erickson said:**
> Is there a repository for Synaptic to get kb2kskype?

I have set up a launchpad account so the plan is to try have a ppa for it ... for now, try the freshly built binary packages, please ...

---

### Post by altariel on 2009-04-02
> **art_erickson said:**
> Is there a repository for Synaptic to get kb2kskype?
yes, now it should be :) 

my ppa lauchpad archive I set up (for hardy right now, will try to get at least intrepid as well) 

[https://launchpad.net/~alatariel/+archive/ppa](https://launchpad.net/~alatariel/+archive/ppa)

I think it should suffice to 
a) add the ppa to your apt sources list 
b) import the key (as per instructions on the page above)
and 
c) sudo apt-get install kb2kskype 
(this -should- pull in the usbb2k-api-mod as well)

---

### Post by art_erickson on 2009-04-02
Ooooh, this is looking good.  Is there a difference in the binary between Hardy and Intrepid?  More directly, should I wait?

Thanks a lot for the effort.  I'm not fond of dealing with binary installs.  Being retired I seem to have lost patience in my old age - I just want things to work.  At which point one has to ask, so why are you messing with a unix based operating system :)  Masochism?

---

### Post by art_erickson on 2009-04-04
I noticed the the new path for Intrepid so I tried it.

Good news - software installs great.

Bad news - it doesn't work for my D-link DPH-50U.

Oh well, it was worth a try.

It also gets errors about kdecache being the wrong uid (1000 - me, instead of 0).

I also get a lot of "Card not found" messages.

Thanks for the effort tho.  You really do work hard to make this easy for the rest of us.

Too bad D-link refuses to write a Linux driver for their hardware.  No more Kodak (they refuse to provide a driver for my printer) and no more D-link for me.

---

### Post by altariel on 2009-04-10
but what does the D-link have to do with the telbox? *somewhat confused* 
that D-link sounds like a router och some such thing, the telbox is only the bridge from the computer to the phone ... 
ah, some googling revealed that it indeed is a kind of bridge too ... 
do you mean you got this exact same stuff working in a virtual box with kb2kskype but it doesn't work natively?

---

### Post by art_erickson on 2009-04-10
When I first started experimenting with Skype I was tethered to the headset.  That was ok because it was just an experiment.  As I found I was able to use Skype reliably I wanted the ability to move about.

I tried a Bluetooth earpiece and was able to get that working.  I use Windows XP and Ubuntu and the greater challenge was always making things work in Ubuntu.  Even tho the Bluetooth earpiece was functional the range was severly limited.

I investigated other options such as a Wi-Fi phone but the cost was prohibitive.

Then I read about a USB to POTS (now called PSTN) phone adapter.  Wow, can I really use my home wireless handset with Skype?  Why, yes I can!  That's where the D-Link DPH-50U adapter comes in.  Skype sees the USP device as an audio device and the driver handles the phone part of it.

What I didn't know is D-Link provides a driver only for Windows (insert curse words here) and does not seem at all interested in providing a Linux driver - bad PR move guys.

Doing some research I discover something called B2K Telbox.  I have no idea what that acronym means but it a appears a company called Yealink sells them.  Since I already had an adapter box I was more interested in finding a driver.

I read about kb2kskype and wondered if it would work.  I have no idea if a D-Link USB adapter is B2K compatible or not but I suffer from masochism (with a particular fetish for Linux) so I was willing to experiment.

I appreciate the work people like you put into making this stuff easier for the amoeba-level users such as myself.  I refuse to consider compiling a kernel and am fast getting to where if it's not in a repository I'll just wait.

So there is more than you ever wanted to know :)  I will continue to work on this as long as I have the will power.  The D-Link box is being recognized by Ubuntu as a softmodem but kb2kskype doesn't recognize it at all.  I believe that goes back to being B2K (whatever that is) compatible.

---

### Post by 1numchucks on 2009-04-18
News with update.

I am running this now without being under MS windows.  That is right Ubuntu on its own.  It works great 98% of time.  The other 2% from what I have been reading is due to power issues. That is getting enough power to my telebox. The great Altariel has suggested that some people have reported better audio quality if using an externally powered usb-hub or an usb-pci-card, maybe you could try that? 

Most of the time sound is perfect but the other 2% I will try to solve with more power to the unit.

---

### Post by art_erickson on 2009-04-18
1num,

What make and model of telbox are you using?

Thanks.

---

### Post by brian_p on 2009-04-21
> **altariel said:**
> 

my ppa lauchpad archive I set up (for hardy right now, will try to get at least intrepid as well) 

I think you wanted reports on the packaging of usbb2k-api-mod and kb2kskype. While I'm using Debian stable this could apply to your Ubuntu packages too.

Using dpkg -i I installed kb2kskype_0.3.8-1_i386.lenny5.deb and usbb2k-api-mod_2.8-1_i386.lenny5.deb, which were obtained from the Sourceforge site.

Then:

```
brian@laptop:~$ sudo apt-get remove --purge usbb2k-api-mod
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED
  kb2kskype* usbb2k-api-mod*
0 upgraded, 0 newly installed, 2 to remove and 3 not upgraded.
After this operation, 659kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 94132 files and directories currently installed.)
Removing kb2kskype ...
Purging configuration files for kb2kskype ...
Removing usbb2k-api-mod ...
Stopping usbb2k-api-mod: usbb2k_api.
find: `/etc/rc.d/': No such file or directory
dpkg: error processing usbb2k-api-mod (--purge):
 subprocess post-removal script returned error exit status 1
Processing triggers for man-db ...
Processing triggers for menu ...
Errors were encountered while processing:
 usbb2k-api-mod
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It's the postrm script looking for /etc/rc.d which causes the problem. Worked round with:

```
sudo rm /etc/init.d/usbb2k-api-mod
```

```
sudo rm /var/lib/dpkg/info/usbb
```

and

```
sudo update-rc.d usbb2k-api-mod remove
```

---

### Post by Slaskpelle on 2009-06-02
Hello, as i understand it this program requires ALSA to work properly, however I can't use ALSA since there's just too many problems with my setup. OSS4 works like a charm, and so does skype with OSS support. I've successfully compiled both usbb2k-api-mod-2.8 and kb2kskype-0.3.8 on x64 Jaunty. the api is working spot on, however when i try to start kb2kskype i get flooded with the following, this happens both as root and user. Is this related to OSS4? Can this work or am I trying in Vain? 

Thanks, 

QFile::atEnd: File is not open
QFile::getch: File not open
QFile::atEnd: File is not open
QFile::getch: File not open
QFile::atEnd: File is not open
QFile::getch: File not open
QFile::atEnd: File is not open
QFile::getch: File not open
QFile::atEnd: File is not open
QFile::getch: File not open
QFile::atEnd: File is not open
QFile::getch: File not open
QFile::atEnd: File is not open
QFile::getch: File not open
QFile::atEnd: File is not open

---

### Post by bugtussle on 2009-07-07
> **1numchucks said:**
> News with update.

I am running this now without being under MS windows.  That is right Ubuntu on its own.  It works great 98% of time.  The other 2% from what I have been reading is due to power issues. That is getting enough power to my telebox. The great Altariel has suggested that some people have reported better audio quality if using an externally powered usb-hub or an usb-pci-card, maybe you could try that? 

Most of the time sound is perfect but the other 2% I will try to solve with more power to the unit.

Are you saying that you were able to get the D-Link DPH-50U to work? Its the one thing that keeps me running one Windows machine.

---

### Post by 1numchucks on 2009-07-10
No it is the Usb telebox sold by yealink
here is a product descripton from ebay


[http://cgi.ebay.com/USB-Skype-MSN-VoIP-to-PSTN-RJ11-Cordless-Phone-Adapter_W0QQitemZ350174713044QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item51880a14d4&_trksid=p3286.c0.m14&_trkparms=65%3A12|66%3A2|39%3A1|72%3A1234|293%3A1|294%3A50](http://cgi.ebay.com/USB-Skype-MSN-VoIP-to-PSTN-RJ11-Cordless-Phone-Adapter_W0QQitemZ350174713044QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item51880a14d4&_trksid=p3286.c0.m14&_trkparms=65%3A12|66%3A2|39%3A1|72%3A1234|293%3A1|294%3A50)

---

### Post by exjinn on 2009-08-10
I wrote about [my success with this setup under Jaunty ]("http://www.jinnfire.info/606/adventures-in-skype/")

---

### Post by Surabaya on 2009-09-20
Hi Exijinn, 

I read your blog and it seems simple and easy to ibstall. You just install "kB2Kskype software which requires usbb2k-api-mod2.8 (both available from the kb2skype site), and kdelibs4c2a (available via apt-get) once installed everything just worked.", only? And it works directly? So simple? No bugs, echo, cut conversatioçns, long setup by shell...?
I am planning to buy a such USB Telbox Phone Adapter,and run it under Ubuntu 9.10. If so easy to setup, i will buy it tommorow morning!

Waiting your comments. Thanks in advance.

Surabaya

> **exjinn said:**
> I wrote about [my success with this setup under Jaunty ]("http://www.jinnfire.info/606/adventures-in-skype/")

---

### Post by exjinn on 2009-09-20
> **Surabaya said:**
> Hi Exijinn, 

I read your blog and it seems simple and easy to ibstall. You just install "kB2Kskype software which requires usbb2k-api-mod2.8 (both available from the kb2skype site), and kdelibs4c2a (available via apt-get) once installed everything just worked.", only? And it works directly? So simple? No bugs, echo, cut conversatioçns, long setup by shell...?
I am planning to buy a such USB Telbox Phone Adapter,and run it under Ubuntu 9.10. If so easy to setup, i will buy it tommorow morning!

Waiting your comments. Thanks in advance.

Surabaya

This was all *I* had to do to get this working. Your mileage may vary. :)

---

### Post by Surabaya on 2009-09-20
Hi exjinn, 

THanks for your answer: look likes I am on my way to buy it.

---

### Post by jwaclawsky on 2009-10-17
Hi Exijinn,

I read your blog and I am fairly new to Linux. I have been using it and supporting myself for 6 months now. I have a Dell mini 9 running Ubuntu 9.04 and I am a skype user. I also have a USB Telbox and would like to get it working but I am confused about how to execute the steps you outlined in Part 2 on your blog that install the necessary files. When I click on the kB2Kskype hot link it takes me to a web page with usbb2k-api-mod2.8 listed and when I try a download that name, I wind up at another page with lots of file choices and I am not sure what to do at this point. I don't want install the wrong thing and possibly mess up my system which is running great. My question is: Can you point me to someplace where I can find more detailed instructions. Or, if you have time could you post some very detailed step by step guide for us novices who would like to have Skype working through a normal phone (using Telbox) while roaming around our homes. Many Thanks in advance.

---

### Post by anewguy on 2009-10-17
OOPPSS - I removed the text of this post since it was erroneous.

Sorry!

dave :)

---

### Post by anewguy on 2009-10-17
OOOOOPPPPPSSSSSS - my mistake!  1numchucks *WAS* asking about the yealink type box - my bad!   However, the rest of my reply still applies.  I also had problems using k2b and the api reliably - I ended up starting 1 on them, then just dialing on the phone because the interface to the box wasn't working correctly.  

The sourceforge link is:

[http://sourceforge.net/projects/kb2kskype/develop]("http://sourceforge.net/projects/kb2kskype/develop")

As mentioned in my previous bad post, the software was written to support b2k type boxes - the kind like the yealink boxes.

Sorry for my bad post!!!

dave :)

---

### Post by Surabaya on 2009-10-17
Hi jwaclawsky,

Sorry but at this time I cannot help you until i didn't buy yet this Telbox Phone Adapter. But as i said previously in a post i am very curious to know about users' experience with Telbox Phone Adapter under Ubuntu/ Linux.
If finnally you get success in installing it, could you share your experience about installation process, quality of the sound when you call, is there any bug of problem... For exjinn, it is already a sucess. But I am still waiting an other success story with Telbox-Linux to be convince to buy one.
Thanks in advance for your help.

Surabaya


> **jwaclawsky said:**
> Hi Exijinn,

I read your blog and I am fairly new to Linux. I have been using it and supporting myself for 6 months now. I have a Dell mini 9 running Ubuntu 9.04 and I am a skype user. I also have a USB Telbox and would like to get it working but I am confused about how to execute the steps you outlined in Part 2 on your blog that install the necessary files. When I click on the kB2Kskype hot link it takes me to a web page with usbb2k-api-mod2.8 listed and when I try a download that name, I wind up at another page with lots of file choices and I am not sure what to do at this point. I don't want install the wrong thing and possibly mess up my system which is running great. My question is: Can you point me to someplace where I can find more detailed instructions. Or, if you have time could you post some very detailed step by step guide for us novices who would like to have Skype working through a normal phone (using Telbox) while roaming around our homes. Many Thanks in advance.

---

### Post by jwaclawsky on 2009-10-18
My problem is that when I go to Exjinn's blog and follow the kB2Kskype hot link it takes me to a web page with usbb2k-api-mod2.8 listed and when I try a download it, I wind up at another page with lots of file choices and I am not sure what to do at this point. I don't want install the wrong thing and I am now confused and wanted to know if there is someplace where I can find more detailed instructions. Or, if Exjinn could post some very detailed step by step guide of how to accomplish Part2 that he talks about on his blog.

---

### Post by Surabaya on 2009-10-18
Ok I checked for you.

You said you use ubuntu 9.04, but you didn't mentionned 32 bits ou 64 bits.But the problem is that there is no files for Ubuntu but for Kubuntu.
I use also Ubuntu 9.04, so if I had to install it, I will choose the Kubuntu Package first. If not working, I will try the Debian one.
But if you are afraid to put a mess in your machine, better wait exjinn comments.

But if you want to try now, don't forget to choose between 32 and 64 bits.

Surabaya







> **jwaclawsky said:**
> My problem is that when I go to Exjinn's blog and follow the kB2Kskype hot link it takes me to a web page with usbb2k-api-mod2.8 listed and when I try a download it, I wind up at another page with lots of file choices and I am not sure what to do at this point. I don't want install the wrong thing and I am now confused and wanted to know if there is someplace where I can find more detailed instructions. Or, if Exjinn could post some very detailed step by step guide of how to accomplish Part2 that he talks about on his blog.

---

### Post by jwaclawsky on 2009-10-19
I am running a Dell Mini 9 with Intel Atom CPU N270 @ 1.60GHz which is a 32 bit architecture. I have 2 GiB of memory and running Ubuntu 9.04 (jaunty). Could you give me some specific advice about what files to use and how to get the files installed (I am a Linus novice) to get my Telbox working. I would appreciate the assistance. Thanks!

---

### Post by anewguy on 2009-10-20
I would seriously suggest you view the information, downloads available, and the support forum for this at:

[http://sourceforge.net/projects/kb2kskype/]("http://sourceforge.net/projects/kb2kskype/")

Asking questions on that support forum will get you the answers you are looking for, and you'll be dealing with the developers.

Dave :)

---

### Post by jwaclawsky on 2009-10-20
Thanks anewguy. I'll try the other forum

---

### Post by anewguy on 2009-10-22
For anyone still watching this thread, here's the link to my very old thread about my success.  The thread also contains info from other posters about such things as using a powered USB hub, etc..  Maybe it will be useful to anyone still following this thread.

[http://ubuntuforums.org/showthread.php?t=679498]("http://ubuntuforums.org/showthread.php?t=679498")

Dave :)

---

### Post by 1numchucks on 2009-10-30
For me this program works great in ubuntu. I have had it working in Ubuntu 8.10 and 9.04. This is what I did. 1st download skype. Next go to this page [http://sourceforge.net/projects/kb2kskype/files/](http://sourceforge.net/projects/kb2kskype/files/) 
For Ubuntu just download the deb files. I did not fool with the files that ended in rpm,
The 1st program you need starts with usbb2k 
If you run Ubuntu 8.10 or 9.04 look for this program 
usbb2k-api-mod_2.8-1_kubuntu810.deb
Istall the download.
Next download the deb file that starts with Kb2kskype
for ubuntu 8.10 and 9.04 download this file
kb2kskype_0.3.8-oubuntu1_i386_kubuntu810.deb
Install program.
Note I upgraded ubuntu 9.04 to 9.10 and the program quit working.  

I am extreamly happy with this program due to my only home phone is skype. Because of this program working so good I only run windows less than 1% of the time now.

---

### Post by 1numchucks on 2009-10-30
After you download you can restart the computer to see if the usbb2k program is stating up automatically on start up. You won't see it but if it does not start then the next steps won't work. 
Next thing to do is 1st open Skype.
2nd open a terminal under ubuntu Applications- Accessories- Terminal
Then type kb2kskype then hit enter. 
That should activate your phone.
Make sure under the b2k controller for kb2skype to choose usb for it to make calls with the internet.

---

### Post by 1numchucks on 2009-10-30
One last thing I did was to go System-Preferences-Startup Applications
click +add and in all 3 spaces type 
kb2kskype

also the same prosess for skype. 

This caused skype and kb2kskype to start up automatically when you start the computer.  These guys wrote a hell of a program and I am very thankful for all the hard work they have done.

---

### Post by art_erickson on 2009-10-31
I guess I need to get one of those European boxes instead of the D-Link one I have now.

Using Skype with the headset in Ubuntu is unacceptable.  I hear the other party fine but they report very poor audio.

---

### Post by Surabaya on 2009-11-01
Hi 1numchucks, 

Oups! I just ordered my Telbox and also upgrade yesterday on Ubuntu 9.10. So for you in 9.10 it is not working anymore? Could you tell me more about that?

Did you plugged a DECT phone on that box? What are your comments about this box + those software? Any bug? The sound is good (you can hear clearly and people hear you also clearly) Any bug, like hang up, strange noises....

Thanks in advance for your feedback.




> **1numchucks said:**
> For me this program works great in ubuntu. I have had it working in Ubuntu 8.10 and 9.04. This is what I did. 1st download skype. Next go to this page [http://sourceforge.net/projects/kb2kskype/files/](http://sourceforge.net/projects/kb2kskype/files/) 
For Ubuntu just download the deb files. I did not fool with the files that ended in rpm,
The 1st program you need starts with usbb2k 
If you run Ubuntu 8.10 or 9.04 look for this program 
usbb2k-api-mod_2.8-1_kubuntu810.deb
Istall the download.
Next download the deb file that starts with Kb2kskype
for ubuntu 8.10 and 9.04 download this file
kb2kskype_0.3.8-oubuntu1_i386_kubuntu810.deb
Install program.
Note I upgraded ubuntu 9.04 to 9.10 and the program quit working.  

I am extreamly happy with this program due to my only home phone is skype. Because of this program working so good I only run windows less than 1% of the time now.

---

### Post by 1numchucks on 2009-11-01
The last download on the download page was for kubuntu 8.10 
I do not know why it does not work with ubuntu 9.10 
But I can guess why it does not. I know when under skype you must set up your audio under options- sound devices for Voip usb phone (plughw:default.0)  On ubuntu 9.10 it does not reconize the Voip USb phone.
It may be a simple fix but I have not taken the time to find it. 
The 9.10 is my experimental copy as my main copy of Ubuntu must run this program without a glitch.

---

### Post by 1numchucks on 2009-11-01
If under earlier Ubuntu programs. Your phone should work just as it would if it were plugged into the wall for the phone company. One glitch that some have complained about is the double ringing your hear when you call someone. It sounds like your cordless phone is ringing the person with a 2nd ringing coming from skype.  Sometimes when I am taking once in about 100 calls the dial tone will kick on during the conversation. To make it go away just press any key button  on your cordless phone and it is back to trouble free talking. Takes about a second to fix. No other glitches. I have a great cordless phone I can walk about 3-4 houses down all the way to the stop sign and talk. If you have a dect phone you should get good results as well.

---

### Post by Surabaya on 2009-11-03
Hi 1numchucks,



Firts many thank for all those informations, they are very useful for me.

Few questions:

- When you said "it does not reconize the Voip USb phone", you mean the USB Box rigth? Because if you are really talking about a USB Phone, for me no problem until I will use a DECT one.
- Regarding your experience, what could be buggy under Ubuntu 9.10, the communication between the Voip Box and Skype? If yes, again no problem for me, until I think I will stop to use Skype and replace it by real Voip. Indeed i will use Voip until they claim this box is working with Voip providers;
[http://cgi.ebay.com/USB-VOIP-SKYPE-to-RJ11-Home-Cordless-Phone-Adapter-B2K_W0QQitemZ190258557374QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item2c4c4b31be](http://cgi.ebay.com/USB-VOIP-SKYPE-to-RJ11-Home-Cordless-Phone-Adapter-B2K_W0QQitemZ190258557374QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item2c4c4b31be)

 Did you tried Voip? Any comments about this Voip will be very welcome.

Regards, 

Surabaya




> **1numchucks said:**
> If under earlier Ubuntu programs. Your phone should work just as it would if it were plugged into the wall for the phone company. One glitch that some have complained about is the double ringing your hear when you call someone. It sounds like your cordless phone is ringing the person with a 2nd ringing coming from skype.  Sometimes when I am taking once in about 100 calls the dial tone will kick on during the conversation. To make it go away just press any key button  on your cordless phone and it is back to trouble free talking. Takes about a second to fix. No other glitches. I have a great cordless phone I can walk about 3-4 houses down all the way to the stop sign and talk. If you have a dect phone you should get good results as well.

---

### Post by 1numchucks on 2009-11-11
I no longer have ubuntu 9.10 as it had too many bugs for me. My speakers no longer worked.  Also my mic would not work. And of course my usb phone.  I only run 9.04 and everything works fine.

---

### Post by anewguy on 2009-11-11
I'm guessing here, because it's been quite a while since I used kb2kskype, but I remember at the time it was based on a certain kind of messaging, and I thought I remembered reading something in the 9.10 release notes about 1 of the "internals" changing, and I believe it was removing what supported that messaging - but I'm not really sure yet.  Would require me going back to look at kb2kskype in detail again and then reviewing the release notes again, and since I no longer use Skype it just seems like a waste of time for me to do so, but perhaps someone else can?

As far as the D-Link box goes, no, it won't be supported.  This software is specifically for the b2k based boxes.

Dave :)

---

### Post by Surabaya on 2009-11-29
Hi,

I just received my Telbox yesterday, so I tried to use it under Ubuntu 9.10 and 9.04; for both the result is the same: the sound is coming out only from the speakers, not from the DECT phone plugged on the box. From the phone I can dial a number but I cannot speak and hear anything. But I am not very suprised because on the sound preference of skype I cannot choose the VOIP USB in the menu for the speakers and microphone. I can only choose my internal audio card (Pulse Audio Server (local)).

For your information, I installed the Debian Lenny package usbb2k-api and usbb2k, not the kubuntu package. The problem could come from that?

For information this is my cat /proc/asound/cards:

0 [Intel ]: HDA-Intel - HDA Intel HDA Intel at 0xe1280000 irq 16 1 [default ]: USB-Audio - VOIP USB Phone
Yealink Network Technology Ltd. VOIP USB Phone

Any help please, I really would like to make this box working. Thanks in advance!





> **1numchucks said:**
> The last download on the download page was for kubuntu 8.10 
I do not know why it does not work with ubuntu 9.10 
But I can guess why it does not. I know when under skype you must set up your audio under options- sound devices for Voip usb phone (plughw:default.0)  On ubuntu 9.10 it does not reconize the Voip USb phone.
It may be a simple fix but I have not taken the time to find it. 
The 9.10 is my experimental copy as my main copy of Ubuntu must run this program without a glitch.

---

### Post by Surabaya on 2009-12-12
Hi again,

I just solved my problem, by creating a file named asoundrc in my home folder and adding the following lines:


pcm.skypeout
{
type plug
slave.pcm « dmix »
}
ctl.skypeout
{
type hw
card 0
}
pcm.skypein
{
type plug
slave.pcm « input »
}
ctl.skypein
{
type hw
card 0
}


And it works!

Hopes that it can help some people.

Regards,

Surabaya

---

### Post by rykel on 2010-01-29
Hi,

I am trying to remove usbb2k-api-mod, but I get the following error message... please advise?

No matter which program I use (apt-get, aptitude, Synaptic Package Manager) I cannot resolve the problem.

> Removing usbb2k-api-mod ...
find: `/etc/rc.d/': No such file or directory
dpkg: error processing usbb2k-api-mod (--remove):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for ureadahead ...
Errors were encountered while processing:
 usbb2k-api-mod
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by rykel on 2010-01-29
Hi, I solved my own problem. I simply created the missing directory and removed the file as normal, and it worked. Thanks for reading.

[B]sudo mkdir /etc/rc.d
Remove usbb2k-api-mod as normal
[/B]

---

### Post by zarthon on 2010-03-19
Has anyone gotten kb2skpye an FT-102 and skpye configured to work on 9.04, 9.10, or soon to be release 10.04? :D
If so do you run pulseaudio ?

i am starting to configure the Freshtel FT-102 VoIP USB Phone
I am running Ubuntu 9.10
After When i plug in the FT-102 it shows up in pulse audio output and input lists as:
FT-102 Phone Analog Mono
and it seems to bind to a driver called yealink
***This is without kb2skype or the module.***

I have tired to get the FT-102 to work with Skype with only pulseaudio but [no shocker here] so far it does not work. I believe that the kb2skpye may be necessary for among other things, dialtone, conversion of touch tones, and signaling an attached phone to ring. If i even get basic talk only to work i'll post back.

I have Skpye working with the Plantronics 995H wireless usb audio headset. Using pulse audio I can direct other programs to use the onboard audio card so I can dedicate this device to skype. 

I suggest that if you have had problems with 9.10 audio, go research Pulseaudio and get that working with your onboard audio and a music player before before starting to get the phone adapter to work. I chat a bit about my pulseaudio experience below.

Cheers + + + + +
Zarthon


[SIZE="1"]**I now go on and on somewhat but someone may find this stuff of use.**
Pulse Audio was introduced in 9.04 and it's a known issue on the forum that upgrading to 9.10 messes up various software mixer settings and also neither really install all the utilities you need. You especially need Gnome ALSA mixer which gives you low level control of your audio interfaces. This gets confusing because pulse has it's own mixer and you have to get every setting write or no yada-yada boom boom for you!

I have Skpye working with a Plantronics 995H wireless usb audio headset. It has a dongle you attach to the comptuer and a large highfi headset that must be charged. The headset has an integrated drop down microphone. I was fairly happy at first this for skpye but the headset is large, gets hot and is very intense. The audio is extremely clear and is channel duplicated stereo. That sounds great but it's just too much for talking on the phone i like to be on a call not immersed. In any case it's been a good solution mostly for outgoing calls when my sprint service is down. I think it may be possible some place to kill the left or right channel but I seriously am digressed to much from the FT-102 and kb2skpy so i made this a "PS"
[/SIZE]

---

