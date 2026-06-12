---
title: "I accidentally my operating system"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by domoappo on 2010-12-09
Well I've been doing the dual boot thingey and I've been using Ubuntu and loving it, but all of a sudden today I can't get Ubuntu running. It takes me to some sort of screen, looks kinda like the terminal thingey where you type in stuff and it makes things happen. It tells me to use the TAB to access all my options. I really have no damn clue what to do. I have important stuff saved in Ubuntu and I need to access it.

---

### Post by Hippytaff on 2010-12-09
Is it a Wubi install or a 'real' dual boot?

---

### Post by domoappo on 2010-12-09
Uhh, I don't know. It let me choose from like 6 different versions (I think?) of Ubuntu.

---

### Post by Mindswap1 on 2010-12-09
Hi there! I no expert when it comes to Linux ( not even close to it ). However I do believe I had this problem before, and I think I fixed it by reinstalling GRUB boot loader. However Here is what I recommend you back your important files first heres how. 

_**Backing Up Important Files**_
Insert the live cd into the disc drive, and restart the computer. Your computer should boot up giving you the option to try or install Ubuntu. Click Try, and wait for it to load it. Once it loads up ( Might take a while depending on your computer ) Go to Places on the menu bar and then computer once there click the file system drive. It should open up a window with a bunch of folders. Go to the "home" folder and your user name should pop up. Double click that and it should open up all the files on your Ubuntu system. Now back up all your important information. 

_**Installing Grub Bootloader**_
And now lets try and reinstall grub boot loader.Once again boot up to the live cd and click try Ubuntu again. Open up the terminal and copy and paste the following without the quotation marks. 

"sudo grub"

Then type in. 

"find /boot/grub/stage1"

followed by 

"root (hd?,?)"

"setup (hd0)"
 
and lastly type in 

"quit"

Now restart your computer, and grub should boot up.

---

### Post by Hippytaff on 2010-12-09
when you get the choice of os's, which one appears at the top, if it's windows, it is probably a Wubi install...also did you download it in windows then double click an icon in windows to install it, if so it's wubi...if this is the case have a read of this excellent wubi help thread :-)[http://ubuntuforums.org/showthread.php?t=1639198Any](http://ubuntuforums.org/showthread.php?t=1639198Any) problems post back or post on that thread (Rubi1200 is good at this stuff :-) )

---

### Post by ppv on 2010-12-09
can you tell us what happens when you type startx at the prompt and enter.

---

### Post by coffeecat on 2010-12-09
> **Mindswap1 said:**
> 

_**Installing Grub Bootloader**_
And now lets try and reinstall grub boot loader.Once again boot up to the live cd and click try Ubuntu again. Open up the terminal and copy and paste the following without the quotation marks. 

"sudo grub"

Then type in. 

"find /boot/grub/stage1"

followed by 

"root (hd?,?)"

"setup (hd0)"
 
and lastly type in 

"quit"

Now restart your computer, and grub should boot up.@Mindswap1, these are instructions for legacy grub. The OP has most likely installed a recent version of Ubuntu which has grub 2 and these commands will not work. I think it's best if we diagnose what's wrong before trying to reinstall grub.

---

### Post by wilee-nilee on 2010-12-09
This "I must say' in the voice of Ed Grimley is what you should do so we can identify what is where.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

---

### Post by Hippytaff on 2010-12-09
also don't do what mindswap1 suggests untill we establish if youve done wubi install or not. :-)

@wileenilee, that was going to be my next post :-) apart from the ed grimley bit ;-)

---

### Post by wilee-nilee on 2010-12-09
> **Hippytaff said:**
> also don't do what mindswap1 suggests untill we establish if youve done wubi install or not. :-)

@wileenilee, that was going to be my next post :-) apart from the ed grimley bit ;-)

That is "totally decent" of you Ed Grimley

---

### Post by ppv on 2010-12-09
It could also be that it is just the graphical environment that cannot start up. Did you try installing some video drivers.

---

### Post by domoappo on 2010-12-09
Okay I didn't use a live CD, I dowloaded it from some website and put a flash drive in my computer, clicked some buttons on some screens that popped up, and viola! I had Ubuntu running. I felt like a ******* god. I put on a pair of shades and told Vista to deal with it. Anyways, I would hit F12 as my computer started, it gave me 3 options and I picked the 2nd one, then had the option of choosing to start up with Ubuntu or Vista, when I chose Ubuntu it let me choose from what seemed to be like 6 different versions.

---

### Post by Hippytaff on 2010-12-09
Can you boot from a liveCD or USB and run the scrip that wilee-nilee suggested...will show exactly how you've got things set up :-)

---

### Post by domoappo on 2010-12-09
One of my friends told me that I could simply re-install Ubuntu, but the problem is I have a whole lot of photos saved on Ubuntu that I need.

---

### Post by domoappo on 2010-12-09
And I just have to say the amount of support I'm getting for Ubuntu is wonderful. It really is. Thanks so much, you guys really make me glad I'm ditching Windows!

---

### Post by Hippytaff on 2010-12-09
> **domoappo said:**
> One of my friends told me that I could simply re-install Ubuntu, but the problem is I have a whole lot of photos saved on Ubuntu that I need.

