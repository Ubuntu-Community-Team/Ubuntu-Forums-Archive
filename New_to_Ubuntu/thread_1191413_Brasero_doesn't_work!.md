---
title: "Brasero doesn't work!"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by hapkidoman on 2009-06-18
Hey guys, is Brasero working for you in Ubuntu 9.04?  It worked for me in intrepid ibex, but when I upgraded to jaunty it stopped working.  More specifically, it won't burn an image of a DVD.  Does anyone have a similar problem?

Specifically, a pop up box comes up saying, 'Error while burning: Error while reading video DVD (no error)'

Why would it say error and then 'no error'?

The log lists the following:

Checking session consistency (brasero_burn_check_session_consistency burn.c:1905)
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_get_current_track
BraseroDvdcss called brasero_job_set_output_size_for_current_track
BraseroDvdcss stopping
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_get_session_output_size
BraseroDvdcss output set (IMAGE) image = /home/chip/brasero.iso toc = none
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_set_use_average_rate
BraseroDvdcss called brasero_job_set_current_action
BraseroDvdcss called brasero_job_get_current_track
BraseroDvdcss called brasero_job_set_current_action
BraseroDvdcss called brasero_job_get_fd_out
BraseroDvdcss called brasero_job_get_image_output
BraseroDvdcss called brasero_job_error
BraseroDvdcss finished with an error
BraseroDvdcss asked to stop because of an error
	error		= 1
	message	= "Error while reading video DVD (no error)"
BraseroDvdcss stopping
Session error : Error while reading video DVD (no error) (brasero_burn_record burn.c:2599)

---

### Post by 123456789123456789123456 on 2009-06-18
I had a simular problem, and I figured out what the problem was.  Do this, use synaptic to completely remove Brasero, then reinstall, it will tell you that to do so another program must be removed, tell it to go ahead and remove that program, and reinstall brasero, it will work.  In 8.10 it seems that Brasero existed along side cd/dvd copy program, as two seperate programs, now with the updated brasero, the cd/dvd copy program is included inside brasero.

---

### Post by nandemonai on 2009-06-18
Funny you mention that actually. I get those errors all the time but my burns are actually fine.

This is a fresh Jaunty install btw. I haven't had time to look into it or file reports as yet.

---

### Post by Crunchy the Headcrab on 2009-06-19
Images burn fine for me in Jaunty. I've never had an error.

---

### Post by hapkidoman on 2009-06-19
It's a fresh install for me as well.  I'll try to completely remove Brasero and re-install it again...see if that works.

---

### Post by hapkidoman on 2009-06-19
Nope.  That didn't seem to do the trick.  Any other suggestions?

---

### Post by Ragnar Bocephus on 2009-06-19
k3b.  :)

---

### Post by hapkidoman on 2009-06-19
I tried K3B.  It will copy the .iso, but it won't burn it to the disk.  It asks for a dual layer dvd-R, but I don't have a dvd player that will burn to a dual layer (I think....I might be making that up).

My compaint is, if brasero worked fine in intrepid, then I 'upgraded' to jaunty, shouldn't it work better?  Not be completely useless?  I thought the point of upgrading was to improve on a design and to get the next best thing.  I upgraded, not downgraded.

I would really appreciate if anyone could help me get brasero working, it seems I'm not the only one with this problem.  

Does anyone have any disc burner they prefer besides brasero and k3b?

---

### Post by nandemonai on 2009-06-19
> **hapkidoman said:**
> I tried K3B.  It will copy the .iso, but it won't burn it to the disk.  It asks for a dual layer dvd-R, but I don't have a dvd player that will burn to a dual layer (I think....I might be making that up).

My compaint is, if brasero worked fine in intrepid, then I 'upgraded' to jaunty, shouldn't it work better?  Not be completely useless?  I thought the point of upgrading was to improve on a design and to get the next best thing.  I upgraded, not downgraded.

I would really appreciate if anyone could help me get brasero working, it seems I'm not the only one with this problem.  

Does anyone have any disc burner they prefer besides brasero and k3b?

So your burns are actually failing then? And are you certain it's not hardware related? (bad discs / bad drive maybe?)

It's always possible though probably unlikely.

---

### Post by Redsunz on 2009-06-22
Same thing with me Brasero worked fine in Intrepid now with Jaunty it errors out every time.

"BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) 2602036235674bdd37d297dadd7547dd (66fa77789c7b8ff63130e5d5a272d67b before)
BraseroChecksumImage called brasero_job_error
BraseroChecksumImage finished with an error
BraseroChecksumImage asked to stop because of an error
	error		= 24
	message	= "Some files may be corrupted on the disc"
