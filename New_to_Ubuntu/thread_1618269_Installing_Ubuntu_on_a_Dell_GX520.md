---
title: "Installing Ubuntu on a Dell GX520"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by timbo59 on 2010-11-10
This is my first attempt to install Ubuntu on one of my computers, having been told by any number of friends to give it a try!

Because a lot of my work revolves around video editing and photographic work, too many of the programs I use are dependent on a windows environment for me to seriously consider making my main computer Linux-based. But I have a second computer sitting around unused, a Dell Optiplex GX520, that would be nice to play around on and finally see what it's like to use an OS like Ubuntu. I've used MS variants all my computer life, so I'm very curious to see what's on offer as an alternative.

My problem though is starting with burning the program to disk so I can try and boot-install Ubuntu on a clean HD. I already have Nero on board my main computer to burn Ubuntu on to, but I can't quite seem to make the process work - I keep getting error messages telling me that Nero couldn't open certain files. I tried installing the suggested burner from Ubuntu, but I have an aversion to programs that try and dump a pile of adverting material that I then have to clean out - I know, they have to make a buck somehow in order to keep providing the product for free. But I already have an excellent program on board for accomplishing the burning process.

Could someone possibly give me a step-by-step list of instructions on how to burn Ubuntu onto a disk using Nero? It would be much appreciated.

Thanks......Tim

---

### Post by bioterror on 2010-11-10
Here's a guide howto burn ISO file to CD.
[http://www.weethet.nl/english/cdrw_usingnero_iso.php]("http://www.weethet.nl/english/cdrw_usingnero_iso.php")

---

### Post by amjjawad on 2010-11-10
> **timbo59 said:**
> This is my first attempt to install Ubuntu on one of my computers, having been told by any number of friends to give it a try!

Because a lot of my work revolves around video editing and photographic work, too many of the programs I use are dependent on a windows environment for me to seriously consider making my main computer Linux-based. But I have a second computer sitting around unused, a Dell Optiplex GX520, that would be nice to play around on and finally see what it's like to use an OS like Ubuntu. I've used MS variants all my computer life, so I'm very curious to see what's on offer as an alternative.

My problem though is starting with burning the program to disk so I can try and boot-install Ubuntu on a clean HD. I already have Nero on board my main computer to burn Ubuntu on to, but I can't quite seem to make the process work - I keep getting error messages telling me that Nero couldn't open certain files. I tried installing the suggested burner from Ubuntu, but I have an aversion to programs that try and dump a pile of adverting material that I then have to clean out - I know, they have to make a buck somehow in order to keep providing the product for free. But I already have an excellent program on board for accomplishing the burning process.

Could someone possibly give me a step-by-step list of instructions on how to burn Ubuntu onto a disk using Nero? It would be much appreciated.

Thanks......Tim

Hello and welcome :)

1) Once you download your iso file, please check [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

2) Check [step 2]("http://www.ubuntu.com/desktop/get-ubuntu/download")

It should not go wrong :)

Let me know if you need more info.

---

### Post by corncob on 2010-11-10
> **timbo59 said:**
> 

Because a lot of my work revolves around video editing and photographic work, too many of the programs I use are dependent on a windows environment for me to seriously consider making my main computer Linux-based. 


