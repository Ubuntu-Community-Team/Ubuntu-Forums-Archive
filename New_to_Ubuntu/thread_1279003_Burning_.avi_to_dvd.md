---
title: "Burning .avi to dvd"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by andyzammy on 2009-09-30
Hi all again,

I know this is an exaustive subject but i haven't been able to find an answer on the web about my problem.

I'm unable to successfully burn a series of avi videos to dvd (note: i'm not bothered about making a working dvd out of them, just wanting to write the avi files as they are to a dvd). I try to burn 11 or 12 avi's to one dvd, and after write has finished, i reinsert the dvd to test it, and all but 2 avi's show a thumbnail. more often than not its not just a missing thumbnail, the file won't play with any program.

I think this is a universal problem because i tried this before i switched to linux on XP and i had exactly the same problem there. I write on the lowest speed possible, but every time there are files that failed to burn properly. They're usually the same files too!

Does anyone know anything about this issue and how to solve it?

Thanks for your time,
zammy

---

### Post by halitech on 2009-09-30
sounds to me like its a possible issue with the files themselves. Do they play before you burn them to the dvd?

If you want a good program to make them into a dvd, devede is a good program.

---

### Post by jward3010 on 2009-09-30
And I hate to give Windows credence for this but another fantastic program is DVD Flick, open source, based on ffmpeg and other great Linux tools but for some reason only available in Windows.

You might try making the bunch of the avi's into a single ISO image and try burning that?

---

### Post by theozzlives on 2009-09-30
I've had great success with devede. It's in the repos.

---

### Post by ovroniil on 2009-09-30
Use DeVeDe. It creates the iso file. Then you can burn by Brasero.

---

### Post by Mark Phelps on 2009-09-30
Are you using the same app to open the avi file on the disk, and then from the DVD?  I ask because not all the apps use the same codecs.  So, it's possible that one app will play the video (because it has the correct codec) and another app will not.

Also, try copying the avi back to disk under a different name, and seeing if the renamed file plays.

---

### Post by andyzammy on 2009-09-30
> **halitech said:**
> sounds to me like its a possible issue with the files themselves. Do they play before you burn them to the dvd?

If you want a good program to make them into a dvd, devede is a good program.

yes, the files play fine off the HD. it makes no sense why they shouldn't work after transferring them to the dvd. 

> **jward3010 said:**
> You might try making the bunch of the avi's into a single ISO image and try burning that?

i know there's a way to do that but i can't find out how. could you help me out please?

> **Mark Phelps said:**
> Are you using the same app to open the avi file on the disk, and then from the DVD?  I ask because not all the apps use the same codecs.  So, it's possible that one app will play the video (because it has the correct codec) and another app will not.

Also, try copying the avi back to disk under a different name, and seeing if the renamed file plays.

i use the bundled movie player to play both from the HD and from DVD. just tried copying the avi back to the computer and it have an input/output error while copying.

> **ovroniil said:**
> Use DeVeDe. It creates the iso file. Then you can burn by Brasero.

just tried devede. i can't see any way of making a data dvd. i won't be able to fit 12 eps onto a dvd because devede will inflate the sizes won't it? 

thanks for the help so far!

---

### Post by mharrison on 2009-09-30
Have you tried to use GnomeBake(r)?  I have had trouble with Brasero burning files....but GnomeBake(r) has always worked wonderfully for me.

YMMV

---

### Post by andyzammy on 2009-09-30
> **mharrison said:**
> Have you tried to use GnomeBake(r)?  I have had trouble with Brasero burning files....but GnomeBake(r) has always worked wonderfully for me.

YMMV

tried it and it gave the same problem. on top of that, it didn't label the cd. thanks though.

suppose i will just have to stock up on external hard drives then?

---

### Post by halitech on 2009-09-30
there is an option when you are adding titles to devede to adjust the sizes. If you look on the left side it is labeled Adjust Disk Usage. It will make the proper adjustments so the episodes will fit on a disk. How long are the episodes?

Do the files have any odd characters in the title or is it all letters and spaces?

---

### Post by HarrisonNapper on 2009-09-30
You can put them in a directory and run the mkisofs command to make the iso and then your pick of an iso burner to create the disk.

---

### Post by andyzammy on 2009-09-30
> **HarrisonNapper said:**
> You can put them in a directory and run the mkisofs command to make the iso and then your pick of an iso burner to create the disk.

the same thing happened when i used mkisofs - when i burned the iso onto a dvd two files didn't have thumbnails and didn't play when i tried opening them. whats wrong with me!? :P 

> **halitech said:**
> there is an option when you are adding titles to devede to adjust the sizes. If you look on the left side it is labeled Adjust Disk Usage. It will make the proper adjustments so the episodes will fit on a disk. How long are the episodes?

Do the files have any odd characters in the title or is it all letters and spaces?
nothing odd really, few letters, few numbers and a full stop in each (not the "."avi, another one). wouldn't have thought anything illegal would have been allowed.