BraseroChecksumImage stopping
BraseroChecksumImage closing connection for BraseroChecksumImage
Session error : Some files may be corrupted on the disc (brasero_burn_record burn.c:2599)"

---

### Post by Redsunz on 2009-06-22
> **Redsunz said:**
> Same thing with me Brasero worked fine in Intrepid now with Jaunty it errors out every time.


I uninstalled Brasero with Synaptic package manager and forced install of 2.26.0.  Because that was listed as the current stable release. Here
[http://www.gnome.org/projects/brasero](http://www.gnome.org/projects/brasero)
I still got the same error as before plus now I have a new drink coaster:(

---

### Post by Pogeymanz on 2009-06-22
Have you tried deleting the config files in your home directory?

I don't know where brasero puts its config files, but some places to look are:

~/.brasero
~/.gnome
~/.config/brasero

Try finding and deleting those files after uninstalling brasero. Then reinstall it and try again.

---

### Post by Redsunz on 2009-06-22
> **Pogeymanz said:**
> Have you tried deleting the config files in your home directory?

I don't know where brasero puts its config files, but some places to look are:

~/.brasero
~/.gnome
~/.config/brasero

Try finding and deleting those files after uninstalling brasero. Then reinstall it and try again.

No, I didn't try that thanks for the idea.  
However it looks like their is a bug in the File checksum plug-in.  I would like to encourage everyone experiencing this bug to add them selves to the bug list in order to bring more attention to this issue.
Thanks
[http://bugzilla.gnome.org/show_bug.cgi?id=572840](http://bugzilla.gnome.org/show_bug.cgi?id=572840)

---

### Post by Redsunz on 2009-06-22
It appears that even though Brasero reports an error the disc is actually just fine.

---

### Post by wpshooter on 2009-06-22
I just downloaded Karmic and burned it using Brasero and it worked just fine on my 9.04 Ubuntu machine.

I am now going to take Karmic upstairs and see what the live CD will do on my test machine.

As far as these failures that others are having, and this may or may not be related to their problems BUT when was the last time they checked to make sure the FIRMWARE (not to be confused with drivers) for their CD-drives are on the latest and greatest version.  I am a stickler for this.  "Sometimes" (not always) making sure your BIOS and hardware firmware are up-to-date can cure a world of problems.

---

### Post by Redsunz on 2009-06-28
> **wpshooter said:**
> I just downloaded Karmic and burned it using Brasero and it worked just fine on my 9.04 Ubuntu machine.

I am now going to take Karmic upstairs and see what the live CD will do on my test machine.

As far as these failures that others are having, and this may or may not be related to their problems BUT when was the last time they checked to make sure the FIRMWARE (not to be confused with drivers) for their CD-drives are on the latest and greatest version.  I am a stickler for this.  "Sometimes" (not always) making sure your BIOS and hardware firmware are up-to-date can cure a world of problems.

Thats a good idea but the only available firmware update for my drive is a EXE file so after looking  around a bit I found my Dos boot flash drive copied the file to it and booted into that old time os tried to run the file and it said I needed to run it in a win32 bit os.  
I don't think the bios is the problem as my brand new Blue ray/dvd burner has the same error message in Brasero.  I won't be wiping Linux off and installing Vista any time soon just to correct a error message in Brasero.:P
However I hear Vista owners can get a free upgrade to Windows 7
I think for now I will just uncheck the image checksum plugin in Brasero.
No more windows Virus's on this machine!!

---

### Post by John_T on 2009-08-03
I'll add myself to the nlist of "Worked in 8.10, broken in 9.04"

I'm not even trying to burn disks.  I'm just creating ISOs of the kids DVDs to play on the other Ubuntu Media box. 

I have all the medibuntu / libdvdcss2 / restricted extras packages installed.

Regardless of the cause, I've got to say that "Error: (No Error)" is a rather non-informative message :P

The complete log is:

```
Checking session consistency (brasero_burn_check_session_consistency burn.c:1905)
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_get_current_track
BraseroDvdcss called brasero_job_set_output_size_for_current_track
BraseroDvdcss stopping
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_get_session_output_size
BraseroDvdcss output set (IMAGE) image = /mnt/bigdisk/Rips/brasero_RipName.iso toc = none
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_set_use_average_rate
BraseroDvdcss called brasero_job_set_current_action
BraseroDvdcss called brasero_job_get_current_track
BraseroDvdcss called brasero_job_set_current_action
BraseroDvdcss called brasero_job_get_fd_out
BraseroDvdcss called brasero_job_get_image_output
BraseroDvdcss called brasero_job_error
BraseroDvdcss finished with an error
BraseroDvdcss asked to stop because of an error
	error		= 1
	message	= "Error while reading video DVD (no error)"
BraseroDvdcss stopping
Session error : Error while reading video DVD (no error) (brasero_burn_record burn.c:2599)
```

---

### Post by saif on 2009-08-12
I am getting that same error when trying to rip a dvd image on jaunty.
error while reading video dvd (no error)
It quite a funny error (no error?) message! :) 
I haven't tried any of the suggestions in this thread, will try now. did anyone manage to find a working solution for it?

---

### Post by venturosa on 2009-08-16
I've had a recent problem burning iso images to dvd. Brasero reports an error and says that some files may be currupted. On playing the dvd (movie) on the computer (ubuntu jaunty) the fault shows up and the movie hangs. After wasting three dvds on this I put one of them in my 'stand alone' dvd player and found it played perfectly right through. I then put it on a windows computer where it also worked perfectly.
I've always used Brasero for burning isos and never had a problem before. All this points, IMHO, to the operating system because this problem has only appeared since I installed jaunty (clean install).

---

### Post by symon1980 on 2009-09-21
Omg! This Bug STILL hasn't been fixed!
i've had the same problem for about 6 months...... I even get the same error in other distro's using brasero such as Mandriva......... so its not Ubuntu related... its just that Brasero is a piece of buggy ****!

my solution... Use k3b! :)

---

### Post by Faolan84 on 2009-10-09
> **symon1980 said:**
> Omg! This Bug STILL hasn't been fixed!
i've had the same problem for about 6 months...... I even get the same error in other distro's using brasero such as Mandriva......... so its not Ubuntu related... its just that Brasero is a piece of buggy ****!

my solution... Use k3b! :)

