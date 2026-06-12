---
title: "no hulu in jaunty"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by DarinB on 2009-04-25
no hulu i clean install of jaunty

---

### Post by lisati on 2009-04-25
What's "hulu"?

---

### Post by gandaran on 2009-04-25
have you installed flash?

---

### Post by DarinB on 2009-04-25
yes i followed the post and purged the flash then installed them and the restricted ones i even went to synaptic and added the flash transitional package it shows in there that i have installed the adobe flash but still no hulu
this is a big deal since i don't have tv and this is how i watch

---

### Post by gandaran on 2009-04-25
the transitional package is for those that upgraded, what you should install in jaunty is flashplugin-installer.

---

### Post by DarinB on 2009-04-25
i did this but it doesn't work do i added the transitional package
 Re: Flash Video Problems in Jaunty
Do Youtube videos work fine? If they don't then this fix seems to work quite well:

Code:

sudo aptitude purge flashplugin-nonfree

Code:

sudo aptitude install flashplugin-nonfree

You might also be missing some of the required codecs to play the videos on Hulu (Not 100% sure since I don't use Hulu and it's a bit hard to check on dialup)

If that is the case you can fix it by running the command:
Code:

sudo apt-get install ubuntu-restricted-extras

Good luck! And in the future don't be to afraid to try a simple search. I'm sure the answer is already out there.

---

### Post by DarinB on 2009-04-25
help anyone????

---

### Post by kansasnoob on 2009-04-25
Hulu is working for me, I just tried it ........... goody, goody, I've been watching the old Battlestar Galactica episodes.

Anyway the only flash related item I installed after a fresh install was ubuntu-restricted-extras and I use Flashblock (which replaces flash images with a "button" you must click to see the flash object) version 1.5.10 w/ Firefox 3.09 - *install by going to Tools > Add-ons > Get add-ons.*

Anyway, being unsure what flash packages you might have installed, just go to Synaptic and click on "Search" then type *flash*.

The only packages I have installed are adobe-flashplugin and ubuntu-restricted-extras ........... so the "extras" package drug in adobe-flashplugin.

Anyway make sure those are the only flash packages you have installed as the swfdec-* packages and gnash don't perform well.

Be sure to sub xubuntu or kubuntu for the extras package if that's what you're using.

Edit: I forgot to say, if you find gnash or any of the swfdec-* packages installed mark them for complete removal and mark the proper "extras" package for reinstallation.

Then be sure to restart Firefox afterwards.

---

### Post by gandaran on 2009-04-25
> **DarinB said:**
> i did this but it doesn't work do i added the transitional package
 Re: Flash Video Problems in Jaunty
Do Youtube videos work fine? If they don't then this fix seems to work quite well:

Code:

sudo aptitude purge flashplugin-nonfree

Code:

sudo aptitude install flashplugin-nonfree

You might also be missing some of the required codecs to play the videos on Hulu (Not 100% sure since I don't use Hulu and it's a bit hard to check on dialup)

If that is the case you can fix it by running the command:
Code:

sudo apt-get install ubuntu-restricted-extras

Good luck! And in the future don't be to afraid to try a simple search. I'm sure the answer is already out there.
the flashplugin-nonfree doesn't exist in jaunty! it's now called flashpluign-installer, this is the package you have to install for flash, remove every all other flash packages and install only this one, then go to youtube and see if it works.
the ubuntu-restricted-extras in jaunty will install the adobe-flashplugin only if you have enabled the archive.canonical-partner repository, so I believe you have the wrong packages installed!

---

### Post by DarinB on 2009-04-25
how do i add the flashplug installer

---

### Post by DarinB on 2009-04-25
you tube has always workd it is Hulu to watch tv shows very important
so i don't know hoe to add flashplug installler

---

### Post by eilios on 2009-04-25
Did you install restricted extras?

---

### Post by DarinB on 2009-04-25
do you mean this in terminal
sudo apt-get install ubuntu-restricted-extras
yes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
darin@darin-desktop:~$

---

### Post by DarinB on 2009-04-25
i did this and hulu started working

Edit: I forgot to say, if you find gnash or any of the swfdec-* packages installed mark them for complete removal and mark the proper "extras" package for reinstallation.

i removed not complete though of the mozilla swfdec and hulu works i hope it doesn't mess up my mozilla apps but i have hulu 
that is awsome thanks Kansasnoob

---

