---
title: "A few noob questions."
date: 2010-12-16
forum: New to Ubuntu
---

### Post by Vhs321 on 2010-12-16
Alright, so to start things off, I am EXTREMELY new to ubuntu, so please keep answers simple and give, if possible, give a step by step for me.

I am trying to run Ubuntu 10.10

Alright, first question. I had downloaded the Windows installer version to install alongside XP. Problem is, my network adapter (Cisco linksys WUSB100 v2) was not even recognized. At all. Nothing could help that.
So I downloaded the AMD64 iso and have it installed on a flash drive to use for now. I can get the adapter recognized now, and it will connect now, but after anywhere between 30 seconds to 2 minutes, it disconnects, and cannot be reconnected unless I unplug it and plug it back in.
Is there a known way to fix this? I have searched other forums with similar questions, but the answer brings me to question #2.

Second question. On both versions (Windows installer and AMD64 on the flash drive) I am unable to install anything.
Even the packets I'm told to install in the fixes, like NDISWrapper, will not install. As if they aren't even there. But, if I search NDISWrapper, it gives 4 results, none of which I can do anything with.
 Same story with all other packets that, from what I understand, are supposed to be on the system.

And lastly, the simplest question. Coming from Windows, I'm used to jumping through a couple of hoops to get something done. But, from what I have experienced thus far, doing just about anything on Ubuntu seems ridiculously complicated, usually involving the terminal.
So, is this what it will be like for all installs and actions, or will it end up being nice and simple?

Thanks.

---

### Post by Rex Bouwense on 2010-12-16
Installing Ubuntu is relatively easy even for a guy like me.  All you need to do is download the ISO (a 32 bit version unless you have a 64 bit system)
The run an MD5Sum on the download:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

If you got a good download.  Then you can burn the ISO to a USB flash drive or CD so you can use that to boot your computer.  You can then try Ubuntu without making any changes to your computer or install it side by side with your Windows OS.  Simple.  It is supposed to be anyway.

---

### Post by joshnielsen on 2010-12-16
> **Rex Bouwense said:**
> Installing Ubuntu is relatively easy even for a guy like me.  All you need to do is download the ISO (a 32 bit version unless you have a 64 bit system)
The run an MD5Sum on the download:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

If you got a good download.  Then you can burn the ISO to a USB flash drive or CD so you can use that to boot your computer.  You can then try Ubuntu without making any changes to your computer or install it side by side with your Windows OS.  Simple.  It is supposed to be anyway.

would booting the installer from a external hard drive be the same as a usb flash drive? because i can boot into my external hard drive i just cant get it to load the installer

---

### Post by Vhs321 on 2010-12-16
> **Rex Bouwense said:**
> Installing Ubuntu is relatively easy even for a guy like me.  All you need to do is download the ISO (a 32 bit version unless you have a 64 bit system)
The run an MD5Sum on the download:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

If you got a good download.  Then you can burn the ISO to a USB flash drive or CD so you can use that to boot your computer.  You can then try Ubuntu without making any changes to your computer or install it side by side with your Windows OS.  Simple.  It is supposed to be anyway.


 Sorry, I should've been more clear. I got it installed alright, and I'm able to boot up fine, its just I have problems once I'm booted up and trying to get things going.

---

### Post by Rex Bouwense on 2010-12-16
I just reread your post and I'm not sure where I got the wrong idea but here we go again.  Did you install Ubuntu along side of Windows or did you install it inside of Windows using WUBI?

---

### Post by Frogs Hair on 2010-12-16
What are you trying to install or get running ?

---

### Post by garr111hotmail.com on 2010-12-16
I think that it depends on what you want to install. If you like to install common programs like a racing game, the Software center in the applications menu has a lot of useful programs and they are really simple to install. But, there are a few programs that are difficult to install. I think that it is about as easy as windows.

---

### Post by Vhs321 on 2010-12-16
What I am trying to do is get the internet connection operational.

