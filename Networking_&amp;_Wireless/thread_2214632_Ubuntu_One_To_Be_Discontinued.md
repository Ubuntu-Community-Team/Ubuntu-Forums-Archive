---
title: "Ubuntu One To Be Discontinued"
date: 2014-04-02
forum: Networking &amp; Wireless
---

### Post by Roasted on 2014-04-02
Haven't seen any other posts and figured it was worth spreading the word so users are aware.

[http://blog.canonical.com/2014/04/02/shutting-down-ubuntu-one-file-services/](http://blog.canonical.com/2014/04/02/shutting-down-ubuntu-one-file-services/)

> As of today, it will no longer be possible to purchase storage or music from the Ubuntu One store. The Ubuntu One file services will not be included in the upcoming Ubuntu 14.04 LTS release, and the Ubuntu One apps in older versions of Ubuntu and in the Ubuntu, Google, and Apple stores will be updated appropriately. The current services will be unavailable from 1 June 2014; user content will remain available for download until 31 July, at which time it will be deleted.

---

### Post by SuperFreak on 2014-04-02
That seemed somewhat shortlived. When did Ubuntu One start 2010?
I have doubts about a lot of these cloud based services

---

### Post by kurt18947 on 2014-04-02
> **SuperFreak said:**
> That seemed somewhat shortlived. When did Ubuntu One start 2010?
**I have doubts about a lot of these cloud based services**
Roasted, thank you for the heads up.
I'm skeptical about 'cloud' services as well, particularly the free ones.  There are certain unavoidable expenses associated with such offerings.  The bills have to be paid somehow.  Then there are the privacy and security concerns.

---

### Post by marco-parillo on 2014-04-02
[http://blog.canonical.com/2014/04/02/shutting-down-ubuntu-one-file-services/](http://blog.canonical.com/2014/04/02/shutting-down-ubuntu-one-file-services/)
Dated: 2[SUP]nd[/SUP] April 2014

Also:
[https://one.ubuntu.com/services/shutdown/](https://one.ubuntu.com/services/shutdown/)

---

### Post by CharlesA on 2014-04-02
Threads merged. Kinda makes me glad I use ownCloud if I want to share stuff or have it easily accessible.

---

### Post by stalkingwolf on 2014-04-02
the question is how will that effect sign in here as that is in some way tied to ubuntu one?   Is this error some way tied to the end of ubuntu one?
ERROR
The requested URL could not be retrieved

The following error was encountered while trying to retrieve the URL: [http://ubuntuforums.org/](http://ubuntuforums.org/)

    Unable to forward this request at this time.

This request could not be forwarded to the origin server or to any parent caches. The most likely cause for this error is that the cache administrator does not allow this cache to make direct connections to origin servers, and all configured parent caches are currently unreachable.

Your cache administrator is webmaster.

now also have errors posting replys, with personal messages, and getting logged out.

---

### Post by coffeecat on 2014-04-02
> **stalkingwolf said:**
> the question is how will that effect sign in here as that is in some way tied to ubuntu one?   Is this error some way tied to the end of ubuntu one?

This is already covered in the link in the OP.

> 
Shutting down Ubuntu One **file services**

My bold, and...

> The shutdown will **not affect the Ubuntu One single sign on service**, the Ubuntu One payment service, or the backend U1DB database service.

My bold again.

The errors you experienced may have been due to an unexpected brief problem with mysql which sysadmins had to deal with urgently - hence the lack of warning. I was offline myself when this happened so I have no further details myself at this time, but we would hope to communicate anything of importance if there is anything further to report.

---

### Post by PaulW2U on 2014-04-02
As a Kubuntu user any integration with my OS was simply not there.

I always saw it as a free service, nothing more, nothing less, as my remote storage requirements were always very basic. I wonder how many users actually paid for an enhanced service that would have helped to make the service profitable?

Time to move on.........

---

### Post by Linuxratty on 2014-04-02
> **CharlesA said:**
> Threads merged. Kinda makes me glad I use ownCloud if I want to share stuff or have it easily accessible.
 Over at LI,three of us tried this and were not impressed. 
It's a shame about  Onecloud,but i also do not trust cloud services any further than i can fling a bull elephant.

---

### Post by pqwoerituytrueiwoq on 2014-04-02
> **CharlesA said:**
> Threads merged. Kinda makes me glad I use ownCloud if I want to share stuff or have it easily accessible.I think i need to do this, also think i should get that rasberry pi now
have a guide? and a ubuntu client (i don't need windows support)
edit thought you said you made your own, maybe owncloud is software to make your own or a service, time to goolge

---

### Post by KBD47 on 2014-04-02
I think it is a shame it's closing. I bought some music and used the storage as extra back up. It worked good on android for me, and I kind of trusted them a bit more to watch out for my privacy than some other cloud storage services. It causes me concern, because as Ubuntu seems all about mobile lately, and they will never really compete against Android, what happens when they realize they are not viable in the mobile market either? It's a fair question.

---

### Post by CharlesA on 2014-04-02
> **Linuxratty said:**
> Over at LI,three of us tried this and were not impressed. 
It's a shame about  Onecloud,but i also do not trust cloud services any further than i can fling a bull elephant.

What didn't you like about it?

> **pqwoerituytrueiwoq said:**
> I think i need to do this, also think i should get that rasberry pi now
have a guide? and a ubuntu client (i don't need windows support)
edit thought you said you made your own, maybe owncloud is software to make your own or a service, time to goolge

Have a read here:
[http://askubuntu.com/questions/362326/owncloud-server-on-ubuntu-12-04](http://askubuntu.com/questions/362326/owncloud-server-on-ubuntu-12-04)

You can host your own stuff with ownCloud.

---

### Post by alankon on 2014-04-02
Anyone got any suggestions for good alternatives to Ubuntu One (that, obviously, integrate well with Ubuntu)?

---

### Post by mattlach on 2014-04-02
> **kurt18947 said:**
> Roasted, thank you for the heads up.
I'm skeptical about 'cloud' services as well, particularly the free ones.  There are certain unavoidable expenses associated with such offerings.  The bills have to be paid somehow.  Then there are the privacy and security concerns.

That's why I run my own "cloud" in my basement.

All of my storage resides on my VMWare server in the basement, using a FreeNAS install and a 12TB ZFS RaidZ2 array.  (the server also has an Ubuntu Server install on it, for general server tasks, and has pfSense on it for my routing.)

My local clients have only OS and programs on small SSD's and small working documents folders synced to my storage server using an rsync cronjob.   Using NO-IP dynamic DNS, I can also sync to my "cloud" while on the go :)   For some things that require it, I have also set up a VPN, so I can access my full local network from anywhere I have a network connection.  (mobile wifi hotspots from my phone are awesome for this)

No need for Ubuntu One or any other cloud service :p  And this way I control my own data :p

---

### Post by mastablasta on 2014-04-02
wish i had a basement :-P

sad to see this. i had 33.4 mb stored there. it was always fast and reliable to me.

spideroak also works but it's so very slow. 

too bad. i guess it's time to get my own server or something.

---

### Post by PartisanEntity on 2014-04-02
I think Canonical is better off this way. There are companies out there specialized in cloud based syncing and sharing. With a big head start. Trying to compete with them requires considerable investments, time and energy. 

I personally use owncloud on my linode vps and could not be happier. I ditched Dropbox after I started using owncloud. And it keeps getting better.

---

### Post by slooksterpsv on 2014-04-02
Thank you there's some files I need so I guess I'll use Google Drive or Microsoft OneDrive (mainly cause OneDrive is on my dell tablet and its nice when programming in Windows to have it sync so fast).

---

### Post by Erik1984 on 2014-04-02
> **PaulW2U said:**
> **As a Kubuntu user any integration with my OS was simply not there.**

I always saw it as a free service, nothing more, nothing less, as my remote storage requirements were always very basic. I wonder how many users actually paid for an enhanced service that would have helped to make the service profitable?

Time to move on.........

Exactly. Not that I think KDE integration would've saved Ubuntu One but for me it was a reason to use Dropbox for my cross platform file syncing.

---

### Post by monkeybrain20122 on 2014-04-02
I thought they are making money on the cloud and servers, just not on the desktop.

---

### Post by Roasted on 2014-04-03
> **CharlesA said:**
> Threads merged. Kinda makes me glad I use ownCloud if I want to share stuff or have it easily accessible.

To be honest, and rather blunt, the only type of cloud storage that makes any degree of logical sense is cloud storage you have true control of. With ownCloud, this is possible. With, well, just about every other service out there, it's not.

Dropbox has had its outages in the past.
Dropbox scans your files for "pirated" content for deletion. (this capability raises concern in regard to what they consider in violation)
Dropbox's disclaimer specifically notates that there is zero guarantee with your data; even for their paid service. If it magically goes poof, too bad.
WD Cloud has been down for 6 days and counting at the time of this post.
iCloud had a few small outages throughout the 2nd half of last year.
SkyDrive (OneDrive) was down for a while this past August. Likewise, Microsoft's recent email snooping doesn't fare well on a trust level by any stretch.

I know home servers aren't a sure-fire 100% uptime guarantee, but the last time my server was down was when my UPS died before I could re-wire the electrical outlets in time during my basement renovation a few months ago. I am continually surprised at how little I have to do to ensure it runs. As long as I pay my electric bill, it seems to keep on trucking.

All of this, of course, is just my 2c.

---

### Post by Roasted on 2014-04-03
> **monkeybrain20122 said:**
> I thought they are making money on the cloud and servers, just not on the desktop.

They weren't making money on Ubuntu One, their cloud storage service. They are heavily focusing on other cloud based server services however, and very well might be coming out in the positives there.

---

### Post by mastablasta on 2014-04-03
> **Roasted said:**
> I know home servers aren't a sure-fire 100% uptime guarantee, but the last time my server was down was when my UPS died before I could re-wire the electrical outlets in time during my basement renovation a few months ago. I am continually surprised at how little I have to do to ensure it runs. As long as I pay my electric bill, it seems to keep on trucking.



ugh any other alternatives but the home server? home server can be a bit expencive to maintain or am i wrong? i mean there is electricity, the initial cost...

Ubuntu one was free, fast and easy to use. anything as good as this one out there? would need about 5 Gb as was offered here. it can be even less as long as it's fast and reliable. i don't want to fill up google drive with data. i use spideroak but that one is very slow, so i just use it for backup of a few important files.

another downside with home server is if you go on the other side of the world and try to connect to it the connection could be very slow (compared to cloud services such as google etc.).

---

### Post by ChiefWOTJ on 2014-04-03
Although I'm not necessarily surprised, it's a bit of a downer since I really thought that tight Ubuntu One integration would have been nice to see in Ubuntu mobile devices.  I expect the bills started piling up and not enough people were signing up for the paid services, like Ubuntu One Music...perhaps?

---

### Post by foxy123 on 2014-04-03
I wonder what people think of the available alternatives? I used U1 for backing up photos from my phone to the laptop and for backing up some docs which I might need on the go. Same for my wife. Now I need to switch to something else.I can probably use some cloud service on my hosting (but not sure if it has an app for Android) or on my NAS (setting up VPN or something) but probably it is easier to use something similar to U1.

---

### Post by PartisanEntity on 2014-04-03
> **foxy123 said:**
> I wonder what people think of the available alternatives? I used U1 for backing up photos from my phone to the laptop and for backing up some docs which I might need on the go. Same for my wife. Now I need to switch to something else.I can probably use some cloud service on my hosting (but not sure if it has an app for Android) or on my NAS (setting up VPN or something) but probably it is easier to use something similar to U1.

I am a big fan of ownCloud an am using it on my hosted server. If you have a similar platform/server as an option, have a look at ownCloud. I gave up using DropBox after I started using ownCloud.

---

### Post by foxy123 on 2014-04-03
> **PartisanEntity said:**
> I am a big fan of ownCloud an am using it on my hosted server. If you have a similar platform/server as an option, have a look at ownCloud. I gave up using DropBox after I started using ownCloud.

Its Android app though is not free :(. Not that it is expensive but still what if I do not like the service.

---

### Post by forrestcupp on 2014-04-03
At first I thought it was an April Fool's joke. It's a shame. When they first came out with Ubuntu One, it was supposed to be a revenue generator for them. I guess it didn't work out that way. It's too bad Google doesn't get off their backsides and get a Linux version of Google Drive out. I think they give something like 15GB of storage free now. It's funny how they can use Linux in house, and use the Linux kernel for Android, but when it comes to stuff like this, they don't care a whole lot about Linux.

> **CharlesA said:**
> 
Have a read here:
[http://askubuntu.com/questions/362326/owncloud-server-on-ubuntu-12-04](http://askubuntu.com/questions/362326/owncloud-server-on-ubuntu-12-04)

You can host your own stuff with ownCloud.

ownCloud is awesome, but you have to be careful to find out if your hosting allows it. I have web hosting that supposedly includes "unlimited bandwidth and storage," but they don't allow using it for backups. So I'm out of luck with ownCloud.

---

### Post by Dragonbite on 2014-04-03
Funny... Microsoft, Apple and Google all are focused on integrating the cloud with their desktop and mobile devices and Canonical goes and axes its!

Was UbuntuOne truly open source?  Maybe the clients, but was the server part ever open?

It started out with some good ideas (sync Firefox bookmarks, contacts, etc.) but then development just stopped.  Little changes here and there but otherwise not many improvements over the years.  And what the heck was with not having it fully integrated with Kubuntu, Xubuntu and Lubuntu?  Not to mention there may have been more activity if non-*buntu distributions had access (Fedora, openSUSE, PCLinuxOS, Mandriva, ... did Mint have a client(? )! ).  It took quite a while for it to open up to Windows.

I think a fully open-source server and cross-platform client software as well as a hosting company running this and offering accounts with certain space could be popular, especially in light of the online spy-snooping.  OwnCloud is the closest option, but I would love to find an organization that hosts a site (like Dropbox does) using ownCloud and is dedicated to security of data.  It would become the showcase of the stable version of ownCloud.

[LIST]
[*][Dropbox]("https://db.tt/LmRN4B0") is great, but small and pricey.  It does, however, have the advantage of 3rd party plug-ins to access and work your files via the cloud.
[*][s]SkyDrive[/s] [OneDrive ]("https://onedrive.live.com?invref=7694c6924b22c8d9&invsrc=90")is actually very good, but not cross-platform (at least not Linux).  I love it that there is no conversion of files between working on it in the cloud, and working on it locally. Plus you can default your files to Open Document format instead of MS's format so my linked Windows machine running LibreOffice doesn't have to convert or pop-up warnings when opening or saving files, yet they can be opened in the browser just fine.
[*]Google Drive is pretty good, but no official Linux port (despite their years of _promising_ one)  If they are going to promise one, then they should provide one. 
[*][Copy ]("https://copy.com?r=wR3jYg")is actually cross-platform and provides a lot of space so that may be my next move.  It doesn't have the "move" feature via the web browser, but the amount of space available makes up the difference (~207 GB). It even has a move feature that will move files from one service to another without it having to download onto your machine in-between.
[/LIST]

I think it is an opportunity lost and I'll be sad to see it go.

---

### Post by forrestcupp on 2014-04-03
> **Dragonbite said:**
> 
[LIST]

[*][Copy ]("https://copy.com?r=wR3jYg")is actually cross-platform and provides a lot of space so that may be my next move.  It doesn't have the "move" feature via the web browser, but the amount of space available makes up the difference (~207 GB). It even has a move feature that will move files from one service to another without it having to download onto your machine in-between.
[/LIST]

I think it is an opportunity lost and I'll be sad to see it go.

Copy is pretty cool, but I had issues with its iOS app. There were too many times when I updated files on my computer, and the iOS app refused to sync and show the updated file. That one issue was enough to cause me to ditch it.

---

### Post by coffeecat on 2014-04-03
> **Dragonbite said:**
> 
Was UbuntuOne truly open source?  Maybe the clients, but was the server part ever open?


This from the link in the OP:

> Additionally, we continue to believe in the Ubuntu One file services, the quality of the code, and the user experience, so will release the code as open source software to give others an opportunity to build on this code to create an open source file syncing platform.

It's not quite clear to me from that whether they mean the client, server or both. The OP in [this slashdot discussion]("http://news.slashdot.org/story/14/04/02/1355244/canonical-shutting-down-ubuntu-one-file-services") appears to think the backend code will be open-sourced, but doesn't cite a source for this statement.

---

### Post by pauljwells on 2014-04-03
Canonical have announced that Ubuntu One will be [discontinued]("http://blog.canonical.com/2014/04/02/shutting-down-ubuntu-one-file-services/") and will not be included as part of 14.04 LTS

---

### Post by craig10x on 2014-04-03
It was removed today from my 14.04 development install when i did the updates...so, no question that it won't be in the final release...
I switched over to Google Drive which gives you 15 gb of free storage...only thing is the web based version can't automatically synch files (you have to upload them manually)...otherwise, very nice and easy to use...They should come out with a downloadable and installed version of Google Drive like they have for windows and mac, they have been very slow about getting that out...but the web based version should suit my needs...

Still getting the cloud icon on my ubuntu top panel though....i guess it will get removed soon...
update: cloud icon is removed...i just had to remove it from the start up applications listing...still had my ubuntu one folder, so i deleted that...;)

---

### Post by Elfy on 2014-04-03
merged and moved

---

### Post by CharlesA on 2014-04-03
> **mastablasta said:**
> ugh any other alternatives but the home server? home server can be a bit expencive to maintain or am i wrong? i mean there is electricity, the initial cost...

Ubuntu one was free, fast and easy to use. anything as good as this one out there? would need about 5 Gb as was offered here. it can be even less as long as it's fast and reliable. i don't want to fill up google drive with data. i use spideroak but that one is very slow, so i just use it for backup of a few important files.

another downside with home server is if you go on the other side of the world and try to connect to it the connection could be very slow (compared to cloud services such as google etc.).

You could host it on a VPS or dedicated server if you wanted to pay extra or use what you already have if you are hosting your website or whatever.

> **PartisanEntity said:**
> I am a big fan of ownCloud an am using it on my hosted server. If you have a similar platform/server as an option, have a look at ownCloud. I gave up using DropBox after I started using ownCloud.

Same, I've got mine on a VPS, but it would probably work fine on my home server if I wanted to serve it from home, too.

> **forrestcupp said:**
> ownCloud is awesome, but you have to be careful to find out if your hosting allows it. I have web hosting that supposedly includes "unlimited bandwidth and storage," but they don't allow using it for backups. So I'm out of luck with ownCloud.

Yep. Most shared hosting plans have it in their ToU that says you can only use their services to serve files for your website, not for storage. That is one reason I have a VPS. :)

---

### Post by Roasted on 2014-04-03
> **mastablasta said:**
> ugh any other alternatives but the home server? home server can be a bit expencive to maintain or am i wrong? i mean there is electricity, the initial cost...

Ubuntu one was free, fast and easy to use. anything as good as this one out there? would need about 5 Gb as was offered here. it can be even less as long as it's fast and reliable. i don't want to fill up google drive with data. i use spideroak but that one is very slow, so i just use it for backup of a few important files.

another downside with home server is if you go on the other side of the world and try to connect to it the connection could be very slow (compared to cloud services such as google etc.).

It depends on your definition of expensive and maintenance. Basically all you do is install Ubuntu or Ubuntu Server, add the ownCloud Server PPA and install it. 

If you fancy you can set up SSL and then in the ownCloud menu of the web interface force it to HTTPS. I forget the exact process to setting up SSL, but I think I ran 2 or 3 commands I found on a guide somewhere and bingo - accessible via HTTPS. I'm sure somebody reading this may know better than I do offhand.

Electricity wise I actually put a lot of thought into my hardware when I built my server. It's honestly nothing special. It's a low wattage i3 processor, 4 GB of RAM, and some sort of H61 micro ATX motherboard. I threw those parts into a case and added a few hard drives.

(1) 160 GB WD Black for / drive
(2) 3TB WD Reds for /media/storage in RAID 1 software raid mirror using mdadm
(I altered the data directory location in the ownCloud config to point to /media/storage/ownCloud/data so it resided on the RAID)

Based on my kill-a-watt vs current price of electricity (I over-estimated the kw/h entry a slight bit) vs 24/7/365 runtime, the calculator suggests it will cost me:

Cost Per Hour: 	$0.005000	
Cost Per Day: 	$0.120000
Cost Per Week: 	$0.840
Cost Per Month: 	$3.36
Cost Per Year: 	$43.68

Given the fact that I use my server for many things (file, print, web, backups, ownCloud, video surveillance, IRC, local video streaming to HTPC, local + external music streaming, etc) eating the 500-600 dollar cost of this box was well worth it. I'm currently sitting at about 1.2 TB of free space, so I effectively have that available to me for ownCloud.

Before I built this server and I was basically running just ownCloud and Samba for local file sharing/backup services I was using an Atom powered nettop. It was just a small book-sized unit sitting on my shelf. It was packing a 500 GB hard drive, so it was a pretty handy little box to whip up for these purposes. I've since re-located it to my parents house to act as their backup server.

One thing to consider is when you utilize a cloud service, there's little doubt that there is *some* sort of backup process. I mean, I doubt your batch of files only exist on one singular drive. Setting up some sort of backup process may very well save your skin some day. Me personally, I put a spare 1 TB hard drive into this old tower I had. It spins up automatically every night at 1:50 AM, then at 2:00 AM my main server rsyncs all of my most important stuff (ownCloud included) to it, then shuts down at 4:00 AM. That way I only run my backup server 2 hours a day instead of 24 hours a day. 

Maintenance wise I don't really do much with it. My server uptime is currently 142 days. Only reason it went down before that is because I was replacing some electrical outlets in the basement. I flipped the breaker and quickly re-wired the new outlet but my UPS battery died right before I got done. Ha? Other than that it is pretty dang reliable. My data is on my server with a mirrored level of redundancy with a daily backup. It does its thing and keeps on truckin without fuss while providing me with a snazzy amount of storage. I'm pretty okay with that. :)

---

### Post by CharlesA on 2014-04-03
https setup is cake if you know how to use Apache or Nginx. :)

---

### Post by mastablasta on 2014-04-04
well i am sure the setup is easy these days. but the initial cost of server box and then electricity is a lot higher than free ubuntu one service :-) 
true it gives you more space, you can do a lot with it and all, but also costs a lot more. yet another issue is access from overseas. will it be as fast as on local continent?

i keep collecting money for a small server, but there is always something else. latest one is some big car maintenance that's going to cost me close to 500 EUR. and it doesn't help when they ramp up the hardware prices in europe.  i mean i was shocked that price that used to be 1 EUR = 1 USd before are now more like 1 USD = 1.3 EUR. it's ridiculous. a GPU card that would cost 80USD is costing close to 102 EUR here (about 138 USD).

---

### Post by forrestcupp on 2014-04-04
You have to keep in mind that part of the benefit of services like Dropbox and Ubuntu One is that you have an off site backup. If you have your own local server, and your house/building burns down, you still lose everything.

---

### Post by PartisanEntity on 2014-04-04
> **forrestcupp said:**
> You have to keep in mind that part of the benefit of services like Dropbox and Ubuntu One is that you have an off site backup. If you have your own local server, and your house/building burns down, you still lose everything.

Since you mention that, has anyone tried Spideroak? I read that their backup tool is compatible with Linux and that one of the features allows you to backup your files to a friends house.

I am thinking of having my brother install this and giving him a HDD which I will set my instance of Spideroak to back-up to, and vice-versa for him of course.

---

### Post by kurt18947 on 2014-04-04
> **PartisanEntity said:**
> Since you mention that, has anyone tried Spideroak? I read that their backup tool is compatible with Linux and that one of the features allows you to backup your files to a friends house.

I am thinking of having my brother install this and giving him a HDD which I will set my instance of Spideroak to back-up to, and vice-versa for him of course.

No first-hand experience.  The only complaint I've read is that it's kind of slow.  Nothing negative otherwise.

---

### Post by Dragonbite on 2014-04-04
The ownCloud.org website also provides a[ list of providers]("http://owncloud.org/providers/") running ownCloud, if you do not want to host it yourself.  Of course this brings up a number of questions but if you are looking for a drop-in replacement for Ubuntu One, Google Drive, Dropbox, etc. then this may provide an option.

---

### Post by pqwoerituytrueiwoq on 2014-04-04
> **mastablasta said:**
> well i am sure the setup is easy these days. but the initial cost of server box and then electricity is a lot higher than free ubuntu one service :-) 
true it gives you more space, you can do a lot with it and all, but also costs a lot more. yet another issue is access from overseas. will it be as fast as on local continent?

i keep collecting money for a small server, but there is always something else. latest one is some big car maintenance that's going to cost me close to 500 EUR. and it doesn't help when they ramp up the hardware prices in europe.  i mean i was shocked that price that used to be 1 EUR = 1 USd before are now more like 1 USD = 1.3 EUR. it's ridiculous. a GPU card that would cost 80USD is costing close to 102 EUR here (about 138 USD).maybe you can do what i am doing and runt it off a raspberry pi
i don't know what you disk requirements are, but mine are very low
i will post back to let you know how it goes, just paid for it yesterday
$3.99 Charger (PSU for Pi)
$2.80 30ft (10m) cat5e amazon addon item discount, cost 0.02 less today <.< (monoprice brand, ebay is full of knockoff cables)
$32.99 used like new Raspberry Pi
$9.98 16GB sd card
$1.25 6ft (~1.5m) HDMI cable
$51.01 USD total
a raspberry pi may be priced better where you are as they are made in the uk

Edit:
Working good with owncloud (very slow web GUI, client usage seems fine)
didn't need the charger or the hdmi cable i ordered, ssh was enabled by default on the Debian pi version
found out i can use a usb A to A cable for power from my desktop (charger has still not arrived & at this point i doubt it will)

---

### Post by forrestcupp on 2014-04-04
> **rscarlett said:**
> Does anyone know of any other good cloud storage services?

My favorite right now is Google Drive because they give you 25GB free, and Google is always going to be stable. But they don't have a Linux client, and who knows when they will?

---

### Post by craig10x on 2014-04-04
Even though they still haven't come out with their linux client, the web based version of Google Drive works fine from my Chrome Browser (just need to be logged into chrome) only thing it won't do is synch files automatically to it...you have to upload manually if you want to save something to the cloud...works very well though and easy to use and i am using it as a replacement for my Ubuntu One cloud account...

@forrestcupp: 25 gb free?  I seem to have 15 gb free....or am i missing something?

---

### Post by Tar_Ni on 2014-04-04
I feel it's a step backward for Canonical Ubuntu, really.

The modern thrend is cloud services, everyone understand that even Microsoft who will no focus a lot more on it. If Ubuntu is serious about getting on tablets and smartphones, to become more than an OS for PC, they need their own cloud storage service.

So, that does not bode well for the future of Ubuntu really, or at least it's expension towards other markets.

One of the reason I choose Ubuntu as my main OS over any other distros is for the expension of their services, the goal to put a Linux distro in a place of choice in various markets. Now I see little advantage of using Ubuntu over say Linux Mint or Fedora. I may even switch eventually.

---

### Post by forrestcupp on 2014-04-04
> **craig10x said:**
> Even though they still haven't come out with their linux client, the web based version of Google Drive works fine from my Chrome Browser (just need to be logged into chrome) only thing it won't do is synch files automatically to it...you have to upload manually if you want to save something to the cloud...works very well though and easy to use and i am using it as a replacement for my Ubuntu One cloud account...

**@forrestcupp: 25 gb free?  I seem to have 15 gb free....or am i missing something?**

Wow. You're right. It's only 15GB. But that's still a heck of a lot more than Dropbox's 2GB.

---

### Post by craig10x on 2014-04-05
Yep...it is pretty generous, isn't it?  and 3x as much as ubuntu one was providing for free... works pretty nice too :D

---

### Post by mastablasta on 2014-04-05
well i went to make new accounts on copy and mega. the next thing to do was to download the backed up files and move them to another service. while doing that i found i can not download some files. they have size 1 byte (wrong) and they seem to not exist anymore. that's preety stupid. so much for safe data in Ubuntu one.

---

### Post by forrestcupp on 2014-04-05
> **craig10x said:**
> Yep...it is pretty generous, isn't it?  and 3x as much as ubuntu one was providing for free... works pretty nice too :D

I'm still kind of disgruntled that they benefit so much from Linux, but they can't find the time to put out a Linux client for things like this. Google Drive has been out for 2 years now.

---

### Post by mastablasta on 2014-04-05
> **pqwoerituytrueiwoq said:**
> maybe you can do what i am doing and runt it off a raspberry pi
i don't know what you disk requirements are, but mine are very low
i will post back to let you know how it goes, just paid for it yesterday
$3.99 Charger (PSU for Pi)
$2.80 30ft (10m) cat5e amazon addon item discount, cost 0.02 less today <.< (monoprice brand, ebay is full of knockoff cables)
$32.99 used like new Raspberry Pi
$9.98 16GB sd card
$1.25 6ft (~1.5m) HDMI cable
$51.01 USD total
a raspberry pi may be priced better where you are as they are made in the uk

i have one of those. i use it as media ceter. it's not very fast. though it is cheap :-) i mean for backup i guess speed is good enough. depends then how much sharing one plans to do.

---

### Post by Tar_Ni on 2014-04-05
> **craig10x said:**
> Yep...it is pretty generous, isn't it?  and 3x as much as ubuntu one was providing for free... works pretty nice too :D

What I don't like of Google Drive is the steering towards the use of Google Chrome. It's a good service to just stock your files there and work on documents in the cloud, but if you intend to watch videos, listen to audio files in the drive, say in your mobile phone or tablet you'll need a chromium browser.

There are other cloud services that are totally browser agnostic, such as Box (10B free), OneDrive(8GB free) , BitCasa (5GB free) and Dropbox (2GB free)

In these, you can watch all kind of videos and films, play musics and podcasts, edit documents ect online wth all major browsers supported.

It is not unheard of that one may use more than one cloud services at once, to increase it's amount of free GB.

---

### Post by bobclops on 2014-04-05
Please can anyone tell me if it is true Ubuntu One Is closing down?
I read something in a magazine, But there is nothing on the Ubuntu site about it.

---

### Post by bapoumba on 2014-04-05
@ bobclops, moved your post in here.

---

### Post by JonPaul on 2014-04-05
Am I the only one who is using Insync to sync my google drive? There is a one off payment of $15 but it works very well. Am quite happy with it.

---

### Post by monkeybrain20122 on 2014-04-05
Reading this thread my impression is that a lot of Uf-regulars use services other than U1 for their cloud (googledrive seems very popular), if this is the case even for avid ubuntu users it is not surprising that U1 has gone out of business. If they can't make it attractive even for the avid users it is not likely to have wider reach.  

Personally I don't use any cloud.

---

### Post by Tar_Ni on 2014-04-05
> **monkeybrain20122 said:**
> Reading this thread my impression is that a lot of Uf-regulars use services other than U1 for their cloud (googledrive seems very popular), if this is the case even for avid ubuntu users it is not surprising that U1 has gone out of business. If they can't make it attractive even for the avid users it is not likely to have wider reach.  

Personally I don't use any cloud.

My understanding is that Ubuntu One was meant to reach beyond the Ubuntu base as well. It's a service available on Linux, Windows, Mac, Android and iOS.

Of course Ubuntu One vs Google Drive or Onedrive is David against Goliath... But so is Ubuntu against Windows.. The cloud is where the web and a lot of it's user are going and Canonical just gave up for some reason.

I take the ''failure'' of Ubuntu One as a confession that Canonical is unable as yet to find ways to compete against the tech giants and so can't put it's services in the forefront of the market. That doesn't look promising for Ubuntu Touch on tablets..


You know I think that Canonical should try to come up with something new like an email service and go on from there. Google for exemple, started up with googlemail to become gmail and acquired quite a huge user base and so expanded beyond. Yahoo is another model. There maybe something that can be done in this area to steer web users towards Ubuntu.

---

### Post by vasa1 on 2014-04-06
> **Tar_Ni said:**
> ..
You know I think that Canonical should try to come up with something new like an email service ...
That hasn't been done before?

And what's with the "failure" and "confession"? The choice of words is interesting.

How many projects Google has started and then "confessed" their "failure" by closing those projects?

---

### Post by craig10x on 2014-04-06
@Tar_Ni: not so at all....all you need to have a google drive account is a gmail account (with associated password)...you can log into your web based google drive on ANY type of browser...

I love chrome and of course on Chrome i am always signed into it but you could be on say, Firefox, Internet Explorer or Safari... log into the drive and access as well as view your documents, pictures and even watch videos you may have on it or mp3s too! (for the mp3s you do need to add the Google Music app)....

Admit it's a tad easier and convenient if you like and use Chrome as i do...but it is perfectly and easily workable using ANY browser (as long as you have a gmail account of course and that gets 15 gb of free storage space)...

---

### Post by JoeFriday49 on 2014-04-06
I received a notice this morning that the file service would be shut down 1 June, 2014.  Has anyone thought about what they will use to replace this service?

---

### Post by 9k0aefbmMtuJ on 2014-04-06
Some time ago I was forced/encouraged to change the way I logged into this forum.
I had to logon with SSO.
That took me to a Ubuntu One page to log in.
Is this anything to do with the Ubuntu One cloud service and how will I log in to the Ubuntu forum when that service is cut down?

---

### Post by tgalati4 on 2014-04-06
SSO will not be affected.

Until it is affected.

---

### Post by coffeecat on 2014-04-06
Threads merged.

@michael-eacott, Ubuntu SSO is not affected by the shutdown of Ubuntu One **file services**. Please see my post #7 in this thread.

---

### Post by Tar_Ni on 2014-04-06
> **craig10x said:**
> @Tar_Ni: not so at all....all you need to have a google drive account is a gmail account (with associated password)...you can log into your web based google drive on ANY type of browser...

I love chrome and of course on Chrome i am always signed into it but you could be on say, Firefox, Internet Explorer or Safari... log into the drive and access as well as view your documents, pictures and even watch videos you may have on it or mp3s too! (for the mp3s you do need to add the Google Music app)....

Admit it's a tad easier and convenient if you like and use Chrome as i do...but it is perfectly and easily workable using ANY browser (as long as you have a gmail account of course and that gets 15 gb of free storage space)...

It's a very good cloud service, there is no doubt about that.

I've tried listening to a 1 hour podcast I had uploaded on the drive with Firefox and it didn't work. It says I need Google Chrome to play this file. I suggest you try it and you'll see.

Can't drag and drop files in the Drive neither, you need a chromium browser.

That's what I call steering towards the use of Chrome. You can't have all the feature without it.

I prefer using Onedrive, Box or BitCasa. It is totally browser agnostic and has the same thing Google Drive offer.

---

### Post by craig10x on 2014-04-06
To play that podcast, perhaps you need to add google drive music app to it...i couldn't play mp3s from my google cloud account until i added that on...seems to need it for any kind of audio files...
I have access to the drag and drop on my Chrome of course, but rarely use it...i usually just have it open my file manager and do it from there...
I use google viewer to view any videos in my cloud....that comes within the drive account automatically by default...that is also used to view documents, photos, etc...

---

### Post by vasa1 on 2014-04-07
> **alankon said:**
> Anyone got any suggestions for good alternatives to Ubuntu One (that, obviously, integrate well with Ubuntu)?
[http://discourse.ubuntu.com/t/what-are-your-plans-to-replace-ubuntu-one-and-why/](http://discourse.ubuntu.com/t/what-are-your-plans-to-replace-ubuntu-one-and-why/)
[http://www.omgubuntu.co.uk/2014/04/three-alternatives-ubuntu-one](http://www.omgubuntu.co.uk/2014/04/three-alternatives-ubuntu-one)

---

### Post by forrestcupp on 2014-04-07
> **monkeybrain20122 said:**
> Reading this thread my impression is that a lot of Uf-regulars use services other than U1 for their cloud (googledrive seems very popular), if this is the case even for avid ubuntu users it is not surprising that U1 has gone out of business. If they can't make it attractive even for the avid users it is not likely to have wider reach.  

Personally I don't use any cloud.Exactly. They wanted to reach out to non-Ubuntu users. But seriously, how many non-Ubuntu users are going to use Ubuntu One when we have so many other proven choices out there that don't have a name associated with an operating system they don't want to use? It wasn't destined to generate the revenue they wanted, just like a phone won't, either. I have a feeling that if they want to become a multi-billion dollar company, they're in the wrong line of business. Maybe they need to start selling timeshares to fund their Linux project. :D

> **vasa1 said:**
> That hasn't been done before?

And what's with the "failure" and "confession"? The choice of words is interesting.

How many projects Google has started and then "confessed" their "failure" by closing those projects?iGoogle is a big one that comes to my mind. ;)

---

### Post by vasa1 on 2014-04-07
> **forrestcupp said:**
> ...
iGoogle is a big one that comes to my mind. ;)

[http://www.theguardian.com/technology/2013/mar/22/google-keep-services-closed](http://www.theguardian.com/technology/2013/mar/22/google-keep-services-closed) lists 39 if anyone is interested ...

---

### Post by xxx6 on 2014-04-07
Hi

well...as title  says...

tia!

---

### Post by BBQdave on 2014-04-07
> **forrestcupp said:**
> They wanted to reach out to non-Ubuntu users. But seriously, how many non-Ubuntu users are going to use Ubuntu One when we have so many other proven choices out there that don't have a name associated with an operating system they don't want to use?

+1

And with some of the information floated from Canonical and Ubuntu + Android devices... It would not surprise me to see Ubuntu Unity tie into Google services.

Personally, I think Ubuntu Unity with Google services would be great. Chrome OS does not offer the flexibility or capabilities of Ubuntu Unity - A great OS would be Ubuntu Unity with Google services :)

---

### Post by Dragonbite on 2014-04-07
> **paracas said:**
> I think [Copy]("https://copy.com?r=RaMUs0") is a great alternative to Ubuntu One. It offers generous 15 + 5 GB storage and is cross platform.
It should be packaged and placed in the Ubuntu repository so that people can install or remove Copy Agent easily from the Ubuntu Software Center.

Copy also makes it easy to get up in space.  I have about 225GB of space in mine.  A package for installing in Ubuntu would be great but I do like how it is cross-platform AND cross-distro. (I also have 125GB of OneDrive, 15GB of Google Drive and 2.25GB of Dropbox)

If Ubuntu announces an agreement with Google to use Google Drive I will welcome it from a consumer perspective, but it would also cast a shadow over Ubuntu and Canonical's independence that isn't so easily dismissed.  Google has killed off Reader and iGoogle and promised a Linux client a couple of years ago.  Not offering a client is one thing, and I can deal with that, but that they _promised_ a Linux client and haven't delivered is what gets me upset.

When you think of it, though, only Ubuntu (Unity) users will miss it.  Kubuntu, Xubuntu, Lubuntu and other Linux distros have never really had access to it and the web interface sucked enough even it wasn't an alternative.

---

### Post by forrestcupp on 2014-04-07
> **vasa1 said:**
> [http://www.theguardian.com/technology/2013/mar/22/google-keep-services-closed](http://www.theguardian.com/technology/2013/mar/22/google-keep-services-closed) lists 39 if anyone is interested ...I guess you can't trust any Google app for longevity. It's a good thing my Google Drive is also stored locally. I wonder how long that will last.

But in other news, thanks for posting that article. I noticed from one of the ads that they're officially working on a Goonies sequel. :guitar:

> **Dragonbite said:**
> Copy also makes it easy to get up in space.  I have about 225GB of space in mine.  A package for installing in Ubuntu would be great but I do like how it is cross-platform AND cross-distro. (I also have 125GB of OneDrive, 15GB of Google Drive and 2.25GB of Dropbox)

If Ubuntu announces an agreement with Google to use Google Drive I will welcome it from a consumer perspective, but it would also cast a shadow over Ubuntu and Canonical's independence that isn't so easily dismissed.  Google has killed off Reader and iGoogle and promised a Linux client a couple of years ago.  Not offering a client is one thing, and I can deal with that, but that they _promised_ a Linux client and haven't delivered is what gets me upset.

When you think of it, though, only Ubuntu (Unity) users will miss it.  Kubuntu, Xubuntu, Lubuntu and other Linux distros have never really had access to it and the web interface sucked enough even it wasn't an alternative.Copy was awesome, but like I said before, I had some major iOS app problems with it that totally killed Copy for me. The app wasn't syncing and fetching updated files that I needed it to, and there is no way to manually force it to sync. It was just opening old versions of the files. If it wasn't for that, I would still be using Copy right now.

---

### Post by marco-parillo on 2014-04-07
Actually I have been a reasonably a happy U1 user in Kubuntu for almost two years:
[https://bugs.launchpad.net/ubuntuone-client/+bug/375145/comments/114](https://bugs.launchpad.net/ubuntuone-client/+bug/375145/comments/114)
I did not really need integration with Dolphin, and the notifications in Plasma (though DBus?) were good enough for me.
It just worked.

---

### Post by Newbunto on 2014-04-07
> **marco-parillo said:**
> [http://blog.canonical.com/2014/04/02/shutting-down-ubuntu-one-file-services/](http://blog.canonical.com/2014/04/02/shutting-down-ubuntu-one-file-services/)


Background information from that link that was not in the email sent to all users:
[INDENT]However, like any company, we want to focus our efforts on  our most important strategic initiatives and ensure we are not spread  too thin.
[/INDENT]
[INDENT]Our strategic priority for Ubuntu is making the best  converged operating system for phones, tablets, desktops and more. In  fact, our user experience, developer tools for apps and scopes, and  commercial relationships have been constructed specifically to highlight  third party content and services (as opposed to our own); this is one  of our many differentiators from our competitors.  Additionally, the  free storage wars aren’t a sustainable place for us to be, particularly  with other services now regularly offering 25GB-50GB free storage.  If  we offer a service, we want it to compete on a global scale, and for  Ubuntu One to continue to do that would require more investment than we  are willing to make. We choose instead to invest in making the absolute  best, open platform  and to highlight the best of our partners’ services  and content.
[/INDENT]

---

### Post by C.S.Cameron on 2014-04-07
For those people asking for alts, I got 50GB free from Box.
With Box you need to use something like WebDAV for Linux.
I don't use cloud much though, except for gmailing myself.

---

### Post by Newbunto on 2014-04-07
> **Roasted said:**
> Setting up some sort of backup process may very well save your skin some day. Me personally, I put a spare 1 TB hard drive into this old tower I had. It spins up automatically every night at 1:50 AM, then at 2:00 AM my main server rsyncs all of my most important stuff (ownCloud included) to it, then shuts down at 4:00 AM. That way I only run my backup server 2 hours a day instead of 24 hours a day. 


Do you have an issue with "single location of failure"? If there's a fire at your place, and your main server and your backup server get "roasted", isn't that a problem?

By all means have your cloud in your "basement" (as I too do) but you need to be able to backup to "out there", just in case, but at the same time ensure privacy of your files. At the very least you need to backup to removable drives that you store elsewhere.

---

### Post by RogerDavis on 2014-04-08
Now that Ubuntu One is on the way out, what cloud services will function with Ubuntu at little or no cost?

---

### Post by xxx6 on 2014-04-08
> **RogerDavis said:**
> Now that Ubuntu One is on the way out, what cloud services will function with Ubuntu at little or no cost?

[http://ubuntuforums.org/showthread.php?t=2214632&page=7&p=12980208#post12980208](http://ubuntuforums.org/showthread.php?t=2214632&page=7&p=12980208#post12980208)

:confused:

---

### Post by crockett-umdnj on 2014-04-08
I paid and it was well worth it.    Now I am undecided on what to do.

I am sorry to see it go.    I found very useful to back up my microsocpe pics.  I had paid for enhanced service.   It was well worth it.   I was a bargain.

---

### Post by Dragonbite on 2014-04-08
I'm considering setting up an ownCloud server at home and synchronizing everybody's files into a couple of TB external hard drive so at least everybody has 2 copies... one on their system and one in ownCloud.  Then maybe set up a separate HD to backup the ownCloud server (everybody's files) nightly or weekly.

Or if I set up a Crashplan acocunt, have the ownCloud server automatically backing up to the cloud.  Might save money that way, as it is only backing up "one" computer....

---

### Post by Dragonbite on 2014-04-11
Looking for an easy way to transfer your files from UbuntuOne to another Cloud Storage Service?  Keep an eye on [Mover.io]("https://mover.io/")!

**Background:**

I have a Copy.com account and they provided a means to use Mover.io to copy files from other online services into Copy.com (Mover.io actually does many more services than just Copy.com... that is just how I heard of them).

**Difference:**
[LIST]
[*]No download-and-upload the files, it works server-to-server and your computer doesn't even need to be turned on.
[*]It can be scheduled to run at specific times, such as in the middle of the night when you are not changing or touching any of the files 
[*]The schedule can be recurring Monthly, Weekly, Daily or Hourly making it an easy method to backup one service to another (including FTP, sFTP, WebDAV and Amazon S2)
[*]You can choose to Archive (Zip) your file before transfer (saves space and bandwidth if you are backing things up)
[*]You can choose to only move files changed between scheduled transfers (Incremental)
[*]Handles 22 different "connectors" or services/server types that you can copy to or from, 
[/LIST]

**Ubuntu One?**

I asked them if they were going to provide an UbuntuOne connector, and a couple days later they implemented a test (Beta) connector for UbuntuOne to my account to try.  So I set it to copy my Ubuntu One files (in its entirety) and it looks like it copied them without any problems!

They (Moveri.io) will be making a public announcement soon, but if you want to use it now you can [EMAIL="support@mover.io"]contact them[/EMAIL] and ask them to attach this connector to your account.

**Free?**

My Copy.com account provided some use of this, but otherwise it [costs money]("https://mover.io/pricing/").  It looks like you get 1 scheduled and 2GB transfer for free, or 5 transfers and 10GB per month for $15 per month (and of course, higher tiers for more money, including business levels).

**Connectors**

Their [list of connectors]("https://mover.io/connectors/") includes 
GreenQloud, Yandex Disk, Office 365, Sharepoint, FTP, Dropbox, Box, Google Drive, OneDrive, Copy, Webdav, Amazon S3, Rackspace, Egnyte, MySQL, SugarSync, SmugMug, SFTP, Dreamhost, Media Temple & Openstack.


I hope this helps somebody.

---

### Post by Tar_Ni on 2014-04-11
Hi,

This is a message for everyone looking for a replacement to Ubuntu One or any other cloud services.

I have a found **FireDrive**, a cloud service offering **50 GB of storage for free!**

Wow! very user-friendly and play MP3, watch videos edit documents on your web browser. Let's just say that Google Drive and it's 15GB, presented earlier as the best alternative, looks small beside it.

Go to ww.firedrive.com

---

### Post by sammiev on 2014-04-11
> **Tar_Ni said:**
> Hi,

This is a message for everyone looking for a replacement to Ubuntu One or any other cloud services.

I have a found **FireDrive**, a cloud service offering **50 GB of storage for free!**

Wow! very user-friendly and play MP3, watch videos edit documents on your web browser. Let's just say that Google Drive and it's 15GB, presented earlier as the best alternative, looks small beside it.

Go to ww.firedrive.com

Going to give it a fly-by. 
Thanks

---

### Post by raisen on 2014-04-12
For those who want to try their own cloud solutions, this page has some good resources:

[https://wiki.debian.org/FreedomBox/LeavingTheCloud](https://wiki.debian.org/FreedomBox/LeavingTheCloud)

---

### Post by Dragonbite on 2014-04-12
Great step-by-step on setting up Copy in Linux (and it works).  This solves my file synchronization issue, especially since Copy is cross-platform AND cross-distribution.  Plus with the ease of Mover.io, I have easy migration from Ubuntu One to Copy on my Ubuntu system.

[http://thinkonbytes.blogspot.com/2014/04/choosing-copy-as-file-syncing-software.html]("http://thinkonbytes.blogspot.com/2014/04/choosing-copy-as-file-syncing-software.html")

---

### Post by twinkel1961 on 2014-04-15
the safest would probably be to use owncloud as that would leave the data at home.

But the ideal workflow for me is to have data available anywhere without being dependent of a single network and server at home.
A good alternative to ubuntuone would be [dropbox]("https://db.tt/3aevd1Y") or [copy.com]("https://copy.com/?r=VZlg7v").
Copy.com starts with a free 15Gb storage space and clients for linux, smartphones, apple and windows.
if you go to [https://copy.com/?r=VZlg7v]("https://copy.com/?r=VZlg7v"), you and I will both get an additional 5Gb storage.

---

### Post by Dragonbite on 2014-04-15
For just synchronizing files, Copy.com does a pretty good job.

Where I find these services failing is when managing and using these files via the browser.  The 2 best for this is, no surprise, Microsoft and Google.  Microsoft gets a slight edge in that the files that are stored in OneDrive and syncrhonized don't have to be "converted" for the online applications to open and edit these files.  I even have them stored in Open Document Format since my associated Windows machines run LibreOffice (not MS Office).  OneDrive can even open and edit things like PHP files with color syntaxing.

Otherwise I prefer Google Docs to Microsoft's Office Online (at this point).. better response time and easy to use features.

---

### Post by Smallwheels on 2014-04-16
I tried Ubuntu One storage once. It was clunky. I use Dropbox for synchronizing files, though I don't actually need synchronizing anymore. I still have a couple of gigabytes of files there. 

I have decided to try Google Drive for some files. It seems to work OK. Yahoo's Flickr now offers 1 terabyte of free image storage with no time limits. I have begun switching to it and it isn't perfect but it is a good place to backup my images. I have less than 100 GB of images. I have about 15 GB of work related videos that I will move there. 

Cloud storage is the future for me. I used Carbonite for a year to backup my files. I didn't have any crashes but it was great for when I wiped a drive and reloaded the data. I ended up dropping it and using Carbon Copy Cloner on my Mac Book. It was better because everything on the drive was copied not just the file system data. 

If my computers are ever stolen or destroyed in a fire my data will be lost, unless I have it stored at another site. That is why I want to move everything to the cloud so I can access it from anywhere no matter what happens to my personal computers. I am implementing a system whereby I save things to my local drive and upload them to the cloud at the end of each day. This way it simplifies my storage and keeps things secure. This also will simplify managing my data when I travel away from my desktop. I don't do sensitive work and I don't store financial data on machines. The cloud will work for me.

---

### Post by markodd on 2014-08-15
Does anyone have an **open-source** alternative to U1/Dropbox/SpiderOak? I'm not interested in hosting my own (owncloud, etc)..

---

