---
title: "Connection assistance required please"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by davidwroe on 2010-06-29
Hi I have just dowloaded the latest ubuntu but cannot get it to recognise my Cosmote mobile broadband - ([ZTE]("file://\\ZTE") modem) apparently Cosmote told someome connection is not possible!! Help please anyone - magoo

---

### Post by okplayer02 on 2010-06-30
you can take a look at this how to i found

either you can install wvdial or umtsmon so its up to you 

[http://www.void.gr/kargig/blog/2009/07/08/vodafone-cosmote-3g-on-linux-wvdial-and-umtsmon/](http://www.void.gr/kargig/blog/2009/07/08/vodafone-cosmote-3g-on-linux-wvdial-and-umtsmon/)

so i hope it helps you.

---

### Post by gandaran on 2010-06-30
does ubuntu detect your modem? if not then just install usb-modeswitch and usb-modeswitch-data from the repositories (use a cable ethernet internet connection or download these packages to a pen drive) then use the network manager mobile broadband option for the setup, you will need some details about your ISP connection requirements like APN and authentication method.

---

### Post by davidwroe on 2010-06-30
thankyou guts  - but as a complete novice (70 yrs old to boot)  this is way above my head - guess I will just have to stick with winxp

---

### Post by gandaran on 2010-06-30
> **davidwroe said:**
> thankyou guts  - but as a complete novice (70 yrs old to boot)  this is way above my head - guess I will just have to stick with winxp

don't give up! this is easy, download using windows the usb-modeswitch  and usb-modeswitch-data packages from [http://packages.ubuntu.com/lucid/allpackages](http://packages.ubuntu.com/lucid/allpackages) ( I'm assuming you have ubuntu 10.04?) then transfer them to ubuntu, to install double click the package, install the data package first then the other, connect the modem, it should be detected now.

---

### Post by davidwroe on 2010-06-30
well sir - it a be easy with your level of knowledge and skill - but to me it is just awesome - having looked at the url you sugessted. perhaps my son can help me using team vision -  thanx anyway for your assistance

---

