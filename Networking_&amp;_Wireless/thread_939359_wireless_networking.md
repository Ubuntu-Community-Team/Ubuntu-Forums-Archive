---
title: "wireless networking"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by shane8002 on 2008-10-05
I have a broadcom 802.11b/g wlan NDIS 5.1 wireless card, and i recently purchased a ubuntu cd and I cant figure out how to configure the wireless card in ubuntu. If i cant even get on the internet with ubuntu then it is of no use to me and i might as well get my money back. Plus i dont have access to the internet at my house so i half to go to cafe's or public wi fi access spots, so i need full functionality from my wireless card

---

### Post by cprofitt on 2008-10-05
can you post the output of lspci and lwconfig.

Thanks,

---

### Post by spiritsongtress on 2008-10-05
I have the Same problem. I did download the b43xx cutter.... but I am still have problems: heres the lspci and lwconfig I got

lspci:
>  00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


lwconfig - the other one doesn't bring up anything

 I also have no response from any of the updates...
I updated but nothing seems to have changed and the icon is still up there. and it still says there are things to be updated

---

### Post by shane8002 on 2008-10-06
Sorry man if you explain to me where i can find the output info i could definently get it to you.

---

### Post by ENigma885 on 2008-10-06
> **shane8002 said:**
> Sorry man if you explain to me where i can find the output info i could definently get it to you.

*(Applications >> Accessories >> Terminal)* paste lspci and iwconfig, not lwconfig, individually.

---

### Post by ENigma885 on 2008-10-06
_[SIZE="3"]**HOW TO SOLVE** :[/SIZE]_

To make it clearer some wireless network cards have **no** Linux drivers. So in the following steps u will use the Windows driver in Linux and it will work natively with no problems as follows:- (as u said u don't have a net connection so download the packages from anywhere then transfer them to ur Ubuntu pc)

1 - Download ndiswrapper-common from [**[COLOR="Red"]HERE[/COLOR]**]("http://yu.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb") 
2 - Download ndiswrapper-utils-1.9 from [[COLOR="Red"]**HERE**[/COLOR]]("http://yu.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb")
3 - Download ndisgtk from [[COLOR="Red"]**HERE**[/COLOR]]("http://yu.archive.ubuntu.com/ubuntu/pool/main/n/ndisgtk/ndisgtk_0.8.3-1_i386.deb") 
4 - Transfer the 3 packges to ur Ubuntu box and install them in the same sequence, they depend on each other,.
5 - After complete installation go to *(System >> Administration >> Windows Wireless Drivers)*
6 - Click *Install New Driver* and browse for ur Windows wireless network driver.

It should work very well..

---

### Post by shane8002 on 2008-10-06
Thanks a million. One more question could i just download those programs onto to a usb stick and then boot up linux and make the transfer because i have tried to do this before and it wasnt compatible. And if i does the steps you provided i will be to search for wireless networks then just click connect right? And also under administration tools theres is no option for windows devices will appear after i install the programs you suggested. Thanks alot and for being patient with a linux illiterate.

---

### Post by ENigma885 on 2008-10-07
_***In case u can't find ur 802.11b/g Windows driver .. ***_[**[COLOR="Red"]HERE[/COLOR]**]("ftp://ftp.work.acer-euro.com/notebook/aspire_3000/driver/802bg.zip") it is...
Unzip the file and when u browse for the driver locate _**bcmwl5.inf**_, in the unzipped folder,.

> **shane8002 said:**
> could i just download those programs onto to a usb stick and then boot up linux and make the transfer yea sure the goal is to get the packages in ur hard disk to install them in Ubuntu as u don't have an accessible internet connection.

> **shane8002 said:**
>  i have tried to do this before and it wasnt compatible. wat do u mean by "this" and "wasn't compatible"?

> **shane8002 said:**
> And also under administration tools theres is no option for windows devices it will appear after installing the packages.

---

### Post by shane8002 on 2008-10-07
thaks alot. I tried to move some music files and some videos from windows over to ubuntu and it said it needs a decoder which im guessing i could get online after i get the internet on my ubuntu and also some programs that i downloaded offline wont work in ubuntu, but im guessing thats probaly because there configured to be used in windows. If i get ubuntu fully functioning to my liking windows wouldnt matter to me cuz frankly i like linux better, but i was wondering could i transfer all my music from i tunes and all my downloads from Azureus to ubuntu, and i have everthing backed up on an external hard drive that i would want to keep just in case i would want to delete windows xp, would that be possible to transfer??

---

### Post by Papa-san on 2008-10-07
While you are gathering drivers, I'd suggest downloading and saving 'bcmwl5.inf' and 'bcmwl5.sys' as well. I had a nightmare of a time configuring it on my old laptop because I had the 'a' version and it wasn't compatible. Just make sure you absolutely get rid of the one you don't need once you are up and running!

---

### Post by shane8002 on 2008-10-07
Im sorry man but could you explain exactly what you mean cuz im clueless when it comes to linux.:confused:

---

### Post by ENigma885 on 2008-10-07
> **Papa-san said:**
> While you are gathering drivers, I'd suggest downloading and saving 'bcmwl5.inf' and 'bcmwl5.sys' as well.....

Those 2 files are in the driver i linked u to in my previous post.

And could u plz follow the instructions in the 2 posts i sent 1st??..
and later we can discuss the Azureus and iTunes..

---

### Post by shane8002 on 2008-10-07
okay the first package installed fine but the other two wont install it says error in dependency so what do you suggest do now???????

---

### Post by ENigma885 on 2008-10-07
it would be easier to tell me wat dependencies are missing so that i can link u to them...
it should be written *"Error Dependency is not satisfied:"* then the missing dependency.

---

### Post by shane8002 on 2008-10-07
The missing dependecie error say libc6

---

### Post by shifty_powers on 2008-10-07
[http://packages.ubuntu.com/hardy/libc6](http://packages.ubuntu.com/hardy/libc6)

---

### Post by ENigma885 on 2008-10-08
ok ur missing dependency can be downloaded from [**[COLOR="Red"]HERE[/COLOR]**]("http://yu.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.7-10ubuntu3_i386.deb")

**_[SIZE="3"]***Briefly wat u r going to do is...***[/SIZE]_

**1 -** Download the missing dependency  [**[COLOR="Red"][COLOR="Red"]HERE[/COLOR][/COLOR]**]("http://yu.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.7-10ubuntu3_i386.deb")
**2 -** Transfer the 4 packages (ndiswrapper-common, libc6, ndiswrapper-utils-1.9, ndisgtk).
-Also transfer ur Windows wireless LAN driver that can downloaded from **[[COLOR="Red"]HERE[/COLOR]]("ftp://ftp.work.acer-euro.com/notebook/aspire_3000/driver/802bg.zip")**
**3 -** In ur Ubuntu box : 
  -a)install the 4 packages in the same sequence (ndiswrapper-common, libc6, ndiswrapper-utils-1.9, ndisgtk)
  -b)Extract the zipped driver *(rightclick and extract here)*
