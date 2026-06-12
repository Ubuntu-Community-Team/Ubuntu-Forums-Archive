---
title: "Ubuntu 10.04 / Thunderbird 3.0.4 / clamdrib not working"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by thane1 on 2010-05-08
In previous versions of Ubuntu I have gotten mozilla addons [COLOR="DarkRed"]Clamdrib-0.2-tb.xpi[/COLOR] to work in Thunderbird to check incoming emails with clamav prior to sending them to my windows-using-friends.  So far I cannot get it to actually check mail in the new ubuntu/tbird.  Clamdrib works well but unfortunately hasn't been updated for a couple of years,so it won't automatically work with Thunderbird 3.0.4 . After much playing around though (after googling) I have Thunderbird's add-ons preferences feature reporting success in clamav being operational, although in fact this isn't the case.  To get clamdrib supposedly "working" what I've done is the following:  Unzip [COLOR="DarkRed"]Clamdrib-0.2-tb.xpi[/COLOR] .
In clamdrib's clamdrib.js file I changed the line 
[COLOR="DarkRed"]GetFirstSelectedMessage();[/COLOR]   to  [COLOR="DarkRed"]gFolderDisplay.selectedMessageUris[0][/COLOR]
Also changed a line in [COLOR="DarkRed"]install.rdf[/COLOR] file to enable installation - I made the line read:
[COLOR="DarkRed"]<em:maxVersion>9.9</em:maxVersion>[/COLOR]
After making the changes to clamdrib.js and install.rdf files I rezipped everything and then renamed the zip file to have a .xpi (zippy) extension.  (Thanks for these ideas from the mozilla developers pages.  My new version of clamdrib was ready for using as an add-on.  
When I finally got clamdrib working in past versions of ubuntu using advice on this forum (thanks Grege) I needed to remove all clamav programs, restart computer, reinstall clamav programs through Synaptic, start thunderbird and install the clamdrib addon.  This time the add-ons/preferences/settings feature said the required settings of [COLOR="DarkRed"]enable clamdrib[/COLOR], [COLOR="DarkRed"]localhost[/COLOR], [COLOR="DarkRed"]TCPsocket value 3310[/COLOR], [COLOR="DarkRed"]100sec[/COLOR] time and [COLOR="DarkRed"]label only[/COLOR] were there, same as in past instl'ns.  But as in past a check of the [COLOR="DarkRed"]/etc/clamav/clamd.conf[/COLOR] file revealed the [COLOR="DarkRed"]localhost[/COLOR] and [COLOR="DarkRed"]3310[/COLOR] values weren't actually installed. The following lines needed to be added to the [COLOR="DarkRed"]/etc/clamav/clamd.conf[/COLOR] file: set host to [COLOR="DarkRed"]localhost[/COLOR] and set TCPsocket value to [COLOR="DarkRed"]3310[/COLOR].  To do this I manually added changes via [COLOR="DarkRed"]sudo dpkg-reconfigure clamav-base[/COLOR].  Chose [COLOR="DarkRed"]automatic[/COLOR] installation and followed through the prompts changing [COLOR="DarkRed"]Unix[/COLOR] to [COLOR="DarkRed"]TCP[/COLOR], [COLOR="DarkRed"]host[/COLOR] to [COLOR="DarkRed"]localhost[/COLOR] and [COLOR="DarkRed"]TCPsocket[/COLOR] value to [COLOR="DarkRed"]3310[/COLOR].  Exit, restart computer, start up Thunderbird, go to tools-addons-clamdrib-preferences-test settings and I got the following result [COLOR="DarkRed"]Success: ClamAV 0.96/10945/Sat May  8 09:08:44 2010[/COLOR] .  Yippee, except when I then check incoming emails, where there was normally a green "[COLOR="DarkRed"][COLOR="Green"][COLOR="Green"]clean[/COLOR][/COLOR][/COLOR]" message for a clean email, there is now a grayed out "ClamAVstatus" with no result.  Now I'm stuck.  Any ideas?  TIA[COLOR="DarkRed"][/COLOR]

---

### Post by cariboo on 2010-05-08
Just a word of advice, use your white space in your posts, it is pretty hard to read the way it is now. 

I'm using 64-bit Thunderbird on Lucid, most of the addons don't work yet. I very rarely get an email with malware in it, in Thunderbird, they show up as attachments in the preview pane making them easy to remove, once removed, you safely forward the email.

---

### Post by thane1 on 2010-05-09
Sorry.  Guess I'm doing something wrong here, but I don't know what you mean by use my white space.  Does that mean I'm jamming everything in too tight in my post?

---

