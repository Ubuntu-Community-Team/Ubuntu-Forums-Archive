---
title: "I have no sound"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by Chris Edgell on 2010-02-09
You can't believe that my friend gave me another"old" Dell.
When he brought it over, I put the liveCD in and installed  it on the entire HD.  You may remember I did this to another machine three or four days ago -- and never got sound.  I was told on that thread, that, YES I should get sound, right out of the box, so to speak.

So with this one, I had high hopes.  I went right to YouTube and it told me that I need Adobe and/or Java.  Even though I've been told not to download from anyplace besides Synaptic (or the software center?)  But at that point I didn't give a darn..... even then I got an error message saying I need libnspr4-dev.  I went and looked at Synaptic, THAT wasn't there.  I looked for Adobe, well, THAT wasn't there.  I looked at the restricted extras and saw that they HAD been installed with the liveCD.  I was thinking that sometime back, maybe Hardy maybe Ubuntu (as opposed to Jaunty Xubuntu), that I had seen Sun Java in the synaptics, but not now.  Wherever I got "Sun"Java, I don't know, but now as I go and look at JavaScript I see that there are about 10 apps that have the word Java.

So shall I install them all?

---

### Post by patchwork on 2010-02-09
Are you comfortable enough from the command line to try:

```
sudo apt-get install sun-java6-plugin
```

If it is not available, check your repository sources.  I've never worked in a true Xubuntu environment, but it might be available through one of the non-default source options.

---

### Post by Chris Edgell on 2010-02-10
Hi patchwork,
Before I read your post, I had decided well why not install the Java...it could always be removed. I only clicked on two lines: 1) JavaCommon and 2) libbackport. As I began the process a window said 15 new packages will be installed and 194 packages will be upgraded. 209 being downloaded. total of 269 MB Do you think the upgrades for the release got mixed in here somehow or no, was it all connected to Java...(I can't think so as I was monitoring stuff as it went by and it was mentioning cups, brasero, evince, firefox, gimp...and on and on and on. It probably WAS the updates...just like 3 or 4 days ago when I KNEW it was the updates. Well, I shouldn't even say it, it HAD to be the updates.)

NOW I try to get back to synaptic and get this message...see screenshot.  I must assume this has something that I was running in the terminal as per patchwork...

---

### Post by thatguruguy on 2010-02-10
If you have synaptic and update manager open at the same time, synaptic will throw that message.

---

### Post by thatguruguy on 2010-02-10
wait. did you still have apt running in the terminal when you opened synaptic?  That will cause that message, too.

---

### Post by Chris Edgell on 2010-02-10
I went and opened the update mgr and then closed it.  Then I went to synaptic and still got that lock message.

---

### Post by Chris Edgell on 2010-02-10
Well , it's true, maybe I didn't wait till terminal finished.  What to do now?

It's a real shortcoming of mine to think something is done....I've been told, "Give it more time."

---

### Post by thatguruguy on 2010-02-10
Wait until terminal is finished, then close it. Then, open synaptic.

---

### Post by Chris Edgell on 2010-02-10
How would I know?   When I open terminal, it looks like a fresh start...totally blank...

---

### Post by patchwork on 2010-02-10
What guru was referring to was to make sure only one or the other was running, i.e. if Synaptic or the Update Manager is running (or in the system tray), apt (in the terminal) will not have exclusive right, and vice-versa.  Try either closing Synaptic and the Update Manager, and installing from the terminal, or bypass the terminal completely and install from Synaptic (without the Update Mangager active)

---

