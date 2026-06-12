---
title: "Yet another newbie joins the force."
date: 2009-09-09
forum: New to Ubuntu
---

### Post by Zlash on 2009-09-09
Hello guys.

A friend of mine showed me ubuntu, completly random. 
I must say, i felt eager to try it just asap. I got home, and installed it over vista (having 2 OSes.) 
By now im almost certain im going to wipe my harddisk and go ubuntu on this laptop. i just have a few issues n stuff id like to get some professional aspects on.

Can Ubuntu run:
Maple 12-13
Mathcad 14
Any video/audio format
Torrent downloader
Windows Office (or turn files into Windows officer, for delivering essays and stuff like that, school related)

I got an Aspire one 150Bb which has 1gig of ram, a graphics card which runs compizz and aero effetcs perfecly without any lag and a proccessor which runs at 10-20% in vista ultimate 32bit (desktop view).

My main reasons for going over to ubuntu:
-Faster, less resourced. Vista takes 700mb/1gig just on the desktop
-Easier, no lame restrictions like mac and vista (have been thinking about going to mac for some time)
-Better, looks just fantastic if you ask me, and the deskspace option is just what i need for school related stuff. Atleast working with both a maple spreadsheet, FF wikipedia and word can be stressfull with a touchpad :)


I am completly new to ubuntu, im a computer interessted person but have been a solid windows user since the age of 7 (13 years).

So this is kinda a information/want help/issue topic. heres my current issues with the ubuntu i got running.

ubuntu doesnt detect the internet on my school, wireless. as soon as i boot vista, no probs what so ever.

Either than that im having some trouble figuring out all the installation, themeing, customizing and in general random shizzle in ubuntu, its a gr8 OS, so far i love the 2 bar system and the eye candy (about a year ago i had so many diffrent eyecandy features on my xp installed aspire one, i literraly broke it due to too much crap.

Hope to get some help as im eager to get started with this asap!
theoreticly i cant start before i get office on it, since its my school pc, and unless ubuntu can run cod4, wow, and upcomming games, im afraid il stay vista on my desktop home pc.

//Zlash aKa Tommy

---

### Post by Penguin Guy on 2009-09-09
Maple - [COLOR="Red"]No[/COLOR]
Mathcad - [COLOR="Red"]No[/COLOR]
Any video/audio format - [COLOR="DarkOrange"]Yes, but not very good at running flash (.swf)[/COLOR]
Torrent downloader - [COLOR="Green"]Yes[/COLOR]
Windows Office - [COLOR="Green"]No, but OpenOffice works exactly the same and can work with Windows files[/COLOR]

Ubuntu can not [(easily)]("http://www.winehq.org/") run Windows programs, but there are lots of Linux alternatives.

P.S. You might also find the [Psychocat Ubuntu guide]("http://www.psychocats.net/ubuntu/") useful.

---

### Post by nothingspecial on 2009-09-09
Post your wireless card.

Open a terminal and post the output of ```
sudo lshw -C network
```

Can you detect other wireless networks. Is it just your schools?

---

### Post by Zlash on 2009-09-09
Mathcad and maple both have linux support on their homepage, Is there any reason why ubuntu cant run these?

Im not going to use this laptop for tons of shizzle. basicly its going to be a tool for studying while also being a fun machine to look at and a very useful media center (download a movie, watch it on the bus, connect a cable to my 22" inc screen (8 sux) for late night views and such.

im ok with not being able to use windows programs, in fact the only windows programs i used to fool around with on my vista, are programs to apply the "ubuntu" or "mac os x" functions to windows, altho they run like crap.

so as mentioned id like to know that when i download a movie over btjunkie.org i wont have issues with sound/picture. for windows i only had to install Klite package off [www.freecodecs.com](www.freecodecs.com) and badabim i wouldnt be having these issues anymore.

i also have an ipod i constantly update music on, hows itunes with ubuntu? i guess its the same? :)

---

### Post by NightwishFan on 2009-09-09
Welcome to Ubuntu. I shall offer you up some good beginner resources.

Free PDF Book:
[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)
Psychocats Help Page
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
Official Community Help (use the search bar)
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

As for your other requests.

Maple and Mathcad? No idea. If they are Windows programs you can try Wine. [http://www.winehq.org/](http://www.winehq.org/)

Audio/Video formats? Yes, using VLC player, or just Gstreamer plugins. You can supplement encrypted DVD support by using Medibuntu, which is a source for media packages. Flash does work quite well at times.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Torrent downloader is included by default. Transmission bittorrent client. Others such as Azureus are available.

MS Office may run using the Wine I mentioned. A free software office client that is compatible with MS Office files is already installed by default. (Openoffice.org)

You can download software for free on Ubuntu by going to add/remove in the applications menu, and setting the dropdown menu to "Show All Available Software". The search for what you need. Note, MS Office is not Linux software, so common Windows programs will not show up in the list. To install just check what you want and hit apply. All the configuration will be handled by the program.

Please note that Ubuntu is not a "free Windows". It is a very different system with different aims and roots. It is sufficient very almost every computing need, even running of many "Windows programs", but I would stress to learn to rely on Linux native software to get things done.

As for hardware, most will work, but you will find some rare hardware does not. If that is the case, you should either file a bug with a related project, or tell the hardware manufacturers to create Linux drivers. There are enough of us out there that we deserve support as well.

Any individual issues you should create a new thread in the help forums for each one, such as your network issue.

Enjoy and please feel free to ask any questions. Have fun!

---

### Post by Zlash on 2009-09-09
> **nothingspecial said:**
> Post your wireless card.

Open a terminal and post the output of ```
sudo lshw -C network
```Can you detect other wireless networks. Is it just your schools?

This was the useful information i could get amonst the long list of spam. not sure if its the stuff you wanted but here goes. also its only on my school. Once im home, ubuntu automaticly connects to my wireless, just like on vista. 
> 
 *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01

---

### Post by Excedio on 2009-09-09
Welcome! :-)

Maple 12:
[http://ubuntuforums.org/showthread.php?t=907702](http://ubuntuforums.org/showthread.php?t=907702)
[http://ubuntuforums.org/showthread.php?t=918151](http://ubuntuforums.org/showthread.php?t=918151) (Use this if you get a Blank Startup screen)

Maple 13 I cannot find for you.

-------------------------------------------------------------

Mathcad 14:
Seems doable in Wine. But may have a bug. Worth a shot though.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10538](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10538)

-------------------------------------------------------------

Any video/audio format:
Yes, more than windows can natively. May need to download the proper codecs though, but very doable.

OP already answered the others.

---

### Post by Zlash on 2009-09-09
> **NightwishFan said:**
> Welcome to Ubuntu. I shall offer you up some good beginner resources.


Please note that Ubuntu is not a "free Windows". 

Thanks! appreciate it alot! 

and as for your comment. <3.

I want to get away from windows, but the fact is, windows got the main source to all software used by non teq places such as a school, Our school does offer software for macs seeing alot of ppl are going for the "macbook study" setup. Ubuntu, ive only seen one dude have it.

Would it be possible to run a virtual machine on ubuntu, running vista/xp just for the short amount of time so you can have these math based software running?

is there any guides on how wine works? any special needs for it or does it run all windows based programs? if so i should be able to run mathcad and maple via that. as mentioned both sites sais that their program support linux. this means ubuntu?

for those who doesnt know what mathcad, maple is: math software, pretty much for soulving difficult mathimatical equations such as integrals and differentials. :)

---

### Post by Penguin Guy on 2009-09-09
> **Zlash said:**
> Mathcad and maple both have linux support on their homepage, Is there any reason why ubuntu cant run these?
Could you post a link - I didn't see any such page. Even if it works with Linux you will probably have to buy the program again and it won't look as jazzy as the rest of Linux.

> **Zlash said:**
> i also have an ipod i constantly update music on, hows itunes with ubuntu? i guess its the same? :)
No iTunes for Ubuntu, however iPod support is (apparently) very good.

