---
title: "Missing Help files"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by Wheel on 2011-02-06
Hi,
(Using GNOME)
Over the past several months, I have added several manuals/help files to  the Help system's bookmarks.  I refer to them now & then when a  question arises.  I had bookmarked help info for Synaptic, Evolution,  Desktop User Guide, Brasero and a few others.  Very helpful.

Today, when I try to access any of these bookmarked manuals, the only thing that opens is the main page of Shotwell. 
This seems pretty weird.
One exception--my DeVeDe Manual (added to the bookmarks in Help just this past week), DOES appear and I can read it.
I tried uninstalling Shotwell, thinking it was interfering in some way.  This didn't fix the problem.
(As of right now, Shotwell remains uninjstalled.)

So, I can no longer access the other manuals even though each of these  items still appears on the bookmark dropdown.  If I click on Synaptic,  for example, it shows me the table of contents for Synaptic's manual.   But when I click on any chapter name to view it, I get a small window  with an error message.  The contents of this error window are exactly  the same (except for the name of the desired file itself), regardless of  which manual I am attempting to view.

This is what I see:

Could not load image "synaptic.xml"         (Or "evolution.xml", or "user-guide.xml" and so on)
Unrecognized image file format.

(I'm not too tech savvy, but I don't think these should be "image" files, should they?)

What I have done recently which may have affected this:

--Clean install Maverick a few weeks ago. 
(Is this just a Maverick problem?  I mean, did the Maverick install somehow short circuit the previously installed manuals?))
--Explored Shotwell, importing some photos from the hard drive (all disposable, by the way) to look at the slide show.
--Explored burning a couple of DVDs with DeVeDe and Brasero
(I had also installed a bunch of gstreamer stuff while tinkering with Brasero.)

Does anyone have any ideas about this?

---

### Post by LewRockwellFAN on 2011-02-08
I'm no expert but I'll hazard a guess since you haven't been answered yet. It sounds to me like your system is trying to open xml files with some image viewer like EOG. Try finding an xml file, by searching for *.xml with file search for instance, open the folder containing it, right clicking on it, click properties, click the "open with" tab, then select the right program. Offhand I'm not sure what the right program should be. Probably it will still appear in the list of choices and you can experiment. Perhaps the help program itself. Perhaps gedit. Or you could try reinstalling the help program from Synaptic.

---

### Post by Wheel on 2011-02-08
> Try finding an xml file, by searching for *.xml with file search for  instance, open the folder containing it, right clicking on it, click  properties, click the "open with" tab, then select the right program.Tried a few different .xml files and explored all offered programs available to open with, but found nothing which would help.  

 > Or you could try reinstalling the help program from Synaptic.     Re-installed Yelp via Synaptic (did not uninstall it first if that matters).  This also did not fix the problem.
But I do appreciate the suggestions.

I'll keep tinkering.

I guess as a last resort, I might go back over all of the Brasero/DeVeDe stuff I recently did and try to un-do it to see if that clears this up....

---

### Post by LewRockwellFAN on 2011-02-13
Does that mean you weren't able to open any .xml files at all after you found some to try? If so, that sounds like we are on the on the right track. Did you try right-click,open_with_other_application,gedit? Did you notice what application was set as the default to open these files? "Image" to me, sounds like it is trying to use either a picture viewer like EyeOfGnome, or, less likely, an iso mounter, or a partition cloning tool, which might possibly call the files they operate on "images". For what it is worth, xml files are just specially formatted text files. The formatting rules are fairly flexible so that xml has been adapted to do many different things with different kinds of programs but any of them can still be read by any text editor although presumably only the program they were meant to be read by, or one designed to emulate it, will know what all the indents and whatnot are supposed to mean. Like I said, I'm no expert, but that's my 2 cents for what it is worth. I had some similar problems with Narwhal but I decided to fall back to 10.04 rather than track them down as Narwhal wasn't really ready for use yet anyway.

---

### Post by Wheel on 2011-02-13
Thanks for being there, LewRockwellFAN

> Does that mean you weren't able to open any .xml files at all after you found some to try?(I  didn't realize that xml files were a form of a text file.  The word  "image" threw me off a bit.  To my un-tech mind, an image is a visual  representation of something, like a photo for example.  The terminology  is always what confuses me when I'm trying to learn new things.)

With  one exception, I am unable to open any of these xml help document  files.  And until I saw the first error message-window, with the  filename displayed at the top, I did not know that these WERE xml files.
As  earlier mentioned, I AM able to open the help docs for DeVeDe, but I'm  not certain if that help doc is also an xml file or not.  I don't know  where to look to figure that out.  And DeVeDe was added to the system  AFTER Maverick was installed.


 > Did you try right-click,open_with_other_application,gedit? Did you  notice what application was set as the default to open these files?  "Image" to me, sounds like it is trying to use either a picture viewer  like EyeOfGnomeWent through the entire list of offered "open with" alternatives.  
Image Viewer is the default app to open with.  Eye of Gnome.  That's right.

