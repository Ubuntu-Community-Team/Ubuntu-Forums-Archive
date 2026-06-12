---
title: "RAM limit"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by SteelCore on 2009-03-04
I'm about to buy a new intel motherboard for a dedicated 32-bit Ubuntu machine.  Is it true that there's a limit on how much RAM can be used with Ubuntu?
I want to install 4Gbs RAM but if it can't be utilize what's the max that Ubuntu can use?
Thanks

---

### Post by iaculallad on 2009-03-04
A thread from [launchpad]("https://answers.launchpad.net/ubuntu/+question/40205").

---

### Post by OutOfReach on 2009-03-04
Ubuntu will only see about 3.2 GB if you have 4gb.
Though, you can install the server kernel from the repositories to get all 4GB in use.
Or of course you can install 64-bit Ubuntu.

---

### Post by SteelCore on 2009-03-11
Thank you all for the answers.  I have already bought the machine and using Ibex which detected 3.2 out of the 4 Gb of RAM.
From your answers and others I read that the server kernel and something called PAE can, if installed on Ubuntu 32-bit, enable the utilization of over 4Gb of RAM.
Why do they enable reading more than 4Gb? Are there any cons for installing these software?
I would appreciate any links that can answer these questions in regard to Ubuntu.
Thank you again

---

### Post by davidsrsb on 2009-03-11
PAE does have a small performance hit for the <3.2GB machines, so probably why it is not installed by default

---

### Post by 3rdalbum on 2009-03-11
If you have a 64-bit processor, why not just install 64-bit Ubuntu? Then you'll get access to 16 terrabytes of address space - including your current 4GB. And a speed improvement.

PAE is an old feature of CPUs from before Intel made 64-bit CPUs; I don't know quite how it works but Wikipedia does.

EDIT: I run 64-bit without problems; just don't install the 32-bit version of Flock as it won't work with your 64-bit Flash Player :-)

---

### Post by Paqman on 2009-03-11
+1 for 64-bit.

---

### Post by skymera on 2009-03-11
Yes, i run 64BIT with 4GB RAM.
Much more stable, highly reccommend

---

### Post by hyper_ch on 2009-03-11
yeah, go for 64bit... and install the 64bit flash plugin - don't go for the 32bit compatibility one. Althought the 64bit flash plugin from adobe is still alpha it's been working without a hitch for months now.

---

### Post by linux_tech on 2009-03-11
64-bit would be best for 4+GB RAM

---

### Post by gn2 on 2009-03-11
> **SteelCore said:**
> I'm about to buy a new intel motherboard for a dedicated 32-bit Ubuntu machine.  Is it true that there's a limit on how much RAM can be used with Ubuntu? ~

Yes, it's 4gb per process up to a total of 64gb

> **hyper_ch said:**
> yeah, go for 64bit... and install the 64bit flash plugin - don't go for the 32bit compatibility one. Althought the 64bit flash plugin from adobe is still alpha it's been working without a hitch for months now.

There was an update released fairly recently: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Works perfectly in my experience.

---

### Post by skymera on 2009-03-11
Yes, the latest Flash player for 64BIT works brilliantly, even with Compiz running.

---

### Post by presence1960 on 2009-03-11
It is not the fact it is Ubuntu that limits the amount of ram, it is the platform: 32 or 64 bit that determines that. Same goes for Windows. Vista SP1 fixed it so your 4GB of ram shows as installed on a 32 bit install, but if you go to system info it still only shows 3.2 GB available.

If you have 4 GB RAM and a 64bit CPU you would be loathe to not install 64 bit Ubuntu.

---

### Post by LowSky on 2009-03-11
I find the whole 32 to 64 bit threads that always pop up to be rather funny as most say or use bad information on how 64bit isn't hat great or ready for primetime. I have been using 64Bit Linux for quite a while, and its never really been an issue, as 32bit apps can be run in a pinch.

For some reason everyone makes 64bit processing to be similar the Pepsi v. Coke battle that rages across the world. Some how people still see it as a preference and not an evolution, like 16bit to 32bit was way back when.

But for people like (not all but many of us) us who build their own machines and like to see it run as fast as possible and even overclock, why use an OS that cannot use the entire processor?

---

