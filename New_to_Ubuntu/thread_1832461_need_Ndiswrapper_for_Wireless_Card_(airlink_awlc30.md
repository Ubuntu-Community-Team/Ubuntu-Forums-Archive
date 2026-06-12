---
title: "need Ndiswrapper for Wireless Card (airlink awlc3026) Install"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by uKEN on 2011-08-24
Hay Yall

I resently played with pupy linux..than tryed Lubuntu..
I feal so nooby..:confused:

The problem im having is my wierrless card is a airlink awlc3026 :(
So I can not fig out how the bassices work..I need to install Ndiswrapper !

BRAIN FART

any help/info or opinion would be greatly wanted

PS. sorry for the bad spelling and gramer

:guitar:

---

### Post by kerry_s on 2011-08-24
the packages are on the installer you used to install.

---

### Post by uKEN on 2011-08-24
> **kerry_s said:**
> the packages are on the installer you used to install.
 
so thay ar on my pc..or do i need to use the cd i used to install Lubuntu ?
 
well i DL the deb..but i have no idea waht im doing...
I dl "ndiswrapper_1.56+r2729.orig.tar.gz" , "ndiswrapper_1.57rc1.tar.gz" , "ndiswrapper-common_1.56+r2729-1_all.deb" , "ndiswrapper-utils-1.9_1.56+r2729-1_i386.deb"

---

### Post by whatthefunk on 2011-08-24
You should be able to double click on the .deb files and they will install themselves.

---

### Post by kerry_s on 2011-08-24
They are on the cd.

put your cd in & browse it with the file manager.
go to-> pool-> main-> n
go in to both of those folders & double click on the *.debs

ndisgtk is the gui for ndiswrapper, once you have all 3 packages installed you should find it in your menu under system tools.

see pics

(sorry about short posts earlier, i was on my ipod touch in the bathroom. ;) )

---

### Post by anewguy on 2011-08-24
The files you want are on the Cd, specifically in the /pool/main/n folder.  You will find 2 folders there:  1 for ndisgtk and 1 for ndiswrapper.  These must be installed in the proper order, so here's what to do:

[LIST]
[*]Boot ubuntu
[*]After ubuntu boots, put the install CD in the drive.  After a short period of time you will probably get a message about a software source CD found - just cancel that.
[*]Via "Places", explore the CD and go to the /pool/main/n folder.
[*]You will see 2 folders:  ndisgtk and ndiswrapper.  Go to the ndiswrapper folder first.
[*]Within this folder are 2 files - 1 for ndiswrapper common and 1 for ndiswrapper utilities.  Double click on the ndiswrapper common file to begin it's installation.  Wait for this to complete.
[*]Double-click on the ndiswrapper common file to begin its' installation and wait for it to finish.
[*]Now navigate back to the /pool/main/n folder, then to the ndisgtk folder
[*]Double-click on the ndisgtk file to begine its' installation and wait for it to finish.
[/LIST]
What you have done so far is 2-fold:

- you installed the ndiswrapper software so you use Windows XP drivers for your wireless

- you installed ndisgtk, the graphical front-end to ndiswrapper.  This makes installation a snap.

What you need to do next:
[LIST]
[*]Locate the .inf and .sys files for your driver.  These *must* be Windows XP *only*, and the architecture must match your ubuntu installation (32 versus 64 bit).  Just put these files in a new folder, such as "wireless", in your home folder.
[*]Install the driver:  Click on System/Administration/Windows Wireless Drivers - this will start ndisgtk.  Click on the item to add new.  Point it to the .inf file for your driver (~/wireless/xxxxxx.inf) and click.  It should install the driver now and show the device as ready.
[/LIST]

Now go to the network manager icon on the top bar and be sure "Enable Wireless" is checked - if not, click to enable it.  After a short period of time you should see the available wireless networks.

Dave ;)

EDIT:  After finishing my post I found that kerry_s had updated their reply, so mine may be a dup of what they are saying and showing you.

---

### Post by kerry_s on 2011-08-24
> Now go to the network manager icon on the top bar and be sure "Enable Wireless" is checked - if not, click to enable it. After a short period of time you should see the available wireless networks.


i would recommend a reboot instead, to make sure ndiswrapper is fully loaded. it should then just work.

