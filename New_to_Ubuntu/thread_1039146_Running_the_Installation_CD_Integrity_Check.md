---
title: "Running the Installation CD Integrity Check"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by MaryMay on 2009-01-14
Hello,

I'm new here after being referred to the OS by a friend. Frankly, I know very little about all this techie stuff. I purchased my first computer 4 years ago and the only OS I've ever used was Windows XP. Linux is going to be new to me. I'm no coder and I do good to know how to run a computer at times, depending on what needs to be done. 

In saying all that, know that I'll likely end up asking some odd questions. 

I successfully burned a CD, verified the md5 sum (hash) of the .iso file according to the directions. Thus far, everything seems to be fine. Then, I tried to check the CDs integrity by following the directions listed here:[https://help.ubuntu.com/community/Installation/CDIntegrityCheck]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck")

I got to the displayed window and selected Check CD for defects, and hit enter. I left it running at 12:AM and got up at 7AM, it was still running. Or, it looked like it was. The screen never changed. Did I do something wrong?

I appreciate any help given.

---

### Post by RichardLinx on 2009-01-14
You didn't do anything wrong;) I've never checked a CD for defects because usually after burning the .ISO file I assume It will work how It's supposed to, and so far It has every time. It's possible that the CD had no defects so no errors showed up on screen (Though I'm not 100% sure since I've never run this process). I suggest you try running the disk as a live CD and seeing If it works. By running the disk as a live CD you get to preview the OS (Operating System) with no changes being done to your computer.

---

### Post by mikewhatever on 2009-01-14
Hi and welcome,
the integrity check shouldn't have to take hours, so it looks like something wasn't right. That said, there is probably nothing wrong on your part. Did you burn the iso at low speed (x4) and used an acceptable quality cd? Did you try the first option of trying Ubuntu without installing?

> **RichardLinx said:**
> You didn't do anything wrong;) I've never checked a CD for defects because usually after burning the .ISO file I assume It will work how It's supposed to, and so far It has every time. It's possible that the CD had no defects so no errors showed up on screen (Though I'm not 100% sure since I've never run this process). I suggest you try running the disk as a live CD and seeing If it works. By running the disk as a live CD you get to preview the OS (Operating System) with no changes being done to your computer.

Lots of confidence will get you in trouble.:twisted:

---

### Post by newbee70 on 2009-01-14
> **MaryMay said:**
> Hello,

I'm new here after being referred to the OS by a friend. Frankly, I know very little about all this techie stuff. I purchased my first computer 4 years ago and the only OS I've ever used was Windows XP. Linux is going to be new to me. I'm no coder and I do good to know how to run a computer at times, depending on what needs to be done. 

In saying all that, know that I'll likely end up asking some odd questions. 

I successfully burned a CD, verified the md5 sum (hash) of the .iso file according to the directions. Thus far, everything seems to be fine. Then, I tried to check the CDs integrity by following the directions listed here:[https://help.ubuntu.com/community/Installation/CDIntegrityCheck]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck")

I got to the displayed window and selected Check CD for defects, and hit enter. I left it running at 12:AM and got up at 7AM, it was still running. Or, it looked like it was. The screen never changed. Did I do something wrong?

I appreciate any help given.

did it show the reboot message at the bottom?

if it showed checksum failure you had a bad burn of the disk.



if so did you reboot?

---

### Post by RichardLinx on 2009-01-14
> **mikewhatever said:**
> Hi and welcome,
the integrity check shouldn't have to take hours, so it looks like something wasn't right. That said, there is probably nothing wrong on your part. Did you burn the iso at low speed (x4) and used an acceptable quality cd?

Well that completely contradicts what I said/thought haha :D Although I don't think burn speed is too much of an issue, I've burned Linux ISO's at speeds of 16x and above and never had a single issue. :)

---

### Post by MaryMay on 2009-01-14
> **mikewhatever said:**
> Hi and welcome,
the integrity check shouldn't have to take hours, so it looks like something wasn't right. That said, there is probably nothing wrong on your part. Did you burn the iso at low speed (x4) and used an acceptable quality cd? Did you try the first option of trying Ubuntu without installing?



Lots of confidence will get you in trouble.:twisted:


How do I change the burn speed? I'm pretty sure I used a good CD. It fits the requirements: 80 min/700 MB. It's a Maxell CD-R if that helps?

Thanks to everyone who responded so quickly.


Edit: Yes, it showed some sort of Reboot option below the list. However, it never said anything about a failure.

---

### Post by mikewhatever on 2009-01-14
> **RichardLinx said:**
> Well that completely contradicts what I said/thought haha :D Although I don't think burn speed is too much of an issue, I've burned Linux ISO's at speeds of 16x and above and never had a single issue. :)

The fact that you haven't had a problem so far, doesn't mean others will have it the same way.

MaryMay, the burning speed is usually adjusted through the burning program.

---

### Post by RichardLinx on 2009-01-14
> **mikewhatever said:**
> The fact that you haven't had a problem so far, doesn't mean others will have it the same way.

Your probably right, I really need to stop 'assuming' everything. :) When It comes to the speed it burned at I guess It would work fine as long as the CD/DVD drive was able to read at those speeds. Then again this is just another assumption of mine. :)