For some tutorials and demos when you get Ubuntu installed go to
[http://www.youtube.com/results?search_query=video+editing+linux&aq=0](http://www.youtube.com/results?search_query=video+editing+linux&aq=0)

---

### Post by timbo59 on 2010-11-10
Hi again,
             Thanks everyone for those tips. I'll give it all a whirl and see how I go. No doubt I'll be back with cap in hand, screaming "Heeellllllppppp"!

Tim

---

### Post by timbo59 on 2010-11-11
Okay, back again - no success. 

Maybe I'm going about this the wrong way with Nero. Am I supposed to burn the disk using CD-ROM (ISO), CD-ROM (BOOT) or CD-ROM (UDF/ISO)?  I tired the first two without getting results, but maybe I was doing something wrong.

Also, the link to a Nero tutorial was more confusing than anything else, as I think it referred to version 5. No criticism, just the fact I couldn't match up what was being suggested.

And for the laugh of the day? The suggestion to 'check' MD5SUM had me squirreling around Nero for I don't know how long looking for a box to check. It was only when I gave up in frustration and actually clicked on the link that I discovered that the point was about checking on the integrity of the download!

Any thoughts?

---

### Post by waynefoutz on 2010-11-12
Don't bother with Nero. 


Get Imgburn. It's free, small and unobtrusive, and doesn't come bundled with spyware.

[http://www.imgburn.com/]("http://www.imgburn.com/") 


To use it, couldn't be any simpler. 

[IMG]http://i719.photobucket.com/albums/ww200/kenofthedragon/imgburn.png[/IMG]

Just click the "write image file to disk" and navigate to the .iso file. Click OK and it will write the disk.

---

### Post by timbo59 on 2010-11-12
Hey again,
                Have Ubuntu up and running at last. Thanks to all for their help.

First impressions are that it looks great. Took a little getting used to having to go the opposite top corner to click pages off or to access the program menu, but I'm sure that's a common comment from newbies - I accidentally tried logging off a few times by going to the top right hand corner!

Only problem so far is that my wife isn't too thrilled with the fact that Open Office's word processor doesn't have any of the fonts she likes working with like Ariel, Calibra, Times New Roman - plus she felt that it seemed a little unwieldy compared to MS Word. She's a professional writer and has used Word for so many years that I'm not going to argue with her desire to stick with what she knows and likes. I'm either going to have to see if I can manage to get Word on board the computer via Wine, or start from scratch with the installation of Ubuntu and partition the disk so that I can put XP on board with Word. I actually tried installing Ubuntu via partitioning from the very beginning, but ran into error messages. Just going for the full install made work without a hitch.

---

### Post by ppv on 2010-11-12
Just in case if you are installing both of them from scratch it would be simpler to first install xp and then ubuntu instead of the other way round.

---

### Post by timbo59 on 2010-11-12
Oh really? Why's that?

---

### Post by sandyd on 2010-11-12
> **timbo59 said:**
> Oh really? Why's that?

installing xp vapes the mbr

---

### Post by corncob on 2010-11-12
> **timbo59 said:**
> Hey again,
First impressions are that it looks great. Took a little getting used to having to go the opposite top corner to click pages off or to access the program menu, but I'm sure that's a common comment from newbies - I accidentally tried logging off a few times by going to the top right hand corner!

Only problem so far is that my wife isn't too thrilled with the fact that Open Office's word processor doesn't have any of the fonts she likes working with like Ariel, Calibra, Times New Roman - plus she felt that it seemed a little unwieldy compared to MS Word. She's a professional writer and has used Word for so many years that I'm not going to argue with her desire to stick with what she knows and likes. I'm either going to have to see if I can manage to get Word on board the computer via Wine, or start from scratch with the installation of Ubuntu and partition the disk so that I can put XP on board with Word. I actually tried installing Ubuntu via partitioning from the very beginning, but ran into error messages. Just going for the full install made work without a hitch.

If having those buttons on the left is any problem it's just a matter of changing themes to get them back on the right side: System > Preferences > Appearance > Themes.

I retrieved Windows fonts by opening the Windows partition in File Browser and going to the /Windows/Fonts directory.  I opened the desired font by double clicking it and then clicking on the 'Install' button to put it into Linux.  I did have Windows on the computer though; you can also google your desired fonts.  I don't know if this is any good but it was one of the Google hits: [http://www.searchfreefonts.com/](http://www.searchfreefonts.com/)

---

### Post by waynefoutz on 2010-11-14
Also AbiWord is another word processor that might suit your wife better. You can get it in the Software Center.

---

