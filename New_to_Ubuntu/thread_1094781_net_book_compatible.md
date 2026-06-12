---
title: "net book compatible?"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by cirabisi2009 on 2009-03-12
i have an acer aspire one netbook. 1gb ram, 120gb hard drive, intel atom, windows xp home. i want to down load it. but im not to sure on how all that works. i've read the documentation but.. its not really a guide for dummies and i want to dual boot xp and ubuntu. what am i to do? help is greatfully apreciated!

---

### Post by robertrock on 2009-03-12
If I was just starting out I would simply buy the live distro CD, boot off of it and try it out for awhile. No changes are written to your hard drive so nothing gets modified.

Here is a link (one of many) to purchase a CD:

[http://www.linuxcd.org/view_distro.php?id_distro=196&ref=distrowatch](http://www.linuxcd.org/view_distro.php?id_distro=196&ref=distrowatch)


or you can save a little $$ and download an iso and burn yo CD and boot off of it from here: (Ubunto 8.10 Desktop version)

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by mjheagle8 on 2009-03-12
[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)

shuld help.

---

### Post by cirabisi2009 on 2009-03-13
first off.. HOLY CRAP! thats gotta be the fastest answer from a web forum ever! props on that!

but there is an issue. the reason i wanted to download is the fact that i have no cd drive.. hence the net book. so please bear with me on that part. my ex. dvd drive wont be in for a lil while longer. and waiting 6-10 weeks.. doesnt exactly sound fun.. i hate waiting. ha ha 

let me know if im not providing enough info!!

---

### Post by cdwillis on 2009-03-13
If you have a thumbdrive you can install from it. Just download the ubuntu live cd and a program called unetbootin, which can be found on sourceforge.org. Unetbootin will let you install the disk to the thumdrive. You might want to use the 8.04.1 disk instead of the 8.10 disk, because the wifi drivers are broken or something. I'm not really sure, but you can search the forum for more info about which to install.

---

### Post by cirabisi2009 on 2009-03-13
sounds lovely! thank you for that tad bit of info :shock: i hope a 10gb thumb drive will work.. if not then im a be waiting for my external drive and cd. :( that'd be a super bummer huh. well thank you all for the help. hopefully next time i visit i will have ubuntu up and running ..

---

### Post by mjheagle8 on 2009-03-13
10 gig is plenty, the image is only 700 meg ish. good luck. hope you enjoy ubuntu!

---

### Post by cdwillis on 2009-03-13
That will be more than enough, I did an install of easy peasy (ubuntu for EeePCs) and I still had room on my 2 gig thumbdrive. Good luck.

---

### Post by cirabisi2009 on 2009-03-13
so a 1gb sd card could even do the trick huh.

---

### Post by funkyali on 2009-03-13
> **cirabisi2009 said:**
> i have an acer aspire one netbook. 1gb ram, 120gb hard drive, intel atom, windows xp home. i want to down load it. but im not to sure on how all that works. i've read the documentation but.. its not really a guide for dummies and i want to dual boot xp and ubuntu. what am i to do? help is greatfully apreciated!
Try [http://wubi-installer.org/](http://wubi-installer.org/)

Its easy to play with no need for a cd or thumbdrive. It will setup the dual boot options for you. I used to use it. If you dont like it you can just boot into windows and uninstall like any other windows program. It will install ubuntu, kubuntu for you,

---

### Post by cirabisi2009 on 2009-03-13
YAY! lol. but wait... ubuntu..kubuntu.. and the difference is? sorry for all the uber noob questions! ha..

---

### Post by aeiah on 2009-03-13
the difference is different desktop environments. just go with standard ubuntu for the aspire one and consider installing the netbook remix packages, or go for a distribution designed for netbooks like easypeasy. its based off ubuntu i do believe.

i run a lightweight version of ubuntu called crunchbang on my acer aspire one and everything works perfectly and it boots very quickly. i have the 1gb / 160GB version so it's very similar to yours. if you do have problems with any part of the system rest assured that it'll work with some configuring.

---

### Post by cirabisi2009 on 2009-03-13
> **aeiah said:**
> the difference is different desktop environments. just go with standard ubuntu for the aspire one and consider installing the netbook remix packages, or go for a distribution designed for netbooks like easypeasy. its based off ubuntu i do believe.

i run a lightweight version of ubuntu called crunchbang on my acer aspire one and everything works perfectly and it boots very quickly. i have the 1gb / 160GB version so it's very similar to yours. if you do have problems with any part of the system rest assured that it'll work with some configuring.

wonderful! im just having a slight issue!! 
i used this to get ubuntu onto my aspire one
[http://wubi-installer.org/](http://wubi-installer.org/)

i cant get any wifi access? what do i do? will this netbook remix package fix this? thanx for any help :)

and im on xp right now.. can i switch between ubuntu and xp without restarting all the time?

---

### Post by funkyali on 2009-03-13
best to look here [https://help.ubuntu.com/community/AspireOne#Install](https://help.ubuntu.com/community/AspireOne#Install)

It would have installed 8.10 on your system. You will need to download and install the wifi drivers which if you follow the guide it should help. I also had the same problem. You may have to do this for your internal mic and I suggest you do the LED blinking as well so you know if wifi activity.

You have to reboot unless you use WINE and run a virtual windows from UBUNTU. you can also run ubuntu from within windows using virtual box.

---

### Post by stchman on 2009-03-13
> **cirabisi2009 said:**
> i have an acer aspire one netbook. 1gb ram, 120gb hard drive, intel atom, windows xp home. i want to down load it. but im not to sure on how all that works. i've read the documentation but.. its not really a guide for dummies and i want to dual boot xp and ubuntu. what am i to do? help is greatfully apreciated!

I have an Aspire One running Intrepid.  Runs pretty darn good.  I have a tutorial to get everything up and running.

[http://www.stchman.com/aspire_one_intrepid.html](http://www.stchman.com/aspire_one_intrepid.html)

---

### Post by cirabisi2009 on 2009-03-13
> **stchman said:**
> I have an Aspire One running Intrepid.  Runs pretty darn good.  I have a tutorial to get everything up and running.

[http://www.stchman.com/aspire_one_intrepid.html](http://www.stchman.com/aspire_one_intrepid.html)

i found your guide but when i type in

sudo apt-get install linux-backports-modules-intrepid-generic

it comes up with a error saying batch could not be found or something along those lines.. and i did all you said. im kinda lost on it at this point.

---

### Post by cdwillis on 2009-03-13
you may have to edit your /etc/apt/sources.list file to allow packages from the backports, I assume that they would specify that in the guide

---

### Post by cirabisi2009 on 2009-03-14
i typed in /etc/apt/sources.list in the terminal and it told me permission denied!

and not only did i type that in. i went ahead and plugged in my ether net cable to my netbook and i still cant even get a connection from that

---

### Post by cirabisi2009 on 2009-03-14
ok so i uninstalled ubuntu and went back to wubi and am putting xubuntu on to see if anything different happens.. if this doesnt work i might try easy peasy or crunchbang. is there a installer like wubi for these?

why doesnt wubi installer for 8.04 work???? im starting to want to give up on ubuntu till stuff gets figured out because i cant

---

### Post by funkyali on 2009-03-14
Hi Cirabisi 

Did you try the guide I sent you?

I'm a linux/ubuntu newbie and I found that guide quiet usefuly and everything works on my aspire one.

If you need help just let me know and drop me a PM.

---

### Post by cirabisi2009 on 2009-03-14
i have had absolutley not luck so far. i tried the guide. but when ever i do what it says. nothin happens and my wired internet isnt working with ubuntu for some reason!?

---

### Post by cirabisi2009 on 2009-03-14
im heading out to get some stuff like more ethernet cables. be bACK IN A FEW so dont think i've given up completely!!!

---

### Post by cdwillis on 2009-03-14
> **cirabisi2009 said:**
> i typed in /etc/apt/sources.list in the terminal and it told me permission denied!

and not only did i type that in. i went ahead and plugged in my ether net cable to my netbook and i still cant even get a connection from that

Go to your menu at the top of the screen and go to System > Administration > Software sources. Click the updates tab and make sure the Unsupported Updates (intrepid-backports) is checked. Now try to follow that guide and it should work.

---

### Post by cirabisi2009 on 2009-03-14
> **cdwillis said:**
> Go to your menu at the top of the screen and go to System > Administration > Software sources. Click the updates tab and make sure the Unsupported Updates (intrepid-backports) is checked. Now try to follow that guide and it should work.

well im reinstalling Ubuntu. i got like 15min. left :-\" so yeahh.... i'll get back to ya on if that works. im on aim if anyone wants to talk im bored as hell


bananas

---

### Post by cirabisi2009 on 2009-03-14
> **cdwillis said:**
> Go to your menu at the top of the screen and go to System > Administration > Software sources. Click the updates tab and make sure the Unsupported Updates (intrepid-backports) is checked. Now try to follow that guide and it should work.

worked like a charm!! im on ubuntu right now but im a little confused as far as the wireless thing. 

[http://www.stchman.com/aspire_one_intrepid.html](http://www.stchman.com/aspire_one_intrepid.html)

this is the guide. and after i do the first step it says bout manually doing something. and i got kinda lost. im a go ahead and do it again and see what comes up

this is the error i get after enter in this command 

"sudo apt-get install linux-backports-modules-intrepid-generic"

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by cirabisi2009 on 2009-03-15
after a few issues with the wireless on aspire one ](*,). i am glad to say its fully up and running!!!!!!!! and i love it\\:D/ lol. thank you all for the help on installing to fixing problems.. it was totally worth not giving up on ubuntu. and plans for the future! i have an old dell 2500 that i plan on converting to full ubuntu :mrgreen: and i am attempting to convert my friends to atleast dual boot xp and ubuntu. :D thanx again

---

### Post by Nero147 on 2009-03-15
Also you could try [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) They have some great scripts for making bootable thumbdrives. I used them for the bootable knoppix drive I use for tech work.

---

