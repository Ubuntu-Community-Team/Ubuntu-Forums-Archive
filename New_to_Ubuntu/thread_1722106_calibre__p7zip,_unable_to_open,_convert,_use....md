---
title: "calibre / p7zip, unable to open, convert, use..."
date: 2011-04-05
forum: New to Ubuntu
---

### Post by lemured on 2011-04-05
Hello.
Today's problem concerns epub-files.
Trying to open my freshly downloaded epub-file by whatever possible means available I get the disappointing message
'File type electronic book document (application/epub+zip) is not supported'
Odd, I do think, since the thing is actually not zipped, but then it might be a very precise, detailed message. And even if zipped, p7zip is installed and normally working fine.
Let's consult calibre.
Calibre has similar problems, so I try to convert.
This results, whatever file-type I choose, in another message of failure, the list of details which I'm happy to relate to anyone interested, ending with 
'raise BadZipfile, "File is not a zipfile"
calibre.utils.zipfile.BadZipfile: File is not a zipfile'
Yes.
I noticed.
I don't want to unzip it.
I want to read it.
If necessary convert it.
As usual I suppose that it's me who's the idiot, but so far the means used did not even go as far as to clearly explain me THAT...
Anyone any ideas? I'd be really obliged...
Thnx

---

### Post by rosencrantz on 2011-04-05
Hi lemured,
epub files are zip files with a different extension. Calibre needs to unzip in order to parse it. I suspect the file is corrupted - rename a copy to .zip and try to unpack. If that doesn't work, you will probably have to try a fresh download. 
Cheers,
rosencrantz

---

### Post by lemured on 2011-04-06
Hi guildenstern...

let's start again, it's such an old, boring joke, I apologize...

Hi rosencrantz,

I tried it, though I had my doubts how an extension alone could do the trick, as an extension alone does not compress the file (always interrupt me when I sound stupid) and even when trying that as well, it won't do the trick.
I already uploaded the file thrice (from library.nu, formerly ka gigapedia) and have the same problem often with files from there.
So I suspect the mistake is on my side somewhere, just that I don't know where and what.
But calibre should not be working with zips alone, should it?

thanks,

    lemured

---

### Post by lemured on 2011-04-06
...and no, I do know how it sounds, it's not a zip-file, 
as stated that's the message I always get, already knowing that it's not.

---

### Post by rosencrantz on 2011-04-06
Well, we interchangeable fake Danes are used to old jokes ;-)

OK. My point is, even if you can't open it as a zip file, it should be zip compressed - all e-book readers expect to find zip compression according to the epub specs ([http://en.wikipedia.org/wiki/EPUB](http://en.wikipedia.org/wiki/EPUB)). Calibre can import a number of other files types, yes, but then the extension has to match the file type.

So, either the distributor made an error in packaging and it's not epub or the file is corrupted. Try opening it (don't modify/save anything) in a text or hex editor - you'll see a jumble of special characters as it's binary, but somewhere on top there are bits of the header. For epub, you should find something like 
'mimetypeapplication/epub+zipPK'. 
You could also try a virus scan (clamscan or browser-based online scanners). Maybe it's Windows malware.

To find out if you have a general problem with ebooks, try downloading something from gutenberg.org. Their .epubs are usually fine. Considering that you don't seem to have the problem with every ebook downloaded from library.nu, I don't think the problem is on your side. 
In that case, try contacting the people running the site.

Cheers,
rosencrantz (stark raving sane)

---

### Post by lemured on 2011-04-08
thank thee, rosencrantz
and, beggar that i normally am, thus poor in thanks, i thank thee
also for thy leading me to good gutenberg.
thou hast of course been right, and my native hue of resolution been darkened by corrupted files, a melancholic soul and darkened towels.
fare thee well, and prosperity bestowed on thee

 lemured, duke of madagascar

---