thanks for the disk usage tip, am creating a dvd now. looks like it will take quite a while (i opted for the divx/whatever it was route, wasn't sure which to take). i'm not sure if it's the solution i'm looking for though. it looks like its going to re-encode everything, while i want it just written to disk and shelved cause i need the space. not that i'm not grateful for your help. its just one of those "it should just work" things, and such a simple one at that.

---

### Post by halitech on 2009-09-30
thinking about things, I'm wondering, do you have a dvd player that supports avi that you are trying to burn a data disk to play? Linux takes the position that you know what you are doing and will let you do something even if it won't work. Try renaming the files to the 8.3 format with no spaces and exta "."s in case the player is having trouble with them.

---

### Post by andyzammy on 2009-09-30
> **halitech said:**
> thinking about things, I'm wondering, do you have a dvd player that supports avi that you are trying to burn a data disk to play? Linux takes the position that you know what you are doing and will let you do something even if it won't work. Try renaming the files to the 8.3 format with no spaces and exta "."s in case the player is having trouble with them.

i'm making the data dvd's not to play on a dvd player but just to play back on my laptop/any computer - my take on that is that as long as it has the codecs, any computer should be able to play these. however, i don't think thats whats going wrong, for some reason the files just aren't being written properly in the first place.

the time i mentioned where i tried in windows, it was a different batch of .avi's, so i'm guessing its related to the avi format and possibly the xvid/divx codec? no clue how though, as only dvd writing is affected and copying/transfering to other memory devices (ie other hard drives or flash drives) works fine.

i'm using dirt cheap dvd's (stack of 100 bought for £20) but the fact that it's more or less the same files that keep corrupting make me think they're not the problem (the other files play back fine anyway).

this is such a confusing occurence, and it can't possibly be a new one. what do other people do as an alternate solution? or is everyone else successful at copying avi's to dvds?

---

### Post by halitech on 2009-09-30
I don't really burn avi files straight to dvd, I usually put them into dvd format so they will play on any dvd player. I'm using memorex dvds at a cost of 100 for 20.00CDN (about 12 UK pounds) so mine are even cheaper. 

Can you burn a data dvd of things other then avi files and read all those files?

---

### Post by Bradtek on 2009-09-30
> just tried copying the avi back to the computer and it have an input/output error while copying.

input/output error is a pretty basic "can't read the source" error

Either your hardware is defective or the Blank DVDs are 
defective / not well supported by your DVD player/writer.

Have you tried a DIFFERENT brand DVD-R / DVD+R ?
With so many fails this would be my first option.

---

### Post by mharrison on 2009-09-30
> **Bradtek said:**
> input/output error is a pretty basic "can't read the source" error

Either your hardware is defective or the Blank DVDs are 
defective / not well supported by your DVD player/writer.

Have you tried a DIFFERENT brand DVD-R / DVD+R ?
With so many fails this would be my first option.

I have to agree with Bradtek....I've been following this thread all day and it seems to me that it is very possible that the DVD's may not be supported by your burner as odd as it may be...I have run into it myself.  One way to test would be to try burning some non avi files, such as Documents and Pictures and see if the burn works for reading and copying back to the HD.

---

### Post by 4Orbs on 2009-10-01
This is a long shot, but I would be suspicious of the audio portion on the non-working avi files. Maybe they (the audio streams) were encoded at a sample rate of 44.1k rather than 48K. Also, maybe the avi's were created by merging two shorter avi files and the audio portions have conflicting hash information.

---

### Post by andyzammy on 2009-10-06
bought some more dvds to try out (different make). what the deuce! it worked!! the same batch of dvds i had a problem with that made me start this thread had the same minor problem of two missing thumbnails, but at least those files could play this time, which i settled for.

completely perplexed as to how the cheap dvds only worked "a little worse than" the newer ones - this is the digital age ffs!! either it works, or it doesn't! the rules of binary aren't being followed! :P

thanks for everyones time and help. never would have thought it would be a problem with the dvds, i ruled them out at the start because i thought it unlikely that two different dvd writers didn't like the dvds.

Zammy

---

### Post by stinger30au on 2009-10-06
> **andyzammy said:**
> Hi all again,

I know this is an exaustive subject but i haven't been able to find an answer on the web about my problem.

I'm unable to successfully burn a series of avi videos to dvd (note: i'm not bothered about making a working dvd out of them, just wanting to write the avi files as they are to a dvd). I try to burn 11 or 12 avi's to one dvd, and after write has finished, i reinsert the dvd to test it, and all but 2 avi's show a thumbnail. more often than not its not just a missing thumbnail, the file won't play with any program.

I think this is a universal problem because i tried this before i switched to linux on XP and i had exactly the same problem there. I write on the lowest speed possible, but every time there are files that failed to burn properly. They're usually the same files too!

Does anyone know anything about this issue and how to solve it?

Thanks for your time,
zammy


i bet your dvd laser is out of alignement

try a different dvd burner

---

