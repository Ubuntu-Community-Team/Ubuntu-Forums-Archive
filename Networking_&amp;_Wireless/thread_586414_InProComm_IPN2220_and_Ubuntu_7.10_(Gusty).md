---
title: "InProComm IPN2220 and Ubuntu 7.10 (Gusty)"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by k3lt01 on 2007-10-22
Ok here it is, InProComm IPN2220 and Gutsy are not working well together. I could get the wifi card and Feisty to live together but not Gutsy. I have been through the various How To's presented in this forum and even the ndiswrapper install guide but nothing makes it work properly.

I can get the card recognised, even have it see my Windows desktop, but it wont read files from the Windows machine and when I try it stalls the linux laptop. It DOES NOT seem to recognise my network though. and only works in roaming mode. The whole situation is very confusing as it is not behaving the same way in Gutsy as it did in Feisty. It is not predictable at all.

Things I have tried apart from what is listed above.

1. Tried logging onto another (ficticious) network and then going back to the real network, this worked in Feisty.
2. Installed Wicd.
3. Clean re-instalation of Gutsy, back to square one.

So my big question is has anyone successfully installed Gutsy and got the InProComm IPN2220 working properly? If yes, How did you do it?

I am seriously considering reverting back to Feisty if I can't get it working soon.

---

### Post by indifference on 2007-10-22
Hello,

It appears that the new kernel doesn't like the ipn2220...

I've managed it to work, by installing the kernel from feisty.
The strange part is, if i modprob ndiswrapper in the kernel from feisty, the wireless card works fine. Then if i reboot ( not shutdown ) and load ubuntu with the new kernel and modprob ndiswrapper the wireless card will function as well, until the the next shutdown...

Can someone explain this? :guitar:

It would be great to have a patchl, so that the card works with the new kernel...

---

### Post by k3lt01 on 2007-10-22
Thanks for your reply, now this leaves me with 2 questions.

1. How do I install the Feisty Kernel in Gutsy?
2. Does anyone know if they will code a patch?

---

### Post by k3lt01 on 2007-10-24
Just thought I'd resurrect this post.

Does anyone have any ideas yet?

---

### Post by criatura555 on 2007-10-30
I just want to say that I'm starting with Linux and Ubuntu and my laptop is almost the same as yours: ACER Extensa 2300 Celeron 1.5 - 512mb Ram - IPN 2220 - Ubuntu 7.10.
I hope some one can find a solution for us.

Wireless is a great weak point with linux, I test a lot of distros and there are a constant: problems with wireless.

---

### Post by k3lt01 on 2007-11-01
I apologise for not replying earlier. I ended up going back to Feisty 7.04 as I knew my wireless worked in that. Within 5 minutes of restarting after the Feisty re-install I was on the net again with my Acer. I to hope someone finds a solution and posts it so we can all see it but until then I'm sticking with Feisty and updating packages with Developer software (i.e. I updated OpenOffice from Feisty's 2.2 to OO2.3 and I am nutting through updating Gnome from Feisty's 2.18 to GNOME's 2.20. Neither of these builds are supported in Feisty but I am updating anyway, there is other software I have updated like FireFox and ThunderBird so you get the idea).

As it is I am :guitar:ing along quite well now. Long Live Feisty :lolflag:

---

### Post by michael003 on 2007-11-23
I had this same problem. I describe how I solved it in this post: [http://ubuntuforums.org/showpost.php?p=3823299&postcount=4](http://ubuntuforums.org/showpost.php?p=3823299&postcount=4).

---

### Post by k3lt01 on 2007-11-23
> **michael003 said:**
> I had this same problem. I describe how I solved it in this post: [http://ubuntuforums.org/showpost.php?p=3823299&postcount=4](http://ubuntuforums.org/showpost.php?p=3823299&postcount=4). Not trying to bag you out here but I am not sure you really solved it all that well, you even admit to it being unreliable.
> **michael003 said:**
> We eventually go it working by installing the kernel from Feisty (version 2.6.20-16) and using the drivers for the Linksys WPC54Gv4. It didn't work very reliably however -- the connection kept freezing and had to be restarted. My friend eventually gave up on Ubuntu because of this.Thanks anyway

---

### Post by tbfr on 2007-12-01
I finally got my IPN2220 working in Gutsy by using the driver attached to this post: [http://ubuntuforums.org/showpost.php?p=3669302&postcount=14]("http://ubuntuforums.org/showpost.php?p=3669302&postcount=14")

The full (non-english) thread is located at [http://ubuntuforums.org/showthread.php?p=3669302]("http://ubuntuforums.org/showthread.php?p=3669302") 

Hope this works for you guys too, here is the relevant output of lspci on my MSI S270:
02:09.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)

With every other driver I tried iwconfig showed a wlan0 entry but 'iwlist wlan0 scanning' never found a network and I also couldn't connect to any network. Good luck.

---

### Post by k3lt01 on 2007-12-01
Thanks mate, I will try it later today and report back what I find.

I really wish I could read, write and speak other languages. There must be so much info like this on the other language forums we cannot access because we can't read it :(

---

### Post by k3lt01 on 2007-12-23
Sorry about not replying earlier, been extremely busy with work but now I am on holidays I have plenty of time :)

I have got Gutsy working with my network card using the above suggested driver and setuo help from Ubuntu Help.

There are other issues though and I have listed them in a new thread which you will find here [http://ubuntuforums.org/showthread.php?p=4000727#post4000727](http://ubuntuforums.org/showthread.php?p=4000727#post4000727)

---

### Post by hayim on 2007-12-28
Woo, i cant believe other people actually have my laptop model.... i thought maybe it was like an australian-only model line that ran for 2 months or something... then disappeared! tho seems non english speaking countries got it too.

Meanwhile, I got my built in wireless working in Gutsy - HOWEVER, it *is* true that sometimes after a hard reset (coz the the computer liked to crash) I could not get the card to work for anything. A couple of reboots later, or a reboot back into windows, and the card was up and running again. go figure.

nm-applet couldnt seem to get the card to fire up tho, ie the radio wouldnt turn on. I had to actually set the essid in iwconfig for the card to fire up. So wrote a script to run iwconfig and dhclient at boot up, and all was good (nm-applet is useless).

I did nothing else special tho: ndiswrapper the neti2220.inf from my original windows install, modprobe ndiswrapper and thats all. hope this helps..

But just coz we have the same hardware, dont mean we have the same results!

Now if i could only get my sound to work..... ive got it working in Puppy and Mandriva 2008.. so i think im taking a break from the Ubuntu until Hardy comes out in april.

---

### Post by k3lt01 on 2007-12-28
Hi Hayim, I think it is an australian only model and there is no reference at all on Acer Australia's website either. My card is working beautifully now and I have no probs at all with nm-app, having said that I have had the problems you describe on previous occasions.

I don't know how to help with your sound issues because mine has worked perfectly from day 1 with everything bar the network. All I can suggest is back up your home drive data delete everything else, configurations etc, and do a totally new clean install reformatting everything. I did this and found all my probs went away as the old configurations left in the /home drive really can play havoc with a new install if they are part of the initial problem.

---

### Post by hayim on 2007-12-29
Hmm... now that you mention it, I did install Gutsy *fresh* but not *clean* - ie, i left my /home partition as is and reformatted /. So maybe that would help.

But also, im kinda weary of ALSA, the last few kernel & ALSA upgrades have seemed to be at war with eachother. Im putting my faith in PulseAudio. 

But as you say, if we have basically the same Extensa 2300 chasis and your sound works, it maybe was an issue with old config files. 

Im liking Mandriva 2008 for now, though the package manager is a bit narcy.

---

