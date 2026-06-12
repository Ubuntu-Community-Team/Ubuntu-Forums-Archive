---
title: "Utter newbie"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by mimseycal on 2010-08-25
And I am, in the words of Ella Fitzgerald, "*Bewitched*, [I]Bothered And Bewildered" ... 

Whenever I download something ... click to open it I get either:

[/I]
[LIST]
[*]* a list of files when I use Archive Manager. *
[*]nothing when I try and use Archive Mounter
[*]zilch when I try Autorun
[*]and: > End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of /home/miriam/Downloads/LettersfromNowhereBeta.exe or
        /home/miriam/Downloads/LettersfromNowhereBeta.exe.zip, and cannot find /home/miriam/Downloads/LettersfromNowhereBeta.exe.ZIP, period.
 when I try Auto Extract
[/LIST]
I spent all day yesterday trying to find a way around this. :(
I'm sure that it is in all likelihood something simple that I am overlooking here but I am starting to get stars in front of my eyes and they are those horrible about to go supernova stars rather then nice twinkly ones ... HELP!!!!! Please?

---

### Post by LiquidMeson on 2010-08-25
Are you downloading .exe or .msi files?

The first two aren't supported by linux unless run in wine. If your looking for applications I recommend using the ubuntu software center (you can fine wine in here), or making sure they support linux (.deb files are ubuntu install files)

---

### Post by mimseycal on 2010-08-25
Oops ... let's see .exe files ... they generally are .exe files.

(I do some beta testing for silly games - which suits me fine as I am a tad silly myself ;))

So do I just look for 'Wine' in the download centre? and is there anything else I should know ... as in Wine will require 'Carafe' to operate?

Thanking you :)

---

### Post by bwang on 2010-08-25
Well, that would explain it. exe's don't run on Linux. Use WINE, or (dare I say it?) Windows.

---

### Post by julio_cortez on 2010-08-25
So, well, either you dual boot with Windows and try games there (I'd recommend this, as I think you're supposed to run them under Windows) or try downloading Wine.

Again, being beta testing of software that is designed to run under Windows, I'd rather do it directly in Windows than in Wine..

---

### Post by mimseycal on 2010-08-25
I don't currently have Windows ... I am refusing to use that bloatware. I'll try 'Wine'

Thank you muchly :)

---

### Post by mastablasta on 2010-08-25
How can you test then? it could be game works in Wine well but not in Windows?!

---

### Post by migs73 on 2010-08-25
> **mastablasta said:**
> How can you test then? it could be game works in Wine well but not in Windows?!

That sounds perfect!!!!

---

### Post by mimseycal on 2010-08-25
Ah well ... it's a chance to try out new games. They aren't serious games as in WoW or anything. Just silly little match three or find hidden objects type things. Having said that ... what's wrong with trying to get game developers to bear in mind the growing number of Ubuntu users?

Anyhoos ... Gone and done the terminal thing with sudo and everything. Even managed to figure out that it is perfectly all right for my password not to register while entering it. But no luck with the Wine ... I mean ... it may well be the answer to this old girls' gaming problem but it ain't there ... so, I'll try again later when the gods and goddesses of the internet highways are perhaps willing to smile favourably upon me

Thank you again

---

### Post by migs73 on 2010-08-25
Mimseycal

