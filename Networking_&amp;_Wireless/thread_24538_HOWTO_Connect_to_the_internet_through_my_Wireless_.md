---
title: "HOWTO: Connect to the internet through my Wireless LAN?"
date: 2005-04-07
forum: Networking &amp; Wireless
---

### Post by samfrancis1 on 2005-04-07
O.k, after install i get the problem i need to access my wireless network but it is not installing as its designed for Windows XP!

I heard that a program called Wine would let me access 95% of my windows programs so i conected my comp through the network cable and i couldnt conect to the internet to get it!

I also tried to get Wine to disc but no luck as you download it throug some special thing.

Any advise of how to conect to the network?

Thanks, Sam

P.S: The other computers in my network are running Windows XP or Windows ME.

Thanks again :grin: :grin:

---

### Post by samfrancis1 on 2005-04-07
[QUOTE=samfrancis1]O.k, after install i get the problem i need to access my wireless network but it is not installing as its designed for Windows XP!

I heard that a program called Wine would let me access 95% of my windows programs so i conected my comp through the network cable and i couldnt conect to the internet to get it!

I also tried to get Wine to disc but no luck as you download it throug some special thing.

Any advise of how to conect to the network?

Thanks, Sam

P.S: The other computers in my network are running Windows XP or Windows ME.

Thanks again :grin: :grin:[/QUOTE]
 Common ppl, i wanna send my new UbuntuLinux to the test!!!!!

Please help me!

Thanks!

---

### Post by WillCooke on 2005-04-07
[QUOTE=samfrancis1]O.k, after install i get the problem i need to access my wireless network but it is not installing as its designed for Windows XP![/QUOTE]


What wireless card are you using?  Does it have drivers for linux (search google),
if it doesnt have a look at NDIS Wrapper (search these forums for a how to).

---

### Post by samfrancis1 on 2005-04-07
[QUOTE=WillCooke]What wireless card are you using?  Does it have drivers for linux (search google),
if it doesnt have a look at NDIS Wrapper (search these forums for a how to).[/QUOTE]
 Well, i am using an INEXQ rooter but i dont no the PCI card allthough its compatable with my rooter.

I try to install the software to let me on the web but it dont install or conect.

---

### Post by samfrancis1 on 2005-04-07
[QUOTE=samfrancis1]Well, i am using an INEXQ rooter but i dont no the PCI card allthough its compatable with my rooter.

I try to install the software to let me on the web but it dont install or conect.[/QUOTE]
 dam! im sooo desperate to get my computer on the internet!!!!!

HELP ME PLZ!!!!!

---

### Post by Technoviking on 2005-04-07
1. Don't beg for help. People will help you when they get the chance.

2. This is the wrong forum area to post a question. This forum is only for FAQ and How-tos (I.e. Guides or instructions) for Hoary and not for questions.

3. You not given enough info for people to help.
- What wireless card do you have?
- Does your Wireless Acess Point have WEP or 802.1x encryption running.
- Have you "Your wireless card and linux" on Google?
- Have you searched these forums for your wireless card?

Mike

---

### Post by samfrancis1 on 2005-04-07
[QUOTE=Mike Basinger]1. Don't beg for help. People will help you when they get the chance.

2. This is the wrong forum area to post a question. This forum is only for FAQ and How-tos (I.e. Guides or instructions) for Hoary and not for questions.

3. You not given enough info for people to help.
- What wireless card do you have?
- Does your Wireless Acess Point have WEP or 802.1x encryption running.
- Have you "Your wireless card and linux" on Google?
- Have you searched these forums for your wireless card?

Mike[/QUOTE]
 i have a InexQ CR054g wireless card
i use 802.11g
i have searched that and its seems to be compatable
not yet

---

