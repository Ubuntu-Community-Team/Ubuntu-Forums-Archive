---
title: "Yet another wireless questen"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by Draq on 2007-02-17
Hey to this forum!

Installed the newest Kubuntu 6.10 Its fantastic so far.. But as a new who want to learn the planet linux it is very importent to have the net online.

I have a Linksys WMP54G v4.5 (RT61) wireless PCI card in my machine. I have a access point (Converted router) with a wire to a combi router/modem for the web.
My rounter is secured with WPA TKIP and a key!

My wireless is seen by Kbuntu under system/network. There is a 0lan and 0master (hope I got these right this is Duelboot windows).

Q1: Anyone her on the forum who has the same wireless netcard there can tell me if Kubuntu 6.10 can work with this card. I read alot of people who has problem with it in older linux systems.

Q2: If i open the wireless manager under internet (the last one down the list) i can see my connection under 0lan. Its all 5 stars and the name is ESSID is right. It tells me WEP. 
I know WEP from my access point but I have WPE. hmmm. 

OK i setup access point to WEP and now the system cant find anything. Back to WPE and I can see it again!! I do a no secured accesspoint and its emtry again. back to WPE and its there!! This is very weird.. 

How the ..... do i do?

Q3: This is out of the line... hd0.. what is that? It was where Grub the bootloader was installed!! would like to know seens this fellow can destroy the XP setup.

Last note.. im a noob in linux.. I tried 4 times in 3 years to jump to linux. Everytime i drowning in terminal stuff with errors missing stuff and no understanding!
I understand some.. But that doesnt mean i can praktic it.. If you give my anything to work with you have to be gently!

Thx for all and hope this will be the time!

Simon!

---

### Post by gradedcheese on 2007-02-17
Hi.  Yeah, I think that card works.  I have a working v4 here, hopefully v4.5 isn't a different chipset.  To use WPA, you should probably switch to Network Manager.  There's a guide here for setting it up.  Otherwise, the WPA guide is this: [http://www.ubuntuforums.org/showthread.php?t=318539](http://www.ubuntuforums.org/showthread.php?t=318539) but he uses some custom settings that you probably don't need (he sets up a static IP, for example)

hd0 is the first partition on the first IDE disk, generally your IDE master disk.

---

### Post by Draq on 2007-02-18
thx for the reply but im getting nowhere.

For now i dont understand to much terminal stuff with to less explanation of the commands.

Im ending up in a error or no go ever time.

This guide is the best explaning things for me.. But  he take it for granted that i can download packede.. i have no internet.. 
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu#EasySteps](https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu#EasySteps)

So now im stucked with this file and no clue what to do.. 
knetworkmanager-0.1.tar.bz2 is the name of the file.. 

How do I installe such file under kubuntu.

Simon

---

### Post by gradedcheese on 2007-02-18
Ok.  "knetworkmanager-0.1.tar.bz2" is an archive (like a .zip in Windows), it has been 'tarred' and then 'bzipped'.  From the GUI, you can just right-click it and choose 'Extract' (or something similar).  This works in Gnome, but I do not ever use KDE (Kubuntu) so you're on your own there.  Once it's extracted, you can look inside and see what it is (probably the source code to knetworkmanager, which you have to build).

If you have no network access, I suggest that you use the Ubuntu or Kubuntu CD instead to grab your packages.  I believe these are actually on the CD... in Gnome, you put the CD in and then you can add it via Synaptic (repositories option).  In KDE... there's something else?

Once that's done, try the usual "sudo apt-get install network-manager" to install it.  You can also use the GUI tools instead (like Synaptic or whatever KDE comes with).

Hopefully someone with KDE/Kubuntu knowledge can step in and help you here before I make you more confused :(

---

