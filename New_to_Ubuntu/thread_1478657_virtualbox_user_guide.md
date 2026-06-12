---
title: "virtualbox user guide"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by flyfishingphil on 2010-05-10
I've spent some time looking for a very basic user guide to virtualbox on setting it up, how it "works" and what all it is aimed at accomplishing and haven't been able to locate it. Anybody know if there is such a guide and, if so, where to get it?

I'm trying to figure out what I can do to use a couple of things that require Windough$ (have Vista in dual boot) and if I have to have Windough$ in to use them, if there may be a way to get around that, and end the dual boot sequence but still have access to those.

Is that statement confusing enough?:confused:

---

### Post by Ozymandias_117 on 2010-05-10
[http://www.linuxadventures.net/virtualization/vbox.html]("http://www.linuxadventures.net/virtualization/vbox.html") This may answer your questions... He is specifically talking about debian, but you should be able to get going from it. If not, post back any questions and I can try to help you.

Note: I would certainly add virtualbox to your repositories instead of just downloading it.

---

### Post by Ocxic on 2010-05-10
Try downloading the user guide from virtualbox.org.

---

### Post by flyfishingphil on 2010-05-10
Thanks for the offers of info. Checked and both look promising but they did form a couple of questions.

Ozymandias, the one you ref'd to shows a download but it only shows matches up to 9.10, not 10.04. Any conflict here? Also says to not use the freebie but to get one that's not "free". How about the Sun Virtual, or is there a better choice?

Ocxic, looks like it will take a little time to open everything up but that looks like an actual "manual" that may well be worth grabbing.

This isn't a rush matter so I can spend some time on both and figure just what I want to do. (I'll also have to figure out how to get the "Windough$" out of my external HDD for installation in the VBox and remove it from the internal.) 

Takes a little time to "adjust" to Ubuntu but it sure appears to be a good choice to make.

---

### Post by Ocxic on 2010-05-10
I should explain the "freebie" / "not free" thing.. There are actually two versions of VirtualBox, one is completely open source(the "freebie"/OSE - Open Source Edition), the other has some proprietary code that allows the use of USB devices.

I would recommend NOT getting the OSE version as you will not be able to use any USB devices, among other things.

And unfortunately you'll have to create a fresh install of windows in the virtual machine, it's not possible to transfer an installation of windows from one HD to another, and it would be a massive change in system hardware that Windows will most likely not agree with.
BUT you can give VirtualBox direct access to the USB drive your currently using, (the downside not being able to boot the drive normally after that. as it would mess up VirtualBox)

---

### Post by howefield on 2010-05-10
> **flyfishingphil said:**
> I've spent some time looking for a very basic user guide to virtualbox on setting it up, how it "works" and what all it is aimed at accomplishing and haven't been able to locate it.

You have been to the virtualbox site, but in case you missed them, there some very good video tutorials there also.

