---
title: "How-to-install? Option iCON 225 3g-usb-datamodem"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by rhinoFinn on 2008-03-27
I'm quite newbie with Ubuntu/Linux.
I have installed latest beta-version of Ubuntu 8.04 and it installed and works wery well ( :
But now I still have one major problem ( : I have tried to install and get working Option iCON 225 3G-usb-datamodem to utilie my 3G-mobiledataconnection. But this hasn't worked yet ) :
I have Windows Vista too in this same laptop and that mobiledatamodem installs and works perfectly in it.

This mobiledatamodem has ZeroCD, so it works in two state, either as flash-drive (to install included win/mac-drivers and software) or as 3Gmobiledatamodem. So it needs drivers, utility to change that stage from flash-drive to mobiledatamodem. 

There is implementation for linux for that modem (hso-driver and rezero-utility to change flashdrive/modem-state, and Vodafones graphical utility to use modem):
I have tried to understand and do as things are (partially) told in these advices :

[http://www.pharscape.org/component/option,com_forum/Itemid,68/page,viewtopic/t,425/](http://www.pharscape.org/component/option,com_forum/Itemid,68/page,viewtopic/t,425/)
see package of hso and rezero in the beginning of those messages

(in French)
[http://www.blogeee.net/2008/03/14/tutorial-une-cle-3g-sur-votre-ultraportable-pour-30e/](http://www.blogeee.net/2008/03/14/tutorial-une-cle-3g-sur-votre-ultraportable-pour-30e/)

Vodafones graphical utility:
[https://forge.vodafonebetavine.net/frs/?group_id=12&release_id=19](https://forge.vodafonebetavine.net/frs/?group_id=12&release_id=19)


I have tried to get this 3G-mobiledatamodem installed and working with Ubuntu 8.04 but haven't succeeded yet. I think that I should change somehow sh-scripts in those mentioned guides, but as a linux newbie don't know how exactly. Those guides seems to be inadeguaite and for different linux-distribution and kernel version than Ubuntu 8.04. And may be that my laptop computers configuration is somehow different, especially with usb-configuration, and needs some investigation and changes with those sh-scripts, but I don't know how to investigate and how to do it ) :
In windows it seems to be easier to look at configuration in graphical utlilities.

I'd be wery gratefull of advices what and how I should to to get this 3Gmobiledatamodem installed and working in Ubuntu too.

---

### Post by TpyKv on 2008-03-30
Hey,

I have a similar card & am also looking for a fix. I have seen it work for the 3 (network)'s card but not for the orange one... 

[http://ubuntuforums.org/showthread.php?p=4612929#post4612929](http://ubuntuforums.org/showthread.php?p=4612929#post4612929) - is the post I put up - anyway I can't get rid of Vista until this works so I am on the case :)

don't know if this is of any use.. 
[http://www.klabs.be/~fpiat/linux/debian/Option_Qualcomm_MSM6275_UMTS/](http://www.klabs.be/~fpiat/linux/debian/Option_Qualcomm_MSM6275_UMTS/)

---

### Post by rhinoFinn on 2008-03-31
Hi,

Aguess this... 

[http://www.equinoxefr.org/index.php/post/2008/03/29/la-clef-orange-icon-225-sur-ubuntu-710/](http://www.equinoxefr.org/index.php/post/2008/03/29/la-clef-orange-icon-225-sur-ubuntu-710/)

...works with Ubuntu 7.10 ... but I'd like to get this working with soon-to-be-released Ubuntu 8.04.
That guide doesn't work with it - needs at least compiling with more recent kernel...

And there's very detailed Finnish guide too ( : (sorry folks my native language ; )

[http://forum.ubuntu-fi.org/index.php?topic=16947.msg126660#msg126660](http://forum.ubuntu-fi.org/index.php?topic=16947.msg126660#msg126660)

---

### Post by TpyKv on 2008-04-01
OK that's great! thank you!!

Now does anyone have a finnish to english translator!?!

:)

---

### Post by TpyKv on 2008-04-01
I have just been told this will not work...

For starters it will use 'chat' parameters for the French network (which are likely to be different from what you need in this country) 

Also - The tarball they are using was written for a version of Ubuntu that they put on to replace Xantos on a eeepc. All in all the combination is not what I want...

still open to idea!!?

---

### Post by VMZ on 2008-04-01
Here's my messy guide :)

It's what I did with Kubuntu 7.04.. 

***

Use a cellphone to disable PIN-request from the SIM. Probably it can be enabled afterwards (didn't try to, so dunno if it works...).

```
sudo -s -H
mkdir option
cd option
wget http://asuseee.free.fr/tuto/01/icon225.tar.gz
tar zxf icon225.tar.gz
mkdir /lib/modules/2.6.21.4-eeepc
mkdir /lib/modules/2.6.21.4-eeepc/extra
./install.sh
gedit conninfo.ini
```

In conninfo.ini you'll need to do the following changes

"# APN=" --> "APN=internet.saunalahti" or "APN=internet"
("# PIN=&#8221; --> &#8220;PIN=blahblahblah&#8220;) ...if PIN-request is enabled.

```
mkdir usb
cd usb
```

download file from [http://www.pharscape.org/index2.php?option=com_forum&Itemid=68&page=download&id=28](http://www.pharscape.org/index2.php?option=com_forum&Itemid=68&page=download&id=28) and save to "usb"-folder

```
tar zxf hso-udev.tar.gz
make
make install
cp hso.udev /etc/udev/rules.d/z20_hso-udev.rules
udevcontrol reload_rules
cd ..
mkdir hso
cd hso

```

download file from [http://www.pharscape.org/index2.php?option=com_forum&Itemid=68&page=download&id=30](http://www.pharscape.org/index2.php?option=com_forum&Itemid=68&page=download&id=30) and save to "hso"-folder

```

tar hso-1.1.tar.gz
make
make install
cd ..
```

stick in your stick

```
dmesg | grep hs
``` ---> if you get something like "HSO: Found Network port hso0", then it's probably ok.

```
exit

sudo ./connect.sh up

```

!!! yippekayee !!!

```
sudo ./connect.sh down
```

***

---

### Post by Bukunut on 2008-04-02
Hello

I got the Option icon 225 modem today (Orange UK). 
Has anyone managed to get the modem working on a laptop (Just for ref :HP Compaq nx9010)  in Hardy Heron?

Any ideas would be welcomed indeed!

Thank you - Bukunut

PS. Hi RhinoFinn! - Have you managed to come across any news on this yet?

---

### Post by rhinoFinn on 2008-04-02
>> PS. Hi RhinoFinn! - Have you managed to come across any news on this yet?

Nope, those guides, drivers and scripts seems not to work on Ubuntu 8.04 Hardy Heron ... need changes and recompiling or something like that ... and I'm not that much fancy on Ubuntu/linux to put that efford ... so I returned to Windows Vista - it just works great and sooooh much more easily :D
I got clear evidence why linux isn't yet not even nearly ready for common computer user - needs far too much work to get into real work with it :D

---

### Post by TpyKv on 2008-04-03
VMZ - you rock! going to *attempt* that & will let you know if it works. 

If so I am going to remove Vista today!! getting pretty excited about that :)

BUKUNUT - I'm trying to get it to work in Gutsy Gibbon on a Sony Vaio....! 

RhinoFinn - there's a very good reason why things don't work out of the box - it was never meant to! if companies made drivers or even released the source our lives would be much easier... which is no fault of Ubuntu or Linux... it's just the way it is :) but I get your point, the average user wouldn't be able to do it. straight away..

That's where the community support/spirit comes in - which is second to none. 

and last but not least, if I can manage to figure it out I'm pretty sure you can 

:)

---

### Post by TpyKv on 2008-04-04
Hi All,

I'm sure there is a simple reason why I'm getting this message : 

[http://premium1.uploadit.org/mentholist//nooooooo.png](http://premium1.uploadit.org/mentholist//nooooooo.png)

do I need to install some kind of dependency package before this will work?? 

I followed the commands properly (this was a re-run as a demonstration) but the ./install.sh bit doesn't work 

:(

this is for an eeepc isn't it - the files just don't exist in ubuntu 

damnit, back to using vista again for the forseeable future!

---

### Post by rhinoFinn on 2008-04-04
So I just wonder, why it has been so impossible to obtain simple site of How-To-Install on Linux,
WHERE would be
- component / product names
- just simple guides how to install it on different Linux distros (just wonder why on earth there must be so many of them actually?!) and their versions
- so just the guides, and not that 99% of blaah blaah (or separate function and page for it, of course ; )

That way wisely?open Lixux world would sure be much more efective and happy to be here world : )

- but this is far too much difficult : ) and frustrating - this present way Linux won't ever rise from 2% use.

---

### Post by VMZ on 2008-04-06
> **TpyKv said:**
> 
I'm sure there is a simple reason why I'm getting this message : 

do I need to install some kind of dependency package before this will work?? 


I forgot this 

```
mkdir /lib/modules/2.6.21.4-eeepc
mkdir /lib/modules/2.6.21.4-eeepc/extra
```

Sorry for that... Check out my previous post, I edited it a bit :)

---

### Post by TpyKv on 2008-04-07
VMZ - You are the best! 

If this works - I will be a happy man :)

Can't try it out till tonight as work won't let my personal PC access the net - at 6pm I'll be hoping it works!! 

Will post back tonight!!

rhinoFinn - I will make a website explaining how I did this. And now the info is available here! on VMZ's edited post - all we can do as consumer's is ask them big corporates to make drivers for it - or maybe I should have thought carefully before buying a Sony laptop - and got one that would work out of the box - but that was my choice and I'm paying the price for it - but I'm learning something new every day!!

---

### Post by TpyKv on 2008-04-07
Orange - in their *infinate* wisdom, have sent me the wrong modem1 I have been sent the orange icon 2 one - not the icon 225 - 

I've asked them to take it back - they're sending the new one this week - back when it's all sorted :)

---

### Post by TpyKv on 2008-04-12
IT WORKS!!!

YES!!!!

I had to change a few commands, as it wouldn't let me download the file to the correct usb/hso folder - even as root- so has to delete the directories and and try again - but then it worked!!

Thank you very much!!!

---

### Post by Bukunut on 2008-04-13
Hello


VMZ .. thank you for that how-to finally got it to work and connect after a few small changes. Looking back how the Icon 225 connects to to Orange changed the APN to **internetvpn** as it did in windows did the trick also, managed to get the carrier IP address that failed before.

Rhinofinn - did you get it to work?

Thank you again. - Bukunut

---

### Post by Bukunut on 2008-04-15
Hello

It's working well under KDE. When you update a kernel, you have to go back through the steps for the HSO for the kernel. Other than that it's slightly hit and miss to connect, but works a treat when it is connected.

The one thing that would be of great use is a way to monitor the total data used, input I/O totalled as I have a usage policy of 3 gig per month and with updates it can be very easy to eat these up without realising and control. 
I am not sure how to apply the start up script to Kppp as the app does not see /dev/HSO0 in the list under modems, neither can I see how Knetworkmanger could assist. 

Anyone got any ideas of a monitor or app that would be able to do this?

Thank you  - Bukunut

---

### Post by rhinoFinn on 2008-04-17
Yes, the installation guide - to be fully informative - needs still guides

- what packages to install (add) to be able to compile (make...), bcause these aren't installed with fresh installation of Ubuntu and if there's one trying to get iCON to work, according to VMZ guide, needs these

- how to set up and turn on firewall on Ubuntu (because Ubuntu doesn't set up firewall when installed - and it really should do so, I think - bcause even Ubuntu isn't so safe to be able to connect to internet without firewall - and other linux distros do install and set up firewall) and maybe some other security settings too (apparmor?)

( : getting real things done still more happily&quickly with Windows Vista than with linux-distros : (

---

### Post by Bukunut on 2008-04-19
RhinoFinn

> - how to set up and turn on firewall on Ubuntu (because Ubuntu doesn't set up firewall when installed - and it really should do so, I think - bcause even Ubuntu isn't so safe to be able to connect to internet without firewall - and other linux distros do install and set up firewall) and maybe some other security settings too (apparmor?)

You have to take into account that there is a 'firewall' built into Ubuntu that is called **IPtables** it essentially is the 'firewall' built into your kernel. You can edit the rules for the iptables as you wish, there are many sites that will show you how. From the repositories you can add the app called Firestarter which is a basic GUI frontage for Iptables. Have look in the Security Discussions for some more information. The section Tutorials and Tips has information on IPtables and firewall set up, damn useful.

...Getting things done with more speed, grace, ease and simplicity in Kubuntu than XP or Vista ever could and finding fun too every time ;-)

---

### Post by Libertino on 2008-04-23
Hallo all,

I am trying to get the icon225 working with unbuntu 7.10 (not Kubuntu) or with sidux4.5 - as a distribution using kde. However I didn't get far yet.
I compile hso1.2 and hso-udev from pharscape, which some people describe as sufficient. However, I didn't get a connection whatever I tried.
As I cannot speak or understand finnish , I need some help in english or german.

Is the way mentioned above (post #6) for eeepc in any way suitable for ubuntu7.10? And what would I have to change - if anything -  like the eeepc*.* files to make it work?

Help would be greatly appreciated (before I go crazy).

---

### Post by rhinoFinn on 2008-04-25
This new French guide for Option iCON 225 is easy to understand, just few easy steps for installation and works on Ubuntu/Kubuntu 8.04 :

[http://www.equinoxefr.org/index.php/post/2008/04/21/la-clef-orange-icon-225-sur-ubuntu-804/](http://www.equinoxefr.org/index.php/post/2008/04/21/la-clef-orange-icon-225-sur-ubuntu-804/)

---

### Post by Am3ndment on 2008-05-20
Hello!

Im having problems with iCON 225 -usb-datamodem. It worked just fine few times, but now it gets stuck on "Trying", someone said that removing that usb-stick from computer and booting would work, but not in my case. Any help? (Running Ubuntu 8.04 LTS)
Thanks.

---

### Post by castela on 2008-05-25
Well i managed to toget the icon 225 working at ubuntu 8.04 on my Hp dv9575ep and on my toshiba satellite L300 and i tried to use the pin code but till now i has only worked without the pin code

---

### Post by Cie on 2008-05-26
If you've not already seen it, there is a great little software stack available at Pharscape.org for the Icon225.

The latest edition is a gui, called HSOConnect for connecting/disconnecting with your provider.

---

### Post by silvermoon75 on 2008-07-02
I have a Problem and hope you can help me. I use the Option 225v 3G USB in Germany with T-Mobile. The connect to the Stick, inkl. PIN works, but by submitting the User and Password i got an Error:

```
irgenwo@voyager:~/option$ sudo ./connect.sh up
Initializing...
Trying internet.t-mobile ...
Failed to initialize connection
ATZ
OK
AT+CPIN="2559"
OK
AT+COPS=0
OK
AT+COPS=?
OK
AT+CGDCONT=1,,"internet.t-mobile"
OK
AT=1,1,"tm","tm"
ERRORFailed (ERROR)

irgendwo@voyager:~/option$ 
``` 

The connectiondata are correct. It would be great if someone can help me.

---

### Post by knippenberg on 2008-07-03
Hi,

Try this in connect.ini

APN = internet
# User
# Pass
PIN = 

PIN is blank!!!

---

### Post by Bukunut on 2008-07-05
Silvermoon.

I strongly recommend that you try Cie's suggestion of the Gui application which works an absolute dream!

 
 HSOconnect Ubuntu 8.04 Step by Step Install
[http://www.pharscape.org/content/view/66/53/](http://www.pharscape.org/content/view/66/53/)

I have been using this Gui for weeks now and find that it works flawlessly instead of using the terminal to fire up the Icon225. The app also keeps a total sum of the MB usage, and allows you to enter your PIN if that is set up. :)

Regards - Bukunut

---

### Post by Bukunut on 2008-07-05
Duplication deleted.

---

### Post by alarichall on 2008-07-23
Oh wow Bukunut, that's really helpful--after no end of struggling, I'm finally online with my icon. Thankyouthankyouthankyou!

---

