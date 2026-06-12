---
title: "Google street view Broke after winetricks flash install"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by enixon on 2010-03-22
Google street view is acting up after installing flash in winetricks. It worked fine before hand. Street view is functional now it's just sized wrong.

[IMG]http://downtownadaptive.com/uploadsparefolder/Screenshot.png[/IMG]

As you can see the black area shouldn't be there. The street view "view" should extend to the borders but does not. This isn't a big deal, but is annoy on a 15 inch laptop. Once in street view it will also not allow you to exit back to the map, and the cursor is a bit off from the mouse x,y position when trying to navigate. 

Can some one verify that this is a winetricks flash issue? Should I file this as a bug?

---

### Post by OriginalName on 2010-03-23
Hi, 

I'm sure I'm stating the obvious here - Why don't you use the linux flash version ;-)

---

### Post by enixon on 2010-03-23
I assumed I was. I've got both installed because a program I was emulating with wine required flash for winetricks. Is there a way to preference one over the other?

---

### Post by OriginalName on 2010-03-23
Nope, you're using the Windows version of (I'm guessing from the screenshot) Google Chrome - So when you've installed flash through Winetricks it's installed the Windows flash version... the Windows GC "looks" for flash to be installed in the fake Windows file system Wine creates not the linux libflash.so (or whatever it is...)

Basically you can't get Windows GC to use Linux flash because, well, because they're different! It'd be like trying to get it to use Mac OSX flash...

---

### Post by waynefoutz on 2010-03-23
> **enixon said:**
> I assumed I was. I've got both installed because a program I was emulating with wine required flash for winetricks. Is there a way to preference one over the other?


It would seem to me if that's the Linux version of Google Chrome you have running there, it would be calling up the Linux version of Flash. If that's the Windows version of Chrome running under Wine, you should run the Linux version. Also that's a boatload of tabs you have open in Chrome.

---

### Post by OriginalName on 2010-03-23
> **waynefoutz said:**
> It would seem to me if that's the Linux version of Google Chrome you have running there, it would be calling up the Linux version of Flash. If that's the Windows version of Chrome running under Wine, you should run the Linux version. Also that's a boatload of tabs you have open in Chrome.

I agree entirely... I assumed at the mention of Wine we were using the Windows version... :p

---

### Post by enixon on 2010-03-31
Yeah, you were right. Google Maps works fine in Firefox. Any idea how to disable wine flash for chrome?

---

### Post by marshmallow1304 on 2010-03-31
To use Linux Flash in Chrome, you'll need to install the Linux version of Chrome.  You can get a beta version [here]("http://www.google.com/chrome?platform=linux") or use a [PPA for Chromium]("https://launchpad.net/~chromium-daily/+archive/ppa").  In my case, Chromium found my Flash (I had it in ~/.mozilla/plugins) and used it automatically.

---

### Post by enixon on 2010-04-03
I have chrome installed. It was installed before wine flash so it must have been directed to use the other version. Is there a way to tell it which version to use or would a uninstall/reinstall work?

---