[http://www.virtualbox.org/wiki/VirtualBoxTV](http://www.virtualbox.org/wiki/VirtualBoxTV)

> Windough$

Haven't seen that one before, there seems no end to the talents of some here to make derogatory terms out of nothing.

---

### Post by seenthelite on 2010-05-10
If you have Virtualbox installed click on Help then Contents and the manual is there.

---

### Post by shae on 2010-05-10
Here is some information about moving an installed version of Windows into VirtualBox: [http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)

---

### Post by Ozymandias_117 on 2010-05-10
To add the free (as in beer) version of VBox, add this to your repositories:
```
deb http://download.virtualbox.org/virtualbox/debian lucid non-free
```

Then run
```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
```
to add the key for it

finally
```
sudo apt-get update
sudo apt-get install virtualbox-3.1
```
to actually install it.

---

### Post by flyfishingphil on 2010-05-10
Thanks to all for the help so far. Just got back on and am really impressed with all of the help offered here. Now I'll spend the next several days going over all of the info and figuring out how to totally mess things up! (Just joking!) Looks like the VBox is probably the best way to go, if I can get the Vista from point A to point B. If not I'll just put up with dual boot because it's not that bad.

Oops! First stumble block. Ozymandias, tried the deb directions in Terminal and here's what I got:

[I][I]flyfishingphil@flyfishingphil-laptop:~$ deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid non-free
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
deb: command not found[/I][/I]

Is there something else I need to do?

---

### Post by howefield on 2010-05-10
Add the line to your software sources, it isn't a terminal command.

System > Administration > Software Sources > Other software tab and Add. Then import the key using the authentication tab in the same Software Sources window.

---

### Post by spydeyrch on 2010-05-10
Hey, hope this helps.

I was helping a few people with some VB issues a few days a go. Here is the [thread.]("http://ubuntuforums.org/showthread.php?t=1474865") Anyway, I posted a quick how-to guide that I wrote up on the fly. Hope it helps. You don't have to deal with the terminal or anything like that.

Check it out and see if it helps at all.

-Spydey :KS

---

### Post by Ozymandias_117 on 2010-05-10
As the other poster said, that needs to be added to software sources, the rest of the commands can be run in a terminal.

---

### Post by flyfishingphil on 2010-05-10
> **howefield said:**
> Add the line to your software sources, it isn't a terminal command.

System > Administration > Software Sources > Other software tab and Add. Then import the key using the authentication tab in the same Software Sources window.
DUH! You can tell I'm wide awake. As somebody once said: Be Alert! We need more lerts!

Spydey, thanks, I'll check it out now.

---

### Post by flyfishingphil on 2010-05-10
> **spydeyrch said:**
> Hey, hope this helps.

I was helping a few people with some VB issues a few days a go. Here is the [thread.]("http://ubuntuforums.org/showthread.php?t=1474865") Anyway, I posted a quick how-to guide that I wrote up on the fly. Hope it helps. You don't have to deal with the terminal or anything like that.

Check it out and see if it helps at all.

-Spydey :KS
spydey, stopped by your link and filled out info requested with question on GPU. I'll wait for an answer there. Thanks.

---

### Post by spydeyrch on 2010-05-10
> **flyfishingphil said:**
> spydey, stopped by your link and filled out info requested with question on GPU. I'll wait for an answer there. Thanks.

Not a problem, I will check it out and respond there.

Oh, and I noticed you location. I am from P-Town, OR  :biggrin:\\:D/

-Spydey :guitar:

---

### Post by flyfishingphil on 2010-05-10
> **spydeyrch said:**
> Not a problem, I will check it out and respond there.

Oh, and I noticed you location. I am from P-Town, OR  :biggrin:\\:D/

-Spydey :guitar:
May be moving back to that area shortly. Currently Medford area.

BTW, possibly good news! My weak mind, and weaker memory, just reminded me that I had recently purchased WinXP for an older computer for a grandson but I installed 9.10 instead. I can get that one back and install it in the vbox and do everything I need to do in windough$. From what I've read it sounds like the better one to use. Thoughts on that?

---

### Post by spydeyrch on 2010-05-10
> **flyfishingphil said:**
> May be moving back to that area shortly. Currently Medford area.

BTW, possibly good news! My weak mind, and weaker memory, just reminded me that I had recently purchased WinXP for an older computer for a grandson but I installed 9.10 instead. I can get that one back and install it in the vbox and do everything I need to do in windough$. From what I've read it sounds like the better one to use. Thoughts on that?

After looking at your specs online, I would say that XP is a better choice, as far as system resource use. You certainly have enough memory and your GPU should be just fine.

I would be a little concerned about your CPU because it doesn't have hardware support for virtualization, which just means that VB would need to do somethings via software virtualization instead of hardware virtualization. That just means that it would be a little more taxing on your system than if you had hardware support for virtualization. Here are the specs for your CPU: [http://ark.intel.com/Product.aspx?id=35583](http://ark.intel.com/Product.aspx?id=35583). 

So XP would use less resources than Vista. If you software can run in XP, then great!!! :guitar:

Some may say that due to XP finishing it's lifecylce soon, it would not be a wise choice. But I say that if it is not going to be your main OS, then go for it!!! Also, I have an XP VM and I don't have a virus scanner on it. The reason being is that I use continual snapshots of my VM. So even if my XP-VM system got infected. All I would have to do is turn off the VM and restart it and the virus would be gone!! YAY!! But, the bad thing is that if you take a snapshot while you are infected, you just did a big no-no!!

Anywho, those are my two cents on the matter. I would go for XP due to lower system requirements, you have an extra license, and you could get by with it just fine.

Hope that makes sense. Let me know if you have any questions.

-Spydey :)

---

### Post by flyfishingphil on 2010-05-10
Looking at that list raises the question: Any way to get the "stuff" needed to do the virtualization support, or is the HDD "fixed" in that regard and not "upgradeable"?

---