### Post by Weidbrewer on 2009-03-11
I agree with **LowSky**.  The main thing that has kept me from upgrading my main 'Buntu machine to 64-bit full time is because I'm lazy.  ;)  I have everything working just how I want it to, and I'm not looking forward to migrating.

---

### Post by presence1960 on 2009-03-11
> **LowSky said:**
> I find the whole 32 to 64 bit threads that always pop up to be rather funny as most say or use bad information on how 64bit isn't hat great or ready for primetime. I have been using 64Bit Linux for quite a while, and its never really been an issue, as 32bit apps can be run in a pinch.

For some reason everyone makes 64bit processing to be similar the Pepsi v. Coke battle that rages across the world. Some how people still see it as a preference and not an evolution, like 16bit to 32bit was way back when.

But for people like (not all but many of us) us who build their own machines and like to see it run as fast as possible and even overclock, why use an OS that cannot use the entire processor?

I hear you LowSky. I read all that in here and that kept me from going 64bit initially. But as I grew more comfortable with Linux and ventured over to the x86-64 bit users section of the forum I was really encouraged by what was going on in there. I decided to give 64 bit a try and have never looked back. In spite of what one may "hear", 64 bit Flash and Java work just fine. 64bit is definitely the way to go if you have a 64bit CPU.

---

### Post by LowSky on 2009-03-11
> **presence1960 said:**
> I hear you LowSky. ....64bit is definitely the way to go if you have a 64bit CPU.

Thanks, but aside from a few processors (Intel Atom comes to mind) all new processors from AMD and Intel are 64 bit enabled

---

### Post by SteelCore on 2009-03-11
I thank all for their replies.  Actually the reason I'm not using 64-bit Ubuntu is the impression I had after quickly browsing the contents and links of this thread ([http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)).  I understood that 64 performs better but few applications are actually written to utilize its power. So I opted to go for the mature and thoroughly tested 32-bit instead. But since this thread is more recent and you all sound very encouraging I'll experiment with a dual boot along side my main 32-bit Ibex.
BTW the configuration is the following :
processor: Intel Dual Core 64 E5200 2.5GHz
motherboard: Intel DG35EC 775
RAM 2*2GB DDR2 800

---

### Post by expatCM on 2009-03-11
Yes, I think that is exactly the point.  There is no point at all to upgrade to 64 bit because the operating system is better / faster / memory is supported / ....  if the applications you want to run are not available in a 64 bit version.

Take Skype for example ...  they have made it clear that they do not see a 64 bit version as a priority.  Well given the choice between using Skype and using 64 bit Ubuntu, there is not going to be any time wasted in making the decision ...  it has to be stay with Skype.

---

### Post by scphan on 2009-03-12
i'd use 64-bit for programming, application development and execution, and for messing around but not for general stuff

---

### Post by hyper_ch on 2009-03-12
> **expatCM said:**
> [some text]

Do you run 64bit? What does not work?

Skype works, use medibuntu.

Why use 32bit if you have the power of 64bit available?

---

### Post by Paqman on 2009-03-12
> **SteelCore said:**
> I understood that 64 performs better but few applications are actually written to utilize its power. So I opted to go for the mature and thoroughly tested 32-bit instead. 

64-bit is mature and thoroughly tested these days, too.

The only small problem you might bump into is that sometimes 3rd parties don't release 64-bit version of their software (i'm looking at *you* Google Gears!) Otherwise you've got the same massive Ubuntu repos as 32-bit to get all your software from.

---

### Post by expatCM on 2009-03-12
hyper_ch ... skype works?   I tried it on a 64 bit version probably about a year or 18 months ago and it did not work at all ....   I cannot recall whether I downloaded from the repositories or from skype.com but I can remember at the time that it would be 32 bit until I saw others using skype on 64 bit.

That being the case, perhaps when 9.04 is out I will take a look at the 64 bit version ... :)

---

### Post by LowSky on 2009-03-12
Just to put it out there there still is no 64bit version of Skype for Linux, but you can install the 32bit version and it will work just fine on a 64bit OS
make sure you have the medibuntu repos... and here are the  instructions, 
[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

---

### Post by hyper_ch on 2009-03-12
skype works fine with medibuntu repos... no need to follow special instructions there, just add medibuntu and install skype.

you can use my repo generator if you don't know how to add medibuntu.

---

