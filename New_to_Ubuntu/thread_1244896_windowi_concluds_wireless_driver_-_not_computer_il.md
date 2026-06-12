---
title: "windowi concluds wireless driver - not computer illiterate but ubuntu failing me..."
date: 2009-08-19
forum: New to Ubuntu
---

### Post by willhall on 2009-08-19
ok so i have booted ubuntu from a usb stick on my toshiba netbook. so far so good, i like orange.

no wireless.

the help pages instruct me to look at the system notification tray and the network manager. sounds simple except that, since i have never used ubuntu, i have no idea where these are. i can't even seem to get to a desktop. so i search for those terms in the help manual but get no help.

finally i conclude there is no system network manager icon notification tray because the wireless is not working, i cannot enable it, so it didn't show up. ah.

ok so under troubleshooting i have to terminal sudo lshw or somethign or other to show what devices. OK so there it is, it recognizes the hardware but says something about not being usable because no driver.

simple enough.

now i follow the link to the windows wireless driver. the ntgsft package link doesn't work, so i have to figure out how to install a package manually. i have no idea what a package is but i somehow get nsfgt package installed. lo and behold, on the administration or preferences or control panel now, Sure Enough, I have the windows driverless wireless thingy.

so now i open that and it says to navigate to my .inf file. Well wonderful, i have looked around when I was in XP and seen that the driver for the wireless card is in somethign called Atheros or something which i guess is the manufacturer. Ok so back in Ubuntu and the wireless driver windowless installer.

I click the little browse icon to navigate to my .inf file, which by the way does not have an .inf extension in windows but it is the only driver associated with the wireless network card i could find.

And here my real troubles begin.

I have no idea in ubuntu how to find a folder that i found in windows. When I go to "File System" i see a bunch of supergeek uber ninja code folders line lib and usr. where is my Documents and Settings where is Windows where is Atheros?

ah so Search, that should be easy to find right?

well the only Search I can find is under Help search topics. I search for search but that search doesn't give me search.

Can someone please tell me how to find the Atheros folder in Ubuntu so i can navigate my windows driverless wireless wrapper ntfgt package software in the administration panel to where the inf file for Atheros is so I can get Ubuntu onto the internet (which just a heads up for any usability people out there, is a dealbreaker if your os doesn't know how to get onto a wireless network without several hours of frustration and a resort to the forums, which of course I have to reboot into windows to surf to).

thanks, but losing faith
- will hall, usually a mac user.

---

### Post by SoftwareExplorer on 2009-08-20
Go to the places menu at the top of your screen. On it there should be items that say things like XX GB media. Open each of them until you find your windows partition. Then it will be like you are in drive C: in windows. Also, if you happen to find yourself in the ubuntu filesystem, go to media and then there will be folders named disk, disk-1 etc and if you have gone to your windows partition at least once since you booted ubuntu, drive c will be in one of those folders. If you need more help, just ask, it sounds like you figured out quite a lot by yourself, so kudos to you!

---

### Post by SoftwareExplorer on 2009-08-20
By the way, welcome to ubuntu forums. :)

---

