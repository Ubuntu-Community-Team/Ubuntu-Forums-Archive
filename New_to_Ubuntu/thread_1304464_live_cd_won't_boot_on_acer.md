---
title: "live cd won't boot on acer"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by john1066 on 2009-10-29
Well I've just started to tryout Ubuntu. Followed the directions copied the download, checked it out, made a live cd, and restarted with the cd in the dvd reader. Guess what - still loads vista every time?? I'm running an acer aspire 6930g and there is some acer propriety software which starts up before vista starts booting (hate it when you get all this stuff you never asked for - some of these companies are so arrogant!). Anybody know how I can get the Ubuntu cd to fly?

Thanks,
John

---

### Post by OffAxis on 2009-10-29
go into the BIOS and set the system to boot from 'DVD' drive first.
Usually you have to push the 'Delete' key when the system is first starting to raise the BIOS menu.

---

### Post by phillw on 2009-10-29
When you boot your acer, press the F2 button, go into boot options and set it to boot from the CD before the hard-drive.

Save, and it'll boot off the CD

Regards,
Phill.

---

### Post by CharlesA on 2009-10-29
Those should work, but if you don't want it to boot from the cd first, you can boot from the cd, with the "boot menu" I believe it's F12.

---

### Post by samh785 on 2009-10-29
> **phillw said:**
> When you boot your acer, press the F2 button, go into boot options and set it to boot from the CD before the hard-drive.

Save, and it'll boot off the CD

Regards,
Phill.
Do what Phil here says, and you'll be installing it in no time. :)

---

### Post by john1066 on 2009-10-29
Well that was not a bundle of fun.

Did what phillw suggested - changed the boot preference to cd.

Laptop goes to cd starts loading ubuntu - get a nice ubuntu logo while its getting the stuff from cd... but then it drops down into command line mode and I get something like

Starting netweork comms manager         (OK)
starting other stuff                                 (ok)
checking battery state....
/dev/sda
setting advanced power mgmt level to oxfe
/dev/sdb
setting advanced power mgmt level to oxfe      (ok)

and then the laptop goes into limbo. Nothing happens and I'm left looking at this command line screen.

Any ideas

---

### Post by phillw on 2009-10-29
1st thing to check is the md5checksum

Don't worry, the steps are here ....

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

My guess would be that you didn't burn the disk at 4X speed (that's a gr8 one for causing funnies)
Other causes can be that the drive needs a cd-cleaner using on it. Data disks have much less tollerence of errors than, say, music / videos have.

I'll keep an eye on this thread for you.

Phill.

---

### Post by CharlesA on 2009-10-29
verify the MD5SUM, then reburn the disc at a lower speed.

---

### Post by Wim Sturkenboom on 2009-10-29
Which version of Ubuntu? 9.04 or 9.10 or ...

---

### Post by phillw on 2009-10-29
> **Wim Sturkenboom said:**
> Which version of Ubuntu? 9.04 or 9.10 or ...


he he - good question, I haven't asked the OP that, yet !!! :D

Phill.

---

### Post by CharlesA on 2009-10-29
> **Wim Sturkenboom said:**
> Which version of Ubuntu? 9.04 or 9.10 or ...

Good question. Nice sig too btw. ;)

---

### Post by john1066 on 2009-10-29
Reburned at 4X as suggested - and it now boots fine. Managed to get my printer (epson c84) going ok. Haven't yet managed to get a network connection or firefox to work. Does it detect automatically or do I have to configure something for that? Once thta's going I'll be well on my way to becoming independant of Microsoft - Vista was just the last straw!

Thanks for your help.

John

---

### Post by CharlesA on 2009-10-29
It should configure the network automatically. Are you using a wired or wireless connection?

---

### Post by philinux on 2009-10-29
Plug the lappy into the router to get a wired connection. Then do an update.

System>admin>update manager

Then wireless can be sorted out. you probalby installed without setting up a wireless connection.

---

### Post by john1066 on 2009-10-29
Connection is wired. Vista also finds the neighbour's wireless stuff. Haven't seen them turn up in Ubuntu yet.

John

---

### Post by CharlesA on 2009-10-29
Post the output of ifconfig.

That'll let us know if it sees the network cards.

---

### Post by john1066 on 2009-10-29
OK wired network up and running - I suspect the provider was having troubles - Vista couldn't pick up the connection either for a while. Any easy way of duplicating my firefox bookmarks from vista into ubuntu?

