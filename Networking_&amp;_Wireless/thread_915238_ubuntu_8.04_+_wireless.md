---
title: "ubuntu 8.04 + wireless"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by redviper on 2008-09-09
First of all I would like to apologize because there is probably a lot of material related to this subject but after a quick google I'm stuck and have decided to call for help..

here is the deal...I'm trying to use wireless on my ubuntu 8.04 32bit...i learned of madwifi and ndiswrapper. I chose the second option, although that is probably not a better one but for now I'm with it so...

i think i successfully compiled ndiswrapper and using ndisgtk isntalled my xp driver that works in winxp..

now since I'm a total linux noob and this is all from various forums and howtos
could someone please help me interpret these outputs:

ndiswrapper -l
[ATTACH]84734[/ATTACH]

sudo lshw -C network
[ATTACH]84735[/ATTACH]

dmesg | grep -e ndis -e wlan
[ATTACH]84736[/ATTACH]

Again I'm a total linux noob so please try to use as simple language as possible, however I am also willing to learn this stuff so any help is welcome.

thanks in advance

btw my wireless adapter is atheros AR5007EG Wireless network adapter

---

### Post by arunvir on 2008-09-09
Pal! you and I are much the same!!!! from system configuration to system user level............

Even I didn't know much about all these stuffs at first

But if you take my advice I would ask you to use ndisgtk for installing the driver........... It is damn good

I'll post some screenshots of how it went about for me!!!!!!!!!! I got mine working btw on kubuntu with wifi-radar........... 

first make sure you remove the madwifi drivers that come with ubuntu pre-installed.

just uncheck the checkboxes in the hardware drivers page and for confirming again type the command in the terminal.

echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist

now open the /etc/modprobe.d/blacklist file and check at the last whether the line 
blacklist ath_pci

is added.

Now restart and then install ndisgtk from synaptic or apt-get
then just for making sure everything went alright restart.

now unzip the WHQL drivers that you got(for ubuntu 8.04 only)
my version was "Wireless_Atheros_V5.3.0.67_XP_XB63_XB62(WHQL).zip"

unzip the zip file and open ndisgtk from system->administration->windows wireless drivers(it ll be there somewhere)

in that click on install new driver and select net5211.inf in the folders <whereyouunzipped>/drivers/xp-32/net5211.inf

and after installing it click on configure network button
that must take care of everything.


Then install wifi-radar using apt-get. It is much more simple than the network manager that comes with ubuntu.

you can use it as illustrated in the screenshots.
just restart once to make sure everything starts working form the first.(most of the time the drivers need to start fresh to 
work properly.)

I didn't want you to miss anything thats why I explained each step that I followed from the beginning.

btw whats your laptop model??????????


> neither madwifi or ndis-wrapper are worst. It's the laptop manufacturers who don't support us/linux are the worst.
btw I have also tried madwifi drivers in ubuntu not far back. They are both excellent(provided one knows how to use them).


---

### Post by arunvir on 2008-09-09
by the :guitar:way I learnt somewhere that the mode has to be managed.......

channel number has to be got from your router configuration...........

security can be open or whatever you want.........

if you have dhcp enabled in you wifi router, then no need to give manual IP as I did........

Leave connection commands unattended.........

check your router configurations when giving these details.

If you are unsure of your config then

use this command to see what networks are available

sudo iwlist wlan0 scan.......... It'll display nearly all details you want(especially look for your Access point in this list.)

u can use that to enter details in your wifi-radar configurations.
:guitar::guitar:

---

### Post by sinofemp on 2008-09-09
i have a compaq c783tu laptop with Atheros wifi hardware.
the problem is that my wifi is not working, "Wireless Networks" is not showing in the "Manual Network Configuration", probably because of not having that driver.

what i have to do to enable my wifi?

i tried google and found in one blog to install madwifi,
i did that but no use,. its still the same!

please help me.

---

### Post by arunvir on 2008-09-09
sinofemp I'm also from india............ i'm going to sleep now................ will post as soon as i get up tomo ........ bye now..........:guitar::guitar::guitar::popcorn:

---

### Post by lilmale1 on 2008-09-09
if you would like to know more, first let me know if you have ur internet runing already. with ubuntu.
or are u going to use wifi-radar or somthing

because you wont have to configure anything anymore just install wifi-radar_1.9.6-0ubuntu4_all_.deb


try searching for wifi radar for linux. then you will get some options, choose debaian file with just runs the program. how do u know wich is a debian file by .deb

and u see it says all.deb it work without configuring anything else for your wif and just the password set it to auto.

worked for me

thanks for lettin me know u can use any inf xp driver i didn't know that. i though you need to search for a linux inf

---

### Post by arunvir on 2008-09-10
Hi pal..... Infact the word "windows wireless drivers" that comes up when you install ndisgtk, must let you know that it is expecting a pure windows driver......... And I also found one thing more.... The new atheros drivers for vista SP1 are also WHQL and therefore can be used in XP as well as ubuntu with ndisgtk..... I have'nt tried it though.........

The one for vista actually was not WHQL......... Wonder what this WHQL is after all....... seeing it for the first time in my life.......I'm going to search about it.......

**lilmale1......... Please let me know your laptop model**..... if it's acer then I think you could tell me how you setup the acer wireless hot keys at the top of the keyboard....... I really am trying to get that working for the past few installs of ubuntu and kubuntu........
:confused::confused:
for sinofemp........ I believe that everything on the first reply I made in this post is all you need........ enjoy your stay with ubuntu...

(for me kubuntu!!!!)

:guitar::guitar::guitar:

---------------------------------------------------------------------

Acer_acpi how do you work???? I'll find it!!!!
:mad:      :guitar:    :popcorn:

---

### Post by redviper on 2008-09-10
@arunvir

thanks for the info...I did not have the time to try anything today and yesterday, as soon as I do I will have results here.

btw my laptop is toshiba a210-19k

---

### Post by arunvir on 2008-09-10
pal. If your system has any special keys or led that glows when you have wireless enabled might not work with these drivers. Don't worry just check whether you are able to scan for any wireless networks and your ifconfig shows up a wlan0 or ath0.

All the Best!!!!:):):guitar::guitar:

---

### Post by redviper on 2008-09-13
I found a solution...thans for helping.
Now I'll probably gonna be bothering everybody with ATI 3d acceleration...:D
but not here...:D

regards,

---

### Post by sinofemp on 2008-09-18
thanks a lot [COLOR="Red"]**"arunvir"**[/COLOR]:guitar:

it works...

good job..

---

