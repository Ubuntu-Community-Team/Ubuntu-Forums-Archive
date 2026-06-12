---
title: "CBC.CA Concerts on Demand"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by Antedeluvian on 2009-11-27
Does anyone have any idea  why Ubuntu does not play  the CBC  Media Player like all other sources?
 I enjoy streaming concerts from many  sources, from smalls ones like the Steam Powered Preservation Society. to large resources like BBC, Scotland.  CBC  Canada has an excellent archive of concerts but when I try to listen to a concert from CBC I get the first song about 5 minutes after I open it, then a delay for another 5 minutes for each piece of music. Often I get nothing.

I use Ubuntu8.04

---

### Post by cariboo on 2009-11-28
You may need to install the w32codecs/w64codecs and non-free codecs from the [Medibuntu]("http://https://help.ubuntu.com/community/Medibuntu") repositories. I just tried one of the cbc.ca concerts, and it start almost right away.

---

### Post by Antedeluvian on 2009-11-28
> **cariboo907 said:**
> You may need to install the w32codecs/w64codecs and non-free codecs from the [Medibuntu]("http://https://help.ubuntu.com/community/Medibuntu") repositories. I just tried one of the cbc.ca concerts, and it start almost right away.

Thanks, you give me hope. I checked and I had both installed already, so I reinstalled them.

Unfortunately the result was the same. I could not access Audio from Concerts on Demand or news from the Video on CBC.  

Any more advice would be welcome, I learn a little more most days.

---

### Post by mc4man on 2009-11-28
While i'm using karmic atm (where cbc cod plays fine w/ totem-mozilla plugin) booted up a relatively stock hardy install.

There are 3 plugins that you could try, totem-mozilla, mozilla-mplayer and gecko-mediaplayer.
search them in synaptic and try one at a time, don't have more than one installed at a time.

Screen shows playback with the mozilla-mplayer plugin installed

If you have medibuntu installed you'll get an ok mplayer install, otherwise many options for a better one in hardy, just ask.

The audio used is wma2 which is decoded thru libavcodec, there are 2 streams available - 64k, 128k, not sure what the in-browser player uses.

You could also try this - right click on the 'play all' link and copy link location.
Then in terminal do something like this ( or try below to test

 ```
mplayer -playlist [COLOR="Blue"]http://www.cbc.ca/radio2/media/20091001milnr/all.asx[/COLOR] -aid 2

```

Also ck. on your gstreamer plugins, see [here ]("http://ubuntuforums.org/showthread.php?p=8400112#post8400112")

---

### Post by Antedeluvian on 2009-11-29
Thanks to you for  your assistance.  I now have the CBC COD and audio archives playing. 
However I still have not been able to access the video stream where I used to watch the news. As always any advice on this is welcome.

 > **mc4man said:**
> While i'm using karmic atm (where cbc cod plays fine w/ totem-mozilla plugin) booted up a relatively stock hardy install.

There are 3 plugins that you could try, totem-mozilla, mozilla-mplayer and gecko-mediaplayer.
search them in synaptic and try one at a time, don't have more than one installed at a time.

Screen shows playback with the mozilla-mplayer plugin installed

If you have medibuntu installed you'll get an ok mplayer install, otherwise many options for a better one in hardy, just ask.

The audio used is wma2 which is decoded thru libavcodec, there are 2 streams available - 64k, 128k, not sure what the in-browser player uses.

You could also try this - right click on the 'play all' link and copy link location.
Then in terminal do something like this ( or try below to test

 ```
mplayer -playlist [COLOR=Blue]http://www.cbc.ca/radio2/media/20091001milnr/all.asx[/COLOR] -aid 2

```Also ck. on your gstreamer plugins, see [here ]("http://ubuntuforums.org/showthread.php?p=8400112#post8400112")

---

### Post by mc4man on 2009-11-29
> ....to watch the news

If possible post link to the page where you're trying to access news ( is there just one news or different ones for different area's...?

---

### Post by Antedeluvian on 2009-11-29
I want to watch "Here And Now", evening news from St. John's. 

This is the link
[http://www.cbc.ca/video/#/News/Local_News/NL/](http://www.cbc.ca/video/#/News/Local_News/NL/)

> **mc4man said:**
> If possible post link to the page where you're trying to access news ( is there just one news or different ones for different area's...?

---

### Post by mc4man on 2009-11-29
no go here, maybe read 
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/455852](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/455852)

---

### Post by Antedeluvian on 2009-11-29
I will conclude this by thanking for the assistance in getting the access to the CBC concerts on demand. For now getting the CBC video stream will have to wait. From what I have read in is likely dependent on CBC  responding to help solve this bug.> **mc4man said:**
> no go here, maybe read 
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/455852](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/455852)

---