I seem to have a viable system now - I'll start moving to a persistent image in the next few days and if all goes well move to a dual boot thereafter.

Is 9.10 now an official release or is it still in beta?

Thanks for all your help.

John

:D

---

### Post by CharlesA on 2009-10-29
It's an official release as of today. :-)

Not sure how to move the bookmarks from FF in Vista to Ubuntu outside of just exporting the bookmarks as HTML and import them into FF in Ubuntu.

---

### Post by redbook4574 on 2009-10-29
> **john1066 said:**
> ok wired network up and running - i suspect the provider was having troubles - vista couldn't pick up the connection either for a while. Any easy way of duplicating my firefox bookmarks from vista into ubuntu?

I seem to have a viable system now - i'll start moving to a persistent image in the next few days and if all goes well move to a dual boot thereafter.

Is 9.10 now an official release or is it still in beta?

Thanks for all your help.

John

:d

easy way to copy bookmarks - setup a free xmarks account in tools, this will save all your bookmarks to a secure site on the web and restore them to any version of firefox you are running.

---

### Post by phillw on 2009-10-29
> **CharlesA said:**
> It's an official release as of today. :-)

Not sure how to move the bookmarks from FF in Vista to Ubuntu outside of just exporting the bookmarks as HTML and import them into FF in Ubuntu.


It's dead easy to transfer FF from MS to ubuntu - it'll also take your passwords for any saved sites :-)

Give me a couple of mins & I'll dig my instructions out for you !!

Phill.

---

### Post by phillw on 2009-10-29
> **CharlesA said:**
> It's an official release as of today. :-)

Not sure how to move the bookmarks from FF in Vista to Ubuntu outside of just exporting the bookmarks as HTML and import them into FF in Ubuntu.


Password Exporter is the add on for FF to take any saved passwords over from FF in MS to FF in ubuntu (I save them to a USB stick)

For your bookmarks ...

Bookmarks --> Organise Bookmarks --> Import / Backup

Same thing with usb stick.

Obviously, you're saving FROM (Backing up from) M$
and loading into / restoring INTO Ubuntu

Both procedures work, rock solid - I lost one password out of some 49 sites when I transferred over.

Until you're ready to make your install persistant, you'll have to load them into 9.10 each time yout use it, but it'll prove it all works :D

Now that you have a running install, to do a nice job of your dual-boot apc have a great set of tutorials. 

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

In my Signature is a link to some resources  (From the Link, Linux --> Resources).

Any problems / questions - PM me on here, or on the site in my links.

Glad we 'got there', I know it can be frustrating when it doesn't work 1st time - It looks worse on the forums, because for the vast majority that don't have any problems - they don't log on to say so !!!

You'll be able now, to help others - and that is how the forums work.

Welcome to the family, 

Regards,

Phill.

---

### Post by CharlesA on 2009-10-29
Awesome! That's a nice add-on! :D

---

### Post by john1066 on 2009-10-30
Now that I've got an up and running live cd (+ working network, printer, scanner), I'm getting really enthusiastic. And the support coming from this forum is just great. I'm thinking my next move would be to make a persistent 9.10 on a usb and then test out video, music, fotos, moving docs/spreadsheets,presentations back and forth from Vista. If all goes well I'll go dual after that. So my main question at the moment is whether UNetbootin makes a persistent usb (versus just a copy of the live CD) - anybody know?

John

Isn't it just the biggest kick to start getting free of Micosoft? Maybe I'll understand someday how they got to dominate the market. 

 :KS
I'm so happy I'm shining!

---

### Post by phillw on 2009-10-30
> **john1066 said:**
> Now that I've got an up and running live cd (+ working network, printer, scanner), I'm getting really enthusiastic. And the support coming from this forum is just great. I'm thinking my next move would be to make a persistent 9.10 on a usb and then test out video, music, fotos, moving docs/spreadsheets,presentations back and forth from Vista. If all goes well I'll go dual after that. So my main question at the moment is whether UNetbootin makes a persistent usb (versus just a copy of the live CD) - anybody know?

John

Isn't it just the biggest kick to start getting free of Micosoft? Maybe I'll understand someday how they got to dominate the market. 

 :KS
I'm so happy I'm shining!


