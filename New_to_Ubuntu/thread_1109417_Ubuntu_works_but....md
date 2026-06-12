---
title: "Ubuntu works but..."
date: 2009-03-28
forum: New to Ubuntu
---

### Post by stone777 on 2009-03-28
Well i now have ubuntu 8.1 working on my pc, except for the modem. 

The modem is a dial up Accent Communications OD-EMS-100 serial modem. It works fine in Windows XP but not with Ubuntu.

I am wondering if i need a general driver or what? After looking at the instructions, there does not seem to be a way to hook this modem up.

It says to go to system > administration > networking. But i have been unable to find this on Ubuntu. Mine does not have networking but 'networking tools'. When this box opens it does not have any dial up modem tools in it, only ethernet tools.

thanks

---

### Post by LiamWilson on 2009-03-28
How is the modem connected? Is it A USB one, or an Ethernet one?

---

### Post by stone777 on 2009-03-28
The modem is a Serial modem connected to a pots phone line.  This is a total dial up phone system. This is not DSL or cable.

The modem is 56k type and the old type of serial connection on the back of my older pc.

thanks

---

### Post by stone777 on 2009-03-28
It seems that the best solution is to find...

gnome-ppp

Perhaps this is some program i need to download off the net?

thanks

---

### Post by hostilejosh on 2009-03-28
there is system > preferences > network configuration which may be what you want.

---

### Post by Temposs on 2009-03-28
This is the standard how-to for dialup modems on Ubuntu:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

I would suggest running wvdialconf from the terminal by opening through Applications->Accessories->Terminal and type:

```
wvdialconf
```

See if this program finds your modem. Or use the ScanModem tool as per this how-to:
[https://help.ubuntu.com/community/DialupModemHowto/ScanModem](https://help.ubuntu.com/community/DialupModemHowto/ScanModem)

If you get the modem identified, try to connect using pppconfig.

I personally recommend the pppconfig method of connecting your modem to the internet, as it has worked for me where other methods have failed. Run this at the terminal:

```
sudo pppconfig
```

Go through the wizard and set up the modem as best you can. When it is finished, type:

```
pon
```

In about a minute, the modem should be dialed up and connected. To disconnect:

```
poff
```

---

### Post by Temposs on 2009-03-28
> **stone777 said:**
> It seems that the best solution is to find...

gnome-ppp

Perhaps this is some program i need to download off the net?

thanks

When I was setting up my Mom's computer, for some reason gnome-ppp wouldn't work, but the pppconfig program that I recommended above did work. But, try both and see what happens. gnome-ppp is prettier :-)

---

### Post by stone777 on 2009-03-28
thanks

If mem serves i tried that and no modem was present. 

I will try gnome-ppp and see if that works. 

Ubuntu 8.1 was installed within Windows xp if that means anything and it gives me a choice at startup to either go Windows or Ubuntu.

i am very clueless when it comes to Linux but if i can get on the net with this thing, then i may try to make it work for most of my computing. 


thanks

---

### Post by stone777 on 2009-03-28
> **Temposs said:**
> This is the standard how-to for dialup modems on Ubuntu:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

I would suggest running wvdialconf from the terminal by opening through Applications->Accessories->Terminal and type:

```
wvdialconf
```