---

### Post by boof1988 on 2009-01-14
> **MaryMay said:**
> How do I change the burn speed? I'm pretty sure I used a good CD. It fits the requirements: 80 min/700 MB. It's a Maxell CD-R if that helps?

Thanks to everyone who responded so quickly.


Edit: Yes, it showed some sort of Reboot option below the list. However, it never said anything about a failure.

You could try checking the cd integrity again.

I just ran the test with these results.  (Note that all of this information is present on the screen after the test):

There was the *graphic* "Ubuntu" with orange progress bar centered on the screen and then the following (three lines of) text below it:

```
Checking integrity, this may take some time
Check finished: no errors found
Press any key to reboot your system
```

Hope this helps some...  If you have/had the line "Check finished: no errors found" than your disk should be good.

---

### Post by boof1988 on 2009-01-14
> **RichardLinx said:**
> Your probably right, I really need to stop 'assuming' everything. :) When It comes to the speed it burned at I guess It would work fine as long as the CD/DVD drive was able to read at those speeds. Then again this is just another assumption of mine. :)

I haven't had many problems with burning disks too fast either (that I know of).  I usually let the application use the maximum speed that it defaults to.  And then use the ?error correction? option as well so (I think) that the burning application keeps track of how well that burn goes.  One application (I can't remember which) has a check CD integrity after the burn.  It burns the disk and then ejects it.  The user is prompted to put the disk back in and then the integrity check is done right then.

Of course there are probably other people who have had a heck of a time getting the disks to burn properly and burning at a slower speed is one of the fixes for them.  Guess I have been pretty lucky in that respect.  I don't have much patience to wait for a disk to burn at slow speed...  To much to get done:)

---

### Post by MaryMay on 2009-01-14
Ahh, see I was never even getting the orange process bar. Though, the burner itself sounded like it was running. Perhaps it was just stuck. At any rate, I tried to run it twice, both with the same results. Also, I never got a no error notification. 

Hmm, I think I'm just going to try the option that allows you to try it without changes to the computer itself and see how that goes. 

Thanks to everyone who replied.

---

### Post by RichardLinx on 2009-01-14
> **MaryMay said:**
> Ahh, see I was never even getting the orange process bar. Though, the burner itself sounded like it was running. Perhaps it was just stuck. At any rate, I tried to run it twice, both with the same results. Also, I never got a no error notification. 

Hmm, I think I'm just going to try the option that allows you to try it without changes to the computer itself and see how that goes. 

Thanks to everyone who replied.

No problem. Tell us how it goes. :)

---

### Post by MaryMay on 2009-01-14
One more, or a couple more, quick questions then I promise to leave you all alone until I need help again. Which could very well be when and if I try to install it.

