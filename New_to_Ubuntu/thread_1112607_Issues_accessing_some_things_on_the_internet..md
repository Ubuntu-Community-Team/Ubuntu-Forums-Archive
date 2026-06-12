---
title: "Issues accessing some things on the internet."
date: 2009-03-31
forum: New to Ubuntu
---

### Post by LOswalt on 2009-03-31
Alright, recently I've noticed I can't access things like videos, games, and interactive websites.
I wanted to watch Chuck online, but all I get is this loading screen and the NBC symbol.
([http://www.nbc.com/Chuck/video/episodes/?vid=1076101](http://www.nbc.com/Chuck/video/episodes/?vid=1076101) link)
[http://musicovery.com/index.php?ct=us](http://musicovery.com/index.php?ct=us)
I can't click on anything on the website above.
And this website is off-limits to me, too.
[http://www.questfortherest.com/](http://www.questfortherest.com/)

What do I need to do in order to be able to watch/play with these things?

---

### Post by aeiah on 2009-03-31
flash

---

### Post by gldearman on 2009-03-31
You need to install support for restricted formats, such as flash.

See if this page helps you.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Hope it does.

---

### Post by 123456789123456789123456 on 2009-03-31
Sounds like firefox does not have the nessary addons/components installed/updated to view this content.  This is not supprising since most web browsers don't, and the sites are set up to inform windows machines about the nessary components.  you need to search for a component for firefox that is able to play windows media file format, I would also update java, flash, pdf also.  Not to mention make sure that video player programs have all codecs needed.  I would also download and install VLC, it is a free media program, plays all dvd's, cd's, VCD, and SVCD, along with 99% of other video formats.  download and install the following way.
in terminal
type "sudo apt-get install vlc"
it will ask for password
after entering this, press enter, it will downlaod, and install for you.  It also comes with firefox plugins, that may allow you to view the content of those web pages.

---

### Post by rockin_goliath on 2009-03-31
I usually run these commands as part of my post installation routine. It installs flash and the packages you need to play dvds. Works like a charm everytime. Just open up a terminal window and cut and paste each line.

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo apt-get install -y ubuntu-restricted-extras libdvdcss2 libdvdnav4 libdvdread3 non-free-codecs ffmpeg
```

---

### Post by LOswalt on 2009-03-31
> **rockin_goliath said:**
> I usually run these commands as part of my post installation routine. It installs flash and the packages you need to play dvds. Works like a charm everytime. Just open up a terminal window and cut and paste each line.

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo apt-get install -y ubuntu-restricted-extras libdvdcss2 libdvdnav4 libdvdread3 non-free-codecs ffmpeg
```

The first one keeps giving me invalid host name.

BTW, I've done like all the downloading I can find based off everybody's links.

---

### Post by gldearman on 2009-03-31
Still not working?

Check the following:

In Firefox, open Tools>Add-ons, and go to the "Plugins" tab.  Do you have a plugin installed for Shockwave Flash?  Is it Enabled or Disabled?

---

### Post by baconn on 2009-04-02
I am having the same issues with certain websites, esp. those with videos.  I teach and use my laptop to show videos overhead using [www.howstuffworks.com](www.howstuffworks.com) and can't access videos using my Ubuntu 8 computer.  

Ive done all the stuff in the above threads--plugins enabled for Firefox, VLC installed updated etc.   Still not working.

---

### Post by abyssius on 2009-04-02
> **baconn said:**
> I am having the same issues with certain websites, esp. those with videos.  I teach and use my laptop to show videos overhead using [www.howstuffworks.com](www.howstuffworks.com) and can't access videos using my Ubuntu 8 computer.  

Ive done all the stuff in the above threads--plugins enabled for Firefox, VLC installed updated etc.   Still not working.

Type ```
about:plugins
``` in the Firefox address bar. You must see

```

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r22

```

listed. If you don't then you don't have flash player installed.

---

