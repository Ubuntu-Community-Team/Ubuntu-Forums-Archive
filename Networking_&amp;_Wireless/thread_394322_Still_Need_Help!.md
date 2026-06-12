---
title: "Still Need Help!"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by dawv on 2007-03-26
"I have read some previous posts.. but none are helping me... What I need is a step by step guide on getting me Airlink101 AWLH3026T Wireless Adapter to work on the Ubuntu side of my XP/Linux PC. (if its even possible) There is **no** way for me to connect to the internet through Linux as of yet, so i may need to transfer some files to separate partitions. I can connect to the internet when running XP... but on linux, it dosen't even detect it.. i even search through the HARDWARE thingy... Please be aware, that im a total n00b at this and this is the first (and will hopefully be the only) Linux distro i have used...

So.. i need a step by step (in plain English) guide on how to get this to work...

I hope this isn't asking too much..

THANKS!"

---

### Post by dawv on 2007-03-26
Some Won Flooping Help Me Pleeeeeze!!!! I Cant Even Connect To My Network!!!!! Come On!!!!!

---

### Post by Mr. C. on 2007-03-26
How about taking a chill pill and learning to relax; stop screaming at the rest of us, and consider that perhaps your communication is not very clear.

Just because you feel "you need" a step by step guide doesn't mean the world owes you one.

That you want us to email your offline because you probably won't come back to follow-up on your own request is pathetic.

Since you're not reading this most likely, don't let the door hit you on the way out.

MrC

---

