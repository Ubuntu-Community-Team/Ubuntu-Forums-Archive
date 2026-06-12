---
title: "Change default pdf reader"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by llmunro on 2010-05-05
Hi forum!  I hope someone can help me figure this out, because I've done  everything that I can think to do and I still can't make it work.  I  really prefer Foxit reader over Evince for various reasons and want to  make Foxit my default reader for everything.  I use the Firefox addon  Zotero to manage my dissertation research and the mountains of PDF files  I've collected.  I would like these to open with Foxit rather than  Evince.  Here are the steps that I've taken and their outcomes:

1.  Right-clicked on a PDF on my desktop, selected properties, and  changed the Open With option to Foxit.

2.  Edited some stuff, like so:  

/usr/share/applications
to FoxitReader %F
as well as changing
/etc/gnome/defaults.list:application/pdf
to FoxitReader.desktop

3.  Changed Firefox preferences (Edit>Preferences>Applications)  and selected Foxit from the dropdown menu for PDF.

4. Uninstalled Evince, in the hopes that this would make Foxit the  default (and only!) PDF reader.  (This seemed to fix a similar problem  on my Mint laptop.)  Unfortunately, this didn't work and PDFs began  opening with GIMP!  I re-installed Evince, as I have to have a PDF  reader for Firefox PDFs in the meantime.

Does anyone have any suggestions?  Did I goof somewhere?  

P.S. This is on Lucid and with Firefox 3.6.3.

Thanks much.
Best,
Lisa

---

### Post by mechro on 2010-05-05
Right click any pdf document. Select **Properties**. Choose and/or Add Foxit in the **Open With** tab.

Edit... Er... I posted while you edited so my post is now irrelevant! :)

---

### Post by llmunro on 2010-05-05
Thanks for the post anyways!  For some reason, my itchy clicker finger clicked submit before I was done writing! Then I had to go back and edit! :P

L.

---

### Post by mechro on 2010-05-05
Is it just Firefox with the problem? How does a pdf open from Nautilus?

---

### Post by mc4man on 2010-05-05
Have absolutely no issue setting foxit as the default in lucid. 
using a .deb install [from here]("http://www.foxitsoftware.com/pdf/desklinux/download.html") (1.1

The r. click -> properties -> open with shows FoxitReader as a choice and sets as default for local .pdf's

As far as firefox - much easier to open a .pdf with firefox and set in the dropdown (if you still get a dropdown) - by choosing 'other' and browsing to it (/usr/bin/FoxitReader

(you can set firefox either online or with a local .pdf

Shouldn't be any need to set in defaults.list, probably best not to, the name of the .desktop should be Foxit-Reader.desktop, not FoxitReader.desktop


The default launch command should already be FoxitReader %F so no need to edit, if need be edit it thru alacarte (edit menus) -> Office -> properties of FoxitReader instead.

If you go 
```
gedit ~/.local/share/applications/mimeapps.list
```
do you see something similar - the first listed is default
> application/pdf=Foxit-Reader.desktop;evince.desktop;gimp.desktop;firefox.desktop;

---

### Post by llmunro on 2010-05-05
Hi all,

Thanks for the help and suggestions!

Let's see...

Files opened from Nautilus open in Foxit.  Files opened from Zotero (via Firefox) open with evince.

I had originally installed Foxit using this: 
[https://help.ubuntu.com/community/Foxit](https://help.ubuntu.com/community/Foxit)

rather than the .deb.  Tried installing the .deb as well, and now have foxit and FoxitReader as options.  Have repeated the steps I originally tried with Foxit Reader rather than foxit with the same results.

Have already tried right clicking and setting default "open with" from Nautilus.  The problem is opening PDFs via Zotero/Firefox.  Right clicking on a PDF file in Zotero gives a Zotero-specific set of options rather than the ones that would be in Nautilus.


The command:
gedit ~/.local/share/applications/mimeapps.list

brings up:

[Added Associations]
application/pdf=Foxit-Reader.desktop;userapp-foxit-CAOMCV.desktop;Foxit-Reader.desktop;gimp.desktop;
audio/mpeg=banshee-1.desktop;
x-content/audio-cdda=banshee-1-audiocd.desktop;
x-content/video-dvd=vlc.desktop;
x-content/audio-player=banshee-1-media-player.desktop;

I am not quite sure what it means to edit through alacarte.


Thoughts?

Many thanks for the help.

Best,
Lisa

---

### Post by lovinglinux on 2010-05-06
Close Firefox, then open your FF profile folder (~/.mozilla/firefox/<profile>) then move **mimeTypes.rdf** file to somewhere you can recover it later if this doesn't work, then start Firefox. This will reset all file/application association in Firefox. Open a PDF, choose FoxIt and tick the option to remember it.

BTW, I would recommend trying [gPDF](https://addons.mozilla.org/en-US/firefox/addon/14814). It works like a charm.

---

### Post by llmunro on 2010-05-06
Hi,

Thanks so much for all of the helpful suggestions!  I have no idea what I did, but tried opening Zotero/Firefox PDF's this morning, and they open in Foxit Reader!

This is what I really like about Ubuntu.  Every day, I learn at least five new things about it!

Thanks much to all for the help and great ideas!

Best,
Lisa

---

### Post by Pseudo-Morph on 2011-10-13
For anyone else who stumbles across this thread a solution can be found on the Zotero wiki & forums.

See here:
[http://www.zotero.org/support/kb/file_handling_issues](http://www.zotero.org/support/kb/file_handling_issues)

And here:
[http://forums.zotero.org/discussion/7250/](http://forums.zotero.org/discussion/7250/)

---

### Post by oldos2er on 2011-10-14
Back to sleep....

---

