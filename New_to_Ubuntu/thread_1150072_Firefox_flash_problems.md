---
title: "Firefox flash problems"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by baddnady23 on 2009-05-05
When viewing flash videos in firefox, sometimes some will load while others wont.  Is there a way to mitigate this?

---

### Post by RealPSL on 2009-05-05
Are the ones that do not load always the same ones and if so can you provide an example link to one of them?

---

### Post by rushmobius on 2009-05-05
I don't know if it is Flash related, but for all of the HD trailers at [http://www.apple.com/trailers]("http://www.apple.com/trailers"), I have to open them in a new tab, and then hit F5 to force it to reload to play.

---

### Post by pastalavista on 2009-05-05
Some videos won't load if Ad-Block plus is being used. Disable it for that page only and reload/refresh the page. If you aren't using it, then... well never mind

---

### Post by baddnady23 on 2009-05-05
For example,  "high quality" videos on youtube

---

### Post by jkd18 on 2009-05-06
I wasnt getting audio in my you tube videos so reinstalled Flashplayer... now I can see videos in a preview window BUT NOT AT ALL in any regular video link...! There is ust a black window- no play button, nothing!!! HELP!!!! I m a filmmaker- occupational disaster! ;-(

---

### Post by pastalavista on 2009-05-06
I suspect you are using Gnash or some other open-source version of Flash. Go to Tools > Add-ons and install the Adobe Flash-player plugin.

---

### Post by Zeedok on 2009-05-06
> **jkd18 said:**
> I wasnt getting audio in my you tube videos so reinstalled Flashplayer... now I can see videos in a preview window BUT NOT AT ALL in any regular video link...! There is ust a black window- no play button, nothing!!! HELP!!!! I m a filmmaker- occupational disaster! ;-(

Check in Firefox under addons to see if the plugin is listed there (ie tools > addons).  If it is not (which is possible if you are not getting anything) then the reinstallation went awry.  I have recently - since upgrading to Jaunty - had trouble getting my flash running (made worse by my fiddling with multiple web-browsers) and I found the easiest way to get everything right is to install adobe acrobat reader from their website (download the reader 8.1 .deb file and install it like you would a windows program) and uninstall gnash player via synaptic (if that is also installed).  Your problem could be that Firefox doesn't know where the plugin is, but if you just want a fix without getting into too much detail, that's what I would do (cause it worked for me).

PS - the adobe flash player is in the same package as adobe reader - just in case that is confusing!

---

### Post by jkd18 on 2009-05-06
People, Ok- I istalled Adobe Flash, but synaptic tells me if i uninstall gstreamer i lose Cheese among other applications... :-( 

but at least now i can see and hear apple streaming video- no you tube yet... nor google video...!

---

### Post by jkd18 on 2009-05-06
BTW, all videos were working fine till a few days ago when audio went from u-yube and to fix that i installed adobe flash. Does that help any?!

---

### Post by baddnady23 on 2009-05-06
sounds like there are multiple problems with 9.04 then?

---

### Post by baddnady23 on 2009-05-06
another example is that video on CNN will not load up either.  I tried installing adobe reader but no dice either...

---

### Post by Nigec on 2009-05-17
I'm having the same problems, a good example is this silly game i did [ here]("http://www.nigecstudios.co.uk/games/room1.html")
the loader and intro work but the game appears black, if it helps it was done in AS2 player 9

It could be down to permissions, should the plugin say adobe flash in firefox?

its a new install of Ubuntu, and a newbie so I could of got it wrong lol

ah.. I just checked properties and its not the adobe its swfdec

edit, 
problem fixed by:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

