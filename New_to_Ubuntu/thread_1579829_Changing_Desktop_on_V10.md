---
title: "Changing Desktop on V10"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by dpowell7299 on 2010-09-22
I had added this post a few days ago but it went missing....

Anyway,

I'm trying to get my daughter to upgrade her Ubuntu but the new version's desktop presentation is clunky (mostly in her eyes).

She likes the Windows like desktop view with the ability to put a few programs and folders on the desktop and get to the other programs via a title bar along the top.

The V10 puts categories along the left and fills the desktop with huge icons for each program in that category.

I've looked all over and I can't find how I setup her windows look before and I can't find how to change it now.

Any help please?

Don

---

### Post by JRBye on 2010-09-22
If you right click on an icon on the Desktop you can get to the 'Resize Icon' option. You can shrink them down if you like. Also if everything is too big go to System->Preferences->Monitors and you can adjust the resolution from there. There is a program called Compiz that you can use to alter a lot of the look and functionality of the desktop.

To install that run the following command in Terminal or search Compiz in the Software Center
sudo apt-get install compiz compizconfig-settings-manager -y

 Ubuntu Tweak also makes many of the changes easier to do.

To install that run the following command in Terminal or seatch Ubuntu Tweak in the Software Center
sudo apt-get install ubuntu-tweak -y

Overall though I would just ask her to give it a try. It might just take some time to get used to the interface. You can do a lot to alter it but it will always be Linux.

Good luck!

J.R.

---

### Post by dpowell7299 on 2010-09-22
Thanks,  I'll try that.

But I actually agree with her.  I have a cool picture that I prefer to look at instead of a bunch of icons based on whatever category I'm on.

With the Windows desktop, it is a lot cleaner presentation (in my opinion).  Not to mention the fact that it makes it MUCH easier for someone to convert to Linux if it looks like what they expect ))

But mostly it is just the desire to see a background image without covering the screen with icons... Even if they ARE in my Favorites Category ))

Also, it can be done on V9 (I think, can't recall which one she has now) so it should exist on the latest too.

Don

---

### Post by coffeecat on 2010-09-22
In all honesty I'm not quite sure what you're complaining about. If you  want icons on your desktop for application launchers and folders, then  you can vary their size the way JRBye suggests. But if you want a clean  desktop then the answer is simple: don't put anything on it. Ubuntu  ships with an empty desktop. As you've discovered, application launchers  can be put on the upper panel (what you call the title bar), and did you  know that you can add folders to the Places menu? Simply open a Nautilus  browser window, navigate to the folder you want to add and Bookmarks  > Add Bookmark.

> **dpowell7299 said:**
> The V10 puts categories along the left and  fills the desktop with huge icons for each program in that  category.

What do you mean by categories? The icons don't have to be huge.

> **dpowell7299 said:**
> With the Windows desktop, it is a lot cleaner  presentation (in my opinion).  Not to mention the fact that it makes it  MUCH easier for someone to convert to Linux if it looks like what they  expect ))

This is a misperception. If you want a Windows person to convert to  something that looks and feels like Windows, then let them convert to  Windows. Most people who convert to Linux are trying to get away from  the Windows look and feel. Make Linux like Windows and you'll scare them  away. In fact, the gnome desktop which Ubuntu uses is very much more  configurable than Windows (or MacOS for that matter), so much so  that  you can make it look just the way you want. If you don't know how,  simply ask here. People are very friendly. :smile:

> **dpowell7299 said:**
>  But mostly it is just the desire to see a  background image without covering the screen with icons... Even if they  ARE in my Favorites Category ))

OK. Don't cover it in icons then. :wink:

> **dpowell7299 said:**
> Also, it can be done on V9

I need to pick you up on terminology. Although people here will  understand - nearly - what you mean by V9 and V10, you need to know that  there are two major releases a year and that these differ  significantly. If you need help, it helps you to be precise about which  release. Releases are numbered according to year and month of release -  hence 10.04 was released in April of 2010. 10.10 will be released early  next month. Releases go by an alliterative code name. Some people are  irritated by this; others like it. The 'V9' and 'V10' releases are/were:

9.04 = Jaunty Jackalope
9.10 = Karmic Koala
10.04 = Lucid Lynx
10.10 = Maverick Meerkat.

And if the names irritate you, just tell yourself that they are simply a  piece of whimsy, but it helps to know them because you'll see people  posting "I'm running Karmic" or whatever.

Good luck with Ubuntu and I hope you get the desktop to your and your  daughter's liking. If you can't, post a screenshot and describe what is  wrong in your eyes and someone should be able to help you.

---

### Post by dpowell7299 on 2010-09-22
This is what I'm talking about.  This was the was 10 came up when I upgraded.  The things along the left I thought they called Categories but I could be wrong about that ))

