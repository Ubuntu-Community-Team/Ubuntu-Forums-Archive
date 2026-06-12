---
title: "Wireless Problems with Hardy etc.? TRY THIS!!!"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by seantm on 2008-05-20
[B][COLOR="Navy"] Hey everyone -still having trouble getting wireless going in Hardy or other distros? TRY THIS! :) --> [http://wicd.sourceforge.net/download.php ]("http://wicd.sourceforge.net/download.php") 

I've browsed forums for days... And posted... Tried all kinds of command line alchemy just to get a common aeth0 intel network card running on my Lenovo/IBM thinkpad -nothing obscure --no luck Until now! This little utility did the trick -and quick -I 'didn't even have to compile it! [/COLOR][/B]

[COLOR="Navy"]**Below is the original post wherein I learned about it --big Kudos to Gais Kay!**---[/COLOR]

> **Gias Kay said:**
> I am a new user to Ubuntu who have just installed 8.04 (Hardy Heron) two days ago. The installation and setup process were all smooth except for one yet major part - the wireless. Since I am using a notebook (HP Compaq nc6000), without wireless means losing the ability to get online for most of the time which would effectively render the notebook half-dead, so I was anxious to solve the problem.

I went onto several forums and saw various suggestions, ranging from asking me to download some third party driver for the wireless card which needed to be further "built up" from the source code on my end, to some crazy command line instructions I can't really tell what the freak that was though the answerer kept guaranteeing that should work. But these were all too intimidating for a Linux newbie like me and I couldn't really have the determination to try out those expert-looking "problem-neutralizing attempts" (didn't even have the confidence to say "yep that looks like a working solution for me").

Eventually, I stumbled upon my savior (on this exact forum) - Wicd:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

According to the explanation I found, the current version of the default network manager in Ubuntu is just *incapable* when it comes to **encrypted wireless connections**, and Wicd, coming with a full-fledged GUI, is a better network managing program that can work correctly with the wireless.

I saw the screenshots in the page and the claim seemed to be reliable enough, and there was no horribly long codes and so on, just like how we do things in Windows - install it, set it, problem solved - so I decided to give it a shot.

The installation is quite simple, just follow the instructions inside the "Download" page, then do some more post-setup inside the "FAQ" page; you may or may not have to reboot to make the new problem work, but for me a reboot was necessary. Once you see the Wicd icon on the tray, right click on it and you'll be able to get into the settings. Now just turn on your wireless, wait a few seconds then reload, you can choose from a list of detected networks and the rest is intuitive. Using Wicd, I can even connect to the encrypted WEP network of my home wireless without the password, so I guess it's really the time for me to switch to WPA2.

Unfortunately this handy software seems to be not known by many users who also have problems in trying to get their encrypted wireless connections to work inside the default network manager, so I am writing this from a newbie perspective as an attempt to offer some experience talk for others who are new to Ubuntu as well and have been frustrated over the wireless issue. I also sincerely hope that Wicd can get some deserved attentions from Ubuntu developers and include it into the software repository if not making it the new network managing default :mrgreen:

---

### Post by Fernanddo Saenz on 2008-05-20
I had the same problems, and found the same solution. I use a Dell Vostro 1000 (Hardy 8.04, dual-boot with XP). with a Dell 1395 wireless card, which uses  **Broadcom BCM4312** (rev.01) chips. This is the weird chip that is reported by lspci as "USB Broadcom BCM4310", and by lspci -n as "[14e4-4315]". Apparently it is not supported yet by the new b43 drivers in Hardy, but it worked well with ndiswrapper. I am quite thankful to the various thread authors who have explained this in great detail. 

For about 3 days all was fine, but then connections started to be lost randomly. Sometimes, even just after boot my WiFi network was not seen at all, no matter how close to the router. Needless to say, wireless was always OK in Windows. Sometimes I would regain connectivity doing a manual disable/enable with ifconfig, or unloading/reloading ndiswrapper, etc. After lots of tinkering around I convinced myself that the driver and ndiswrapper themselves work perfectly, there is nothing wrong with them. Most system logs didn´t show anything wrong, until I looked at /var/log/daemon.log. The strange bahavior is basically this:

1) Network-manager does all kinds of stuff trying to activate my wired Ethernet interface, eth0 (which has no cable plugged-in, and obviously no link!). N-mgr says it found a "link" on it, DHCP tries to obtain an IP address (4 trials), obviously gets none, it resigns, and "avahi-daemon" decides to grant it a bogus Ip in 169.254.X.X. By now, around 25 seconds have elapsed.

2) Finally, N-mgr somehow "discovers" the wlan0 interface, the same procedure starts over, apparently dhcp never receives an IP address (DHCPOFFER), gives up, and the avahi-daemon gives it a bogus IP again. N-mgr shows all addresses as "0.0.0.0". At this point nothing helps: disabling roaming mode and trying to connect manually, using dhcpd manually, etc. The router´s (D-Link DIR-300) log shows absolutely no trace of having received a DHCPREQUEST from the laptop.

(I can post excerpts from daemon.log if anyone is interested). I am not sure if the problem lies in Network-Manager or in avahi, but it is surely NOT the driver or ndiswrapper. Avahi seems to me a pretty useless service; but when I disabled its loading at boot time (using BUM) I lost connectivity completely. I read about Wicd in some posts, and after installation all the troubles disappeared! Now I have solid wireless connections all the time.

I have not checked my daemon.log again, or attempted to disable Avahi again now that everything works. The user interface of Wicd is rather crude and there is little documentation for it, but in my case it solved all the wireless frustration. 

I don´t know if people using non-Broadcom Wi-Fi chipsets are getting the same kind of behavior with Avahi and/or Network Manager.

---

### Post by Strfie89 on 2008-05-22
Erm.... What if wireless is the only internet option I have (no ethernet)? (There's no actual DOWNLOAD link on the website, so I can't get the package through another computer.)

---

### Post by sondosia on 2008-05-22
You can download a package here: [https://sourceforge.net/project/showfiles.php?group_id=194573](https://sourceforge.net/project/showfiles.php?group_id=194573)

I need help - I installed Wicd and amended my /etc/network/interfaces file as the wicd website said to, but it still refuses to connect to my home wireless network. Could the Windows drivers package I installed or something else I have be interfering?

---

### Post by santhony on 2008-05-30
Just installed... So far sooo goood....  I'll write back in a few days to let you know how stable my wireless is... Wasn't very with the default manager.. always had to restart my network to get it to work....

---

### Post by seantm on 2008-05-30
Try removing it (go to applications add/remove or sudo remove etc.)) and then do a fresh reinstall. ---No your windows drivers are on separate partition 8.04 let alone wicd ,doesn't even see them. If you have the means, perhaps try the wired connection first before the wireless. See if it can find a gateway. Open the wicd interface and see if  detects the wireless signal then try connecting and grabbing an IP.

---

### Post by seantm on 2008-05-30
you'll need to get the utility from a friend with net' access and download it onto on a usb drive or something similar then install via this...You must have net' access somewhere otherwise you could not have posted this question right? :)

---

### Post by seantm on 2008-05-30
cool --hope it works as well for you as it has for me let us know....

---

