---
title: "HowTo install MS office on ubuntu, a lil help please.."
date: 2009-08-29
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-08-29
ok guys i have installe the wine and all i just dont unterstand the last part of the this how to 

the part i don't understand is :
"change rpcrt4.dll ng Wine with rpcrt4 that i got from windows ([COLOR=Blue]attached file at the bottom of this post[/COLOR])
 
 when all are done, place you Ms Office 2007 CD installer (i still use the  trial version downloaded from M$) then click on "**setup**"
 
 and wait mo lang matapos mag-install, minsan at 70% kala mo nag-hang pero bayaan mo lang it will push thru.. 
 
 once installed.. run 
      PHP Code:
     [LEFT]                      [COLOR=#000000] [COLOR=#0000bb]winecfg  
[/COLOR] [/COLOR]               [/LEFT]
 
  tapos change mo ulit yung Windows version to "XP".. 
 
 your done!.."

 

this is the howto that i got it from its toward the bottem:

[code]                                  **How to: Install MS Office 2007**             
                                                                I just wanted to share how i did it, my wife been bugging me to install it on Ubuntu since she's beginnig to like it, except that she's really familiar using MS Office and ito din yung ginagamit nya sa Office.. i've tried all the possible ways on installing it, i even tried using CrossoverLinux kaso may bayad :sad:.. then ganito ginawa ko..

i totally remove my old wine version, i even deleted the .wine on the home folder, then i downloaded Wine ver 1.1.4 if you have installed winetricks,i would suggest for you to delete it as well.


to get Wine ver 1.1.4
     PHP Code:
     [LEFT]                      [COLOR=#000000] [COLOR=#0000bb]sudo wget http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#ff8000]//wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list  
[/COLOR] [/COLOR]               [/LEFT]
 
tapos....
     PHP Code:
     [LEFT]                      [COLOR=#000000] [COLOR=#0000bb]sudo apt[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]get update  
[/COLOR] [/COLOR]               [/LEFT]
 
once done type in.. 

     PHP Code:
     [LEFT]                      [COLOR=#000000] [COLOR=#0000bb]sudo apt[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]get install wine  
[/COLOR] [/COLOR]               [/LEFT]
 
- this will install "wine" on your system

then download winetricks..
     PHP Code:
     [LEFT]                      [COLOR=#000000] [COLOR=#0000bb]wget www[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]kegel[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]com[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]wine[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]winetricks  
[/COLOR] [/COLOR]               [/LEFT]
 
tapos..
     PHP Code:
     [LEFT]                      [COLOR=#000000] [COLOR=#0000bb]sh winetricks msxml3 dotnet20 gdiplus riched20 riched30 vcrun2005sp1  
[/COLOR] [/COLOR]               [/LEFT]
 
it will install some DLL na kailangan for you to install MS Office

tapos..
     PHP Code:
     [LEFT]                      [COLOR=#000000] [COLOR=#0000bb]winecfg  
[/COLOR] [/COLOR]               [/LEFT]
 
change Windows version to "**Vista**"

change rpcrt4.dll ng Wine with rpcrt4 that i got from windows ([COLOR=Blue]attached file at the bottom of this post[/COLOR])

when all are done, place you Ms Office 2007 CD installer (i still use the  trial version downloaded from M$) then click on "**setup**"

and wait mo lang matapos mag-install, minsan at 70% kala mo nag-hang pero bayaan mo lang it will push thru.. 

once installed.. run 
     PHP Code:
     [LEFT]                      [COLOR=#000000] [COLOR=#0000bb]winecfg  
[/COLOR] [/COLOR]               [/LEFT]
 
 tapos change mo ulit yung Windows version to "XP".. 

your done!..

---

### Post by arochester on 2009-08-29
Try installing the app called "PlayOnLinux" . Microsoft Office 2007 is listed as one of the installs.

---

### Post by Maheriano on 2009-08-29
1. Posting questions in multiple languages probably won't yield much help.

2. Install Open Office and forget about Microsoft.

---

### Post by R3fr4cti0n on 2009-08-29
i am getting sick of the coments about OO, the program is dated for what i need to do, and the other programs that i use that ONLY work with Office. i have OO, it came with jaunty, it serves it purpose, but it is not a fit for me, It's possible to use Office in Ubuntu so i would like to since i already paid for it and i dont like windoze, is this crime?

and the Howto is from another post it was the only one i found on how to get Office up and running that did't have broken links, i was hoping that someone else is useing office in ubuntu and they could help, please spread the love not the constructiveless criticism

---

### Post by nhasian on 2009-08-29
> **Maheriano said:**
> 2. Install Open Office and forget about Microsoft.

thats not really helpful.  in some cases you have to have office.

Anyway R3fr4cti0n, I dont understand why your having trouble.  I just did this a few days ago without a hitch.  All i did was install the latest wine from [www.winehq.org](www.winehq.org) and then ran the setup.exe on the office 2007 cd and everything went smoothly.

---

### Post by R3fr4cti0n on 2009-08-29
> **nhasian said:**
> thats not really helpful.  in some cases you have to have office.

Anyway R3fr4cti0n, I dont understand why your having trouble.  I just did this a few days ago without a hitch.  All i did was install the latest wine from [www.winehq.org]("http://www.winehq.org") and then ran the setup.exe on the office 2007 cd and everything went smoothly.


  i read that i have to have wine 1.1.14 or highter to use office 2007 did you just get the latest Stable:                              **[Wine 1.0.1]("http://www.winehq.org/announce/1.0.1")**?

---

### Post by Merk42 on 2009-08-29
> **R3fr4cti0n said:**
> i am getting sick of the coments about OO...

..and I'm sick of people saying "M$" and "Windoze"

Anyway, it seems you do need at least 1.1.13 to run Office 2007.  To get something higher than the 1.0.1 that is in the repositories, I recommend adding WINE's repository.  That way you will always have the latest version. Instructions on how to do so are [here](http://www.winehq.org/download/deb)

I am curious though, what Office does that OO.org doesn't for you.

---

### Post by howefield on 2009-08-29
> **R3fr4cti0n said:**
> i read that i have to have wine 1.1.14 or highter

Then go to winehq.org and follow the instructions to add the repository.

---

### Post by scrooge_74 on 2009-08-29
Hey install Virtual Box, then virtualize XP and then install Office 2007 ;)

---

### Post by scorp123 on 2009-08-29
> **R3fr4cti0n said:**
> i read that i have to have wine 1.1.14 or highter to use office 2007 

Open a terminal. Then type this into it:
```
gksudo gedit /etc/apt/sources.list.d/winehq.list
```

When you're asked for a password: That should be your own password (I assume you have administrative rights?). If all goes well a new empty editor window should have opened now.

Kubuntu/KDE users would type this command:
```
kdesu kate /etc/apt/sources.list.d/winehq.list
```

OK, now that the editor is open, copy & paste this stuff into it:
```
#
# wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
# sudo apt-get update
# sudo apt-get install wine cabextract
#

deb http://wine.budgetdedicated.com/apt jaunty main
```
Save + close!

The first few lines with the hash # in front of them are comments. I always place comments into my *.list files, e.g. I put the info where and how to get the GPG keys from.

So we will do as the comment says. Please type this command into the terminal: ```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

Then do the other commands:
```
sudo apt-get update
sudo apt-get install wine cabextract
```

Voila. If you did all this you should now have WINE version **1.1.28**

And now that your package manager knows about it too (via that *.list file) it will automagically tell you whenever there is an update to a higher version.

Hope this helps?

---

### Post by scorp123 on 2009-08-29
> **scrooge_74 said:**
> Hey install Virtual Box, then virtualize XP and then install Office 2007 ;) Yes, that's probably the best idea with the least hassle. With the "seamless" mode any Office app could even be run directly in the Ubuntu desktop.

---

### Post by R3fr4cti0n on 2009-08-29
> **Merk42 said:**
> ..and I'm sick of people saying "M$" and "Windoze"

Anyway, it seems you do need at least 1.1.13 to run Office 2007.  To get something higher than the 1.0.1 that is in the repositories, I recommend adding WINE's repository.  That way you will always have the latest version. Instructions on how to do so are [here]("http://www.winehq.org/download/deb")

I am curious though, what Office does that OO.org doesn't for you.

well the most important is my wife college keyboarding and doc processing add-on for ms word 2007 that sne needs for her online college, it updates right to the webcollege site and the program is no able to be added on to OO, ty for instructions!

:) i do believe i sarted this thread, so ill say what i want!  \\:D/

---

### Post by partsdale on 2009-08-29
> **R3fr4cti0n said:**
> i am getting sick of the coments about OO, the program is dated for what i need to do, and the other programs that i use that ONLY work with Office. i have OO, it came with jaunty, it serves it purpose, but it is not a fit for me, It's possible to use Office in Ubuntu so i would like to [SIZE="4"][COLOR="Red"]since i already paid for it[/COLOR][/SIZE] and i dont like windoze, is this crime?

and the Howto is from another post it was the only one i found on how to get Office up and running that did't have broken links, i was hoping that someone else is useing office in ubuntu and they could help, please spread the love not the constructiveless criticism

[http://shop.canonical.com/product_info.php?products_id=530&osCsid=db823c966e0226bd1a49b762a741cf5b](http://shop.canonical.com/product_info.php?products_id=530&osCsid=db823c966e0226bd1a49b762a741cf5b)


another possibility...

---

### Post by MrWES on 2009-08-29
[QUOTE=scrooge_74;7866763]Hey install Virtual Box, then virtualize XP and then install Office 2007 ;)[/QUOTE

+1 -- that's the way I've done it in the past.

---

### Post by scorp123 on 2009-08-29
> **R3fr4cti0n said:**
> doc processing add-on for ms word 2007 that sne needs for her online college, it updates right to the webcollege site So that program expects to find a complete Windows network stack? In that case forget about WINE. You will need to emulate a complete PC and have a virtual Windows XP installed on it.

Here a posting that explains how to get the latest and greatest VirtualBox:

[http://ubuntuforums.org/showpost.php?p=7614149&postcount=2](http://ubuntuforums.org/showpost.php?p=7614149&postcount=2)

---

### Post by R3fr4cti0n on 2009-08-30
i dont have a xp disk. and i have been trying to install from my recovery disk for an hour, i dont think i can use a recovery disk, so i tried my vista Premium disk, and it wont even boot.

---

### Post by 3rdalbum on 2009-08-30
> **scorp123 said:**
> So that program expects to find a complete Windows network stack? In that case forget about WINE.

It might not use low-level functions of Windows. If it's using the ordinary APIs for network/internet access on Windows it will probably work.

---

### Post by scorp123 on 2009-08-31
> **3rdalbum said:**
> it will probably work. You said it yourself: "probably". For real Windows compatibility I'd still recommend a VM, despite the overhead.

---

### Post by scorp123 on 2009-08-31
> **R3fr4cti0n said:**
> i dont have a xp disk. It should be possible to buy one cheap at your next computer shop? Or a used package from e-Bay? You mentioned your wife going to college .. maybe she can get one cheap from there with educational discounts?

---

### Post by A_M_S on 2009-08-31
I'm using office 2007 in virtual box and it runs with no problems!

---

### Post by mlentink on 2009-08-31
Quite frankly, apart from running within a virtual machine, I have found that running windows software through wine is as troublesome as trying to run linux software on windows. 
It might run. 
Seeing as how your spouse needs to use networking-features that are dependent upon the windows networking stack. I sincerely advise you to get hold of a XP-disk and install the whole thing in Virtualbox. 
And yes, I really do accept the fact-of-life that sometimes, Microsoft software cannot be avoided.

As a personal remark, whith which you can obviously do whatever you want, using derogatory adjectives with regards to the folks in Redmond might give the wrong impression to some. Much as I am an advocate of OSS, I also recognize the influence Microsoft has had on the development of ICT. And I have yet to see an alternative as feature and function rich as the Exchange/Outlook combo. Which I do not use if I can possibly avoid it.

---

### Post by R3fr4cti0n on 2009-08-31
I DL'ed Vbox however on shut down it all froze on me this has happened a few times now please see
[http://forums.virtualbox.org/viewtopic.php?f=6&t=21831&p=95278#p95278](http://forums.virtualbox.org/viewtopic.php?f=6&t=21831&p=95278#p95278)
i dont know the prob but could it be i DL'ed the proper version i am running 64bit is therer 2 diffrent versions?

---

### Post by scorp123 on 2009-09-01
> **R3fr4cti0n said:**
> I DL'ed Vbox however on shut down it all froze on me this has happened a few times now please see
[http://forums.virtualbox.org/viewtopic.php?f=6&t=21831&p=95278#p95278](http://forums.virtualbox.org/viewtopic.php?f=6&t=21831&p=95278#p95278)
i dont know the prob but could it be i DL'ed the proper version i am running 64bit is therer 2 diffrent versions? Why did you download VirtualBox from a website when better instrucions were already given to you?

[http://ubuntuforums.org/showpost.php?p=7867342&postcount=15](http://ubuntuforums.org/showpost.php?p=7867342&postcount=15)

---

### Post by scrooge_74 on 2009-09-01
hum Virtualbox version in their website is a lot newer than the one in the repositories (at least for Hardy), I enabled backports, downloaded from their website. And now I have integration between the XP desktop and my Linux desktop.

---

### Post by scorp123 on 2009-09-01
> **scrooge_74 said:**
> hum Virtualbox version in their website is a lot newer than the one in the repositories  If you had cared to read the post in question you would have seen that I gave pointers to SUN's own repo. It can't get newer than that. Who's using that outdated release in Ubuntu's repos anyway?? That's not even the repo I was referring to.

---

### Post by scrooge_74 on 2009-09-01
> **scorp123 said:**
> If you had cared to read the post in question you would have seen that I gave pointers to SUN's own repo. It can't get newer than that. Who's using that outdated release in Ubuntu's repos anyway?? That's not even the repo I was referring to.

Nope I didn't care to read what you said before ;)  I being too busy the past two weeks to read everything ;)

---

### Post by scorp123 on 2009-09-01
> **scrooge_74 said:**
> Nope I didn't care to read what you said before ;) Ha, gotcha :D  \\:D/

But to get back to the topic: I'd strongly recommend getting the latest and greatest VirtualBox from SUN's / virtualbox.org's repo ... that way you get auto-notified when there is an update.

---

### Post by R3fr4cti0n on 2009-09-02
i downloaded from synaptic and it wont even display on my computer, by display i mean it says i have downloaded it and have the version but i cannot find it any where. so i did a fresh install of ubuntu and  got vvox from their website, the 64 bit one and i am going to try again later today.

---

### Post by KIAaze on 2009-09-02
Just curious: What language did you mix in in your first post? (or if you copied the text from another howto, what language was it?)

> and wait mo lang matapos mag-install, minsan at 70% kala mo nag-hang pero bayaan mo lang it will push thru..

...

tapos change mo ulit yung Windows version to "XP".. 
...
and ito din yung ginagamit nya sa Office.. i've tried all the possible ways on installing it, i even tried using CrossoverLinux kaso may bayad .. then ganito ginawa ko..
...
it will install some DLL na kailangan for you to install MS Office

:confused::confused:
As for me, I'm perfectly happy with OpenOffice. :)

---

### Post by scrooge_74 on 2009-09-02
> **R3fr4cti0n said:**
> i downloaded from synaptic and it wont even display on my computer, by display i mean it says i have downloaded it and have the version but i cannot find it any where. so i did a fresh install of ubuntu and  got vvox from their website, the 64 bit one and i am going to try again later today.

What you downloaded? Open Office? using synaptic? if you used synaptic it is there already. You can't go wrong with synaptic

---

### Post by Merk42 on 2009-09-02
> **scrooge_74 said:**
> What you downloaded? Open Office? using synaptic? if you used synaptic it is there already. You can't go wrong with synaptic
He means Virtualbox

> **R3fr4cti0n said:**
> i downloaded from synaptic and it wont even display on my computer, by display i mean it says i have downloaded it and have the version but i cannot find it any where. so i did a fresh install of ubuntu and  got vvox from their website, the 64 bit one and i am going to try again later today.
Most likely you needed to add yourself to the vboxusers.

I recommend installing it through VirtualBox's repositories, that way you always have the latest version.
Uninstalled the one you have and then go [here](http://www.virtualbox.org/wiki/Linux_Downloads) and scroll past the .deb files to the instructions on how to set that up.  Once that is done, I recommend reading the [manual](http://download.virtualbox.org/virtualbox/3.0.4/UserManual.pdf), a lot is explained there, like adding people to vboxusers, the additions I told you about earlier, plus if you still have problems it's good to know you followed instructions to the letter and are having a problem

---

### Post by scorp123 on 2009-09-02
> **R3fr4cti0n said:**
> i downloaded from synaptic and it wont even display on my computer, That's a glitch. Just logout and login again. It will be in the system tools menu:

Applications > System Tools

---

### Post by scorp123 on 2009-09-02
> **Merk42 said:**
>  Most likely you needed to add yourself to the vboxusers. That's probably the next thing he'll run into, yes.

> **Merk42 said:**
>  I recommend installing it through VirtualBox's repositories, that way you always have the latest version. We're already past that point :D  and those recommendations were already given.

---

### Post by scared0o0rabbit on 2009-09-02
So I have a somewhat related question.  I installed the latest wine and then installed office no problem, however it only shows up on one of my accounts on this computer.  Do I need to install a separate copy of office 2007 for each user on the computer?

---

### Post by scrooge_74 on 2009-09-03
I'm thinking YES!. Remember when you install a Windows program it goes into the .wine folder in your home folder so it only available for this particular user

---

### Post by KIAaze on 2009-09-03
No, I think you can avoid installing it multiple times.

I don't know wine very well, but it's probably possible to create a shared wine directory / specify a wine directory to use.

Or by creating a shared user account like this for example:
[http://ubuntuforums.org/showthread.php?t=917422](http://ubuntuforums.org/showthread.php?t=917422)

Otherwise, a symbolic link to something like /opt/shared/office should do.
Copy the created program files "office" folder to /opt/shared and then make every wine install symlink to it.

---