> 
EDIT: After finishing my post I found that kerry_s had updated their reply, so mine may be a dup of what they are saying and showing you.


:lolflag: i couldn't do screenshots from my ipod. i'm running lubuntu 11.04, so i can post any pics he needs to help him along. :P

---

### Post by anewguy on 2011-08-24
Your absolutely right - I have always said just to reboot - don't know what I was thinking but glad you caught all of that!

Dave ;)

EDIT:  Forgot the main reason I also have people reboot - to make sure any changes for not loading modules "take".  It at least used to be - especially with the old way of doing things with the Broadcom chipsets - that ndisgtk made sure that the default modules were no longer being loaded.  I always recommended a reboot to be sure those changes worked.  Just so others reading this thread looking for help understand they *SHOULD* reboot just as you said! ;)

Again - thanks for catching that! ;)

---

### Post by kerry_s on 2011-08-25
> **anewguy said:**
> Your absolutely right - I have always said just to reboot - don't know what I was thinking but glad you caught all of that!

Dave ;)

EDIT:  Forgot the main reason I also have people reboot - to make sure any changes for not loading modules "take".  It at least used to be - especially with the old way of doing things with the Broadcom chipsets - that ndisgtk made sure that the default modules were no longer being loaded.  I always recommended a reboot to be sure those changes worked.  Just so others reading this thread looking for help understand they *SHOULD* reboot just as you said! ;)

Again - thanks for catching that! ;)


yeah, i've had problems with ndiswrapper not even loading till after a reboot as well, even after it loads the files just fine in the gui.

what i do:
install ndis
add windows drivers
then reboot

only then does it usually always work, except on that rare occasion where i put the wrong drivers. :)

---

### Post by uKEN on 2011-08-25
well ty all for your responses i'll try it out wen I get home .
 
> **kerry_s said:**
> 
 
:lolflag: i couldn't do screenshots from my ipod. i'm running lubuntu 11.04, so i can post any pics he needs to help him along. :P
 
hay u us lubuntu on you ipod ? what gen ?

---

### Post by kerry_s on 2011-08-25
> hay u us lubuntu on you ipod ? what gen ?

8gb ipod touch 4th gen, the 1 with cameras. i actually do everything over wifi(smb), i only plug in to charge.

it is detected if thats what your wondering.

---

### Post by anewguy on 2011-08-25
uKEN:

 BTW - I know you're new here - so please don't take this the wrong way - this forum gets lots of different age groups and all kinds of different countries.  To avoid confusion for others, especially those for which English is a 2nd or 3rd language, please avoid the abbreviations, etc., that are common in the US from texting, etc..  Again, please don't take this the wrong way!  ;)


kerry_s:

 You know, that's exactly the way I've always done it as well until this post - I think I had a major brain malfunction! ;)  (Hoping that doesn't happen to much more - I'm getting too young in my 2nd childhood for that kind of problem ;) ).  Anyway - thanks again!  ;)  Glad to have made your aquaintance here on the forum!

---

### Post by uKEN on 2011-08-27
> **anewguy said:**
> uKEN:

 BTW - I know you're new here - so please don't take this the wrong way - this forum gets lots of different age groups and all kinds of different countries.  To avoid confusion for others, especially those for which English is a 2nd or 3rd language, please avoid the abbreviations, etc., that are common in the US from texting, etc..  Again, please don't take this the wrong way!  ;)


kerry_s:

 You know, that's exactly the way I've always done it as well until this post - I think I had a major brain malfunction! ;)  (Hoping that doesn't happen to much more - I'm getting too young in my 2nd childhood for that kind of problem ;) ).  Anyway - thanks again!  ;)  Glad to have made your aquaintance here on the forum!

O my bad.. 
I should have thout about it..I make sherr to remember..:lolflag:

---

### Post by uKEN on 2011-09-09
work great thank you booth for you'r time..

hay how do I mark the topic as [SOLVED] ?

---

### Post by whatthefunk on 2011-09-09
> **uKEN said:**
> work great thank you booth for you'r time..

hay how do I mark the topic as [SOLVED] ?

Towards the top of the page, there is a Thread Tools drop down menu.  You can set it as SOLVED from there.

---

