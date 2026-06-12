---
title: "Unistall MS Office 2003"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by JacquesPotter on 2011-07-31
How do I uninstall MS Office 2003?

---

### Post by techtabu on 2011-07-31
Uninstall from where? Why are you asking uninstalling Office in Ubuntu forum?

---

### Post by Wim Sturkenboom on 2011-07-31
Not familiar with uninstalling MS apps in general, but doesn't running setup again give you the option to uninstall? Seem to remember that from long ago but might be wrong (might only be repair).

> **techtabu said:**
> Uninstall from where? Why are you asking uninstalling Office in Ubuntu forum?
If you read his other threads, you could have known that he's using wine (or maybe crossover office) :D

---

### Post by amjjawad on 2011-07-31
> **JacquesPotter said:**
> How do I uninstall MS Office 2003?

[http://www.msofficeforums.com/](http://www.msofficeforums.com/)

---

### Post by amjjawad on 2011-07-31
> **Wim Sturkenboom said:**
> If you read his other threads, you could have known that he's using wine (or maybe crossover office) :D

I did and he is supposed to post it there or provide at least a link to his other thread so that people who did not read his other threads will know what's going on :)

---

### Post by JacquesPotter on 2011-07-31
Sorry everyone about not "linking" my other threads. How do I do this and I'll be sure to do it in the future. Also, I noticed that this thread isn't showing on my subscribed threads. Did I do something wrong? Any help is appreciated by the experts.

---

### Post by JacquesPotter on 2011-07-31
Not to sound unappreciative,but I am in the Ubuntu forum so I thought that it would have been obvious that I wanted to uninstall it from Ubuntu. Sorry for any confusion.

---

### Post by jtarin on 2011-07-31
Open up a terminal window and type the command below.

```
wine uninstaller
```

What this will do is open up a program similar to the Windows add/remove programs control panel, allowing you to uninstall applications from a Wine installation. Running uninstall programs directly via Wine should also work normally. Alternatively, you could also simply delete the folder of the application. However, as when done in Windows, this method will be unclean and will not remove the program's configuration from the Wine registry like using an uninstaller will.

---

### Post by JacquesPotter on 2011-07-31
> **jtarin said:**
> Open up a terminal window and type the command below.

```
wine uninstaller
```

What this will do is open up a program similar to the Windows add/remove programs control panel, allowing you to uninstall applications from a Wine installation. Running uninstall programs directly via Wine should also work normally. Alternatively, you could also simply delete the folder of the application. However, as when done in Windows, this method will be unclean and will not remove the program's configuration from the Wine registry like using an uninstaller will.
Thanks. But there must be a problem with my Wine Uninstaller. I open it up and click the "Microsoft Office Professional..." and the add/remove programs window kinda blinks but nothing happens to MS Office. Any other suggestions?

---

### Post by colin.p on 2011-07-31
By mistake I installed MS Office 2007 in wine (I wanted to install it in XP running in VB). I went through the uninstall through wine, but it would not uninstall properly, so I removed it manually through wine's "C" drive and everything remotely sounding like office. There is still references to office in  "add/remove programs" that I can't get rid of, but I find it easier to manually remove windows software in wine anyway.
BTW, it works fine in a virtual XP, that is the few times I actually use it. I actually prefer Open-office.

---

### Post by JacquesPotter on 2011-07-31
> **colin.p said:**
> By mistake I installed MS Office 2007 in wine (I wanted to install it in XP running in VB). I went through the uninstall through wine, but it would not uninstall properly, so I removed it manually through wine's "C" drive and everything remotely sounding like office. There is still references to office in  "add/remove programs" that I can't get rid of, but I find it easier to manually remove windows software in wine anyway.
BTW, it works fine in a virtual XP, that is the few times I actually use it. I actually prefer Open-office.
I'm really knew to this stuff so I don't feel safe enough to go through randomly deleting things. 

Also, how do you work the Virtual MS. Part of my problem is that I lost my MS XP disks when I moved (yes I have the licence and the receipt) and I just don't have the money to pay for a new OS. I wish I did, this Ubuntu is really confusing for a newbie like me. That's why I wanted to be able to work with the programs I'm familiar with while I get to know Ubuntu. Now I'm forced to jump in with weights on my legs.

---

### Post by jtarin on 2011-07-31
> **JacquesPotter said:**
> Thanks. But there must be a problem with my Wine Uninstaller. I open it up and click the "Microsoft Office Professional..." and the add/remove programs window kinda blinks but nothing happens to MS Office. Any other suggestions?If you have no other MS applications installed in WINE you might just uninstall WINE then delete the /home/username/.wine folder (a hidden folder in your /home/username directory) then re-install wine.

---

### Post by JacquesPotter on 2011-07-31
> **jtarin said:**
> If you have no other MS applications installed in WINE you might just uninstall WINE then delete the /home/username/.wine folder (a hidden folder in your /home/username directory) then re-install wine.

OK, I think you're right. Where do I go to uninstall wine?

---

### Post by colin.p on 2011-07-31
If you have the license with key, all you need is the install cd. If you can borrow one from a friend, just put your license key in, remember it is the license, not the media, that is what MS gets into a tither about.
There are of course lots of ways to get what you need, but may not be entirely "kosher". But that is a subject that would be best served elsewhere.
I am not entirely sure, but you could remove wine, through synaptic, then remove the hidden wine folder in your "home", then re-install wine and start all over.
Now as far as using XP in a Virtual-box, it works just fine, and will allow you to use all your win programs within windows.

edit, jtarin beat me to it.

---

### Post by themusicalduck on 2011-07-31
I read your other thread.

If you want to use Crossover to install Office, I believe that Crossover does not use the same Windows files that wine uses. Every time you install an application in Crossover, it creates a new 'bottle' which means recreating the Windows files specifically for that application (similar to wine prefixes). So it might not be necessary to remove everything related to the original office installation, since it shouldn't interfere with it.

> **JacquesPotter said:**
> OK, I think you're right. Where do I go to uninstall wine?

Uninstall it from the Software Centre.


As you are a new user coming from Windows here's some more advice for you -

Try not to get too much into using Wine. It seems like the first thing a new user does when getting Ubuntu is install Wine and try to use all of their old Windows apps. In theory Wine seems like a brilliant idea, but in practice it almost never works as well as you hope.

I say this because I did exactly the same thing when I first started using Ubuntu, and got frustrated at all the fiddling I had to do to get things to work sort of well.

Now I just use Wine very occasionally only when I have to and using my computer is much simpler and more pleasant.

If you want to use Windows apps all the time, then it's best to use Windows. If you want to use Linux, then find the Linux apps that do what you need.

---

### Post by JacquesPotter on 2011-07-31
> **colin.p said:**
> If you have the license with key, all you need is the install cd. If you can borrow one from a friend, just put your license key in, remember it is the license, not the media, that is what MS gets into a tither about.
There are of course lots of ways to get what you need, but may not be entirely "kosher". But that is a subject that would be best served elsewhere.
I am not entirely sure, but you could remove wine, through synaptic, then remove the hidden wine folder in your "home", then re-install wine and start all over.
Now as far as using XP in a Virtual-box, it works just fine, and will allow you to use all your win programs within windows.

edit, jtarin beat me to it.

Oye, so many new terms. What is synaptic?
And, I've been looking for someone to borrow the xp disc's from for over two weeks and no luck. :(  So, the next question is do I need the cd's to be able to use Virtual-box. I'm assuming I do.

Also, I'm not sure of the rules.. can I provide you with an email addy to discuss other options to solve me MS Office problem?

---

### Post by jtarin on 2011-07-31
Synaptic: Gnome Menu>Systems>Administration>Synaptic.
Or open a terminal and type ```
gksudo synaptic
``` and provide your password.
Then use the Synaptic search box, search for wine and then right-click the entry and choose "remove completely". Before you re-install make sure the folder I mentioned in my last post is deleted.
As an aside...I have MS Word 2007 installed but I used CrossOver to do it. CrossOver has its own implementation of WINE so you don't need to install it separately.
As to VirtualBox.....yes you need the install CD of the OS you want to run.

---

### Post by colin.p on 2011-07-31
Synaptic is the repository for software, or at least the way to access the software. Software Center is basically the same thing.
Just type in "wine" and it will flag it for you, then mark it for removal. If you want to re-install wine later, don't be too worried about removing every trace, just remove the hidden wine folder in your home (a good idea may be to copy that folder somewhere else, just in case there is something there you want).
Virtual box is a virtual drive that you install OS's into. You need the OS install media, or an ISO, to be able to install in Virtual Box. However, you will need to do a fair bit of research to find out how to use it. It's not hard, but something that shouldn't be done in an hour or so, from scratch.

---

### Post by JacquesPotter on 2011-07-31
There are several "packages" with Wine. Do I need to select them all?

---

### Post by jtarin on 2011-07-31
No....only the ones that are designated/marked as being installed. A right-click will tell you if its uninstallable.....if you don't know.There is a column to the left with a vertical menu if you click "installed applications" then search for Wine it will show those.

---

### Post by colin.p on 2011-07-31
I have 5 things that show up, when I type in wine. If you are intending to re-install wine later, then choose "wine 1.3" (that's what I have), your version number may be different. Synaptic will remove what needs to be removed, if something remains checked in synaptic, don't worry, just leave it. However, again, it is the hidden wine folder (.wine) in your home folder that needs to be removed. You access it by hitting the "crtl" button and the "h" button at the same time to view hidden folders.
CAVEAT removing that hidden folder will also remove any other program that that you installed in wine, so do the usual back-up and re-install that software once you re-install wine.

---

### Post by JacquesPotter on 2011-07-31
> **jtarin said:**
> Synaptic: Gnome Menu>Systems>Administration>Synaptic.
Or open a terminal and type ```
gksudo synaptic
``` and provide your password.
Then use the Synaptic search box, search for wine and then right-click the entry and choose "remove completely". Before you re-install make sure the folder I mentioned in my last post is deleted.
As an aside...I have MS Word 2007 installed but I used CrossOver to do it. CrossOver has its own implementation of WINE so you don't need to install it separately.
As to VirtualBox.....yes you need the install CD of the OS you want to run.

OK, Now how do I find and delete the folder you mentioned earlier? It's still showing under the Applications drop down menu.

---

### Post by colin.p on 2011-07-31
The hidden folder ".wine" is in your home folder. What is listed in the applications menu can be removed by right clicking on the application menu, clicking "edit menu>wine>programs", select the offending item then unclicking it. Then you will no longer see it.

---

### Post by JacquesPotter on 2011-07-31
So now I should re-install MS Office 2003 with Crossover instead? Any specific instructions?

---

### Post by colin.p on 2011-07-31
I've never used crossover, it is a commercial product, but they have a trial. You would have to check it out to see how it will let you use it.
Lots of people swear by it, but I don't know anything about it (too cheap, I don't usually pay for sw, if there is a free alternative)
Someone will probably be by shortly to help with that.

---

### Post by JacquesPotter on 2011-07-31
> **colin.p said:**
> I've never used crossover, it is a commercial product, but they have a trial. You would have to check it out to see how it will let you use it.
Lots of people swear by it, but I don't know anything about it (too cheap, I don't usually pay for sw, if there is a free alternative)
Someone will probably be by shortly to help with that.

OK sounds good. Either way. This thread has been solved. I will go back to my other two threads and work on the Crossover from there. 

THANK YOU EVERYONE FOR YOUR HELP!! Especially for putting up with my ignorance.

---

