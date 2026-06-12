---
title: "Linksys WUSB54GS"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by X40nick on 2007-12-28
Hello.

I have a desktop upstairs running Windows XP Pro. I use a linksys wireless USB adapter to connect to my network. 

I have tried Linux on this computer before, but I still have never got the wireless card to work. 

I am a newbie, and I don't know what to do. How can I get this card working?

Thank you.

Nick.

---

### Post by wieman01 on 2007-12-28
You might want to try the tutorial (Ralink) in my signature. It should work for you as well. Have you got the Windows drivers? If you need a hand, let me know.

---

### Post by wieman01 on 2007-12-28
I found this as well:

[http://ubuntuforums.org/showthread.php?t=516649]("http://ubuntuforums.org/showthread.php?t=516649")

---

### Post by X40nick on 2007-12-29
I don't think my adapter is a "ralink", I have the CD which came with it? 

I will read your tutorial. 

Thank you! And I would be really grateful for all your help.

Nick.

---

### Post by X40nick on 2007-12-29
I have the computer upstairs with Windows XP and I access the internet via the wireless, I can't get access to a wired-on connection. Can I still install the necessary drivers and programs via CD.

Could I download them via Windows XP and then just copy them to a USB drive.

Thanks

Nick.

---

### Post by wieman01 on 2007-12-29
> **X40nick said:**
> I have the computer upstairs with Windows XP and I access the internet via the wireless, I can't get access to a wired-on connection. Can I still install the necessary drivers and programs via CD.

Could I download them via Windows XP and then just copy them to a USB drive.

Thanks

Nick.
A USB drive will do. Or simply insert the CD which Ubuntu should recognize.

---

### Post by X40nick on 2007-12-30
Thanks!

So all I need is the CD containing the driver? Then install Ndiswrapper and it should work?

Nick.

---

### Post by wieman01 on 2007-12-30
> **X40nick said:**
> Thanks!

So all I need is the CD containing the driver? Then install Ndiswrapper and it should work?

Nick.
Pretty much. If you encounter problems, please post here, I'll guide you through this.

---

### Post by X40nick on 2007-12-30
Thanks, I will now go ahead and install Ubuntu. 

I hope it works!!!

Nick.

---

### Post by wieman01 on 2007-12-30
> **X40nick said:**
> Thanks, I will now go ahead and install Ubuntu. 

I hope it works!!!

Nick.
If not, drop me a line. :-)

---

### Post by X40nick on 2007-12-30
Well I did some back research and I have found some not-so pleasing results.

Nobody with that adapter has managed to get it working with Ndiswrapper. And on the wiki the device is not listed.

I have some important data on the HD and I can not install another operating system if the internet doesn't work.

Nick

---

### Post by wieman01 on 2007-12-31
> **X40nick said:**
> Well I did some back research and I have found some not-so pleasing results.

Nobody with that adapter has managed to get it working with Ndiswrapper. And on the wiki the device is not listed.

I have some important data on the HD and I can not install another operating system if the internet doesn't work.

Nick
Bad news... But would you want to give it try anyway? Try to find out what chipset your device has got and follow my tutorial. I'll be there to guide you through it. Perhaps there is a little chance...

---

### Post by X40nick on 2007-12-31
I don't want to install Ubuntu, let go of 40GB of my Windows partition. And then find a operating system that won't connect to the internet. 

I can't seem to find the part of your tutorial that tells me what chipset my adapter has?

Thank you.

Nick

---

### Post by wieman01 on 2008-01-02
Ok, what version of WUSB54GS is it? There is a version number on the backside of the device. The chipset depends on the version number.

---

### Post by X40nick on 2008-01-02
It doesn't say, so I would assume it is Version 1.

Thank you.

Nick

---

### Post by wieman01 on 2008-01-02
> **X40nick said:**
> It doesn't say, so I would assume it is Version 1.

Thank you.

Nick
Odd... sure there is no number anywhere? I think it is a Broadcom BCM4320SKFBG, but I am not sure.

Following a Broadcom tutorial could be an option. This one for instance:

[http://ubuntuforums.org/showthread.php?t=405990]("http://ubuntuforums.org/showthread.php?t=405990")

---

### Post by wieman01 on 2008-01-02
Just came across this thread:

[http://ubuntuforums.org/showthread.php?t=516649]("http://ubuntuforums.org/showthread.php?t=516649")

Check it out.

---

### Post by LastChanceLeeward on 2008-01-02
Did it work?


The Linksys WUSB54GC (not GS) works quite easily with a script.

Take a look as it could help:

[http://ubuntuforums.org/showthread.php?t=516649](http://ubuntuforums.org/showthread.php?t=516649)

---

### Post by X40nick on 2008-01-03
Thank you!

If I download it, copy it to a USB drive. Then move the file to the Desktop is this the "cd" command?

cd /home/nick/Desktop/.wireless

Is that correct? 

Thank you so much! I am really going to give it another try!!!

Nick

---

### Post by X40nick on 2008-01-03
I did try the script, no luck.

I have downloaded the offline installed for the broadcom tutorial.

Nick

---

### Post by wieman01 on 2008-01-03
> **X40nick said:**
> I did try the script, no luck.

I have downloaded the offline installed for the broadcom tutorial.

Nick
Please follow the Broadcom tutorial. I think that's the best shot we've got.

---

### Post by X40nick on 2008-01-03
The offline install doesn't work. 

Can anyone help me as I am really close to going back to Windows.

---

### Post by X40nick on 2008-01-03
I have read the Broadcom tutorial, no luck!

Please help me.

---

### Post by wieman01 on 2008-01-03
> **X40nick said:**
> I have read the Broadcom tutorial, no luck!

Please help me.
What steps have you performed and what error messages did you encounter. Please provide that information, otherwise we cannot help.

---

### Post by X40nick on 2008-01-03
I have followed the tutorials exactly, and it does not work.

I am going back to Windows.

---

### Post by wieman01 on 2008-01-03
> **X40nick said:**
> I have followed the tutorials exactly, and it does not work.

I am going back to Windows.
Fair enough.

---

### Post by X40nick on 2008-01-03
I will get myself another adapter in the Summer, hopefully it will work then.

Thank you for all your help.

Nick

---

### Post by wieman01 on 2008-01-03
> **X40nick said:**
> I will get myself another adapter in the Summer, hopefully it will work then.

Thank you for all your help.

Nick
No problem at all. Wireless adapters can be quite a pain if you happen to own the wrong one. Sorry to see you leave, but hopefully see you again. Before you buy a new adapter, make sure you post here and get advice on compatibility.

---

### Post by lswest on 2008-01-03
what you can also try is using linuxant driverloader (see if you can get it working with the trial, and then pay for it if you need to, it's a one time purchase) and it's on [here]("http://www.linuxant.com/driverloader/")  it got me running a T-sinus 154data when ndiswrapper failed, worth a shot.

---

### Post by X40nick on 2008-01-03
Thanks but I am not going to try it again with this adapter.

I am keeping Ubuntu on my laptop!

Thank you.

Nick

---

### Post by LastChanceLeeward on 2008-01-03
Disclaimer: I am a n00b but I made wireless work on my laptop "with a little help from my friends".

Listen- more power to you if you wanna go back to windows, as freedom of choice is indeed a marvelous concept. On the other hand, I am honestly telling you that you can make this wireless thing work IF you buy the exact correct adapter or be more of a linux wizard than you and I combined times three. So, check the Hardware Compatibility List, and choose what seems the most logical consistent performer, but don't to forget to pray or hope or whatever. I was as frustrated as you seem to be. I thought I was buying smart when I purchased a Toshiba laptop L45-S7423, for $599. However, this otherwise decent laptop has a RealTec 8187b freaking inbuilt wireless chipset that for reasons only known to God is attached to the USB bus. After many hours banging my head on the wall, I realized I had learned valuable info but I was going down a dead-end road. Disheartened, I feared that no wireless internet access is a complete show-stopper for acceptance by anyone approaching the average Joe or Jane. Fortunately, I am a hard head so I persisted.  Furthermore, I decided to work SMARTER not harder by committing up to 50 bucks in my head for another wireless chipset and the addition of painstakingly really spending some time on the darn HC list here

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

I decided to buy the D Link WNA-2330 PCMCIA card from perusing the HCL and local big box availability, as well as reading individual consistent positive comments about actually making the darn thing work. However, before buying the card I actually looked at my laptop and realized I had no PCMCIA slot! WTF? expresscard does not equal PCMCIA and their is very few cards even available for this new "better" technology and no mention of linux. Dismayed, I realized it was USB or nothing baby. So back to the HCL and checking inventory of local big box stores. 49 bucks is what I paid for a Linksys WUSB54GC. Thus, that is my recommendation because I made it work in 5 freaking minutes by myself after following a guru's simple advice, and downloading a script and telling it to run. Good luck. Here is the script if you can part with the dough.

[http://ubuntuforums.org/showthread.php?t=516649:popcorn:](http://ubuntuforums.org/showthread.php?t=516649:popcorn:)

---

### Post by X40nick on 2008-01-04
I will buy a new adapter soon, but I will make sure it will work.

Nick

---

