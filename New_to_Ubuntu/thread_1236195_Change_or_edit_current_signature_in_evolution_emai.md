---
title: "Change or edit current signature in evolution email"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by Stoneface on 2009-08-10
I have a signature that has been created before in Evolution email and I would like to edit or adjust this signature. I can add signatures in Evolution, but I cannot find an option to edit the signature. How do I edit an existing signature?

---

### Post by Stoneface on 2009-08-10
I did find this at Evolution's website:

Evolution stores your data in $HOME/.evolution/, your account settings in $HOME/.gconf/apps/evolution and your passwords in $HOME/.gnome2_private/Evolution.

When I changed to the evolution directory
```
cd ~/.evolution/
```
 I found the signatures folder. 
```
cd ~/.evolution/signatures
```
The I  entered ```
ls
``` for an overview of all files there. I got ```
signature-0  signature-1  signature-1~
```
Then I used gedit to open them one by one and see which one it was I wanted to change in the first place. I found the right one right away:```
gedit signature-1
```

Footnote 

[S]I wonder how I view what . files there are in Linux...[/S] ```
ls -a
``` :-)

Furthermore it would be nice if Evolution had an in built signature editor and clearer information on where to edit signatures that were created before..

---

### Post by longtom on 2009-08-10
For a Gui way:

In Evolution do the following:

Go to Edit > Preferences > Composer Prefernces

on top choose:  Signature

On the right hand side choose "Edit"

Off you go....

Here's a pic what mine looks like:

---

### Post by Stoneface on 2009-08-10
@ Longtom Thanks a lot! Didn't see that option. Now I just need to find out why it is not loading my external image in my signature: 
```
<a href="http://www.linkedin.com/in/profile" >
          <img src="http://www.linkedin.com/img/webpromo/btn_profile_greytxt_80x15.gif" width="80" height="15" border="0" alt="View My profile on LinkedIn">
```

When I reply to a message the images does not load and I get this error when I right click it to see its properties: 
```
The folder contents could not be displayed
```
It tries to find the image on my hard disk whereas it is online..

---

### Post by longtom on 2009-08-10
> **Stoneface said:**
> @ Longtom Thanks a lot! Didn't see that option. Now I just need to find out why it is not loading my external image in my signature: 
```
<a href="http://www.linkedin.com/in/profile" >
          <img src="http://www.linkedin.com/img/webpromo/btn_profile_greytxt_80x15.gif" width="80" height="15" border="0" alt="View My profile on LinkedIn">
```

When I reply to a message the images does not load and I get this error when I right click it to see its properties: 
```
The folder contents could not be displayed
```
It tries to find the image on my hard disk whereas it is online..

Saw your other thread refering to that error.  I can't even get a picture from my harddrive into my signature.  The option "insert > image" is greyed out.
When I make a signature and save it as an html and import it, the pic only shows as an empty frame.
Any ideas welcome.

*This is a hijack - nobody move....:p

---

### Post by Stoneface on 2009-08-10
Well thanks anyway Longtom. Haven't figured it out yet either. Evolution dislikes images in signatures and has issues with external images. Maybe something comes out of the [other thread]("http://ubuntuforums.org/showthread.php?t=1236273") and my bug report at Launchpad.Thanks again for all your help!

---

