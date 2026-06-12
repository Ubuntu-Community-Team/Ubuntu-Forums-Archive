---
title: "open a pdf with firefox?"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by MichaelBurns on 2009-12-14
Back in the dark days when I used Windows XP, I discovered that opening .pdf file in firefox was much more convenient than opening .pdf file in acroread (quicker, less likely to freeze the computer).  So, in Windows XP, I set the file association for .pdf to open with firefox, and all was well.  I don't recall that I had to make any special settings in firefox in order to do this, but that was a while ago; I just don't remember.

Now, I am in the days of enlightenment of using Xubuntu (on the same computer).  After some investigation, I presume that the default .pdf viewer (that I have been using) is called evince.  It is slow to load and sluggish to scroll.

I have looked through the forums for a solution.  My first attempt was to try xpdf, but that was so unbelievably slow to load a .pdf file (literally minutes), that I promptly uninstalled it (after freezing the computer from clicking on the same .pdf icon over and over again not knowing if it was doing anything).  Now, I have tried installing the PDF Download add-on (for firefox).  But, when I right-click a .pdf icon and select the open-with-firefox option, firefox gives an infinitely recuring dialog box asking if I want to open it with firefox.  (I wonder what would happen if I check the set-this-as-default box.)  Maybe there're some settings that I need to make now that I have the add-on?

Any suggestions?  I want two things (or three if possible):
1.  loads the .pdf in < 1 sec,
2.  scrolls through the pages of the document seemlessly,
(3.  uses minimal RAM)
(I realize that 2. and 3. may be incompatible.  If I must choose, I prefer 2..)
In other words, I don't care about any fancy features; all I want from the pdf viewer is to read papers on my computer without (annoying/distracting) delays between pages and between several different papers.

---

### Post by bodhi.zazen on 2009-12-14
Personally I have been happy with evince, but if you like, try a ff extension :

