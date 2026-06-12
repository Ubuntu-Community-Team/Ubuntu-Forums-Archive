---
title: "Flashplayer not working?"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by grant4353 on 2009-09-20
Howdy,

I'm trying to use this website, [www.tairabunkai.com]("http://www.tairabunkai.com") to watch the videos. I haven't really been having problems with videos using Ubuntu before, having recently started using Ubuntu. But this one wont seem to play. I clicked on info and it says swfdec, which I think I have, because I also tried to install and it said that swfdec has already been installed. Could it be a different version? Does it require a certain codec or player? I don't know much about this stuff. When I had windows the video on the site ran fine.

Any suggestions?

---

### Post by Windows Nerd on 2009-09-20
Have you installed the newest flash player from adobe's website?

If not, go to:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

And download it. It will automatically detect which operating system you use, and give you the correct download link accordingly.

It downloads as a .deb. Double click it and it installs itself worry free.

Scott

---

### Post by grant4353 on 2009-09-20
Hey Thanks for the info!

I went to the site and downloaded it and installed it, it said that I had already had installed it. So I went back to the site I mentioned in the opening post and the video still didn't play.

Any other suggestions?

---

### Post by erilidon on 2009-09-20
I just install the "ubuntu restricted extras" which installs flash among many others.

---

### Post by grant4353 on 2009-09-20
Thanks eliridon.

I'm looking for a site to get right now. Any recommendations?

Anyone use VLC? I used to use that with windows.

---