1) I read somewhere that Ubuntu doesn't require antivirus protection. Is there a reason why? If this is true, I'm in love already. My Norton slows my computer down terribly!

2)Do Windows programs work on Ubuntu as well? If not, is there a way to get them to do so?

3)Does Internet Explorer work on Ubuntu?

4) If you don't feel like answering a bunch of what are probably basic questions, just refer me to where I can find the information myself.

Thanks again. I've never seen such a helpful forum in my life, and you're all so quick to respond.

---

### Post by maclinux on 2009-01-14
Something similar has been happening to me lately.  I download the CD. Burn the iso, K3b or Brasero do the check sum and integrity check, but the same keeps on happening which does not take place with another CD that I've burned a year ago.  When it starts either to try the OS or straight to install, it never mounts a kernel, goes straight to a black screen with a blinking dot in the upper left corner and it remains like this forever.  Sometimes I prefer to downl the later image so I dont have to stay to long to bring everything to date, just in case I have to reinstall.  I seriouly doubt there is a problem with the iso itself.

Any help please?

---

### Post by RichardLinx on 2009-01-14
> **MaryMay said:**
> [B]One more, or a couple more, quick questions then I promise to leave you all alone until I need help again. Which could very well be when and if I try to install it.
[/B]
Just about everyone here is happy to help. Well at least I think so anyway. :)

1) **I read somewhere that Ubuntu doesn't require antivirus protection. Is there a reason why? If this is true, I'm in love already. My Norton slows my computer down terribly!**
Ubuntu does not require Antivirus protection, I can't remember the specifics (the technical side of things) but I can tell you that there are some advantages to having around a 1% user base. I also believe that If a virus is written It would be patched almost instantly since there are developers working pretty much around the clock.
2)**Do Windows programs work on Ubuntu as well? If not, is there a way to get them to do so?**
It is possible to get some (not all) windows programs to work on Linux/Ubuntu using WINE or Crossover Office and a few other apps out there. However you'll likely be able to find alternatives for a lot of software, unless It is something specialized like CAD for example.

**3)Does Internet Explorer work on Ubuntu?**
You are able to get IE6 working on Ubuntu through WIne. I haven't tried using IE7 yet though... Do you mind me asking why you would want to use IE7 on Ubuntu?

**4) If you don't feel like answering a bunch of what are probably basic questions, just refer me to where I can find the information myself.**
[http://en.wikipedia.org/wiki/Ubuntu](http://en.wikipedia.org/wiki/Ubuntu)
[http://www.ubuntu.com/support](http://www.ubuntu.com/support)
There are also many free books available as well as books for sale. 
[B]
Thanks again. I've never seen such a helpful forum in my life, and you're all so quick to respond.[/B]
Always happy to help.:)

PS: Sorry my answers couldn't be a bit more comprehensive, It's quite late (or early I should say) where I am.

---

### Post by RichardLinx on 2009-01-14
> **maclinux said:**
> Something similar has been happening to me lately.  I download the CD. Burn the iso, K3b or Brasero do the check sum and integrity check, but the same keeps on happening which does not take place with another CD that I've burned a year ago.  When it starts either to try the OS or straight to install, it never mounts a kernel, goes straight to a black screen with a blinking dot in the upper left corner and it remains like this forever.  Sometimes I prefer to downl the later image so I dont have to stay to long to bring everything to date, just in case I have to reinstall.  I seriouly doubt there is a problem with the iso itself.

Any help please?

Could you please post your hardware specs and what version of Ubuntu you have recently tried which is causing you problems. It could be that you have download a 64Bit version and you are running 32Bit hardware. My friend had a similar problem only It was the other way around. :D

---

### Post by MaryMay on 2009-01-14
Thank you!

Well, Internet Explorer is all I've ever used. I don't even know what else is available in that area. I wouldn't mind trying another browser though.

---

### Post by Doug11987 on 2009-01-14
> **MaryMay said:**
> 
1) I read somewhere that Ubuntu doesn't require antivirus protection. Is there a reason why? If this is true, I'm in love already. My Norton slows my computer down terribly!