### Post by Technoviking on 2005-04-07
According to google. ndiswrapper should work with this card. 
[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

Also these drivers may run native under linux [http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page)

Mike

---

### Post by samfrancis1 on 2005-04-07
[QUOTE=Mike Basinger]According to google. ndiswrapper should work with this card. 
[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

Also these drivers may run native under linux [http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page)

Mike[/QUOTE]
 My drive is compatable but the software to install it doesnt install!

Thats the only prob.

Sam

---

### Post by samfrancis1 on 2005-04-07
[QUOTE=samfrancis1]My drive is compatable but the software to install it doesnt install!

Thats the only prob.

Sam[/QUOTE]
 Common ppl!!!!! ive gotta go soon and wanna configure my comp!!!!!

---

### Post by CrashTECH on 2005-04-07
[QUOTE=samfrancis1]Common ppl!!!!! ive gotta go soon and wanna configure my comp!!!!![/QUOTE]
 Stop being a jerk... seriously... you are making all newbs to linux (and ubuntu) look bad.... (and I for one don't want to admit to being a newb if it makes me be on the same level with you...) And this is also why nobody responds to your posts...

You need to install NDIS Wrapper (it does work... there are MANY tutorials/how-tos about how to use it in these forums alone, let alone out on the web. I found several within 15 minutes of searching) You probably can't compile it becuase you dont have GCC installed (for whatever reason I did not get an option to pick the packages, and had to install it later)... so you need to synaptic to get it). Seriously... search the forum for NDIS Wrapper, and your wireless card (you even said you haven't done that yet).

I spent 2.5 hours lastnight geting NDIS Wrapper installed and getting my wireless driver installed, only to not have it work, but you don't see me begging/whining...

The problem is Linux is not always 'plug and play' like windows is... so you have to read a little bit. You wont get an answer right away not even part of the time.

---

### Post by dataw0lf on 2005-04-07
The behavior that I deleted in this post was unacceptable.  Don't let it happen again.  Thanks, Mike, for bringing this to the mods' attention.

---

### Post by samfrancis1 on 2005-04-07
[QUOTE=dataw0lf]The behavior that I deleted in this post was unacceptable.  Don't let it happen again.  Thanks, Mike, for bringing this to the mods' attention.[/QUOTE]
 thanks as i didnt notice this forum here.

Thanks, Sam

PS if you can help me reply to this thread!

---

### Post by jdodson on 2005-04-07
[QUOTE=samfrancis1]thanks as i didnt notice this forum here.

Thanks, Sam

PS if you can help me reply to this thread![/QUOTE]

hey sam, can you turn the font down on you signature?  its a bit loud and obnoxious.

we all are quite aware you need networking help.

simply posting over and over in caps and bold large text does not sway people to help you faster.

---

### Post by chz on 2005-04-08
with a wireless card you need to set up your networking to point to your router.

Find "networking"...(i dont recall the menus to hit from the gnome menu, since my desktop looks completely different from the base install now, it maybe in System tools or something to that effect). then click on the device of your wireless card. One install i did for a friend i noticed that it didnt add the card in the networking configs, so you have to add it manually, but don't worry its not hard. Just click add then Wireless card...and itll find the card automatically for you. after that you should now see it in your list. click on it, then hit properties, hit activate when computer starts checkbox if you want it or not. then enter your routers name...you can find this easily in Winblows since you seem to have a few. I don't remember where to look for it since i havent used windoze in a few years now, but its somewhere in the control panel...sometimes you see it in that lil annoying balloon near the control panel saying Connected to "YourRouterName". Enter that name in and it must be entered EXACTLY the same way...caps and everything. If you have a WEP key, enter that as well. Click ok until the networking box is completely gone...after that you should be connected...
a good way to see if your connected is to install the Wireless Applet...just right click on a taskbar and Add to the Panel the wireless app. You should then see a monitor of how well your connection is to your router. that way you dont have to click on firefox everytime to check if its working...or typing ifconfig everytime to check if your IP address has been updated althought sometimes it helps.

---

### Post by mehaga on 2005-04-09
I just installed Ubuntu this morning. I am using my rtl8180 based card succesfully on SuSE 9.2. I wanted to install it on Ubuntu, but I don't know where to begin. My questions are:

- **How do I install ndiswrapper?** (the howto link to this topic is broken). I  
  installed it  on SuSE, but I don't know if it is any different here)

- In SuSE's YaST, I had to add new network card, tell it it should use ndiswrapper...
   **Where do I add a new NIC in Ubuntu?**

- **Will I be able to use non-debian-based S/W like Aegis client on Ubuntu?**

I am sorry if any of my questions irritates you :)

---

### Post by hyde on 2005-04-09
I'm also having mission impossible with my wireless pcmcia card and Hoary. I've tested several different distros and I've usually succeeded with my wi-fi connection. Now I really don't know where the problem lies.

My wireless card is Asus WL-100g which has Broadcom chipset. I can load my Windows drivers with ndiswrapper, as usual. But when I try to kick that connection up, it won't work. iwconfig shows that wlan0 is existing. *iwconfig wlan0 essid NAME* etc. configuration commands doesn't change anything. 
iwconfig listing:

wlan0     IEEE 802.11g  ESSID: off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key: off
          Power Management: off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

What to do? System finds the device correctly, I've tried to change Radiostate from 1 to 0 as was suggested in some other discussion, "acpi=noirq" as boot option doesn't help either.

By the way, I'm using Kubuntu, but it is basically same as "real" Ubuntu.

---

### Post by bfisher on 2005-04-09
I have idential problems Hyde... I am using Kubuntu with a Broadcom-based card, and I cannot set the essid. The iwconfig commands do not work. I tried to force the changes with iwconfig wlan0 commit, but that didn't help either. I have another thread I started last night (Wireless Card Not Seeing ESSID), so watch that and we'll see we get it figured out. I am thinking I may just install Warty and see if it works under there. At least then I'll know it has something to do with Hoary. I've had this card working under other distros, so I know it will work... eventually. :)