### Post by gandaran on 2010-06-30
okay, these links should make it easier to download but you still have to click/choose a mirror to download.
[http://packages.ubuntu.com/lucid/all/usb-modeswitch-data/download](http://packages.ubuntu.com/lucid/all/usb-modeswitch-data/download)
[http://packages.ubuntu.com/lucid/i386/usb-modeswitch/download](http://packages.ubuntu.com/lucid/i386/usb-modeswitch/download)

these packages are for Ubuntu 10.04 and 32-bits system, if you are running any other version of Ubuntu please indicate which one.

---

### Post by davidwroe on 2010-06-30
thankyou - Ihave downloaded ad installe the 2 files and nothing appears to have changed!
 
further info that may be relevant
 
I am using Ubunu 10.04  
 
I have not yet installed it - using it from cd that I downloaded and burned yesterday
 
although the Cosmote icon appears on the desktop I am not sure that the modem is being installed - as in windows - anyway I can check this..  Maybe the relevant info is not being passed to Ubuntu?
 
thanx for assistance - magoo

---

### Post by gandaran on 2010-06-30
> although the Cosmote icon appears on the desktop I am not sure that the modem is being installed 
well then the modem is detected! now you need the connection setup, this is the hardest part, click the panel network icon » edit network connections » mobile broadband tab » click the add button » run the setup wizard » choose country and isp provider. you may have to edit the setup depending your ISP connections requirements like APN and authentication method, you can easily find these details from your windows computer mobile broadband setup by opening the properties window, check if it uses dynamic APN, in this case leave the APN box blank in Ubuntu, if it uses a static APN then fill in exactly the same information in the ubuntu setup, its easy if you can just copy the needed details from the windows computer.
and you will have to do this every time you run the live cd, why not install it on the computer.

---

### Post by davidwroe on 2010-06-30
well the reason I have not installed it is because I have had difficulties with it in the past - and I just dont find it easy to use - I have followed your advice and it still does not work - it is not identified as apossible connection - so until this is sorted  there is no poit in installing it.  I have to say in this respect  windows is easy - put the dongle in and it self installs and just runs!!  
 
So now I have no idea how to proceed from here  I must be omitting to do something. - magoo

---

### Post by davidwroe on 2010-06-30
Just like to thank those who have offered assistance.    Any further  helpful suggestion would be very  welcome.  I really would like to give Ububtu a run out  -  magoo

---

### Post by gandaran on 2010-06-30
> I have to say in this respect windows is easy - put the dongle in and it self installs and just runs!! 
yes windows is easy and why? because your ISP installs windows drivers when you plug the dongle in, why don't they do the same for Linux?
Linux users have to make it work themselves and I can say I find it a enjoyable challenge getting thinks to work, thats one of the reasons I love Linux

> I have followed your advice and it still does not work - it is not identified as apossible connection
did you run the setup wizard? what have you done so far?

---

### Post by davidwroe on 2010-07-01
Ok I stand rebuked - I have run the wizard - filled in country,  isp -   and apn was automatically identified - I filled in name and password and entered Cosmote pin #   and applied.   Still says  'no network'

---

### Post by gandaran on 2010-07-01
> **davidwroe said:**
> Ok I stand rebuked - I have run the wizard - filled in country,  isp -   and apn was automatically identified - I filled in name and password and entered Cosmote pin #   and applied.   Still says  'no network'
are you sure the APN was the correct one? (was it 'internet') did you check the Cosmote properties in windows?
and do you really need a username and password? most mobile broadband ISP's don't use it, I don't know what the Cosmote specifications are, I'm just trying to help with some of my experience with mobile internet.
and the pin you only enter it if its enabled in the dongle sim card, if you don't have to enter the pin in windows every time you connect to Cosmote internet then probably its disabled. 
also don't forget the authentication method.

---

### Post by davidwroe on 2010-07-01
Hi  I appreciate the trouble you are taking (ubuntu!)   the computer selects  the APN = '3g internet'
I have re-installed without name -password - pin - cant find anything in windows setup re authenticain method.   When I played around  with Ubuntu 9.10  sometime ago  connection was simple to install with instant internet connection. - magoo

---

### Post by davidwroe on 2010-07-01
Mind you I was using Win Vista at that time - would that have made any difference?

---

### Post by davidwroe on 2010-07-01
hi  I looked at vmdial and uptsmon but have no idea how to proceed - can you asist please ?

---

### Post by davidwroe on 2010-07-01
well gandaran thanyou  for all your efforts on my behalf - reading up it does seem that others have had a similar problem.  Some problem with the modem I read.   I will keep reading up and trying new ideas as they come along  -  many thanks again  - magoo

---

### Post by gandaran on 2010-07-02
> **davidwroe said:**
> well gandaran thanyou  for all your efforts on my behalf - reading up it does seem that others have had a similar problem.  Some problem with the modem I read.   I will keep reading up and trying new ideas as they come along  -  many thanks again  - magoo
hi again
I don't think it's a modem problem because it's fully detected by Ubuntu (the desktop icon) the problem must be in the login details if you cant find those details in Cosmote windows setup properties then contact you internet provider ask them if a password is needed and what type of APN and athentication method they use.
that '3g internet' APN is probably wrong, try deleting it and just leave it blank (this is equivalent to dynamic APN) ad try selecting CHAP authentication method fist, if it doesn't work with CHAP then try others one at a time.
and you will probably face another problem, sometimes a reboot is needed for the setup to work which is impossible if you are  running the live cd, better to install Ubuntu first.

---

### Post by davidwroe on 2010-07-02
ok I have now installed Ubutu and run through the procedures as you suggested with no luck. However foud an article about wvdial and cosmote dongles and linux - all necessary settings for getting online with wvdial are displayed. So I downloaded wvdial and now have it on my ubuntu desktop. but when I click on the wvfolder it just shows the files - how do I 'run' the programme please?   Can you help with this one please.

---

### Post by gandaran on 2010-07-02
> **davidwroe said:**
> ok I have now installed Ubutu and run through the procedures as you suggested with no luck. However foud an article about wvdial and cosmote dongles and linux - all necessary settings for getting online with wvdial are displayed. So I downloaded wvdial and now have it on my ubuntu desktop. but when I click on the wvfolder it just shows the files - how do I 'run' the programme please?   Can you help with this one please.
what type of package did you download? if it is .deb you just double click them to install, if they are not .deb I recommend to download from the earlier post ubuntu repository link I mentioned.

I went  thought the same problem as you the first time I tried mobile internet, I couldn't find any useful instructions and the forums wouldn't help to, some said my modem wouldn't work, others said to use wvdial which I didn't want to so I don't know how to use wvdial, I'm sorry cannot help here. 
in my case I spent nearly a whole day trying to get it working using network manager, was just about to give up but then came a bright idea of checking the Windows mobile setup and comparing it to the Ubuntu setup, that was the trick, its very easy once you know the correct necessary details to fill in! 
good luck with wvdial then.
bye.

---

