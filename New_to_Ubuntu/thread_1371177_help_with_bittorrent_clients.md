---
title: "help with bittorrent clients?"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by knurledflanges on 2010-01-03
Greetings all. I recently had some virus issues with Windows and decided to throw in the towel for using Windows day-to-day, and am now on Ubuntu. 

My machine is pretty old - 1.2ghz/1gb. I do a lot of downloading with bittorrent. Almost everything goes on a big external hard drive. I do occasionally take the hard drive other places, and I have some kind of BIOS problem where the system hangs if the hd is plugged in when I turn the computer on, so it's fairly common for my OS to be running without the harddrive plugged in.

Now, here's my problem. For a bitorrent client under XP, I was using the BitTorrent client, and it worked very well. I usually have a large number of large torrent files loaded, and am usually downloading a couple things. I prefer to only use a "full-featured" bt client, with easy selection of individual files to download. BitTorrent satisfied this under windows and the nice thing is that somehow it was extremely low-footprint. The performance hit while running other major programs at the same time was tiny. I'd like some recommendations for something that might be able to do the same under Ubuntu.

So far, I've used a bunch of "simplified" clients that I don't really like (Transmission, Bittornado), and Deluge, which has the features I like but has 2 issues for me. The first is that when it's running it "feels" like it's slowing things down more than I'm used to, but only a bit and to an extent I can probably live with. The second is more major: when I start it without my external drive plugged in, which is going to happen to me sometimes whether intentional or not, it sets all the loaded torrents on the drive to 0%, and then it requires that they be re-checked once the drive is present again, which if I had my full collection loaded would take days. BitTorrent didn't do this -I could just select everything and press the play icon once the drive was plugged in, and everything would just go- and I haven't found a way around it in Deluge, although I'd be happy with it if I could.

I see that there's linux source files available for the BitTorrent client at [http://www.bittorrent.com/btusers/download/directory-list#section-linux](http://www.bittorrent.com/btusers/download/directory-list#section-linux), but compiling is way beyond me at this point. Does anyone know of a package of it that I can download somewhere?

Anyone got any tips for me? Thanks.

---

### Post by Methuselah on 2010-01-03
Have you tried Vuze (formerly Azureus).
I have never used it but some people like it.

There is also the option to try bittorrent in wine but that might be a fiar bit of work to set up.
Once again, I've never done that either as the default clients are usually fine for me.

---

### Post by knurledflanges on 2010-01-03
Thanks, I'll give it a try, but I have strong doubts from experience using Azureus on this and other old machines... I've always found it to be the most resource-demanding of all of them, although I liked a lot of other things about it. Maybe things will have changed...

---

### Post by lovinglinux on 2010-01-03
I am a big fan of Deluge, but I'm using KTorrent since I switched to KDE and I'm loving it. Perhaps you could try it, although it will install some kde dependencies don't know how many).

Anyways, why don't you plug the hard drive before starting Deluge?

To avoid needing to re-check all torrents, you could make a backup of Deluge's configuration folder every time you exit the application, so if you accidentally start deluge with the hard drive unplugged, then simply close it, restore the configuration folder and start it again. Deluge will remember the state of all torrents.

Deluge configuration folder can be found at ~/.config/deluge. The state of torrents are saved there, along with the application preferences.

BTW, I don't see a good reason to use a proprietary Windows client under wine, when you can get open source native clients that do a better job. 

Azureus is indeed one of the most resource demanding clients out there. It is a very powerful client, but has too many options that are usually not used and uses Java. I try to avoid anything that uses Java.

---

### Post by WhiteHorse on 2010-01-03
I use Vuze, It IS a resource hog and now it keeps asking me for money(nagware). I recommend using the default client Transmission. It sucks but you'll get your downloads just the same without driving your machine into the ground.

---

### Post by knurledflanges on 2010-01-21
Just an update to anyone who might find this thread later on: I basically settled on Transmission. It seems respectably low footprint and is pretty stable for me, and I can deal with having to double click, go to Files and then select what I want to get next, although I think it's a really poor design choice to have to click around so much to get to such a commonly needed place, and if it's a philosophy thing about trying to get people to download the whole file, I don't really like or buy into that. I'll probably keep an eye towards new clients or maybe try BitTorrent or uTorrent under wine eventually. KTorrent wasn't very stable for me with large files in the works, but I did like it.

Couldn't find any answers to the file verification problem with Deluge. Being diligent about only starting it with the drive plugged in isn't really a workaround I like because I don't like the idea of being punished for using a bt client without the drive present. I like to seed a bunch of stuff and having to watch Deluge re-verify it all just because the drive wasn't plugged in once isn't really tenable for me.

Tried out Vuze and it is just way too heavy for this machine if I want something that just runs quietly in the background without cutting into everything else's resources too much.

Thanks for the help all.

---

