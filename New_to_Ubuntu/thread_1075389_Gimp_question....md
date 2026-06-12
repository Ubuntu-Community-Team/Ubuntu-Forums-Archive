---
title: "Gimp question..."
date: 2009-02-20
forum: New to Ubuntu
---

### Post by longtom on 2009-02-20
Hi 

I print ID cards on Photoshop on a credit card sized carton (54 x 86mm).

That works fine in Windows and Photoshop.  I can make my card in Gimp - but when it comes to printing I can't get Gimp to print correctly on my Canon pixma 5300 over a lan Network.  The size is just never correct as are the colours.

I checked drivers over and over, can't find a mistake.

Another thing I need to go back to Windows for....aaaaaaaaaaaaaaargh.

Regards

longtom

---

### Post by longtom on 2009-02-20
Just trying to print in scribus....only print empt pages.

Any ideas?

longtom

---

### Post by longtom on 2009-02-20
Got some more details:

When I print in Office writer, the picture is stripie and light of colour.

The same pic on a Windows Machine, same printer, looks perfect.

How can I improve the quality and responsivness of that printer so it works like it does in Windows?

Regards

longtom

---

### Post by mikechant on 2009-02-20
Can you print anything at all correctly from any Linux program? E.g. text, black & white images, colour images other than your id cards? Or is it just these specific id card images that give trouble (it's not quite clear from your 2nd and 3rd posts if you're always printing these items).

I'm currently running 7.10 as my main system and 8.10 as my test system, and some prints that work in 7.10 come out wrong in 8.10; I haven't investigated yet, but it's possible that yours is a 8.10 specific problem. Can you try a different version (e.g. on a live CD so you don't have to install)?

---

### Post by longtom on 2009-02-20
> **mikechant said:**
> Can you print anything at all correctly from any Linux program? E.g. text, black & white images, colour images other than your id cards? Or is it just these specific id card images that give trouble (it's not quite clear from your 2nd and 3rd posts if you're always printing these items).

Sorry for being confusing.  I print text alright.  But with any image the colours are too light ad I have these fine but visible stripes.  WEll colours in general are not true and appear to light or to dark, depending on program used.

As mentioned above - some programs do print - some refuse to coorperate.

I started discovering the problem when I tried to print my cards and than went on exploring - and discovered my problems with scribus and office.  It appears that the malfunction differs, depending what program I'm working in.  I know, it's not gonna help to find the problem - but that's the way it is right now.

I tried to "search" as well...couldn't find anything which might help...

Regards

longtom

---

### Post by Barriehie on 2009-02-20
Did you check in System > Administration > Printing and see how the printer is setup?

Barrie

---

### Post by Bölvaður on 2009-02-20
System &#8594; Preferences &#8594; Default printer
make sure it has correct printer model


I think this is 8.10 only
System &#8594; Administrator &#8594; Printing
Can you find correct printer and model in there?
Right click &#8594; properties
There you can change colours and all sort of stuff.

in 8.04 there is something like
System &#8594; Administrator &#8594; Printers
or similar to that, which in my opinion is much more intuitive and easy for anyone to figure out.


Make sure that when printing in different programs, make sure you are using the exact same settings.
It may well be that the makers of your printer do not support linux at all.

I cannot help any further, need more details.

---

### Post by Kellemora on 2009-02-20
Hi LongTom

We publish brochures, newsletters and tons of those tri-folds you pick up at tourist traps.  And recently I just printed out 86 ID badges for a local club I belong to.

However, we rarely if ever print directly from Gimp, although it works OK for us from there.  Due to text and many other things that must be included we normally embed images into Open Office Writer, lighten and darken as need be, basically manipulate those images as to how they would work best for the project at hand.

But after reading your post, I decided to print out the images used on the ID cards just to see if I could replicate your problem.  They would print to the exact size I set them up to print at and I tried 3 different settings then checked and they were dead on each time.

