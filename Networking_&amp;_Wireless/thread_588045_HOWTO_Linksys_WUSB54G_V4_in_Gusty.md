---
title: "HOWTO: Linksys WUSB54G V4 in Gusty"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by AlexMono94 on 2007-10-23
Okay, after a whole week of trying I **finally** have the Linksys WUSB54G V4 working in Gutsy **without ndiswrapper**.

This should work with a fresh install of Gutsy or an upgrade from Feisty

You will need the following packages:

[LIST]
[*]build-essential   -   which you can get from an Ubuntu CD. (Edgy/Feisty/Gutsy etc.)
[*]linux-headers-'uname -r'   -   which you can get from a quick search at [packages.ubuntu.com](packages.ubuntu.com)
[/LIST]
The first thing you will need to do is find a way of getting the RT2570 CVS driver on to your computer from [http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz).

First of all extract the contents of the archive into your **home folder**.

Then in the the terminal:

```
cd rt2570-cvs-xxxxxxxxxx
```

(where xxxxxxxxxx is what that part of the folder name which you extracted. (it changes depending on the date)

and then change into the module directory:

```
cd Module
```

after that make the source code:

```
make
```

and then install as root

```
sudo make install
```

That covers installing the driver. Now if all goes well you will need to blacklist the default driver that comes with Gutsy.

```
sudo gedit /etc/modprobe.d/blacklist
```

at the bottom add "blacklist rt2500usb" (without the quoatation marks)

Then restart and manually configure your network by clicking the network monitor and choosing "manual configuration" and click "wireless connection" and then properties. Untick "enable roaming mode" and fill in the details as necessary then press ok and be sure to check the box next to wireless configuration.. And restart again and check if you are connected.

If you are not connected, in the terminal:

```
sudo gedit /etc/network/interfaces
```

and change all occurrences of "rausb1" to "rausb0" and then yet again, restart.

Please post back if this method works for you. :)

---

### Post by tdmoore on 2007-10-23
I am really looking forward to trying this.

Have the WUSB54G v1 and have this via a USB Hub.  Hub is detected I think (complete newb to Linux) but cannot detect ANY wireless anywhere.  Boot up in XP though and it detects automatically 6 in my neighborhood including mine.

I realize this is V4...do you think that this would be any different in v1?

Appreciate a reply...

---

### Post by AlexMono94 on 2007-10-23
I'm not sure because I think they both have different chipsets but you might as well give it a go.

---

### Post by rustybronco on 2007-10-23
> **AlexMono94 said:**
> I'm not sure because I think they both have different chipsets but you might as well give it a go.
V1 has a different chipset it's a prisim chipset so it wont work, sorry.

try ndiswrapper and
[http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843775&packedargs=sku%3DWUSB54G&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4377543775B01&displaypage=download#versiondetail](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843775&packedargs=sku%3DWUSB54G&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4377543775B01&displaypage=download#versiondetail)

---

### Post by floquet on 2007-10-23
It works!. I just tried with a fresh installation of Gusty and WUSB54G rev4, and it worked flawless!!. Thanks a lot:)

---

### Post by AlexMono94 on 2007-10-23
Happy to help.

---

### Post by webbie180 on 2007-10-23
I have this,
rt2570-cvs-daily.tar.gz 

How do I change to this,
cd rt2570-cvs-2007102305

Thanks.

OK, figure that out, simply just by double clicking on it.

---

### Post by webbie180 on 2007-10-23
Is there a difference if my interface is wlan0 instead of rausb1?

---

### Post by AlexMono94 on 2007-10-23
extract the contents of the archive by double clicking it in the file manager and follow the code using the terminal. Also the archive must be in your home folder. As for the issue on wlan0 id change it just incase.

---

### Post by webbie180 on 2007-10-23
I dont a Gusty CD, where can I download build-essential package?

---

### Post by webbie180 on 2007-10-23
This is wat I get after make,
/Desktop/rt2570-cvs-2007102319/Module$ make
make: *** /lib/modules/2.6.22-14-386/build: No such file or directory.  Stop.
rt2570.ko failed to build!
make: *** [module] Error 1

---

### Post by AlexMono94 on 2007-10-23
packages.ubuntu.com but you will have a hard time getting all the dependencies. I already installed it prior to upgrading.

---

### Post by AlexMono94 on 2007-10-23
> **webbie180 said:**
> This is wat I get after make,
/Desktop/rt2570-cvs-2007102319/Module$ make
make: *** /lib/modules/2.6.22-14-386/build: No such file or directory.  Stop.
rt2570.ko failed to build!
make: *** [module] Error 1

this is why you need build-essential. also if you have a feisty/edgy/dapper cd see if its included with them

---

### Post by webbie180 on 2007-10-23
> **AlexMono94 said:**
> this is why you need build-essential. also if you have a feisty/edgy/dapper cd see if its included with them

Anyway to get all the neccesary from synatic package manager?  If so, wat are the files that I will be looking to installed?

---

### Post by AlexMono94 on 2007-10-23
not if the computer in question doesnt have an internet connection but if you have another computer with an internet connection you can install on that in synaptic but choose to download package files only. they will then be downloaded to /tmp from where you can copy them over

---

### Post by webbie180 on 2007-10-23
Does this mean that I have build-essential?  But still cant make...thanks alot for answering.

sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**build-essential is already the newest version.**
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
@ubuntu:~$ cd Desktop
@ubuntu:~/Desktop$ cd rt2570-cvs-2007102319
@ubuntu:~/Desktop/rt2570-cvs-2007102319$ cd Module
@ubuntu:~/Desktop/rt2570-cvs-2007102319/Module$ make
make: *** /lib/modules/2.6.22-14-386/build: No such file or directory.  Stop.
rt2570.ko failed to build!
make: *** [module] Error 1

Did I do something wrong here?

---

### Post by Latooni on 2007-10-24
> **webbie180 said:**
> I dont a Gusty CD, where can I download build-essential package?
EDIT: Ah, I'm too late. Oh, well.

Oh, and thank you, AlexMono. This helped me very much.

---

### Post by webbie180 on 2007-10-24
@ubuntu:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
**build-essential is already the newest version.**
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
@ubuntu:~$ cd Desktop
@ubuntu:~/Desktop$ cd '/home/ching/Desktop/rt2570-cvs-2007102402'
@ubuntu:~/Desktop/rt2570-cvs-2007102402$ cd Module
@ubuntu:~/Desktop/rt2570-cvs-2007102402/Module$** ./configure**
bash: ./configure: No such file or directory
@ubuntu:~/Desktop/rt2570-cvs-2007102402/Module$ make
make: *** /lib/modules/2.6.22-14-386/build: No such file or directory. Stop.
rt2570.ko failed to build!
make: *** [module] Error 1
@ubuntu:~/Desktop/rt2570-cvs-2007102402/Module$

Tried ./configure but still didnt work.

---

### Post by AlexMono94 on 2007-10-24
I think I know the problem. You need some modules. I've attached them. Install it and see if it works then.

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-ubuntu-modules-2.6.22%2Flinux-ubuntu-modules-2.6.22-14-386_2.6.22-14.37_i386.deb&md5sum=4d0ca6e8aa40751c64038dea7e2ab541&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-ubuntu-modules-2.6.22%2Flinux-ubuntu-modules-2.6.22-14-386_2.6.22-14.37_i386.deb&md5sum=4d0ca6e8aa40751c64038dea7e2ab541&arch=i386&type=main)

---

### Post by EricD on 2007-10-24
After I blacklist the rt2500usb driver and go to edit my interfaces file, all I see is this:

auto lo
iface lo inet loopback

with no mention of rausb0 or wlan0. I am new to this, what line should I add to this file so I can get my internet working?

---

### Post by growingneeds on 2007-10-24
I've been using Ubuntu since Dapper Drake. Although the default configurations set up by Gutsy Gibbon for Linksys WUSB54G version 4 are faulty, this tutorial corrects the error. I would like to point out that the downloaded archive file has to be extracted in the "Home Folder", and please follow the date on the folder as indicated on your extracted folder. The folder name (the one with the date) mentioned here [cd rt2570-cvs-2007102305] does not reflect what I had extracted [cd rt2570-cvs-2007102410]. Take note that the terminal is case-sensitive: cd Module &#8800; cd module.

Also, after blacklisting the rt2500usb driver, there is NO mention of rausb0 in the interfaces file. Just proceed to restart the system. Finally, edit the network's "manual configuration": key in the SSID and password (still no support for pass-phrase generation). Do remember to check the box for your preferred wireless connection. Internet works fine as it did in Feisty Fawn.

Thank you, AlexMono94. I chose to install a fresh copy of Gutsy Gibbon, forgoing the upgrade option in Feisty. Will continue exploring Gutsy. I am trying out the Compiz-Fusion effects and gtkpod. =)

Alvin Lee

---

### Post by cutlerite on 2007-10-24
> **EricD said:**
> After I blacklist the rt2500usb driver and go to edit my interfaces file, all I see is this:

auto lo
iface lo inet loopback

with no mention of rausb0 or wlan0. I am new to this, what line should I add to this file so I can get my internet working?

I have the same issue.

---

### Post by AlexMono94 on 2007-10-24
Leave the file as it is, restart and click the network manager. Turn off roaming on wireless connection and enter the wireless details manually. Restart and then change the file and then restart again.

---

### Post by webbie180 on 2007-10-24
> **AlexMono94 said:**
> I think I know the problem. You need some modules. I've attached them. Install it and see if it works then.

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-ubuntu-modules-2.6.22%2Flinux-ubuntu-modules-2.6.22-14-386_2.6.22-14.37_i386.deb&md5sum=4d0ca6e8aa40751c64038dea7e2ab541&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-ubuntu-modules-2.6.22%2Flinux-ubuntu-modules-2.6.22-14-386_2.6.22-14.37_i386.deb&md5sum=4d0ca6e8aa40751c64038dea7e2ab541&arch=i386&type=main)

Tried again after reinstalling the above package even thou already have it, but unfortunately still didnt work for me.  Is there anymore thing that I could be missing?  Thanks.

---

### Post by AlexMono94 on 2007-10-25
> **webbie180 said:**
> Tried again after reinstalling the above package even thou already have it, but unfortunately still didnt work for me.  Is there anymore thing that I could be missing?  Thanks.

Try these then:

[http://packages.ubuntu.com/gutsy/misc/linux-restricted-modules-2.6.22-14-386](http://packages.ubuntu.com/gutsy/misc/linux-restricted-modules-2.6.22-14-386)
[http://packages.ubuntu.com/gutsy/misc/linux-restricted-modules-common](http://packages.ubuntu.com/gutsy/misc/linux-restricted-modules-common)

---

### Post by rustybronco on 2007-10-25
Something else to try.
[http://ubuntuforums.org/showpost.php?p=3629885&postcount=23](http://ubuntuforums.org/showpost.php?p=3629885&postcount=23)

---

### Post by dude2300 on 2007-10-25
> **webbie180 said:**
> This is wat I get after make,
/Desktop/rt2570-cvs-2007102319/Module$ make
make: *** /lib/modules/2.6.22-14-386/build: No such file or directory.  Stop.
rt2570.ko failed to build!
make: *** [module] Error 1

I had the same problem as this person.  I got it working but am not happy with the hack I needed to do.  I'll explain what I did and why, maybe someone can help me fix this next problem.

The reason "make" doesn't work is that there is no file in /lib/modules/2.6.22-14-386 called build... if you boot to the -386 selection at start up.  If you look in the /lib/modules/2.6.22-14-generic there is a build there.

I rebooted my computer to the 2.6.22-14-generic selection and followed the original instructions.  Everything worked exactly as described.  Now when I boot the the 2.6.22-14-generic kernel I have a fully functional wireless network.  When I boot to the -386 selection I get nothing.

My question is two fold.
1.  How can I get this working under the -386 boot?
2.  What is the difference between the -386 and -generic boot?

To those that were stuck where I was... at least we can get it working now, even if it's a hack.

---

### Post by dude2300 on 2007-10-25
Forgot to add.  I didn't need to install any of the restricted drivers.  I did add the build-essential, but I'm not sure if it was necessary (the base install may have this).  I only followed the original post instructions.  For what it's worth I did the upgrade from FF to GG, not a clean install.

---

### Post by rustybronco on 2007-10-25
I have been suggesting this fix to others, so at least I should give it a try...
WORKS!!!!   my hat's off to you.
p.s. manual config only no roaming mode

now I can put it back in the drawer it came from...

---

### Post by webbie180 on 2007-10-25
After installing this, I was able to make the source code,
> sudo apt-get install build-essential linux-headers-`uname -r`

Now to try out whether my wireless works or not....

---

### Post by webbie180 on 2007-10-25
**It  Works.  Thanks Alot For Your How-to.**

---

### Post by AlexMono94 on 2007-10-25
> **webbie180 said:**
> **It  Works.  Thanks Alot For Your How-to.**

yaaaaaay it finally worked! lol. thanks for the feedback. i will change the package requirements to linux-headers-'uname -r' asap aswell.

---

### Post by introspectif on 2007-10-26
Thank you for writing this tutorial. It looks promising, and I will try it once I'm done upgrading my Ubuntu Gutsy, and will notify you of the result.

On another note, it is curious why Ubuntu Gutsy cannot support this device in the default installation, where it was working fine (relatively) in Feisty. Any Ubuntu developer has answers?

---

### Post by bd@cb8be8510 on 2007-10-26
**Thanks a lot for this contribution!** Downloading and installing the driver from serialmonkey was
the only solution that got my wireless network working under feisty! (I'm using an ASUS WL-167G USB-adapter). I'm a happy Ubuntu-user again! :):):-D:-D:-D

---

### Post by NoSmokingBandit on 2007-10-26
i followed the guide but when i reboot and do the whole manual configuration it wont give me the option to connect wirelessly. Like if i right click on the icon in the panel theres a checkbox for Networking, but none for wireless connections.
Its a wusb54gv4 on a clean install of gusty.

---

### Post by AlexMono94 on 2007-10-26
> **NoSmokingBandit said:**
> i followed the guide but when i reboot and do the whole manual configuration it wont give me the option to connect wirelessly. Like if i right click on the icon in the panel theres a checkbox for Networking, but none for wireless connections.
Its a wusb54gv4 on a clean install of gusty.

you wont get an entry for wireless, if you have manually configured your SSID and password (leave it blank if you dont have one) you should be connected, try it!

---

### Post by NoSmokingBandit on 2007-10-26
awesome dude. Works great now. Thanks for the guide, i've been trying for days to get this working. One thing that concerns me though is that i now dont have the signal strength meter on my panel, but at least my connection wokrs fast now:
[[IMG]http://www.speedtest.net/result/196377279.png[/IMG]](http://www.speedtest.net)
I dont even get it that fast in windows with official drivers! My connection worked with the rt2500usb drivers but it wouldnt recognize if it was 802.11b/g/n but i guess it does now! Dude, if i could i would give you a hug.

---

### Post by zzsu on 2007-10-26
It's useful for me, very thanks!

---

### Post by introspectif on 2007-10-27
It worked, but only under the generic kernel. Thanks

---

### Post by daveteran on 2007-10-27
Got a bit of weird problem... I followed the guide on a fresh Gutsy install and can now successfully connect to my router. However, I am not able to view any web pages in Firefox. But what I can do is ping internet locations (e.g. Google) without a hitch. Anybody got any ideas?

---

### Post by reuyl on 2007-10-28
This tutorial worked... for one day.

Two days ago, my wireless internet connection dropped out of nowhere and won't even connect to the router anymore. It has to be a software issue, as my internet works in Windows XP (although Firefox won't load any pages for some reason). I'm completely frustrated now. Help! :(

---

### Post by tdmoore on 2007-10-29
> **rustybronco said:**
> V1 has a different chipset it's a prisim chipset so it wont work, sorry.

try ndiswrapper and
[http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843775&packedargs=sku%3DWUSB54G&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4377543775B01&displaypage=download#versiondetail](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843775&packedargs=sku%3DWUSB54G&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4377543775B01&displaypage=download#versiondetail)

Thank you.

I have downloaded the driver off my XP machine to USB key, loaded driver to Gutsy desktop and now not sure what to do other than follow previous instructions.

Anything you can do to assist would be greatly appreciated.  Thanks again!

---

### Post by Jmtan on 2007-10-29
Hello, does this method support WPA2 encryption? Or is everyone using WEP for their networks?

---

### Post by MariusSilverwolf on 2007-10-29
> **Jmtan said:**
> Hello, does this method support WPA2 encryption? Or is everyone using WEP for their networks?

I'm using WEP for reverse compatibility with a Linksys WUSB11 card on an older laptop.  From what I've read, though, these drivers only support WPA1, not WPA2.  Hopefully I'm wrong.

---

### Post by rustybronco on 2007-10-29
> **tdmoore said:**
> Thank you.

I have downloaded the driver off my XP machine to USB key, loaded driver to Gutsy desktop and now not sure what to do other than follow previous instructions.

Anything you can do to assist would be greatly appreciated.  Thanks again![http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

### Post by tdmoore on 2007-10-30
> **rustybronco said:**
> V1 has a different chipset it's a prisim chipset so it wont work, sorry.

try ndiswrapper and
[http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843775&packedargs=sku%3DWUSB54G&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4377543775B01&displaypage=download#versiondetail](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843775&packedargs=sku%3DWUSB54G&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4377543775B01&displaypage=download#versiondetail)

Thanks for the help here.

Need specific directions as I am so new to this.

[LIST]
[*]"Try ndiswrapper" - please define how I do this
[*]Driver download-done and on my desktop.  Need to know next steps please & thanks.
[/LIST]

Sorry to be a pain...not really up to speed on how to install drivers and packages yet.  Thanks again!

---

### Post by tdmoore on 2007-10-30
Just noticed your link and will try that rustybronco.

Again..(starting to sound very redundant) THANKS!

---

### Post by pasabaporaqui on 2007-10-31
Thanks for the instructions! 
It worked fine!

---

### Post by rustybronco on 2007-10-31
Sorry I didn't see your post fast enough, and your welcome.

---

### Post by trellis2 on 2007-11-01
Thank you, thank you, thank you. I got the fix to work on 2 of 3 computers. They all have the generic kernel. I could not get the fix to work on Xubuntu. Has anyone else encountered this problem?

---

### Post by steam_engenius on 2007-11-03
I'm posting this from my fresh gutsy install-that-was-about-to-make-me-cry-cause-it-broke-my-internet

needless to say, I love you.

---

### Post by RealG187 on 2007-11-04
OMFG~!!!!!!!!!!


 It works!!!!

Little slow but thats how my old Pentium III always was, how the hell did you figure this out, it would take me a billion years! I cant even install tar.gz!

[color=red]UPDATE[/color];

> The first thing you will need to do is find a way of getting the RT2570 CVS driver on to your computer from [http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz).
PSP Memory Stick, had it cuz I had a link ot something I found at school!

> and then change into the module directory:
```
cd Module
```
Remember people its a capital M! in the directions part when he says change to the modules directory its not capital but I guess there he was using it as a verb and not a noun...

> Then restart and manually configure your network by clicking the network monitor and choosing "manual configuration" and click "wireless connection" and then properties. Untick "enable roaming mode" and fill in the details as necessary then press ok and be sure to check the box next to wireless configuration.. And restart again and check if you are connected.

All I get in that thing it "Enable Networking" and dimmed out "Connection Information" and "About", but did it the old way and got in, didnt even need to restart more than once.


THANK YOU! 0% said it didnt!


This should be sticked, upon it not working I looked at the stickes, found nothing, made [This thread](http://ubuntuforums.org/showthread.php?t=602190) finally searched 5USB54G and found this wonderful thread!

---

### Post by hagerdoc on 2007-11-04
Just wanted to say Thank you! I had installed Ubuntu Feisty a few months ago, I upgraded to Gutsy today and wireless stopped working. I was looking around to see if I needed to reinstall Feisty and found this solution. It is so nice that people who are Linux experts provide help to those of us who want to throw out our WIndows CD's.

---

### Post by dln9 on 2007-11-04
> **AlexMono94 said:**
> Originally Posted by NoSmokingBandit  
i followed the guide but when i reboot and do the whole manual configuration it wont give me the option to connect wirelessly. Like if i right click on the icon in the panel theres a checkbox for Networking, but none for wireless connections.
Its a wusb54gv4 on a clean install of gusty

you wont get an entry for wireless, if you have manually configured your SSID and password (leave it blank if you dont have one) you should be connected, try it!

I am sorry, but the reply shown above is too vague for me.  I have the same problem - all I see available is networking, but no options to connect wirelessly.  And I have manually configured my SSID and password.  Still, nothing works.  

My router is using WPA-PSK wireless security, TKIP encryption, and it is not broadcasting the SSID.  However, when I leave out the SSID in the rausb0 configuration dialog box, the system automatically switches over to roaming mode, which the instructions said we should not use.

---

### Post by insomniaccanuck on 2007-11-06
> **EricD said:**
> After I blacklist the rt2500usb driver and go to edit my interfaces file, all I see is this:

auto lo
iface lo inet loopback

with no mention of rausb0 or wlan0. I am new to this, what line should I add to this file so I can get my internet working?

This is the same thing that I get.  I rebooted my machine and it no longer loads the wireless network device automatically.  

so in the terminal I ran iwlist scan
the device is listed but "rausb0 Interface doesn't support scanning"
so I ran "sudo ifconfig rausb0 up" in the terminal
then connected in the terminal with dhclient after setting the essid and enc for rausb0.

EDIT
I can connect in the terminal, but no luck with the GUI recognizing the wireless still.

also when I run iwconfig the output is this

> lo        no wireless extensions.

eth0      no wireless extensions.

rausb0    RT2500USB WLAN  ESSID:"ZIO"  Nickname:""
          Mode:Managed  Frequency=2.422 GHz  Access Point: 08:10:73:09:96:42   
          Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=69/100  Signal level:-75 dBm  Noise level:-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Does the fact that RT2500USB is still mentioned mean that the rt2500usb driver is still being used?
I blacklisted it as stated in the instructions.


Anyone that has the same interface file able to get this solution to work?
Ideas?
thanks

---

### Post by nikin on 2007-11-17
it worked for me like a charm....

Thanx for the great tuto :D

---

### Post by Scott-271 on 2007-11-28
> **trellis2 said:**
>  I could not get the fix to work on Xubuntu. Has anyone else encountered this problem?

I am also having problems getting it to work on Xubuntu. I get to the "sudo make install" and the terminal just freezes and does nothing. I'd hate to have to start over by installing Ubuntu and working backwards towards Xubuntu, but if I have to I will; so any help would be appreciated.

Thanks,
Scott

P.S. and before anyone asks, I did substitute mousepad for gedit.

---

### Post by mohawk82 on 2007-12-01
This worked for me.  Thank you VERY much for the excellent contribution!

Mohawk82

---

### Post by drengi on 2007-12-02
This tutorial worked, but there's still a little problem:

My wusb54g v4 works flawlessly in gutsy for about 20 minutes, then it dies. All the lights on the adapter go out.

Reconnecting it doesn't solve it. When I unplug it and plug it back in, the light flash for a split second and die again. The only way to restore the connection is to reset my PC.

I installed feisty and got my internet working, but the same thing happens. 20 minutes and it dies completely (no lights, nothing).

Strangely enough, iwconfig thinks my adapter is still working. It gives me a signal strength and everything even though it's obvious the stupid thing is dead.

Help?

---

### Post by RealG187 on 2007-12-03
> **drengi said:**
> This tutorial worked, but there's still a little problem:

My wusb54g v4 works flawlessly in gutsy for about 20 minutes, then it dies. All the lights on the adapter go out.

Reconnecting it doesn't solve it. When I unplug it and plug it back in, the light flash for a split second and die again. The only way to restore the connection is to reset my PC.



Mine does that too, even back in 6.10 it did that, the works then it dies, then the lights blink upson plugging it in. If I leave it out (which is inconvenient, the thing is supposed to network my computer not site around and be a peice of s***!) after I while it will go again, I think it only does this is Linux and not Windows (I dont use Windows on that PC that much)

---

### Post by pVilaça on 2007-12-03
This works for me. Very very thanks!

---

### Post by eskimomo on 2007-12-06
This worked in some ways and not in others. It worked great because now i have an internet connection which is amazing. I am having problems with mythweb though. Although my linux box maintains that it is connected to my network my router doesn't seem to think so. I don't really understand that. But hey it's still great to have internet access.

Eli

---

### Post by martinw89 on 2007-12-10
Ugh unfortunately this is not working for me.  I'm using Xubuntu (straight from the Xubuntu cd so none of the packages that come with gnome flavored Ubuntu).  The module compiles fine.  Make install works fine.  Blacklisting went fine, "cat /proc/modules" only shows the rt2570.

Where I have the problem is connecting to my network.  No matter what I do, it connects to the neighbor's unsecure network.  I have roaming mode off, I entered in all the correct values.  /etc/network/interfaces shows rausb0 and the settings I entered using the network manager.  However, after all of this, iwconfig shows that the card connects to my neighbor's unsecure network.

Any help would really be appreciated.

---

### Post by bart_simpson on 2007-12-19
Great guide, worked the first time for me on my Gutsy 64-bit install.

Also, for anyone who might be too lazy to search for the linux-headers:
[http://packages.ubuntu.com/gutsy/devel/linux-headers-2.6.22-14](http://packages.ubuntu.com/gutsy/devel/linux-headers-2.6.22-14)

---

### Post by SuperJETT on 2007-12-26
Thanks!  My adapter worked under Edgy, I was about to go nuts until I found this.

---

### Post by fickenbaisage on 2007-12-30
This solution doesn't work for me. Does KDE have similar issues? Will my wireless problem be solved if I installed KDE?

---

### Post by floydjunkie8 on 2007-12-30
ok so i havent tried this yet but i need to know what is meant by 


linux-headers-'uname -r'

can someone give me a link or tell me how i can get this


i cant find this on ubuntu.packages.com ....


thanx

---

### Post by martinw89 on 2008-01-01
> **floydjunkie8 said:**
> linux-headers-'uname -'
Those aren't actually single quotes, those are `s (it's the key to the left of 1, above tab).  When you put something in `` in the command line, it does that command and the output is inserted where the `s where.  For example:```
ls /home/`whoami`
```The above command lists the contents of the current user's home directory.  Basically it executes "whoami", which returns the current user's name, and puts it after "/home/".  This is actually a bad way to do it, "ls ~" would do the same thing (~ is a shortcut for the user's home directory), I just used this for an example.

"uname -r" returns the name of the current kernel, so:```
sudo apt-get install linux-headers-`uname -r`
```The above is just a really quick way to get the headers for the kernel you are currently using.  You could have typed "uname -r" in a terminal and looked for those headers in Synaptic and it would have done the same thing, this is just a short way.

Sorry for the long explanation, I hope this helps!

---

### Post by wonton180 on 2008-01-02
this didn't work for me....well, i should say this didn't work for my specific configuration.

The native rt2500 driver in the 2.6.22 kernel with Gusty automatically picks up the device and works with NetworkManager.  I believe the part sorely missing is the appropriate configuration steps for configuring WPA with this device.  I have tried every combo i could find using native kernel driver, and a source built version from the serialmonkey CVS, both using NetworkManager and manual configuration when disabling the NM.

I can post my specific access point config and what appears OTA from iwlist scanning if anyone here feels like an expert.

---

### Post by rustybronco on 2008-01-02
synaptic>wpasupplicant

---

### Post by pVilaça on 2008-01-07
It's work for me.

But, when i'm using azureus, 10 minutes later the network stop. I do 
       service networking restart 
and network comes up.

When i'm not using azureus, i don't have this problem.

Any help? 

thanks

---

### Post by bailout on 2008-01-09
Just posting to say thanks for the howto. I finally wiped my fiesty install and reinstalled with gutsy kubuntu to find that ubuntu's support for ralink chips has followed recent releases by getting worse yet again despite open drivers :( I actually have a Belkin usb dongle but it is based on the same ralink chipset. I wasn't really in the mood for too much faffing about trying to get it to work and almost restored an image of my fiesty install so this howto being so easy saved me from downgrading.

Just a few points after my experience:
On a fresh install of kubuntu from the live cd the kernel headers installed by default and the build essential stuff was on the cd so it was just the driver file that I had to download on another computer and transfer across.

I followed the howto to build and install driver but none of the other steps. ie I didn't do the blacklist old driver etc.

Kubuntu uses knetworkmanager which I haven't been able to get to work with the new driver. It used to show networks but couldn't connect to any but since changing the driver as in the howto knm just doesn't seem to see the device at all. Instead I just used the network section in system settings to enable the device and set it so that it turns on during boot.

If anyone has any ideas for why networkmanager doesn't see the device and how I could get it working that would be great but at least I can now connect to the internet.

thanks again

---

### Post by kevdog on 2008-01-09
Did you compile the cvs serial monkey sources?

---

### Post by bailout on 2008-01-09
> **kevdog said:**
> Did you compile the cvs serial monkey sources?

Yes I downloaded the cvs driver from the link in the first post and did the make/make install steps. After that I just set up the device through the kde system settings to come on on boot. Knetworkmanage didn't show the device at all (under the default driver knm would see it and scan but couldn't connect).

---

### Post by shankscomp on 2008-01-15
OK, I've been at this now for the last 6 days straight... I think I've tried every fricking solution possible...  I'm about to format the hard drive and start fresh again.  I did get my PCMCIA Linksys card installed, but I had to use the NDISWRAPPER to get it working.  Now when it comes to the WUSB54G Ver 4, I've tried everything I could find.. Any more ideas???  I'm glad I made a backup of my hard drive before trying to install each time.  Unfortunately, for my job, it helps to have two wireless NICs.  Running a dell laptop C640 with a gig of ram and 80gb hard drive.

---

### Post by engineerbob on 2008-01-16
After many days of frustration and aggravation trying the many different solutions found in the forums, this one was the one that worked ---- Almost. What I mean is it works in WEP and unencrypted modes but I cannot get it to work with WPA. I even went so far as to wipe my system and do another clean install (this was the fifth time i did this). 

I have tried with and without wpa_supplicant. Didn't seem to make any difference. kevdog's excellent How-To on setting up encryptions didn't help either. 

I have resigned myself to using the WEP setup for my system unless you have any other suggestions. I live in an isolated area where the only people within 5 miles are not computer literate enough to present a security threat. But i have to admit I am not feeling warm and fuzzy in this mode. 

Any help you might offer is greatly appreciated.

---

### Post by wieman01 on 2008-01-16
I am not sure if I have asked this question before, excuse me if I have done so... But does this driver support WPA as well? Could I use Network Manager in order to connect to my WPA secured network?

If yes, then I'd like to include a reference to this tutorial in my own Ralink guide. What do you think?

---

### Post by rustybronco on 2008-01-16
If you get no answer about if this tutorial works with network manager and wpa, I'll play guinne pig and try it. I just need to retrieve my adaptor back from my son.

---

### Post by wieman01 on 2008-01-16
> **rustybronco said:**
> If you get no answer about if this tutorial works with network manager and wpa, I'll play guinne pig and try it. I just need to retrieve my adaptor back from my son.
It be great if you kept an eye on it, yes, I would appreciate it. But let's wait for a few days. My system is running nicely, so I don't want to touch it right now. If you are willing to try, please send me a note. I'll support you if anything goes wrong later on. :-)

---

### Post by rustybronco on 2008-01-16
> **wieman01 said:**
> I'll support you if anything goes wrong later on. :-)
If it breaks i'll learn from it and fix it. :)

---

### Post by wieman01 on 2008-01-18
> **wieman01 said:**
> I am not sure if I have asked this question before, excuse me if I have done so... But does this driver support WPA as well? Could I use Network Manager in order to connect to my WPA secured network?

If yes, then I'd like to include a reference to this tutorial in my own Ralink guide. What do you think?
Mmm... 

No one please?

---

### Post by leingod86 on 2008-01-18
I did everything as written and my wireless is still not functioning correctly. :( I included the blacklist entry but when I run lshw -C network the last line reads "configuration: broadcast=yes multicast=yes wireless=RT2500USB WLAN"

Is this normal or is there something else I need to do to make rt2570 the used driver?

---

### Post by rustybronco on 2008-01-18
Leingod86,
64 bit drivers.
[http://forums.linksys.com/linksys/board/message?board.id=Wireless_Adapters&thread.id=2371](http://forums.linksys.com/linksys/board/message?board.id=Wireless_Adapters&thread.id=2371)

Maybe check for posts/how-to's on using ndiswrapper on a 64bit system with 32 or 64 bit drivers
ndiswrapper how-to's  [http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)
[http://ndiswrapper.sourceforge.net/joomla/index.php?/](http://ndiswrapper.sourceforge.net/joomla/index.php?/) scroll down...

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
> Wireless support varies with architecture. For example, ndiswrapper will work on the x86 architechture.

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/)   
> Card: Linksys WUSB54Gv4, 802.11b/g, USB 2.0
Chipset: RT2500USB (RT2571F) (They just changed the chip and didn&#8217;t tell anybody. Be careful which version (v1/v2/v4) you buy!)
usbid: 13b1:000d
Driver 00: Ralink Driver, Open Source: [http://rt2x00.serialmonkey.com/](http://rt2x00.serialmonkey.com/) - 2005-07-25 / Good alternative to ralinktech.com&#8217;s driver. Works WELL.
Driver 0: Ralink driver: [http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm) - 2005-03-25 / Drv2.0.1.0, rt2500usb.inf & rt2500usb.sys Notes: ndiswrapper v1.2-rc1, kernel 2.6.11.7 (also works with grsec2 patch v2.1.5): works on both USB2.0 (load with modprobe ehci-hcd log2_irq_thresh=4 to avoid &#8220;usb X-Y: reset high speed USB device using ehci_hcd and address Z&#8221;) and USB1.1 (UHCI (OHCI not tested (yet?))). WEP works with 64bit and 128bit keys. but bitrate is only 11Mbit/s Note: rename the configuration file for the adapter once you installed the drivers (getting them extracted is quite a mess (WINE/Cedega) you need rt2500usb.*). &#8216;mv /etc/ndiswrapper/rt2500usb/148F\:2570.0.conf /etc/ndiswrapper/rt2500usb/13b1\:000d.0.conf&#8217; should do the trick.
Driver 1: Linksys Windows XP driver: [http://www.linksys.com/download/default.asp](http://www.linksys.com/download/default.asp) Notes: ndiswrapper v1.1, kernel 2.6.11.7 vanilla: kernel-oops! ndiswrapper v1.2-rc1 loads fine (EHCI loaded with modprobe ehci-hcd log2_irq_thresh=4) but oopses when unloading the module and the adapter is still plugged in (Kernel 2.6.11.7 vanilla). Yet transmission seems to fail completely (except increasing &#8216;Tx Invalid misc&#8217; values nothing happens).
Driver 2: older Linksys Windows XP driver: [ftp://ftp.linksys.com/pub/network/WUSB54Gv4_20040703.exe](ftp://ftp.linksys.com/pub/network/WUSB54Gv4_20040703.exe) Notes: ndiswrapper v1.2-rc1, kernel 2.6.11.7 (also works with grsec2 patch v2.1.5): seems to work, but only 11Mbit/s and without any encryption. no need to unplug the device before removing the ndiswrapper module. works on USB2.0, USB1.1 not tested (yet).
Driver 3:There is a native driver for rt2x00 but it has no USB support yet. View its status at rt2x00.serialmonkey.com

---

### Post by trieb on 2008-01-20
Yo.  Thanks for posting this.  I have had good luck with your sugguested process, it worked the first time for me.

---

### Post by wieman01 on 2008-01-21
> **trieb said:**
> Yo.  Thanks for posting this.  I have had good luck with your sugguested process, it worked the first time for me.
Including WPA support? Would be nice if you confirmed that.

---

### Post by trieb on 2008-01-21
Nah, I am using wep, WPA is another day.

---

### Post by rustybronco on 2008-01-21
> **wieman01 said:**
> Including WPA support? Would be nice if you confirmed that.I'll give wpa a try on this chipset as soon as I get my adaptor back.

---

### Post by wieman01 on 2008-01-22
> **rustybronco said:**
> I'll give wpa a try on this chipset as soon as I get my adaptor back.
Excellent, thank you.

---

### Post by pcrussell50 on 2008-01-27
> **AlexMono94 said:**
> Okay, after a whole week of trying I **finally** have the Linksys WUSB54G V4 working in Gutsy **without ndiswrapper**.

This should work with a fresh install of Gutsy or an upgrade from Feisty

You will need the following packages:

[LIST]
[*]build-essential   -   which you can get from an Ubuntu CD. (Edgy/Feisty/Gutsy etc.)
[*]linux-headers-'uname -r'   -   which you can get from a quick search at [packages.ubuntu.com](packages.ubuntu.com)
[/LIST]


Alex, I can't for the life of me seem to be able to find "linux-headers-'uname -r'" anywhere in the link you gave me.  I searched using the EXACT string in double quotes above, as well as using "linux-headers", and  "'uname -r'",  nothing.  It is also unavailable in synaptic, even with all the repositories enabled, unless I've missed something.  Everything else is going along nicely.  Anyone know how to find:

linux-headers-'uname -r'   ???

Am I missing something obvious?

-Peter

---

### Post by rustybronco on 2008-01-27
Hardy alpha 3................

output of uname -r 
```
dale@hardy-laptop:~$ uname -r
2.6.24-5-generic
```

output of lsusb with the wusb54g-v4 
```
dale@hardy-laptop:~$ lsusb
Bus 001 Device 002: ID 13b1:000d Linksys 
Bus 001 Device 001: ID 0000:0000 
```
[13b1:000d]   [http://www.linuxquestions.org/hcl/showproduct.php?product=3478&cat=all](http://www.linuxquestions.org/hcl/showproduct.php?product=3478&cat=all)

output of lsmod
```
Module                  Size  Used by
rt2500usb              24320  0 
rt2x00usb              12800  1 rt2500usb
rt2x00lib              22528  2 rt2500usb,rt2x00usb
rfkill                  8208  1 rt2x00lib

```

output of lshw -C network
```
 *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:b6:95:04:91
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.7 multicast=yes wireless=IEEE 802.11g
```
This might put to rest this and other chipsets *****edit*** dropped the connection like a hot potato!!!!!!!!!!** oh well I can hope it gets better as 8.04 advances can't I?
i'll play with it some more later.........

Haven't tried wpa yet, but soon as I can it will be done.

---

### Post by pcrussell50 on 2008-01-28
> **AlexMono94 said:**
> .

Please post back if this method works for you. :)

alex...after following this advice, my machine no longer recognizes wireless networks when I have my wusb plugged in.  This is ok with me, as I still have a wired connection.  But I thought you should know.  Here is the output of lshw -C network:

```
  lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 19
       serial: 00:15:f2:54:ed:7c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A ip=192.168.2.17 latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: rausb0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT2500USB WLAN
  
``` 

Note the DISABLED part under the wireless interface.  This was not the case before I performed all the tasks in your procedure.  Again.  Not to worry.  I have wired connection.  This is proving to be a learning experience.  Any idea of how to reverse these steps?

-Peter

---

### Post by cheetah_thompson on 2008-01-29
Those should be backticks (``) around uname -r. backticks execute the command enclosed and the result is substituted in place
type
    man uname
you will see one option is -r, which prints the kernel release
on my system the command
    uname -r
outputs the following
    2.6.22-14-generic
so the line
    linux-headers-`uname -r` 
on my system is just
    linux-headers-2.6.22-14-generic
I was able to find that using the search button on packages.ubuntu.com

Now if I could only get my WUSB54G Linksys network adapter to work! I have a thread which I started yesterday. Is it the case that the rt2500 driver is just no good (which was working fine under Windows and is installed under ndiswrapper)? Why are people using rt2570? Looks like I may have to buy a really long ethernet cable (about 30 feet!) or reinstall Windoze!

---

### Post by rustybronco on 2008-01-30
> **wieman01 said:**
> I am not sure if I have asked this question before, excuse me if I have done so... But does this driver support WPA as well? Could I use Network Manager in order to connect to my WPA secured network?

If yes, then I'd like to include a reference to this tutorial in my own Ralink guide. What do you think?
In 7.04 wpa-tkip is a no go.
I may try 7.10 and the daily cvs drivers in the future.

---

### Post by wieman01 on 2008-01-30
> **rustybronco said:**
> In 7.04 wpa-tkip is a no go.
I may try 7.10 and the daily cvs drivers in the future.
Too bad. Thanks for replying. This driver is no option for me under the circumstances.

---

### Post by daveteran on 2008-01-30
Those of you that got this method to work on a fresh Gutsy install, did you have adaptor plugged into the computer all the way through the process from inserting the live disk and installing Gutsy through to getting a working connection?

---

### Post by pcrussell50 on 2008-01-31
> **daveteran said:**
> Those of you that got this method to work on a fresh Gutsy install, did you have adaptor plugged into the computer all the way through the process from inserting the live disk and installing Gutsy through to getting a working connection?

yes.  i did this very thing, and no-go.  does not work.  you can see all the available wirelss networks and their signal strenghths, but it WILL NOT connect.

only now that i've followed alex's procedure, it no longer sees any wireless networks either.  i have a regular wired connection too, so all's not lost.

wonder if anyone knows if there are usb or pci wifi adapters that are known to work.

-peter

---

### Post by pavlick on 2008-02-07
Hi, I am a complete beginner to Linux and my problem occurs right in the beginning, when i try to extract the files into my home directory, apparently I am NOT the admin and i do not have the right privileges!? So how can i change my permissions? or did i not install Gutsy properly? Thanks, i want to see if this guide will help me!

---

### Post by daveteran on 2008-02-07
Hi pavlick, your "home" folder is not located at /home but for example /home/pavlick. If you are logged in as the user "pavlick" you should have proper access permissions for that folder. How are you trying to extract the files?

---

### Post by pavlick on 2008-02-07
oh alright, that will work, i thought it was /home but /home/pavlick sounds perfect, i'll get back at you once im done the above :) thank u

---

### Post by pavlick on 2008-02-07
so, i did all of ur instructions alex, hoping that THIS will finally fix my problem, but trying to go to a website with firefox got me nowhere, it's not working, and the adapter link light doesn't even flash at all, looks like its making no effort what so ever. So any suggestions which might help me?

---

### Post by pavlick on 2008-02-07
never mind me, i forgot that i turned the WEP security back on my wireless. works like a charm, THANK A TON, FINALLY I HAVE INTERNET, SO HAPPY. MANY SAID IT BEFORE, I LOVE YOU MAN, i really WOULD hug YOU if i could. THANK U THANK U THANK U!

---

### Post by sir_pewe on 2008-02-11
Thank you very much.
This helped me get my wusb54g to work!
Finally I can rock :guitar:

// Per

---

### Post by pavlick on 2008-02-11
if anybody could make the same guide for the Linksys Wireless-B Notebook Adapter WPC11 ver.4, that would be awesome, I need that for my laptop!

---

### Post by mikeyphys on 2008-02-19
Hi,
First of all I am pretty much brand new to linux, I have tried a couple different distros over the past few years but got lost in the learning curve. I've decided to give it a better attempt this time though, surely it isn't THAT hard to get to grips with it?

Anyway,

I have a WUSB54G v.4 from Linksys, I have just installed Ubuntu(7.10) from the DVD. I haven't changed anything yet. I can find wireless networks but when I try to connect, nothing. It just comes back with the popup for networks security code. I'm using WEP encryption, as I figured it would be best for compatibility.

I've read through the instructions but I don't understand what i'm supposed to do with:
linux-headers-'uname -r' - which you can get from a quick search at packages.ubuntu.com

Where and when do I use this, because it doesn't come up again in your instructions, even if someone could just explain it's purpose that would be great! hah, sorry.

Thanks!
mikeyphys

---

### Post by pavlick on 2008-02-19
hello,
as far as i can remember u just have to make sure that you have your Ubuntu CD!
dont worry about the step linux-headers-'uname -r' unless smth doesn't work out.
so just download the driver from serial monkey and follow the rest of the instructions. it will ask u to install ur ubuntu cd, at which time do so, follow through to the end, and u'll get urself a working internet connection!

---

### Post by pavlick on 2008-02-19
can anybody help me? I have the MOST puzzling problem! I have a dual-boot system, Windows XP and Ubuntu 7.10! Lately I have been using only my ubuntu but felt like playing a few windows games and I started to boot into my Win XP. at the Windows loading screen, my computer restarts. so i tried to start up in safe mode with networking, restarts as well, but I get a blue screen which says smth about rt2500usb.sys . i have not changed anything in my windows at all, is there anyway that using the rt2750 driver from this tutorial it would somehow affect the hardware in the usb adapter itself? how can i solve this?
ps, i have a wusb54g v4
thank you

---

### Post by mikeyphys on 2008-02-19
Well, I'm back already, despite my uncertainty with that particular thing I mentioned in my last post, I tried it, step by step, and... well... it WORKED!! HUZZAAAH!!! Thank you for your guide, I don't really know what was different when I tried this two days ago but I reinstalled and retried and it's working now!

Thanks for the guide!

---

### Post by pcrussell50 on 2008-02-19
which set of instructions did you follow?  there was one set for using ndiswrapper, and one set for NOT using ndiswrapper.

i followed the set of instructions for NOT using ndiswrapper...twice...on two different computers with a fresh install of 7.10, and i actually went backwards.  not only did it not work, but now i can't even see available networks anymore.  this is hugely frustrating.  does anybody know how i can get back to where i can at least see available networks again...even if it won't connect?  IOW, how do I REVERSE the procedure so I can try it again?

-peter

---

### Post by pavlick on 2008-02-19
u are NOT supposed to see the available networks, you HAVE to enter all the connection information by urself, manually! as to going backwards i guess you would have to remove the blacklist line for rt2500usb that you've added!but that willl not get you anywhere! follow the last few points of the instructions carefully if u want to connect, just enter all the info manually and you are SET!

---

### Post by pcrussell50 on 2008-02-19
> **pavlick said:**
> u are NOT supposed to see the available networks

Interesting...not only did **I** see all available neworks before I followed the instructions, but so did mikeyphys, the guy above with the success story.  Here's a quote from his first post:

mikeyphys said:
> I have a WUSB54G v.4 from Linksys, I have just installed Ubuntu(7.10) from the DVD. I haven't changed anything yet. **I can find wireless networks but when I try to connect, nothing**.

This was EXACTLY the problem I had until I followed the instructions.  Now I can't even see available networks anymore.  I'll try to mess with removing the blacklist thing and see if I can get back to where I started.  Bolding mine, for emphasis.

-Peter

---

### Post by martinw89 on 2008-02-19
> **mikeyphys said:**
> I've read through the instructions but I don't understand what i'm supposed to do with:
linux-headers-'uname -r' - which you can get from a quick search at packages.ubuntu.com

Where and when do I use this, because it doesn't come up again in your instructions, even if someone could just explain it's purpose that would be great! hah, sorry.

Thanks!
mikeyphys

It's great that you've got the problem finished, but for the sake of anyone finding your post (whether through google or the forums) I just wanted to mention the purpose of `uname-r`.  Please see: [http://ubuntuforums.org/showthread.php?p=4054173#post4054173](http://ubuntuforums.org/showthread.php?p=4054173#post4054173)  The backticks in that command are a nifty little trick that makes things easier when making copy-and-paste guides etc.

---

### Post by pavlick on 2008-02-19
here's the deal, before u had the rt2500 driver, with it u saw the wireless networks u could connect to, but u couldn't connect to them, it just won't work. now ur using the rt2750 driver,with it, you can't see the networks u want to connect to, but with the proper information (SSID NAME, and password) you can connect no problem! all u ahve to do is configure ur wirelss settings, im on my windows system right now, and i cant remember where exactly u go to configure it, but if u want i'll restart and give u step-by-step instructions!

---

### Post by mrudolph on 2008-02-19
I have the exact same wireless adapter, but I have been unable to make this work, even on a fresh install.  I have also tried using ndiswrapper, but I was also unsuccessful with that.  I am able to detect the networks (at least I am when using ndiswrapper), but I cannot connect.  I am certain that my wireless adapter is funtioning properly, as it still works in xp.  I usually prefer to merely lurk in forums, but I have been working on this for quite some time, without success.

At one point, this device did work in ubuntu, but after one of the updates to gutsy it no longer worked.  When I would choose the earlier version from grub, it would still work, though.  

Any advice or suggestions would be greatly appreciated.

---

### Post by pavlick on 2008-02-19
when it did work on gutsy earlier, before the update, did it work natively or through ndiswrapper?

---

### Post by mrudolph on 2008-02-19
It worked natively in Gutsy at first.  It was a little bit sporatic, though.  It was very consistent in fiesty, but when I upgraded to Gutsy, it would work intermittently and require me to reconnect about every half hour (which was really annoying).  With a later update to gutsy, it stopped working, and i've never been able to really fix it.

---

### Post by pavlick on 2008-02-19
i've actually reinstalled gutsy myself right now, and trying to make my adapter work with ndiswrapper? u've tried this before and u've had no luck?maybe try to do a fresh install of gutsy and see if ndiswrapper will work then

---

### Post by mrudolph on 2008-02-20
I had already tried the fresh install w/ ndiswrapper, and it didn't work.  I'm pretty sure that I did it right, which is why I came here to ask for help.  I'm completely baffled as to why I can't get it to work.

---

### Post by rustybronco on 2008-02-20
wrong thread sorry.

---

### Post by pavlick on 2008-02-20
> **mrudolph said:**
> I had already tried the fresh install w/ ndiswrapper, and it didn't work.  I'm pretty sure that I did it right, which is why I came here to ask for help.  I'm completely baffled as to why I can't get it to work.

i really think u should try the ndiswrapper. it works for me perfectly, without the need to configure it all manually, just do a fresh install and i'll try to give u step-by-step instructions. i had trouble following some instructions on the forum for ndiswrapper but i've got through it myself and now my wireless is working perfectly. i can supply u with all the files that i used

---

### Post by mrudolph on 2008-02-20
I suppose I could give it another try.  I'm relatively sure that when I installed ndiswrapper on a fresh install last time I did it right (when I followed instructions, the results I got back in terminal were what the tutorial said they should be).

Thankyou for offering to help.  I'll give it another try if you don't mind walking me through it.

---

### Post by pavlick on 2008-02-21
> **mrudolph said:**
> I suppose I could give it another try.  I'm relatively sure that when I installed ndiswrapper on a fresh install last time I did it right (when I followed instructions, the results I got back in terminal were what the tutorial said they should be).

Thankyou for offering to help.  I'll give it another try if you don't mind walking me through it.

First off you will need to save the latest ndiswrapper source files as well as the latest driver files on a CD or a Flash Drive to put it on you fresh install of Ubuntu.

Download Ndiswrapper 1.52 here: [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.52.tar.gz?modtime=1201988892&big_mirror=0]("http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.52.tar.gz?modtime=1201988892&big_mirror=0")

Download the most recent drivers from Linksys here: [http://www-ca.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=CAen%2FLayout&cid=1153781228635&packedargs=sku%3D1153781424459&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=2863512181B03]("http://www-ca.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=CAen%2FLayout&cid=1153781228635&packedargs=sku%3D1153781424459&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=2863512181B03")
Click on the Download Driver

Now that you have your files and your fresh install of gutsy, copy the files on your dekstop and extract them to their respectful folders,

Make sure to have your Ubuntu 7.10 CD inserted in your CD drive in order to get the needed dependencies to build ndiswrapper.

Once all of the above is finally done, let's get to the terminal.

First let's get the dependencies from the Ubuntu CD:
```
 sudo apt-get install build-essential 
```

When you're done installing those (if no errors come up)
We can move onto removing any old ndiswrapper files (not like there should be any, but just a precaution)

Navigate to the ndiswrapper folder and do make uninstall:
```
 cd '/home/**YOURUSERNAME**/Desktop/ndiswrapper-1.52' 
sudo make uninstall
```

Now we need to blacklist your current driver for your wireless adapter:
```
 sudo gedit /etc/modprobe.d/blacklist 
```
and at the bottom of the file add:
```
 blacklist rt2500usb 
```
save the file and exit it.

Then we compile the ndiswrapper:
```
 make 
```

And install it:

```
 make install 
```

Hopefully all of the above worked without any problems, now that we got ndiswrapper installed let's install the driver:
```
 ndiswrapper -i '/home/**YOURUSERNAME**/Desktop/WUSB54Gv4_20050503/Drivers/WUSB54Gv4/rt2500usb.inf'   
```

Let's check if the driver is installed and compatible with your device:
```
 ndiswrapper -l 
```

You should get back something like this:
```
rt2500usb : driver installed
        device (13B1:000D) present (alternate driver: rt2500usb)
```
if you don't then something is wrong, so let me know what you get.

Now you have to activate the driver
```
 sudo modprobe ndiswrapper 
```

And inorder for ndiswrapper to run at start up you have to edit the modules file:
```
sudo gedit /etc/modules
```

and add
```
ndiswrapper
```

right before
```
loop
lp
sbp2
fuse
```
save the file and exit it.

also just in case make ndiswrapper replace itself as the driver in modules, type this in the terminal as well:
```
sudo ndiswrapper -m
```

This should just about do it, restart your computer and you should have your perfectly working internet connection.
Hit me back when you get a chance to try this. Hope it works. Just follow the instructions carefully. Good Luck.

---

### Post by synthoid on 2008-02-24
I can't find this package anywhere:

linux-headers-'uname -r'

Could someone point me to a direct link? I already tried searching in the packages section of the site.


EDIT: Nevermind, I found this same query earlier in the thread. Sorry all.

---

### Post by Donmeister on 2008-02-24
Okay, I came across this tutorial so I gave it a try and it works somewhat.  Here's a problem though.  When I enter manual configuration, I enter all of my details like ESSID, network password, encryption type and set DHCP.  Then I click on the network under the network manager icon at the top and it asks me for my passphrase.  I enter it and I get bars with no signal strength.  When I go back to manual configuration, all of my details are erased.  Oh, and I check enable roaming mode too.  Is there something I missed?

And if you haven't noticed, I'm a Linux n00b.  Sorry.

---

### Post by pavlick on 2008-02-24
basically the problem is that first you start configuring ur network manually and then u tell it to use the roaming mode, which is all automatic. DO NOT check the roaming mode, just set everything manually, ur essid and password and DHCP, set all that, leave roaming mode UNCHECKED! after you click okay in that screen, put a checkmark next to your wireless connection and press okay again, this way it should work, its all in alex's instructions on the first page

---

### Post by dkitty on 2008-02-24
I transferred the [coreutils](http://packages.ubuntu.com/gutsy/coreutils) package (containing rname) and the rt2500-cvs-daily tarball to my PC by USB stick. Your instructions worked beautifully for me AlexMono94. Thank you.

---

### Post by archangelabove on 2008-02-25
Okay, So..

I followed all the directions in the original post, but no luck.

lshw -C network outputs:

>   *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: rausb0
       capabilities: ethernet physical wireless
       serial: 00:12:17:7d:50:be
       configuration: broadcast=yes multicast=yes wireless=RT2500USB WLAN

Why is it still using RT2500USB?

Also, I may be running into an issue in the manual configuration portion of the how-to, because my network has no WPA or WEP. I just choose WEP and leave the password blank. DHCP does everything IP wise. I'm thinking, maybe it might help if I manually put in an IP address, based off of my other computers on the network?

Some help would be great. I've been trying to figure this thing out for days. Im very close to just buying a usb device that is known to work good with Gutsy.

---

### Post by pavlick on 2008-02-25
well make sure that u have ur rt2500usb blacklisted, i guess its not if its still using that driver. also did u restart before trying it out?and in manual configuration, if u dont have any security like WEP, just dont pick anything, leave it a WPA i believe and leave it blank, it works like that! so try ```
sudo gedit /etc/modprobe.d/blacklist
``` and adding ```
blacklist rt2500usb
``` again and make sure u save the file before u exit! good luck!

---

### Post by pavlick on 2008-02-25
also the network being disabled, did u put the checkmark next to your wireless connection in manual configuration?

---

### Post by archangelabove on 2008-02-25
I put a check in the box, well an "X" anyway. now the DISABLED part is gone.

I put in the blacklist:

"blacklist rt2500usb"

and

"blacklist RT2500USB"

But sitll, "lshw -C network" still outputs that it is using rt2500usb.

is there no way to force the driver to be installed on the device? should i reinstall the drivers?

---

### Post by pavlick on 2008-02-25
that is weird, i dont undestand why the driver isn't installed properly. well have just one entry of the blacklist rt2500usb, reinstall the rt2570 driver again, see if anything will change, just dont forget to restart!

---

### Post by pavlick on 2008-02-25
the thing is that ur already forcing the driver onto the device i just don't see how it is not working out for u :S

---

### Post by archangelabove on 2008-02-25
Sweet. I got it.

I just redid the process. Reinstalled it all.

And now I'm online!

YES.

Now to install my printer and get this Ubuntu rig going!

---

### Post by pavlick on 2008-02-26
glac i could help,somewhat :)

---

### Post by thegoochisloose on 2008-02-26
thank you pavlik.  after hours of messing with this i found your instructions and they worked perfectly within about 5 minutes i had my wireless working

---

### Post by pavlick on 2008-02-26
no problem, do u mean the instructions to install ndiswrapper?

---

### Post by pauljs75 on 2008-02-28
I'm going to have to try this, since my PCI based Linksys WMP54G v.4.1 (Ralink RT61 chipset) wireless doesn't work right using the default Ubuntu install...  Wish me luck, I'm still very new at this.

I keep seeing elsewhere in my googling and forum browsing of the topic that wireless usually worked in older versions. And I have read that they changed from IPv4 to IPv6 for their network protocol in the latest release. Anyone think that could explain why the wireless functionality got broken?

Also I hope they get this fixxed on the default install. From what does work - Ubuntu makes desktop linux look pretty ready for "typical users". But the non-working wireless network thing is a big owwie upon the user experience. ](*,) Once they get this remedied, I don't see a reason not to recommend Ubuntu for most people with basic computing needs.

---

### Post by hookzilla on 2008-03-08
Frist, I'm a newbie, so I may not know some of the basic stuff yet.   I tried to follow the procedure, but still have no luck.   iwconfig still shows rt2570usb as the driver.  I think I may not have done the first steps of installing the "build-essential-linux-headers-`uname -r`" correctly.  Is there a way to reverse  the procedure and start over without a clean install?   I've read thru the posts, but at this point I'm more confused than "educated".   Thanks in advance for any help.

---

### Post by pavlick on 2008-03-09
just a few quick questions, iwconfig shows rt2570usb as the driver or rt2500usb? it is supposed to show rt2570! don't worry about the installation of the build essentials. Just make sure you have configured your wireless connection manually (write in the ESSID, and the password as well as set the IP address either to automatic DHCP or a manual one), and that you have blacklisted the rt2500usb in the /etc/modprobe.d/blacklist on the bottom. Also, in the terminal try writing ping google.com and see what it bring back!

---

### Post by hookzilla on 2008-03-09
Thanks for the response.      The driver is RT2500USB, not RT2570USB

iwconfig reports:
rausb0    RT2500USB WLAN  ESSID:"West8208"  Nickname:""
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-120 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ping google.com reports:
user@Ubuntu:~$ ping google.com
PING google.com (64.233.167.99) 56(84) bytes of data.
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=2 ttl=234 time=56.9 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=3 ttl=234 time=62.3 ms
........
--- google.com ping statistics ---
138 packets transmitted, 77 received, 44% packet loss, time 137059ms
rtt min/avg/max/mdev = 55.549/60.886/67.152/3.850 ms

Thanks again

---

### Post by hookzilla on 2008-03-09
Sorry 'bout  me....
When I posted the ping results, I was wired.    Unwired, ping returns unknown site.
Thanks

---

### Post by xjgnsdof on 2008-03-11
I followed the steps in Xubuntu 7.10 (replacing "gedit" with "mousepad," of course), but I still can't access the web through the Linksys adapter. What outputs should I post for you all to pinpoint the problem?

---

### Post by hookzilla on 2008-03-11
Well, progress of sorts....  I am using my WUSB54G V4 in Ubuntu 7.10 as I enter this.  The post by kevdog "Useful resources for beginners setting up your wireless connection" (t= 596797) mentioned that rutilt is an alternate to wireless manager for RA chipsets.  I tried it and here we are in wep at 11 mbps.  So, it works.  However, I'm using the RA2500USB driver, even though I  supposedly  have it blacklisted.   I haven't given up on using the other method, but at least I know the hardware works.  

 Is there a way to list all of the drivers installed?  Maybe the ra2570usb driver didn't install correctly?  Or maybe I only think I have the ra2500usb driver blacklisted?   

Any additional help is appreciated.

---

### Post by xjgnsdof on 2008-03-11
I notice that my network password doesn't stay in the field. That is, once I exit the window, then re-enter the network settings, the field goes blank. I think that this is stopping me from accessing my wireless network. Any ideas on how to fix this in Xubuntu?

---

### Post by pavlick on 2008-03-11
> **elgilicious said:**
> I notice that my network password doesn't stay in the field. That is, once I exit the window, then re-enter the network settings, the field goes blank. I think that this is stopping me from accessing my wireless network. Any ideas on how to fix this in Xubuntu?

I have no idea about Xubuntu, sorry I cannot be much help, just make sure you have the right encryption selected and try again.

As for hookzilla,
I would recommend you follow the instructions once more and try to make it work, it that won't work, you can always use ndiswrapper! I have the instruction a few pages back on how to make that work as well. But you should not have any problems with the method from Alex, it works like a charm, so I advise you to try it again, make sure you blacklist the RT2500usb driver properly, double check everything and do everything again, and it really should work

---

### Post by xjgnsdof on 2008-03-11
FOR XUBUNTU USERS
I am happy to report that I got the wireless adapter to work in Xubuntu 7.10.

Instead of blacklisting "rt2500usb," as the guide suggested, I blacklisted "rt2570." Maybe because I'm using Xubuntu, I had to blacklist something different; I really don't know. But, after changing that single line in /etc/modprobe.d/blacklist, the adapter finally recognized my home wireless network.

Another important distinction from the guide posted at the start of this thread: I didn't manually configure my wireless network. Rather, the WUSB54G was in roaming mode and found it. Once I entered the password and picked a keyring, I was all set.

---

### Post by hookzilla on 2008-03-13
After some success using rutilt to connect with my WUSB54G V1, I have done a clean install and upgrade to 7.10.   I followed the procedure again and got the same results - no connection.   I even tried blacklisting rt2571usb like elgilicious, but that didn't work either.   

Any suggestions?  I may have to revert to rutilt?

---

### Post by pavlick on 2008-03-13
hi,
well this post will help u with the V4 of the linksys adapter not the V1, however you could try using ndiswrapper, a few pages back I posted step by step instructions how to do that, the only difference for you, is you would specify the linksys driver for your adapter from the V1 folder. Let me know if i can be of any more help in the future!

---

### Post by hookzilla on 2008-03-13
My, bad......   Adapter is WUSB54G V4.     (I have a WUSB54GS V1, but as you say that's another thread and another day.)    Thanks.

---

### Post by lemmalone on 2008-03-18
I want to thank AlexMono for posting on this; I got my WUSB54 v4  working quickly after following his instructions. As a very new user of Mythbuntu (7.10) I also wanted to report on my hardware and a couple of extra things I had to do  in case it will help others who have had more difficulty. The motherboard is an MSI K9N Platinum, with AMD64 x2, and the kernel I am running is (I believe) 2.6.22.14 generic. I used a wired connection so I  downloaded the serialmonkey daily build, build-essenial, and the kernel headers using Synaptic. Then I removed Device Manager completely, also via Synaptic. I mention this because I probably should have waited, because this brought down my wired internet connection and I had to restart manually. Then some additional steps:

Although the drivers installed correctly, "sudo ifconfig -a" still showed my wireless as "wlan0."
 In addition to blacklisting rt2500usb I had to remove the module manually, "sudo rmmod rt2500usb" and insert the rausb0 module: "sudo modprobe rausb0". Now "sudo ifconfig -a" showed the adapter as "rausb0" and I was able to scan and find my router, "sudo iwlist rausb0 scan," and connect to the router and the web. (I think I did "sudo iwconfig rausb0 mode managed essid ["router essid"]", then "sudo dhclient rausb0" and the internet came up.

Next I opened the interfaces file (using emacs21 but use your text editor) "sudo emacs21 /etc/network/interfaces" and added the following two lines:

auto rausb0
iface rausb0 inet dhcp

The difference here is that in AlexMono's example I believe that "wlan0" had to be replaced by "rausb0," but I had no wireless entry in the interfaces file (I had one previously but in changing settings it had disappeared.) I had installed RutilT after removing Network Manager but configured my network manually; now I opened RutilT and it showed the correct information.

A final note my original problem. I hesitated in installing the serialmonkey drivers because I thought that the default ones were working. Using the standard rt2500 drivers I had been able to scan for my router (occasionally), to connect to it always, and to ping it. I could never get dhclient to connect properly, however, thus no internet--the "no working leases" problem. So if your wusb54 seems to be working except that you can't get on the net, AlexMono's cure may fix your problem. It did mine. Good luck!

---

### Post by darkendshadow on 2008-03-23
i fallowed the instructions on a fresh install of gutsy and so far it has worked except my transfer speeds are ridiculously slow. can anyone help?

edit: got it figured out :)

---

### Post by trieb on 2008-03-24
Slow greatly depends on the signal strength, post some info from running 

iwconfig


On a similar note, has anyone noticed the device shutting off after a certain amount of time and heavy utilization?

---

### Post by martinw89 on 2008-03-25
trieb:  There is a known bug in the Gutsy kernel where large amounts of wireless data transmission seem to cause some system problems.  I know a bug report exists but sorry, I don't have the exact report right now.

Hope that helps!

---

### Post by hookzilla on 2008-03-27
Today I managed to install wicd.   It handled the wireless/adapter with no problem.

Thanks to all for the help,  Especially pavlick.  This is a great forum.

---

### Post by Xodarap on 2008-04-01
It worked for me until after the first reboot. After rebooting, my network manager doesn't even have the wireless option (it was there before). 

I have attached what I think are some relevant details, it's finding the physical USB device but no wireless stuff. Let me know if there's more.

```

ben@ben-desktop:~/rt2570-cvs-2008040117$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ben@ben-desktop:~/rt2570-cvs-2008040117$ lsusb
Bus 002 Device 002: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
**Bus 005 Device 002: ID 13b1:000d Linksys **
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

ben@ben-desktop:~/rt2570-cvs-2008040117$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:8F:A2:D9:65  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:fea2:d965/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1889 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1550 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2076959 (1.9 MB)  TX bytes:321037 (313.5 KB)
          Interrupt:20 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:675 (675.0 b)  TX bytes:675 (675.0 b)

ben@ben-desktop:~/rt2570-cvs-2008040117$ dmesg | grep "wlan"; dmesg | grep "wireless"; dmesg | grep "wusb"
ben@ben-desktop:~/rt2570-cvs-2008040117$ 

```

My sound also seems to have died, although this could be unrelated.

---

### Post by wscott52 on 2008-04-02
Thanks for your help.

After installing Ubuntu 7.10 on my computer yesterday I disovered my USB WiFi adapter didn't work. After trying a couple of other "fixes" that did involve installing ndiswrapper and ndisgtk and didn't work I found your post. While it was a little intimidating for a complete Ubuntu and Linux novice, but not a computer novice, I am now able to use the Linksys adapter. I'm not sure how well I followed your instructions. I didn't have to install anything off the disk but maybe I had already done it trying one of the other fixes. Just wanted to let you know you're appreciated. I'm sure I'll have other issues.

---

### Post by stevenmitnick on 2008-04-04
I am using 7.10 and have a Linksys USB 54G V4 wireless adapter. I have spent quite a bit of time trying to get it operational to no avail. Hard wire is working but wireless has never worked. When I click on the Network-Manager it shows a good signal and when I click on the radio button to connect it to the network a window pops up to request the passphrase. After I enter the passphrase and click login into network the program searches for several moments and then shows two monitors in the upper right corner. The problem is that the wireless is still not connected to the network. I followed instructions at, which are similar to the ones above: [http://blog.eksfiles.net/2008/01/05/using-the-linksys-wusb54g-v1-or-v4-with-ubuntu-gutsy/](http://blog.eksfiles.net/2008/01/05/using-the-linksys-wusb54g-v1-or-v4-with-ubuntu-gutsy/) 
Does anyone have any suggestions on what else I can do to establish the wireless network connection? Thanks ahead of time for any assistance.

The following is what I get from the terminal:

steven@family:~$ $ndiswrapper -l
bash: -l: command not found
steven@family:~$ ndiswrapper -l
rt2500usb : driver installed
device (13B1:000D) present (alternate driver: rt2500usb)
steven@family:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

eth1 no wireless extensions.

wmaster0 no wireless extensions.

rausb0 IEEE 802.11g ESSID:”"
Mode:Managed Frequency:2.437 GHz Access Point: Not-Associated
Retry min limit:7 RTS thr:off Fragment thr=2346 B
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

steven@family:~$ lsusb -v | more

Bus 005 Device 002: ID 13b1:000d Linksys
Device Descriptor:
bLength 18
bDescriptorType 1
bcdUSB 2.00
bDeviceClass 0 (Defined at Interface level)
bDeviceSubClass 0
bDeviceProtocol 0
bMaxPacketSize0 64
idVendor 0×13b1 Linksys
idProduct 0×000d
bcdDevice 0.04
iManufacturer 1
iProduct 2
iSerial 0
bNumConfigurations 1
Configuration Descriptor:
bLength 9
bDescriptorType 2
wTotalLength 32
bNumInterfaces 1
bConfigurationValue 1
can’t get device qualifier: Operation not permitted
can’t get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
–More–can’t get hub descriptor: Operation not permitted
can’t get device qualifier: Operation not permitted
can’t get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can’t get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can’t get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can’t get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can’t get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

---

### Post by stevenmitnick on 2008-04-04
There is not supposed to be smiley instead it is supposed to read:
Retry min limit:7 RTS thr:off Fragment thr=2346 B

---

### Post by spaceship9 on 2008-04-05
I've read through this thread and am unable to find a solution to my problem that actually worked
I followed the instructions exactly, and end up with failure.
The connection doesn't connect, just displays the two monitors
I know my connection info (essid, passphrase, encryption type)  is correct
iwconfig shows I'm still running the 2500 drivers even though I blacklisted it correctly
editing /etc/networks/interface shows no sign of rausb1 or rausb0, only wlan... upon attempting to switch wlan to rausb, it just creates a new listing
And i've restarted practically after any change, to no luck
It is the WUSB54G v4 and I am indeed running Gusty
No errors in the installation either

Rather unfortunately the computer does not have wired internet access, so I have to switch the drives back to windows and/or use my laptop (which happily IS running ubuntu :) ) when I search for help or download files...

---

### Post by jacoblyles on 2008-04-18
I would just like to give a big THANK YOU!!!! to the threadstarter for getting me back on Linux after being stuck with Windows for several months. 

Thank you, thank you, thank you.

---

### Post by AlexMono94 on 2008-04-20
I've just installed the Hardy Release candidate, and guess what!?

WUSB54G Doesn't Work!

And here's the worst of it, the method here doesn't work! :(

Any ideas?

---

### Post by AlexMono94 on 2008-04-20
> **AlexMono94 said:**
> I've just installed the Hardy Release candidate, and guess what!?

WUSB54G Doesn't Work!

And here's the worst of it, the method here doesn't work! :(

Any ideas?

Not to worry, pavlicks ndiswrapper solution works great! Wonderful work pavlick! :)

---

### Post by daveteran on 2008-04-22
With regards to Pavlick's ndiswrapper solution a few pages back, is there any particular reason why you need the latest ndiswrapper source rather than the version supported by the current Ubuntu distribution as used in Wieman's ralink solution?

---

### Post by Happy Grandad on 2008-04-23
Many thanks to Alex Mono94 for this excellent guide in the original post, although my setup is a bit different.

I'm using a WMP54G wireless adapter on a Hardy Heron install and have been suffering from random disconnects due to the notoriously buggy rt61pci driver. I have tried other long-winded methods of installing the rt61 (no pci) driver without success but after downloading the rt61 driver from the serial monkey site and then following your guide, substituting rt61 where appropriate, it worked flawlessly.

Thanks again :)

---

### Post by jacoblyles on 2008-04-27
I would like to report that this solution also worked after I upgraded to 8.04 and my wireless config broke post-upgrade. Thanks again!

---

### Post by pavlick on 2008-04-28
I am very glad that I could help out. AlexMono, you actually inspired me to make the ndiswrapper how-to post. I looked for solutions all over the forums and not once have I found a full one with regards to installing and making ndiswrapper work so I decided to make my own. I am a novice at Linux but we try :) . Hope to see more great solutions from all of you in the future, and I will try to help as much as I can. I am too now finally running Hardy with the ndiswrapper fix. Works like a charm :)

---

### Post by ahawesome on 2008-04-28
I just tried the ndiswrapper solution, and I think the last command messed up my system. The computer now freezes on the message that it is loading bluetooth. If I'm correct that last command should have replaced ndiswrapper as the default driver in modules, according to pavlick. I believe Ubuntu is trying to find a bluetooth driver in ndiswrapper and having no luck. There must be some way to disable bluetooth at startup or remove ndiswrapper as the driver, I do not need the bluetooth functionality. I am using Hardy, by the way. Finally, I actually installed drivers for a linksys WUSB11, substituting file names where appropriate, instead of a WUSB54G. Please help, and thanks in advance.

---

### Post by I Was Drunk At 4 on 2008-04-28
pavlick, thanks man!  My WUSB54G was working pretty crappy in 8.04 but it's all good now.  One question though ... do I still need to keep both of the extracted folders (the driver and the ndiswrapper), and if I do can I at least move them somewhere else (off my desktop) or would that mess **** up?  Once again, thanks.

---

### Post by pavlick on 2008-04-28
u can delete the folders, all the files have been copied to where they have to be so those folders are now useless. i would advise u to put them on a cd or usb stick for future use so u dont have to re-download it them if u will need to ever reinstall it all

---

### Post by mkgnsr on 2008-04-30
I'm new to Ubuntu and Linux and new to this forum as well.  I just wanted to thank everyone for their hard work and great effort for us who have the Linksys WUSB54G.  I spent hours trying to get this to work when I first installed Gusty in January and my hours of effort with a lot of help payed off as I was able to get it to work.  I tried to upgrade to Hardy a couple of days ago and once again my wireless didn't work.  Trying the things that did work in Gutsy were not working in Hardy.  My solution, I re-installed Gutsy and I bought a D-Link WDA-1320 with the Atheros chipset and it worked out to the box.  I'm going to give it a few weeks before trying Hardy again.  My intention with this post is not to be a wise guy but I need my system to work as I provide off hour system support for a large insurance company.  I enjoyed the challenge of getting the WUSB54G to work but in the end I needed my system to work.

---

### Post by pavlick on 2008-05-01
Well we have been successful with getting the WUSB54G v4 working under hardy with ndiswrapper, have u tried that solution? it works and it is really easy to set up, my detaited, step-by-step instructions are a few pages back. Hope it helps. It is unfortunate that the WUSB54G v4 doesn't work out of the box :( hopefully it'll get fixed in the next release or so.

---

### Post by daveteran on 2008-05-01
AlexMono94's solution works fine for me on a fresh Hardy install. Am I the only one??

---

### Post by AlexMono94 on 2008-05-09
I think I'll make a video on how to get this darn adapter working and post it on  YouTube, hopefully it will make getting it to work easier. :)

---

### Post by devosion on 2008-05-10
I'd just like to add that your guide helped resolve my issues with a slow connection in Hardy and finally got me away from using ndiswrapper. Greatly appreciate it. :)

---

### Post by AlexMono94 on 2008-05-10
My video is finished and it's uploading to YouTube now. :)

---

### Post by AlexMono94 on 2008-05-10
The video is up, here it is: [http://www.youtube.com/watch?v=fskARysZRwM](http://www.youtube.com/watch?v=fskARysZRwM)

Please rate (nicely) and comment.

---

### Post by cptnff on 2008-05-18
Ok, so I had my wireless up and running in hardy, but a few days ago it stopped working. Everything seems to be installed just fine, but for some reason I can't connect. I've tried uninstalling and reinstalling ndiswrapper, and the driver. I also tried it on the previous kernel, because that's what I had to do to get it to work in the first place. Does anybody have any ideas? help would be greatly appreciated. 

Never mind, i got it working by switching to roaming, but now my connection strength is kind of crappy. right now I'm at 34%, so I'm looking at this as a temporary solution.


well it looks like I still need some assistance. using roaming only worked that one time. When I turned my computer on today, I'm right back where I started... no connection. in roaming mode it says I have a signal strength of 78%, and it recognized the wireless network I connect to, and my wusb54gv4 is definitely installed, but for some reason no matter what I do I cant connect to the internet.

---

### Post by n0deal on 2008-05-21
Thanks for the pointers, worked like a charm!

---

### Post by devosion on 2008-05-29
After using AlexMono's method for a day my connection began to act up and then was unable to authenticate to my router at all. So instead I tried pavlick's method, but im running into the unusual problem of whenever I blacklist rt2500usb wlan0 disappears from iwconfig. And when I try to manually input it through connection manager it is associating it with eth0. 

Runnin lsusb shows that my machine is still picking up the linksys wifi dongle but it is not associating it with ndiswrapper. Any ideas how I can get around this?

BTW im using Hardy.

---

### Post by pavlick on 2008-05-29
hi devosion, 
im not expert at these troubles man, 
my best advice would be this: reinstall HARDY, do it my way (ndiswrapper) cuz alex's way is more complicated and you CANNOT use roaming mode his way, u have to manually type all the network information. I honestly do not see any difference while using ndiswrapper except that u do not run into any probelms at all :) especially in HARDY. alex's way was THE WAY in GUTSY, but it barely works for ppl on hardy. so all the best!

BTW, u dont have not reinstall, u can try to use the ndiswrapper way now, i am not really sure how alex's solution will effect that, but i would reinstall. if u can, DO IT :)

Regards, 
Pav

---

### Post by devosion on 2008-05-29
> **pavlick said:**
> hi devosion, 
im not expert at these troubles man, 
my best advice would be this: reinstall HARDY, do it my way (ndiswrapper) cuz alex's way is more complicated and you CANNOT use roaming mode his way, u have to manually type all the network information. I honestly do not see any difference while using ndiswrapper except that u do not run into any probelms at all :) especially in HARDY. alex's way was THE WAY in GUTSY, but it barely works for ppl on hardy. so all the best!

BTW, u dont have not reinstall, u can try to use the ndiswrapper way now, i am not really sure how alex's solution will effect that, but i would reinstall. if u can, DO IT :)

Regards, 
Pav

I've been able to use your way (ndiswrapper) before in Gutsy when I hadnt used Alex's way. This had been my preferred method since Feisty as well. The strange thing is that in Hardy whenever I blacklist the default wusb54gv4 driver (rt2500usb) my wireless device (wlan0) disappears from iwconfig. And even when I try to set up the connection manually it does not reappear. But the moment I un-blacklist it is back. Im beginning to think this is a bug in Hardy.

---

### Post by pavlick on 2008-05-30
has this problem occured to u just in one install or did u try to re-install and install the drivers with ndiswrapper on a fresh install? it should work... haven't seen ur problem around here yet

---

### Post by DirtDawg on 2008-06-02
My WUSB54Gv4 has worked in Hardy "out of the box," but it seems sort of weak.

Are those of you using ndiswrapper or the OP's method doing so for improved performance over the rt2500 driver, or because the rt2500 driver did not work at all?

---

### Post by pavlick on 2008-06-02
it hasn't worked for us out of the box, also the performance is excellent with ndiswrapper

---

### Post by DirtDawg on 2008-06-02
> **pavlick said:**
> it hasn't worked for us out of the box, also the performance is excellent with ndiswrapper

Thanks. I might give ndiswrapper a try, but since it is working, I'm worried to look a gift horse in the mouth.

---

### Post by DirtDawg on 2008-06-08
UPDATE: Even though the default open-source drivers worked out of the box on my Hardy Laptop, the signal was weak and caused consistent lock-ups. 

Installing the proprietary Windows drivers with ndiswrapper appears to run very well and fixed the signal and lockup problems. Others with similar problems can do the same with no fear of screwing things up or being forced to reinstall.

Follow Pavlick's simple tutorial on the top [page 13]("http://ubuntuforums.org/showthread.php?t=588045&page=13") of this thread *carefully* and everything should work splendidly.

A few notes, however: The Linksys driver comes in an .exe file. Running this .exe in wine will extract it (why it's not just a zip file, I'll never know).

Also, several of the commands need to be run as root, so add a "sudo" in front of them if they don't work, (ie: "sudo make install" and "sudo ndiswrapper -i etc/etc/etc/").

Good luck and thanks to Pavlick!

---

### Post by stevenmitnick on 2008-06-21
After more hours than I can count, I finally got this wireless Linksys to work. Many thanks for the information. The Youtube version was a great visual in allowing me to make sure I clicked on the correct things. A BIG THANK YOU! Now I can cut the cord and stay straight wireless on this computer.

---

### Post by sop408 on 2008-07-11
Hi, I don't have this usb adapter, but this howto also works to belkin usb adapter f5d7050 ver 1 !!!! I thought I let people know about it.

---

