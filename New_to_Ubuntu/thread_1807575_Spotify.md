---
title: "Spotify"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by Barn35 on 2011-07-19
Spotify works fine under wine in 11.04:guitar::)

---

### Post by computerandu on 2011-07-19
> **Barn35 said:**
> Spotify works fine under wine in 11.04:guitar::)

Thanks for providing the info...

I am waiting for a Linux version which could be available to all (right now only premium user can use it on linux)
:(

---

### Post by Barn35 on 2011-07-19
I'm using free right now, but definitely going premium. So much better than pandora or slacker. I prefer making playlists to randomizing and having to skip songs all the time.

---

### Post by haddog on 2011-07-30
Go premium. Linux version of Spotify works great. It is a preview version but I have had no issues with it.

---

### Post by stangdaman on 2011-08-03
I'm having issues installing the linux version. Every time I try I get a message that says that action would require installation of non authenticated packages. Does anyone know how I can fix this?

---

### Post by aeiah on 2011-08-03
> **stangdaman said:**
> I'm having issues installing the linux version. Every time I try I get a message that says that action would require installation of non authenticated packages. Does anyone know how I can fix this?

well the solution would be to authenticate the packages :p

in the [instructions](http://www.spotify.com/uk/download/previews/) did you add their public key?
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E
```

---

### Post by stangdaman on 2011-08-03
No, I was lazy and just added the repository to the software center and didn't bother reading instructions. :(

I have it installed now but I'm getting a message that says use of this device is not enabled for this account. Is the linux version only available for the pay accounts?

Sorry, I missed the OP. I'm on a roll today.

---

### Post by aeiah on 2011-08-03
> **stangdaman said:**
> No, I was lazy and just added the repository to the software center and didn't bother reading instructions. :(

I have it installed now but I'm getting a message that says use of this device is not enabled for this account. Is the linux version only available for the pay accounts?

yea. you can run the windows version under wine pretty well though if you want to use the free version. they had problems delivering drm and adverts in a linux native client, so the linux client is pay only.

---

### Post by stangdaman on 2011-08-03
I have it running in Wine now. You're right it is running fine. It would be nice not to have to do that though. Hopefully they'll get that fixed soon. I read on the Spotify forum that it was because the advertisements weren't working on the Linux version. I don't know why that would be but this is fine for now.

---

### Post by stangdaman on 2011-10-10
This was running great in Wine for a really long time but lately every time I try to start up I get a crash report message with the option to send crash report or skip it. If I send it Spotify always closes itself out. If I try to skip it sometimes it does the same thing but usually after a few tries it will allow me to run it. Even than though it will randomly crash. I don't know what changed that is causing to crash so much. Is anyone else having these issues?

---

### Post by ezramorris on 2011-10-10
Just a heads up, I tried installing via Software Sources, and got errors when I tried to do an apt-get update. This seemed to be because a deb-src line was added as well as a deb line. Removing the deb-src line fixed it, however following the instructions on the download page (i.e. editing sources.list manually) avoids this problem in the first place... :)

---

### Post by stangdaman on 2011-10-19
Are you talking about the linux client or the windows version installed in Wine?

Also, I tried uninstalling and than reinstalling the latest version and I noticed that it's crashing still but that right before it does it is displaying a message that says that I am using an unsupported platform. Did spotify put something in to stop you from using it in Wine. If so that is highly obnoxious especially since they are advertising on their website that it does work in Wine.

---

### Post by ezramorris on 2011-10-19
> **stangdaman said:**
> Are you talking about the linux client or the windows version installed in Wine?

Also, I tried uninstalling and than reinstalling the latest version and I noticed that it's crashing still but that right before it does it is displaying a message that says that I am using an unsupported platform. Did spotify put something in to stop you from using it in Wine. If so that is highly obnoxious especially since they are advertising on their website that it does work in Wine.

I'm using the Linux client, and when I run it it constantly says at the top that I'm using an unsupported platform, despite it working completely fine otherwise.

I'm guessing "unsupported" here means "we won't help if it doesn't work".

---

### Post by stangdaman on 2011-10-19
> **ezramorris said:**
> I'm using the Linux client, and when I run it it constantly says at the top that I'm using an unsupported platform, despite it working completely fine otherwise.

I'm guessing "unsupported" here means "we won't help if it doesn't work".

Hmm, I'm getting the same message from the windows client in wine. I was very much enjoying using Spotify on my laptop. So disappointed right now.

---

### Post by endontoddy on 2011-10-19
On the bright side it doesn't appear to make any difference to the actual running of the app :) and they keep making updates so it doesn't look like thy are going to drop it. One of my PCs get the crash dialog every time I start Spotify but if i click skip it always loads fine anyway.

As an aside, I think its well worth paying the £5 a month for no adverts and unlimited play, and it's vastly superior to the alternatives.

---

### Post by stangdaman on 2011-10-20
> On the bright side it doesn't appear to make any difference to the actual running of the app  and they keep making updates so it doesn't look like thy are going to drop it. 

It is for me. It's currently unusable. I'm back to Pandora.

---

