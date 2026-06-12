---
title: "Okular on GNOME?"
date: 2011-08-25
forum: New to Ubuntu
---

### Post by ingarion on 2011-08-25
Hello,
I have an HP Mini 210 running Ubuntu 11.04 and I wanted a PDF reader that also allows me to highlight and annotate. I downloaded Okular because I read great review for it. At first, it worked perfectly, but after restarting my computer, the error "Unable to find Okular component" always appears. After a bit of research, I learned that Okular is part of KDE, though I do not need the entire desktop for it to function; I only need kdegraphics. I installed all the necessary kdegraphics packages via synaptic, updated everything, and rebooted, but the same error still occurs. (Though it may be possible that there are other packages that I may have missed.) My questions are: Why did Okular work the first time that I installed it? Why won't it work now that I have installed kdegraphics and what can I do to fix it? Or if you all know an alternative PDF editor, please let me know. :D
Thanks

---

### Post by XubuRoxMySox on 2011-08-25
I annotate pdfs with a way-cool and kid-friendly lightweight application called [Xournal]("http://robinsrantsandraves.wordpress.com/2011/08/10/xournal-a-fun-note-taking-pdf-annotating-app/")! It's actually a note-taking application, but the pdf annotator great! The link above is my li'l "tutorial" about it. Xournal is in the Ubuntu repositories.

-Robin

---

### Post by SeijiSensei on 2011-08-25
On my Kubuntu desktop, an "apt-cache showpkg okular" reveals a lot more dependencies than just kdegraphics including things like kdebase-runtime. 

If you installed okular from the Ubuntu repositories, it should have brought in all the needed dependencies.  If you installed it from somewhere else, you'll have a lot harder time sorting out what it needs.  

Try running:

```

sudo apt-get purge okular
sudo apt-get install okular

```

Any better?

---

### Post by ingarion on 2011-08-25
dixiedancer, thanks for the suggestion! I have tried Xournal before, and the only thing that I don't like about is that the highlighter doesn't stick to the lines. In Okular, when I drag the highlighter along a line of text, only the text is highlighted, and not the area around even, even if the mouse strays away a little bit. This is a bit hard to do on Xournal since I only have a touchpad. Perhaps I have been taught to "color inside the lines" a bit too well. xD

SeijiSensei, I ran "apt-cache showpkg okular", installed all the dependencies, ran the "purge" and "install" commands, and rebooted. But the error still persists. =[ You mentioned "If you installed okular from the Ubuntu repositories, it should have brought in all the needed dependencies." Wouldn't using "sudo apt-get install okular" count as installing form the Ubuntu repositories? Also, when I choose to "Open with..." > "Other Application..." I see over a dozen Okulars on the list. I'm assuming that that is not normal? o_O I noticed this problem before, when it first stopped working, but there were maybe only 8 Okulars on the list...

---

### Post by ingarion on 2011-08-26
I thought about running Okular from the terminal so that it could tell me what exactly goes wrong, so here goes:
```
name@Computer:~$ okular
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kbuildsycoca4 running...
/usr/bin/knotify4: error while loading shared libraries: libpulse.so.0: cannot open shared object file: Permission denied
okular(2451): Couldn't start knotify from knotify4.desktop:  "KDEInit could not launch '/usr/bin/knotify4'." 

okular(2451)/kdeui (KNotification) KNotification::slotReceivedIdError: Error while contacting notify daemon "Process /usr/bin/knotify4 exited with status 127" 
KCrash: Application 'okular' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/charlton/.kde/socket-Charlton-HP/kdeinit4__0

[1]+  Stopped                 okular

```Is anyone able to pinpoint what it is that I need to do?
Thanks in advance. :D

---

