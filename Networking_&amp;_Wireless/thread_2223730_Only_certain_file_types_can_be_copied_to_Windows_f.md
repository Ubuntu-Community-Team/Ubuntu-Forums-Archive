---
title: "Only certain file types can be copied to Windows from Ubuntu"
date: 2014-05-12
forum: Networking &amp; Wireless
---

### Post by WB0HYQ on 2014-05-12
I hope this is in the right place.  I've searched the forums, but searching didn't turn up anything.

If I am at my Ubuntu machine (12.04LTS) I can use the network to reach my other machines (mostly Windows 7) and "see" the shared directories.  I attempted to copy several JPG files from Ubuntu to a shared Windows directory and got an error telling me "Error while copying 'Screenshot........JPG' to smb://prinserver/public_c/" and the "see more" provided "invalid argument".

On the Windows machine(s), if I 'push' a JPG to the Ubuntu machine it works, but the reverse fails.  Text files, Document (.DOC) files, and all that type will transfer just fine.

I've done some experimenting and I find that I cannot transfer (so far) JPG, GIF, MP3.  BUT, if I zip them up into either a .GZ or .ZIP file, I can transfer them and unzip at the Windows end.

Is there some weird network permissions thing at work here?

Bill

---

### Post by WB0HYQ on 2014-08-02
Looking at some of my old posts, I realized this one never got an answer.  It is still happening as I described even in 14.01.

Any answer here?

Bill

---

### Post by The Cog on 2014-08-02
My first guess would be the antivirus software on the windows machine.
I assume these file names don't contain characters that are illegal in windows.
Have you tried just changing the file name extension and then copying it across?

---

### Post by WB0HYQ on 2014-08-02
That's what I though at first, but even briefly stopping the A/V didn't allow picture files through.  It did allow EXE files both directions though, which makes me wonder.  I renamed a couple of pictures (JPG) files to simply a.jpg through z.jpg and tried to move them from Ubuntu to Windows7.  No go.  They wouldn't move unless I zipped them up and copied them that way.

Changing the extension to XXX didn't allow them either.  I changed one of them to a.exe and it did get moved.

Very strange.

Bill

---

### Post by The Cog on 2014-08-03
That really is strange. 
I thought that changing the extension might fool any av, but maybe that's not enough. I suppose that any self respecting file scanner would look inside to work out the type.

Are you saying that just changing the extension from .JPG to .exe allowed the file to move OK? How about if you rename a JPG as .DOC or .TXT? If so, that is significant. It rules out issues with file sizes, and bit patterns in the file, and directly implicates something at a higher level that wants to know about different file types. I am certain that must be something on the windows side. Does it have UAC enabled? I have seen UAC do some truly strange things that make the machine unusable.

---

### Post by WB0HYQ on 2014-08-03
I changed extension to a few common ones.  TXT and DOC made it, but GIF, PNG, and JPG won't go.  I suspect that something (as you say, probably in WIndows) is examining the headers and finding a picture and rejecting it.  Of course, that won't hold water because if I ZIP the files up, then the whole shebang copies just fine.  I do agree that Windows is probably the culprit as I can push anything FROM Windows to Ubuntu, just not the other way.

I've been using Windows since before Windows 3.0 so the very first thing I do when setting up my computers now is getting rid of that horrible crud called UAC.  I am behind a hardware firewall in my router (so I can safely turn off my computer firewall for testing) and when I do that nothing changes - certain files just won't copy.

I do a lot of photo editing and I like doing it on my Ubuntu machine in Gimp.  I know Gimp runs on Windows, but my Ubuntu machine has a larger screen.  For now, I just use a 16G thumb drive and transfer that way (or ZIP them up).  I just thought the non-transfer of pictures was odd.

Bill

---

