---
title: "Battery Meter Vanished from Panel"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by Andavane on 2010-05-06
I plugged my laptop into the mains, carelessly not noticing that mains wasn't switched on. The battery ran out while I was using it, and on booting again, the battery/power applet had dropped off.

I have been unable now to find it in the R/click add-on options in the panel. I went to System/preferences/power management  & under notification area selected "always display icon"; an icon has now appeared in the top bar but it is completely non-fuhctioning.

I also went to synaptic and checked for broken links - there are none.

I've now run out of ideas over this one, and would appreciate some help.

Best wishes, John

Ubuntu 9.10

---

### Post by _0R10N on 2010-05-06
If I'm correct, there's an option for that, under System->Preferences->Startup Applications

I'll check this when I get home!

---

### Post by Andavane on 2010-05-06
Yes indeed! It's the Power Management Daemon.
It was listed in the start-up applications and the option was ticked.
I unticked it then foolishly removed it
& I need the Daemon back, and up & running :-o

Crikey, I'm screwing stuff up today :-(

Am stumped as to how to get it back....

---

### Post by shebaw on 2010-05-06
Ok I'm not sure if this will work but anyways, I do this whenever I experiment with the panels and mess them up.

[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

It restores your panel back to the original settings so you could hopefully get the batter meter back.

---

### Post by Elfy on 2010-05-06
> **Andavane said:**
> Yes indeed! It's the Power Management Daemon.
It was listed in the start-up applications and the option was ticked.
I unticked it then foolishly removed it
& I need the Daemon back, and up & running :-o

Crikey, I'm screwing stuff up today :-(

Am stumped as to how to get it back....

Go to Preferences - Start Up Apps and add it back in

---

### Post by Andavane on 2010-05-07
> **forestpiskie said:**
> Go to Preferences - Start Up Apps and add it back in

Yes that's what I tried to do, but as I said, I foolishly removed it:
[IMG]http://farm5.static.flickr.com/4039/4586143330_74be13819b.jpg[/IMG]

I'm really asking now: how to add power management back in? If I knew the path to the daemon, I guess I'd be there ;)

Regarding the command line instructions, I'm getting:

[IMG]http://farm5.static.flickr.com/4054/4586143272_b745fc033a.jpg[/IMG]

I think this is because it works on earlier versions of Ubuntu (7.10 & 8.04) and I'm using 9.10

Regards

John

---

### Post by Elfy on 2010-05-07
> **Andavane said:**
> Yes that's what I tried to do, but as I said, I foolishly removed it:
Check the screenshot in my post ;)

It has the information for the power manager there - all you need to do is Add and fill in the boxes.

---

### Post by Andavane on 2010-05-08
> **forestpiskie said:**
> Check the screenshot in my post ;)

It has the information for the power manager there - all you need to do is Add and fill in the boxes.

ummmm yes indeed. It just goes right back in, doesn't it?
:oops:

---

