---
title: "BT Business Broadband HSDPA"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by hoggson on 2008-11-12
BT have changed their Business Broadband packages to include free mobile broadband (HSDPA @ 7.2Mbps) to all option 2 & 3 customers :)  Good news, until I received my HUAWEI E170 and tested it.  On my Vista box it worked fine, then I plugged it into my Ubuntu laptop, what it was intended for.

First problem was that it does not load the storage, so you cant get the dialer to run or look at the files for any settings etc.  I put the SIM in my Vodafone Nokia, and it worked fine... so their network is Vodafone.  I put the SIM back in the dongle... told Ubuntu 8.10 it was a Vodafone Contract connection.  This did not work.

So i rang BT, who told me that it did not work in Linux at all, and I should give up.  After arguing with them for a while I managed to get them to tell me the settings, which they seemed reluctant to do. They gave me the username and password my router uses, and told me to put something I forget into the APN.  This did not work.

Then I rang BT Business Mobile, who were very nice :)  I deleted the connection and started again.  I used the Vodafone (contract) setting that Ubuntu 8.10 offers (this ended up setting the DNS servers which BT Mobile did not know).  Then I put in the following setting they supplied:

Dialup Number:   *99#            (default setting put in by Ubuntu)
User:            bt
Password:        bt
APN:             btmobile.bt.com
DNS:             10.206.65.68    (default setting put in by Ubuntu)
                 10.203.65.68    (default setting put in by Ubuntu)

Now the connection work fine :)  And BT asked me for the details of the version of Linux I was using, and any other information that will help them to help other Linux users.  Which is good, as they offer no support at all for Linux users as I have sadly discovered in the past, and been very annoyed about.

Hope this helps anyone with the same problem with BT Business Mobile Broadband.

---

### Post by steve_d on 2008-11-21
Good news for anyone using this usb stick, Can you tell us who the manufacturer is of this usb stick, or the chipset being used and version numbers?

If it worked relatively 'out of the box' maybe post lsusb -v and we'll have some numbers to look at.

Thanks
Steve

---

### Post by hoggson on 2009-03-11
Apologies Steve, but I have leant this USB stick to a friend so they can get on the net; however the stick is a HUAWEI E170.  Hope this helps.

Rob

---

### Post by ngarner on 2009-05-05
BT have started doing a Home Mobile Broadband service that ships with a Huawei E180 modem. I am trying to use this modem from Ubuntu 9.04 but am having a few problems. 

I tested the modem by plugging it into a Windows PC, installing the 'BT Connection Manager' application and activating the SIM. All worked fine and was pretty easy. I also rang up BT Mobile Broadband support and they confirmed that the APN/Username/Password are the same as for BT Business Broadband. (See above). The only difference being that no DNS servers should be entered (Windows listed one DNS of 10.205.65.68). 

When I try to connect with Ibex I get one of two situations occuring. First being that I am prompted for a password, while the second is just a 'GSM Network Disconnected' message. 

Does anyone happen to know if there are some specific authentication, PIN or other such configuration that needs to be enabled to make it all work? 

Many thanks

---

### Post by Robsmac on 2009-05-19
Hi I have similar problem with my MAC OS  X 10.5.6 and using the E180 Huawei USB modem when trying to connect to BT Mobile Broadband.
I have so far downloaded new drivers to get the Mac to recognise the modem.