Our only problem using GIMP is they changed the height of the tool windows and main screen so it's larger than our newer computers.  Works fine on the older computers, but on all the newer ones, we have to HIDE both the Top and Bottom Panels while using Gimp, which is a ROYAL PITA!

You might try to check for a newer or updated driver also or possibly even an OLDER driver!
I had to revert back to the old printer drivers and install them to get the printers to work on the new 64 bit machines.

Good Luck

TTUL
Gary

---

### Post by longtom on 2009-02-21
Thank you for your replies.  They all, in one way or another, contributed, that I am able to print in and from gimp.  Just can't print from preview - but that appears to be a bug.

But the colours as well as the quality of the print is not as it should be (or as it is in Windows by comparison).
Looks a bit like a draft print.

Anything I can do abaout that?  I have the suspicion if I can hit through that knot my colours will come right as well.

Suggestions are welcome.

Regards

longtom

---

### Post by ramjet_1953 on 2009-02-21
Have you tried navigating to:

[COLOR="Blue"]System>Administration>Printing[/COLOR]

When the widow opens, make sure your printer is the one highlighted in the left column.

Now click on the [COLOR="Blue"]Printer Options[/COLOR] Tab and set the quality of print that you require in the two [COLOR="Blue"]Printout Mode[/COLOR] drop-down menus.

Regards,
Roger :D

---

### Post by longtom on 2009-02-21
I have been in the equivalent of your suggestion in my Ubuntu.  I fiddles arround with the print settings.

On Print Quality I can choose between "Standard" and "manual".  The result appears to be exactly the same.

I also fiddles arround with the settings in "Output Control Common".  No joy yet.

regards

longtom

---

### Post by Kellemora on 2009-02-21
Hi Longtom

I just checked with one of the gals to see what setting she uses for the final display copy.

She sets the Paper Type to CARTON, this makes the paper feed slower so it gets hotter, slower through the heater section of the printer.

And she selects Printout Mode as PHOTO.

On occasions, in the System/Administration/Printers, she will select Job Options and scroll down and select Pretty Print.
Says she never saw that made much difference though, except on LARGE TEXT on some of the pamphlets, there it looks a little sharper.

Apparently using the PHOTO setting causes black to use all three colors instead of black too, because she goes through color cartridges 2 to 1 of everyone else.  But then too, she's the one making the final copies for the customers approval too.

TTUL
Gary

---

### Post by longtom on 2009-02-22
> **Kellemora said:**
> Hi Longtom

She sets the Paper Type to CARTON, this makes the paper feed slower so it gets hotter, slower through the heater section of the printer.

And she selects Printout Mode as PHOTO.

TTUL
Gary


Hi Gary,

thank you for that.  Since I am using a Canon Pixma IP5300 (inkjet printer), the heat logik doesn't apply really.  That's more for the laser printers I guess.

The only 2 settings I have is Standard and Manual, which appear to be exactly the same.

I assume there is just not a decent driver available for this printer and I need to do my final printing in Windows.

Maybe somebody still comes up with a suggestion.

regards

longtom

---

### Post by Kellemora on 2009-02-22
I hear ya LongTom!

Interestingly enough, the driver for our color laser printers is BETTER than the OEM drivers used with the DOZE.  It don't have the fancy on screen warning system on supplies and such, but as for as the working end of the drivers, many more features that we put to good use.

However, as good as it is, the writers of this driver made a serious error!

Or else they know something I don't.  Like where to buy toner cartridges that NEVER run out, hi hi.........

They made NO PROVISION for changing out toner cartridges when they are empty.  Our printers require software to do so!  So, we keep a doze machine up here in the corner on a board with wheels to roll over to the printer to connect to the Doze in order to change out the printer cartridges.  Then it gets rolled back into the corner again.

Another quirk with printers is it REALLY DOES depend upon which machine they are plugged into, as to what quality of printout they produce.