I used to get this bug all the time. I have a computer repair company, so I burn a lot of recovery / install ISOs that I leave for customers at the end of service jobs, and I also keep fresh copies of the latest Ubuntu, OpenSuSE, and Arch on me as well. I find that "feature" useless and it ought to just be removed since it has never worked right. Or fixed.

---

### Post by beerdoctor on 2009-11-28
The strange thing about Brasero, it did work sometimes in 9.10, but then it began to just stop, making audio copies impossible, a data CD is problematic at best.I have tried removal using synaptic manager then reinstall... there is definitely a bug here that needs to be fixed.

---

### Post by Redsunz on 2009-12-28
Its working fine now in Ubuntu 9.10 (karmic)

---

### Post by madmax75 on 2009-12-29
I now use Xfburn instead of Brasero. It's so much quicker, simple to use and does the job.

---

### Post by mutex023 on 2009-12-29
> **symon1980 said:**
> .... its just that Brasero is a piece of buggy ****!

my solution... Use k3b! :)

Totally agree dude. What beats me is, why the hell did they make brasero the default burning app. They replaced the 'right-click->burn' app in Intrepid with brasero in Karmic. The earlier CD/DVD creator thing worked fine. I'm yet to do a successful burn with Brasero . When something isnt broken dont fix it !

---

### Post by greybeard62 on 2010-01-24
Ubuntu user for two years now.  I can say with no doubt and great certainty that I have never been able to burn a dvd in Ubuntu, single layer, double layer - nothing.  Brasero always gives an error.  Now, using the same external drive, Sony, DL capable, I simply boot into Vista (I hate this, bummer, slow) and burn my .iso and dvds.  It is painful but alas, it works.  The only reason I keep the dual boot is burning dvds and GPS stuff in Vista. I hope there will someday be a dvd burning software which actually works in Ubuntu.  DVD prices are low but it frosts me every time I make a coaster in Ubuntu, just gave up.  The only solution to man today is boot into Windows and use that to burn your dvds.  Hopefully someone will give me a clue if you can do it in Ubuntu.  There is one program which works for me, different app, DVDStyler.  It burns the DVD every time perfectly in Ubuntu.  Now why can't I burn a data file in Brasero?

---

### Post by mutex023 on 2010-01-24
Forget brasero, Use K3B - always worked for me.
Install it from synaptic pkg manager

---

### Post by greybeard62 on 2010-01-24
Thanks, I was doubtful but went ahead and installed K3b.  It works just as you said. Forgot to mention, three laptops, various ages all Ubuntu 9.10, only one dual boot - X61 Thinkpad.  Now only one thing is keeping that dual boot alive and I might give it up. The more I use Ubuntu the more I like the open community and all the knowledgeable people willing to take a few minute to answer.

