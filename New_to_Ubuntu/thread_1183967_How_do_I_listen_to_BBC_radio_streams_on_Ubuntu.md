---
title: "How do I listen to BBC radio streams on Ubuntu?"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by petermadd on 2009-06-10
Hi,
Been using Ubuntu 8.04 for about 3 weeks now on a Toshiba netbook. I am delighted with it and have managed to solve a few problems. So far my only real disappointment is that I have to return to my Windows based laptop to listen to internet radio streams for local BBC radio or use BBC  iplayer. Have wandered about the help pages with no success.Perhaps I should accept that nothing is perfect! Pete

---

### Post by ddrichardson on 2009-06-10
You can use BBC iPlayer but you need to accept the experimental license. I haven't a link but if you poke around the site you'll find it.

---

### Post by CatKiller on 2009-06-10
> **petermadd said:**
> So far my only real disappointment is that I have to return to my Windows based laptop to listen to internet radio streams for local BBC radio or use BBC  iplayer. 

I'm pretty sure that the iPlayer (or at least the streams from their site) just uses Flash, Java, and RealMedia's codec for the streams themselves. The ubuntu-restricted-extras package should pull in everything that you need to install those. You might need to enable the Universe repository.

---

### Post by ddrichardson on 2009-06-10
> **CatKiller said:**
> I'm pretty sure that the iPlayer (or at least the streams from their site) just uses Flash, Java, and RealMedia's codec for the streams themselves. The ubuntu-restricted-extras package should pull in everything that you need to install those. You might need to enable the Universe repository.
You'd be wrong ;-)

---

### Post by CatKiller on 2009-06-10
> **ddrichardson said:**
> You'd be wrong ;-)

Well, maybe. But I certainly don't have to resort to using Windows to listen to streams from the BBC. Or save them to listen to later for that matter.

And I certainly haven't installed the BBC's client.

---

### Post by ddrichardson on 2009-06-10
Here's the labs link: [http://www.bbc.co.uk/iplayer/labs](http://www.bbc.co.uk/iplayer/labs)

---

### Post by ddrichardson on 2009-06-10
No need to get excited - that's what the smiley indicates.  There is Linux support for the client, its just not in the main site.

---

### Post by ddrichardson on 2009-06-10
Anyway, once you accept the Beta, click the download link under the episode you want as usual then it'll install AIR and the BBC client.

---

### Post by CatKiller on 2009-06-10
> **ddrichardson said:**
> No need to get excited - that's what the smiley indicates.  There is Linux support for the client, its just not in the main site.

Of course :)

My point is just that the OP doesn't have to install an experimental client to use the BBC. It's a shame that they insist on proprietary technology at all, so that it can't just work out of the box. But if you've got the normal proprietary stuff installed that many people would have anyway, you don't need to install anything extra.

Personally, I tend to use mplayer --dumpstream which you can't do with their client anyway. But you can with the tools that come with the ubuntu-restricted-extras package.

---

### Post by ddrichardson on 2009-06-10
Normally I'd agree and I'd like to see an OSS solution but then again, I pay my TV license and aren't particularly keen to see others get access for free - the DRM is pretty unobtrusive in any event.

---

### Post by Cheesemill on 2009-06-10
> **ddrichardson said:**
> I pay my TV license and aren't particularly keen to see others get access for free - the DRM is pretty unobtrusive in any event.

