---
title: "Ubuntu Software Center issue"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by Xenomorph05 on 2009-10-31
Is it just me? I can't get any of the images to load and when I press Install nothing happens? I have tried multiple servers, Canada, Main, USA but I can't download anything with it.

Sorry to add to the pile of new threads but no one seems to have posted this so I wonder if it is just me?

It worked when I first installed 9.10 but it hasn't for the past 24 hours.

---

### Post by Temposs on 2009-10-31
It may be that your mirror is slow or down. It's working fine for me, though a little slower than I'd expect. 

To try another download mirror, go to System->Administration->Software Sources

On the "Download From" list choose "Other". Then click "Select Best Server". When it's done scanning, select "Choose Server". Click "Close" then "Reload". If there are errors then do this whole process again. Then restart any installations you wanted to do before.

---

### Post by Xenomorph05 on 2009-10-31
I have all ready tried that. Regardless what server I try I can not get any images to load or install anything. I can surf and torrent and do updates just fine so I assume it is something with the Software Center.

---

### Post by Temposs on 2009-10-31
Are you able to install things in Synaptic Package Manager? When you open Synaptic, does it inform you of broken packages?

---

### Post by Xenomorph05 on 2009-10-31
Yes sir I can install with the SPM. I just installed one of th software I wanted to with the USC.

---

### Post by Temposs on 2009-10-31
Good. I think maybe there's some kind of bug where you have to install first with SPM before USC. Not sure, though.

I mean, the first time you're using Karmic, you need to use SPM first.

---

### Post by Xenomorph05 on 2009-10-31
I think I worded that last post wrong. I installed one of the software I had wanted to in USC with the SPM instead. 

I just tried the remove with the USC and it doesn't work either. It seems I can only install and uninstall with the SPM.

edit: I tried to uninstall and reinstall USC with the SPM but it did not fix it.

---

### Post by ikisham on 2009-10-31
If that goes on please file a bug. Open SC and click 'report a problem' in the help menu (that even collects automatically useful info for the debugging). It's good to have a [launchpad]("https://launchpad.net/") account if you haven't got one yet.

---

### Post by Xenomorph05 on 2009-10-31
I did as you suggested and it seems there are a few bugs similar to mine already posted.

---

### Post by lawentzel on 2009-10-31
I don't even get an "install button" to appear when I am trying to install applications.  It was a clean load.  The pictures will appear eventually on the software center.

---

### Post by Xenomorph05 on 2009-10-31
> **lawentzel said:**
> I don't even get an "install button" to appear when I am trying to install applications.  It was a clean load.  The pictures will appear eventually on the software center.

When I submitted my bug I noticed that there was a bug with your problem too.

---

### Post by Temposs on 2009-10-31
My Ubuntu Software Center eventually worked after I installed, but I don't remember what I did to make it work. For now, just use Synaptic Package Manager, and wait for an update to the USC program to come through to us. I'm sure they've got someone working on it.

---

### Post by Xenomorph05 on 2009-10-31
My Ubuntu Software Center worked at first but since I updated and installed a few things via terminal it is now borked.

---

### Post by fjcurcio on 2010-02-21
I'm having the same issue; install and uninstall buttons do nothing.
anyone ever find a fix?

---

