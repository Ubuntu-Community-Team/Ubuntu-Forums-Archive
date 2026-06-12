---
title: "Finally got Iron - sort of - need help installing correctly"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by ClientAlive on 2011-04-21
Wow! Just spent the last 3+ hours trying to find the Iron web browser and get it on my machine. Someone on the forum gave me a link to the company's web site and I finally found the link to the Linux version and the tar.gz file for it. (Tiny little link near the bottom of the page).

So I'm so new to this I didn't even understand what a tar file is or what to do with it. Now, I got it extracted on my desktop and went into the folder; and, though there is no readme in there, found out what to do from the internet - sort of.

It turns out that double clicking the icon in the folder launches the app but that's kind of a screwy way to have to use it. I tried to launch it from the launcher/ bar by clicking "keep in launcher" but it does not launch. The icon will stay in the launcher but it will not launch the app.

Does anyone know how to really install something like this? I mean install it like the other normal apps? I want it to show up in applications and to be able to keep it in the launcher and actually have it work.

Thanks in advance.

Jake

---

### Post by ClientAlive on 2011-04-21
I'm trying to follow the instructions given in old post but the commands this guy gives you are not correct or something. I tried to improvise but I'm guessing I'm only maybe half way there. I'm stuck. I'm not really sure if one command I fan may have done something extra or unneeded. I attached the output from the terminal that shows everything that was done so far.

Can someone please help?

---

### Post by LewRockwellFAN on 2011-04-21
> **ClientAlive said:**
> It turns out that double clicking the icon in the folder launches the app but that's kind of a screwy way to have to use it. . . .
Does anyone know how to really install something like this? I mean install it like the other normal apps? I want it to show up in applications and to be able to keep it in the launcher and actually have it work.
Jake
You may get a better answer before I finish sloooooowly typing this one but I'll give in an uneducated shot in the meantime. About that "icon" you double click to get the program to run. It might help to take a look at properties with a right click. You can try making a launcher and put the exact path and filename of it or of some file it points to in the launcher and putting the launcher in the panel above the desktop. Or to put it in the Applications menu right click on "Applications", click "edit menus", "new item", and then fill in the command field with the path and file name, including extension, of the of the script (somename.sh, usually) or other executable the "icon" points to if it is some sort of launcher or the thing itself if it is an executable. What interested you in "Iron"?

---

### Post by ClientAlive on 2011-04-21
> **LewRockwellFAN said:**
> You may get a better answer before I finish sloooooowly typing this one but I'll give in an uneducated shot in the meantime. About that "icon" you double click to get the program to run. It might help to take a look at properties with a right click. You can try making a launcher and put the exact path and filename of it or of some file it points to in the launcher and putting the launcher in the panel above the desktop. Or to put it in the Applications menu right click on "Applications", click "edit menus", "new item", and then fill in the command field with the path and file name, including extension, of the of the script (somename.sh, usually) or other executable the "icon" points to if it is some sort of launcher or the thing itself if it is an executable. What interested you in "Iron"?



Well the thing is like lightning fast; and, I hear, it's like chrome with a little opera thrown in as far as the features go. I guess it basically is chrome but they did something to make it anonymous and more secure.I've never used chrome but I hear that it reports a lot of things that you do on the internet to the google servers. Supposed to be you can change those settings so it doesn't but I don't tend to trust those sort of things. To me its just another big corporation with an agenda. That's just me though. Bottom line is I wanted to find a great browser and something that's maybe a little different than the mainstream. Iron is about the fastest thing out there and seems to offer some really cool features.

As far as the file type of that icon, I did go into properties and check that out before even starting this thread. It'is an executable file. It's just that I don't understand enough about how the computer system works for that knowledge to do me any good. What you say about making a launcher and all those things sounds really great and it would probably get me what I'm shooting for but I just don't have a concept of what is happening when you do those things.

Everyone is different and maybe for some people that would be ok, but for me I need to understand what is happening so I know what I'm trying to do. It wouldn't have to be some in depth complicated explanation either. Just something real basic but also the concrete, the conceptual and the connections between them. The necessary ingredients for knowledge.