Brandon

---

### Post by mehaga on 2005-04-09
I used to have a USB Asus card, and I never got it to work. I don't think it can be done. I replaced it with a Micronet card that cost 20 euro. I can't remember the model. sp906bb, I think. It worked great with suse 9.2...

Now, I can't get it to work with Ubuntu :(

I got the ndiswrapper installed, it loads and says that both the HW and the driver are present. But I don't have wlan0 interface :(( I only have lo and sit0.

I used lscpi to get the card PCIID.
I did:
ndiswrapper -d 00:00:0d:00 net8180
That should load the driver for the device specified by PCIID number. I get  an error saying that it's an invalid PCIID :( 

I bought a gun, put it in my mouth and pulled the trigger, but that didn't work either. The gun didn't fire.

:)


Seriously, how do I get the wlan0 to show up?

---

### Post by hyde on 2005-04-09
[QUOTE=bfisher]I have idential problems Hyde... I am using Kubuntu with a Broadcom-based card, and I cannot set the essid. The iwconfig commands do not work. I tried to force the changes with iwconfig wlan0 commit, but that didn't help either. I have another thread I started last night (Wireless Card Not Seeing ESSID), so watch that and we'll see we get it figured out. I am thinking I may just install Warty and see if it works under there. At least then I'll know it has something to do with Hoary. I've had this card working under other distros, so I know it will work... eventually. :)

Brandon[/QUOTE]
 Hi Brandon

Do you get your card alive? Usually my card's "link" led turns on when I give "modprobe ndiswrapper". With this Hoary thing it doesn't happen.  I see from dmesg lines that module is loaded and wlan0 added.

I read similar problem from [http://ubuntuforums.org/showthread.php?t=22312](http://ubuntuforums.org/showthread.php?t=22312)
Problem is probably in ndiswrapper package.
I started to compile new version of ndiswrapper, but I gave up because there was some hassles with kernel sources blah blah etc. 

Sounds too damn hard for me in a year 2005! Call me lazy if you want, but I think that there should be apt-get/synaptic(/kynaptic for Kubuntu) solution for this asap!
I'd like to like this distro, because it's clean, good looking one CD distro without all extra bloatware stuff (like Mandrake or Fedora to name a few...) But I'm sad to see this kind of problems, because I automatically suppose that newer version is always better than older ones. Take a look at SimplyMepis, if you want to see quite easy and simple way to configure wireless cards.

---

### Post by mehaga on 2005-04-09
Sorry. I lied about Asus card. I DID get it to work, but I never got the PEAP encryption to work. I remember I used wlanctl stuff, not the iwconfig stuff. :)
I love that last sentence :)

