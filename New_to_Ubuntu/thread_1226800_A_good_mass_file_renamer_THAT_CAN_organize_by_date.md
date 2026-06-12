---
title: "A good mass file renamer THAT CAN organize by date?"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by BastardNamban on 2009-07-29
I used to use Flash Renamer before I switched to linux last year, and it worked phenomenally well. However, it refuses to run in Wine for me, even a trial installer. Nothing happens clicking on the file, or adding it in Wine config.

I have 10s of GIGS of pictures from Japan I'm trying to sort, and in all this, some pictures I had renamed improperly elsewhere have complicated efforts. I want to sort the pictures by date created/modified first, and then rename them in batch (something Flash Renamer in windows did wonderfully well). I have KRRename AND GPRename. Neither will organize the files the way I need before I can rename them. It's driving me nuts!!!!

I need a mass file renamer that ISNT run from the command line, and can sort the files by creation/modified date, or any user defined field (ultimate wish), before I rename.

Does anything like that exist in Linux? Someone please help, it will take decades to do this by hand.

---

### Post by jbrown96 on 2009-07-30
You are probably out of luck. Linux is not known for having GUI tools for this sort of thing. You will need to find/make some type of script to do this.

---

### Post by HotShotDJ on 2009-07-30
> **BastardNamban said:**
> I need a mass file renamer that ISNT run from the command line, and can sort the files by creation/modified date, or any user defined field (ultimate wish), before I rename.

Does anything like that exist in Linux? Someone please help, it will take decades to do this by hand.Thunar will do that with its bulk rename utility.  I just checked on my system.  Just install using Applications --> Add/Remove.

---

### Post by BastardNamban on 2009-07-30
That's what I thought I'd hear. I had searched far and wide before I posted this, and found nothing. Probably because, there is nothing!

I can't believe I have to do this, but I think I will use the family XP box, hook up the external HDD I have with all the pictures, install Flashrenamer on the XP box, and use it to rename everything.

I wish Flashrenamer was ported to Linux! I'd gladly pay to use it in linux.
I'll have to contact the maker, and see if they'd be willing to make a version for us.

---

### Post by BastardNamban on 2009-07-30
HotShot- I think you've hit the jackpot for me!

Thunar didn't show up in my searches, as I was looking for something that directly handled bulk renames as an app. I found the part you mentioned.

It seems like a very simple and nice interface, but I can't seem to figure out how it's supposed to arrange by time. I see how you can add the date into the filename for everything, but right now I have some misnamed pictures (20 or so) in a folder of several hundred, all taken on the same DAY (Sapporo snow festival). It seems there is some nomenclature to customize what's added, but can it add TIME, not just date?

Do you know? This looks to be pretty nice.

EDIT- further searching has shown me the answers I needed [HERE.]("http://thunar.xfce.org/pwiki/documentation/bulk_renamer")

Thank you!

---

### Post by HotShotDJ on 2009-07-30
1) Open Thunar File Manager -- browse to the directory with the files you want to sort and then rename
2) From the "View" menu, sort as desired (there are not any user defined sorts, but there is a sort by date modified, as you requested)
3) Now, from the Edit menu, either "Select All" or "Select By Pattern" (for example, *.jpg to select all jpg files in the directory)  -- you can also manually select the files you want using the "shift" and/or "ctrl" key like any other file selection dialog.
4) Right click on one of the highlighted files and select "Rename"
5) The bulk rename app will open with the all the selected files sorted as requested.

It would be easier if they had the sort function in the Bulk Rename application, but not by much. :)

---

### Post by BastardNamban on 2009-07-30
> **HotShotDJ said:**
> 1) Open Thunar File Manager -- browse to the directory with the files you want to sort and then rename
2) From the "View" menu, sort as desired (there are not any user defined sorts, but there is a sort by date modified, as you requested)
3) Now, from the Edit menu, either "Select All" or "Select By Pattern" (for example, *.jpg to select all jpg files in the directory)  -- you can also manually select the files you want using the "shift" and/or "ctrl" key like any other file selection dialog.
4) Right click on one of the highlighted files and select "Rename"
5) The bulk rename app will open with the all the selected files sorted as requested.

It would be easier if they had the sort function in the Bulk Rename application, but not by much. :)

Oooohhh, that works even better! Thank you very much:D

---