### Post by regor210 on 2009-04-25
Click on Applications>Add/Remove Applications Click the check mark inside the show box and select (All available application) now in the Search box type ubuntu-restricted-extras 
When you see it in the Application box, click on it then once its marked click Apply Changes. 
after every thing is installed try hulu and see if it works.

I you did not install Jaunty Ubuntu 9.04 AMD64 or if hulu is working forget this next part. 

I installed Jaunty's amd64. The flash Player that came when installing &#65279;ubuntu-restricted-extras did not work with hulu. 

So I went to System> Administration>Snaptic Package Manager  and removed  flashplugin-nonfree.

Then I went here and installed the (64bit Flash Alpha)
[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

I restarted my computer.

Now I can watch hulu and never get white screens in YouTube.

Note. This is an Alpha or experimental &#65279;64bit Adobe Flash Player so it would be a good idea to read what Kilz has to say.  I have been using the Adobe 64bit Flash Player for a long time and have had no problems.

---

### Post by kansasnoob on 2009-04-25
> **DarinB said:**
> i did this and hulu started working

Edit: I forgot to say, if you find gnash or any of the swfdec-* packages installed mark them for complete removal and mark the proper "extras" package for reinstallation.

i removed not complete though of the mozilla swfdec and hulu works i hope it doesn't mess up my mozilla apps but i have hulu 
that is awsome thanks Kansasnoob

It won't break anything.

---

### Post by DarinB on 2009-04-25
any idea why hulu is choppy now it was never choppy in the same pc with intrepid

---

### Post by sports fan Matt on 2009-04-25
Im still at "what is hulu"?

---

### Post by gandaran on 2009-04-25
> **sox fan Matt said:**
> Im still at "what is hulu"?
[http://www.google.pt/search?hl=pt-PT&q=hulu&btnG=Pesquisa+do+Google&meta=&aq=f&oq=](http://www.google.pt/search?hl=pt-PT&q=hulu&btnG=Pesquisa+do+Google&meta=&aq=f&oq=)
[http://www.hulu.com/](http://www.hulu.com/)

---

### Post by kansasnoob on 2009-04-25
> **DarinB said:**
> any idea why hulu is choppy now it was never choppy in the same pc with intrepid

Did you install Flashblock version 1.5.10 as I suggested?

Flash heavy sites tend to "eat" a lot of system resources and Flashblock allows only those flash objects to run that you choose.

For instance here's my Hulu page with Flashblock installed:

[ATTACH]111001[/ATTACH]

You can see that the Flash objects are replaced with a "F" button. If you tick on the button you'll view that Flash object.

The Flashblock version in the Ubuntu repos is horribly outdated so install the new Flashblock by going to Tools > Add-ons > Get Add-ons. then restart Firefox.

Otherwise you could still have some old configuration files lingering from the swfdec stuff .......... not sure how to clean that:confused:

Maybe something as simple as running in terminal:

```
sudo apt-get autoclean
```

But it could require creating a new Firefox profile, **but I'm not sure!**

Also if this is 64 bit I'm clueless.

---

### Post by DarinB on 2009-04-25
i have the flash block working and it does stop in occasion
then it catches up
so any more ideas i also ran 
sudo apt-get autoclean
so that is where i am at.
so far i am really happy that it runs again
maybe a little more tweaking

---

### Post by kansasnoob on 2009-04-25
And when you search "flash" in Synaptic you have only adobe-flashplugin and restricted-extras installed?

If so then I'd go to System > Administration > System Monitor and see what's eating resources while playing a video.

I also didn't ask what version of Firefox you're running?

Do you have only Firefox 3.0 installed? (Check in synaptic)

Firefox 3.1 was phased out by 3.5 but they're both in pre-release stage.

At this point things you could try beyond that:

(1) Install Firefox 3.5 from Synaptic. It'll show up as Shiretoko Browser in Internet Menu.

(2) If that doesn't work then remove 3.5 and go to terminal and run:

```
sudo apt-get -f install
```

It will likely kick you back something like "run apt-get autoremove", remember to use "sudo" and run that command.

Then create a new Firefox profile by using Ubuntuzilla (there are other ways), but I prefer this. Install Ubuntuzilla (choose 32 bit or 64 bit):

[http://ubuntuzilla.wiki.sourceforge.net/#tochome6](http://ubuntuzilla.wiki.sourceforge.net/#tochome6)

Unless you've chosen otherwise it'll download to your desktop, just double click the icon and let it install. (it's perfectly safe to send that desktop dl to trash when you're done).

Next copy this command to Abiword or Open Office:

```
ubuntuzilla.py -a install -p firefox

```

because **Firefox must be closed while running the Ubuntuzilla script!**

Then when you run that command you'll get the true Mozilla build of Firefox! You'll be asked a few simple questions.

---

### Post by DarinB on 2009-04-25
wow thanks amazing amount of knowledge.

---

### Post by Saabtite on 2009-04-25
Get rid of the SWF plugin.  That fixed it for me.

---

### Post by DarinB on 2009-04-25
yes that is what did it for me

---

### Post by tmas98 on 2009-04-26
This worked for me.  Open Synaptic, search for swf, and choose complete remove for swfdec-mozilla.  Then, search for flash and select install for flashblock, adobe-flashplugin, and flashplugin-installer. Click apply and reboot. Hulu is back in the business of turning our brains to mush.

---

### Post by IamJohnHayes on 2009-04-26
thanks for the code,  that was a lot easier than any previous version of ubuntu to make youtube/flash work

---

### Post by Aaris on 2009-04-26
I just wanted to say that this thread was helpful to me.

I was experiencing a strange problem. Hulu was loading and the page said "Done" but nothing was there and no errors were showing. The place where the video should have been was just empty. After reading this thread, I tried a few things including making sure that the swf and gnash items were completely removed. It turns out that I had ubuntu-restricted-extras installed, but for whatever reason it still wasn't working. I uninstalled and then re-installed ubuntu-restricted-extras and now everything works fine once again.

Thanks to all of those who have contributed to this thread. :)

---

### Post by wcGary83 on 2009-04-28
Hi guys!

I am having the same problem, but nothing seems to fix the stuttering 
video on hulu!

This is an upgrade from intrepid, Dell e1505-core duo-2 gigs, and runs
pretty easy when watching video, Firefox eats about 20% cpu, the computer
runs at about 50%...

I checked my packages- flashplugin-nonfree, adobe-flashplugin, 
flashplugin-installer, and restricted-extras, no SWF plugin.

I also ran autoremove (deleted a ton of packages), firefox 3.5, and 
ubuntuzilla, but no luck!

Sound runs fine, but the picture freezes for 1-2 seconds at a time making 
it tough to watch.  Everything else runs smooth, I can torrent unchoked 
no problem, burn DVDs, etc.

Do you guys think my only option would be to run a clean install, or is 
there anything I can still try? maybe an update soon?

Thanks!
Gary

---

### Post by gandaran on 2009-04-28
> I checked my packages- flashplugin-nonfree, adobe-flashplugin,
flashplugin-installer, and restricted-extras, no SWF plugin.
why three adobe flashplugins installed? only one flash package is recommend, firefox can only use one and all of them installed can conflict!

---

### Post by wcGary83 on 2009-04-28
Oh yeah stupid me!

I thought all three were interdependent, but it seems only flashplugin-nonfree and flashplugin-installer are. They must have been left over from intrepid...  Thanks!

But unfortunately, removing the two did not help, same stuttering problem...

Any suggestions?


P.S. I forgot to mention... It seems the video driver might be slow... When effects are on, opening and closing windows are also very choppy unlike intrepid, which ran perfectly smooth no matter what.  Could this be a video driver issue? I have an integrated video card on an e1505, nothing special

update...

It probably is the driver, found this thread
[http://ubuntuforums.org/showthread.php?t=1134984&highlight=jaunty+choppy+video](http://ubuntuforums.org/showthread.php?t=1134984&highlight=jaunty+choppy+video)

---

### Post by 0per4t0r on 2009-04-29
> **kansasnoob said:**
> For instance here's my Hulu page with Flashblock installed:
[ATTACH]111001[/ATTACH]
I know it's unrelated, but what firefox theme are you using? It looks pretty cool (Although it probably wouldn't go with my dark grey and orange theme)

---

### Post by wsonar on 2009-04-29
> **lisati said:**
> What's "hulu"?


Awesomeness:)



It's probably due to not using the adobe version of flash or having multiple versions but I'm sure 30 post in this has been answered already

---

### Post by wsonar on 2009-04-29
> **sox fan Matt said:**
> Im still at "what is hulu"?

If you don't have cable you can watch full episodes of
show's like the daily show, Family guy, Lots of stuff check it out

[http://www.hulu.com]("http://www.hulu.com")

---