### Post by Floppyjoe on 2007-03-26
I read this post:
[http://www.ubuntuforums.org/showpost.php?p=2294391&postcount=3](http://www.ubuntuforums.org/showpost.php?p=2294391&postcount=3)
and it seems to suggest that you need to use ndiswrapper with the windows driver to get your card to work. I'm not sure what native driver they blacklisted but perhaps you can search the forums and figure out a way to get it working.

---

### Post by chili555 on 2007-03-26
We are all volunteers. We get not a cent for helping or not helping anyone. You are trying to get help by yelling and cursing. There are many posters here who say please and thank you. I will help one of them.> the odds of me actually comeing back here are slim to none {im a busy guy}Then I doubt you will benefit from those gracious enough to try to help.

---

### Post by MontanaMax on 2007-03-26
Dawy, the exact plain english step by step guide that you **need** is right here.

[http://www.ubuntu.com/community/conduct](http://www.ubuntu.com/community/conduct)

Please see the other posts for more information about the technical issue.

---

### Post by dawv on 2007-03-26
ya im sorry, i just get irritated easily, im sorry if i offended any one, but thanks for the help....

I have  ndiswapper, and I have the native driver on this cd.. so do i just blacklist it?

How exactly would i go about doing this... and i said I "may not" come back.. but i did.. that was my first post, and by my second.. i decided i should saty for awihle.. so sorry for any confusion..

so.. do i blacklist, ndiswapper, then will it work? or what am i missing here....


again sorry, i did act a bit childish and i get overly anxious when it comes to stuff like this...

ignore the e-mail part that i said.. just reply here or wherever, thnx for everything..

---

### Post by dawv on 2007-03-26
P.S. i have read two posts before about this exact model (googled.. only two cases {several trys too}) and have come up with nothing...

would this be counted as a bug? or has this not worked because barley anyone has it? (no linux driver mde yet)

I have seen some things saying something about a ralink driver.. but how in the world would that work? (two completely different companies),

Thanks again... again...

---

### Post by digital_sabotage on 2007-03-26
if you have ndiswrapper installed you should be able to run it from >System>Administration>Windows wireless drivers  ...select "install driver"
...you then browse to where the ".inf" file is on your windows driver disk or folder ...after that is complete you should see your wireless connection in >System >Administration >Networking  ...if you have a password set up on your router that is where you enter your ssid and password

---

### Post by dawv on 2007-03-26
ssid?

i have a WEP key if thats what you mean.. ive set it up in windows b4.. soooo ya

---

### Post by MontanaMax on 2007-03-26
Unfortunately ndiswrapper drove me half-crazy when I tried to use it several months ago. I'm sure that project works extremely well for some people, but I wasn't having any luck with it. Wo I went the fast and easy way with this product:

[http://www.linuxant.com/driverloader/](http://www.linuxant.com/driverloader/)

Worked like a charm on the first try. However, after the trial period ends my buddy is going to need to shell out the 20 bucks for the license. Well worth it in my opinion.

Good luck.

---

### Post by digital_sabotage on 2007-03-26
that's what i mean

---

### Post by Floppyjoe on 2007-03-26
There is possibly a native driver that will attempt to associate with your network card that comes installed in Ubuntu. This native driver would need to be blacklisted if it interferes with your driver that you will install with ndiswrapper. First you need to install ndiswrapper if you have not already. Then you need to look for your windows drivers for your card on the CD that you may have. The files needed for installing your driver via ndiswrapper are ones that end with .inf and .sys and possibly .bin. You need to move these files to your home folder then open up a terminal and issue the command"
```
sudo ndiswrapper -i drivername.inf
```
Where the drivername is the name of the driver from your disk.
After that you need to see if the driver and hardware are present and validby issuing:
```
sudo ndiswrapper -l
```
If everything is okay then issue:
```
sudo depmod -a
```
```
sudo modprobe ndiswrapper
```
Then
```
sudo ndiswrapper -m
```
to get ndiswrapper module to load at boot.

Then there is the matter of blacklisting the native driver.
I don't know the name of that driver but if you find it then :
```
sudo gedit /etc/modprobe.d/blacklist
```
and add the words:
```
blacklist drivername
```
where drivername is the name of the conflicting native driver that you will need to figure out.

---

### Post by dawv on 2007-03-26
it doesn't appear my card, or even my manufacturer for that matter, is supported with it....

would it still work?

---

### Post by dawv on 2007-03-26
how would i find the conflicting driver, and how would i know there *IS* one?

---

### Post by dawv on 2007-03-26
wait a sec..... i've heard (or read i should say) somewhere that linux thinks this card is a ralink, and triees to use *its driver*... i think.... they said blacklist... ralink... and Airlink101 AWLH3026t all in one post.. so i *think* this is it... tell me if im wrong... and ill doucle check to see what that driver was...

---

### Post by antmenj on 2007-03-26
It could be an idea to remove your email address (first post) before the spam bots grab it ;-)  You dont want more crap emails about v1agra etc?

---

### Post by dawv on 2007-03-26
lol.. i already get those :P

---

### Post by Floppyjoe on 2007-03-26
> **dawv said:**
> how would i find the conflicting driver, and how would i know there *IS* one?

I am just going according to this post where the person says how he got his to work:
[http://www.ubuntuforums.org/showpost.php?p=2294391&postcount=3](http://www.ubuntuforums.org/showpost.php?p=2294391&postcount=3)

possibly issue :
```
dmesg
```
and search for a driver that is binding to your wifi card.

---

### Post by dawv on 2007-03-26
oh ya.. i remember reading that thread about a month ago.. man this is a small internet.. :P

i didn't see what he did there....

---

### Post by dawv on 2007-03-26
switching over to linux to try what you guys said... wish me luck!

---

### Post by dawv on 2007-03-26
i have a WLAN card.. not a Wifi...

---

### Post by Floppyjoe on 2007-03-26
> **dawv said:**
> i have a WLAN card.. not a Wifi...

wlan means wireless lan or wifi(wireless fidelity)

---

### Post by MeeMaw on 2007-03-27
You have talked about ndiswraper and also RaLink drivers - We need to see what you actually have.  Please post the output of the following commands---

sudo lspci

sudo iwlist scan

Please be patient and we will try to help.    :)

---

### Post by dawv on 2007-03-27
well, i cant figure out how to install this ndiswrappper thing... what does it mean my "switch to that directory" (second or third satep i think)

---

### Post by dawv on 2007-03-27
and how am i suposed to post the output? i cant copy and paste between OS's.....

---

### Post by MeeMaw on 2007-03-27
> **dawv said:**
> and how am i suposed to post the output? i cant copy and paste between OS's.....

You CAN copy & paste to an Open Office document - save it as a Word document and open it up in Windows.....   or you can _write it down on a piece of paper_...... (I did LOTS of that trying to get my wireless going!!!! My Windows hard drive is at work!)

:KS

---

### Post by dawv on 2007-03-27
oook, then how do i open it in Windows... i don't eben have word.....
 
and i cant see files between different partitions... so what then?

---

### Post by MeeMaw on 2007-03-27
Well, I guess you'll have to use the pencil...... and write it all down.
:(

---

### Post by Floppyjoe on 2007-03-27
> **dawv said:**
> well, i cant figure out how to install this ndiswrappper thing... what does it mean my "switch to that directory" (second or third satep i think)

To install ndiswrapper with a internet connection click on System/Administration/Synaptic Package Manager.

Search for ndiswrapper.

Download "ndiswrapper-utils-1.8" and "ndiswrapper-common"

To install ndiswrapper without internet connectivity click on System/Administration/Synaptic Package Manager

Click on Edit/Add CDROM and follow the instructions using your Ubuntu Install disk.

Then click Reload.

Search for ndiswrapper.

Download "ndiswrapper-utils-1.8" and "ndiswrapper-common"

If you want to know how to install a windows driver with ndiswrapper the most easy way is to move the windows driver files to your home directory by clicking on places then home folder and copying the files into there. Then issue the "sudo ndiswrapper -i drivername.inf" command where you substitute the name of your driver for drivername.inf. If you have some invalid ndiswrapper drivers you can delete them by using the command "sudo ndiswrapper -e drivername". You can see any ndiswrapper installed drivers with the "ndiswrapper -l" command

---

### Post by dawv on 2007-03-27
ummmm if you havent figured out what im trying to do here... the you should read...
 
I have NO way for an internet connection in Linux, thats what this whole topic is about... so how would i install the ndiswrapper that i have onto it? i don't get the terminal commands...
 
or more specifically, the writer of the instructions cant use proper english at all...
 
I dont get where it says "go to the other folder" dose it mean browse? go throught the terminal, or what? and how?...... and how would i download something without any connection to any network, none the less an internet connection...
 
 
anyway... heres what i got on the output MeeMaw:
 
```
 
sudo lspci:
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP2A ISA bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP2A SMBus (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP2A USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP2A USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation MCP2A USB Controller (rev a2)
00:04.0 Bridge: nVidia Corporation MCP2A Ethernet Controller (rev a3)
00:06.0 Multimedia audio controller: nVidia Corporation MCP2S AC'97 Audio Controller (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP2A PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation MCP2A IDE (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)
02:07.0 Network controller: RaLink Unknown device 0302
02:08.0 Communication controller: Conexant HSF 56k Data/Fax Modem

Please not i DO NOT have ANYTHING RaLink.... As it thinks I do....
------------------------------
sudo iwlist scan:
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wmaster0  Interface doesn't support scanning : Operation not supported
wlan0     No scan results
sit0      Interface doesn't support scanning.

well.... i have no idea what this means...


```
 
and thats cool, casue in notepad it was messed up (the "code") and when i copied and pasted, it fixed it! coooolllll
 
anyway thats what i got from the teminal....

---

### Post by Floppyjoe on 2007-03-27
You don't need the internet to install ndiswrapper if you have the Ubuntu install disk handy like i described in my previous post.

---

### Post by dawv on 2007-03-27
yes i have the ububu edgy (6.10) disk handy, right here infact, so is ndiswrapper on the disk or something?
 
or does it do something else?
 
thx in advance

---

### Post by dawv on 2007-03-27
btw, i have a version of ndiswrapper on my linux.... but i don't know if its the right version or what.. i really don't know how this stuff works...

---

### Post by Floppyjoe on 2007-03-27
> **dawv said:**
> yes i have the ububu edgy (6.10) disk handy, right here infact, so is ndiswrapper on the disk or something?
 
or does it do something else?
 
thx in advance

Yes ndiswrapper is on there. if you do not already have it installed you can use that disk like I described in the other post to install it. I unfortunately have to run(coffee) so I won't be able to help you farther at the moment.

---

### Post by MeeMaw on 2007-03-28
Unfortunately, if you need to configure it with ndiswrapper, I can't help you, because I've got no experience with ndiswrapper.  I'm sure someone who knows can help.

I'm sure you can get it with a little work. Don't give up!!!  :KS

---

### Post by dawv on 2007-03-28
ok.. ive run into problems... i ndiswrapped all of my drivers and 3/4 of them sayl "invalid driver" or something like that. Only one works..... 
 
im kinda lost, i don't even know what the problem is.. 
 
i have ndiswrapper installed and one of my drivers working, but i cant find which driver is messing everything up and what its calles.. i tryed the command you said, but it came up with a loooooooooooong list of nonsence.(*as in WTF does all this mean*!)

---

### Post by dawv on 2007-03-28
oh and MeeMaw, I know EXACTLY what hardware i have (im not a re' re') and it definately isn't a*** Ralink***, as linux believes. *(as you can see in the code)*
 
my ethernet port isn't even Ralink, it's like an nVidia or something.....
 
my _wireless_ card *(the one i'm using in windows roght now as i type, and the one i cant get to work for linux)* is an **Airlink101 AWLH3026T** *(i memeorized the number!!!)*

---

### Post by Floppyjoe on 2007-03-28
> **dawv said:**
> ok.. ive run into problems... i ndiswrapped all of my drivers and 3/4 of them sayl "invalid driver" or something like that. Only one works..... 
 
im kinda lost, i don't even know what the problem is.. 
 
i have ndiswrapper installed and one of my drivers working, but i cant find which driver is messing everything up and what its calles.. i tryed the command you said, but it came up with a loooooooooooong list of nonsence.(*as in WTF does all this mean*!)

I'm not sure which guide you are following to install your drivers but usually there is a .inf file and a .sys file and sometimes a .bin file. You only need to install the .inf file with ndiswrapper however the other file(s) need to be in the same directory that the .inf file is in when you install it.

The drivers are case sensitive and must be spelled with the right lower or upper case letters when you install them.

You need to delete any drivers listed as invalid. To view your installed drivers enter into the terminal the following:
```
ndiswrapper -l
```

To delete the invalid driver listed from the command above enter:
```
sudo ndiswrapper -e drivername
```
Where drivername is the above listed invalid driver.

---

### Post by dawv on 2007-04-05
sorry for the bump....
 
but anywayz.. i was at my dads hous ethe last week, and i was checking my email (i do this every month or so) and found a reply from the Airlink support peeps... and they gave me a link to some Ralink drivers... so now i know that i have an Airlink card the was *manufactured *by Ralink... so i know have the drivers and have yet to test them... wish me luck...

---

### Post by dawv on 2007-04-08
ok... again, i have the Ralink drivers needed and the instructions that came with them are extremely confusing, and i cant actually find which are the drivers... 
 
There are a bunch of different files that came with the package that it came with, and the instructions to install the drivers are poorlly translated from french with the worst grammer i have seen in my life. 
 
Its like a 2 year old trying to explain quatom mechanics... it just doesn't make any sense....
 
so if you want to help ill send you the stuff needed too figure it out.
 
either ask for the instructions, the files or both...
 
thanks!;)

---

