---
title: "Blank screen Rel 10.04 Boot maybe GRUB??"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by ken poy on 2010-11-25
Hi i have the blank screen problem as described below.  i am running rel 10.04 and have gone in several directions with Video drivers and bypasses to allow me to Boot 10.04.
now i am questioning GRUB as outlined below.

Some observations:  
1.  i began my Ubuntu experience a few months ago with rel 9.10 which booted fine.  although i think it did 
     fail on occasion. 
2.  i updated to 10.04 via the update Manager which was a disaster so back to 9.10.
3.  i have Virtualbox so booted the CD ISO and installed 10.04 which booted okay  100%
     this makes sense since the Video Driver is active and doing it's thing.
4.  then i used the CD ISO to install 10.04 and am still using it with the Boot circumventions.
5.  One touted advantage of 10.04 is reduced boot time.
6.  i assume (which is dangerous) that GRUB loads/activates the Drivers prior to passing control to
     Ubuntu Desktop.

my conclusion:
the boot blank screen problem seems to be a timing issued which got  worse with the 10.04 version of GRUB.   i think GRUB is not verifying  the Video Driver is loaded/activated prior to the Splash Screen.

What i need:
Since i am a 74 yr senior i do not need speed.  i am slowly learning Linux and do enjoy the experience.
i need an antique version of GRUB (9.10 or earlier) and how-to install.  i would like to give that a try.

Now i made some assumptions so please let me know if i am right or wrong.

Thanks   ken
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=10161679") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=10161679")

---

### Post by Rubi1200 on 2010-11-25
Hi,
in order to help you troubleshoot this problem we need to know what graphics card you have installed.

If you can boot into Ubuntu, go to Applications > Accessories > Terminal and run this command:

```
lspci | grep VGA
```

Copy/paste the results back here please.

And my hat off to you for wanting to learn Linux!

---

### Post by sikander3786 on 2010-11-25
Would you please like if we try to solve your blank screen problem using Grub2? And if it gets fixed, no need to roll-back Grub.

And I don't think if Grub Legacy would solve the problem. It is a problem with X and Plymouth up-stream, yet I would say that I haven't tried Grub Legacy with newer versions of Ubuntu.

Please provide some more details. Which graphics card is there in your system and did you install any drivers for that?

And moreover, were you ever able to boot 10.04 successfully?

---

### Post by ken poy on 2010-11-26
Follow is my video card info:

ken@ken-laptop:~$ lspci | grep -i vga
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
ken@ken-laptop:~$ 

i have a thread now marked solved in which we determined this VGA uses the open source driver.
the video works fine once at Ubuntu desktop. i understand Ubuntu or something determines the needed driver
and installs it.  i have not touched the driver.  do not know how to.  

i have been able to boot 10.04 successfully but very limited.  i just power on like this am and if it boots okay
which it did not this morning.  so i then use the nomodeset circumvention. it might work 10% of the time.
i would be willing to try GRUB2.  glad to help with a solution.

thanks  ken

---

### Post by sikander3786 on 2010-11-26
What if you put nomodeset permanently to the boot line?

```
gksudo gedit /etc/default/grub
```

Replace "quiet & splash" with "nomodeset" in there. Save, close and exit and then run update-grub.

```
sudo update-grub
```

---

### Post by ken poy on 2010-11-26
hi  i did the GRUB Default update.  thanks   still would like to attempt fix to GRUB or whatever.   ken

---

### Post by sikander3786 on 2010-11-27
> **ken poy said:**
> hi  i did the GRUB Default update.  thanks   still would like to attempt fix to GRUB or whatever.   ken
You need to keep on providing the details ;-)

Did you put "nomodeset" in your /etc/defaut/grub file? What happens now?

---

### Post by ken poy on 2010-11-27
Hello,   yes i did put nomodeset in /etc/default/grub.
the 2/3 times i have booted it worked fine.
[FONT=monospace]the difference is the boot shows lines of text and not the Ubuntu screen.
when the boot is finished i get my graphic ubuntu desktop and proceed as
normal.     thanks   ken 
[/FONT]

---

### Post by ken poy on 2010-11-30
Hello,  i am able to boot my system okay with "nomodeset" so i guess i no longer have a problem.
i think i furnished  all requested information.
one of the individual updates was about trying GRUB2 and Plymouth.  i am willing to help but am not sure where it stands.  
i will leave this thread open a few days and if no updates mark it solved.      
thanks for all your help           ken

---

### Post by ken poy on 2010-12-02
Marking the thread resolved due to lack of interest.

---

### Post by sikander3786 on 2010-12-02
> **ken poy said:**
> Marking the thread resolved due to lack of interest.
Don't mark it unsolved if the issue is not solved yet.

You said this,

> Hello, i am able to boot my system okay with "nomodeset" so i guess i no longer have a problem.

Thats why I thought there is no more problem :-)

If you think there is some, please post that and re-mark your thread as unsolved.

Thanks.

---

