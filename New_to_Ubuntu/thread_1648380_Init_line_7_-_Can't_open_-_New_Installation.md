---
title: "Init line 7 - Can't open - New Installation"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by JiNaMoN on 2010-12-18
Hey all, this is my first time posting and just wanted to let you know that my technological skills are not as good as yours lol. I looked at the solutions that you have up for my problem and I didn't understand how to solve it :( I'm a college student trying to pick up Ubuntu because I want to learn how to use it. I installed the 32bit version onto a USB and I'm running WinXP on my desktop. I want to boot it from my desktop, I went into the BIOS, changed to have it boot from the USB. So far so good. Then it came up to the load screen for Ubuntu, I choose to boot it from the USB, and then when it came to the other loading screen (The screen with Ubuntu's name and the 5 or 6 dots under it) I keep getting errors. After restarting my computer and hoping that the problem will go away on its own, I went back into my BIOS and started up WinXP with no problem. Please let me know what I can do to fix this, I have Ubuntu 10.10 Desktop version and I'm sorry but if its super technical I might need some extra help. Have a wonderful day all, thank you for this interesting OS I am really excited to learn how to use it.

---

### Post by drs305 on 2010-12-18
JiNaMoN,
[I]
Edit: After reading the next reply I have moved this user's post to a new thread. This is a new Wubi installation.[/I]

Welcome to Ubuntu and the Ubuntu forums. Your problem isn't with the Grub bootloader but something after Grub transfers control to the kernel. The Ubuntu screen with the dots means that Ubuntu is controlling things but is having a problem getting to the Desktop. (The next time it gets to that screen, make sure there isn't a message at the bottom about pressing S to skip mounting a partition. If you see that, press S and perhaps it will boot).

Although it doesn't sound like a driver problem, you might also press "e" at the Grub menu (if you don't see it, hold down the SHIFT key during boot) and add **nomodeset** to the end of the "linux" line (which probably currently ends with "quiet splash").  CTRL-x to boot after typing it. I don't think your problem is the standard nvidia driver problem, but if it is this should let it boot. Let us know if it does or doesn't.

You can also boot the LiveCD, then download and run the boot info script from the following site. As I mentioned, I don't believe you have a grub problem but we can get a bit more information about your system. Just post the contents of RESULTS.txt, which the script generates:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by JiNaMoN on 2010-12-18
Hey man, thanks for the quick response! I tried running Ubuntu again, and I added the nodemodeset line where you told me to, however, my line ended in just "splash" and not "quiet splash." - I don't know if that makes a difference.

I'm using my laptop now to type up the error codes im seeing on the computer. It begins like this..

Begin: Loading essential drivers...done
Begin: Running /scripts/init-premount ...done.
Begin: Mounting roof file system ... Begin: Running /scripts/casper-premount done.
[55.000314]end_request: I/O error, dev fd0, sector 0
[55.000584]Buffer I/O error on device fd0, logical block 0


And the errors just continue to repeat themselves. 


Edit** They just ended in the following line:

stdin: I/O error
/init: line 7: can't open /dev/sdc: No medium found
/init: line 7: can't open /dev/sdc: No medium found
/init: line 7: can't open /dev/sdc: No medium found
/init: line 7: can't open /dev/sdc: No medium found
/init: line 7: can't open /dev/sdc: No medium found
Warning: Unable to find the persistent medium

And then the error messages just started coming back again

On a last note...I would boot the liveCD if I could but this computer's DVD drive does not work and have had the time/extra $$ to replace it.


The one thing that was different this time was that at the load screen with the dots, it said Ubuntu 10.10 instead of Ubuntu the first time, again, don't know if that matters just trying to give you as much info as I can.

Thanks for all the help.

---

### Post by JiNaMoN on 2010-12-18
Update: I have tried reinstalling the files on the USB as well as using noapic and nolapic in the linux line and it has been to no avail. I also attempted to google the problem and look up solutions but it has not lead to anything promising. If anyone has experienced anything similar, please let me know because I am completely in the dark :(

---

### Post by electric_tom on 2010-12-19
I am actually having a very similar problem. I am trying to install Ubuntu remix on a Toshiba NB305 net-book, despite all the problems I have read about other peoples problems with it installed. 
I have made the usb stick, and as it begins to boot, I get the error 
/init: line 7: can't open /dev/sdb: no medium found, 

now it will just sit there, unless I hit a  random key, then it trys again, and again, after about 3 times it gives me this
warning: Impossible to include the casper snapshot 

It does this loop about 4 - 5 times, and then continues with the boot up. 

now after about 15 minutes, it loads into the live version, and I can play with that, gets online, etc. If i choose to install it, it hangs after about 2 hours of installing. I have to remove power cord, and release battery to restart.  

do these errors i get at the beginning have anything to do with the install. I'm thinking either the USB drive, or the USB stick itself is having problems, But i'm no genius when it ***es to linux. 

Thanks for any help. 

Tom

---

### Post by electric_tom on 2010-12-20
Yeah, After about 3 days, and maybe 15 attempts, using different usb drives, different utility's for creating the boot device, i gave up, and installed Fedora instead, I'm sure I will come back to Ubuntu for this net book when i have more time to play with it.

---

### Post by JiNaMoN on 2010-12-20
Hey any chance anyone could help us out? I'm a computer science major @ Rutgers University and would love to start using Ubuntu! Please let me know what I need to do...thanks all!

---

### Post by fmmarzoa on 2011-01-14
Just one to say that today I've buy a new box for my wife and I'm experimenting exactly the same exasperating problems right now.

---

### Post by fmmarzoa on 2011-01-14
Just one to say that today I've buy a new box for my wife and I'm experimenting exactly the same exasperating problems right now.

---

### Post by e_carbon on 2011-03-06
Hello,

I'm pretty new to Linux myself, and trying to do a USB install via any method - USB Live creator / Wubi / UNetbootin, USBUniversal isntaller  - nothing works, they all produce the same result when trying to boot via the USB drive:

/init: can't open loop over and over.  If it does come live, (who knows how long later) it is very slow and unresponsive, freezes up.

It seems a liittle strange to me that there are this many users in the Ubuntu Community and this thread's been here since the 18th of last Dec. without anyone replying to it other than with the same problem.  

Does anyone know how to fix this? :confused:

---

### Post by xxnishantxx on 2011-06-27
i'm no computer expert but...
I got the error message with 
.../dev/sdb: no medium found

so i booted into an existing installation and found /dev/sdb was my laptops card reader.
now i tried disabling it in the BIOS but sadly it gives no option to do that, and i'm not confident enough with hardware to open the machine up and disconnect it manually.

if anybody has this problem, and you can identify the device as a card reader, and you manage to disconnect it somehow, it would be really helpful if you could post your results here...

of course I could be completely wrong and this might all be bull (in that case: sorry :))

---

