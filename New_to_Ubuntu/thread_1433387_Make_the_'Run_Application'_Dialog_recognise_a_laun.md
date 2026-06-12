---
title: "Make the 'Run Application' Dialog recognise a launcher"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by sabrehagen on 2010-03-19
Today is my first day running Ubuntu on my netbook, and I am really liking it! I've always used Windows and haven't liked previous versions of Ubuntu, but I'm finding 9.10 much more likable.

I have been using the Alt-F2 shortcut to open the Run Application Dialog to launch most of my programs. I just installed Songbird, but unlike windows where the installer extracts all the files and creates shortcuts on your desktop, you manually had to extract the files and then create a launcher. The settings on my launcher are:

Name: Songbird
Command: Songbird/songbird

I have put the launcher in my /home/<username>/ directory, but when I use the Run Application dialog there is no autocomplete after typing 'son' (for songbird) and if I type songbird and press enter I get the message "Could not open the location file:///home/jack/songbird, no such file or directory'. 

Essentially, my question is how do I make it so the Run Application dialog will suggest/search for launcher files I have made?

Thanks!


sabrehagen

P.S. Is there are shortcut to open the file browser?

---

### Post by Temposs on 2010-03-19
hi sabrehagen,
   I'm glad Ubuntu meets your approval this time around. It is definitely evolving and maturing :-)

So, it's true Ubuntu doesn't create desktop launchers for you, but it usually does create a launcher in the Applications menu. In general, it's better to not have launchers on the desktop, because the desktop is meant as a temporary holding place for random files you're currently working with that you need to keep at the front of your attention or you haven't had time to file away. You know, like how most people treat a physical office desktop. It shouldn't be filled with launchers, and it should ideally be straightened up every now and then. 

The correct place for launchers in Ubuntu besides the menu is on the panels.

So, I think if you go to Applications->Sounds & Video, then there should be a Songbird entry there. You can drag that launcher onto a panel(it will stay in the menu as well). That way you can have the launchers you want visible at all times with easy access.

In terms of auto-complete with the Run Application dialog, the auto-complete may only work with launchers in the menu(which should include songbird if you ran its installer). To make a new launcher in the menu, right click on the menu and click Edit Menu. Then you can create launchers wherever you want in the menu.

---

### Post by Temposs on 2010-03-19
Also, for the keyboard shortcuts, if you go to System->Prefs->Keyboard Shortcuts, you can set your own shortcut for opening the file browser.

Lastly, since you seem to like the Run Application dialog, I want to point you in the direction of Gnome Do, which is an excellent application for doing all sorts of tasks from a similar kind of interface, i.e., a small box that pops up where you type something in. It's much more versatile than the Run Application dialog, and may suit your needs better.

---

### Post by mcduck on 2010-03-19
> **sabrehagen said:**
> Today is my first day running Ubuntu on my netbook, and I am really liking it! I've always used Windows and haven't liked previous versions of Ubuntu, but I'm finding 9.10 much more likable.

I have been using the Alt-F2 shortcut to open the Run Application Dialog to launch most of my programs. I just installed Songbird, but unlike windows where the installer extracts all the files and creates shortcuts on your desktop, you manually had to extract the files and then create a launcher. The settings on my launcher are:

Name: Songbird
Command: Songbird/songbird

I have put the launcher in my /home/<username>/ directory, but when I use the Run Application dialog there is no autocomplete after typing 'son' (for songbird) and if I type songbird and press enter I get the message "Could not open the location file:///home/jack/songbird, no such file or directory'. 

Essentially, my question is how do I make it so the Run Application dialog will suggest/search for launcher files I have made?

Thanks!


sabrehagen

P.S. Is there are shortcut to open the file browser?
The autocompletion for commands doesn't really care about launchers or menu entries, it simply looks for executable files that are in locations defined in your user's path variable.

What I recommend is that you create a directory called "bin" in your home directory, and put the executable file there (you can also just link it there, if you want to). That directory is automatically included in your path if you just create the dir, so any executable files you put there you can start from terminal by simply typing their name, exactly like any system commands and things installed through package management.

Of curse you could also put (or link) the executable in /usr/bin if you want to make it available for all users of the system and not just your own.

---

### Post by sabrehagen on 2010-03-19
> **Temposs said:**
> hi sabrehagen,
   I'm glad Ubuntu meets your approval this time around. It is definitely evolving and maturing :-)

The correct place for launchers in Ubuntu besides the menu is on the panels.

So, I think if you go to Applications->Sounds & Video, then there should be a Songbird entry there. You can drag that launcher onto a panel(it will stay in the menu as well). That way you can have the launchers you want visible at all times with easy access.

In terms of auto-complete with the Run Application dialog, the auto-complete may only work with launchers in the menu(which should include songbird if you ran its installer). To make a new launcher in the menu, right click on the menu and click Edit Menu. Then you can create launchers wherever you want in the menu.

I was unfamiliar with the install process on Ubuntu so I looked at the FAQ on Songbird's website and they recommended downloading the zip file and extracting to your home folder. From there it was recommended that you created a launcher for the file. As a result of this, no installer file was run and thus there is no icon in the Sound and Video menu. I was actually trying to place a launcher in there before posting here.

In Windows, there is a Start Menu folder and you can place shortcuts to executable files in there and they will show up in your start menu. Is there a similar think I can do in Ubuntu?

> **mcduck said:**
> The autocompletion for commands doesn't really care about launchers or menu entries, it simply looks for executable files that are in locations defined in your user's path variable.

What I recommend is that you create a directory called "bin" in your home directory, and put the executable file there (you can also just link it there, if you want to). That directory is automatically included in your path if you just create the dir, so any executable files you put there you can start from terminal by simply typing their name, exactly like any system commands and things installed through package management.

Of course you could also put (or link) the executable in /usr/bin if you want to make it available for all users of the system and not just your own.

Thanks mcduck, I tried creating a bin folder and linking the the executable file there but no luck. Where can I edit the path variables?

> **Temposs said:**
> Also, for the keyboard shortcuts, if you go to System->Prefs->Keyboard Shortcuts, you can set your own shortcut for opening the file browser.

Lastly, since you seem to like the Run Application dialog, I want to point you in the direction of Gnome Do, which is an excellent application for doing all sorts of tasks from a similar kind of interface, i.e., a small box that pops up where you type something in. It's much more versatile than the Run Application dialog, and may suit your needs better.

I'll check out gnome do - sounds great.

Also, I just wanted to say, one of the things that has made Ubuntu so appealing to me is the speed at which it runs on my netbook. Windows loads slightly quicker, but starting programs like firefox and navigation through folders started to feel lethargic. Ubuntu is snappy in both respects which is great on a low powered netbook! Finally, the interface and look of a software package is important to me. I love running Windows 7 on my powerful desktop because it looks so beautiful. When I had seen Ubuntu running 2 years ago, it looked blocky and unattractive. Now, the interface is more sleek, and with programs like compiz, the user experience is much more visually pleasing. I only have the basic settings on; things like wiggly/jelly windows just look silly to me, but the basics are classy.

Thanks for all your help guys!


sabrehagen

---

### Post by mcduck on 2010-03-19
> **sabrehagen said:**
> 

Thanks mcduck, I tried creating a bin folder and linking the the executable file there but no luck. Where can I edit the path variables?

You need to log out and back again after creating the ~/bin directory.

The best place to add new directories to your path would be ~/.profile (which is where the ~/bin is already defined)

---

