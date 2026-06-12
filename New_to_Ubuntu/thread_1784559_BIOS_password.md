---
title: "BIOS password"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by wep940 on 2011-06-17
I suspect this would be considered cracking - heck I'd even think so if I saw the post.  Perhaps instead of discussing this in the forum someone could PM me and maybe include links.

The situation:  I just purchased 2 old Dell inspiron laptops online.  The lady said she bought them at a bank sale and didn't know a thing about them.  They both even still have the asset tags from the bank but it appears the bank is either out of business or otherwise doesn't have a web presence.  

1 of them, an inspiron 8200, has an administrator password set in the BIOS, so I can't do things like change the boot order, change the default date and time, etc., etc., etc..  I found all kinds of sites that claim they have the way to do it using Windows, but they are either paid services or sites that it appears Dell probably (rightfully so) had shut down.

So, my question is, are there any tools that are Linux and floppy based (right now it doesn't recognize the CD drive - apparently because I have no hard disk - waiting on Dell adapters) that would allow me to do this?

Thanks for the time, and I perfectly understand if this is considered a hacking question and the thread is closed - I'm just reaching for a rope ;)

---

### Post by ngubk on 2011-06-17
I had a BIOS password in my PC before. I just opened the case, remove the bios battery and put it in again and the pass is gone. I wonder you can do that in a laptop. But i think you can take the lap to the shop and they can help you.

---

### Post by mastablasta on 2011-06-17
> **wep940 said:**
>  
So, my question is, are there any tools that are Linux and floppy based (right now it doesn't recognize the CD drive - apparently because I have no hard disk - waiting on Dell adapters) that would allow me to do this?

 
search for Plop boot manager. It can run from floppy and you basically boot from floppy and then choose in a simple menu from which device you want to boot the system from. also handy if computer BIOS can't boot from USB.

---

### Post by mastablasta on 2011-06-17
> **ngubk said:**
> I had a BIOS password in my PC before. I just opened the case, remove the bios battery and put it in again and the pass is gone. I wonder you can do that in a laptop. But i think you can take the lap to the shop and they can help you.
 
regarding this - you should search how to flash BIOS on your notebook (try to find the manual for it). Sometimes it is really like this - to take out the battery and then wait a bit and then put it back in. sometimes though you need to move a jumper on motherboard to flash it/reset it.

---

### Post by crispy_420 on 2011-06-17
Remove battery and power source. Hold down power button for a minute and pray it works. There maybe in internal battery but unlikely or another chip that acts as a security module to store this type of info (ThinkPads use this).

From what I have read you can't get past this on your own and Dell won't help either.

---

### Post by User3k on 2011-06-17
Not sure if you will find anything useful here but this link might help.

[http://www.technibble.com/how-to-bypass-or-remove-a-bios-password/](http://www.technibble.com/how-to-bypass-or-remove-a-bios-password/)

Also this might help to?

[http://www.ehow.com/how_5513345_cmos-dell-inspiron.html](http://www.ehow.com/how_5513345_cmos-dell-inspiron.html)

---

### Post by ayenack on 2011-06-17
You'll need to take the case of the laptop and take the battery out it's a little lithium battery about the size of a penny.

Once done put the battery back and reboot.

That should work.

---

### Post by wep940 on 2011-06-17
> **User3k said:**
> Not sure if you will find anything useful here but this link might help.

[http://www.technibble.com/how-to-bypass-or-remove-a-bios-password/](http://www.technibble.com/how-to-bypass-or-remove-a-bios-password/)

Also this might help to?

[http://www.ehow.com/how_5513345_cmos-dell-inspiron.html](http://www.ehow.com/how_5513345_cmos-dell-inspiron.html)

I'll give those a look-see - thanks!


ayenack:  Most laptops will not reset the BIOS passwords by just removing batteries - it's more of an anti-theft thing.  They usually require either a program or changing jumpers on the motherboard.  They are normally stored in either NVRM on the BIOS chip or in a seperate chip.

Some give instructions on using DOS debug to change values in the BIOS forcing it reboot and reinitialize such that the BIOS passwords are removed.  I'm a little leary of this because I don't see how one can guarantee the address of the data to be changed given different versions of the BIOS.

I have downloaded a couple of tools only to find they require Windows and a running hard disk to run.  Sort of defeats the purpose for me - no hard disk = can't run the programs.


While I'm quite comfortable taking laptops apart to fix things, I was hoping I could be lazy here and find a "short-cut".  

Thanks for the replies, and I'll keep looking!

---

### Post by jmore9 on 2011-06-17
Find the model of your machine and then go to the manufacturs web site and download the manual/s for your machine.  In one of them (  if there is more than one ) there will be a routine for you to follow to reset the bios settings .  This also deletes the bios passwords.  You also have to go back and put your settings back that you had before you reset the bios.

---

### Post by wep940 on 2011-06-17
I already have the manual and the service manual.  Resetting the BIOS doesn't do anything to the passwords.  

Where I am at it that I either have to pay for Dell support, with the most likely result being they won't give me a master password, or I need a program to reset the service tag.  Resetting that tag will make the BIOS administrator password be reset on a reboot.  I just can't find those programs that will run stand-alone in DOS mode.  It seems Dell has requested the sites that had the software to be closed, as it appears that it is probably the internal Dell service CD.

Thanks for the reply!

---

### Post by wep940 on 2011-06-18
I was able to change ownership on the Dell site to me.  Does anyone know what they charge on their 888 support number?

---

### Post by crispy_420 on 2011-06-18
No idea but you can always back out of the call right since 888 is toll free.

---

### Post by wep940 on 2011-06-19
Forwarded an alternate solution - worked great.

Thanks for all the input!

---

### Post by crispy_420 on 2011-06-19
You gonna share with the group?

---

### Post by wep940 on 2011-06-19
This is one of those times when it would be best not to.  Kinda of a don't ask don't tell thing, if you know what I mean.  If someone wants to PM me I could explain more.

---

### Post by fooman on 2011-06-19
just as a reference....

i had a client of mine whom i had fixed a couple of computers for in the past,  call me to say that he had been given a hp netbook that he could not access because of a bios password problem.  he said the previous owner had the problem and did not know how it happened,  neither he nor anyone else had set such a pssword and of course,  no one knew what it was.  picked it up from him and brought it home.

tried all the easy, default passwords i could think of and none worked.  tried a bunch of other tricks i saw online,  also to no avail.  finally opened the removable panels on the bottom that house the ram, hard drive and such,  and i could see the small coin battery just tucked under a corner near the hard drive.  grabbed my needle-nose pliers and could just get a hold of enough of it to pull it out.  it was attached to a wire that plugged into the board....unplugged it and waited a few minutes before plugging it back in and starting it up.

no go,  same situation where it would start to boot,  then prompt for a password.  tried it again and let it sit for about a half hour....still no go.

contacted hp and was told i had no choice but to send it in to them for repair.  hung up,  called my client, told him he was screwed and that i would return it to him the next day.

later that night i decided to give that battery thing one more try and this time....*let it sit overnight.*

well to my delight,  the next morning i got up,  plugged the battery back in,  started it up and low and behold.....it booted straight up.  has been working fine ever since.

---

