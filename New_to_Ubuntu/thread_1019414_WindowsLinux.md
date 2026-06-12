---
title: "Windows/Linux"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by littlebytecc on 2008-12-23
"How can I switch a notebook, Sahara Image BOOK SWCS, from Linux (NeoShine) to Windows. I have a customer requesting this, but, there is a password under the XpressROM that's making it difficult to change the way the notebook boots up. In other words, it does not help if I just pop in the Win CD that came WITH the notebook. Also, there is NO Linux CD with FDisk on it, as per the recommendations I received via Google. "

I believe that I can reset the BIOS...but how do I do this..?  The system cannot be changed so that it boots up from CD instead of hard drive...

Do you have some advise for me..? It will be MUCH appreciated. It seems I must just be able to get pass the XpressROM supervisor password. 
:confused:
:(

---

### Post by earthpigg on 2008-12-23
> I believe that I can reset the BIOS...but how do I do this..? The system cannot be changed so that it boots up from CD instead of hard drive...

you have to open it up, find the bios battery (it looks like a watch battery), and take it out.... count to 1, put it back.

---

### Post by earthpigg on 2008-12-23
o, and be careful you dont break anything in the process ;)

alternatively, you can pay some computer tech dude $100 to do it for you.

---

### Post by littlebytecc on 2008-12-23
> **earthpigg said:**
> o, and be careful you dont break anything in the process ;)

alternatively, you can pay some computer tech dude $100 to do it for you.

hahahh..yea..i just encountered some difficulties with the screws..!!!!  do they friggin clue the stuff in...i wonder..!!!!  thanx for the advice..im sure its going to work, will post as soon as..!!

---

### Post by kestrel1 on 2008-12-23
normally leaving a CMOS battery out for 30 seconds should reset the BIOS.
You may find though that there is an easier way to boot from the CD. When the machine first boots you may see what F key you need to press to get a boot menu. Not sure if this machine has that though.
Often this is F12 or F8. Some notebooks use CTRL + C to boot directly to the CD. Have a look at the initial boot up screen before it starts booting into Linux.

---

### Post by littlebytecc on 2008-12-23
> **kestrel1 said:**
> normally leaving a CMOS battery out for 30 seconds should reset the BIOS.
You may find though that there is an easier way to boot from the CD. When the machine first boots you may see what F key you need to press to get a boot menu. Not sure if this machine has that though.
Often this is F12 or F8. Some notebooks use CTRL + C to boot directly to the CD. Have a look at the initial boot up screen before it starts booting into Linux.

i tried to get to the CMOS battery, but cannot find it - tried unscrewing the laptop base, but it wont open and i am afraid of breaking it.  i then tried the F12, F8 and the CTRL + C, it wont work...

i read elsewhere that i shouldnt try to rmeove the cmos battery, that i may not be able to boot at all, after that...  grrrrr....this thing is making me fume..!!! :mad:  ](*,)

thanx for all help - it was and is really much appreciated..
:P

---

### Post by theozzlives on 2008-12-23
See if you can find a jumper to erase the CMOS, and removing the battery won't hurt it. This is why I don't work on the internals of laptops.

---

### Post by Captain_tux on 2008-12-23
I can see asking for Windows to Linux advice here, clearly... *but Linux to Windows*?

---

### Post by littlebytecc on 2008-12-23
> **Captain_tux said:**
> I can see asking for Windows to Linux advice here, clearly... *but Linux to Windows*?

hi there...it was just a topic ie win/lin - but it is meant to be linux to windows :oops:

---

### Post by Captain_tux on 2008-12-23
Ahhh, I see... you've been seduced by the Dark Side of the Force ;)

---

### Post by EV500B on 2008-12-23
You can also try those tiny, little programs that allow erasing(resetting) the bios' configuration from within windows. 
It also depends on what version of windows you are using.
(I don't work on Windows Vista but I guess that it will not allow running that type of application but try anyway)

---

### Post by littlebytecc on 2008-12-23
> **Captain_tux said:**
> Ahhh, I see... you've been seduced by the Dark Side of the Force ;)

dark side of the force..?  :tongue:
dunno what u mean -  I have a very valid and legal windows copy, it is just too difficult for my client to run linux neoshine which takes forever to boot up on this very annoying little notebook/laptop from Sahara (8 inch)
..okay...i cant get right by any way and means at this stage...am trying a different linux operating system such as PCLinuxOS or Fedora which i have available.  this neoshine system wont autorun this either...do you perhaps know what the file extension is so that i select the correct file to try and start what would have been the 'exe' as in windows..?

---

### Post by littlebytecc on 2008-12-23
> **EV500B said:**
> You can also try those tiny, little programs that allow erasing(resetting) the bios' configuration from within windows. 
It also depends on what version of windows you are using.
(I don't work on Windows Vista but I guess that it will not allow running that type of application but try anyway)
nope - i am running linux neoshine, and would LOVE to install windows, but it wont give me the option because of the bios setup that is protected by a password...
which little program are you talking about..?  i cant seem to find any...
i have even spoken to Sahara but they say that i have to send in the laptop, which will cost me money - i was very upset and said then why do they sell the thing saying that it has dual operating systems, which is then a lie...grrrrrrr  i can go nuts right now...and this before xmas...darn

anyways, thanx for the help, it is much appreciated..!

---

### Post by kestrel1 on 2008-12-23
Did you try any of the other F keys to see if you can get a boot menu?
Manufacturers don't normally set a BIOS password unless it is some kind of custom setup.
If you know the manufacturer of the BIOS you could do a google search for backdoor passwords that sometimes work.
Have a look here at one site I found:
[http://www.measham.force9.co.uk/reference/biosp.htm](http://www.measham.force9.co.uk/reference/biosp.htm)

---

### Post by EV500B on 2008-12-24
There is [COLOR=Red][CmosPwd]("http://www.cgsecurity.org/wiki/CmosPwd")[/COLOR] and [COLOR=Red][!Bios]("http://www.11a.nu/software/bios-pc-bios-security-and-maintanance-toolkit/")[/COLOR] but unfortunately i cannot find any information about the Sahara Image BOOK's motherboard, so i can't say if it will be compatible/work or just blow up your motherboard.

---

### Post by Xiong Chiamiov on 2008-12-24
> **littlebytecc said:**
> i tried to get to the CMOS battery, but cannot find it - tried unscrewing the laptop base, but it wont open and i am afraid of breaking it.

Manual?
> **littlebytecc said:**
> 
i then tried the F12, F8 and the CTRL + C, it wont work...

There are many, many keys used.  I usually mash esc, f1, f2, f5, f9, del, tab and control at the same time repeatedly when trying to get into the BIOS of a system that I don't know the key for.
> **littlebytecc said:**
> dark side of the force..?  :tongue:
dunno what u mean -  I have a very valid and legal windows copy, it is just too difficult for my client to run linux neoshine which takes forever to boot up on this very annoying little notebook/laptop from Sahara (8 inch)
..okay...i cant get right by any way and means at this stage...am trying a different linux operating system such as PCLinuxOS or Fedora which i have available.  this neoshine system wont autorun this either...do you perhaps know what the file extension is so that i select the correct file to try and start what would have been the 'exe' as in windows..?
I'm a bit confused by what you're trying to say here, but I gather that installing Windows may not actually be the problem, but rather something else.  If you ask about that directly, it is possible that we may be able to fix your initial problem, rather than going through all of this mess of operating systems.

---