### Post by emoguitarist06 on 2010-05-10
Robbie hosts a tech show Tuesday nights
[www.category5.tv](www.category5.tv)
He is actually feature in Ubuntu 9.10's expamples folder
here are two tutorials for virtual box.
[http://www.category5.tv/show_notes/episode_112.php](http://www.category5.tv/show_notes/episode_112.php)
[http://www.category5.tv/show_notes/episode_116.php](http://www.category5.tv/show_notes/episode_116.php)

I recommend the regular version and not the OSE version in the repositories as it does not have usb support and other features

---

### Post by flyfishingphil on 2010-05-10
> **emoguitarist06 said:**
> Robbie hosts a tech show Tuesday nights
[www.category5.tv](www.category5.tv)
He is actually feature in Ubuntu 9.10's expamples folder
here are two tutorials for virtual box.
[http://www.category5.tv/show_notes/episode_112.php](http://www.category5.tv/show_notes/episode_112.php)
[http://www.category5.tv/show_notes/episode_116.php](http://www.category5.tv/show_notes/episode_116.php)

I recommend the regular version and not the OSE version in the repositories as it does not have usb support and other features
Thanks emo. I'm starting to think I might just put together a full listing of these tips and save it for others that don't know where to look.

---

### Post by spydeyrch on 2010-05-10
> **flyfishingphil said:**
> Looking at that list raises the question: Any way to get the "stuff" needed to do the virtualization support, or is the HDD "fixed" in that regard and not "upgradeable"?

When you say the "stuff", do you mean the hardware support for virtualization? Or are you referring to something else? I am a little thrown off by you mentioning the HDD because hardware support for virtualization doesn't have anything to do with your HDD (Hard Disk Drive).

The hardware support for virtualization is really only a CPU thing. It is pretty simple, either your CPU supports it (Intel VT-x or AMD-v) or it doesn't. Simple as pie. Hardware support for virtualization doesn't deal with any other piece of hardware, just your CPU (if you want to get really technical then I guess you could mention the Mobo, but that is not really the subject at hand. :P)

Now, by mentioning the HDD, it makes me think that perhaps you are referring to being able to migrate/transfer your current windows install, or true install, to VM install. Is that it or am I way off? :confused:

-Spydey :guitar:

---

### Post by flyfishingphil on 2010-05-10
Sorry about that. Hit the wrong buttons. Refering to CPU not having the hardware support for the virtualization. Is that changeable? I see from above that this is not a "changeable" situation and will just have to put up with a slower operation because of the lack of support for virtualization.

Don't plan to do the migrate/transfer. I can have that XP cd here in a couple of days and will probably install it into vBox. Since it will only be a once in a while use the "end" of XP won't really matter. I'll only be using that for a couple of special purposes like a portable printer that's not Ubuntu usable and my Magellan GPS. No plans to use it for anything on the 'net, already have Avast!, so no worry at all regarding virus/trojan/hacker/. I'll probably need to replace both before the XP is "worn out" with what little I'll be using it for.

Thanks again, and watch for the "OK, followed instructions and my computer ran away out of fear of what I was doing" thread. Grand opening probably just a few days away!

---

### Post by spydeyrch on 2010-05-10
> **flyfishingphil said:**
> Sorry about that. Hit the wrong buttons. Refering to CPU not having the hardware support for the virtualization. Is that changeable? I see from above that this is not a "changeable" situation and will just have to put up with a slower operation because of the lack of support for virtualization.

Don't plan to do the migrate/transfer. I can have that XP cd here in a couple of days and will probably install it into vBox. Since it will only be a once in a while use the "end" of XP won't really matter. I'll only be using that for a couple of special purposes like a portable printer that's not Ubuntu usable and my Magellan GPS. No plans to use it for anything on the 'net, already have Avast!, so no worry at all regarding virus/trojan/hacker/. I'll probably need to replace both before the XP is "worn out" with what little I'll be using it for.

Thanks again, and watch for the "OK, followed instructions and my computer ran away out of fear of what I was doing" thread. Grand opening probably just a few days away!

No problem. :)

I will await the thread that sates "Everything worked out great and I am running XP as a VM, no hitches at all!" That is the ideal thread. But your comment on your computer running away made me chuckle! :popcorn:

Hopefully it will work correctly for you.

Also, something I would recommend as a side option, install ubuntu tweak. Great liitle tool!

-Spydey :guitar:

---

### Post by flyfishingphil on 2010-05-11
Hokey Dokey. Did the VBox thing, installed the XP into it and got that working right but cant get externals, like the Lexmark printer, to connect with the windough$ in the VBox. I get the impression it has to be installed in Ubuntu to use in VBox and Lexmark doesn't offer and Linux compatible software with the printer I have. Guess the only option there is is to find a small, printer only, printer that is Linux/Ubuntu compatible to do what I want. 

Guess I'll just have to keep Vista and dual boot if I want to continue working with several things. Really hoped I could get around that with VBox but apparently not.

Too bad there isn't a SOLVED, but FRUSTATED notice we can put in.

---