### Post by HotShotDJ on 2009-07-30
> **BastardNamban said:**
> I have some misnamed pictures (20 or so) in a folder of several hundred, all taken on the same DAY (Sapporo snow festival).Even EASIER... after you sort as I mentioned in my other post, just select the files from the target date and then right-click -> Rename.

> **BastardNamban said:**
> EDIT- further searching has shown me the answers I needed [HERE.]("http://thunar.xfce.org/pwiki/documentation/bulk_renamer")

Thank you!Good find!  And your more than welcome... Thunar has been a huge time-saver for me.

---

### Post by BastardNamban on 2009-07-30
ahhg, actually, while you are right- it only offers date without time.
So pictures/files created on the same day can no further be sorted!

Looks like I'll have to do it the way the site I found above allows- use Thunar Bulk Renamer to rename by set time created, then sort by that, and rename numerically.

Thank you though, it seems Thunar's app can do what I need, if a bit out of step. :D

---

### Post by lavinog on 2009-07-30
> **BastardNamban said:**
> 
I need a mass file renamer that ISNT run from the command line, and can sort the files by creation/modified date, or any user defined field (ultimate wish), before I rename.

Does anything like that exist in Linux? Someone please help, it will take decades to do this by hand.
you could try [krename (click to install with synaptic)](apt://krename)

What is your procedure for renaming your files? Do you rename them to some format like NAMEPREFIX_NUMBER.JPG ?
A nautilus script could be made to simplify tasks like this.

---

### Post by HotShotDJ on 2009-07-30
> **BastardNamban said:**
> Looks like I'll have to do it the way the site I found above allows- use Thunar Bulk Renamer to rename by set time created, then sort by that, and rename numerically.Well, Thunar is VERY configurable.  You could probably write a script and then attach it to a Custom Action (see Thunar's "Edit --> Configure Custom Actions" function).  Of course, by the time you (or I) figured out how to write the script, you could have done it the way you listed above for 5 trips to Japans. ;)

---