[https://addons.mozilla.org/en-US/firefox/tag/pdf%20viewer](https://addons.mozilla.org/en-US/firefox/tag/pdf%20viewer)

---

### Post by Sir Jasper on 2009-12-14
Hi,

There is a linux version of Foxit Reader which may please you.

My regards

---

### Post by MichaelBurns on 2009-12-14
Thanks to both of you for your prompt replies!

> **bodhi.zazen said:**
> ... if you like, try a ff extension :

[https://addons.mozilla.org/en-US/firefox/tag/pdf%20viewer](https://addons.mozilla.org/en-US/firefox/tag/pdf%20viewer)I thought that's what I had done with the PDF Download add-on ???

But PDF Download is is not on the list on that site, which shows only four items.  The only item whose description seems close to what I'm looking for is the Google Docs Viewer, but it talks about clicking on hyperlinks, and clicking as usual to use my default viewer otherwise.  But I want firefox to be my default viewer (I think).  And anyway, why doesn't the PDF Download thing work?

I suppose that I can try the Google Docs Viewer.

BTW, what's the difference between "add-on", "extension", and "plugin"?  For instance, in the Tools > Add-ons menu, there is a Get Add-ons button, but there are also extensions and plugins buttons.

> **Sir Jasper said:**
> Hi,

There is a linux version of Foxit Reader which may please you.

My regardsI'll give it a try.  Thanks.

---

### Post by MichaelBurns on 2009-12-15
I could not find foxit with synaptic.  Does it go by some other name?

---

### Post by Grey Seal on 2009-12-15
Stupid question.

Just downloaded Kubuntu 9.10 yet have been unable to download FF 3.5. Went into Internet my menu editor and got nowhere. Is EI 8 the final solution?

GS

---

### Post by Sir Jasper on 2009-12-15
Hi,

For Foxit Reader for Debian go to:
[http://www.foxitsoftware.com/pdf/desklinux/download.html](http://www.foxitsoftware.com/pdf/desklinux/download.html)
click the second option 
FoxitReader_1.1.0i386.deb
to download it to your desktop.

Double click your desktop file and it will install under Applications>Office

My regards

---

### Post by MichaelBurns on 2009-12-16
Thanks for the link, Sir Jasper.  Do you know why synaptic can't find it?

---

### Post by Sir Jasper on 2009-12-16
Hi,

Yes I do, but have you tried it and do you find it meets all of your three ideal requirements?

My regards

---

### Post by llawwehttam on 2009-12-16
Hmm, I think foxit used to be in synaptic but I just use evince now and I don't have any problems with it.

---

### Post by MichaelBurns on 2009-12-16
> **Sir Jasper said:**
> ... have you tried it and do you find it meets all of your three ideal requirements?I mean no offense, and I do appreciate your suggestions, but I don't want to try something that is not in the repositories.

A while back I bought an EeePC and put Easy Peasy on it.  There were a lot of programs that I wanted that were not in the repositories, so I either got their source code or their .deb file and "make"ed or installed.  I reinstalled Easy Peasy several times.  I don't know if Easy Peasy just had problems, or if I downloaded some bad sources or bad .deb packages (or, most likely, that I just have no clue how to run a computer).  Anyway, I just feel safer now to stick with the repositories.

I don't want to ***ever*** reinstall Xubuntu on my laptop, which has been rockin' along (with Windows XP until I recently installed Xubuntu) without a hitch since 2005.  I realize that I will have problems with an OS that isn't designed specifically for my laptop, and I am willing to tolerate many issues, as long as the important ones can get resolved.  I'm even willing to tolerate the inability to use some of the programs that I once loved under Windows XP, as long as I can find a good alternative under Xubuntu.  But reinstallation will be too much for me to handle.  Since I intend to make a tremendous effort to stick with Xubuntu, and after my Easy Peasy experience, I don't imagine that I will be installing from outside the repos any time soon.

---

### Post by Sir Jasper on 2009-12-16
Hi,

I hope that you are cloning Xubuntu (ideally regularly) else what you want may not be possible.

Foxit Reader uses about 1/6 th of the RAM used by evince (10 MB v 60 MB) and for me the load time is twice as fast as evince (about 1¨ v about 2¨) and both scroll seamlessly.

Under Application>System do you see Computer janitor? If not, then if you use Synaptic and install it you will be able to easily uninstall any Debian package such as Foxit Reader. 

Foxit Reader is hugely regarded, but you are welcome to try it or not.

My regards

---

### Post by MichaelBurns on 2009-12-18
> **Sir Jasper said:**
> I hope that you are cloning Xubuntu (ideally regularly) ...What does *that* mean?

> **Sir Jasper said:**
> Under Application>System do you see Computer janitor?No.  But that's probably because I use an underpriveledged desktop account for regular use.  I will have to get back to you after I log into my admin account.  However, I don't remember seeing such an item in the Application>System menu in the admin account anyway.

As in my last reply, thank you for taking the time to explain.  I'm sure someone will stumble upon your comments and find them useful.  But I maintain my recalcitrance.

---

### Post by Sir Jasper on 2009-12-18
Hi,

Google ¨clone¨ or ¨cloning¨ or use the search facility above. Many of those who seek help in this Forum would not need any help if they could restore their
entire OS and MBR when all goes sadly wrong.

It hardly matters whether you have ¨Computer janitor¨ if you would never use it even if you have it.

My regards

---

### Post by yeats on 2009-12-18
> I mean no offense, and I do appreciate your suggestions, but I don't want to try something that is not in the repositories.

A while back I bought an EeePC and put Easy Peasy on it. There were a lot of programs that I wanted that were not in the repositories, so I either got their source code or their .deb file and "make"ed or installed. I reinstalled Easy Peasy several times. I don't know if Easy Peasy just had problems, or if I downloaded some bad sources or bad .deb packages (or, most likely, that I just have no clue how to run a computer). Anyway, I just feel safer now to stick with the repositories.

I understand your reluctance, and if you install a lot of non-repository .debs or programs from source, you are risking breakage to your system (I speak from experience!).  *However* the logic behind using .deb packages is that they check your system for the right dependencies and will not work if those dependencies are not present.  

./configure and make scripts do the same thing, but they are not part of the apt/.deb/dpkg structure that knows what your system needs to continue functioning.  They just check if you have the right version of a  dependency installed or not and exit if you don't.

In short:  .debs are *basically* safe as long as you don't try to install a lot of them that were not built for your distro/release.

---

### Post by MichaelBurns on 2009-12-20
Thanks to both of you.  I killed my harddrive, so, I guess this issue has become moot, for me at least.

---

### Post by Sir Jasper on 2009-12-20
Hi,

Do you mean you accidentally erased one or more partitions; or was it more drastic and/or more deliberate?

I hope you have not lost too much time or important data.

My regards

---

### Post by sgosnell on 2009-12-20
You can install the actual Adobe reader, and it will open .pdf files inside Firefox.  That isn't everyone's choice, but it does work.  It's not in the repositories, but Adobe should be as trustworthy as Ubuntu for the security of the software they provide.

---

### Post by MichaelBurns on 2009-12-22
> **Sir Jasper said:**
> Do you mean you accidentally erased one or more partitions; or was it more drastic and/or more deliberate?It's funny that you should ask if it was deliberate.  Let's just say it that I learned an inconvenient and expensive lesson about venting my frustration, which, I'm sad to say, is probably not the last time I will learn it.  Now I have to decide if the handful of files that I hadn't backed up are worth a few hundred $, or if I should spend that $ on anger management.  Hmm...

> **sgosnell said:**
> You can install the actual Adobe reader, and it will open .pdf files inside Firefox.Do you know if that's the way Windows XP does it?

---

### Post by sgosnell on 2009-12-22
Yes, it's exactly the way Windows does it.  I don't like it very much, but that's just me.  It opens in a Firefox tab, not in a separate window.  If you have Firefox set to open new windows instead of tabs, then it should open a new Firefox window.

---

### Post by MichaelBurns on 2009-12-22
I hate those godawful tabs.  Whenever I actually have a harddrive in my laptop, I change *a messload* of the firefox settings ... one of the main reasons that I didn't want to reinstall.

Well, I suppose that, since I'm gonna have to reinstall anyway, and since I would have to go outside of the repos anyway to set it up the way I liked it in Windows, then I might as well try this foxit thing first.

---

### Post by sgosnell on 2009-12-22
Well, I hate having many browser windows open, I prefer tabs by far.  But there's a reason they let you do it both ways.

---

### Post by Warprunner on 2010-04-04
> **bodhi.zazen said:**
> Personally I have been happy with evince, but if you like, try a ff extension :

[https://addons.mozilla.org/en-US/firefox/tag/pdf%20viewer](https://addons.mozilla.org/en-US/firefox/tag/pdf%20viewer)

Thank you ...was pulling my hair out trying to find this again. FYI works in 10.04 with Firefox

---

