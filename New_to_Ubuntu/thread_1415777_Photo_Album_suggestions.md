---
title: "Photo Album suggestions"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by gallifrey on 2010-02-25
Hi, 
not sure if I am posting in the right place, but I am a beginner, so I'll give it a try. I am looking for photo album software that meets some quite specific requirements. It has to be able to produce stand alone albums, with categorizing, and the ability to associate personal data with the photos, e.g. names, dates, etc. 

It must also be searchable, with the option of thumbnail viewing. And I DO NOT want it to be HTML, or online-related in anyway. In fact, it would be nice if I could set privacy settings for individual albums, e.g. password access.

Basically, I am just looking for an ordinary personal photo album, but for linux. 
The ability to decorate the album would be nice, but not necessary. And I am not too fussed about being able to edit photos (except perhaps rotating.)

Does anybody have any suggestions as to software that fits this criteria? i would be most grateful for any suggestions.

---

### Post by mikeyphi on 2010-02-25
Welcome!!

open System/Admin/Synaptic Package Manager

do a search on 'photo album'

you should see several hopefully suitable programs.

I'm not familiar with any of them but you can easily install, try, remove as required!

---

### Post by spillz on 2010-02-25
> **gallifrey said:**
> Hi, 
not sure if I am posting in the right place, but I am a beginner, so I'll give it a try. I am looking for photo album software that meets some quite specific requirements. It has to be able to produce stand alone albums, with categorizing, and the ability to associate personal data with the photos, e.g. names, dates, etc.
 

I think what you are looking for is a photo manager. The leading apps are:
* DigiKam (KDE based)
* F-Spot (Gnome)
* Picasa (closed source windows-centric app, Linux version relies on WINE)

By default, all three want to manage your entire collection/library of photos and have a bevy of features. I think that DigiKam and F-Spot let you define albums, which are a subset of photos in the collection. Most programs also support the concept of tagging and editing other descriptive data (metadata). If you tag your images, you can then filter by tags, so basically the same as an album.

Other lightweight contenders
* gthumb - folder based, but also supports tagging (and, I think, albums)
* kphotoalbum - tightly focused on collection management (KDE based)

One of the things to be aware of is that some programs will typically default to keeping information (tags etc) about your images in a database rather than write that information to the images themselves. Other programs will automatically write data to your images without telling you. These issues inspired me to write my own...

---

### Post by gallifrey on 2010-02-25
> **spillz said:**
> I think what you are looking for is a photo manager. The leading apps are:
* DigiKam (KDE based)
* F-Spot (Gnome)
* Picasa (closed source windows-centric app, Linux version relies on WINE)

By default, all three want to manage your entire collection/library of photos and have a bevy of features. I think that DigiKam and F-Spot let you define albums, which are a subset of photos in the collection. Most programs also support the concept of tagging and editing other descriptive data (metadata). If you tag your images, you can then filter by tags, so basically the same as an album.

Other lightweight contenders
* gthumb - folder based, but also supports tagging (and, I think, albums)
* kphotoalbum - tightly focused on collection management (KDE based)

One of the things to be aware of is that some programs will typically default to keeping information (tags etc) about your images in a database rather than write that information to the images themselves. Other programs will automatically write data to your images without telling you. These issues inspired me to write my own...

I have tried the defaults supplied with Ubuntu, but found them lacking certain functionalities that I require. Writing my own would not be a bad idea, which I may try, but I have only ever programmed in Winblows (C and BASIC), so I might have to gen up on some other languages. 

Thanks for the input so far!

---

### Post by spillz on 2010-02-25
> **gallifrey said:**
> I have tried the defaults supplied with Ubuntu, but found them lacking certain functionalities

Can you be specific?

> Writing my own would not be a bad idea, which I may try, but I have only ever programmed in Winblows (C and BASIC), so I might have to gen up on some other languages. 

It's a *lot* of work to get up to speed with the toolkits and the linux way of doing things, then a lot more work to reinvent the photo manager wheel. Digikam, F-spot support plugins, which might be another way to get what you need. Digikam is C++, F-spot is mono C#. I wrote my own app in python -- I find coding in python is fast and very natural, but I'm also comfortable with C/C++.

---

### Post by gallifrey on 2010-02-25
> **spillz said:**
> Can you be specific?

Well, the functionality I am looking for sort of entails security, for one thing, and presentation. I want to build individual book-type albums for different photo sets, and edit the presentation of the albums, and add my own details. Just like a real life photo album, really, but on a computer. 

From a security perspective, I want to be able to lock out some photo albums, e.g. password protect them. And I certainly do not want anything web based. Having the option to upload is fine, but I do not want my photos online. 

I use Lifeograph as a Journal, and I want a photo album that has that kind of feel to it.

---

### Post by Zill on 2010-02-25
I suggest you take a look at [JAlbum]("http://jalbum.net").

A java based application that is very flexible and produces impressive photo albums that *can* be published if you choose to.

---

### Post by gallifrey on 2010-02-25
> **Zill said:**
> I suggest you take a look at [JAlbum]("http://jalbum.net").

A java based application that is very flexible and produces impressive photo albums that *can* be published if you choose to.

I will check that out. Thank you, Zill.

EDIT: Cjecked out JAlbum, and it's a good piece of software, but not right for me. Too much emphasis on the web element, which I am trying to avoid. Am I being too fussy?? Anyhow, thank you for your suggestion Zill.

---

### Post by gallifrey on 2010-02-26
I have found a program called Album Shaper, which looks okay, but it seems that it dates from 2005?? Does anybody know about this app, and support/updates? I can't seem to find anything.

---

### Post by Zill on 2010-02-26
gallifrey:  I had never used Album Shaper before but have now installed it and it seems to be quite a good application.  Version 2.1 is in the repos and seems to be the latest version according to the [home website]("http://albumshaper.sourceforge.net/screenshots_visualtour.shtml").

Personally, I don't generally worry about the age or status of a project.  If it does what I want then I am quite happy to use it!

---

### Post by x C0MMAND0 x on 2010-02-26
Picasa doesn't need wine.  [http://picasa.google.com/linux/]("http://picasa.google.com/linux/")

---