This is what happened when I selected each of those alternatives (looking at Synaptic.xml):
1)Appearance--Opens appearance prefs.
2)Archive Manager--Get a message: "Could not create the archive".
3)Autorun Prompt--Does nothing.  (Hey, I'm trying everything here)
4)Buzztard Music Editor--Opens Buzztard Music Editor.
(I  never noticed Buzztard on Lucid.  I'm not sure if this is built in to  Maverick or if this was installed     when I played around with DeVeDe  and Brasero.  BTW, I have no music on my hard drive.)
5)Document  Viewer--Only gives me an error message:   "Unable to open document.   File type docbook document (application document + xml) is not  supported."    
6)File Browser--"Could not display.  Location is not a folder."
7)Firefox--Opens  a window which says:  "This xml file does not appear to have any style  information associated with it.  The document tree is shown below."   What is shown is more-or-less legible English, but include lots of stuff  I don't understand. 
8)Gedit--Displays essentially the same content as the Firefox selection, in a much less legible form.
(Ignore the above smilie--it's just a mis-click.)
9)Open Office Word Processor--Only get an error message:  "General error.  Input/output error."
...That's everything on the list.

I have also noticed this;
When I file search for synaptic.xml, 3 items are displayed.
The actual folder-- dated Sept, 2010--which gave me access to the above items,,  AND
2 very small (55 bytes each) broken links, each with a date of Jan 17, 2011. 
(Jan 17, 2011 is the day I installed Maverick.)
Again, I'm left thinking:  Did the Maverick install trash the help docs which I had added to the Help bookmarks on Lucid?
But  then again, since Maverick was a CLEAN install, and not an upgrade,   how would it even know what I had bookmarked when using Lucid?

I've been thinking about reverting to Lucid, but I thought I'd try to sort this out first if I can.

---

### Post by LewRockwellFAN on 2011-02-13
> **Wheel said:**
> To my un-tech mind, an image is a visual  representation of something, like a photo for example.
That is precisely the sense meant in the error message you are reading and it is the surprising use of the word than made me suspect EyeOfGnome as the culprit. I suggest trying this:

Find some xml file with file search. Open the directory it is in. Right click on it and click "properties". Click the "Open With" tab. Click the little round circle to the left of "Firefox". Now it should have a little black dot in the circle after you click it. If it doesn't, click it again until you get that little black dot there. Then click the "Close" button. You have now changed the default ap for opening xml files from EyeOfGnome, which is totally inappropriate, to Firefox, which may not be the right one for all circumstances but WILL open them without choking generally. Firefox is marked as default on my system and I don't remember resetting it so presumably it is the out of the box default. And it kind of makes sense since it wouldn't be surprising for the help files to be intended to be read with a hypertext reader (i.e., a "web browser"). You could check properties again to be sure the change took. You might even need to reboot. I'd give even money (but no odds!) your help will work after that. Please let us know.

As to why Gedit didn't open the file I'd forgotten how incredibly picky Gedit is. It apparently gives up if it encounters any characters it doesn't recognize.  I miss Edlin and Notepad. I need to investigate Nano and some Linux text readers.

---

### Post by Wheel on 2011-02-19
Hi again,

I followed your suggestion and changed the default from Image Viewer to Firefox.  Re-checked properties afterward and it is now set to Firefox.

Then I tried to open synaptic.xml and it did open with Firefox, but what is displayed was exactly what I saw when I previously ran through the entire list of offered alternate programs which could be set as default for opening these files.  

Those results are itemized in my previous post.  Firefox was #7 on that list.

What I saw did contain some English, but also included lots of carets, and other symbols which I don't understand (some kind of internal commands I'm guessing).
It's not really legible; it's certainly not a simple page of text the way the help doc is supposed to display.

I re-booted and see the same thing.

And gedit does open the file--sort of.  It's displayed similar to the way Firefox displays the content, although it contains even more illegible stuff.  This is also on the list in my previous post.

Thanks for the effort.  

This is a puzzler....

---

### Post by LewRockwellFAN on 2011-02-22
Then I'm stumped. That's frustrating because I feel sure we have half the problem figured out. Eye of Gnome should definitely NOT have been the default for opening an xml. Ahh ... wait a sec ... - you reinstalled Help, but maybe it isn't Help that was the problem but the documents it reads. I don't know why several such should all go bad at the same time but maybe you might get some results from looking in Synaptic for the documentation files that you are trying to look at and reinstalling THEM. If nothing else, at least this is bumped so maybe you'll get someone else to suggest something.

---

### Post by Wheel on 2011-03-06
I'm pretty much out of ideas; I'm shootin' blanks here.  In the next couple of weeks, I'll likely re-install Lucid.  Never had a single problem with it; everything just worked the way it was supposed to.  When I first installed Lucid, I thought "Oh, good.  An LTS (my first).  I'll just hang on to this until the next LTS comes down the pike".  I guess I should've listened to my gut.  
In any case, I DO want to thank you LewRockwellFAN, for all the time and effort you put into this.

---

### Post by nashjc on 2011-05-04
As a long-time Ubuntu user, I thought I would try Natty. Installed it on an Asus Eee 900. Seemed to work, but I didn't like Unity and rebooted and selected "Classic" (i.e., Gnome) interface. (Might add that this took a couple of tries for reasons yet to sort out.) However, when I right clicked on the panel and tried Help, I got "Unknown error" The file..... user-guide.xml could not be parsed...". 

I reinstalled the gnome docs and ubuntu docs after completely removing, but no joy. Looks like something in the repo is broken. 

So far 11.04 does not look like a winner, but I'm open to being convinced otherwise.

JN

---