### Post by HotShotDJ on 2009-07-30
> **lavinog said:**
> you could try [krename (click to install with synaptic)](apt://krename)Although it is a KDE application (or perhaps because it is a KDE application), krename looks like it has every option under the sun -- see: [http://www.krename.net/Features.12.0.html](http://www.krename.net/Features.12.0.html)

A great find, lavinog!

---

### Post by BastardNamban on 2009-07-30
> **lavinog said:**
> you could try [krename (click to install with synaptic)](apt://krename)

What is your procedure for renaming your files? Do you rename them to some format like NAMEPREFIX_NUMBER.JPG ?
A nautilus script could be made to simplify tasks like this.


Please see my first post- I found KRrename a while ago. It didn't do what I wanted, or if it did, the interface was so bad I couldn't figure out how.

I always rename files like this: "Filename Is This.ext"- I HATE how Linux defaults to uppercase for extentions. I like the first letter of every new word capitalized, and all extentions lowercase. I've extremely, extremely meticulous about this (obsessive compulsive to a T), and I lose sleep over unnamed/unorganized files on my computer that don't conform (yes, I'm insane, I know, I can't help it)

I'm noticing now that even between Thunar AND GPrename, I can't have one operation with multiple parameters specified to hold at once, like Flash Renamer can do all at once (auto capitalize all first letters, lowercase extentions, replace existing filename with something else WITHOUT adding to it first, etc.)

I'm getting it done now, but having to switch back & forth between the two programs, where as in Flash Renamer, it could handle all these parameters in one action.

EDIT- Btw, I'm a total newb- I have no idea what a "script" is, much less how to write one, and I imagine with the level of my meticulousness, holding to all these multiple parameters, it would take a massive amount of syntax to write whatever command would do what I want. Sorry, can't go that route.

---

### Post by HotShotDJ on 2009-07-30
> **BastardNamban said:**
> I lose sleep over unnamed/unorganized files on my computer that don't conform (yes, I'm insane, I know, I can't help it)A little OCD can be a good thing. My assistant can be very OCD about things -- the lab has NEVER run more smoothly. :)

---

### Post by lavinog on 2009-07-30
> **BastardNamban said:**
> 
I always rename files like this: "Filename Is This.ext"- I HATE how Linux defaults to uppercase for extentions. I like the first letter of every new word capitalized, and all extentions lowercase. I've extremely, extremely meticulous about this (obsessive compulsive to a T), and I lose sleep over unnamed/unorganized files on my computer that don't conform (yes, I'm insane, I know, I can't help it)

EDIT- Btw, I'm a total newb- I have no idea what a "script" is, much less how to write one, and I imagine with the level of my meticulousness, holding to all these multiple parameters, it would take a massive amount of syntax to write whatever command would do what I want. Sorry, can't go that route.

First: a script is basically a program written as a text file, that can be modified to suit a persons needs. In linux, many programs you run are scripts. Linux takes advantage of many powerful scripting languages such as python, bash, perl...etc.

I am attempting to write a script that might be able to do everything you need. It will probably take me a couple of days, because I am still new to making GUI applications.

---

### Post by BastardNamban on 2009-07-30
I see. If you really want to take that much trouble for me, and it works, it's very much appreciated. I'd paypal you some cash for your trouble in a case like this, but I'm out of a job, and have 1.45$ left in my bank account!

I found that between Thunar & GPrename, I'm getting done exactly what I wanted, so a script really isn't needed here. Most of my pictures are un-renamed, from the camera, in names like "CIM0094.jpg", so editing those once properly sorted is easy. The really hard folder I had with misnamed pictures worked out too, albeit longer, after adding hour, minute, and second time modified data to the names with Thunar using %H%m%s, and then normal renaming with replace-text.

I really appreciate when people like you two go out of your way to help me on here, because I only post when I'm absolutely at wits end. I hope someday I'll know enough to start helping others like you helped me today.

---

### Post by unutbu on 2009-07-30
If you install the jhead package, you can rename image files like this:
```

jhead -n%Y%m%d_%H:%M:%S *.jpg
```

%Y%m%d_%H:%M:%S means year,month,date_hour:minute:second.

However, this only works for images with exif data. 
Images from digital cameras usually fall into this category.

Note that the datestamp refers to when the image was taken, not the last modification time of the file.

---

### Post by egalvan on 2009-07-30
> **BastardNamban said:**
> 
I always rename files like this: "Filename Is This.ext"- **I HATE how Linux defaults to uppercase for extentions (sic).** I like the first letter of every new word capitalized, and all extentions (sic) lowercase. I've extremely, extremely meticulous about this (obsessive compulsive to a T), and I lose sleep over unnamed/unorganized files on my computer that don't conform


I too am obsessive about how files are named...

but I have been running Linux for over a year, and have NEVER had Linux default to uppercase for extensions...

In fact, Linux being Unix, it defaults to lowercase and no spaces...


(Of course, with the on-going MS-Windowization of the Linux GUI, this is going out the window,
 and mixed-case and uppercase and spaces are becoming becoming more accepted. :( )

---

### Post by lavinog on 2009-07-30
> **BastardNamban]
I see. If you really want to take that much trouble for me, and it works, it's very much appreciated. I'd paypal you some cash for your trouble in a case like this, but I'm out of a job, and have 1.45$ left in my bank account!
[/quote]
I would be happy to have the opportunity to make something that someone would find useful.
I am working on making it a nautilus script, but afterwards I could make it a standalone app like gprename. Most of the options will be checkboxes so that you can do more than one operation in a single pass.
**Case operations:**
[list][*]all upper
[*]all lower
[*]upper/lower extentions
[*]First upper
[*]First after spaces upper
[/list]
**Numbering:**
[list]
[*]number after sorting by creation/modification time, filename, filesize, filetype
[*]add/remove leading zeros
[/list]
**Prefix operations:**
[list]
[*]insert prefix
[*]change prefix
[*]convert spaces or illegal characters to other
[/list]

[QUOTE=egalvan said:**
> 
but I have been running Linux for over a year, and have NEVER had Linux default to uppercase for extensions...

I think it is dependent on the camera. My main camera stores the images with uppercase extensions, while my phone camera stores them with lowercase extensions.

> 
(Of course, with the on-going MS-Windowization of the Linux GUI, this is going out the window,
 and mixed-case and uppercase and spaces are becoming becoming more accepted. :( )
The problem is in linux IMG0001.JPG and IMG0001.jpg can coexist, but if you copy the two files to a windows computer, one overwrites the other.

---

### Post by riarda on 2009-10-06
You must try [Metamorphose2]("http://file-folder-ren.sourceforge.net/"). The best renamer I have ever used. It is an all in one solution. ;)

---