You can do a fresh install...it would fix everything, but in order to rescue your files we need some information first.

boot into windows and go to add/remove programmes in the control panel. If there is a programme there called Wubi let us know.

If you did a real install then boot from the cd or usb that you used to install it...go to this link [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Download and run the script and post the Results.txt here.

Then we can find out what is what and how it might be possible to either fix the install or just rescue your files before you do a fresh install :-)

---

### Post by domoappo on 2010-12-09
I see no program called Wubi, but I do see Ubuntu.I'll do what you said and get back to you.

---

### Post by Hippytaff on 2010-12-09
> **domoappo said:**
> I see no program called Wubi, but I do see Ubuntu.I'll do what you said and get back to you.

maybe it is recognised as ubuntu by windows then :-s

try this thread [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

though the boot script is always useful :-)

---

### Post by domoappo on 2010-12-09
I tried to run Ubuntu again. I noticed that before it sent me to the terminal it said "No wubuilder" or something like that. but it says that even before ubuntu stopped working for me, it's been saying that for a while now. I went to the thread and I'll try to see if any of that stuff helps.

---

### Post by Hippytaff on 2010-12-09
this is probably the thread your referring to [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

and it will probably help...if you get stuck post there. Rubi1200 is really good at this stuff :-)

---

### Post by anewguy on 2010-12-09
HippyTaff - way to hang on there until we finally found the user is indeed using a wubi install - extremely important!

Good work!

Dave ;)

---

### Post by Hippytaff on 2010-12-09
> **anewguy said:**
> HippyTaff - way to hang on there until we finally found the user is indeed using a wubi install - extremely important!

Good work!

Dave ;)

Thanks Dave - I used to work in a call centre, thank God I only do this kind of thing voluntarily now :-)

---

### Post by anewguy on 2010-12-09
I never had the "fun" of a call center, instead I was a Senior Systems Programmer and System Administrator on big iron, minis and eventually micros.  I went through SO many years of what I realized where just innocent (I'd use the term ignorant, as in its truest form it just means a lack of knowledge) but still extremely aggravating calls.  Also many, many years of 24/7 support - couldn't be more than 15 minutes away from the systems.  Made dating, etc., a challenge.  Couldn't even just leave for a weekend without telling them a month in advance and then getting the 3rd degree on why I needed to be away - they claimed that's why they paid me the big bucks - I told them no amount of money was worth it.  So, I feel your pain, and I now understand how you also have the ability to ask the more meaningful questions instead of things that sidetrack the problems.

Dave ;)

---

### Post by wilee-nilee on 2010-12-09
> **domoappo said:**
> One of my friends told me that I could simply re-install Ubuntu, but the problem is I have a whole lot of photos saved on Ubuntu that I need.

Lets be sure to let the OP know that windows can't be removed if Ubuntu is installed inside. Ubuntu will have to be moved to a partition a or just a new install.

As it is having important stuff inside of a wubi=Ubuntu installed from a live Windows environment is at best not a good idea, back that stuff up to a usb drive  or something.

---

### Post by domoappo on 2010-12-09
Okay I took my issue to the other forum place. Once again thank you all for your help! : )

---

### Post by Hippytaff on 2010-12-10
> 
Okay I took my issue to the other forum place. Once again thank you all for your help! : )

Righto
 
Fred I'm also still a noob, so I know how confusing things can appear until you get a bit more familiar with how Linux works.
 
Your intput on my Debain thread would be much appreciated both ;-)
 
[http://ubuntuforums.org/showthread.php?t=1641929](http://ubuntuforums.org/showthread.php?t=1641929)

---

### Post by Jake Noodles on 2010-12-16
I'm the friend domoappo mentioned before...
 
His system definitely is a wubi installation. I was able to get it to boot from livecd. The issue is when he selects Ubuntu from the OS list, he gets a black screen. (I should mention that ubuntu is second on the list). When he gets the screen, this is seen:
 
---------------------------------------------------------------------------------------------------
                                GNU GRUB version 1.98-1ubuntu6
 
Minimal BASH-like line editing is supported. For the first word, TAB lists possible commands completions. Anywhere else TAB lists possible device or file completions. 
 
grub> _
 
---------------------------------------------------------------------------------------------------
 
He has very limited command, and this is definitely not a regular terminal. SUDO is not avaiable, so any sudo commands y'all may mention(ed) are not possible. I've tried fsck, but again, not available. 
 
Again, livecd boot worked, however as you all could have guessed, only his Windows files are available from within the live boot, and his root from his wubi installation is not available, so he cannot access his files and photos etc. 
 
If you all could have suggestions/questions/more information, I'll try to rectify the problem for him (as I have more experience with Ubuntu, however I, too am limited in my knowledge of Ubuntu, as you could've guessed). 
 
-Jake

---

### Post by Hippytaff on 2010-12-16
Hi Jake, welcome to the forums...try having a read of this post by Rubi1200 the Wubi specialist.
 
[[COLOR=#444444]http://ubuntuforums.org/showthread.php?t=1639198[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1639198")

---