Can anyone tell me the settings for Telephone number, Username, Password, APN to connect to BT home Mobile Broadband.
Details of the BT offering are at: [http://www.productsandservices.bt.com:80/consumerProducts/displayCategory.do?categoryId=CON-MOBILE-R1](http://www.productsandservices.bt.com:80/consumerProducts/displayCategory.do?categoryId=CON-MOBILE-R1)

I have tried various settings obtained from the internet including the ones above but keep getting disconnected.

My MAC says I have a Vodafone signal with the E180 so if I can get the settings above correct we are away.  BTW  it all works fine from a PC running Vista but I want to use it on a MAC !!!
BT say they dont provide support for Macs !!! cheers

---

### Post by frankdjs on 2009-05-22
Hi RobsMac,

The details for the BT Mobile Broadband Home dialer are:

Dial Number(default is "*99#")                                   *99***1#      
User Name(default is blank)      bt    
Password(default is blank)       bt    
APN     btmobile2.bt.com       
Authentification(CHAP or PAP,default is CHAP)    CHAP  

BT will shortly (next couple of weeks) be bringing out a Mac Specific dialer, but in the interim you can use these details for the Huawei dialer.

Good luck.  I got it to work with my mac.

Rgds
Frank (BT Employee)

---

### Post by GemmaRay on 2009-05-27
Hi everyone,

Did a search online trying to see if my new BT mobile broadband Huawei E180 dongle works with my mac and it brought me here.

I have bought TV, broadband and a phone package with BT and was due to have the phone line installed today.  However, the engineer couldn't find the wire and we have no telephone socket so he left baffled.

I am desperately in need of getting the internet set up due to work commitments and though the mobile dongle might work and solve the problem in the interim before another engineer can come out and install the phone line.  However, when I plug it into my computer a CD icon comes up which is completely blank.  I have tried verifying it using the disk utility function but it is still blank.

I noticed some people on here work for BT and so far every time I try to call and get some help it sounds like I just get someone completely clueless in Bangladesh!  It is like banging my head against a brick wall as nobody understands.

Can anyone explain to me if this will work in my Macbook Pro?  Its on Mac OS X version 10.4.11.

I would be eternally grateful if anyone can help me out.

Thanks so much for reading

Gemma

---

### Post by JoeHay on 2009-05-29
Hi everyone,

I've recently switched to BT broadband and ordered a mobile dongle. I've plugged the dongle (HUAWEI E180) into ubuntu and it registers it ok, although I 've not tried logging on to it though.

However, nothing happens at all when I plug it in to my MAC? Tried looking for drivers/dialers on the net but I've drawn a total blank.

Can anyone help?

Frank, is the plan still for BT to release a MC dialer for the dongle? I spoke to the helpdesk today and I was told that no support is planned.

Thanks in advance.

Joe.

---

### Post by JoeHay on 2009-05-29
I've tried running parallels desktop (on my macbook) and then installing XP on it, but still can't get the card to register. Would it work with installing ubunutu on parallels desktop?

Cheers,

Joe.

---

### Post by toystoryii on 2009-06-01
Hi Ubuntu users,

I finally got my BT Huawei E180 working in Ubuntu.  My version is Linux version 2.6.28-11-generic. (/proc/version)

Out the box I plugged the e180 into a Vista box, registered my details on [www.bt.com/account](www.bt.com/account) and went through the registration process.  After vista had finished installing loads of junk, it give me a PIN number which i was to enter on the bt.com site to activate the e180.  After all this, it was all working and I was able to surf pages no problem.

Now onto Ubuntu!

First of all I removed my sim out of the e180 and put it into a unlocked phone (but a Vodafone locked phone will also do, as BT use Vodafone for their service, very strange as BT used to own BT Cellnet which eventually became o2, I guess no loyalty since offcom cut the pie in half anyway...) and made sure the security for the PIN request was off.  After pluggin it back in Ubuntu detected it was a GSM Device, i went though the wizard and selected Vodafone pre pay.

Once this is all done, leave the e180 plugged in and right click on your network icon in the task bar and go to edit connections.  Get to mobile broadband, select the device and goto edit

Try these details...

**Mobile Broadband**

Number: *99#
Username: bt
Password: bt

APN: btmobile2.bt.com
Network: (blank)
PIN: (Blank)
PUK: (Blank)

**PPP Settings**

Configure Methods only have CHAP ticked

Tick 
Allow BSD, Allow Defalte Data, User TCP Header Compression

**IPv4 Settings**

Method should be Automatic (PPP)

When you have a connection you should have a solid blue light, and if you use it for a while it can keep you warm if you put it in your pocket.

Hope this helps someone

---

### Post by JoeHay on 2009-06-03
Cheers toystoryii,

With your settings I managed to get the broadband working on both ubuntu and mac os x now!

Much appreciated!

Cheers,

Joe.

---

### Post by ngarner on 2009-06-10
Thanks a lot for those settings, they worked a treat on Ubuntu 9.04. When I previously asked for the settings from BT they gave me btmobile.bt.com as the APN which was the root cause of my issue.

Cheers

---

### Post by jamesdew on 2009-06-17
> **ngarner said:**
> Thanks a lot for those settings, they worked a treat on Ubuntu 9.04. When I previously asked for the settings from BT they gave me btmobile.bt.com as the APN which was the root cause of my issue.

Cheers

Mine too, I missed out the 2 on btmobile2.bt.com thanks for all the info everyone!

---

### Post by RogerMort on 2009-06-24
> **Robsmac said:**
> Hi I have similar problem with my MAC OS  X 10.5.6 and using the E180 Huawei USB modem when trying to connect to BT Mobile Broadband.
I have so far downloaded new drivers to get the Mac to recognise the modem.

Can anyone tell me the settings for Telephone number, Username, Password, APN to connect to BT home Mobile Broadband.
Details of the BT offering are at: [http://www.productsandservices.bt.com:80/consumerProducts/displayCategory.do?categoryId=CON-MOBILE-R1](http://www.productsandservices.bt.com:80/consumerProducts/displayCategory.do?categoryId=CON-MOBILE-R1)

I have tried various settings obtained from the internet including the ones above but keep getting disconnected.

My MAC says I have a Vodafone signal with the E180 so if I can get the settings above correct we are away.  BTW  it all works fine from a PC running Vista but I want to use it on a MAC !!!
BT say they dont provide support for Macs !!! cheers

Would you be kind enough to post a link to the relevant driver? I'm using a MacBook Pro running 10.5.7

---

### Post by StefanKrause on 2009-08-09
[FONT=Verdana]BT Dongle E170 under Linux on CnMBook[/FONT]
 


[FONT=Verdana]Hi, I bought a CNMLifestyle Minibbook just now from Maplan for £80 with Linux which is my first contact with this 'outside Bill Gates world'. This remembers me as I started with an Atari 800XL and all others had a C64. ooops, back to the facts:[/FONT]

[FONT=Verdana]However, after few tests I visited the supplier's website and uploaded few applications but very soon all stopped to get internet access if no wifi is available.[/FONT]
[FONT=Verdana]I have a BT Dongle E170 and wanted to try to get this up and running here.[/FONT]
[FONT=Verdana]As a convenient user I plugged in the USB stick and waited the magic minute and nothing happened. [/FONT]
[FONT=Verdana]I tried again and searched the handbook. There's everything fine and no issues with USB. I had a problem and no idea. So, I started search in forums. And with trials and your advice - here's the solution:[/FONT]

[FONT=Verdana]Update V70 CNMLifestyle Minibook from [www.cnmlifestyle.com]("http://www.cnmlifestyle.com") with the info / patches for mobile broadband. Do it independently from the advice on the website that those are already installed. Believe me, they aren’t. I tried everything and wrote my fingers hot to get advice. [/FONT]
[FONT=Verdana]I am not an expert but if nothing works – I start to try. I figured out that my mini notebook responded on all installations ‘add success’.[/FONT]
[FONT=Verdana]As this was done – The BT broadband dongle E170 was first time recognised from my minibook.[/FONT]
[FONT=Verdana]The Wireless Connection Wizard appeared with a range of empty fields which I couldn’t answer but the following input resolved all issued:[/FONT]
 
[FONT=Verdana]Device: GPRS[/FONT]
[FONT=Verdana]Phone Number / Dialup Number: *99#[/FONT]
[FONT=Verdana]Account / User: bt[/FONT]
[FONT=Verdana]Password: bt[/FONT]
[FONT=Verdana]APN: btmobile.bt.com[/FONT]
[FONT=Verdana]Primary DNS: 10.206.65.68[/FONT]
[FONT=Verdana]Secondary DNS: 10.203.65.68[/FONT]
 

[FONT=Verdana]I am absolutely delighted that I am now connected too .[/FONT]

[FONT=Verdana]Thank you all here for your big help.[/FONT]

[FONT=Verdana]regards,[/FONT]
[FONT=Verdana]Stefan[/FONT]

---

### Post by b1ackcr0w on 2009-08-21
Sometimes BT's DNS servers can be *ahem* less than 100% reliable. You might find on several of the BT dongles that you get a nice blue light, everthing seems to work fine, but it won't look up web pages.
 
One solution I found when my E180 did this was to use somebody else's DNS servers. Specifically Open DNS.
 
If you hoik out the standard or BT supplied DNS adresses, and replace them with:-
 
Pri 208.67.222.222
Sec 208.67.220.220
 
You should find things work swimmingly. (in fact, with the exception of their Wonky DNS, their Mobile Broadband is generally scorchio quick).

---

### Post by ehajri on 2009-11-03
I had a similar problem. My Huawei E620 used to work until last night when I upgraded Ubuntu8 to 9.04, after that the connection is established but there is no internet. Had a tough time until I found toystoryii's post. It indeed fixed my problem. Many Thanks

---

### Post by ben1828 on 2010-05-28
This was esactly the thread I was looking for.. unfortunately it hasn't got me a result! :)
 
Have a BT Huawei E270 which has been working fine on Win7 on this machine. Having installed Ubuntu 10.04 (on the same machine) I am experiencing difficulty in achieving a successful connection. BT are telling me they don't officially support Linux (they have an app that installs on Windows) and I'm on my own.
 
I have followed the suggestions above (ensuring that the '2' is in the APN address). The error message I receive is "GSM Network. Disconnected - you are now offline"
 
I haven't installed any extra drivers or packages. When I first connect the device, it flashes green twice, then slowly flashes blue - indicating that it's connected and can see a signal.
 
Bit of a loss here - any pointers?
 
Thanks

---

