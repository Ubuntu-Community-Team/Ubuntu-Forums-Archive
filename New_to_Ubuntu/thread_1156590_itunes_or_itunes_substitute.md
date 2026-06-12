---
title: "itunes or itunes substitute"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by austin7 on 2009-05-11
is there any way i can connect to the itunes store or is there atleast any substitut i can use that will recognize my ipod touch

---

### Post by tkelito on 2009-05-11
Not sure how much reading you take in on technology but here is the latest on the iTunes Open Source Project:

[http://www.pcworld.com/article/163909/apple_is_sued_after_pressuring_opensource_itunes_project.html](http://www.pcworld.com/article/163909/apple_is_sued_after_pressuring_opensource_itunes_project.html)

> Apple Is Sued After Pressuring Open-source ITunes Project

Robert McMillan, IDG News Service
Apr 27, 2009 4:20 pm

The operator of a technology discussion forum has sued Apple, claiming that the company used U.S. copyright law to curb legitimate discussion of its iTunes software.

The lawsuit, filed Monday, could test the limits of the U.S. Digital Millennium Copyright Act (DMCA). It centers around an open-source effort to help iPods and iPhones work with software other than Apple's iTunes. Last November Apple's lawyers demanded that the Bluwiki.com Web site remove a project called iPodhash, saying that it violated the DMCA's anti-circumvention provisions.

The lawsuit was filed jointly in U.S. District Court for the Northern District of California by the Electronic Frontier Foundation (EFF) and attorneys representing OdioWorks a small Herndon, Virginia, company that runs Bluwiki. Lawyers argue that the iPodhash discussions were about reverse-engineering software, not breaking copy protection, and ask for a court ruling to clarify the matter.

The EFF has previously argued that reverse engineering in order to build new products is permitted under the DMCA. However, this case is a little different, according to Fred von Lohmann, an attorney with the digital civil liberties organization. "This is the first time I've seen a company suggest that simply talking about reverse engineering violates the DMCA," he said. "All of the previous cases have been cases that involved actual successful reverse-engineered tools."

Bluwiki is a free wiki service that hosts discussion pages for a number of projects. After Apple's November takedown letter, three Web pages that talked about a cryptographic function used by iTunes were removed from the Bluwiki Web site.

Open-source developers have been working on breaking cryptographic mechanisms used by iTunes since 2007. That's when Apple first introduced a special operation, called a checksum hash, into its products to ensure that Apple's devices were communicating with iTunes and not some other type of software.

Developers reverse-engineered Apple's checksum mechanism, but in late 2008 the company introduced a new version of the crypto-technique with its iPod Touch and iPhone products. That's what was being discussed when Apple filed its takedown notice.

The EFF and OdioWorks say iPodhash was trying to get the iPod and iPhone to work with other software such as Winamp or Songbird, and that the work would also help iPod and iPhone users who ran the Linux operating system, because Apple doesn't ship a version of iTunes for Linux.

However, in a Dec. 17 letter to the EFF, Apple's law firm said that the EFF is "mistaken" to assume that this technology is only used to authenticate the iTunes software. The work also threatens Apple's FairPlay copy-protection system, the letter states.

Apple did not respond to requests for comment on the lawsuit.

In an interview Monday, OdioWorks Founder Sam Odio said that he believes that the iPodhash's lead developer, who went by the pseudonym Israr, would pick up the discussion if OdioWorks and the EFF win the case. "What this guy was doing was legitimate," Odio said. "He was just trying to reverse engineer Apple's products to try to get them to work with Linux and other third-party software"

I don't think anyone will be of any assistance at this point.

-tkelito

---

### Post by lvleph on 2009-05-11
I know that the closest thing to iTunes I have found is Rhythmbox. It has a media store too. I am not sure about support for iPod Touch.

EDIT:
[This looks interesting.](http://www.atunes.org/wiki/index.php?title=Main_Page)

---

### Post by tkelito on 2009-05-11
Maybe down the road...

>   Is it possible to synchronize my iPod with aTunes?

Currently aTunes can only READ iPod contents until 4th generation. It has not been tested with later versions. It can't write songs to iPod. However, aTunes can write to many generic mp3 players acting as external hard drive (i.e. mass storage devices). 

-tkelito

---

### Post by abhiroopb on 2009-05-11
amarok syncs ipods quite effectively.

---

### Post by DGortze380 on 2009-05-11
Buy your music music from Amazon. No DRM.

---

### Post by tkelito on 2009-05-11
> **abhiroopb said:**
> amarok syncs ipods quite effectively.

Really, did not know that, about to go get the classic and test!

> **DGortze380 said:**
> Buy your music music from Amazon. No DRM.

Apple removed DRM some months ago and offered for around $.30 a song to remove DRM from previously downloaded songs.

-tkelito

---

### Post by DGortze380 on 2009-05-11
> **tkelito said:**
> 

Apple removed DRM some months ago and offered for around $.30 a song to remove DRM from previously downloaded songs.

-tkelito

read the releases ... they STARTED to removed DRM. It will take until Christmas for the whole store to be DRM Free.

---

### Post by abhiroopb on 2009-05-12
With amarok I'd suggest a couple of things...

Firstly, the current 2.0 release is not that great, for whatever reason they have decided to leave out a number of features. Therefore I'd suggest using the 1.4 release.

You can add this ppa which has the 1.4 release
```

deb http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main
```

Next I had highlighted a guide in my blog which goes through the steps involved in setting up the iPod for Amarok. In jaunty most of these are now defunct.

This is what you need to do...

1. Connect your iPod

2. See what the "mount" point is called. If you look under "Places" you should see your iPod. If you do then note down what it is called, e.g. "iPod" or "tkelito", etc.

3. Open Amarok, go to Settings > Configure Amarok > Media Devices (tab on the left).

4. Add Device

5. Put the following into the dialog:
plugin: "Apple iPod Media Device"
name for device": (whatever name)
mount point: /media/iPod (or whatever the name you found in "Places").

6. Now connect the iPod and go to the "Devices" tab on the main amarok page, and click connect.

If you have any problems let me know!

---

### Post by Grenage on 2009-05-12
Songbird is excellent, as is Amarok.

---