I'll try the suggestions and see what I can do.

I've been on Ubuntu for a couple or 3 years and UNIX for 30, it is just sometimes difficult to find the answer when you are not sure what to search for :)  After all, "Desktop" tends to bring back lots of things I was not looking for ))

Don

---

### Post by spiky001 on 2010-09-22
Thats the netbook remix is,nt it will the desktop version be any good?

---

### Post by coffeecat on 2010-09-22
Now I see what you mean. Unless you're running a netbook you've installed the wrong version! That's the netbook remix version especially for tiny screens. It makes sense on a little screen. If you've got that on a desktop monitor, no wonder it looks weird. I sympathise. :)

What hardware are you using?

---

### Post by dpowell7299 on 2010-09-22
Yep, I'm on a netbook.  Actually I use an external monitor too but even with the 7" screen, the other view would be fine.

I chose the netbook remix because I was concerned that the regular version would not be optimized and as anyone with a netbook knows, they are portable and great usefulness but not very powerful :)

Any idea if the standard version would work OK with a netbook?

Or just be able to change or add a new desktop presentation would be fine ))

Don

---

### Post by coffeecat on 2010-09-23
Someone will probably correct me, but I believe the netbook remix has no optimisation other than the special desktop interface. In fact I believe it just sits on top of the ordinary vanilla gnome desktop. In versions prior to 10.04, there was a desktop switcher so that you could switch between the netbook interface and a standard gnome desktop. But this was removed for some reason in 10.04 - I believe.

Tbh I've hardly used my little Asus 701 for ages so I'm a bit rusty about all the details of the netbook remix. Certainly at one time I did run a standard gnome version of Ubuntu (Jaunty I think) on it and it ran just fine. Er - ambled just fine. :)

There should be a way of removing the netbook interface. I would guess simply uninstalling the netbook packages. I'm not in Ubuntu atm so I can't check the package manager for you. Perhaps someone else will advise. Or you could try running the standard Ubuntu release from a live USB and seeing how that fares. It will run slower, of course, but you will be able to see if everything does run.

One last thought. If you don't like the nbr interface then fair enough. I think it's a love it or hate it thing. But it has been designed with a lot of thought especially for the small screen. Though it must look absurd on a large monitor.

---

### Post by QLee on 2010-09-23
[QUOTE=dpowell7299]...
I've been on Ubuntu for a couple or 3 years and UNIX for 30, it is just sometimes difficult to find the answer when you are not sure what to search for :)  After all, "Desktop" tends to bring back lots of things I was not looking for ))
...[/QUOTE]
Yeah, don't you just hate it when that happens? However, searching the Ubuntu forums with the additional keyword, netbook (since that's what you're using) I get several hits, see if one of these three might be useful for you.
[http://ubuntuforums.org/showthread.php?t=1576740&highlight=netbook+desktop](http://ubuntuforums.org/showthread.php?t=1576740&highlight=netbook+desktop)
[http://ubuntuforums.org/showthread.php?t=1565138&highlight=netbook+desktop](http://ubuntuforums.org/showthread.php?t=1565138&highlight=netbook+desktop)
[http://ubuntuforums.org/showthread.php?t=1561957&highlight=netbook+desktop](http://ubuntuforums.org/showthread.php?t=1561957&highlight=netbook+desktop)

---

### Post by dpowell7299 on 2010-09-23
QLee, thanks for the links.  It always helps with the right combination of search keywords ))  The articles helped alot.

CoffeeCat,  I don't doubt that a lot of thought went into the interface but my eyesight is awesome and I like small icons and type.  I just wish they had an easy way to switch it.

I'm the opposite of a security nut, so I have auto-login turned on.  That means I either have to re-install Ubuntu Desktop or turn off Auto-Login so I have the option to switch at login.

Oh well, I can't really complain, those Ubuntu programmers are still WAY better than I am :)

Don

---

### Post by dpowell7299 on 2010-09-23
Changing it to Gnome from the login fixed it.  Now I can see my sweetie on the screen again and my daughter can upgrade and still see her background.

Thanks for all the help, I have been looking for about 3 months for this.

Don

---

### Post by QLee on 2010-09-24
[QUOTE=dpowell7299]Changing it to Gnome from the login fixed it.  Now I can see my sweetie on the screen again and my daughter can upgrade and still see her background.

Thanks for all the help, I have been looking for about 3 months for this.

Don[/QUOTE]
Great. We have served as a good example to users looking for help, illustrating how useful a forum search can be. Many times a forum search gets one to the answer faster than waiting for someone to reply to a post. Keyword choice is good foo to cultivate.

Since you have over 30 yrs. experience, between us we have over 60 yrs. experience and, at this point, serving as a good example is probably most of our value to society.

---

