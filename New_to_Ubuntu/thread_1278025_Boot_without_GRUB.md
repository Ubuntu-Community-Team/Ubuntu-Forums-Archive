---
title: "Boot without GRUB"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by donescamillo on 2009-09-29
Hi,

I installed Ubuntu on my notebook (Lenovo 3000 N200) and as a result the DVDROM in the WinXP installation disappeared. After some search on the Web I found that the problem is in GRUB. There are solutions but they involve mucking around with MBR etc. which to me is rather scary.
I was wondering if I could install Ubuntu but without GRUB (I remember there was a checkbox for it, maybe).
In that case how do I boot?

Thank you
donescamillo

---

### Post by mathay on 2009-09-29
You could always get rid of your Ubuntu partition, re-expand the XP partition and boot through a VM or Wubi. This would have no effect on your XP partition. 

The GRUB issue isn't all that difficult to resolve. I've broken GRUB several times and with a good guide there isn't a great deal of hassle. In fact, truth be told, I've had more difficulty installing various OSes than I've had fixing GRUB.

---

### Post by donescamillo on 2009-09-29
I will try to install under windows and see how it works.
As for the GRUB problem, it has been around for a while. Probably they should fixing in the next version. As for fixing, I am just starting with Linux and am still far from it.
I may try it probably when Zealous Zebra comes out :) if not fixed by then

Thank you
donescamillo

---

### Post by Maxxtsch on 2009-09-29
After you choose you drive that you will install it one, you will see an 'Adavnced options' chick it, and un check the install bootloader

---

### Post by theozzlives on 2009-09-29
You could use lilo instead of GRUB.

---

### Post by donescamillo on 2009-09-29
To Maxxtsch:

This is actually what I did, but when I restarted the PC went straight to WinXP, the point was how to be able to select between WinXP and Ubuntu without GRUB. I thought the LiveCD will somehow detect that there is an Ubuntu installation and give me a choice between WinXP and Ubuntu but it did not work.
I am downloading now the Alternate CD, I will give LILO a try

Thank you
donescamillo

---

### Post by sliketymo on 2009-09-29
> **donescamillo said:**
> To Maxxtsch:

This is actually what I did, but when I restarted the PC went straight to WinXP, the point was how to be able to select between WinXP and Ubuntu without GRUB. I thought the LiveCD will somehow detect that there is an Ubuntu installation and give me a choice between WinXP and Ubuntu but it did not work.
I am downloading now the Alternate CD, I will give LILO a try

Thank you
donescamillo

You could try installing EasyBCD in  XP,then ad your Ubuntu to your boot options.

---

### Post by donescamillo on 2009-09-30
Unfortunately EasyBCD does not work with WinXP bootloader.

---

### Post by egalvan on 2009-09-30
> **donescamillo said:**
> Unfortunately EasyBCD does not work with WinXP bootloader.


I don't know where you got this information, but...

Directly from the EasyBCD  website!!!

