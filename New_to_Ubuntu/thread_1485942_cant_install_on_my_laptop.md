---
title: "cant install on my laptop"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by mohhas on 2010-05-17
I became interested linux 10. 04 and it is ok on desktop but i cant install on laptop 
after booting i select install linux but many lines of dos screen  that last for long time . i made several trails  and the same problem
[SIZE=2][COLOR=Black]my laptop is toshiba with vista in drive c( active) & windows 7 on drive d 
any help plz[/COLOR][/SIZE]

---

### Post by mbzn on 2010-05-17
Md5 Your iso file and see to it that the cd is written at low speed.

[www.pc-tools.net/win32/md5sums/](www.pc-tools.net/win32/md5sums/)

---

### Post by mohhas on 2010-05-17
> **mbzn said:**
> Md5 Your iso file and see to it that the cd is written at low speed.

[www.pc-tools.net/win32/md5sums/](www.pc-tools.net/win32/md5sums/)

thanks for reply but i use this cd to install on my desktop
any more help

---

### Post by Mark Phelps on 2010-05-17
If you can boot using the LiveCD, open a terminal and post the results of "sudo fdisk -l" (that's a lowercase L, not a one).

It could be that your drives are all full and there is no space or ability to create new partitions.

---

### Post by mohhas on 2010-05-17
plz im waiting !!!!!!!!!!!

---

### Post by mohhas on 2010-05-17
> **Mark Phelps said:**
> If you can boot using the LiveCD, open a terminal and post the results of "sudo fdisk -l" (that's a lowercase L, not a one).

It could be that your drives are all full and there is no space or ability to create new partitions.

no  there is large free space more than 160 gb

---

### Post by mörgæs on 2010-05-17
> **mohhas said:**
> plz im waiting !!!!!!!!!!!

It seems like your !-key is stuck. Better get that fixed.

---

### Post by mohhas on 2010-05-18
> **mörgæs said:**
> It seems like your !-key is stuck. Better get that fixed.


thanks..
any help

---

### Post by MartyBuntu on 2010-05-18
I could never get my Toshiba to play nice with Ubuntu.

That's why I sold it. Sorry if that's not what you wanted to hear.

---

### Post by mohhas on 2010-05-18
> **MartyBuntu said:**
> I could never get my Toshiba to play nice with Ubuntu.

That's why I sold it. Sorry if that's not what you wanted to hear.


oh no but where is the problem ?? why toshiba ?

---

### Post by Peter09 on 2010-05-18
Try booting through to the live CD environment and select install from there. I believe there may be a bug around this.

---

### Post by 3rdalbum on 2010-05-18
When you first start the CD, a screen appears with the Ubuntu logo and a little grey strip down the bottom with a picture of a man in a circle and a keyboard.

Hit any key on the keyboard while this screen is up, and you'll get the menu of whether you want to install Ubuntu, run it live, check the CD etc.

Hit F6 and you'll be able to choose some options. These include:

acpi=off
noapic
nolapic

Put an X next to these top three, then hit Escape to exit that submenu and press Enter to boot.

Give this a try; having these three options turned on is kind of like a failsafe mode.

---

### Post by flyfishingphil on 2010-05-18
> **mohhas said:**
> I became interested linux 10. 04 and it is ok on desktop but i cant install on laptop 
after booting i select install linux but many lines of dos screen  that last for long time . i made several trails  and the same problem
[COLOR="DarkRed"][SIZE="4"]my laptop is toshiba with vista in drive c( active) & windows 7 on drive d 
any help plz[/SIZE][/COLOR]
I have a Toshiba L305, started with 9.10 and upgraded to 10.04 and everything worked great. Didn't see any of the problems listed here with anything.

Did notice that you already have Vista and 7 via drives c & d. Mine is set to just one drive and Vista. (Plan to get rid of that as soon as I can get VirtualBox, and installing into it, figured out.)

Did mine by booting, clicked on the run/install/ opened it up and then did install. No problems there. My thought would be to check your security settings and see if you are blocking it there. (I turned off Firewall and Avast! before trying to install.)

---

### Post by mohhas on 2010-05-18
> **Peter09 said:**
> Try booting through to the live CD environment and select install from there. I believe there may be a bug around this.

thanks 
but  the same problem

---

### Post by mohhas on 2010-05-18
> **3rdalbum said:**
> When you first start the CD, a screen appears with the Ubuntu logo and a little grey strip down the bottom with a picture of a man in a circle and a keyboard.

Hit any key on the keyboard while this screen is up, and you'll get the menu of whether you want to install Ubuntu, run it live, check the CD etc.

Hit F6 and you'll be able to choose some options. These include:

acpi=off
noapic
nolapic

Put an X next to these top three, then hit Escape to exit that submenu and press Enter to boot.

Give this a try; having these three options turned on is kind of like a failsafe mode.

thanks 
i tried  but still same problem

---

### Post by Peter09 on 2010-05-18
Try downloading the 'alternate' iso and using that. It gives a text base install so less resources are used during installation, especially graphics drivers, which are always a bit of a problem.

---

### Post by mohhas on 2010-05-18
thanks to every one try to help me
these lines appear after booting and start installation = my give idea about the problem 

""stdin: error 0""

""151-39897  bug :soft lockup - cpu # 0 stuck for 61 s ! ( polymouthed: 1091)""

  and many other lines with same message
i hope this help someone

---

### Post by Linux_junkie on 2010-05-18
It could be that your laptops hardware might not be compatible with Ubuntu.  Not every computer is compatible with Linux in general which is why you should always run the LiveCD first and if that works then you can install it.

---

### Post by mohhas on 2010-05-18
> **Linux_junkie said:**
> It could be that your laptops hardware might not be compatible with Ubuntu.  Not every computer is compatible with Linux in general which is why you should always run the LiveCD first and if that works then you can install it.
  may be 
but it mean[SIZE=2][COLOR=Black] failure of linux[/COLOR][/SIZE]

---

### Post by Peter09 on 2010-05-18
See
[http://swinky-linuxblog.blogspot.com/2009/05/ubuntu-904-on-toshiba-satellite-l305.html](http://swinky-linuxblog.blogspot.com/2009/05/ubuntu-904-on-toshiba-satellite-l305.html)

---

### Post by mohhas on 2010-05-18
> **Peter09 said:**
> See
[http://swinky-linuxblog.blogspot.com/2009/05/ubuntu-904-on-toshiba-satellite-l305.html](http://swinky-linuxblog.blogspot.com/2009/05/ubuntu-904-on-toshiba-satellite-l305.html)
  thanks not my problem 
thanks again

---

### Post by Peter09 on 2010-05-18
May be not but obviously these people did not have a problem in the actual install. Have you tried 9.04?

---

### Post by mohhas on 2010-05-18
> **Peter09 said:**
> May be not but obviously these people did not have a problem in the actual install. Have you tried 9.04?

no

---

### Post by eltonw on 2010-05-18
> **mohhas said:**
> I became interested linux 10. 04 and it is ok on desktop but i cant install on laptop 
after booting i select install linux but many lines of dos screen  that last for long time . i made several trails  and the same problem
[SIZE=2][COLOR=Black]my laptop is toshiba with vista in drive c( active) & windows 7 on drive d 
any help plz[/COLOR][/SIZE]
This sounds like a problem with your video card not supported, and needing video drivers. SEARCH the forums here for the 'nomodeset' command.


HTH...

---

### Post by MartyBuntu on 2010-05-18
> **mohhas said:**
> oh no but where is the problem ?? why toshiba ?

Power management issues...overheating...awful battery life...

For the short time I had the Toshiba laptop, the only distro that I could run successfully was PCLINUXOS. Now, I go way back with PCLINUX, but I've been a dedicated Ubuntu/Kubuntu user for four years and use it exclusively on all my machines. Even PCLINUX threw up the odd quirk with battery life.

Looking into the matter on Toshiba's help forums, the general consensus from Toshiba was:

"We didn't sell you a laptop with Linux. Buh-Bye, now."

Goodbye Toshiba. Never touching your stuff again.

---

### Post by mohhas on 2010-05-21
where are men? no hope

---