---

### Post by Excedio on 2009-09-09
> **Zlash said:**
> *snip* Would it be possible to run a virtual machine on ubuntu, running vista/xp just for the short amount of time so you can have these math based software running?*snip

[http://www.virtualbox.org](http://www.virtualbox.org)

---

### Post by NightwishFan on 2009-09-09
Wine is in the Ubuntu repositories. It creates a "virtual windows" where you install Windows programs and they run using Linux resources. So basically, if your printer does not work in Linux it will not work in Wine. However, WINE (Wine Is Not an Emulator) does not virtualize in the same sense as commonly used. It actually can achieve equal or even greater performance than the programs being used on Windows. Please note you MUST install the programs in Ubuntu on Wine, and not link them from an existing Windows installation. It is possibly but can cause problems.

Wine is easier than you think. Just install it from add/remove, and then double click on a Win23 .exe file. I will link you some wine resources.

Wine App Database: Use the search to see how well your program works. [http://appdb.winehq.org/](http://appdb.winehq.org/)
Wine FAQ: [http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)
Wine Documentation: [http://www.winehq.org/documentation](http://www.winehq.org/documentation)
Ubuntu Wine Guide: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

For Gaming Links from Artificial Intellegence profile

Ubuntu Gamer Arena: [http://gaming.gwos.org/doku.php](http://gaming.gwos.org/doku.php)
Ubuntu Game List: [http://ubuntugamelist.org/](http://ubuntugamelist.org/)
Ubuntu 64-bit Gaming Guide: [http://gwos.org/doku.php/guides:start](http://gwos.org/doku.php/guides:start)

---

### Post by Excedio on 2009-09-09
> **Zlash said:**
> *snip*  i also have an ipod i constantly update music on, hows itunes with ubuntu? i guess its the same? :)

[http://getsongbird.com](http://getsongbird.com)

---

### Post by Zlash on 2009-09-10
I'm still having WiFi problems, any ideas(lshw output on page 1)?

---

### Post by nothingspecial on 2009-09-10
In your menu goto system > administration > hardware drivers and try enabling the alternative madwifi driver in there.

---

### Post by Zlash on 2009-09-10
> **nothingspecial said:**
> In your menu goto system > administration > hardware drivers and try enabling the alternative madwifi driver in there.

doesnt work.

I reinstalled my laptop with Ubuntu, completly removing windows vista and clearing my harddisk 100%. wifi connection seems to be fine, ive been online on the schools wifi for about 90min now, no troubles at all, so far seems like ubuntu reqonizes the wifi alot easier than vista used to do. il post on the wifi section if new problems/same problem comes up again.

Thanks alot for the help tho :)

---

