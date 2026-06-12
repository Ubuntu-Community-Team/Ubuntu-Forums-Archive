---
title: "Lucid just wont happen"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by daniell59 on 2010-05-01
I burned many cds and still cannot install Lucid. Various error messages.
Tried to upgrade and got the following message. Please see image.
I really hate to give up.

---

### Post by Seal Daemon on 2010-05-01
> **daniell59 said:**
> I burned many cds and still cannot install Lucid. Various error messages.


It doesn't seem you're trying to install it from the CD .. Any specific difficulties / errors ?

---

### Post by daniell59 on 2010-05-01
> **Seal Daemon said:**
> It doesn't seem you're trying to install it from the CD .. Any specific difficulties / errors ?

I burned numerous CDs and most of the time I got this error.

---

### Post by ugm6hr on 2010-05-01
Did you check the md5sum of the iso?

Did you run the CD integrity checker?

---

### Post by daniell59 on 2010-05-01
> **ugm6hr said:**
> Did you check the md5sum of the iso?

Did you run the CD integrity checker?

I ran the CD integrity checker but not the md5sum. How do I run the md5sum?

Thanks

---

### Post by Michl on 2010-05-01
This is a known bug on launchpad.  I had the
same problem on a Dell C610 laptop.  You
could try the alternate install CD.  I didn't 
try that.

It's good to learn how to do the MDsum check,
and for instructions go to HowToBurnCD on
the ubuntu wiki page.  But I'm sure this isn't
your problem.

---

### Post by ssulaco on 2010-05-01
> **daniell59 said:**
> I ran the CD integrity checker but not the md5sum. How do I run the md5sum?


