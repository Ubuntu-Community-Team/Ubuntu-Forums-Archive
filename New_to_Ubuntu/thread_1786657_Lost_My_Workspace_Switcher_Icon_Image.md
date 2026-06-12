---
title: "Lost My Workspace Switcher Icon Image"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by stevedude on 2011-06-19
Hi all,

For whatever reason, I lost my icon image on Unity to switch workspaces. What I mean is, the icon is there on the launcher, but it is a bland looking box, not the default icon image used to show the "Workspace Switcher"

I figured out the theme I am using is causing this. Is there a way to edit a file so that this shows a particular icon image?

Enclosed is a screenshot. I'm not sure what file needs to be edited if anyone can help with this, I would appreciate it - Thanks!

---

### Post by Peter09 on 2011-06-20
Yeah - I have the same problem - but I think I am using a different theme to you.

---

### Post by computerandu on 2011-06-20
I too have the same problem...did not notice until i saw this post

---

### Post by cracker89 on 2011-06-20
You know, you really ought to keep in mind that someone put that search box up there for a reason, unless you've already seen this :P

[http://ubuntuforums.org/showthread.php?t=1744736](http://ubuntuforums.org/showthread.php?t=1744736)

Hope it helps. 

Cheers.

---

### Post by compmodder26 on 2011-06-20
> **cracker89 said:**
> You know, you really ought to keep in mind that someone put that search box up there for a reason, unless you've already seen this :P

[http://ubuntuforums.org/showthread.php?t=1744736](http://ubuntuforums.org/showthread.php?t=1744736)

Hope it helps. 

Cheers.

Don't think that's the OP's problem.  It appears that functionality is fine, but the icon in the launcher is not correct.  As the OP pointed out, this most likely due to the icon theme he is using.

---

### Post by stevedude on 2011-06-20
> **cracker89 said:**
> You know, you really ought to keep in mind that someone put that search box up there for a reason, unless you've already seen this :P

[http://ubuntuforums.org/showthread.php?t=1744736](http://ubuntuforums.org/showthread.php?t=1744736)

Hope it helps. 

Cheers.

Thanks compmodder26, however, this is a totally different issue than the other thread and I typically search before I post to be a good Internet citizen :)

I'm looking for the file and/or icon I need to edit/change in order to change the look of the Workspace Switcher icon. I have full functionality, and my current icon set (Buuf) is causing the issue. I'm sure it's possible to make the icon change, I just don't know how to go about that.

---

### Post by cracker89 on 2011-06-20
> **compmodder26 said:**
> Don't think that's the OP's problem.  It appears that functionality is fine, but the icon in the launcher is not correct.  As the OP pointed out, this most likely due to the icon theme he is using.

Well, my apologies, Sir.

I misread I suppose. Darn burning eyes.. [https://bugs.launchpad.net/unity-2d/+bug/751450](https://bugs.launchpad.net/unity-2d/+bug/751450)
EDIT: Altho I doubt theres much in that link, you might get a start. too tired to read right now. Cheers.

---

### Post by stevedude on 2011-06-20
Well, I did find this post: [http://scotthomas.wordpress.com/2011/01/04/howto-change-icons-in-ubuntu-netbook-unity-launcher/](http://scotthomas.wordpress.com/2011/01/04/howto-change-icons-in-ubuntu-netbook-unity-launcher/)

This will help those looking to change application icons, but it still doesn't address my issue with a system icon, because I can't find the related file needed for Workspace Switcher.

That link is a very good start and I hope it helps others. At least I know I need to find a *XML* or the associated .*desktop* file. I'll keep looking around my system to see if I can find it, if someone locates theirs, please post so I can have some peace - lol

---

### Post by dFlyer on 2011-06-20
Did you change your default system set? If so check those icons to see if an icon is included for the Workspace switcher.

---

### Post by cracker89 on 2011-06-20
Hmmm.. I hear theres a software called [confity]("http://www.makeuseof.com/tag/easily-configure-ubuntus-unity-interface-confity-linux/") that has some use in this regard, although I wonder if it'll fit your need. 

Also, a lil research led me to this, which i share for the OP's benefit and further research... :-
[http://ubuntuforums.org/showthread.php?t=1741364](http://ubuntuforums.org/showthread.php?t=1741364)

---

### Post by JASONFUSARO on 2011-06-20
Hello 
I wonder if you can help me out with a problem, I was editing a reply and I used a go back one page to read something and can't get back to that edit page, I had alot of stuff typed and I really need to get it back, is it lost for good or is there some option I can use to get back to the edit page??

---

### Post by dFlyer on 2011-06-20
> **JASONFUSARO said:**
> Hello 
I wonder if you can help me out with a problem, I was editing a reply and I used a go back one page to read something and can't get back to that edit page, I had alot of stuff typed and I really need to get it back, is it lost for good or is there some option I can use to get back to the edit page??

Please don't hijack the thread, it makes it really confusing.

---

### Post by stevedude on 2011-06-20
Thanks dFlyer and cracker89 for taking the time to provide input. 

One of the 1st things I checked was the Buff icon set to see if there was a Workspace Switcher icon - There is not.

Confity seems to utilize what Compiz already has for Unity and adds the ability to add "Quicklists", both don't meet the needs I have, sorry to say.

I have done more researching and came across gconf-editor. [ALT-F2, type gconf-editor]

You have to navigate to /apps/panel/default_setup/applets/workspace_switcher  (phew!)
Refer to screenshot #2

There are keys to use a custom icon (checkbox) and the path for the custom icon. I will try that and report back. Fingers are crossed!

---

### Post by stevedude on 2011-06-20
No go trying to add a custom icon path...

gconf-editor states: "The location of the image file used as the icon for the object's button. [COLOR=Red]This key is only relevant [/COLOR]if the object_type key is "**drawer-object**" or "**menu-object**" and the use_custom_icon key is true. "

Well I have the custom icon key set to true (is checked), and I rebooted the system after making the changes. No luck

I'm really thinking I need to find that XML file and/or the .desktop file to make any changes.

This is pretty frustrating....:(

---

### Post by stevedude on 2011-06-20
I made it waaaay too complicated!

I revisited the replies and I finally realized what DFlyer was saying. I just copied a "workspace-switcher.png" icon file from another icon set into the buuf icon set > rebooted> and all is well as shown in the enclosed pic.

Thanks everyone!

---

### Post by morrisjones on 2011-07-19
Wait wait ... explain that a little further.

I too have this problem. I found the right icon here: /usr/share/icons/unity-icon-theme/apps/48/workspace-switcher.png

But what/where is the buuf icon set?

Mojo

---