### Post by mikechant on 2009-10-06
> bought some more dvds to try out (different make). what the deuce! it worked!! the same batch of dvds i had a problem with that made me start this thread had the same minor problem of two missing thumbnails, but at least those files could play this time, which i settled for.

The thumbnails are not part of the avi files, they're stored elsewhere (probably in the .thumbnails hidden directory in your home directory), so them being missing or wrong doesn't mean there's anything wrong with your backup.


Obviously the people recommending DeVeDe didn't quite read exactly what you were trying to do (backup avi files unchanged to a data DVD for playing on other PCs), but anyhow DeVeDe is excellent for converting video formats and making 'normal' DVDs with simple menu structures. I find it really good for making music video compilations where I can select individual tracks or just leave it on to play through; the discs it produces play fine on all my DVD players.

---

### Post by andyzammy on 2009-10-08
> **mikechant said:**
> The thumbnails are not part of the avi files, they're stored elsewhere (probably in the .thumbnails hidden directory in your home directory), so them being missing or wrong doesn't mean there's anything wrong with your backup.


Obviously the people recommending DeVeDe didn't quite read exactly what you were trying to do (backup avi files unchanged to a data DVD for playing on other PCs), but anyhow DeVeDe is excellent for converting video formats and making 'normal' DVDs with simple menu structures. I find it really good for making music video compilations where I can select individual tracks or just leave it on to play through; the discs it produces play fine on all my DVD players.

yes DeVeDe looks very useful, but i'm not too sure how to use it.
For example, the pixel ratio is messed with (starts off 720x400 but final size is 720x480). It takes away the black bars on the top and bottom, but when i open up advanced options, the option "add black bars" is selected. That's very confusing (or is that just MPlayer taking care of it automatically for you?). Also, its not obvious how to name the DVD's. When it comes to writing the iso to disk you have no choice on what to name your dvd. It's grayed out. Is there a way to tell DeVeDe what to call the dvd?

stinger30au, i doubt that is the problem. i have tried doing this on an older pc, and had exactly the same problem with that. i did use the same dvd's on that pc, so the dvd problem is more likely.

Thanks again for the posts!

---

### Post by mikechant on 2009-10-10
> For example, the pixel ratio is messed with (starts off 720x400 but final size is 720x480). It takes away the black bars on the top and bottom, but when i open up advanced options, the option "add black bars" is selected. That's very confusing (or is that just MPlayer taking care of it automatically for you?)

Personally I've never messed with any of that stuff, just let it do what it wants and the results have been fine.

> Also, its not obvious how to name the DVD's. When it comes to writing the iso to disk you have no choice on what to name your dvd. It's grayed out. Is there a way to tell DeVeDe what to call the dvd?

When I have defined a disc structure, I click on 'forward' and a get a dialogue which allows me to select from of list of folders (including 'other' for folders not on the list) and also enter a name for the iso. Is this the dialogue which you say is greyed out? Is it just the name field that you can't change or can you not select a folder either?

---

### Post by andyzammy on 2009-10-10
> **mikechant said:**
> Personally I've never messed with any of that stuff, just let it do what it wants and the results have been fine.



When I have defined a disc structure, I click on 'forward' and a get a dialogue which allows me to select from of list of folders (including 'other' for folders not on the list) and also enter a name for the iso. Is this the dialogue which you say is greyed out? Is it just the name field that you can't change or can you not select a folder either?

i couldn't see anywhere in the DeVeDe program that names the actual iso produced. i'm refering to the "write to disk" function in ubuntu. if you were making your own dvd you would be given the option to name it (default is personal data time, date etc), but a devede iso it is grayed out (i think it says DVDVIDEO or something along those lines).

---

### Post by mc4man on 2009-10-10
I'm not sure if any linux burning aps will let you change the volume label of the .iso if you can't find a way to adjust in devede.
If any maybe k3b or possibly ..? a cli tool.

Personally I use Imgburn in wine for all .iso creation and burning tasks ( nothing even close as to configurabilty and success rate - virtually 100%

Imgburn can change the volume label of any .iso, very handy.
Ex.
the .iso file name was war.iso and the volume label was DVD_VIDEO (scr.1
Changed to actual name DAS BOOT (scr 2

---

### Post by andyzammy on 2009-10-12
> **mc4man said:**
> I'm not sure if any linux burning aps will let you change the volume label of the .iso if you can't find a way to adjust in devede.
If any maybe k3b or possibly ..? a cli tool.

Personally I use Imgburn in wine for all .iso creation and burning tasks ( nothing even close as to configurabilty and success rate - virtually 100%

Imgburn can change the volume label of any .iso, very handy.
Ex.
the .iso file name was war.iso and the volume label was DVD_VIDEO (scr.1
Changed to actual name DAS BOOT (scr 2

interesting. i googled, and it turns out that if i burn the dvd with k3b i'll be able to change the label. weired how devede won't let you do it though:
[http://ubuntuforums.org/showthread.php?p=7845722](http://ubuntuforums.org/showthread.php?p=7845722)

---

