---
title: "Channel4.com player and linux"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by roccivic on 2009-02-23
I'd like to watch Skins on the catch-up service of channel4.com, but the website tells me that I need IE6+ for this. :-&

link: [http://www.channel4.com/video/skins/catchup.html](http://www.channel4.com/video/skins/catchup.html)

I tried Wine and IE6, but it doesn't work... I guess I could install VMWare server and Windoze inside it, but there must be a simpler way... Is there any way of fooling the server into thinking that I'm actually running IE6+ and some Windoze OS?

I'm on Hardy, I have FF3, Seamonkey 1.12 and Opera.

Many thanks for the help.

Rouslan

---

### Post by binbash on 2009-02-23
use user agent switcher extension at firefox

---

### Post by Flimm on 2009-02-23
You could try (in Opera) right-click on page, 'edit site preferences', 'network', 'browser identification', 'identify as Internet Explorer'.

---

### Post by roccivic on 2009-02-23
> **binbash said:**
> use user agent switcher extension at firefox

Thanks man, that resolved half the problem.
Now it doesn't complain about the browser anymore, but it tells me that I need to install Windoze Media Player 11 or greater :-&

Any way around this?

Many thanks again.

Rouslan

---

### Post by roccivic on 2009-02-23
bump

---

### Post by SuperSonic4 on 2009-02-23
What about the vlc plugin ```
sudo apt-get install mozilla-vlc-plugin
```

---

### Post by roccivic on 2009-02-23
> **SuperSonic4 said:**
> What about the vlc plugin ```
sudo apt-get install mozilla-vlc-plugin
```

Tried and failed, but thanks anyway.

BTW, "apt-cache search vlc mozilla" revealed that the package name actually is "mozilla-plugin-vlc"

Any other guesses much appreciated ;)

Rouslan

---

### Post by hobo89 on 2009-02-23
AFAIK there is no way to use 4od or 4 catch up in Linux, other than by installing Windows in VMware and the likes. But there are many other website that stream TV shows, usually in Flash so there are no compatibility issues. Though they will generally be of lower quality than the catch up service, but still watchable.

---

### Post by roccivic on 2009-02-23
Though so... Will take the VMWare-server route then...

Pity channel4 doesn't have forums or blogs, you know, just just to thank them for being such wankers and not including linux or mac support for their apps................

Peace

---

### Post by hobo89 on 2009-02-23
You'd only get the same generic response they give to any emails regarding this. 'Microsoft DRM blah blah blah'. I expect all their users would jump in with the same response too. Would hardly be worth the effort.
At least the BBC have some sense.

---

### Post by simtaalo on 2009-02-23
i think enough emails may make them change mind? no reason bbc can do it and c4 can't.

---

### Post by hobo89 on 2009-02-23
What do you propose? Get as many Linux and Mac users to send an email, all at one set given time, demanding their software supports our systems? It would at least piss them off.

---

### Post by alexcckll on 2009-02-23
> **hobo89 said:**
> What do you propose? Get as many Linux and Mac users to send an email, all at one set given time, demanding their software supports our systems? It would at least piss them off.

There wouldn't have been the hassle if OFCOM had bought a clue and let Kangaroo go live...

---

### Post by t0p on 2009-02-23
> **simtaalo said:**
> i think enough emails may make them change mind? no reason bbc can do it and c4 can't.

The BBC Trust told them to develop a platform-agnostic iPlayer quick smart.  The BBC's public service commitments etc.

And something similar *could* happen with Channel 4.  They also have public service commitments.  If they want to be given cash from public funds, they ought to serve the *whole* public.  Not just the windows users.

---

### Post by roccivic on 2009-02-24
> **hobo89 said:**
> What do you propose? Get as many Linux and Mac users to send an email, all at one set given time, demanding their software supports our systems? It would at least piss them off.

Maybe start a Facebook group and after enough members have signed up, file a formal complaint against channel4.com?

Besides, what's the story with this DRM thing? What the hell does it actually do? DRM or no DRM, I'm pretty sure I can rip just about any content from them without any noticeable quality loss, anyway...

Peace

---

### Post by redseventyseven on 2009-02-24
Does the Channel 4 player really not work for Mac users either? That seems odd, given all the unnecessary MacBook product placement that typifies a lot of their news reports!

---

### Post by roccivic on 2009-02-24
> **redseventyseven said:**
> Does the Channel 4 player really not work for Mac users either? That seems odd, given all the unnecessary MacBook product placement that typifies a lot of their news reports!

Channel4 "only" asks for:
an MS OS,
an MS web browser (IE) and 
an MS media player (WMP) :-&

I personally don't own a Mac, but I doubt that it do the job with such system requirements...

---

### Post by hobo89 on 2009-02-24
Actually according to Channel 4's website, Catch-Up will be available on Mac around March, but they are 'considering various options to make Catch-Up available on further platforms'. So there are options out there, (as the BBC have shown) they are just so damn slow to implement them.
As for the DRM issue:
> Windows Media Player is the most common digital video player in the market and **it works most effectively with Windows Digital Rights Management (DRM) software**, which is the software Channel 4 uses to protect content from being pirated and distributed illegally.
So there are others that also work with Windows DRM, albeit not as effectively, but surely it's for the user to decide whether they use an effective media player or not. DRM also encourages the content to be pirated and distributed illegaly, especially amongst those that it is least available to.

---

### Post by Robinwilli on 2009-03-30
It's a real pity that Channel4 and as far as i know, ITV are not supporting Linux as its the one thing that is stopping me from totally switching my girlfriend over. 
As so many say, its ultimately the tv companies losing out, as the number of linux users grows so they lose out on potential advert viewers and revenue.
Very interesting point someone made earlier about channel4 and public service commitments, i wonder who we have to pressurise about that? It may be more fruitful to find the body responsible for public broadcasting funding / commitments and show them there are a lot of people out there who are not being properly served by C4 / ITV.

---

