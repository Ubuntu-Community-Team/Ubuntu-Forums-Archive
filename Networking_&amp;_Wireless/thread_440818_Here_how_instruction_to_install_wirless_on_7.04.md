---
title: "Here how instruction to install wirless on 7.04"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by andytx on 2007-05-12
I did installed on my network card Belkin F5D7000 V7  Can be download here:[http://www.belkin.com/support/article/?lid=en&pid=F5D7000&aid=6001&scid=0](http://www.belkin.com/support/article/?lid=en&pid=F5D7000&aid=6001&scid=0)   or driver this driver: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L)
My card is realtek 8185L chip
I used the XP driver from Link above: Below is intruction:


To load Driver 

1 go to Application >> ADD/remove 
Search Box Type" NDiswrapper" Then Hit Apply to install
and install Network manager, Wirelesss asistant, and Wifi, and what ever relative to networks.
Or Can install new version of NDiswrapper if you like

2: Go to your wireless website download Driver XP or Vista driver of your network card whatever USB or PCI.
x64 is for 64bit OS
X86 is for 32bit OS

3: Save it to your Desktop and doube click and extract the folder to the desktop
should have 3 files in the folder. Name.inf , name.sys , name cat or bin

4: Now go to terminal console:
Type > cd and drag the folder of the driver on the desktop to terminal should be like this
 
$ cd driverfolder
Then Type:
ndiswrapper -i name.inf
>It's will show 
>>Installing name.inf
>its mean OK
now type:
ndiswrapper -l 
it's will show:
Driver name.inf installed
Then Restart the computer

come back to terminal:
type again:
ndiswrapper -l
It's will show
bcmwl5: driver installed
device (14E4:4320) present 

That mean Drivers had loaded

Now Final: To load Device (module)

Type :
depmode -a

If there is NO error then continue

Type: modprobe ndiswrapper 
If there is NO error, Your wirless card Light should be Blinking now


Then go to Admin>> Network> check mark to the Wirless device

now goto Application > open Wirless asistant or wirless whatever to set THE WEP password


Have Fun

yeuemnhat(andytx)

---

### Post by hdensley on 2007-06-24
Hey Andy,  we seem to have the same card.  I tried your instructions, and here's where I'm having problems with step 4:

4: Now go to terminal console:
Type > cd and drag the folder of the driver on the desktop to terminal should be like this

$ cd driverfolder
Then Type:
[COLOR="Red"]ndiswrapper -i net8185.inf[/COLOR]
>It's will show
>>Installing net8185.inf
>its mean OK
now type:
ndiswrapper -l
it's will show:
[COLOR="Red"]Driver net8185.inf installed[/COLOR]
Then Restart the computer

come back to terminal:
type again:
ndiswrapper -l
It's will show
net8185.inf: driver installed
[COLOR="Red"]it will not show this -[/COLOR] device (14E4:4320) present

---

