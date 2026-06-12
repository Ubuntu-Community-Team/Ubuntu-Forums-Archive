---
title: "Some flash objects play, but others dont.."
date: 2009-05-03
forum: New to Ubuntu
---

### Post by qjmoss on 2009-05-03
I just recently installed 9.04.

Whats the deal with the "play" button on bulletins or adds on websites,

And why doesnt myspace music player load when I load a webpage, I tried to install flash player, but it came up as unnecessary.


Any information would help greatly.

Thank you

---

### Post by MontelEdwards on 2009-05-03
```
sudo apt-get install ubuntu-restricted-extras 
```

---

### Post by cor135 on 2009-05-08
hello,

seems i have the same, or a very similar problem. you tube works, but myspace music player doesn't. im very new to ubuntu and i was playing around with add/remove and synaptic...so i have most likely deleted something i needed.

when i tried the above code, the output contained this - 

ubuntu-restricted-extras is already the newest version.

if someone could point me in the right direction that would be Awesome!

Thanks.

---

### Post by MontelEdwards on 2009-05-08
hmm,
strange.
The only thing that i can say now is to directly download Flash from Adobe.

---

### Post by Pjotrovitz on 2009-05-08
You could always try to reinstall the flashplugin-nonfree package:

sudo aptitude reinstall flashplugin-nonfree

---

### Post by kansasnoob on 2009-05-08
Well, when you say "buttons" that's indicative of either Flashblock or a similar add-on.

I'd begin (in Jaunty only) by going to synaptic and clicking on Search (not rebuilding or quick search) and typing flash. The only packages you should see installed are ubuntu-restricted-extras and adobe-flashplugin. Any swfdec* or gnash packages should be marked for complete removal! (It will not break anything, it's the equivalent of purge remove)

As far as Add-ons I like Flashblock whick replaces Flash objects with a button, but the version in the repos is ancient! Install only the add-ons you want using the Get Add-ons feature in Firefox!

---

### Post by james_mcl on 2009-07-11
Hi Cor135.

I suggest closing your browser, deleting the hidden ~/.macromedia folder, then reopening it and trying again.

(Please see my post at [http://ubuntuforums.org/showpost.php?p=7600753&postcount=2](http://ubuntuforums.org/showpost.php?p=7600753&postcount=2) for an explanation of why I think this might work.)

James.

---