I first installed it alongside windows (I believe, I was given the choice to boot into either Ubuntu or Windows when the computer was turned on, so whichever that is) and then, when that seemed to not work, I installed the regular (64 bit) version onto a flash drive, which I can boot from into Ubuntu.

In either installation, I am unable to get any sort of real network functionality (I am using a WUSB100 V2 network adapter). When booting from the flash drive, I can connect, but only for a few moments before it drops the connection.
In the hard drive installation, Ubuntu doesn't recognize that there is a network adapter plugged in at all.

I've looked online, and, in the case of the hard drive installation, the solution seemed to be a program called NDISWrapper, but I cannot find the file on the system. Even with the terminal, it said the file was not there. This, I found in both cases (The flash drive installation, and the HDD one). So I tried other measures to get it operational, on both installations, and came to the conclusion that I am unable to install any of the programs referenced in most of the networking threads I've read.

So, now I am confused. Are these programs (In this case, NDISWrapper) already on the OS, and I am just having alot of trouble for some reason, or is there a source I should download and transfer any necessary programs from?

If there are any possible solutions, or if you could point me in a new direction, it would be greatly appreciated :D

Thank you for your time so far.

---

### Post by RedRat on 2010-12-16
If you are a newbie, I would suggest that you might want to go with Ubuntu 10.04 LTS. Usually, the LTS versions are a bit more stable while the 6 month updates sometimes tend to present problems. After you have a few months of Ubuntu under your belt, then you might want to try the upgrade, but keep in mind that these are basically "beta testing" of the system.

---

### Post by Vhs321 on 2010-12-16
Alright, Ill try that, thanks.

---

### Post by mastablasta on 2010-12-17
ok first off leave Wubi... (you already gave up on it).
 
next how did you install to USB drive? if you installed using unebooting or similar programme then you are only running a live version and not a porpper install. live version can act and behave differently.
 
as for you internet trouble, have you tried checking in the hardware drivers application for any proprietary drivers available?

---

### Post by Vhs321 on 2010-12-17
Same story with 10.04.

Can't get any network functionality. Was able to install it to the HDD, same story as 10.10 on the HDD. No recognition the network adapter was even there.

I was unable, however, to install it successfully on the flash drive. Made several attempts, tried formatting, no dice. Wont let me boot from it.

Are there any other possibilities?

---

### Post by Vhs321 on 2010-12-17
> **mastablasta said:**
> ok first off leave Wubi... (you already gave up on it).
 
next how did you install to USB drive? if you installed using unebooting or similar programme then you are only running a live version and not a porpper install. live version can act and behave differently.
 
as for you internet trouble, have you tried checking in the hardware drivers application for any proprietary drivers available?

I used the Universal USB Installer as the Ubuntu website directed. Is there something else I should be using?

Anyway, no, there were no drivers available, and I cant install any drivers that I have.

---

### Post by waynefoutz on 2010-12-17
Sorry you are having problems. What you are going to have to do is get it connected to the internet somehow, probably with a hard wire directly into your router. Once you establish a connection, open up "Synaptic Package Manager" in the System/Administration menu, and hit the "reload" button. When it's finished, try System/Administration/Hardware drivers again (if you did it before. You should see drivers listed this time. If there are more than one, try each one until your Wifi adapter works. I'm betting it can't find the drivers because it hasn't downloaded them yet.

If you don't find one at all, while you are connected to the internet, install "ndisgtk" in synaptic package manager. Then find the Windows driver for that particular wifi adapter. copy the .inf file to a spot on your ubuntu drive, probably your /home folder. Open the ndiswrapper utility in the menu, it will be there after you install it. Point the utility to the .inf file. That's another way to get it going.

---

### Post by Vhs321 on 2010-12-17
Thanks, I'll try that as soon as I can.

---

### Post by RedRat on 2010-12-17
When you boot from the LiveCD for 10.04LTS do you get network connectivity? Can you use Firefox to go out onto to the net? If you cannot, there might be a problem with your network adapter in your machine.