You only need a TV license for the live streams.
At present you are allowed to download and watch previously broadcasted programmes with iPlayer without a license (although how long this will last I don't know).

Cheesemill

---

### Post by petermadd on 2009-06-11
Hi DDR,
Thanks for the link. I can now use iplayer to playback TV. When I try to listen to radio however still no joy. Thanks once again fo your help.
Pete

---

### Post by mister_p_1998 on 2009-06-11
If you want to download the shows as mp3 look into get_iplayer
[http://linuxcentre.net/getiplayer/](http://linuxcentre.net/getiplayer/)

Steve

---

### Post by solitaire on 2009-06-11
Have you tried the BBC Sidebar in Totem (Movie player)?

You might find what you are looking for there. (it's experimental but there are a few radio stream on there)

---

### Post by grappler on 2009-06-11
If we're talking radio rather than TV I can and regularly - every day -  do listen to the BBC using three different ways. I'm running ubuntu jaunty 64bit on a lenovo t61p.

1. I don't know what I've installed (certainly mplayer, realplayer, etc) - but nothing special from BBC. When I click on a programme in the schedules of, say, bbc7 in the firefox browser it takes me to another page with a button on it.  When I click on that it opens iplayer and usually, but not always, plays the programme. 

2. If it fails I right click on the button and download the link. If I then click on this it opens up the "BBC iplayer console" and gives me an option to open in realplayer. This always works. 

3.  I've installed get_iplayer 

[http://linux.softpedia.com/get/Multimedia/Video/get-iplayer-46788.shtml](http://linux.softpedia.com/get/Multimedia/Video/get-iplayer-46788.shtml)

This allows me to download from the command line all schedules for all BBC programmes and to stream or record in a range of formats. It is a command line application but it has an excellent man page.

I  don't know what more one could need.

---

### Post by petermadd on 2009-06-11
Tried to install getiplayer. Downloaded OK but wouldn't install. I am using Ubuntu 8.04.
Pete

---

### Post by philinux on 2009-06-11
I have a default install Jaunty. I have not got iplayer or adobe air installed. However I can listen to radio streams and view iplayer flash content. I think radio streaming is flash based. as right clicking on the stream gives "about adobe flash 10".

Maybe the OP has not got flash installed.

---

### Post by mister_p_1998 on 2009-06-11
> **petermadd said:**
> Tried to install getiplayer. Downloaded OK but wouldn't install. I am using Ubuntu 8.04.
Pete

Go on the Get_Iplayer site and search for the SVN install, that worked for me..
Steve

---

### Post by Scunnered on 2009-06-11
I received a lot of assistance which lets me have full benefit of all BBC Radio & TV output in the UK.

Suggest that you look at "**Access to BBC radio & iPlayer in the UK via Jaunty**"
as it worked for me.

Hope this assists

---

### Post by ddrichardson on 2009-06-12
> **philinux said:**
> Maybe the OP has not got flash installed.
Yes you only need flash to watch but what people are usually after is the ability to download shows and watch them later, which requires accepting the labs agreement, downloading Adobe Air and installing the iPlayer app.

---

### Post by philinux on 2009-06-12
The OP was..

How do I listen to BBC radio streams on Ubuntu?

---

### Post by bekind2thenoob on 2009-06-12
What streams are you trying to listen to?

Im listening to the 20-20 on the bbc sport site as I type.

Its streaming windows media but totem plays it fine from the browser as long as you have the ubuntu-restricted-extras package installed.

Btw I've been using the iplayer client since it was beta and I'm very happy with it no stability problems and vidoe quality is fine on my machine

---

### Post by ddrichardson on 2009-06-12
> **philinux said:**
> The OP was..

How do I listen to BBC radio streams on Ubuntu?

No, that's the title. He said:
> So far my only real disappointment is that I have to return to my Windows based laptop to listen to internet radio streams for local BBC radio ***or use BBC iplayer***.

---

### Post by petermadd on 2009-06-12
Whoops! Or should have read and. Pete

---

### Post by Chalfont on 2009-06-24
So

The question still stands.
I go to the BBC radio 4 page.
I click on the Live now link.

In windows this opens real player in a separate little pop up and away goes the PM programme with lots of news and views.

In Linux it just sits there and after a while says there seems to be a problem with content try again later.

So how do I get the BBC streaming of the current radio 4 to play in Linux?

Please note I do not yet understand where to do things or get things so please be specific.  Using Ubuntu 9.04 with teh classic standard desktop in brown.

Logging off and going back to Windows so I can hear the BBC now.

---

### Post by Scunnered on 2009-06-24
**Chalfont**

I listen regularly to BBC and received great assistance when I requested it against the following post heading :

Access to BBC radio & iPlayer in the UK via Jaunty

If you follow the advice given there you will be able to fully listen to all the UK output from the BBC.

I note that you remarked about Radio 4 and that you seemed to be having a problem there.  I have been having no end of problems with it also.  There is some problem with the software and the Beeb say if you go to [http://www.bbc.co.uk/radio4/](http://www.bbc.co.uk/radio4/) and click on the listen live button in the top right things will work OK

Trust this assists

---

### Post by Chalfont on 2009-06-24
Two problems.
1.  I searched on the subject you posted and it brought me to this same thread, not sure how.

2.  Did all the stuff about going into Labs and clicking there, it took me back to teh normal iPlayer as far as i can see, and still no Radio 4.  I tried teh alternative link to teh Radio 4 page, clicked on teh top right, takes me to iPlayer again and still no joy.

I don't want to oad some strange software that is going to download everything, I just want the current broadcast streaming file.

How come it's so hard? I thought having sound coming through teh browser would be a pretty integral thing by now, not somethig that takes forever to problem solve.

---

### Post by Chalfont on 2009-06-24
x

---

### Post by nothingspecial on 2009-06-24
You have Rhythmbox?

You want to listen to radio 4?

Close rhythmbox and type

```
rhythmbox http://www.bbc.co.uk/radio/listen/live/r4.asx
```

---

### Post by drifter2502 on 2009-06-27
To play all BBC Radio stations in ubuntu including Listen Again follow the instructions here ...[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) . Download  Downloadhelper ...[https://addons.mozilla.org/en-US/firefox/search?q=downloadhelper&cat=all](https://addons.mozilla.org/en-US/firefox/search?q=downloadhelper&cat=all) . Now go to BBC I Player (make sure you allow site in No Script or whatever)and select say Radio 4 listen live. Click on drop down on Downloadhelper icon in tool bar and download the the r4.ram file to your desk top. This should open Totem and play R4 listen live. If you want to 'Listen Again' you may find it better to select Low Bandwidth at the bottom of I Player window and it should load and play. I have all BBC national radio station ram icons on my desktop including a local station.

---

### Post by t0p on 2009-06-27
> **ddrichardson said:**
> Yes you only need flash to watch but what people are usually after is the ability to download shows and watch them later, which requires accepting the labs agreement, downloading Adobe Air and installing the iPlayer app.

Yes, you can do that.  Alternatively, you could get **[get_iplayer]("http://linuxcentre.net/getiplayer/")** - a lean, mean command-line download machine.  Don't be frightened by the command-line interface, get_iplayer is very easy to use.  You can download radio shows, plus tv shows from the BBC, ITV, Channel4, Five.  Plus it's nice and Free, unlike the BBC tools (Free as in Freedom).

---

### Post by typos1 on 2009-06-27
I m having a similar problem-as soon as I get the iplayer box on the screen it says it doesnt seem to be working. Tried all the suggestions suggested-nothing

---

### Post by drifter2502 on 2009-06-27
#typos1. Have you got Totem.Gecko Player,gstreamer,flashplugin-nonfree and all other essential packages installed?  As per....[http://ubuntuforums.org/showthread.php?t=76668](http://ubuntuforums.org/showthread.php?t=76668) . It should work!

---

### Post by ddrichardson on 2009-06-27
> **t0p said:**
> Yes, you can do that.  Alternatively, you could get **[get_iplayer]("http://linuxcentre.net/getiplayer/")** - a lean, mean command-line download machine.  Don't be frightened by the command-line interface, get_iplayer is very easy to use.  You can download radio shows, plus tv shows from the BBC, ITV, Channel4, Five.  Plus it's nice and Free, unlike the BBC tools (Free as in Freedom).
I'm hardly afraid of the command line and certainly don't need to be patronised nor do I need any information on free software.

If you recommend the command line, you get told its too complicated and when you recommend the way the user is used to in Windows you get told the command line is much better.

Damned if you do and damned if you don't.

---

