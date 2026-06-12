---
title: "FireFox - not all images display"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by cwmoser on 2009-06-20
Ubuntu 9.04 running Firefox

If I browse to a website that has numerous thumnail images, not all are displayed.

An example website is:

[http://www.auctionzip.com/cgi-bin/photopanel.cgi?listingid=657252&category=0&zip=27006&kwd=]("http://www.auctionzip.com/cgi-bin/photopanel.cgi?listingid=657252&category=0&zip=27006&kwd=")

Note for blank images that you can right click and select "Show Image".
  That tells me the image file is OK but FireFox decided not to display it.

Any help figuring this out is appreciated.

Thanks

Carl

---

### Post by starcraft.man on 2009-06-20
Hello there. Ok, can you go edit > preferences in the firefox menu, then under content tab check that load images automatically is checked. Also look at exceptions make sure it's not listed there. If that isn't it do you have any add ons that modify behaviour of firefox in this area (i.e. images)?

For me, the page worked just fine. Can you take a printscreen and attach to next reply so I can see the problem?

---

### Post by cwmoser on 2009-06-20
Under Edit -> Preferences -> Content, I have Load images automatically checked.

Exceptions - I have cleared it and tried to add auctionzip.com to Allow - both do not work.

Under Tools -> Addons -> Plugins, I have only the Default Plugin.


Here is a screen shot of what I see:
[IMG]http://www.cerant.com/Screenshot-1.png[/IMG]


Thanks much,

Carl

---

### Post by starcraft.man on 2009-06-20
That's quite peculiar. The torn page over where the pictures should be definitely indicates a problem.

Alright, in order to rule out the local browser I want you to open a terminal (alt + F2, type gnome-terminal, then enter) and install the epiphany browser with the following command (type in terminal then enter):

```
sudo aptitude install epiphany-browser
```

After it's installed under the Applications > Internet section in the panel launch epiphany and navigate to the same site and see if the pictures still blocked. If so, I think it's a networking issue either with your ISP (i.e. the external net) or your local configuration. If the pictures display, then it's an issue with firefox configuration and I'll track it down from there.

If something else happens beyond those possibilities, I'll have to summon all the knowledge of the protoss high council!

As a side note, you haven't been editing your local hosts file have you? If you don't know what that is, that's fine.

---

### Post by cwmoser on 2009-06-21
Hi, thanks for your help.

I installed the Epiphany Browser as you suggested.  I used FireFox to browse to a website where it displayed only some of the images -- then I copied the URL into Epiphany and Epiphany displayed everything the way it is supposed to.

Any ideas on what is needed to make FireFox display all images?

Thanks

Carl

---

### Post by cwmoser on 2009-06-26
Anyone else have this problem?

Carl

---

### Post by mc4100 on 2009-06-26
Do you see anything different runring firefox in a terminal window with ```
--safe-mode
```

---

### Post by Kryzzalid on 2009-06-27
Hi,

I have about the same problem with firefox. Sometimes it does display all the thumbnails, sometimes it doesn't (I attached a screen's capture). I have all the firefox's options right and default plugins.

---

### Post by QIII on 2009-06-27
Firefox has some limitations on how much it can do at a time -- with its default settings.

Look here for some suggestions.

There are other places for tweaks.


