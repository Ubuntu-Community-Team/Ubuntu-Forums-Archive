---
title: "Newbie need help - LinkSys WUSB54GS Wireless"
date: 2005-06-08
forum: Networking &amp; Wireless
---

### Post by Marrojj on 2005-06-08
I'm a Newbie trying to make the jump from Windows XP to Ubuntu. I've made a couple of mistakes trying to get setup - the first of which was to erase my windows partition during the Ubuntu setup * before* making sure the setup was successful. It wasn't ... I couldn't access the internet to track down further assistance, and had to reinstall Windows to make this help request. Live & Learn  :)  Here's my problem:

I have a Linksys WUSB54GS wireless USB internet adapter, which evidently was not detected & installed during setup, and being a complete linux challenged newbie, I have absolutely no idea what to do next. I've read some other posts on different adapters - but I don't understand what the replies are saying to do.

Wold someone take pity on an 'ol Windows user, and help walk me through the setup - or at the least - point me towards a "newbie friendly" help page?

Thanks!

Marrojj

---

### Post by Hobbes on 2005-06-17
Unfortunately, I can't help, but at least I can cry with you... I have a dual booting machine which I brought back from college and recently added this usb adapter to because it is a shuttle and has no free PCI slot... I obviously didn't realize at the time that so few wireless adapters are supported in linux....but at least it works great on my Windows :???: .  Actually that is almost a bad thing as I now almost solely boot into windows, which is exactly what I wanted to get away from!

Anyway, I looked all over and could not find a fix, I have tried ndiswrapper and it seems that at least for now it will not work that way, I did download DriverLoader, but I don't have all the packages that it needs I don't think, so maybe I will give that another try.

In the meantime, GoGo Developer Communtiy or Step up to the plate Linksys!

Which reminds me I'm going to e-mail them and bug them about not having linux drivers, and perhaps you should do the same so that at some point this will stop happening to people.

If you ever find a solution, e-mail me at [email]JTerry828@yahoo.com[/email], in case I don't check here right away, and I will be happy to do the same for you.

Good Luck!

---

### Post by Arktis on 2005-06-18
I've got a WUSB54G (not with speedboost) and I got it running (stubbornly) with ndiswrapper on my laptop.  What I had to do was follow the normal ndis setup steps, then do a couple additional things.

1.) Use the command lsusb to find out what I.D. the adapter has.
2.) Use the command ndiswrapper -d I.D. nameofdriver to associate the two together.  After that, ndis and the adapter play nice... sorta.

It'll freeze on modprobe unless the adapter is unplugged first, and it will also lock up during boot until I unplug it upon which boot continues.  Other than that it works if you don't mind getting your hands dirty.  I've had no problems with it once the adapter gets started up though.

---

### Post by iBuntu on 2005-06-21
I finally got a stable solution using the same device. It involved adding ndiswrapper to modules and adding some general instructions to ifup. When I get home, I'll copy what I entered here. Up time >3 days so far. Loaded automatically on boot.

---

### Post by Hobbes on 2005-06-23
[QUOTE=iBuntu]I finally got a stable solution using the same device. It involved adding ndiswrapper to modules and adding some general instructions to ifup. When I get home, I'll copy what I entered here. Up time >3 days so far. Loaded automatically on boot.[/QUOTE]
 Hey iBuntu hopefully you will check this again, but if you could put up the steps you used (translated for n00b like me) that would be really helpful, thanks.

Arktis I tried to put something together from what you said, and although at one point i got "such and such usb device is associated with the wusb54gs driver" but then nothing happened, i tried iwconfig and nothing was showing up still,  I can't modprobe or I get some fatal error, so yeah either there is more to it and I just don't know what that is, or maybe you could walk me through it exactly as you did it and i can uninstall the driver and try again. (also did you have a sys file cuz i don't, just inf and cat on my cd)

---

### Post by Hobbes on 2005-07-11
Hate to beat on a dead horse here... , but I am really hoping this last kick will help revive it...

Now that some more time has passed, I'm hoping that perhaps a few other users have been dumb enough, i mean fortunate enough, to have this usb wireless solution, and have figured out how to make it work with ndiswrapper or stolen code from linksys and made their own driver, or something along one of those lines...

Anyone out there? Why must you torment me with these answers promising solutions and never delivering on them (although i suppose that is the story of most people's experience with the world of tech)?

Ok, so please help if you can, otherwise i'll resign to using.....  :roll:  well you know..... for the rest of the summer so I can have internet.

---

### Post by coldman on 2005-07-15
[QUOTE=Arktis]I've got a WUSB54G (not with speedboost) and I got it running (stubbornly) with ndiswrapper on my laptop.  What I had to do was follow the normal ndis setup steps, then do a couple additional things.

1.) Use the command lsusb to find out what I.D. the adapter has.
2.) Use the command ndiswrapper -d I.D. nameofdriver to associate the two together.  After that, ndis and the adapter play nice... sorta.

