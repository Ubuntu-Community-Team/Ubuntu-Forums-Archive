---
title: "dialup connection"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by tfrost2002 on 2010-10-07
I am a beginner but have started a new computer with Ubuntu 64 bit and cannot determine how to create a dialup internet connection.  I have searched the archives here but found no help.  I have tried reading and rereading everything that came on the disk but it is not clear how to start a dialup connection.  Any help would be greatly appreciated.  Thank you.

---

### Post by yeats on 2010-10-07
So have you read this?:

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

You'll need to provide some more details for someone to really help you:

1) is the modem detected by Ubuntu?  if not, what kind of modem is it?
2) what have you tried so far?  any error messages?

---

### Post by mastablasta on 2010-10-07
someone decided it might be a good idea to remove dialup access form default ubuntu installation.
 
you could install it if you have another way to connect or download a package somehow in another system then install it in ubuntu:
[http://www.ubuntux.org/how-to-install-dialup-ppp-client-gnome-ppp](http://www.ubuntux.org/how-to-install-dialup-ppp-client-gnome-ppp)
 
How to:
[https://lists.ubuntu.com/archives/ubuntu-users/2010-March/214063.html](https://lists.ubuntu.com/archives/ubuntu-users/2010-March/214063.html)
 
and package i believe:
_[COLOR=#810081][http://packages.ubuntu.com/lucid/gnome-ppp](http://packages.ubuntu.com/lucid/gnome-ppp)[/COLOR]_[]("http://packages.ubuntu.com/dapper/gnome-ppp")

---

### Post by lkraemer on 2010-10-07
tfrost2002,
The easiest way is to purchase an External US Robotics Hardware
Modem from Ebay and use it with your computer. That shouldn't take
you more than 15-30 minutes if you follow the guide at:

[http://ubuntuforums.org/showthread.php?t=1100310&highlight=wvdial](http://ubuntuforums.org/showthread.php?t=1100310&highlight=wvdial)
Posting #4

But, I also understand that you may want to try and use the WinModem that
is already in your machine. So, you're in for a little work, mostly
3-5 days with several emails to Marvin and the fine folks at
[www.linmodems.org](www.linmodems.org) You need to set your email for PLAIN TEXT,
then subscribe to their discussion list. Also you will need to download
their script, execute it, and post the results back for Marvin and those
folks to analyze, then post your method of proceeding.  It isn't an easy
process, but it is possible.

If you don't have a Dialup account, Look for one that works well
with Linux. Copper.net seems to work fine, as I have used it for
several years now. Search forum for "Linux ISP's"

You ONLY need to download and install the following:
1. wvdial & dependencies......

You need to download wvdial and the following dependencies for 10.04,
or your speciific version.
wvdial & dependencies:
```

libuniconf4.6
libwvstreams4.6-extras
libwvstreams4.6-base

```
Located at:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Select 10.04 -> Communications Programs -> wvdial 1.60.3
Download these with XP, then copy the *.deb files to USB Flash Drive,
& then to Ubuntu subdirectory /var/cache/apt/archives & then install
using Synaptic Package Manager.....ie.
```

sudo cp ~/Downloads/mydebs/*.deb /var/cache/apt/archives

```
OR you can go to SYSTEM -> ADMINISTRATION -> SOFTWARE SOURCES
and check the box for installable from CDROM/DVD.........then
insert your LiveCD and install from the CDR.

2. Gnome-PPP
But wait until you have wvdial working before trying anything with
Gnome-PPP.

Or you can download [http://keryxproject.org/download/](http://keryxproject.org/download/) and
use it where you have internet access to get:
```

Gnome-ppp
wvdial

```
(and anything else you want before you get dialup working).

Take those downloaded files to your Ubuntu computer on the USB Flash
Drive.

Then proceed to the guide.

lk

---

### Post by tfrost2002 on 2010-10-10
I appreciate the hardware suggestion and think I will make the purchase of the US Robotics modem.

I appreciate the help from everyone.

Please consider this thread closed.

---

### Post by SeijiSensei on 2010-10-10
This is the one you want: [http://catalog.ebay.com/3Com-U-S-Robotics-Courier-V-Everything-Analog-Modem-3453VAR20-LA-/66731414/r.html?_fcls=1](http://catalog.ebay.com/3Com-U-S-Robotics-Courier-V-Everything-Analog-Modem-3453VAR20-LA-/66731414/r.html?_fcls=1)

I ran some dialup services in the mid-1990's, and these were our modems of choice.  Rock solid, always connects.  At the time we paid about $250 for one of these; they're at eBay for $9 today.  I've still got a couple in my closet!

---

### Post by QLee on 2010-10-10
I agree that the courier is a very stable and solid modem, it was marketed as a "business class" solution and its reliability is probably why it found its way into those modem arrays which were common in the dialup days. I too have one and it still works well today. If you can find one on ebay for a low cost, it might be the most cost effective solution for you.

---

### Post by tfrost2002 on 2010-11-18
As suggested above I bought a US Robotics external modem which would not connect since I had no additional nine pin plug on the motherboard.  So I ordered a USB connector as suggested by US Robotics now I have installed the connector but the program does not recognize the connector or the modem.  

The more I see of Ubuntu the more I find that it is not for newbies.

I don't know what to do now.  I hate Microsoft but at least Windows works some of the time.  

Prior to trying this 64 bit Ubuntu I tried to get 32 bit to work on another pc but it would not install ever after many hours of trial under different situations and with help from forums.  I have over the years gotten valuable help from various forums but most often have gotten off topic chatter and tons of misinformation.  Since some of you are experts I was hoping for this to be easier than it has been.  I ordered Fedora 64 bit thinking I may have better luck with that but it will not install.

I will continue to try using ubuntu but I am very frustrated.  I would also like to point out that suggestions from all of you should consider the recipients knowledge level.  Simple instructions on topic, no shorthand, complete sentences and complete thoughts would be helpful.  

I have no knowledge of Ubuntu, or linux, therefore I am a newbie pleae treat me as such.

Thank you for your help and to those of you who simply offer information without knowledge of what you speak I would ask that you keep it to yourself since hours are spent trying what you offer as knowledge.

---

### Post by roger_1960 on 2010-11-18
Hi

I found the article below which solved my dial up problems - the part about user priviledge settings 

Dial-up Internet Access With A USB Modem
One easy way to connect to the internet using a dial-up
account is to buy a USB modem which the manufacturer
describes as "Linux-compatible".
&#8218;- Install Gnome PPP (available in Synaptic Package Manager)
&#8218;- Access System > Administration > Users and Groups
&#8218;- Access Advanced Settings (enter password)
&#8218;- Open User Privileges Tab
Make sure everything (especially &#8218;-Connect to internet with a
modem&#8218; plus &#8218;Use modems&#8218;) is checked then plug in your
external (USB) Linux-compatible modem [in this example I'm
using a USRobotics USR Model 5637.]
A &#8218; Open Gnome PPP, click on Setup, click on Detect (Gnome
   PPP will then detect the modem), after detection close the
  setup box, and enter your connection information such as
 login, password, local telephone number of ISP and so on.
When connection is established, open your browser and surf!

To end the session and exit, close the browser and click
Disconnect


Hope it helps

Roger

---

### Post by theozzlives on 2010-11-18
I'm not sure USB to serial will work for you. What's plugged into your 9 pin plug? can you use the USB adapter for that? If you can, you could plug the external modem into a REAL serial port. If not, do you have a 25 pin serial that you can get an adapter for?

---

### Post by tfrost2002 on 2010-11-18
Roger,

I do not find Gnome PPP in the synaptic package manager.  I have downloaded the app but do not understand how to install it.

Thank you for your help.

---

### Post by roger_1960 on 2010-11-18
Hi

I'm not certain that gnome-ppp is included in 64 bit Ubuntu - perhaps why you can't find it. Have you got the Universe and Multiverse repositories enabled in system>admin>softwaresources?  Have you looked in the software center - it is there in the 32bit 10.04LTS. You could try installing wvdial instead.  Its similar but commmand line only (no GUI) and more involved.

Have you downloaded a .deb file?  If so it should install by double clicking the file and using the installer which comes up.  If you have downloaded a large group of package files, I'm out of my depth - sorry.

The point of my post was really to make sure that the user priviledges were set, since no software will run a dial up modem unless they are.

---

### Post by jrev on 2010-11-18
We don't have any more serial port on the new computers and that is a pity !

---

### Post by tfrost2002 on 2010-11-19
Gnome PPP and wvdial would not install.  I have forgotten the exact message but if it would help I would try again and post the exact message.

---

### Post by tfrost2002 on 2010-11-19
Can not find this "the Universe and Multiverse repositories" option! User priveledges are enabled.

---

### Post by theraje on 2010-11-19
> **jrev said:**
> We don't have any more serial port on the new computers and that is a pity !

Indeed it is. Of course, a USB modem can work in Ubuntu... it doesn't HAVE to be a serial-modem.

I have a Rosewill RNX-56USB. It's a standard USB dial-up modem, but it is a *hardware* modem. It doesn't require extra software (i.e. Windows drivers) to work. I have used it successfully with Ubuntu.

tfrost2002: How are you trying to access the Ubuntu repositories on your computer?

---

### Post by roger_1960 on 2010-11-21
Hi again

Yes, it would help to know what the error message said.  Were you trying to install from synaptic, software manager or the downloaded files?  Which version of Ubuntu are you using, 64bit 10.10 or 10.04 ?

Roger

---

### Post by Bartender on 2010-11-24
tfrost -
If you're still there, try reading thru my old dial-up thread

[http://ubuntuforums.org/showthread.php?t=1377619](http://ubuntuforums.org/showthread.php?t=1377619)

I tried to make it as straightforward as possible.  That thread is based on using a US Robotics modem.  And yes, you can use an adapter to go from serial to USB.  The Sabrent cable I use is described.

Dial-up is still almost an usable proposition because of the huge updates.  If you can get to broadband every once in a while, or use someone's broadband connection and build PDS'es (also described) it makes life a lot easier

---

### Post by tfrost2002 on 2010-11-26
Bartender,

I tried those things suggested but I have not been successful yet.

Please keep in mind that I am an "absolute beginner".  I don't know how to interpret the responses.  

Thank you for your help it is greatly appreciated.

---

### Post by Bartender on 2010-11-28
> **tfrost2002 said:**
> Gnome PPP and wvdial would not install.  I have forgotten the exact message but if it would help I would try again and post the exact message.

If you're not online they can't download/install.  You probably got an error message saying something like 
"Could not find etc. etc."

If you're new to all of this there are lots of small problems that can trip you up.  I say "small" problems in terms of they're not hard to understand.  If you can't get online that's a big problem, but resolution might entail solving a series of small, understandable problems.

Do you have access to any broadband anywhere?  Getting your PC in front of a broadband connection for an hour or two can make a huge difference!

I mentioned something in the Dial-Up Redux thread that you may have missed.  Until you can get Synaptic to reload the packages one time, it won't find packages.  AFAIK you have only two options - 
1) get to a broadband connection and reload Synaptic so that it knows where it's at, then install gnome-ppp and etc., *or* 
2) start out with pppconfig and make your crappy dial-up connection, then sit there patiently while Synaptic reloads and you find that your PC wants 200+MB of updates.

In case you didn't catch the sarcasm, Option 1 is the better of the two.

- If your dial-up ISP is a Windows-centric one like PeoplePC or Juno you'll be in for heartache
- I'm not familiar with the US Robotics serial to USB but I know the Sabrent works.  There's actually a small chip in the cable, so it may be that the USR chip isn't recognized in Linux.  Who knows if the Sabrent is the same now as it was a few years ago, but the chip was recognized at the Linux kernel level so using it was hassle-free.  I still haven't gotten the Sabrent to work in Windows!!
- thraje's advice re: the Rosewill might be a good option.  I'm glad to hear there are options to scrounging for 20 year old modems.  I've found the old USR's to be a solid device that gives us a better connection than any other external modem I've tried.  But I've only tried a few.


There's one tool that's made dial-up tolerable at home.  I make PDS files from the PC at home, save the PDS to a thumbdrive, then go into town with the laptop and find some broadband.  That's all described in the Redux thread.

Without the ability to get updates and bring them home I don't know what we'd do.  I was gonna say go back to Windows but anymore Windows pummels you with big downloads too and AFAIK there's no simple tool like the PDS.  Plus with Windows you spend half your online time getting malware updates.

EDIT: Are you sure the USR external works?  Can you try it in Windows?  Watch out for under-powered wall warts.  One time I tried to use a generic Radio Shack wall wart that only put out 800 mA.  With the Radio Shack wall wart the USR modem lights came on, so that the modem appeared to be working, but it wouldn't connect.  The genuine USR wall warts put out 1000.

---

### Post by theraje on 2010-11-28
> **Bartender said:**
> - thraje's advice re: the Rosewill might be a good option.  I'm glad to hear there are options to scrounging for 20 year old modems.  I've found the old USR's to be a solid device that gives us a better connection than any other external modem I've tried.  But I've only tried a few.

There are a couple other USB modems that will/should work. USR even makes one of these (but you have to make sure you get the right model. (USR5637 is the model number.)

The trick is to make sure you have a modem with a Conexant chipset. These can be auto-detected by Linux - all you need to do is get Gnome-PPP installed, then set your dialout device as ttyACM0. The device alias may be a little different based on the setup of the computer and/or modem. If so, we can help you figure out the correct alias.

Of course, getting a PPP application installed seems to be the big problem, at the moment...

---

### Post by lhb1142 on 2010-11-28
> **tfrost2002 said:**
> I am a beginner but have started a new computer with Ubuntu 64 bit and cannot determine how to create a dialup internet connection.  I have searched the archives here but found no help.  I have tried reading and rereading everything that came on the disk but it is not clear how to start a dialup connection.  Any help would be greatly appreciated.  Thank you.

If you have not yet succeeded in establishing your dial-up account, here is how to do it.

First go into Synaptic Package Manager < System > Administration > Synaptic Package Manager > (you will be asked for your password).

Next, within the Synaptic Package Manager, go to < Settings > Repositories >.

Within the < Repositories > section you will see several tabs.

Under the first tab (Ubuntu Software), make sure that everything is checked.

Under the second tab (Other Software), make sure everything is checked.

Under the third tab (Updates), the first (upper) section is entitled Ubuntu updates; there are four choices therein. Make sure all four are checked.

Then Close the dialog box. You will receive a message that the Repositories have changed. Close the message. Then click on the Reload button. Once that process is complete, click on Mark All Upgrades.

When that process finishes, enter < gnome-ppp > (just as spelled here without the brackets of course) in the Quick Search box. You should then see the program (along with < gpppon >, a program which is not necessary).

Mark < gnome-ppp > for installation and proceed. Once the process has finished, you can then close the Synaptic Package Manager.

At that point, follow the instructions which were printed here previously by Roger (in fact, I am the author of those instructions which appear in my review of the USRobotics 5637 USB modem on Amazon and which were also printed in Full Circle Magazine; I have reprinted them here with some slight additions):

Dial-up Internet Access With A USB Modem

One easy way to connect to the internet using a dial-up account is to buy a USB modem which the manufacturer describes as "Linux-compatible". (I recommend the USRobotics Model 5637 which, over the year and a half that I have owned it, I have found to be very reliable).

- Install Gnome PPP (available in Synaptic Package Manager) [described above]. After Gnome PPP is installed, follow the instructions below:

- Access System > Administration > Users and Groups

- Access Advanced Settings (enter password)

- Open User Privileges Tab

Make sure EVERYTHING (especially  < Connect to internet with a modem > plus < Use modems >) is checked. Then plug in your external (USB) Linux-compatible modem.

Open Gnome PPP (which you will find under Applications->Internet). Click on Setup. Click on Detect (GnomePPP will then detect the modem).

After detection close the setup box, and enter your connection information such as login, password, local telephone number of ISP and so on.

When connection is established, open your browser and surf!

To end the session and exit, close the browser and click Disconnect.

Please note that you WILL have to have an external USB modem which is Linux-compatible and you will, of course, have to have a dial-up account.

I have had an EarthLink account for many years and both the USR modem and Ubuntu work perfectly with it.

I hope you are able to follow these instructions (which you need do only once) and are successful in effecting your dial-up ISP via your Ubuntu computer.

You will not want to use a dial-up internet connection for updating Ubuntu but, for most other uses, dial-up is fine. Both my wife and I used dial-up when we drove across the country this past summer; in many of the hotels their "high-speed" internet service was slow, spotty, or non-existent. Dial-up was our method for obtaining our e-mail under those conditions.

In conclusion, I hope these instructions have been of help to you and to anyone else reading this who wants a dial-up service either as a primary means of internet access or, as in our case, as a back-up. (If my instructions have helped you, please mark this question as "solved.")

Thank you for reading this.

Lawrence H. Bulk

---

### Post by Bartender on 2010-11-30
> **lhb1142 said:**
> Then click on the Reload button. Once that process is complete, click on Mark All Upgrades.

When that process finishes, enter < gnome-ppp > (just as spelled here without the brackets of course) in the Quick Search box. You should then see the program (along with < gpppon >, a program which is not necessary).

Instructions like these aren't very helpful.  The OP has not got online yet.  "Mark All Upgrades", yeah right that'll fix everything

---

### Post by lhb1142 on 2010-12-01
> **Bartender said:**
> Instructions like these aren't very helpful.  The OP has not got online yet.  "Mark All Upgrades", yeah right that'll fix everything

If he's not online, then how did he post here?

My instructions are perfectly clear; I have posted them elsewhere and have received thanks from people who have followed them and successfully established a dial-up option.

I presume that the person in question has, or has access to, a broadband connection; otherwise he could not have joined this group nor asked his question.

There are many people who wish to be able to access the internet via a dial-up account using Ubuntu in addition to accessing it via broadband (for which Ubuntu is really intended).

I was trying to help the person. Your taking only a small part of my instructions, doing so anonymously, and making a sarcastic comment is of no help to anyone.

Lawrence

---

### Post by tfrost2002 on 2010-12-02
No I do not have broadband access, only dial up (rural living), and my access is with a windows pc.  I hope this helps.  I am trying some of the things suggested but have had no success thus far. 
Thank you for your help.

---

### Post by lhb1142 on 2010-12-02
> **tfrost2002 said:**
> No I do not have broadband access, only dial up (rural living), and my access is with a windows pc.  I hope this helps.  I am trying some of the things suggested but have had no success thus far. 
Thank you for your help.

Dear 'tfrost2002',

One of the things Windows does better than Ubuntu is to make establishing a dial-up internet access account easy. That is because Windows started in the dial-up age and Ubuntu was started only in 2004, well into the broadband era.

That said, once dial-up is activated on a Ubuntu machine, it is quite convenient to access.

You say you are trying some of the things I suggested. I am afraid that is not enough; you must follow ALL of my instructions - and in the order I presented them.

Unfortunately, if you do not have any access to a broadband network (a public library or even a public Wi-Fi hotspot in a store or restaurant), you cannot download and effect the necessary Ubuntu downloads to establish a dial-up account simply because you don't HAVE a dial-up account by which to do it!

I presume then that you have installed Ubuntu from a disc which was mailed to you. If that is NOT the case and you did install it from a DOWNLOADED disc, just take your Ubuntu computer to the place from which the disc was downloaded (a friend's house perhaps?).

If you did get the disc via the mail and you absolutely have no possible means of accessing a broadband connection, there are two pages which MAY help you:

This one < [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware) >

and

this one < [https://help.ubuntu.com/8.04/add-applications/C/offline.html](https://help.ubuntu.com/8.04/add-applications/C/offline.html) > (note that this page refers to an older version of Ubuntu; the link at the bottom for AptOnCD will discuss the latest version, 10.10).

It is going to take some time for you to digest all this information. Access to a broadband account, even if you have to physically drag a desktop computer to that location, would be the best overall means of being able to follow my instructions.

Once you have done all that, you would then have the ability to access your dial-up account.

It is a great pity, in my opinion, that Canonical/Ubuntu has not made this process easier; I'm sure there are many people in the same boat as you are and who would benefit from easily activating and configuring dial-up accounts.

By the way, have you noticed that more and more computers (especially laptops) are now being sold with NO internal modem? It looks as though dial-up may be going the way of the buggy whip.

Have you ever considered investigating satellite internet access which is offered even in places with no wired broadband availability? It's not cheap, but it IS good and reliable.

Another, relatively inexpensive, and MUCH more versatile broadband option is this:

< [http://www.virginmobileusa.com/mobile-broadband/mifi-2200.html](http://www.virginmobileusa.com/mobile-broadband/mifi-2200.html) >

It works anywhere you can get a cell-phone signal (it uses the Sprint 3G network). I bought one for use when traveling and it works very well indeed, almost as fast as our home DSL does (and we can get our e-mail even in our car!). If it were your main internet connection, it would cost $40.00 per month, not too bad when you consider that you can take the little unit (it fits in a shirt pocket) with you anywhere. Even considering the $150.00 price of the unit, for what it does, it is a bargain. Plus, you don't have to use/pay for it every month if you don't wish to do so; you could use it for updating your Ubuntu computer (paying $10.00 for 10 days access, another option) and then go back to your dial-up account (which you would have configured per my instructions when attached to the Virgin Mobile broadband network). Or. if you didn't mind paying $40.00/month, you could drop your dial-up account as you would no longer need it.

All of what I have suggested immediately above costs money and time. I do not know (nor do I wish to know) your financial situation but if you DO have the time and the money to try this, it will definitely work.

If nothing I have said (including those dial-up establishing instructions which must be followed to the letter) is an option for you, you probably would be better off sticking with your Windows computer (with all of ITS attended costs), at least at the present time.

And that would really be too bad ...

I do hope that things work out for you.

Best of luck,

Lawrence

---

### Post by sammiev on 2010-12-02
> **lhb1142 said:**
> If you have not yet succeeded in establishing your dial-up account, here is how to do it.

First go into Synaptic Package Manager < System > Administration > Synaptic Package Manager > (you will be asked for your password).

Next, within the Synaptic Package Manager, go to < Settings > Repositories >.

Within the < Repositories > section you will see several tabs.

Under the first tab (Ubuntu Software), make sure that everything is checked.

Under the second tab (Other Software), make sure everything is checked.

Under the third tab (Updates), the first (upper) section is entitled Ubuntu updates; there are four choices therein. Make sure all four are checked.

Then Close the dialog box. You will receive a message that the Repositories have changed. Close the message. Then click on the Reload button. Once that process is complete, click on Mark All Upgrades.

When that process finishes, enter < gnome-ppp > (just as spelled here without the brackets of course) in the Quick Search box. You should then see the program (along with < gpppon >, a program which is not necessary).

Mark < gnome-ppp > for installation and proceed. Once the process has finished, you can then close the Synaptic Package Manager.

At that point, follow the instructions which were printed here previously by Roger (in fact, I am the author of those instructions which appear in my review of the USRobotics 5637 USB modem on Amazon and which were also printed in Full Circle Magazine; I have reprinted them here with some slight additions):

Dial-up Internet Access With A USB Modem

One easy way to connect to the internet using a dial-up account is to buy a USB modem which the manufacturer describes as "Linux-compatible". (I recommend the USRobotics Model 5637 which, over the year and a half that I have owned it, I have found to be very reliable).

- Install Gnome PPP (available in Synaptic Package Manager) [described above]. After Gnome PPP is installed, follow the instructions below:

- Access System > Administration > Users and Groups

- Access Advanced Settings (enter password)

- Open User Privileges Tab

Make sure EVERYTHING (especially  < Connect to internet with a modem > plus < Use modems >) is checked. Then plug in your external (USB) Linux-compatible modem.

Open Gnome PPP (which you will find under Applications->Interner). Click on Setup. Click on Detect (GnomePPP will then detect the modem).

After detection close the setup box, and enter your connection information such as login, password, local telephone number of ISP and so on.

When connection is established, open your browser and surf!

To end the session and exit, close the browser and click Disconnect.

Please note that you WILL have to have an external USB modem which is Linux-compatible and you will, of course, have to have a dial-up account.

I have had an EarthLink account for many years and both the USR modem and Ubuntu work perfectly with it.

I hope you are able to follow these instructions (which you need do only once) and are successful in effecting your dial-up ISP via your Ubuntu computer.

You will not want to use a dial-up internet connection for updating Ubuntu but, for most other uses, dial-up is fine. Both my wife and I used dial-up when we drove across the country this past summer; in many of the hotels their "high-speed" internet service was slow, spotty, or non-existent. Dial-up was our method for obtaining our e-mails under those conditions.

In conclusion, I hope these instructions have been of help to you and to anyone else reading this who wants a dial-up service either as a primary means of internet access or, as in our case, as a back-up. (If my instructions have helped you, please mark this question as "solved.")

Thank you for reading this.

Lawrence H. Bulk

TY Sir! Worked great. Now just have to get it to with PC-Anywhere. :D

---

### Post by lhb1142 on 2010-12-03
> **sammiev said:**
> TY Sir! Worked great. Now just have to get it to work with PC-Anywhere. :D

You're welcome. I don't know anything about PC-Anywhere but I hope you are successful.

Lawrence

---

### Post by brumman on 2011-03-08
I hope that I am not breaking any forum rules by posting this but I must wholeheartedly agree with 
tfrost2002's comments especially "I am an absolute beginner & I don't know how to interpret the responses." 
As he says, simple instructions on topic, no shorthand, complete sentences and complete thoughts would be helpful.  I cannot understand half of the acronyms being used! This is  supposed to be the absolute beginner forum after all.
 I agree that Ubuntu is still most definitely not user friendly, unfortunately there's no doubt that Linux systems will never occupy anything other than a minute segment of the OS market.  But the afficionados must realise that the majority of people cannot, and don't want to spend their lives tinkering with a computer, they want it simply to work! I hate MS, but on my new machine I have installed Win7 with a dial-up connection and it has been perfect for the past year - none of the old Windows problems at all! 

Now I have used ubuntu (off-line) on a usb stick but had hoped to try going on-line using the Hiro v92 modem - however I assume it will be impossible; but if I did manage it somehow I suppose all the dialer settings would be lost on shut down, or is there a way of saving settings to the USB installation?
If I can test it this way I would then later install Ubuntu either in a new partition or another HD.

---

### Post by wsl on 2011-03-17
Hi,

I am new to Ubuntu. I don't know if it is good to post here for my dialup. 

I installed Ubuntu 6.06.1 Desktop on my old HP Celron 533, 194MB memory. Working nicely and I am happy except dialup. 

My Modem is USB USR detected on /dev/ttyACM0. Now I am trying KPPP. I tried two connections to two different companies but the same problem. 
(These 2 connections work well in my MS Windows system in the same computer and moodem easily.)

 
I am trying modem settings as follows.

Flow control: Hardware
Line termination: CR
Connection speed: have tried 19200, 38400, 57600

I config "Dial" tag, Authentication: to PAP/CHAP, after well dialing up, I got PPP log: 
...[pppd7844]: The remote system is required to authenticate itself  but I couldn't find any suitable secret (password) for it to use to do so....


The better try is set "Dial" tag, Authentication: Terminal-based, and then input my login name and password manually, and then on Login Script Debug Window:

Entering PPP mode.
Async interface address is unnumbered (Loopback0)
Your IP...
Header compression is on.

~...}#@!}!u} &}*.... a lot of these kind of stuff. Around 20 lines. Then,
NO CARRIER

in PPP log:
...[pppd8739]: The remote system is required to authenticate itself  but  I couldn't find any suitable secret (password) for it to use to do  so....



Still can not go online. It is obviously problem on setting but it's almost there. Pls help!

---

### Post by tfrost2002 on 2011-03-18
I am no expert and hope this helps or answers your question because I don't understand any of the string info you provided but I read somewhere the some ISP's will not work with Linux only Windows.  You may need to contact your ISP to see if it works with ubuntu or any other form of non windows os.

Beyond that I have no further idea.  Good luck.

---

### Post by lkraemer on 2011-03-18
tfrost2002,
First thing to do is get wvdial installed.  Did you get wvdial installed?
YES or NO

If wvdial is not installed try this:
Boot up your Ubuntu system.  Then insert your LiveCD and go to
SYSTEM -> ADMINISTRATION -> SOFTWARE SOURCES  and check the box for installable
from CDROM/DVD.........then try installing wdvial from the LiveCD.

Next is to configure wvdial with your ISP's Phone Number, Login, and Password.  Have you done this? YES or NO

To Configure wvdial open a Terminal Window (Console) and do:
```

sudo wvdialconf /etc/wvdial.conf

```
You should get a configuration file something like this at
/etc/wvdial.conf (you may need to add/change a few things...)

wvdial.conf contains:
```

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 48800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyACM0
ISDN = 0
Phone = 4460568
Password = yourpassword
Username = yourusername@yourisp.net

```

Some Dialup ISP's aren't friendly to Linux.  What Dialup ISP are you using?
I use Copper.Net as it works well.  You can search the Forum for
Linux Dialup ISP's for some other suggestions.

Next is to power up your Ubuntu machine WITHOUT the USB to Serial Adapter
inserted into a USB Port.  Then Open a Terminal and Copy & Paste the
following to the Terminal Window (Console):
```

lsusb

```
Then Plug in your USB to Serial Adapter and wait 1 Minute.  Then again do:
```

lsusb
dmesg | tail

```

You should see a difference as your device should be detected.......................

This will return a Manufactuer & Product Number, so use it to get more information.... example.....0a5c:2101...)
```

Bus 008 Device 003: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
Then do:
```

lsusb -v -d 0a5c:2101

```
Gives:
```

Bus 008 Device 003: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         1 Bluetooth
  bMaxPacketSize0        64
  idVendor           0x0a5c Broadcom Corp.
  idProduct          0x2101 A-Link BlueUsbA2 Bluetooth
  bcdDevice            1.00
  iManufacturer           1 Broadcom Corp
  iProduct                2 BCM92045B3 ROM
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          216
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0019  1x 25 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0019  1x 25 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0021  1x 33 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0021  1x 33 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       5
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0031  1x 49 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0031  1x 49 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       254 Application Specific Interface
      bInterfaceSubClass      1 Device Firmware Update
      bInterfaceProtocol      0 
      iInterface              0 
      Device Firmware Upgrade Interface Descriptor:
        bLength                             7
        bDescriptorType                    33
        bmAttributes                        5
          Will Not Detach
          Manifestation Tolerant
          Upload Unsupported
          Download Supported
        wDetachTimeout                   5000 milliseconds
        wTransferSize                      64 bytes
Device Status:     0x0000
  (Bus Powered)

```
Post the output from the above commands.  Can you do this?  YES or NO

We'll go from there.

lk

---

### Post by wsl on 2011-03-19
I was suggested to have new thread but I don't know how to start.

Can't find wvdial in menus in x-window, but in terminal, yes.

After trying wvdial:
sudo pppconfig
sudo wvdialconf /etc/wvdial.conf
sudo edit text/conf:wvdial.conf
(manually key in login name, pw, tel#) 
wvdial /etc/wvdial.conf

Finally... works on Bell's connection well but not on 295.ca's connection.
Well, not easy. Any quick way? Like setup an icom on desktop and click it?

Why KPPP does not work?
Thank you all.

---

### Post by lkraemer on 2011-03-19
wsl,
It's simple.  Click on Absolute Beginner Talk from [http://ubuntuforums.org/](http://ubuntuforums.org/) and then you will see a dark gray
area stating "NEW THREAD" right above "Threads in Forum : Absolute Beginner Talk".

The correct command for editing wvdial.conf should have been one of these:
```

sudo nano /etc/wvdial.conf
gksudo gedit /etc/wvdial.conf

```

You won't find any GUI menu's for wvdial as it is a program that you run in
Terminal Mode directly from the command line.

Once you have wvdial working, and can connect & surf, go to:
SYSTEM -> ADMINISTRATION -> SYNAPTIC PACKAGE MANAGER
and download GNOME-PPP.  Configure it, and you can run it from the GUI (Graphical User Interface).

See Photo's on Posting #4.
They can be used as a guide.
KPPP should also work.

lk

---

### Post by Bartender on 2011-03-21
[QUOTE=wsl Why KPPP does not work?[/QUOTE]

KPPP should work, but you need to download a truckload of dependencies. KPPP is native to KDE and it won't work on GNOME without those dependencies.

---

### Post by jay941 on 2011-07-29
i have two hard drives, both with ubuntu on them. one version has kernal 2.6.32-25-generic and the other has 2.6.32-33-generic on it. the one with2.6.33-25 dials in and connects just right. the other one will dial in and gets stuck saying "waiting for prompt" it nevers goes past that. when i look at the log, it says
"check permissions or specify a PPPD path in wvdial.conf."
the next line says "unable to run /usr/sbin/pppd"
can anyone clue my into what is needed to get my modem working right in the second hard drive.

---

### Post by jay941 on 2011-08-05
i found how to connect to dial up. using terminal, signing in as
root, then running gnomeppp from terminal it works just fine. i am using it now

---