**[http://neosmart.net/wiki/display/EBCD/Windows+XP](http://neosmart.net/wiki/display/EBCD/Windows+XP)**
**The [COLOR="Red"]XP Boot Process[/COLOR]**
A heading from this page...

***The [COLOR="Red"]XP Boot Process[/COLOR]***

Seems the EasyBCD folks have a different view of XP.


Or maybe you confused EasyBCD with Vista...
*you cannot use the Vista bootloader to directly enter a Windows XP (and below) installation*

---

### Post by donescamillo on 2009-09-30
I thought so because I saw this on their documentation page:

Quote
It all depends on who you ask or what you want to get done, but
 
[LIST]
[*][**EasyBCD**]("http://neosmart.net/dl.php?id=1") is NeoSmart Technologies 100% **free** [COLOR=Red]Vista bootloader[/COLOR] modification tool.
[*]A way to get your Vista working with Linux, BSD, Mac OS X, and **dozens more** operating systems without a headache!
[/LIST]
Unquote
Anyway, I will download it and try it, it costs me nothing, I have made an image of the installation

---

### Post by donescamillo on 2009-09-30
I downloaded, run EasyBCD and was greeted with the following dialog box (see picture attached). Since I dont have Vista, EasyBCD cant help.

Regards,
donescamillo
[IMG]file:///D:/DOCUME%7E1/Me/LOCALS%7E1/Temp/moz-screenshot.jpg[/IMG][IMG]file:///D:/DOCUME%7E1/Me/LOCALS%7E1/Temp/moz-screenshot-1.jpg[/IMG]

---

### Post by louieb on 2009-09-30
You can install Ubuntu without installing GRUB. However you must have a Linux boot loader in order to use it. That means you need GRUB or LILO. 

GRUB does not need to control the MBR. You can install it in the boot sector (aka VBR) of the / (root) Linux partition. Then use the windows boot loader to load GRUB - GRUB will load Linux. You will have manually configure XP's boot loader.  That is the hard way to dual boot XP and Linux.    

Another option is boot with a SuperGrubDisk every time you want to boot to Linux. 

And there is WUBI - have not used it. From threads I have read - ok when it works. 

If you have a 1.5GB ram or more, a few GB of hard drive space and a fast CPU then [VirtualBox]("http://www.virtualbox.org/")  is a good way to test drive Linux. 

Give me GRUB - imo the best option for those that want to dual boot.

---

### Post by donescamillo on 2009-09-30
I actually tried installing Grub inside the partition but since it was installed last, it screwed my cdrom again. I dont know how to configure the XP boot loader, I tried to manually add an entry in boot.ini but it did not work. I solved the problem like this:

1. install WinXP
2. install Ubuntu from [COLOR=Red]AlternateCD[/COLOR]
   2.1 specify LILO as a boot loader
   2.2 install LILO [COLOR=Red]IN[/COLOR] the Linux parrtition
   2.3 the installer will still want to write something in the MBR-[COLOR=Red]DO NOT LET IT[/COLOR]
3. now you cant boot in Linux
4. burn a GAG disk (GAG is a boot manager)
5. boot from GAG and create two boot entries-one for Win and for Linux
6. Save changes on HDD (this will install on HDD GAG also)

I dont know if this is the right solution but at least works for me. And it also holds both OSes apart, ie WinXP does not know about and Linux does not know about WinXP.
I also dont know what will happen if I let the Ubuntu installer write into MBR, it may pick the WinXP entry and thus eliminate the need for GAG, I may try it

regards
donescamillo

---

### Post by egalvan on 2009-10-01
OK, I confess that the EasyBCD thing has me confused, since a HowTo guide used it to repair an XP install...
I'll have to check on this much closer...
I hate to have given you bad information.


> **donescamillo said:**
> I actually tried installing Grub inside the partition but since it was installed last, **it screwed my cdrom again**.

Again, I am confused...
What exactly do you mean by **it screwed my cdrom again** ?
Did the DRIVE stop working?
Did the DRIVE stop working under Linux?
Did the DRIVE stop working under XP?
Did the DRIVE stop showing up under XP?

I have NEVER heard of GRUB causing this kind of problem.


> I dont know if this is the right solution but at least works for me.
 And it also holds both OSes apart, ie WinXP does not know about Linux, and Linux does not know about WinXP.
I also dont know what will happen if I let the Ubuntu installer write into MBR, 
it may pick the WinXP entry and thus eliminate the need for GAG, I may try it


If it works for you, then great, but it's 'kludgey'.

The thing is, there are some hundreds of thousands of machines happily dual-booting XP and some flavor of Linux,
and the great majority are using GRUB.
Without problems.

I myself have at least twenty dual-boot installs in the last year,
and except for one (my fault, I did not pay attention during the partition phase),
they have all turned out great.
This includes several multi-boot, booting three different *nix's, along with XP.

And all OS's are separate.

---

### Post by donescamillo on 2009-10-01
Hi,

I apologise, I should have been more explicit in my posts. 
When GRUB is installed on Lenovo 3000 N200  it causes the CD-ROM to disappear from both WinXP and Ubuntu (see **[https://bugs.launchpad.net/ubuntu/+bug/198319](https://bugs.launchpad.net/ubuntu/+bug/198319)**).
Well, my notebook is Lenovo3000 N200. I install WinXP and after that I install Ubuntu with GRUB and the CD-ROM goes missing, no CD-ROM shown in file explorers, this is what I meant screwed.
So I tried to install again but with GRUB in the linux partition instead, the installer allows this. It did not work either. So I installed Ubuntu with LILO. The installer asked where to install LILO and I told it in the linux partition and not to write anything in MBR, in order not to affect the WinXP installation in any way. And because this way I cannot boot in linux, I used GAG. I agree it is 'kludgey', but the only improvement would be to let LILO write in MBR so that LILO handles the dual boot instead of GAG, I may try it. 
I have another PC with two HDDs and on the first HDD I have Win98, WinXP and Ubuntu living happily and no problems with GRUB either. But it did not work with the notebook.
The point is that this problem with GRUB should be fixed.

regards,
donesacmillo

---

### Post by egalvan on 2009-10-01
Muy Bueno. Don Escamillo

I looked at that link, and it seems to me, and others, to be a hardware
problem with specific drives and BIOS,
not so much a GRUB problem.

Many times hardware manufacturers act as if Microsoft was the only game in town,
and that causes problems for other OS's.
of course, the other OS's get the blame...
"it works under Microsoft, and blows up under Linux,
that proves that Linux is useless"
and most folks never see the lousy MS-centric engineering that led to that situation.
The POWER debacle in laptops is one specific instance.
ACPI is broken under Linux, because it is MS-centric.
Mandrake installs "bricking" CD-RW drives is another.

So, onward and upward...
have you tried the "fix" that the last post suggested?
Disable the optical in the BIOS?

Have you written to Lenovo and complained that their hardware is incompatible with Linux?

A year ago, a customer purchased a scanner that would not work on his Linux install.
We finally found one that did.
But I took the time to write a letter to the manufacturer to advise them that they would not receive any of his money, until Linux compatibility was assured for their hardware.

---

### Post by donescamillo on 2009-10-01
Hi,

I dont really understand how OSes talk to these devices and to BIOS so I cant judge whose the fault is. I am happy that I found a solution. I should have tried the fix with disabling the CDROM from BIOS, but now that everything is up and running I would not bother. As for writing to Lenovo, I would not bother either, I would (and I did) probably get more help from a forum like this one than from them (or any big company for that matter). 

Regards,
donescamillo

---

### Post by louieb on 2009-10-01
> **donescamillo said:**
> 
When GRUB is installed on Lenovo 3000 N200  it causes the CD-ROM to disappear from both WinXP and Ubuntu (see **[https://bugs.launchpad.net/ubuntu/+bug/198319](https://bugs.launchpad.net/ubuntu/+bug/198319)**).


How weird is that?  GRUB does probe BIOS to find what drives are attached. But so does Windows and Linux. Maybe Grub2 will cure that.

> asked where to install LILO and I told it in the linux partition and not to write anything in MBR, in order not to affect the WinXP installation in any way. And because this way I cannot boot in linux

played with Slackware a few times. Never could get LILO to install in the Linux partition boot sector.  (installer said it failed).  But have been able to install it in the MBR - go figure.

> I agree it is 'kludgey'

  Thanks for letting us know that you got it working and how you did it. GAG and LILO - to boot Linux - never would have thunk it.
lou :P

---

### Post by egalvan on 2009-10-02
> **donescamillo said:**
> Hi,

 As for writing to Lenovo, I would not bother either,
 I would (and I did) probably get more help from a forum like this one than from them (or any big company for that matter). 

Regards,
donescamillo

I agree with louieb, it's good you found a solution.


as for writing to Lenovo...

this is more to let them know of your problems and displeasure,
and possibly taking  your money elsewhere...
than a search for help.

When a customer says "I'll never buy brand X again"
Brand X often has no clue as to WHY sales are off.
If the customer takes the time to write, then the company will be made aware of problems.
of course, what they do with that info is not always useful,
and indeed some companies have no concern about customers.


And you may be surprised at what a well-written letter, mailed to the proper person, can accomplish at some "big companies".
Some companies rate a printed letter at 100-to-1, so if they receive two letters on the same subject, they figure on 200 users feeling the same way.

---

### Post by LewRockwell on 2009-10-02
> **egalvan said:**
> i agree with louieb, it's good you found a solution.


As for writing to lenovo...

This is more to let them know of your problems and displeasure,
and possibly taking  your money elsewhere...
Than a search for help.

When a customer says "i'll never buy brand x again"
brand x often has no clue as to why sales are off.
If the customer takes the time to write, then the company will be made aware of problems.
Of course, what they do with that info is not always useful,
and indeed some companies have no concern about customers.


And you may be surprised at what a well-written letter, mailed to the proper person, can accomplish at some "big companies".
Some companies rate a printed letter at 100-to-1, so if they receive two letters on the same subject, they figure on 200 users feeling the same way.

+ 1

.

---

