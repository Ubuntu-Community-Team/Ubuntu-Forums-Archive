---
title: "Evolution Email compressing photos - my 1 problem with Evolution Email"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by mjp29 on 2009-10-14
As a person that is transitioning from a 10 year old Mac running os X to Ubuntu (which I love) I still have one gripe about Evolution Email when compared to "mail" on Mac os x.

My gripe is:

On the old Mac os X box I can drag many many photo files and drop them on the dock (thing on bottom), drop the many photos on the dock where "mail" on the mac is.  The mac then launches "mail" where on the bottom of "mail" on the Mac, "mail" tells me the message size [on bottom left] but more importantly on bottom right i get to click in and choose from "actual size, small size, medium size, or large size"

Basically, on the Mac mail I can send a bunch of photos to Mac mail, see how big in gigs the message is going to be, and on the fly [in real time] choose quickly for mac mail to instantly compress the photos to small, medium or large, and quickly see on bottom left [before i send the email what size the email is going to be]

In evolution mail on Ubuntu, it appears that I can select multiple photo files and send to evolution mail; however, it appears at first to me [as a new Ubuntu user] that the compression method I can select is only if I select it to be a zip file.

Summarizing:  I like how mac os x allows me to zing a bunch of photos to it and quickly determine how mac mail will compress the photos and see quickly the size of the email I'll be sending and just as important the size of email the recipient will be receiving.  And if I don't like the size of the email I can quickly [on bottom right of mac mail] choose "small, medium, large" and mac mail will zing out another report on the size of email i'm about to send and i can then change again if i think i can go a little larger or should go a little smaller.  

I've read there are other email programs for Ubuntu that may be able to do what I want to do, but do they work as good as evolution mail?

How can I report to some folks [in our open source community that work on making evolution mail even better] to consider adding this type of on-the-fly option into future evolution mail verisons - ?

p.s. I still love Ubuntu and am making the transition from old mac to new pc box to put Ubuntu on.  p.s.s. Anything but MS Windows os OUCH!

---

### Post by dvlchd3 on 2009-10-15
I use Thunderbird.  I hated Evolution when I tried it.  It seemed very screwy.  Not sure if it does everything you just mentioned, but it is developed and maintained by Mozilla (same people that made Firefox).  Therefore, it has several hundred extensions to choose from.

Its in the repos!

```

sudo apt-get install thunderbird

```

Extensions:
[https://addons.mozilla.org/en-US/thunderbird/](https://addons.mozilla.org/en-US/thunderbird/)

---

### Post by stinger30au on 2009-10-15
another way to do it is to hold the ctrl key on the keyboard and point and click each photo

then right click and compress and save as .rar

email the .rar file

---

### Post by mjp29 on 2009-10-15
> **stinger30au said:**
> another way to do it is to hold the ctrl key on the keyboard and point and click each photo

then right click and compress and save as .rar

email the .rar file

Thanks for your reply post.

However, I don't really want to ctrl key click each photo.  I want to be able to highlight/select many photos and have the email program make a smaller version of them to be sent within the email program [while at same time not effecting the file size and not compress the original photos on hd]

If what I'm wanting to do can be done by Thunderbird, then please tell me how one pulls this off in Thunderbird.

---

### Post by kostkon on 2009-10-15
Check this [app]("http://ubuntuforums.org/showthread.php?t=518624").

---

### Post by mocoloco on 2009-10-15
The app kostkon linked to looks great, I'll have to try it out.  Also FYI if you're using F-Spot to manage your photos you can select a bunch in there, then from the menu select Photo > Send By Mail.  It then gives you the option of resizing your photos to a more suitable size for emailing, "medium" is a good setting for it.

---

### Post by mjp29 on 2009-10-16
> **mocoloco said:**
> The app kostkon linked to looks great, I'll have to try it out.  Also FYI if you're using F-Spot to manage your photos you can select a bunch in there, then from the menu select Photo > Send By Mail.  It then gives you the option of resizing your photos to a more suitable size for emailing, "medium" is a good setting for it.

that sounds like a great idea and i'll do it that way

i did open f-spot and select 33 photos and did what you said.  now the photos i took didn't need compressed, because they were taken with an old 2 megapixel dig. camera that i had intentionally told to take photos at 1 star (smallest file size in K) and not 2 or 3 stars (which 3 stars is the highest file size photo it will take).  so perhaps why f-spot would not let me select anything but "original" was because f-stop knew there was no need to further compress these original pic files - what are your thoughts?

i'll try it with my newer camera in a few hours

---

### Post by mjp29 on 2009-10-16
> **kostkon said:**
> Check this [app]("http://ubuntuforums.org/showthread.php?t=518624").


that app looks like a killer app-lol

i didn't read everything about it (was pretty long) but do you know if this can be used in a way that it will compress the images to be emailed and will not do any compressing to the original photo files (which would suck)

---

### Post by mocoloco on 2009-10-16
The app wouldn't change your originals, it makes copies and resizes those and sends them.  
Just want to clear you up on terminology, you keep saying "compress" when I think you mean "resize".  The term compress refers to taking the original file (or files) and running an algorithm to make the file take up less space, and putting them into a container file like .zip or .tar.gz.  When compressed they can't be viewed or change until they are uncompressed.

Resizing the picture causes it to also take up less space by changing the resolution of the picture.  The changed copy is better suited for email or posting online.  This concept can be confusing because sometimes when viewing a picture that has a very large resolution software will automatically (temporarily) resize it when displaying it to you so that you can see it all at once rather than zoomed in on someone's mole :P.  Then after resizing it might still look the same size in the viewer software even though the file size is much smaller.

---

### Post by mjp29 on 2009-10-22
> **stinger30au said:**
> another way to do it is to hold the ctrl key on the keyboard and point and click each photo

then right click and compress and save as .rar

email the .rar file

About .rar files

I know .rar files makes many files smaller; however, what if one sent a tremendous amount of files stored in .rar

couldn't a .rar file also be so large that an email server would reject it

is there any way to have any control over the size a .rar file is other than what you put into the .rar file 

?

---

### Post by mjp29 on 2009-10-22
> **kostkon said:**
> Check this [app]("http://ubuntuforums.org/showthread.php?t=518624").

the app, i have it and am trying it, however it seems like i am only "setting it up to be used"

how does on actually use the app

I suppose what's confusing me is that it has to be done from a nautilus window

?

---