**4 -** Go to* System >> Administration >> Windows Wireless Drivers*
Click *Install New Driver* >> Click the box next to *Location* >> Browse to the unzipped driver folder >> and locate ***_bcmwl5.inf_***[COLOR="Red"] not [/COLOR]bcmwl5a.inf >> Click install 
and ur done with the installation ... (further network configuration can be done easily)
**5 -** Reboot ur System

---

### Post by shane8002 on 2008-10-08
alright enigma i tried the other guys package and it would download almost to the end and then it said could not complete download but ill try your steps and let you know wat happens

---

### Post by shane8002 on 2008-10-09
okay how do i install the driver for my card because its like a document with a bunch of diffrent files in it

---

### Post by ENigma885 on 2008-10-09
> **ENigma885 said:**
> 
**4 -** Go to* System >> Administration >> Windows Wireless Drivers*
Click *Install New Driver* >> Click the box next to *Location* >> Browse to the unzipped driver folder >> and locate ***_bcmwl5.inf_***[COLOR="Red"] not [/COLOR]bcmwl5a.inf >> Click install 
and ur done with the installation 


..

---

### Post by shane8002 on 2008-10-09
cant install libc6 pakage because it froze on installation and i couldnt close the window so restarted and when i tryed the installiton again it says one one package manager can run at a time please close current package manager

---

### Post by ENigma885 on 2008-10-09
- Close ur Synaptic Package Manager and any other installation
- Put the packages on ur Ubuntu desktop, or any other Linux format folder,

---

### Post by shane8002 on 2008-10-09
when i clicked on the package manager program it says error must run dkpg--command-a manually

---

### Post by ENigma885 on 2008-10-09
ok if the packages on ur desktop now, open a Terminal (Applications >> Accessories >> Terminal)