### Post by lidex on 2009-09-20
Aha. You really should peruse this thread:
[http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

You are using Firefox, correct??

---

### Post by erilidon on 2009-09-20
yeah, I have VLC installed on all my computers, Works great! what do you need to know?

---

### Post by the.phantom on 2009-09-20
to get the restricted extra's

applications

and search for "restricted extra's"

note
i could view that site with that and default media player

---

### Post by grant4353 on 2009-10-04
Howdy,

So I installed the restricted extras and the video on the site still isn't running for me. Any thoughts on the matter?

I think I'll see about installing VLC but Idk if that works for that sort of video.

---

### Post by sandyd on 2009-10-04
this line
```

<td style="border-width: 1px; border-style: solid; border-color: #9999CC; width: 50%;"><a href="[http://www.okinawadirect.com/shopdisplayproducts.asp?id=115&cat=Saifa+Bunkai+E%2Dbook]("http://ubuntuforums.org/view-source:http://www.okinawadirect.com/shopdisplayproducts.asp?id=115&cat=Saifa+Bunkai+E%2Dbook")" target="_blank"><img src="[../../../../../flash/Advert.jpg]("http://ubuntuforums.org/view-source:http://www.tairabunkai.com/flash/Advert.jpg")" alt="TairaBunkai Saifa Bunkai E-book II - Contains over 430 color photographs covering 29 bunkai variations for Saifa" width="175" height="290" border="0" /></a>  </td><td style="border-width: 1px; border-style: solid; border-color: #9999CC; width: 50%"><object classid="clsid:D27CDB6E-AE6D-11cf-96B8-444553540000" codebase="http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=7,0,19,0" width="330" height="290">
  <param name="movie" value="../../../../../flash/senden384K.swf" />
  <param name="quality" value="high" />
  <embed src="[../../../../../flash/senden384K.swf]("http://ubuntuforums.org/view-source:http://www.tairabunkai.com/flash/senden384K.swf")" quality="high" pluginspage="http://www.macromedia.com/go/getflashplayer" type="application/x-shockwave-flash" width="330" height="290"></embed>
</object></td>


```
seems to be the one giving trouble btw.

---

### Post by grant4353 on 2009-10-04
> **carlee said:**
> this line
```

<td style="border-width: 1px; border-style: solid; border-color: #9999CC; width: 50%;"><a href="[http://www.okinawadirect.com/shopdisplayproducts.asp?id=115&cat=Saifa+Bunkai+E%2Dbook]("http://ubuntuforums.org/view-source:http://www.okinawadirect.com/shopdisplayproducts.asp?id=115&cat=Saifa+Bunkai+E%2Dbook")" target="_blank"><img src="[../../../../../flash/Advert.jpg]("http://ubuntuforums.org/view-source:http://www.tairabunkai.com/flash/Advert.jpg")" alt="TairaBunkai Saifa Bunkai E-book II - Contains over 430 color photographs covering 29 bunkai variations for Saifa" width="175" height="290" border="0" /></a>  </td><td style="border-width: 1px; border-style: solid; border-color: #9999CC; width: 50%"><object classid="clsid:D27CDB6E-AE6D-11cf-96B8-444553540000" codebase="http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=7,0,19,0" width="330" height="290">
  <param name="movie" value="../../../../../flash/senden384K.swf" />
  <param name="quality" value="high" />
  <embed src="[../../../../../flash/senden384K.swf]("http://ubuntuforums.org/view-source:http://www.tairabunkai.com/flash/senden384K.swf")" quality="high" pluginspage="http://www.macromedia.com/go/getflashplayer" type="application/x-shockwave-flash" width="330" height="290"></embed>
</object></td>


```seems to be the one giving trouble btw.

Cool, so what does that mean?

---

### Post by tuxxy on 2009-10-04
Is this 64-bit Ubuntu?

---

### Post by grant4353 on 2009-10-04
> **tuxxy said:**
> Is this 64-bit Ubuntu?

Ah I don't know, how do I check for that?

---

### Post by lidex on 2009-10-04
Try this:

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-installer
```


One line at a time please.

---

### Post by RandyRandola on 2009-10-04
I had a small problem (don't ask lol ) and thought I would start over. Everything worked fine (well, my Devede stopped and I was trying to get that to work again) but everything else was good.

I installed 8.04 and now Devede 3.12c doesn't work, AND I can't get this flash to work either. There must have been an update somewhere and blew everything up. Reminds me of Windoz....

But this is my error message when I follow the above commands...

E: Couldn't find package flashplugin-installer

---

### Post by lidex on 2009-10-04
Do you have "multiverse" repository enabled? Check it in gnome menu: System>Administration>Software Sources. On the first tab - "Ubuntu Software" make sure first four options are checked. Click "close" and allow it to update. Then try to install again.


ps = you can run this command to find os version info:```
uname -a
```
the string will contain "x86_64" if your ubuntu is 64 bit

---

### Post by grant4353 on 2009-10-07
> **lidex said:**
> Do you have "multiverse" repository enabled? Check it in gnome menu: System>Administration>Software Sources. On the first tab - "Ubuntu Software" make sure first four options are checked. Click "close" and allow it to update. Then try to install again.


ps = you can run this command to find os version info:```
uname -a
```the string will contain "x86_64" if your ubuntu is 64 bit

Yea I did that and I didn't see the "x86_64" and I checked and the first four options are checked, still not working. Any other ideas?

---

### Post by grant4353 on 2009-10-07
Is there a way to watch streaming videos with video programs like VLC or the one that comes with Ubuntu? Maybe I should try that if you can. I'm going to contact the administrator on the site and see if he knows what would work.

---

### Post by lidex on 2009-10-08
Try running those commands I gave in previous post but instead of the last line use this:
```
sudo apt-get install flashplugin-nonfree
``` Then make sure you restart your browser.

BTW what version of ubuntu and browser are you using? Are you able to view flash on other sites?

---

### Post by grant4353 on 2009-10-11
> **lidex said:**
> Try running those commands I gave in previous post but instead of the last line use this:
```
sudo apt-get install flashplugin-nonfree
``` Then make sure you restart your browser.

BTW what version of ubuntu and browser are you using? Are you able to view flash on other sites?

Ok thanks I'll try that, my Ubuntu version is 9.04 and firefox is 3.0.14.

I'm able to view flash on other sites, youku.com, and youtube was working fine but as of like three days ago it isn't working for me. I do have the restricted extras installed also and flash player ten I think.

I just searched in the add/remove application and I dont have macromedia flash plugin installed, should that be installed? I also don't have swfdec flash, gnash, and movie play totem installed.

---

### Post by sandyd on 2009-10-11
> **grant4353 said:**
> Ok thanks I'll try that, my Ubuntu version is 9.04 and firefox is 3.0.14.

I'm able to view flash on other sites, youku.com, and youtube was working fine but as of like three days ago it isn't working for me. I do have the restricted extras installed also and flash player ten I think.

I just searched in the add/remove application and I dont have macromedia flash plugin installed, should that be installed? I also don't have swfdec flash, gnash, and movie play totem installed.
flashplugin-nonfree IS flashplayer.

just install that first and see if it works.

---

### Post by lidex on 2009-10-11
Conflicting plugins are known to cause flash issues so, no, you don't want gnash or swfdec installed. The cure for me was to remove everything flash-related and then install flashplugin-installer. However you state you cannot install it, although I know for a fact it is in the Jaunty Repositories. There is another route. Go here:
[http://packages.ubuntu.com/jaunty-updates/flashplugin-installer]("http://packages.ubuntu.com/jaunty-updates/flashplugin-installer")

At the bottom of the page under "Download flashplugin-installer" click on the i386 link and on the next page click one of the mirrors to download the deb package. You can install it by double-clicking the downloaded file unless GDebi is not installed. In that case I would recommend installing that from "Add/Remove Applications" as it is a useful tool.

---

### Post by grant4353 on 2009-10-11
> **lidex said:**
> Conflicting plugins are known to cause flash issues so, no, you don't want gnash or swfdec installed. The cure for me was to remove everything flash-related and then install flashplugin-installer. However you state you cannot install it, although I know for a fact it is in the Jaunty Repositories. There is another route. Go here:
[http://packages.ubuntu.com/jaunty-updates/flashplugin-installer](http://packages.ubuntu.com/jaunty-updates/flashplugin-installer)

At the bottom of the page under "Download flashplugin-installer" click on the i386 link and on the next page click one of the mirrors to download the deb package. You can install it by double-clicking the downloaded file unless GDebi is not installed. In that case I would recommend installing that from "Add/Remove Applications" as it is a useful tool.

Thanks a bunch for your help folks! It's fixed now, I did the commands you told me to do and now it's working!

Sweeet.

---