---

### Post by mehaga on 2005-04-09
Hyde, I don't think you need ndiswrapper for your Asus card. There are linux drivers for it, if I remember well.

---

### Post by hyde on 2005-04-09
[QUOTE=vekaz]Hyde, I don't think you need ndiswrapper for your Asus card. There are linux drivers for it, if I remember well.[/QUOTE]

Asus wlan card is based on Broadcom chip, which is very common. Broadcom doesn't deliver any Linux support. It works very well with ndiswrapper and WinXP driver. But not at this time... [-(

---

### Post by samfrancis1 on 2005-04-10
dude's

im the one who needs the help here and still do :(

Dammit! Its just not damm working! TELL ME WHAT TO DO!!!!!!

i went back to windows a few days ago and now im bak with Linux, dont make me convert back!

---

### Post by jonny on 2005-04-10
[QUOTE=hyde]Asus wlan card is based on Broadcom chip, which is very common. Broadcom doesn't deliver any Linux support. It works very well with ndiswrapper and WinXP driver. But not at this time... [-([/QUOTE]Try [this How To.](http://ubuntuforums.org/showthread.php?p=125537#post125537)

---

### Post by samfrancis1 on 2005-04-11
[QUOTE=jonny]Try [this How To.](http://ubuntuforums.org/showthread.php?p=125537#post125537)[/QUOTE]

tryed and stil not working.

[SIZE=3]Help Plz:)[/SIZE]

---

### Post by lao_V on 2005-04-11
Am I the only one to think that the title of this post and others started by samfrancis1 are completely misleading, and also in the wrong place?

---

### Post by samfrancis1 on 2005-04-11
[QUOTE=lao_V]Am I the only one to think that the title of this post and others started by samfrancis1 are completely misleading, and also in the wrong place?[/QUOTE]

no, cause i cannot connect into my WLAN!

Also this is the right place cause i sort of put it in the HOWTO and FAQ's section and then moved here

---

### Post by lao_V on 2005-04-11
if you type lspci can you see your card listed? If so what is the output of iwconfig?

---

### Post by samfrancis1 on 2005-04-11
[QUOTE=lao_V]if you type lspci can you see your card listed? If so what is the output of iwconfig?[/QUOTE]
 i c mine on there

no wireless extentions for all.

---

### Post by lao_V on 2005-04-11
Ok, you will most likely have to use [NDISWrapper]("http://ndiswrapper.sourceforge.net/") or [DriverLoader]("http://www.linuxant.com/driverloader") to make it work. Both if these require you have Windows drivers for your wireless. I've found driverloader extremely easy to use but lot of people prefer NDISWrapper. Follow the guides on the website on how to install them and also look at [WiFiHowto]("http://www.ubuntulinux.org/wiki/WiFiHowto") for Ubuntu

---

### Post by samfrancis1 on 2005-04-11
tryed NDIS but i havnt put my disc in yet what ill do now!

---

### Post by hyde on 2005-04-11
[QUOTE=samfrancis1]tryed NDIS but i havnt put my disc in yet what ill do now![/QUOTE]

I got mine Broadcom based wlan card working! :grin:
I had to edit **all** the .conf files in my /etc/ndiswrapper/bcmwl5 directory. 
My card started to work after I changed all "RadioState" values from 1 to 0.

Have you tried that already?

---

### Post by samfrancis1 on 2005-04-11
theres no .conf in my file there:(

---

### Post by escuchamezz on 2005-04-11
Yo, diggity check yoself before you wreck yoself

---

### Post by hyde on 2005-04-11
If you don't have any *.conf files in your /etc/ndiswrapper/DRIVERNAME directory, then it seems that you haven't loaded any driver with ndiswrapper. You have done all that *ndiswrapper -i driver.inf* and *modprobe ndiswrapper*? Is there any lines regardind to ndiswrapper in dmesg?

---