[http://www.madwahm.com/webmaster-stuff/8-easy-firefox-tweaks-for-super-fast-web-browsing/](http://www.madwahm.com/webmaster-stuff/8-easy-firefox-tweaks-for-super-fast-web-browsing/)

---

### Post by philcamlin on 2009-06-27
purge and reinstall firefox

---

### Post by cwmoser on 2009-06-27
> **philcamlin said:**
> purge and reinstall firefox


sudo  apt-get  purge  firefox

sudo  apt-get  install  firefox


did not work -- images still do not appear properly.

Carl

---

### Post by cwmoser on 2009-06-27
> **QIII said:**
> Firefox has some limitations on how much it can do at a time -- with its default settings.

Look here for some suggestions.

There are other places for tweaks.


[http://www.madwahm.com/webmaster-stuff/8-easy-firefox-tweaks-for-super-fast-web-browsing/](http://www.madwahm.com/webmaster-stuff/8-easy-firefox-tweaks-for-super-fast-web-browsing/)


I installed the tweaks in the URL you mentioned.  I am sure they made FireFox faster but still graphic images do not all display.

Carl

---

### Post by QIII on 2009-06-27
That's not good!

I just went to the site myself and had no problems with it, so it's not their server.  (I was sort of hoping we could blame someone else!)

Judging by the number of beans you display, I can assume you done all the checking for hardware like graphics and driver.

Is this something that has only begun to happen in Jaunty?  Maybe after an upgrade?

---

### Post by Kryzzalid on 2009-06-28
Thank you for the link:) the tweaks worked very well:) i have tried few websites and all the pictures were so far displayed.=)

---

### Post by cwmoser on 2009-06-29
> **QIII said:**
> That's not good!

I just went to the site myself and had no problems with it, so it's not their server.  (I was sort of hoping we could blame someone else!)

Judging by the number of beans you display, I can assume you done all the checking for hardware like graphics and driver.

Is this something that has only begun to happen in Jaunty?  Maybe after an upgrade?


I had no problems with FireFox and Ubuntu 8.04 32-bit edition.
I'm now running Ubuntu 9.04 64-bit edition.

Wonder if it is something to do with running on 64-bit OS?


Carl

---

### Post by cwmoser on 2009-07-13
ANyone have any idea why not all thumbnails are displayed by FireFox?  Epiphany web browser works just fine.

Is it a bug in FireFox?  I've tried all of FireFox 3.0, FireFox 3.5, and SwiftFox and all of them will not show all the thumbnails as depicted in the thread I posted earlier.

Carl

---

### Post by philinux on 2009-07-13
Your link in the first post loads all images very quickly. I'm using 64 bit.

Maybe create a new FF profile. When you install 3.5 it copies your existing  profile so if there is something amiss it will persist.

---

### Post by cwmoser on 2009-07-13
> **philinux said:**
> Your link in the first post loads all images very quickly. I'm using 64 bit.

Maybe create a new FF profile. When you install 3.5 it copies your existing  profile so if there is something amiss it will persist.

Phillinux, thanks.  Looks like your suggestion fixed the problem that has bene plauging me for weeks.  This solved it:

First I went in FireFox and backed up my Bookmarks, settings, etc.

From the command prompt, I entered as you suggested
$  firefox -ProfileManager -no-remote

I noted a "default" profile and then created another one.
I highlighted t he new profile and started FireFox.

Now, the websites I go to shows all the graphic images.

Thanks so much.

Carl

---

### Post by philinux on 2009-07-13
> **cwmoser said:**
> Phillinux, thanks.  Looks like your suggestion fixed the problem that has bene plauging me for weeks.  This solved it:

First I went in FireFox and backed up my Bookmarks, settings, etc.

From the command prompt, I entered as you suggested
$  firefox -ProfileManager -no-remote

I noted a "default" profile and then created another one.
I highlighted t he new profile and started FireFox.

Now, the websites I go to shows all the graphic images.

Thanks so much.

Carl

Nice one. I'd love to know what exactly gets borked in a profile.

---

### Post by billharris on 2009-08-02
I'm having that problem on one of two Jaunty machines.  Under FF 3.0.11 on machine T, all works well.  Under FF 3.0.12 on machine H, I miss images on certain Web sites (e.g., [http://www.johnlscott.com/](http://www.johnlscott.com/)).  On machine H, Epiphany does just fine.

That just started within the past week.  I don't know exactly when.  AFAIK, I did not do an upgrade around the time it began to fail.

Bill

---

### Post by cwmoser on 2009-08-03
See post #18

Philinux's suggestion worked for me.

Carl

---