[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
and....hashes...
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
Burn........Slllooooowwwww,.......instead of install try running "Live"

---

### Post by daniell59 on 2010-05-01
> **Michl said:**
> This is a known bug on launchpad.  I had the
same problem on a Dell C610 laptop.  You
could try the alternate install CD.  I didn't 
try that.

It's good to learn how to do the MDsum check,
and for instructions go to HowToBurnCD on
the ubuntu wiki page.  But I'm sure this isn't
your problem.

Thanks
So I guess there is no use burning more CDs.
I downloaded the alternate CD. It did not have an option to try before installing. Will the alternate CD give the same results once installed.
With so many people experiencing bugs, I am surprised that they have not fixed it as yet. Any advice on how to lear to use MDsum will be appreciated.

---

### Post by slooksterpsv on 2010-05-01
Few things I would do, md5sum like stated above, if it checks out, burn it at a slower speed, if that still fails, a memory check - could have bad RAM.

---

### Post by ssulaco on 2010-05-01
You might also try a torrent
[http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)

---

### Post by daniell59 on 2010-05-01
> **slooksterpsv said:**
> Few things I would do, md5sum like stated above, if it checks out, burn it at a slower speed, if that still fails, a memory check - could have bad RAM.

I burned it at the slowest possible speed. I have both Ubuntu 9.10 and Vista on this machine. They both run perfect. I guess it wont hurt to run another memory check. Previous memory checks have shown no errors.

---

### Post by RyanBFS on 2010-05-01
I ran into the same message and went to live CD mode where it installed correctly.... so far that is.  I also burned the CD at 10x which is the max I'm comfortable with ISO's.  You could also try putting it on a flash drive and installing from there.  I didn't check the MD5 but it's a good idea, just couldn't wait to get my first 10.4 final up and running :) .

---

### Post by daniell59 on 2010-05-01
> **RyanBFS said:**
> I ran into the same message and went to live CD mode where it installed correctly.... so far that is.  I also burned the CD at 10x which is the max I'm comfortable with ISO's.  You could also try putting it on a flash drive and installing from there.  I didn't check the MD5 but it's a good idea, just couldn't wait to get my first 10.4 final up and running :) .

What is "live cd mode"?

---

### Post by ssulaco on 2010-05-01
> **ssulaco said:**
> [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
and....hashes...
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
Burn........Slllooooowwwww,.......instead of install try running "Live"

[https://help.ubuntu.com/community/LiveCD#How-To%20LiveCD%20Ubuntu](https://help.ubuntu.com/community/LiveCD#How-To%20LiveCD%20Ubuntu)
You are going to be running the OS from the optical drive........if everything seems good try installing while running live ,like Ryan suggested....there will be an install icon on the desktop

---

### Post by RyanBFS on 2010-05-01
sorry, I meant trying to see if you get the same problems when running off the live CD.  I'd download the 10.4 stan eddition and go to "try ubuntu without installing" and test it out.  Then you can click on the install ubuntu option and move forward from there.

---

### Post by ssulaco on 2010-05-01
> **ryanbfs said:**
> sorry, i meant trying to see if you get the same problems when running off the live cd.  I'd download the 10.4 stan eddition and go to "try ubuntu without installing" and test it out.  Then you can click on the install ubuntu option and move forward from there.
+1

---

### Post by Axilus on 2010-05-01
I got the exact same error message earlier today, however I just ran the live CD and ignored it; Then I proceeded to installing Lucid once the CD was up and running.

Seems to be a bug free install so far.

---

### Post by myth01 on 2010-05-01
> **RyanBFS said:**
> sorry, I meant trying to see if you get the same problems when running off the live CD.  I'd download the 10.4 stan eddition and go to "try ubuntu without installing" and test it out.  Then you can click on the install ubuntu option and move forward from there.

+ another 1

I had the same problem at first.  Googling found this:

[http://www.ubuntu.com/getubuntu/releasenotes/1004/]("http://www.ubuntu.com/getubuntu/releasenotes/1004/")

check out the section titled 'Desktop installer sometimes crashes on startup'

Worked for me.

---

### Post by daniell59 on 2010-05-01
> **RyanBFS said:**
> sorry, I meant trying to see if you get the same problems when running off the live CD.  I'd download the 10.4 stan eddition and go to "try ubuntu without installing" and test it out.  Then you can click on the install ubuntu option and move forward from there.

I wish that I could get that far.

---

### Post by myth01 on 2010-05-01
> **daniell59 said:**
> I wish that I could get that far.

How far do you get?  Does the live CD (ie the CD you burned with the standard - not alternate - ISO) spin up, load for ages and then give you the error?

---

### Post by daniell59 on 2010-05-01
> **myth01 said:**
> How far do you get?  Does the live CD (ie the CD you burned with the standard - not alternate - ISO) spin up, load for ages and then give you the error?

yes

---

### Post by RyanBFS on 2010-05-01
> **daniell59 said:**
> yes

Can you get to BIOS? or even better do you get to the options page on the disk? where you can run mem test?  Also is this the first CD still?   Do you have another comp that you can burn one from?

---

### Post by myth01 on 2010-05-01
Same thing was happening to me, this is what I found out/did, not sure if you have tried this already:

Right at the beginning of the CD booting there should be a purple screen with a tiny icon at the bottom that looks like a keyboard/arrow/person in a circle, hit any key on the keyboard and you should get the normal live CD boot menu (Try Ubuntu without installing/Install Ubuntu/Disc Error Check etc).  Select 'Try Ubuntu without installing' and then the desktop should load up, from there double click the Install Ubuntu icon.

---

### Post by daniell59 on 2010-05-01
> **myth01 said:**
> Same thing was happening to me, this is what I found out/did, not sure if you have tried this already:

Right at the beginning of the CD booting there should be a purple screen with a tiny icon at the bottom that looks like a keyboard/arrow/person in a circle, hit any key on the keyboard and you should get the normal live CD boot menu (Try Ubuntu without installing/Install Ubuntu/Disc Error Check etc).  Select 'Try Ubuntu without installing' and then the desktop should load up, from there double click the Install Ubuntu icon.

Thanks, I will try it later and report back.

---

### Post by myth01 on 2010-05-01
No worries, I hope it works :)

---

### Post by Don1500 on 2010-05-01
Seen this also. 

Had the problem with Beta1, Beta2, RC and Final. But on Final when I hit "OK" insted of rebooting it loaded Ubuntu. I then installed and everything is now working. I hope this bug is found and fixed soon. It could be carried forward to 10.10 if it's not found.

---

### Post by daniell59 on 2010-05-01
> **myth01 said:**
> Same thing was happening to me, this is what I found out/did, not sure if you have tried this already:

Right at the beginning of the CD booting there should be a purple screen with a tiny icon at the bottom that looks like a keyboard/arrow/person in a circle, hit any key on the keyboard and you should get the normal live CD boot menu (Try Ubuntu without installing/Install Ubuntu/Disc Error Check etc).  Select 'Try Ubuntu without installing' and then the desktop should load up, from there double click the Install Ubuntu icon.

It worked. I am now on the Ubuntu live cd. I have a question however. Am I missing something? I don't see the little squares on the upper right side of the page. To minimize or maximize.
What is going on? Why was it necessary to do that?
How could I have known that?
I wasted about 10 cds.

---

### Post by myth01 on 2010-05-01
> **daniell59 said:**
> It worked. I am now on the Ubuntu live cd. I have a question however. Am I missing something? I don't see the little squares on the upper right side of the page. To minimize or maximize.
What is going on? Why was it necessary to do that?
How could I have known that?
I wasted about 10 cds.

Glad it worked daniell59, sorry you wasted so many CDs, at least you have lots of copies to dish out to mates/family to help spread the Ubuntu...:P

The maximise/minimize buttons in the default theme are in the top left of the windows instead of top right.  I have seen threads about changing it but I'm not too bothered about changing it yet so haven't checked them out.  A different theme will most likely restore them to the top right.

I have no idea why they decided to include the splashscreen/keyboard combination to reach the menu rather than automatically displaying it (as they have in at least the last 5 releases).  Makes no sense and will only serve to confuse potential switchers (from other OS's).

Just my 2cents but I haven't been all that wow-ed by Lucid yet, Nautilus can be slow when using tabs, Google Chrome hangs when you go to Options, various menus/tools seem to hang for some time before displaying anything, seriously considering falling back to 9.10.

---

### Post by finster_pa on 2010-05-01
I was having this same problem, over and over.  Burned a few CDs, checked the MD5, etc, ran the alternative wubi d/l, no joy.

When it was rebooting and giving me the 5 seconds to hit "ESC", I did it and selected something like "ACPI workaround", even though I don't know what that means.  

It then started the installation!  I'm installed and running updates now.  I'm going to try it through a few reboot cycles next.

Hope that's helpful!

---

### Post by OmegaAI on 2010-05-01
I have encountered this error before and I have done the same thing you did (but I got really mad and broke something XD). 

Just off of a hunch I redownloaded the ISO and burned a disc using the new ISO and it seemed to have solved all my issues. 

Not sure if this will help but give it a go and see what happens.

---

### Post by Seal Daemon on 2010-05-02
Just tried to install Ubuntu 10.04 from a working CD ( worked fine a few days ago ) and got the same issue - somewhere around 85%, right after it updates something from the internet, it broke with the same error message.
 
** I'm not sure but it seems that the problem isn't in the image itself but some of the updates being pulled from the repos ..

---