Sending the SAME file to the printer, pulled from the file server and sent through each of different computers, produces different outputs.
Minor variances most wouldn't notice, but since we have to work to exact specs to comply with commercial printing mask machines, we have one computer set up for only this use and all masks are done only on that machine for the final file sent to the outsourced printing company.

I have a gal here that although not the greatest in graphical work, when it comes to getting near perfect output from a computer to a printer, she can't be beat.  She can just look at a printed page and no what setting to change to fix it.  And she's NEW to Ubuntu also!  I might add she LOVES it too!  Open Office is GREAT at NOT messing up images at the 9th hour like msWord would do all the time, just as we were ready to go to press we would find images clear off the page sometimes, for no reason.  They were fine when we filed the document!

msWord I think uses printer settings to control it's output, so if you change printers, you must reedit the file for that printer.
Open Office doesn't work that way at all, that I can tell.  It don't matter what printer we send a file too, we get the same output with no fiddling, unless we were running to maximum margins the printer itself will allow, but then in OOoWriter, you can override and print outside of the allowable margins.  Nothing prints out there but it don't change the mask if you know what I mean by that.

I can print a 9x12 image on an 8-1/2x11 piece of paper without changing the size of the image, it's not shrunk, just the part that lies outside of the printers capability don't appear on the printed page.  Or I can shift the image to print the top left or top right so see the corners, again without adjusting the image itself.

Our printer uses like 23x35 inch paper so it CAN print two of the full trimmed 11x17 sheet cut again to a tri-fold with NO white space around the edges.
Our printer meaning the COMPANY we use for printing, not our on-site printing machines.  We gave up trying to run our own crash printers years ago, hi hi........  Takes brains to keep them things running!

TTUL
Gary

---

### Post by longtom on 2009-02-23
Hi Gary

thanks for that little inside info.  I have the colour problem as well - even in Windows and Photoshop.  Not with the Canons but with to Epsons I use for sublimation printing.

Sublimation ink is a real bugger and will only run on those few printers - and all from Epson...and I'm not an Epson fan whatsoever.  But these two identical printers have 2 different colour outputs and a special profile, which has been designed for Photoshop in order to get some similarity in colour with what you see on screen, calibrated or not.

Here we do stuff insstantly and the customers stands there, waiting, drumming on the countertop.  Not the time to do things 3 times over.  That is that I didn't have the courage yet to switch that system to linux.

Seeing the trouble I'm having with normal printing - that will not be happening for quite some time coming.

Greetings

longtom

---

### Post by Kellemora on 2009-02-24
Hi LongTom

If it makes you feel any better, our POS machines are still DOZE in order to run the necessary hardware up front!

It's only the back production end where I converted over to Ubuntu.  But the front end needs data from the back end and vice versa.

I bought the frau a new 64 bit machine and she found out that she can't run her sewing machine, recipe program and a few other things on it.
So she wants her old machine back and I'll have another 64 bit machine back here, so I iz happy, hi hi........

I have a few old doze program I run in wine, but many of them will not work simply because they require the doze machine to be in administrative mode to work.  Dangerous I know, we have a stand alone machine not connected to the LAN we use for accounting and these programs that won't run in wine.  Now that I've learned what flash drives are, I picked one up and use it to transfer the accounting data to that machine rather than plugging up the LAN even for a few minutes long enough to do the transfer.
It actually saves getting up two extra times, hi hi......

I had a little playing around time last night waiting for a job to finish up and made a little automated gif image using the layers in Gimp.
Couldn't get it to run though, or at least thought I couldn't.
I put it on my file server to work on later.
I opened it using Firefox while I'm eating my lunch here and it works just fine.
I wonder if there is a way to make a gif image animate in Gimp.  If so, I haven't found it yet.

Good Luck my friend!

TTUL
Gary

---

### Post by rustutzman on 2009-02-24
This doesn't solve the problem in gimp but have you tried gLabels for your cards. It has worked great for me in the past.

Russ

---

