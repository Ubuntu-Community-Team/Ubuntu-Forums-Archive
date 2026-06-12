---
title: "&quot;Could not download release notes&quot;?"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by random turnip on 2009-10-29
I am trying to upgrade 9.10, but every time i press the upgrade button it says "Could not download release notes.  Please check your internet connection".

I've tried doing all normal updates, that worked straight away so i tried again and got the same message.  And i'm typing this ont he same computer, so i'm fairly sure im connected to the internet.

Any ideas?

TBH i don't fancy doing a fresh install.

---

### Post by aktiwers on 2009-10-29
Try ALT+F2
and type:
```
update-manager -d
```

If you still get the error, try changing your software sources to another country.

---

### Post by ikisham on 2009-10-29
You'll have to be patient. The servers are overwhelmed because of the release, some time you'll be able to do the upgrade.

*Edit*- about changing the servers, now it's ok but later on wouldn't it present some problems since the contents on servers are not exactly the same in a given time (then messing with the updates)?

---

### Post by dj-toonz on 2009-10-29
> **ikisham said:**
> You'll have to be patient. The servers are overwhelmed because of the release, some time you'll be able to do the upgrade.

*Edit*- about changing the servers, now it's ok but later on wouldn't it present some problems since the contents on servers are not exactly the same in a given time (then messing with the updates)?


I second that, I had the same problem when I tried to upgrade, but I grabbed a torrent instead as I couldn't wait (update-manager when It did work said 15 hours to download everything & the torrent was 10 Minutes to download & 20 minutes to dual boot & install Karmic

---

### Post by fixerman on 2009-10-29
> **random turnip said:**
> I am trying to upgrade 9.10, but every time i press the upgrade button it says "Could not download release notes.  Please check your internet connection".

I've tried doing all normal updates, that worked straight away so i tried again and got the same message.  And i'm typing this ont he same computer, so i'm fairly sure im connected to the internet.

Any ideas?

TBH i don't fancy doing a fresh install.

Keep trying every few minutes. I kept getting the same message but after about 10 attempts I got a  successful connection. Be prepared for a long download and install time. Mine has been going for over two hours and is only half way. Not surprising really with all the users poised to upgrade.

Good luck.:D

---

### Post by random turnip on 2009-10-29
Ahh, thanks guys, i figured this could be a possible problem, i dont want to do a fresh install so i'll probably just keep trying and leave it doing it over night (or is that not wise?) or do it tomorrow.

It finally started, but it's jumping between 6 and 14 hours download 0.0

---

### Post by Rollodog on 2009-10-29
I am in the process of updating now. It is downloading but very slowly. The servers must be very busy. I  guess we have to be patient today.

---

### Post by webbyone on 2009-10-30
same error here, we have 2 laptops and 2 desktops same error all the way.

---

### Post by leeliquid on 2009-10-30
I had the same problem, but after I change the download server from "United States" to "Main". It is working right now and downloading fast. 

Here is how to change the server.   
System -> Administration -> Update Manager -> Setting -> Tab "Ubuntu Software" (the first tab)-> "Download from " change it to Main server.

---

### Post by pyutaros on 2010-02-23
The BEST thing to do would be to select "other" and then click the "select best server" button.  That kind of best practice will prevent the MAIN server from becoming overloaded as well.

---

### Post by bhavinvora on 2010-04-30
Had the same problem.. tried multiple times and it started working.. ]

--Bhavin

---

### Post by jazzyjay on 2010-04-30
I recommend switching to another source/country. I'm now using Norway and the downloading is rather swift.

J.

---

### Post by dakota34 on 2010-04-30
'choose best server option' working now from toronto (picked Waterloo, which makes sense)...:):)

---

### Post by thedarksavant on 2010-05-16
So if it really is server loading issues, can we get the error message changed? Most people don't even know how to "check your internet connection" and when it's not even the real problem, that just leads people down the garden path.

It's these kinds of things that keep the pundits saying "Linux just isn't ready for prime time."

---