---

### Post by Das Goat on 2010-01-24
This is related but different.

I have two matching laptops. Both burned ISO images to DVD with no problem. Then about a week ago after some updates, neither one will burn the ISO. I don't get any error messages, the drive light flashes and Brasero says the disk is done burning, but when you put it in anything, the disk is still blank, like Brasero is stuck in simulation mode. I thought K9 copy might be making bad ISO files, but when I fired up an Ubunutu box that had been off for a few weeks, the ISO files burned just fine. Stupid me left that box on and now it has the same symtoms, but I don't remember updating it.

After reading about K3B I installed that and tried burning. It just makes coasters. It is like what ever the update was, it is messing with the drives ability to write. Reading here I tried loading Xfburn. It does exactly the same thing as K3B, it says it is burning and ejects the disk. when you put the disk back in the PC it takes a while, but the DVD finally loads. However, when you put it in a DVD player, it never loads.

Tonight I told Ubuntu to manually update on one laptop. After it did, I tried to burn. I still get a blank disk when it is done, but now I get an error saying that the system can not mount a blank disk, so something changed.

It is definately damn odd behavior and not the first time I had to do a new clean install to make Brasero start working right again. I really hate Brasero. The simple right click burn worked just fine. I really want to have a long talk with who ever thought up the idea of making Brasero the default ISO burner and remind them that 1) if it is not broken, don't fix it and 2) Linux - it just works (remember that mantra)

UPDATE: I completely removed Brasero, libbrasero, and RythemBox (dependancy) and tried again with K3B. It still made coasters.

---

### Post by Das Goat on 2010-01-30
If you read my posts you know that I had some very bizarre problems. I found the answer, but the behavior was so bizarre I think I should tell you so that it my help someone else.

Wrap up configurations:

Desktop - Just regular updates
Laptop #2 - Just regular updates
Laptop #1 - Match to Laptop #2, but scrubbed and a fresh install with updates.

Ok, so I tried again after updates to just ISO files. 

Desktop - I burn ISO file #1. When it is done, I eject the disk, put it back in and Ubuntu says it is blank.

Laptop #1 - I took the same disk an put it in. Ubuntu said it was blank, so I burnt ISO file #2. When it was done, I ejected the disk, put it back in, and Ubuntu said it was ISO file #1 !  It even played the disk. Bizarre!

Laptop #2 - I took the disk to this laptop and Ubuntu said it was blank! Put it in the DVD player and it too said it was blank. I took it back to Laptop #1 and it said it was blank not too!

I was so confused. I had been kicking this problem around for two weeks. In desperation, I stopped at Walgreens and bought a $2 pack of cheep DVD blanks. Everyone of them burned correctly, one on each PC.

So you see what was wrong. I got a 100 pack of HP brand blanks, and as I worked through the first 30 of them, everything was fine, but it turns out the whole rest of the stack were defective. I bought a new 50 pack of Philips disks today and tried them out. All worked fine. There is still a touch of odd behavior as the messages from all PCs do not match, but they all work now.

Tip: When in doubt, try a different batch of media. (I actually tried this early on, but with only one disk to try, I dismissed this as the possible cause.)

i hope this helps someone.:popcorn:

---

### Post by kennedyjch on 2011-08-30
Had a problem (Ubuntu 10.10) that burning one set of folders (data disc) was OK; but trying to burn multiple folders (and large amounts of data (>300MB)) caused error 24 and could not read the files written to the disc. Was on the verge to purchase a new CD burner when...

... I followed instructions above and removed the three brasero packages and then reinstalled - works just fine... Thanks for the great tip!!!

---

### Post by serpentracer on 2011-09-08
I'm new to linux as in, I'm not real savvy with using or understanding everything about it just yet.  but I've been trying my hand at it since the first time I heard about ubuntu.  I think it was around version 7 or something like that.
anyway, I've tried it on and off with little to get excited about.  after using it for a few weeks I just gave up because 1/2 of the software for it never works.
one being any kind of burning software.  no it's not a computer issue.  windows burns stuff all the time.
and it's not the only computer I've tried to use ubuntu on.

I sit right now with a decent computer and ubuntu 11 and it still doesn't burn anything.  it's always some kind of error or it just locks up and I have to use xkill to kill the process.

I still don't see why everyone thinks linux is superior to anything.  maybe it's better than windows 95? ...no, windows 95 had less glitches than any linux distro I've tied. 

sorry to rain on your linux parade...but it's still nowhere close to being a windows replacement.

---

