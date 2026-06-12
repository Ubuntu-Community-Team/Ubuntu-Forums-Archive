---
title: "F-Spot default folder, Open Office gallery"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by Bucky Ball on 2009-08-20
Hi all,

I built a computer for my mother-in-law in February '09 (the build is outlined in the link in my signature) and have been helping her get to know and learn Ubuntu. Trouble is, she is 750kms away so it hasn't been easy! 

I thought I would post the answers to her recent questions here as it occurred to me they may be of some use to folks new to Ubuntu generally (and others). Hopefully, others think this post is appropriate to this forum, too.

**1/ F-Spot default folder:** There are a couple of ways of going about this. The first is to open F-spot (Applications->Graphics) then go to Edit->Preferences->Import Settings. To the right of 'Folder' you probably have 'Photos' (which, to answer another question, is where your pics are being saved to). Click that and select 'Other' at the bottom of the list. Simply choose the folder you want to use (in my mother-in-laws case she correctly nominates Home->Pictures for her setup). 

Once that is set, open a pic, go to File->Save As, and a window should open to the folder you have chosen to be the default. Give the file an appropriate name and save. I usually create a new, dated folder in there so I can identify the photos if I'm saving a lot. You could create one and call it something suitable.


**The second way**, and the way I generally go about dumping a whole lot of photos from the digital camera, is to open two folders, the 'Pictures' folder and the 'Camera' folder (whatever model, you should be able to click the camera's icon on the desktop or find it in places). 

In the 'Pictures' folder, I make another folder (Create Folder) and name it the date of my dump. You could call it something suitable. 

Now, in the 'Camera' folder, select all the photos (just the photo files, probably .jpg, not anything else) and drag and drop them into the new folder you have created in 'Pictures'. If you don't create a specific folder for your dump you will end up with a zillion photos in one folder. Kinda confusing and makes things hard to find. 

Finally, once I know the pics are safely on the hard drive, I go back to the 'Camera' folder where the picture files are all selected and hit delete. Camera empty and ready to reload. Advantages to doing it this way is that the photos are going to be faster to view and manipulate from the hard drive, you can view them in whatever software you like (Gimp more options for editing) and if you don't want, you can kill it forever from the hard drive (ALL the photos are already gone from the camera). Once you've deleted all the pics you don't want from you new folder on the hard drive, you can back-up the folder and your precious pics and secure, camera ready for the field.

**** Important note here**: make sure you are not copying any of the camera's own system files over when you drag and drop. Check that you are only copying the .jpg files (if that is what your camera shoots). More importantly, when you delete the picture files from the camera, make sure you are not deleting anything essential to the camera (delete .jpg files only). :)

[CENTER]*

[LEFT]**2/ Can't get rid of Open Office Gallery toolbar: **In Open Office, go to the 'Tools' drop down menu. You will note that 'Gallery' is ticked. Untick it. Voila!

[CENTER]*

[LEFT]Hope that fixes those problems and is some help to other people along the way.

Although the distance has been difficult, I'd like to publicly congratulate my m-i-l on making a gutsy statement by diving headlong into open-source after years of Windows (her machine is single-boot Ubuntu). ;-)
[/LEFT]
[/CENTER]


[/LEFT]
[/CENTER]

---

### Post by zarthon on 2009-08-20
It is good to know that f-spot will deal with pictures in sub-folders.

I find though that f-spot replaces the need to manage the files directly so I don't let the big mess of files bother me. I just let f-spot automatically import from my photo card when it's inserted. When I want to make a copy of picture files i just select what i want in f-spot and then export them to a file. I love how f-spot manages originals and touched up versions of photos. Using this method it will move the latest and greatest images.

Since my camera expects to use different cards I have never had a problem deleting all the files on the card. The camera just recreates them. I do have a very nice camera (nikon 20d)that is also fairly old.

Your post has reminded me of a problem with photos that I need to post about soon.

---

### Post by Bucky Ball on 2009-08-20
Thanks zarthon, I think you summed that up better than myself in MUCH fewer words. Working from the card (rather than plugging the camera in) is definitely the best way to go. Was thinking the latter. (My m-i-l has a Tomato card reader which should do the job painlessly).

I also never use F-Spot for importing so this is much more informed advice from someone who uses it to do just what is required. :)

---

### Post by zarthon on 2009-08-20
Thanks! You are very kind.  :redface:

---

### Post by ArtLaForge on 2009-08-21
Hi Bucky Ball:
I like the sounds of your picture organization, however, my experience (has me very confused) When I tried to import from my Canon 20D F-Spot gave me an error could not read camera format. So I clicked on the Canon Icon on the desktop and copied the pictures to my folder (from Camera) then imported from F-Spot using the source as (from Camera)folder. F-Spot shows all the pictures in browse mode and when I selected the latest import set, I tried to export to cd, this failed with error could not find the pictures. At that time the pictures were still in that folder, so what does F-Spot do with the import? When I right click on the thumb to copy the location it shows my (from Camera) folder. So if I create another folder and move those pictures to be ready for my next camera download F_Spot will not have the right folder location? As if it matters, it can't find them when they are where F-Spot thinks they are. I wonder if there is an export bug or if I am missing a plug-in to handle exports??? I tried to export to CD and Folder selecting different batches of pictures and none would export.

---

### Post by Bucky Ball on 2009-08-21
I think my mother-in-law is having a similar problem. She has set the default folder in 'Preferences' in F-Spot but they are still not going there.

My suggestion is to take note of one of the file names, export them and then do a search on the hard drive for that file name using Places->Search for files. You could also use a terminal (Applications->Accessories) and type, using your filename of course:

```
locate your_filename_here
```See if that at least tells you where they are going. I am curious. ;-)

---