While I am not entirely sure about this but your network adapter (Cisco linksys WUSB100 v2) should work with Ubuntu. That is a fairly common adapter. I use Linksys routers in my system and have never had a problem.

---

### Post by waynefoutz on 2010-12-17
> **RedRat said:**
> When you boot from the LiveCD for 10.04LTS do you get network connectivity? Can you use Firefox to go out onto to the net? If you cannot, there might be a problem with your network adapter in your machine.

While I am not entirely sure about this but your network adapter (Cisco linksys WUSB100 v2) should work with Ubuntu. That is a fairly common adapter. I use Linksys routers in my system and have never had a problem.

the problem is, is that they can only squeeze so much data on a 700 megabyte CD, so drivers for less popular Wifi adapters don't make the cut. A quick reload in Synaptic or typing "sudo apt-get update" in the terminal while the computer is connected to the internet usually does the trick.

Another option is to download "SuperOS" from this site:

[http://hacktolive.org/wiki/Super_OS]("http://hacktolive.org/wiki/Super_OS")

All SuperOS is is Ubuntu, but it's on a DVD, so it has a lot more software installed out of the box, and a lot more drivers. You'll also get the added benefit of having Adobe Flash, Java, and DVD playback installed and ready to go. Honestly, that would be the way I would go if I were new. Heck, I've been using Ubuntu for years, and I use SuperOS because it saves a lot of time configuring things after the install.

---

### Post by mastablasta on 2010-12-18
> **Vhs321 said:**
> I used the Universal USB Installer as the Ubuntu website directed. Is there something else I should be using?


Unetbootin
or perhaps even better is Linux Live USB creator.

as suggested your first conneciton will need to be with a wire to get the porpper drivers from the net.

---

### Post by Vhs321 on 2010-12-18
@RedRat: I can't boot the liveCD of 10.04 at all for some reason. Tells me something about a bad or missing configuration file, but redownloading and reinstalling didn't help.

@Waynefoutz: downloading now, hopefully will work out better.

@Mastablasta: downloading those now.


Thanks for all the help, it's much appreciated.

---

### Post by RedRat on 2010-12-18
> Re: A few noob questions. 			 			 			 		   		 		 		@RedRat: I  can't boot the liveCD of 10.04 at all for some reason. Tells me  something about a bad or missing configuration file, but redownloading  and reinstalling didn't help.

Oh, oh. There is something wrong here with either your computer setup (perhaps via the BIOS) or the LiveCD burn. While the appropriate drivers may be at fault here, your network adapter, being a Cisco/Linksys, out to work, it is not really all that exotic, but then I might be wrong about that. Definitely try the DVD version and larger software download. If you can boot to the 10.10 and not the 10.04, I would say something is wrong with the burn.

---

### Post by albert s on 2010-12-18
I would definately suggest a hard wire to the internet either while booting the CD or when first trying to set up the system,
that way all the relevant updates and drivers get installed.

---

### Post by Vhs321 on 2010-12-18
Alright, I have a full install running now (running 10.10 because of the difficulties I was having with 10.04) and have a hardline running for now.

Got NDISWrapper set up and got a driver installed, but it just says that it's connecting for a while, and then just asks for the password repeatedly.

On another note, there is a bit of random stutters and freezes going on occasionally. Should I be concerned about this or is it normal?


EDIT: It could've been a bad burn. Ill try once again to get 10.04 running.

---

### Post by Vhs321 on 2010-12-20
Alright, running, 10.04, I cannot get any wireless connectivity even with drivers installed. Does not even register that there is a network adapter.

Any solutions, or should I got back to 10.10?

---

### Post by waynefoutz on 2010-12-21
> **Vhs321 said:**
> Alright, running, 10.04, I cannot get any wireless connectivity even with drivers installed. Does not even register that there is a network adapter.

Any solutions, or should I got back to 10.10?



Well, I'm at a loss. 

Sometimes the easiest fix in a situation like this is to get a different wireless adapter. Like others have said, yours is not that uncommon, if you do a little bit of googling, others have gotten it to work. I had one that would not connect to a WPA encrypted network in Ubuntu, I ended up replacing it. $20 fix.

---

### Post by Vhs321 on 2010-12-21
Alright then, that seems to be the easiest solution at this point, I've exhausted google of solutions by now.

Thanks for all the help you guys have given me.

---

### Post by gordintoronto on 2010-12-21
> **Vhs321 said:**
> Alright, running, 10.04, I cannot get any wireless connectivity even with drivers installed. Does not even register that there is a network adapter.

Any solutions, or should I got back to 10.10?

It's a lot easier to help you if you say, "I did A and B and C and expected result X, but Z happened instead." You're telling us about results, but we're not sure what evidence those results are based on. For example, did you run the command:
lsusb
which lists the USB devices on your computer?

---

### Post by Vhs321 on 2010-12-21
Alright, I'll try to be more descriptive.

Running lsusb reveals that it is there (simply says 'linksys'), however even installing drivers (RT2870, cannot find the RT30xx drivers described in other threads) cannot get it listed as a network device from which to pick a connection.

---

### Post by RedRat on 2010-12-21
> **Vhs321 said:**
> Alright, running, 10.04, I cannot get any wireless connectivity even with drivers installed. Does not even register that there is a network adapter.

Any solutions, or should I got back to 10.10?
Are you trying to install this on desktop or laptop or netbook? You might have mentioned this but I forgot. This is indeed odd. If you know someone, perhaps you can borrow a network adapter card (if in a desktop) and see if it works. 

You said that you finally got 10.04 installed over your 10.10 installation. Did you figure out what prevented the 10.04 installation? Was it a bad copy or bad burn?

I have an old desktop with a very cheap network adapter (it is a no-name brand that I got for less than $20)  in it that is now about 5 years old and 10.04 from the LiveCD easily finds it and connects to the internet. 

If you are trying to install Ubuntu on a laptop or netbook, things can get a bit tricky on these machines due to proprietary drivers. For example, I have seen it written here by System76 guys that trying to install Mint on one of their machines might not be possible. This seems to indicate that compatibility can be an issue.

---

### Post by Vhs321 on 2010-12-21
Yeah, I'm running it on a desktop.

My best guess was that it was either a bad download or burn. Don't know which, since I swapped out both the download file and the burn program.

I'm going to get a new network adapter as soon as I can, since it could be the problem. (Even when it got recognized and installed before, it would only connect for a minute or two)

---

### Post by RedRat on 2010-12-21
> **Vhs321 said:**
> Yeah, I'm running it on a desktop.

My best guess was that it was either a bad download or burn. Don't know which, since I swapped out both the download file and the burn program.

I'm going to get a new network adapter as soon as I can, since it could be the problem. (Even when it got recognized and installed before, it would only connect for a minute or two)
Before you run out and buy one, check Google for compatibility with Ubuntu as others have mentioned here. Try to find out what chip set is used in the adapter card, you might want to peruse online stores like Newegg or a few others to see if they have info on chip sets. I suspect that the adapter might be faulty in some way. Have you tried it wired directly to your router/modem using a network line?

---

### Post by Vhs321 on 2010-12-21
Yeah, I have it running straight to the router so I can get internet when I boot into Ubuntu.

---

### Post by RedRat on 2010-12-22
> **Vhs321 said:**
> Yeah, I have it running straight to the router so I can get internet when I boot into Ubuntu.
OK, if this connection drops in a minute or two, or even longer than that, I would say it indicates a faulty network card. There is a second rather distant possibility that your router/modem, for one reason or another is giving your computer a new dynamic address. Usually, your computer is assigned an internal router address, e.g., 192.XXX.XXX.002 or something like that. Usually as long as you don't disconnect your computer that address stays the same, even if you turn off the computer. This is why I suggest that you find a friend and try to borrow his/her network card and see if the problem goes away. Try that before dropping $20 or so for a new card.

---

