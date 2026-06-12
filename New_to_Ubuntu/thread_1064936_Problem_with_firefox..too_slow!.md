---
title: "Problem with firefox..too slow!"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by dazle on 2009-02-09
Hi...
I've noticed that when Transmission Bit torrent is working my browser is much slower...I don't know If it is relevant but when I exit the program it seems to be working just fine!
Can anyone help with that?
Or maybe,If it's not because of the Transmission,what can be slowing down Firefox?
Please..It is really annoying!!
Thnx

---

### Post by mistypotato on 2009-02-09
You have "X" amount of bandwidth.  When your computer is downloading or uploading data, it uses up your available "bandwidth".  I would expect your browsing to be slower when that's in progress.

Unless you have a 6.0 GB + data transfer rate.

---

### Post by LowSky on 2009-02-09
If you are downloading or uploading files ove rthe intenet, then anything you also do will take a hit.

You can t be downloading huge files, and expect to be playing a online game and or surfing the net at the same speeds as you would without downloading

---

### Post by irishbeer on 2009-08-26
I have the same problem. Some notes:

My Internet connection is 20Mb/s
I have not problems using SeaMonkey (Mozilla)
No problems under Windows Vista (same computer using Ares or Bittorrent)

it happens only with Firefox. (3.5.2)

---

### Post by Damon68 on 2009-08-26
I had the same problem downloading with transmission and using firefox, and as everyone above has mentioned the bandwidth currently in use is going to be an issue, BUT,

if you havn't tried some of the firefox "tweaks" you may want to give them a go, my firefox runs pretty good even when downloading with transmission at around 800+ kb/s

These are all tweaks from within this forum and many thanks to the people that posted them, 
*** I unfortunatly didn't save the original links just the tweaks ***

or do a search for firefox tweaks in ubuntu forums and find the original posts

The tweaks I saved:

Firefox tweaks

type in about:config

search for network.http.pipeling  --  Normally false change to true
network.http.pipelining.maxrequests  --  Default it says 4 under value field and you need to change it to 8
network.http.proxy.pipelining  --  Normally false change to true
network.dns.disableIPv6  --  Normally false change to true
plugin.expose_full_path  --  Normally flase change to true

Now you need to Create new Preference name with interger value for this got to Right click -> New -> Integer
type nglayout.initialpaint.delay and click ok
Now you need to enter 0 in value filed and click ok

Now you need to Create one more Preference name with interger value for this got to Right click -> New -> Integer
Here you need to type content.notify.backoffcount and click ok
Now you need to enter 5 in value filed and click ok

Now you need to Create one more Preference name with interger value for this got to Right click -> New -> Integer
Here you need to type ui.submenuDelay and click ok
Now you need to enter 0 in value filed and click ok

Some more Tweaks

Enable the spellchecker for inputfields and textareas (default is textareas only)

layout.spellcheckDefault=2

Open lastfm://-links directly in amarok

network.protocol-handler.app.lastfm=amarok
network.protocol-handler.external.lastfm=true
Firefox Memory Leak Fix

Open a new tab. Type “about:config” without quotes into the address bar and hit enter/click Go.

Right-click anywhere, select New, then Integer. In the dialog prompt that appears, type:

browser.cache.memory.capacity

Click OK. Another dialog prompt will appear. This is where you decide how much memory to allocate to Firefox. This depends on how much RAM your computer has, but generally you don’t want to allocate too little (under 8MB), but if you allocate too much, you might as well not do this. A good recommended setting is 16MB. If you want 16MB, enter this value into the dialog prompt:

16384

(Why 16384 instead of 16000? Because computers use base-12 counting. Thus 16 megabytes = 16384 bytes. Likewise, if you want to double that and allocate 32MB, you’d enter 32768.)

Click OK to close the dialog box, then close all instances of Firefox and restart. If your Firefox still uses the same amount of memory, give it a few minutes and it should slowly clear up. If that fails, try a system reboot.

-------------------------------------------------------------------------

Good luck and hopefully that helps alittle :)

Damon

---

### Post by MyR on 2009-08-26
Opera!!

(Yeah, I'm that guy)


Or try another bt client like deluge (package deluge-torrent)

peace

---