2)Do Windows programs work on Ubuntu as well? If not, is there a way to get them to do so?

3)Does Internet Explorer work on Ubuntu?


Hi, I have only just started using Ubuntu too, but can help you answer your questions.

1. It isn't ***as*** susceptible to virus as, compared to Windows very few people run it, and therefore people just don't tend to make them for Ubuntu. Also it is designed to be harder to break. I have decided to use a firewall but no antivirus with mine. But I am careful with what websites I go to. If you plan to swap files you download etc with a Wndows computer then it is good as a virus could be downloaded, not damage your Ubuntu computer, but be transfered to a Windows computer.

2. There are a couple of ways to do this, I know ones called Wine, but I don't know anything about them. I have been able to find free linux programs that work for everything I need.

3.Not that I am aware of, but Firefox comes with the CD and it does exactly the same, even looks pretty similar.

I am just passing on info here, I'm sure others can give you more advice. 

On a side note, I found it very easy to switch, everything worked straight away for me (external HHD, wireless, wired network, USB key etc.) so give it a try.

Hope that helps, Doug.

---

### Post by RichardLinx on 2009-01-14
> **MaryMay said:**
> Thank you!

Well, Internet Explorer is all I've ever used. I don't even know what else is available in that area. I wouldn't mind trying another browser though.

Haha, and I was wondering why people still use It! :D I wont bother going into a long rant (well hopefully) but IE is full of security vulnerabilities (I believe a recent one was discovered which actually allowed people to take full advantage of another users windows installation.) There are many alternative browsers available for both Linux and Windows. Firefox is default in Ubuntu. Not to mention that browsers like Firefox and Opera are much faster at things like page rendering compared to IE. And I'm not 100% sure on this but I believe Opera and Firefox make much better use of system resources compared to IE, well I know Opera definitely does... Whoops looks like I've gone on a bit to long already, I'll stop now. :)

---

### Post by mikewhatever on 2009-01-14
> **MaryMay said:**
> Thank you!

Well, Internet Explorer is all I've ever used. I don't even know what else is available in that area. I wouldn't mind trying another browser though.

Wow, I kind of expect users to drift to Linux from using open source apps like Firefox and OpenOffice under Windows. This way they are familiar at least with a couple of application. Why do you want Linux anyway?

---

### Post by kansasnoob on 2009-01-14
> **MaryMay said:**
> One more, or a couple more, quick questions then I promise to leave you all alone until I need help again. Which could very well be when and if I try to install it.

1) I read somewhere that Ubuntu doesn't require antivirus protection. Is there a reason why? If this is true, I'm in love already. My Norton slows my computer down terribly!

2)Do Windows programs work on Ubuntu as well? If not, is there a way to get them to do so?

3)Does Internet Explorer work on Ubuntu?

4) If you don't feel like answering a bunch of what are probably basic questions, just refer me to where I can find the information myself.

Thanks again. I've never seen such a helpful forum in my life, and you're all so quick to respond.

First things first; before I ever burn an iso to disc I check the md5sum of the download. Like I was recently doing some testing for Ubuntuzilla and I needed Mint 4 so I copy & print the MD5SUM from the download site and then downloaded the iso to my desktop. Then I just had to go to terminal and:

```
cd ~/Desktop 
```

That results in:

> lance@lance-desktop:~/Desktop$

So then (using my Mint 4 download as an example) I enter:

```
md5sum LinuxMint-4.0.iso
```

It looks like (including the output):

> lance@lance-desktop:~/Desktop$ md5sum LinuxMint-4.0.iso
572a56ec165ef6ad8f785cc7f13a5a14  LinuxMint-4.0.iso

I then compare that md5sum to the one I previously copied and printed.

Of course I was using Ubuntu to perform those steps and you're still using Windows so look here to find out about checking md5sum with Win:

[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows)

And there's more here about checking md5sum on the cd itself (much slower):

[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20CD](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20CD)

Now, as far as your other questions:

[http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