Unfortunately I may end up spending a pretty good chunk of time to gain those things. (And I'm still just talking about one simple thing - installing one specific program - Iron). It's just that learning about things that are so vast is often hard to do and confusing. You don't always see a clear path to where you want to go. You don't always know the right questions to ask or what the right information is to look for. I guess that's what they call the learning curve. Well that's what I'm doing here, on this forum, in this thread - trying to find people who will help me bridge that curve. I know this isn't wikipedia; and, obviously I can't expect anyone to give me a college course. That's not what I'm looking for here anyway. I just wonder sometimes whether people know just how much another person doesn't know.

I did find someone LewRockwellFAN. You're helping me understand it. Thank you and thanks for hearing me out. Yes, it's still about installing Iron and I probably shouldn't have said all this - but, in a general sense, I'm really struggling with this whole switching to Linux thing. It's hard to need to learn so much and at the same time not be able to just take a break and  enjoy the thing you're trying to learn about.

Jake
:-k

---

### Post by mikewhatever on 2011-04-21
For those like myself, who didn't know what Iron browser is and where to get it:
[https://secure.wikimedia.org/wikipedia/en/wiki/SRWare_Iron](https://secure.wikimedia.org/wikipedia/en/wiki/SRWare_Iron)
[http://www.srware.net/forum/viewtopic.php?f=18&t=2293](http://www.srware.net/forum/viewtopic.php?f=18&t=2293)

There is no need to install this browser, because it's provided in a binary form. All you need to do is copy its folder somewhere convenient and run it from there.

To make a launcher for it, create a text file named iron.desktop with the following content:
```

[Desktop Entry]
Name=Iron Browser
Comment=Privacy and Security aren't the same thing
Exec=/home/ClientAlive/iron-linux/iron
Icon=/home/ClientAlive/iron-linux/product_logo_48.png

```

Now, I've assumed above that you are going to run it from the 'iron-linux' folder, located in your home folder, and that your user name is ClientAlive. Adjust if needed.

If you use Unity (11.04), drag and dropping that file to the Unity launcher should add it to the launcher.

---

### Post by ClientAlive on 2011-04-21
> **mikewhatever said:**
> For those like myself, who didn't know what Iron browser is and where to get it:
[https://secure.wikimedia.org/wikipedia/en/wiki/SRWare_Iron](https://secure.wikimedia.org/wikipedia/en/wiki/SRWare_Iron)
[http://www.srware.net/forum/viewtopic.php?f=18&t=2293](http://www.srware.net/forum/viewtopic.php?f=18&t=2293)

There is no need to install this browser, because it's provided in a binary form. All you need to do is copy its folder somewhere convenient and run it from there.

To make a launcher for it, create a text file named iron.desktop with the following content:
```

[Desktop Entry]
Name=Iron Browser
**Comment= wrong place for you to put that. Try being polite. Thank you for your help.**
Exec=/home/ClientAlive/iron-linux/iron
Icon=/home/ClientAlive/iron-linux/product_logo_48.png

```

Now, I've assumed above that you are going to run it from the 'iron-linux' folder, located in your home folder, and that your user name is ClientAlive. Adjust if needed.

If you use Unity (11.04), drag and dropping that file to the Unity launcher should add it to the launcher.


Thanks. Got it.

---

### Post by mikewhatever on 2011-04-21
I know, but it's hard to be very polite when reading something like this:
> SRWare Iron: The browser of the future - based on the free Sourcecode "Chromium" - without any problems at privacy and security

IMHO, the above statement is preposterously ridiculous, but perhaps I am exaggerating, and the company simply needs to look for another web master.

---

### Post by LewRockwellFAN on 2011-04-21
> **ClientAlive said:**
> **[B]Comment= wrong place for you to put that. Try being polite.**[/B]Wrong thing to carp about. Try some insensitivity training.

---

### Post by ClientAlive on 2011-04-23
> **mikewhatever said:**
> I know, but it's hard to be very polite when reading something like this:

IMHO, the above statement is preposterously ridiculous, but perhaps I am exaggerating, and the company simply needs to look for another web master.


I see. I agree. Sounds like some marketing mumbo jumbo to me. Where did that quote come from mikewhaever?

Btw: I did get everything sorted out with this (except for one teensie weensie thing - but it's not a biggie for now). i like the app a lot but it does seem to have a few bugs. Nothing too annoying though - thankfully.

LewRockwellFAN: I had some trouble doing it the way you mentioned but I did end up getting a shortcut on the desktop by right clicking on the desktop and selecting "Create Launcher" and using that.

I tried to get it so it's only in the launch bar and not on the desktop but haven't figured that one out yet. I tried dragging the shortcut onto the launch bar but no dice. I looked under "System Settings" for something that allows me to put it on the launch bar but again, no dice. I can launch the application and then right click the icon in the launch bar and select "Keep In Launcher" but then if I delete the shortcut on the desktop I lose that too.

Oh well, no biggie I guess.

Thanks a whole bunch for your help guys. Thanks mikewhatever. Sorry if I was a little too sensitive. I apologize.

Jake
:)

---

### Post by mikewhatever on 2011-04-23
The quote was from here: [http://www.srware.net/en/software_srware_iron.php](http://www.srware.net/en/software_srware_iron.php)

As for the launch bar launcher, just keep the file you created. You might want to move it out of the way to, say, /usr/share/applications.

---

### Post by ClientAlive on 2011-04-23
> **mikewhatever said:**
> The quote was from here: [http://www.srware.net/en/software_srware_iron.php](http://www.srware.net/en/software_srware_iron.php)

As for the launch bar launcher, just keep the file you created. You might want to move it out of the way to, say, /usr/share/applications.


Well I never thought of that. Duh!

Thanks mikewhatever. Sounds like a plan.

---