Look under Applications > Ubuntu Software Centre. Click on this and it will open up. In the search box in the corner type in Wine and it should appear in the list below. Click on the install button and let it do its stuff. You will need your password at this point. Once done Wine will appear in the applications menu.
Google for instructions on how to install a program in wine (it's been a while since I did it).

---

### Post by julio_cortez on 2010-08-25
> **mimseycal said:**
> Having said that ... what's wrong with trying to get game developers to bear in mind the growing number of Ubuntu users?
There's a notable difference: if you ask them to developing **for Ubuntu** and get from them a *.deb package to try, you are really OK to try it with Ubuntu.

But if the games are for Windows (I assume so as they are *.exe files),  again I'd second the suggestion to try them first under Windows.
Or just wait until they are ok under Windows, then try them in Wine.

Trying games in wine doesn't mean that those games are made for Ubuntu!!
In addition, it could have some unwanted side-effects (e.g. *the game doesn't work properly in Wine but you're not aware that it works in Windows, so you convince them to fix something that actually is *not* broken*)

---

### Post by mimseycal on 2010-08-25
> **migs73 said:**
> Mimseycal

Look under Applications > Ubuntu Software Centre. Click on this and it will open up. In the search box in the corner type in Wine and it should appear in the list below. Click on the install button and let it do its stuff. You will need your password at this point. Once done Wine will appear in the applications menu.
Google for instructions on how to install a program in wine (it's been a while since I did it).You are a :KSThank you ... I'll give it a go.

---

### Post by mimseycal on 2010-08-25
> **julio_cortez said:**
> There's a notable difference: if you ask them to developing **for Ubuntu** and get from them a *.deb package to try, you are really OK to try it with Ubuntu.

But if the games are for Windows (I assume so as they are *.exe files),  again I'd second the suggestion to try them first under Windows.
Or just wait until they are ok under Windows, then try them in Wine.

Trying games in wine doesn't mean that those games are made for Ubuntu!!
In addition, it could have some unwanted side-effects (e.g. *the game doesn't work properly in Wine but you're not aware that it works in Windows, so you convince them to fix something that actually is *not* broken*)Oh ... I will be sure that they know I use Ubuntu when I send in my review. What they do about it is entirely their concern really :D

---

### Post by migs73 on 2010-08-25
From my experience, it is the simpler games that are more likely to run under Wine. I think if the developers have any sense, they will welcome your input ,and if it runs fine they could add it to the AppDB. By the way Mimseycal WoW (since you mentioned it)has platinum rating under wine, in other words it installs and runs perfectly.

---

### Post by mimseycal on 2010-08-25
I've installed Wine now but it won't open the .exe ... it reckons it may be some malicious script or something. It isn't, as I know the source, but evidently that isn't enough for the now. Oh well ... Hopefully the developers of Wine will get on to it eventually ;)

I'm not a serious gamer so WoW doesn't do anything for me. I'm one of those growing army of using the game to unwind for a few minutes between jobs.

---

### Post by julio_cortez on 2010-08-25
> **mimseycal said:**
> I've installed Wine now but it won't open the .exe
Have you already tried to right-click the exe and select "open with Wine application loader" (or something similar, I'm far away from my Ubuntu machine at the mo)?

---

### Post by mimseycal on 2010-08-25
Yup! Tried it and failed. I've also looked at the 'Wine' developers doodah ... where they tell you what they have been doing. It looks as if it is something that is in the pipeline but they haven't got around to yet.


BTW ... you will have to forgive my non-technical phraseology. I'm old, uneducated and entirely self taught.

---

### Post by migs73 on 2010-08-25
> **mimseycal said:**
> 

BTW ... you will have to forgive my non-technical phraseology. I'm old, uneducated and entirely self taught.

You use the terms 'non-technical phraseology' and claim to uneducated? Being self taught is probably the best way to learn anything, especially this stuff. As for being old.....;)

Oh, BTW have you tried right clicking on the .exe and changing the properties to allow it to be executable? I can't remember the correct wording as I am on my works XP machine (I am working of course!!).

---

### Post by mimseycal on 2010-08-25
I'll give it a go ... thanks for the suggestion

---

### Post by mimseycal on 2010-08-25
Migs!!! I could kiss you ... if it hadn't been for my avowal never to kiss strangers and you being at work and all ... It WORKS :D Now we'll see what this game is made of ;)

---

### Post by 3rdalbum on 2010-08-25
Instead of going down the purely-GUI route for Wine (which has never worked for me), try running the program from the command-line using my little howto:

[http://www.chrislees.info/ubuntu/easy-run-files.shtml](http://www.chrislees.info/ubuntu/easy-run-files.shtml)

---

### Post by mimseycal on 2010-08-25
Thanks 3rd ... I've got it up and loading now but I will give your program a go when I have finished with it :)

Had a quick look at your site. Looks nice and very inviting ...

---

### Post by migs73 on 2010-08-25
Glad to be of help mimsey. If there is one thing about Ubuntu that makes it far superior to any other OS I've seen, it's the people on here.

Just remember there is no such thing as a stupid question, only stupid answers. Also (my favourite) 'to ask it but a moments shame, but not to ask and to remain ignorant, is a lifelong shame', apparently an ancient chinese proverb.

EDIT; Just realised that sounds like me bigging myself up!! I meant that I have learned all that I know (not much really, so far still a noob) from others on here. I like being able to give some help back. Hopefully soon you will be able to do the same.

---