```
cd ./Desktop
```
then
```
sudo dpkg -i PACKAGE.DEB
``` and replace PACKAGE.DEB with the package complete name  (like ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb or libc6_2.7-10ubuntu4_i386.deb)

---

### Post by shane8002 on 2008-10-09
No such file or directory Errors were encountered while processing PACKAGE.DEB

---

### Post by REDace0 on 2008-10-09
If you're going to type out messy package names, you should know that the terminal features autocompletion. If you press TAB after typing part of the name of the command or file or whatever, it will finish typing for you. If it doesn't, double-press tab to see the list of possible matches, and type enough additional characters to identify whatever it is you want.

---

### Post by shane8002 on 2008-10-09
ive tryed all of the packages and it says no such file or directory found

---

### Post by shane8002 on 2008-10-09
ive got it installing but i think it might be frozen again cuz the package is only 4.1 megabytes and its been installing for like ten minutes now is that normal???

---

### Post by REDace0 on 2008-10-09
Err...maybe. Quick question though: if you can't get on the internet in Ubuntu because the wireless isn't working. How are you posting? The way I've gotten my laptop up and running both times is by hooking it up to a wired connection to get the right drivers, then letting it loose once those work. Is there any possible way to get the Ubuntu machine hooked up to a wired connection? Package installation should be easier that way and we can get the output of those commands to see precisely what your wireless card is.

---

### Post by shane8002 on 2008-10-09
im at a friends house using his internet and hes got a cable plugged into his computer with high speed are saying i should plug that into my laptop get on the internet in ubuntu and try to install

---

### Post by REDace0 on 2008-10-09
If he doesn't mind, you could try it. But I'd feel better about it if your friend knows about his network and ISP a bit. In most cases that should work, but some ISPs will try to limit access to just one PC at a time, in which case it either won't recognize yours, or it will, and then won't recognize his for a while. If you seriously doubt any of the above terrible things will happen, I say go for it.

---

### Post by ENigma885 on 2008-10-09
_[COLOR="Red"]@shane8002[/COLOR]_
I sent u my email address in a private message, u can add me for an easier way to help

---

### Post by shane8002 on 2008-10-12
i got the three packages installed and the libc6 package, but when i
click on the windows wireless drivers option it shows up on the taskbar
for like one second, so basically it wont open and the driver package
cant be read in ubuntu because its in win rar format so im making
progress but still not all the way there.

---

### Post by ENigma885 on 2008-10-13
_[SIZE="3"]Please answer the exact following questions and be precise:-[/SIZE]_

**1.** Y didn't u add my email address i sent u in a private message? 
**2.** Can u get ur get ur laptop connected to the internet through ur friend's cable only for 10 minutes ?
**3.** > **shane8002 said:**
> the driver package
cant be read in ubuntu because its in win rar format
i linked u to the driver but it was in .zip format not .rar..so r u talking about the same thing?
**4.** Open a terminal window (Applications>>Acces.>>Terminal) and paste
```
gksu /usr/sbin/ndisgtk
```, this should launch "Windows Wireless Drivers",> **shane8002 said:**
> ....when i click on the windows wireless drivers option it shows up on the taskbar for like one second, so basically it wont open....
if it exits the same way u described, some errors should appear in the Terminal window..so send them here plz

---

### Post by anewguy on 2008-10-13
Please, people without wireless connections and no access to a wired connection can install ndiswrapper from the LiveCD.  Just put in the CD, let it open in the explorer windows, navigate to the pool/main/n/ndiswrapper folder and double-click each file there to install it.

---

### Post by shane8002 on 2008-10-13
enima i sent you a e mail like two days ago. Also i hooked up my laptop to a wired connection but it was slow on my computer so i think that has something with the isp. Also i did redownload your zip. file and when i run it in ubuntu it shows a bunch of diffrent files and when you try to click on them it says media cannot be read.

---

### Post by shane8002 on 2008-10-14
Enigma here is the error code when i tried to run windows devices from the terminal.

(gksu:5099):GHK-WARNING**:Locale not supported by c library.
(ndisgtk:5100):Gtk-warning **: using the fallback 'c' locale.
Traceback (most recent call last):
File "/usr/sbin/ndisgtk" line 53, in?
locale .setlocale(locale,LC-ALL, ")
File "/usr/lib/python2.4/locale,py," line 381, in setlock return_setlocale
(category,locale)
locale.Error" unsupported locale setting

---

### Post by shane8002 on 2008-10-22
i guess ill half to take my ubuntu cd back to the store since nobody can figure out how to get the wireless card to work in ubuntu....

---