It'll freeze on modprobe unless the adapter is unplugged first, and it will also lock up during boot until I unplug it upon which boot continues.  Other than that it works if you don't mind getting your hands dirty.  I've had no problems with it once the adapter gets started up though.[/QUOTE]

Hi Arktis, me very newbie, just started on linux (ubantu) yesterday, could you explain how you manage to setup the WUSB54G on your laptop?
i tried but it can't even be detected, or i don't know where to find it? ](*,) 
What is the ndis setup steps that you do? and where to do it?
Very sorry! me super super newbie. :? 
Thanks in advance!

---

### Post by Hobbes on 2005-08-18
*Bump?*

Anyone figured out how to work this yet?
If the earlier posts are to be believed, it is in theory possible....

stupid linksys..... and ati.... and audigy2.... why must u plague me!!

---

### Post by edtech on 2005-10-15
I got mine working a few minutes ago.  I also am very much of a newcomer to Linux, so here goes.
First you must get the files WUSB20XP.sys and WUSB54G.inf from your install disk or from Linksys.com
Open the terminal:
type:
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i ~/Desktop/WUSB54G.inf
sudo ndiswrapper -m
for conffile in /etc/ndiswrapper/WUSB54G/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done

Reboot
Go to System>Administration>Networking and set it up.

Note: I had to go through the procedure twice, but once it hit it was fine.

---

### Post by shaunm666 on 2005-10-26
thx for your help edtech, it seems to work better than the other advice i have so far encountered, but...!
after i complete the last set of commands, after hitting "done" i get the following error;