UNetBootin is this way -->  [http://ubuntuforums.org/showthread.php?t=811397](http://ubuntuforums.org/showthread.php?t=811397)

9.10 on usb is this way -->  [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Regards,

Phill.

---

### Post by john1066 on 2009-10-31
Well I've got 9.04 on my usb - works fine - more reliable than the cd copy!. I used UNetbootin. But I'm not yet persistent - loose add-ins etc between boots. Must be something else I need to do?

John

---

### Post by phillw on 2009-10-31
> **john1066 said:**
> Well I've got 9.04 on my usb - works fine - more reliable than the cd copy!. I used UNetbootin. But I'm not yet persistent - loose add-ins etc between boots. Must be something else I need to do?

John

I've never tried ubuntu on a usb stick. I'd be interested for you to write how you get on with it - I'll pop it onto vpolink, if that's okay with you.

You will find ubuntu well behaved ;) 

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1159008](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1159008)  has a discussion on the matter.

Have gr8 fun :)

Phill.

---

### Post by john1066 on 2009-11-02
I've now got a persistent ubuntu 9.04 on my usb. I used [www.pendrivelinux.com](www.pendrivelinux.com). Very easy, no problems. I'll spend a couple of weeks on usb and if all goes well I'll make a dual boot (and maybe never visit Vista again!). 

Cheers,
John

:D

---

### Post by phillw on 2009-11-02
> **john1066 said:**
> I've now got a persistent ubuntu 9.04 on my usb. I used [www.pendrivelinux.com]("http://www.pendrivelinux.com"). Very easy, no problems. I'll spend a couple of weeks on usb and if all goes well I'll make a dual boot (and maybe never visit Vista again!). 

Cheers,
John

:D


Vista ???? ... Crikey, you've just reminded me - I'm still dual boot ;)

I haven't found a way to boot ubuntu with Mac Classic (9.02), so still need need that ability to use the Mac --> Windoze programme, it seems a bit daft to go ahead and try to get wine to run windows, to run Mac Classic !!!

Besides, I've found a really cool person who is into 'photoshop' in a big way to graphic stuff for me - Yes, I could do it in GIMP, but he can do in 15 minutes what would take me 2 days :p   And, yes, he uses a Mac, so I'll let him off :D

Going Dual-Boot is quite painless, all your data on M$ is easy to access via ubuntu, I now use that partition to do back-ups to, and it's still a handy place to hold my music mp3s. Glad to hear you're getting the hang of it.

regards,

Phill.

---

### Post by john1066 on 2009-11-03
On Vista when I plug my headphones in sound gets muted and comes through on the headphones. I also use that socket to output music from my laptop through to my hifi system.Ubuntu 9.04 seems to ignore the fact that I have plugged into the headphone socket - no input to the headphones and/or hifi. And sound comes out via the laptop as if no headphones had been plugged in. 

Something wrong somewhere - any ideas?

John

:(

---

### Post by john1066 on 2009-11-03
So I get a nice document in my mail that needs to be filed in folder "investments" which is a folder within the folder "money" within folder "personal". The ubuntu pop up allows me to browse to "personal" but won't show any folders within this or allow me to go deeper.

Any ideas?

John

---

### Post by phillw on 2009-11-04
> **john1066 said:**
> On Vista when I plug my headphones in sound gets muted and comes through on the headphones. I also use that socket to output music from my laptop through to my hifi system.Ubuntu 9.04 seems to ignore the fact that I have plugged into the headphone socket - no input to the headphones and/or hifi. And sound comes out via the laptop as if no headphones had been plugged in. 

Something wrong somewhere - any ideas?

John

:(


Try this thread ..  [http://ubuntuforums.org/showthread.php?p=8238980](http://ubuntuforums.org/showthread.php?p=8238980)

The other nice thing about ubuntu -- someone has usually had the same problem, and posted the solution !!

Hope that gets you sorted.

Phill.

---

### Post by phillw on 2009-11-04
> **john1066 said:**
> So I get a nice document in my mail that needs to be filed in folder "investments" which is a folder within the folder "money" within folder "personal". The ubuntu pop up allows me to browse to "personal" but won't show any folders within this or allow me to go deeper.

Any ideas?

John

Do those folders exist yet? when you browse to personal, you should see the option 'make folder' - make the folder money, go into it, then make the folder 'investments' and go into it. -- You will then be able to save your document within that folder

Regards,

Phill.

---

### Post by john1066 on 2009-11-07
Didn't seem to be getting anywhere on the headphone problem so I upgraded to a persistent 9.10 usb. Works fine now. Got some other stuff that needs sorting out but I'll start a new thread for that since it is  not related to sound.

John

---

