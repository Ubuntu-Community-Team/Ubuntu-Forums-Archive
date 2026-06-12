---
title: "Using Skype"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by flyfishingphil on 2011-08-14
Just did a clean install of 11.04  and, so far, it seems to be much better than 10.04 or 10.10. May take a little time to "re-learn" the Desktop and how everything works, but that comes with use. Do have 1 question though:

Followed instructions in a different file, went to Software Center, did the thing to get the Skype for "Naughty", installed Skype but don't know where to look for it.

Anybody know where I might need to look to open it up, get signed in, and keep the Icon on the upper bar so I know it's active?

Thanks.

---

### Post by HalfEmptyHero on 2011-08-14
Did you try running it from the terminal? Just type in skype and see what it says.

---

### Post by flyfishingphil on 2011-08-14
> **HalfEmptyHero said:**
> Did you try running it from the terminal? Just type in skype and see what it says.

Just did that and it offered Skype to open. Next question. When I closed Terminal it disappeared. Any idea of where it went? Do I have to keep Terminal open to use it? Is there a way to put it on the Taskbar at the top of the page so I can click it there, if needed?

Worked it just fine in 10.04 but this is a whole new ballgame!

---

### Post by HalfEmptyHero on 2011-08-14
You're using unity right? Hit either alt-f2 or the window key and type in skype and hit enter.

That is expected terminal behavior, nothing to worry about. That was just to make sure your skype was installed and working properly. Using the alt-f2 run dialog will keep it running.

---

### Post by flyfishingphil on 2011-08-14
That brought it up, but where is it? I don't "see" it anywhere so I can't "turn it off" or anything else. Like I said, just installed  11.04 so still trying to figure everything out.

---

### Post by HalfEmptyHero on 2011-08-14
There should be an icon in the top panel, most likely the left most one. If you are signed in it will be green with a check mark, otherwise it will be grey.

---

### Post by flyfishingphil on 2011-08-14
Ubuntu Icon is in upper left corner. Click on that, click on Internet Apps and Skype is showing there. Click on that and it offers "open" window. Enter password and it says it is already open.

Just a thought. Might it work better if I removed and reinstalled but checked the "add to Taskbar" option?

EDIT:

Just clicked around on Skype and saw a tip that said it will not work on a "private network" only on "public networks" where you "pay by the minute". The one I had in 10.04 worked fine. Is the Skype 2.2 beta no longer "free", or do I need to get a different Skype? Is there a "free" Skype that is workable in 11.04?

---

### Post by HalfEmptyHero on 2011-08-14
By left most I meant the left most on the right side. It will probably be next to the network manager icon. I would show you a screenshot, but apparently that doesn't work with the skype icon.

---

### Post by HalfEmptyHero on 2011-08-14
If it's not there, run this command in the terminal:

gsettings get com.canonical.Unity.Panel systray-whitelist

You should something like this:

['JavaEmbeddedFrame', 'Mumble', 'Wine', 'Skype', 'hp-systray', 'scp-dbus-service']

If you don't see 'Skype' in there, then run the following:

gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Mumble', 'Wine', 'Skype', 'hp-systray', 'scp-dbus-service']"

Then log out and log back in. I have to go to work, so I can't help you any more today. Good luck!

---

### Post by flyfishingphil on 2011-08-14
Nope, not there. Shows  shutdown button, name, chat accounts button, time, envelope, volume icon and network icon. Can only reach Skype thru the "alt-f2" and it doesn't offer the shutdown option.

What is the "Unity" you mentioned and does it come with 11.04. Just did some on line checking regarding the "free" Skype and came across something about Unity. Is this something I need to accomplish more in 11.04?

Don't enjoy looking like a total "newbie" to Ubuntu but the change from 10.04 to 11.04 is almost as dramatic as the change from Windough$ to Ubuntu.

---

### Post by flyfishingphil on 2011-08-14
> **HalfEmptyHero said:**
> If it's not there, run this command in the terminal:

gsettings get com.canonical.Unity.Panel systray-whitelist

You should something like this:

['JavaEmbeddedFrame', 'Mumble', 'Wine', 'Skype', 'hp-systray', 'scp-dbus-service']

If you don't see 'Skype' in there, then run the following:

gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Mumble', 'Wine', 'Skype', 'hp-systray', 'scp-dbus-service']"

Then log out and log back in. I have to go to work, so I can't help you any more today. Good luck!

Did the first one. Skype shows. Still don't see the option to log out/shutdown Skype though. Maybe a day off would b a good idea. 

Catch you later and thanks for assist.

---

### Post by mikewhatever on 2011-08-14
When I installed skype in 11.04, just searching for it in the search-centric menu brought up the usual blue launcher icon. When Skype is open, its icon also appears in the panel on the left. If you right click it, there should be an option to keep it in that panel.

---

### Post by Hakunka-Matata on 2011-08-14
for me with 11.04 - 32bit Desktop, it's in the upper right-hand corner.
see attached .png
right-button on icon, "quit" command @ bottom

"For me @ least"

---

### Post by flyfishingphil on 2011-08-14
mike & Hakuna - Thanks for the replies. I think what I have to do is remove the version I have then see what else I may be able to install. 

It is currently visible in the sidebar (11.04) but I still can't find a shut down option on it and it does not show on the upper taskbar. 

Really hate to mess around with this new 11.04. That's what caused some of the problems I hand in 10.04, I think.

Will do a remove, search for what other versions I can find that are workable with 11.04, and post the results back here.

EDIT:

Went in and removed Skype then re-installed. Seems to be working fine now with Icon on upper taskbar. Will see if it works OK, but all appears correct. Problem solved.

---

### Post by xx58 on 2011-08-18
:rolleyes: Skype
Then click - Option
Then put Mark in Box - Start Skype minimised in the system try.
So, after that you will see in system try Skype Icon.

Then, go and open under[COLOR=Red] main menue[/COLOR],
Preferences
Start Application
Add
Name- Skype
Command - skype
Add

Now when starting computer, then will start Skype

This is turtorial for Unity, Uniti 2D.

---

### Post by beew on 2011-08-18
To find Skype, go to the Unity bar, click Applications and then either search for Skype in the search box or go to "Ineternet" and the icon will show up. Click it to start Skype. When it is running, you can see its icon on the Unity bar, right click and check keep in launcher (or something like that) then the icon will stay in the Unity bar. Next time when you want to start Skype just click it. When Skype is running you will see an icon in the top panel (just like in 10.04 and 10.10), right click to show the drop down menu to choose "quit" to exit Skype.

It is very simple. :)

P.S. You can make Skype autotsrat by editing StartUp Applications (in the System Settings menu, you can bring it up by clicking the power icon and choose from the drop down) like XX58 said, though I don't like to autostart it.

---