bash: /etc/ndiswrapper/WUSB54G/*.conf: No such file or directory
cat: /etc/ndiswrapper/WUSB54G/*.conf: No such file or directory

Everything seems to work fine up until the last part, PLZ PLZ help as I feel this route is the only way to get my ubuntu onto the net!

Thx
Shaun

---

### Post by vendetta red on 2005-11-08
So the question still stands, will the WUSB54GS work with ndiswrapper without the .sys file or what?

---

### Post by Emmanuel_uk on 2006-04-19
Can please anybody tell me the first 5 or 6 characters of 
any WUSB54GS and the firmware/hardware version,
and whether they made it to work or not.

I will see if I can get a table serial no vs version from linksys
I do believe these are around
               WUSB54GS v1  
               WUSB54GS v1.1  
               WUSB54GS v2  
               WUSB54GS v2.1 

ndiswrapper websiste only quote
WUSB54GSv2
Chipset: Broadcom - BCM4320SKFBG 
usbid: 13b1:0014

---

### Post by Pimpity Snicket on 2006-04-26
I tried getting this adapter working a long time ago but I was unsuccessfull.  As for your question about ndiswrapper, you need a driver for it to work.  It's not a driver set, just a windows driver loader.

---

### Post by Emmanuel_uk on 2006-04-27
I managed to make this WUSB54GS to work
my "mini howto" is at
[http://www.linuxquestions.org/questions/showthread.php?t=356315](http://www.linuxquestions.org/questions/showthread.php?t=356315)

>>As for your question about ndiswrapper
I do not think you got my point. Ndiswrapper says 13b1:0014 will work.
That is the model I managed to get working as well (no credit to me,
the credit is all to the ndiswrapper guys!)
What about 13b1: v1, V1.1, v2.1 ?  This is my question

---

### Post by Jakelshark on 2006-06-07
I have a v1.0 (I think) and havent gotten it to do anything yet

and for your information its SN is MI00000xxxxxx, the USBID is 13b1:000e


If i can figure out the chipset Ill just try another driver for the chipset that does work and use the ndiswrapper -d command.  I dont know if it will work but its the only thing I havent done yet.  (I did do the method 1 on the ndiswrapper wiki, but I think the chipset is different for v2 than v1)

---

### Post by Emmanuel_uk on 2006-06-08
Thanks for the details.

A not of caution, I am currently helping somebody with suse 10,
and that did not work so far.
I tried on suse 10.1 yesterday at home, no luck either.

I feel mandriva does some magic with usb scripts that other distro handle
differently

---

### Post by Jakelshark on 2006-06-12
I talked to Linksys tech support and they said to check the model no. to see what version you have.  If you have nothing (like me) you have v1.  I then asked to know what chipset the card uses, since I couldnt find it online.  Tech support doesnt even know...

for kicks, here is the tail end of the actual chat log because I cant believe how stupid it was

trey: I am trying to use this with a Linux distro, can you tell me what type of chipset the card uses
Robert Francis (13573): Unfortunately, Linksys Technical Support Department does not have any information on the chipset of any device. The only information that we can provide is the one that is on the manual. The manual is also remiss in this respect. 
trey: so you dont know whats in your product...
Robert Francis (13573): That is correct. We do not have that information. 
trey: is it possible for me to get the information from you at all
Robert Francis (13573): One option that you can do is to email us at [email]support@linksys.com[/email] and ask them about your this. Your email may be forwarded to the proper department and you can get a response about that. As for the technical department, we do not have that information.  
trey: fine

So I sent an email asking for the chipset for the v1, as well as the 1.1, 2.0, and 2.1.

---

### Post by Jakelshark on 2006-06-12
My official reply from them,

We appreciate your time in giving us your concern. With regards to this inquiry, I regret to inform you that we are not allowed to make chipset information available for customers. The reason being is that this information is supposedly confidential and should not be disclosed.

This is incredible, why will they not let me know so that I might use my product correctly...

However I was able to get this to work, I used the files off the CD and used method one.  And once I got modprobe to work I was connecting. The problem with the modprobe was the debian package I was using wasnt working correctly...

---

### Post by Emmanuel_uk on 2006-06-13
Good to know it worked.
Good nagging as well. The more the merrier.
Had similar answers from them
Can you cut and paste the bit in syslog that says which driver your are using
something of the like
kernel: ndiswrapper: driver wusb54gsv2 (Linksys,01/25/2005, 4.01.20.0) loaded
It may be of use of somebody else

>>was the debian package I was using wasnt working correctly
Which ndiswrapper are you using then? May help other as well. Thanks

---

### Post by wieman01 on 2006-06-16
please ignore...

---

### Post by s3xy_n00b-nuts4bunty on 2006-07-08
Hey all,

I have been following many developments of Linksys, and i too asked their tech support for help. I was stonewalled by them and tghey said they refuse to support people using Linksys products outside of the working and tested environemnts, as Linux is too experimental and is liekly to be the trouble with my non-functioning card. Utter bull but hey. I have a Linksys WUSB54GS V2.1. Details below are to help. I have tried the drivers listed on ndiswrappers wiki, and no joy. i tried a search for the same pci id, and no joy, and since they wont release the name of the chipset used, i cant get a similar driver to test it. This may have the same pci id, but i dont think this uses the Broadcom Chipset of the original V2 that is listed. All the goodies are below to help others:

PCI_ID: ID 13b1:0014 Linksys
Model No. WUSB54GS ver. 2.1
Type: Linksys Wireless-G USB Network Adapter
Serial Number (S/N): M1010F415708
MAC Number: 0016B65C12A1
FCC ID: Q87-WUSB54GSV2
Manufactured: 04/2006

Of note to me is the FCC ID lists it as a V2 but it is clearly a V2.1 so im not suprised that Linkyss dont know the chipset they use, as neither does the FCC by the seems of things.

I have no luck with this device in Linux. I have used both CD drivers, those from the net, and also combining these drivers with Broadcoms drivers so i could install the WUSB54GSV2.inf file. Nothing works. The lights remain inactive, and ifconfig shows no wlan0 present. Driver claims it is present, and installed, after running ndiswrapper -l, and also after modprobing there is no troubles but the rest of the steps cant be performed as no wlan0 is not listed by ifconfig, and iwlist scan.

As a side note again, i tried this on SUSE 10.1 also and this did not work either. I set this up via the network manager after failing to do it with ndiswrapper with above troubles. Once i set up network manager, i still had no lights on the device. Nothing works, and when the scripts are started at boot time, again nothing but an error saying no wireless extension (wlan0)...

I have tried the version WUSB54GS V2.1 with both ndiswrapper, and NetworkManager, in both GNOME and KDE on, with different versions of ndiswrapper, and different drivers:
Ubuntu 6.06 Dapper Drake
SUSE Linux 10.1
Fedora Core 5 Bordeux
Fedora Core 6 Test 1

None work. AVOID THIS DEVICE LIKE THE PLAGUE.

Anyone cracked this problem??

MAniX ([http://www.manix-place.co.uk/wireless](http://www.manix-place.co.uk/wireless))

---

### Post by javaJake on 2006-07-29
I have cracked this issue. I made a little how-to here:
[http://www.ubuntuforums.org/showthread.php?t=225206](http://www.ubuntuforums.org/showthread.php?t=225206)

Let me know if you have issues with this HOW-TO.

---

### Post by Emmanuel_uk on 2006-07-30
Good to see another howto, I will X-link it to mine for mandriva

I think it is worth specifying where the sys files are from in these
commands.
sudo cp usb8023.sys /etc/ndiswrapper/wusb54gs/
sudo cp rndismp.sys /etc/ndiswrapper/wusb54gs/

---

### Post by javaJake on 2006-07-30
> **Emmanuel_uk said:**
> Good to see another howto, I will X-link it to mine for mandriva

I think it is worth specifying where the sys files are from in these
commands.
sudo cp usb8023.sys /etc/ndiswrapper/wusb54gs/
sudo cp rndismp.sys /etc/ndiswrapper/wusb54gs/

Thanks for your suggestion. I have changed my HOW-TO accordingly. I hope to make a script to automate this whole process, since many people want it to "Just Work" without a lot of work.

---

### Post by Emmanuel_uk on 2006-07-30
> The best idea is to get a Windows XP installation, and to browse to C:/WINDOWS/system32/drivers. There you'll find usb8023.sys, and rndismp.sys. Copy those over to Linux into a folder.

I do not have ZinXp
Or create a directory and put F5D7051.exe in it
[http://www.belkin.com/support/download/downloaddetails.asp?download=1871&lang=1](http://www.belkin.com/support/download/downloaddetails.asp?download=1871&lang=1)
get hold of unshield-0.4-3mdk.rpm or equivalent for debian/ubuntu
unzip F5D7051.exe
unshield x DATA1.CAB
unshield x DATA2.CAB
then the driver I would have used
2Kdriver/usb8023k.sys
# ls -l 2Kdriver/
total 48
-rw-r--r-- 1 root root 29184 May 19 23:11 RNDISMPK.sys

---

### Post by javaJake on 2006-08-02
> **Emmanuel_uk said:**
> I do not have ZinXp
Or create a directory and put F5D7051.exe in it
[http://www.belkin.com/support/download/downloaddetails.asp?download=1871&lang=1](http://www.belkin.com/support/download/downloaddetails.asp?download=1871&lang=1)
get hold of unshield-0.4-3mdk.rpm or equivalent for debian/ubuntu
unzip F5D7051.exe
unshield x DATA1.CAB
unshield x DATA2.CAB
then the driver I would have used
2Kdriver/usb8023k.sys
# ls -l 2Kdriver/
total 48
-rw-r--r-- 1 root root 29184 May 19 23:11 RNDISMPK.sys

I have included these instructions as well. Thanks for the huge support Emmanuel_uk! If you find anything else let me know! :D

---

### Post by javaJake on 2006-08-02
> **Emmanuel_uk said:**
> I will X-link it to mine for mandriva

Huh?

---

### Post by Emmanuel_uk on 2006-08-02
> Originally Posted by Emmanuel_uk  
I will X-link it to mine for mandriva 

Huh?

I have my own howto for mandriva for the WUSB54GS 
in Linuxquestions. I posted the link before in the ubuntu
thread I think.
So what I am saying is, my howto points to yours!

---