See if this program finds your modem. Or use the ScanModem tool as per this how-to:
[https://help.ubuntu.com/community/DialupModemHowto/ScanModem](https://help.ubuntu.com/community/DialupModemHowto/ScanModem)

If you get the modem identified, try to connect using pppconfig.

I personally recommend the pppconfig method of connecting your modem to the internet, as it has worked for me where other methods have failed. Run this at the terminal:

```
sudo pppconfig
```

Go through the wizard and set up the modem as best you can. When it is finished, type:

```
pon
```

In about a minute, the modem should be dialed up and connected. To disconnect:

```
poff
```

thanks

i will try that, it takes a long time to restart etc. So will have to get back later.

Eventually hoping to get DSL which should be a piece of cake. Dial up modems are probably the hardest way to use Linux if my searches are correct.

---

### Post by Temposs on 2009-03-28
You are correct. Dialup support for Linux pretty much sucks, since most people who develop for Linux these days don't use a dialup connection, and thus have no motivation to develop software for dialup modems.

---

### Post by Temposs on 2009-03-28
> **stone777 said:**
> thanks

If mem serves i tried that and no modem was present. 

I will try gnome-ppp and see if that works. 

Ubuntu 8.1 was installed within Windows xp if that means anything and it gives me a choice at startup to either go Windows or Ubuntu.

i am very clueless when it comes to Linux but if i can get on the net with this thing, then i may try to make it work for most of my computing. 


thanks

Did you install using Wubi([http://wubi-installer.org/](http://wubi-installer.org/)), or did you download and burn to a CD and install that way([http://www.ubuntu.com/getubuntu/download)?](http://www.ubuntu.com/getubuntu/download)?)

Also, it's Ubuntu 8.10, not 8.1. Ubuntu versions go by year and month, so 8.10 was released in the eighth year( 2008 ) in the tenth month ( October ). The version to be release next month is 9.04, released in 2009, in April( 4th month ).

---

### Post by stone777 on 2009-03-28
> **Temposs said:**
> Did you install using Wubi([http://wubi-installer.org/](http://wubi-installer.org/)), or did you download and burn to a CD and install that way([http://www.ubuntu.com/getubuntu/download)?](http://www.ubuntu.com/getubuntu/download)?)

Also, it's Ubuntu 8.10, not 8.1. Ubuntu versions go by year and month, so 8.10 was released in the eighth year( 2008 ) in the tenth month ( October ). The version to be release next month is 9.04, released in 2009, in April( 4th month ).

thanks

Ubuntu sent me a factory made CD and i installed it under Windows XP. 

It must be Ubuntu 8.10

Anyway i tried using pppconfig and it asked me the IP number for your primary nameserver.

Well that drew a blank.

Called the ISP tech and being Saturday you get the endless hold. So may have to try again during the week day.

The tech knows nothing about Linux but claims he can set up an Apple computer.

thanks

---

### Post by stone777 on 2009-03-28
I did find this in the Windows xp when dial up to write this...

server ip address

client ip address

Perhaps this is what the computer wants to know? 

Also using wvdialconf it did find my modem. Is this enough? It also printed out a ton of tech specs.

thanks

---

### Post by Temposs on 2009-03-28
Most dialup services don't use a static IP address. When you're configuring with pppconfig, choose **dynamic** DNS rather than static DNS. Then it won't ask you to enter an IP address.

---

### Post by Temposs on 2009-03-28
Go here:
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-0769b0061bf81bfba710118540bd86223e815761](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-0769b0061bf81bfba710118540bd86223e815761)

Follow the instructions on that page titled: **Alternative Way 2 (using pppconfig & pon/poff)**

---

### Post by Temposs on 2009-03-28
Also, in pppconfig, if you're trying to select something other than what's selected, navigate to the option you'd like to use with arrow keys or tab, and use the **space bar** to select the option that's highlighted.

---

### Post by stone777 on 2009-03-28
> **Temposs said:**
> Most dialup services don't use a static IP address. When you're configuring with pppconfig, choose **dynamic** DNS rather than static DNS. Then it won't ask you to enter an IP address.

thanks Temposs

Just got off the horn with the isp tech and he said to call back on Monday as they have a guy that knows Linux.

The tech didn't know any IP numbers but thought i could find them inside of the Windows xp control panel. 

I will try the Dynamic DNS, thanks.  Last i tried i selected static DNS because i found some numbers on my computer and threw the dice.

Also found the Terminal Server Client and hit the 'dial' button and it gave me an error.

Next is to try Alternative 2. It looks like this method has a better chance of working.

---

### Post by stone777 on 2009-03-28
> **Temposs said:**
> Go here:
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-0769b0061bf81bfba710118540bd86223e815761](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-0769b0061bf81bfba710118540bd86223e815761)

Follow the instructions on that page titled: **Alternative Way 2 (using pppconfig & pon/poff)**

Temposs, i used alternative 2 and all 'seemed' well.

Then when trying to dial up using pon command it gave an error message:

error only members of the dip group can use this command

Apparently i am not part of the 'dip' group and don't know what that is.

Also tried using the gnome-ppp and that was totally hopeless.

I tried selecting the modem manually and that may be my error. The directions says that auto doesn't work too good. 

thanks for the help, i have been trying to use Linux for years and this is the closest i have ever come.

Stone

---

### Post by _duncan_ on 2009-03-29
You can add your user id to the dip group using the following command in a terminal:

```
sudo adduser [COLOR="Blue"]<userid>[/COLOR] dip
```

where [COLOR="Blue"]<userid>[/COLOR] is your own user id without the brackets. So if your user id is 'stone' the command should look this this:

```
sudo adduser stone dip
```

---

### Post by Temposs on 2009-03-29
What duncan suggests should work.

Tell what happens :-)

---

### Post by Maxlite on 2009-04-01
:( Regarding the incentive to develop better dialup software, it's a shame to not have it readily available and easy to install. Some of us still live in areas where our voice comms are still over "tin cans and cotton string". I've been working with Gnome PPP for weeks and have yet to make it work correctly. Connects and disconnects are made easily. But data exchange rates are measured in "bits and bytes" and one "packet" at a time. I can't use Gnome PPP because it is so unbelievably slow. Same thing for wvdial. If I could get a good data rate of exchange and find a good financial software package, I'd dump that **V**ery **I**rritating **S**oftware **T**o **A**ccomodate (VISTA) and the rest of its **M**assively **S**tinky siblings. Anyone have any suggestions for increasing the data exchange rates? Pleeeze.

---

### Post by Temposs on 2009-04-01
Maxlite, in GnomePPP, when you click Setup, what does it say under the Speed setting? Can you make it higher? Does that make a difference in the performance?

Alternatively, you might try pppconfig, which I have detailed earlier in this thread. It works differently from GnomePPP, even though they both have "ppp" in them.

---

### Post by hyper_ch on 2009-04-01
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Maxlite on 2009-04-02
You're right about the subject thing. Please don't be too hard on the 'new kids'.  We're still learning the ropes. BTW, where in the world did you get that ugly 'Satanic' photo posted under your id? That is repulsive to me, no offense intended.

---

### Post by Maxlite on 2009-04-02
Temposs, I apologize for the delay. Too many irons in the fire.
Yes, I did have Gnome PPP maxed on the speed. No, it did not make any difference. I have tried several speeds with no effect, none.

I went to your previous post and then I went through the pppconfig wizard. Now I have a message I've seen before regarding permissions. I think I have inadvertently changed my permissions and now I can't remember how to undo the mistake. Please provide some guidance on the correct string to get my permissions corrected if you can.  Below is what I'm seeing:

Found an USB modem on /dev/ttyACM0.
Modem configuration written to /etc/wvdial.conf.
/etc/wvdial.conf<Warn>: Can't write 'etc/wvdial.conf.tmp6133: Permission denied
/etc/wvdial.conf<Warn>:can't write 'etc/wvdial.conf'
('/etc/wvdial.conf'): Bad file descriptor
ttyACM0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

---

