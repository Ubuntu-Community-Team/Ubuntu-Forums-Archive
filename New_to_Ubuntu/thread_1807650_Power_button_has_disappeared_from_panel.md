---
title: "Power button has disappeared from panel"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by Bearly Able on 2011-07-19
Hi,

I've just been helping a friend restore the panels on her Xubuntu install after they mysteriously vanished.  That problem is solved, but there is no longer a "Power Off" button on the panel - just a log-out button.  I've tried "Add to Panel" but the option doesn't appear.  The only way to close down is to log out and then choose "close" from the log-in screen.

I'd be very grateful for any assistance.  Thank you.

---

### Post by 2F4U on 2011-07-19
What version of Xubuntu is that and what did you try to add to the panel? I think the shutdown option is contained in a Session Menu item.

---

### Post by Jet Chang on 2011-07-19
> **Lesley Lutomski said:**
> Hi,

I've just been helping a friend restore the panels on her Xubuntu install after they mysteriously vanished.  That problem is solved, but there is no longer a "Power Off" button on the panel - just a log-out button.  I've tried "Add to Panel" but the option doesn't appear.  The only way to close down is to log out and then choose "close" from the log-in screen.

I'd be very grateful for any assistance.  Thank you.

Open a terminal and type: **sudo shutdown -h now**

---

### Post by Toz on 2011-07-19
> **Lesley Lutomski said:**
> Hi,

I've just been helping a friend restore the panels on her Xubuntu install after they mysteriously vanished.  That problem is solved, but there is no longer a "Power Off" button on the panel - just a log-out button.  I've tried "Add to Panel" but the option doesn't appear.  The only way to close down is to log out and then choose "close" from the log-in screen.

I'd be very grateful for any assistance.  Thank you.

Right-click the Logout button and select "Properties". You should be able to change which button is displayed there.

---

### Post by Bearly Able on 2011-07-20
Thanks for the replies.  I use Ubuntu myself and I'm not familiar enough with Xubuntu to know where to look when things aren't working.

@2F4U - The version is 10.04 (LTS).  I looked right through the list of possibilities to add to the panel and couldn't find anything that looked remotely relevant.  I can't remember if "Session Menu" was among them; I'll look for it next time I'm round.

@Jet Chang - Thanks, but my friend is an elderly computer newbie.  Closing down from the log-in screen is confusing enough for her without trying to teach her to use the command line.

@Toz - I'm sure I tried right-clicking the log-out button and nothing happened.  I'll give it another go when I get a chance and report back.

---

### Post by Bearly Able on 2011-07-20
OK, I've just been round and had another look at the machine.

@2F4U - there is no "Session Menu" option or anything else with power off options.  The only thing I could find was "Action Buttons" (log out or lock the screen) which is what is already there.

@Toz - right-clicking gets me a "Properties" tab, but the only options are Quit (=log out), Lock Screen or Quit & Lock Screen.

Any other suggestions anyone?  Thanks.

---

### Post by halitech on 2011-07-20
I've seen this before on a Debian machine I had set up when logging in as a non-root user after activating sudo. I think I had to add the user to the sudo group (if I remember right). You could also just create a launcher with the command **sudo shutdown -h now** as Jet Chang suggested doing in the terminal.

---

### Post by Bearly Able on 2011-07-20
Thank you.  I failed to grasp the suggestion properly first time round.  It will be a couple of days before I get the chance to try that.

---

### Post by Toz on 2011-07-20
> **Lesley Lutomski said:**
> @Toz - right-clicking gets me a "Properties" tab, but the only options are Quit (=log out), Lock Screen or Quit & Lock Screen.

What version of Xubuntu are you using? In 11.04 (Natty) with XFCE 4.8, I get the following options to choose from:
[LIST]
[*]Log Out Dialog
[*]Log Out
[*]Lock Screen
[*]Shut Down
[*]Restart
[*]Hibernate
[*]Suspend
[/LIST]

---

### Post by mokrates on 2011-07-20
> **halitech said:**
> I've seen this before on a Debian machine I had set up when logging in as a non-root user after activating sudo. I think I had to add the user to the sudo group (if I remember right). You could also just create a launcher with the command **sudo shutdown -h now** as Jet Chang suggested doing in the terminal.
I think you can't do this. at least on my ubuntu box, sudo asks for a password on the console. An alternative would be to use gksudo or sth. but that still would ask for a password. The session-applet shuts down by signalling the login-manager; thats why you normally don't need a password for that.

If the appropriate applet vanished from the available-applets-list, you could check if all the packages are installed. I'd do that by asking 'apt-cache search applet' on the console, perhaps grep'ing for 'session', and checking dpkg -l against it.

```
mokrates@mokbook:~$ apt-cache search applet | grep session
indicator-applet-session - Clone of the GNOME panel indicator applet
indicator-session - An indicator showing session management, status and user switching.
mokrates@mokbook:~$ dpkg -l | grep applet | grep session
ii  indicator-applet-session                        0.4.12-0ubuntu1                              Clone of the GNOME panel indicator applet

```mo

---

### Post by halitech on 2011-07-20
forgot about that, I guess gksudo would be a better option then just sudo. But, there should be a reason why they can't select it from the menu and I'm guessing it has something to do with the users priviledges

---

### Post by mokrates on 2011-07-20
> **halitech said:**
> forgot about that, I guess gksudo would be a better option then just sudo. But, there should be a reason why they can't select it from the menu and I'm guessing it has something to do with the users priviledges
That is unlikely. The applets in the available-applet-lists are normally not filtered by permissions. What I deem likely is that the applet just isn't there, or he has missed it looking for it (the names are often not helping).

there could be a permissions problem, which would mean (by my opinion) that the applet is, in fact, in the panel, but not displaying anything because of missing permissions. I don't use XFCE, is there a possibility to check for applets which are loaded in the panel? if it is loaded, it probably would be missing from the 'available-applets-list' but be in the 'applets-in-panel' list.

---

### Post by halitech on 2011-07-20
I use XFCE on all my machines here and I always have to set them up to have permission to actually shut a system down as normally in Debian, only the root user can do a shutdown.

the fact that he can log out to me says the user isn't in the sudo group

---

### Post by mokrates on 2011-07-20
So the shutdown button didn't vanish in the panel, there never was one. There was a session button, which now doesn't show the shutdown menu-entry anymore.
?

---

### Post by halitech on 2011-07-20
> **Lesley Lutomski said:**
> Hi,

I've just been helping a friend restore the panels on her Xubuntu install after they mysteriously vanished.  That problem is solved, but there is no longer a "Power Off" button on the panel - just a log-out button.  I've tried "Add to Panel" but the option doesn't appear.  The only way to close down is to log out and then choose "close" from the log-in screen.

I'd be very grateful for any assistance.  Thank you.

> **mokrates said:**
> That is unlikely. The applets in the available-applet-lists are normally not filtered by permissions. What I deem likely is that the applet just isn't there, or he has missed it looking for it (the names are often not helping).

there could be a permissions problem, which would mean (by my opinion) that the applet is, in fact, in the panel, but not displaying anything because of missing permissions. I don't use XFCE, is there a possibility to check for applets which are loaded in the panel? if it is loaded, it probably would be missing from the 'available-applets-list' but be in the 'applets-in-panel' list.

> **mokrates said:**
> So the shutdown button didn't vanish in the panel, there never was one. There was a session button, which now doesn't show the shutdown menu-entry anymore.
?

by the sounds of it, there was an option to shut down before he fixed whatever was the issue with the panels but after restoring the panels, he only has log off and not shut down

---

### Post by mokrates on 2011-07-20
Yes, I got that. The question remains: where did it vanish? Was it a single applet in the panel, displaying exactly one button, which is now vanished (not installed anymore, as i suspect), or was there an applet which displayed multiple buttons, or options in a menu (logout AND shutdown) which now only displays one (which could have something to do with permissions).
Where did it vanish from: from the applet or from the panel? Looks similar to the user but has different reasons.

---

### Post by halitech on 2011-07-20
I'm taking from what the poster has stated that it was 1 button that brought up multiple options but I guess it could be either way. maybe we can get a screen shot showing what it looks like now so we can figure it out better.

---

### Post by Bearly Able on 2011-07-21
Hi guys and thanks for the interest.

What used to be there was a button (round, power-type icon if I recall correctly but I might not, as it's not my machine) which brought up a small window with six options - Shut Down, Restart, Log Out, Hibernate and a couple of others I don't remember.  What is there now is an open door icon, identical to - and providing the same functions as - the "Action Buttons" available in the applets list.

I don't know what caused the panels to disappear in the first place, but it has happened once before.  On that occasion, they were there when my friend closed down the computer and not when I restarted it.  On this occasion, she had a 12-year-old great-grandson staying.  He insists he didn't touch the computer, but I suppose anything is possible.

I restored the panels using the same [advice I received last time]("http://ubuntuforums.org/showthread.php?t=1708098").  Last time, this restored the panels exactly as they were; this time, the power button has been replaced by a log-out button but everything else is as it was.

The last time the panels vanished, I'm sure I could shut down by right-clicking the desktop and choosing the option from the main menu, but again I can now only log out by that method.

I can't get round to check user privileges or anything else until tomorrow.  I'll post back then.

---

### Post by finrod_felagund on 2011-07-21
[FONT=Comic Sans MS][COLOR=DarkSlateBlue]I have had the same problem - I was trying to remove an error message to get at the shutdown button, but removed it instead.

Move away from any panel buttons, right click on the panel, Add to panel, which produces a list of buttons, one of which is a red Shut Down.

Placement may not match the original (maybe just as well in my case) [/COLOR][/FONT][IMG]http://ubuntuforums.org/images/icons/icon12.gif[/IMG]
[FONT=Comic Sans MS][COLOR=DarkSlateBlue]
Mark[/COLOR][/FONT]

---

### Post by Bearly Able on 2011-07-21
@finrod_felagund: thanks for the reply, but that's precisely my problem - there *isn't* a red shut-down button anywhere, not on the panel, not on the add-to-panel list and not anywhere else I've managed to look.

(I had an intermittently-vanishing power button in Ubuntu and I became a dab hand at adding one to the panel - but only if there's one there to be added!)

---

### Post by finrod_felagund on 2011-07-21
[FONT=Comic Sans MS][COLOR=DarkSlateBlue]Sorry, I thought at the time it seemed strange that a newbie could turn up with a Gordian knot solution.[/COLOR][/FONT]

---

### Post by mokrates on 2011-07-21
Please! Do you /have/ to use that font?

---

### Post by Bearly Able on 2011-07-21
@finrod_felagund - thanks for trying, anyway.  Nice to know Ubuntu has reached Beds!

@mokrates - some people like it.  I was asked to build a Web site using Comic Sans, as that's the font the group uses for their leaflets, newsletter, etc.  Infinite Diversity in Infinite Combinations!

---

### Post by nickdc on 2011-07-21
Hi,
 I don't know if this will be of any help or not:

I've come to this thread having experienced exactly the same problem as you, Lesley: out of the blue, I boot up to find a desktop with no panels, having been fine earlier in the day. Thanks to your including the link to that problem, I got my panels back, but, like you, the logout button (mine's got a green running man icon) had no other functions - I couldn't restart, shutdown etc. And these functions were not present via the "Add New Items" menu option. The good news from my point of view, is that I've now got them back, but the bad news is that I don't know how it happened! I can confirm, though, that even when the full functions are present once again on the logout button (ie clicking it brings up a small square window with five square buttons in it: Log Out, Restart, Shut Down, Suspend and Hibernate, plus a "Save session for future logins" checkbox and a Cancel button), the Add New Items options on the right click menu are exactly the same as they were when the button had only the  Log Out function, ie one of the options is the Action Buttons (running green man icon) with a "Log out or lock the screen" descriptor. The fact that it's named as Action Button_**s**_ suggests that it's designed to display the range of functions (Restart, Shutdown etc) and their absence is due to something more embedded in the bootup or login process. I suspected it may have been caused by a series of power shutdowns and session logins that I executed after losing the panels, and I got it back due to further playing around with the Session and Startup settings, but I can't now reproduce the original problem: all the shutdown functions remain doggedly persistent now, which is good from my point of view but doesn't help troubleshooting! Maybe you'll strike lucky and they will simply reappear for you too!

---

### Post by mokrates on 2011-07-21
On the risk of taking this thread OT and getting a beating from a mod for being impolite:
there are people who are offended by comic sans

[http://bancomicsans.com](http://bancomicsans.com)

And please don't embarrass the vulcans with this silly font...

But as I don't let this topic go... why do i have this font installed anyway?

---

### Post by Bearly Able on 2011-07-24
@nickdc: Thanks for that.  If nothing else, it's nice to know I'm not alone!

@mokrates: I know -they tend to be a very vocal lot.  And don't worry about the Vulcans - embarrassment is an emotion.

To get back on topic, I've finally managed to take another look at the machine.  I've tried the other user account (very seldom used) and there is no problem there; the "Quit" button brings up the dialogue as before - see screen shot.

Both accounts are Administrator accounts, and both have the same user privileges.  As far as I can see, both users are also members of the same groups, so I can't work out why one account is OK and the other is not.

Anybody got any more ideas on the subject?  Thanks.

---

### Post by westie457 on 2011-07-24
Not sure if this will work in Xubuntu. It does in other distros.
In a terminal run ```
gconftool --recursive-unset /apps/panel && killall gnome-panel

```

---

### Post by Bearly Able on 2011-07-24
Thanks - what does that do?  I like to know before I do anything, especially on someone else's system.

---

### Post by Bearly Able on 2011-07-24
> **halitech said:**
> I use XFCE on all my machines here and I always have to set them up to have permission to actually shut a system down as normally in Debian, only the root user can do a shutdown.

the fact that he can log out to me says the user isn't in the sudo group

The user wasn't in the sudo group - but then, neither was the other user where there's no problem.  I've tried adding the user to sudo, but it makes no difference.  The "Quit" button will still only log out, and there are no new options in the "Add to Panel" menu.

---

### Post by westie457 on 2011-07-24
> **Lesley Lutomski said:**
> Thanks - what does that do?  I like to know before I do anything, especially on someone else's system.

Quite right you asked about a command you do not understand. BTW I am not offended.
All that command does is reset the top panel to clean install defaults keeping any minor adjustments you have made EG Setting the clock to show day/date in place.

Perfectly safe to run.

---

### Post by Bearly Able on 2011-07-24
Thanks for that.  What I get from that command is ```
gnome-panel no process found
```presumably because it's actually using xfce4-panel.  How do I amend the command to take account of that?

---

### Post by westie457 on 2011-07-24
> **Lesley Lutomski said:**
> Thanks for that.  What I get from that command is ```
gnome-panel no process found
```presumably because it's actually using xfce4-panel.  How do I amend the command to take account of that?

Play around a bit with the first letter of the command. IE remove the 'g' and type a 'x' without the quote obviously. if it does not work first time add one bit of xfce4 at a time until it does.

                  ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

OOPS my bad did not read it properly. Try the original again changing 'gnome-panel' to xfce4-panel

---

### Post by Bearly Able on 2011-07-24
Thanks.  I had to leave before I saw your reply.  I'll try to get round there tomorrow, otherwise it will be about a week before I can try it as my friend will be away.  I'll post back the results when I can.

---

### Post by Bearly Able on 2011-08-09
> **westie457 said:**
> Try the original again changing 'gnome-panel' to xfce4-panel
OK, I've finally had a chance to try this.  The above command just removed the panels altogether again, and restoring them has left me back at the original problem.

Any other suggestions, anyone?

---

### Post by whatthefunk on 2011-08-09
If I am correct, you have accidentally deleted the shutdown panel button.  Right?

Okay, first let me say that I dont use Xubuntu nor have I ever used it.  But I had the exact same in Lubuntu and fixed it. 

I believe that Xubuntu uses the xfce panel.  Go to ~.config/xfce4/panel  If you cant find this, hunt around for some other panel file in ~.config.  This file dictates the look of your panel.

Now (again this is for Lubuntu) go to /usr/share and look for the folder for your panel.  Im guessing its called xfcepanel or something like that.  Or maybe its in xfce4 and then a seperate panel folder??  Hunt around in there for the default panel settings.  In Lubuntu, the file is at /usr/share/lxpanel/profile/LXDE/panels so maybe yours would be at /usr/share/xfcepanel/profile/XFCE/panels????  No idea really.

Anyway, when you find the default file, open it up and look for something mentioning shutdown or logout.  Copy that whole section and paste it at the end of the first file we found, the one in ~.config.  Youll probably have to restart the panel for the new settings to take place.

If that fails, I believe that if you deleted the panel file in ~.config (back it up first) then the system would force the creation of another default one.

---

### Post by JKyleOKC on 2011-08-09
> **Lesley Lutomski said:**
> Any other suggestions, anyone?I'm using Xubuntu 10.04 LTS so perhaps I can help. If you have the "Action Buttons" applet on the panel, right click it and select properties (yes, I know you've already tried this, but bear with me). On the pull-down that offers the three options beginning with "quit" select "quit" and close the properties window. Now try that icon on the panel.

If you don't have it on the panel, add that applet; I believe it defaults to the "quit" choice but you can verify and change to it if necessary.

When I click the panel icon, I get a window with five buttons on it: Logout, Restart, Shut down, Suspend, and Hibernate. You can go to the "Settings" choice from the "Applications" menu and turn off the Suspend and Hibernate buttons to leave only three choices if you like.

You can also create a launcher as suggested earlier to execute "sudo shutdown" but as you've noted that normally requires a password entry. However you can add a line to the /etc/sudoers file to remove the password request for just the "shutdown" command; take a look at the "man sudo" page for details of how it's done, and be very careful to use "visudo" to do the editing -- otherwise you can lock yourself out of sudo entirely!

---

### Post by JKyleOKC on 2011-08-09
Oh, oh! I should have read the entire thread before posting...

Check the "groups" membership of both users; in Xubuntu at least, the "sudo" group doesn't control much of anything. The critical one is either "adm" or "admin" (both exist and I never can remember which is the one that controls sudo access; just checked, though, and it's "admin"). The very first user created, during the install process, becomes a member of this critical group automatically. Later users must be added by hand.

Take a look at the sudoers file via "gksudo mousepad /etc/sudoers" and you'll find the critical information near the end of the file. You may have to do this from the user account that has the full action window, though, because the other one probably won't be able to use any "sudo" or similar actions.

The fact that one account works normally proves that the applet is still there and in working order, so the group membership seems to be the most likely cause of the problem.

Apparently there's some sort of interlock in the "quit" panel applet that depends on this same group membership to allow shutdown! Hope this helps a bit...

---

### Post by Bearly Able on 2011-08-09
> **JKyleOKC said:**
> On the pull-down that offers the three options beginning with "quit" select "quit" and close the properties window. Now try that icon on the panel.
Thanks, but it doesn't help.  "Quit" is what it's been set to all along and that only logs me out.  I might try your other suggestion if I get really desperate, but I'm loathe to start messing about with etc/sudoers when I'm not entirely sure what I'm doing!

> **whatthefunk said:**
> If I am correct, you have accidentally deleted the shutdown panel button.  Right?I didn't actually delete it - it vanished of its own accord for no apparent reason.
> **whatthefunk said:**
> 

I believe that Xubuntu uses the xfce panel.  Go to ~.config/xfce4/panel  If you cant find this, hunt around for some other panel file in ~.config.OK, well I have a directory called panel, with several files inside it, including one called "panels.xml".  See second screenshot.
> **whatthefunk said:**
> 
Now (again this is for Lubuntu) go to /usr/share and look for the folder for your panel.  Im guessing its called xfcepanel or something like that.  Or maybe its in xfce4 and then a seperate panel folder??  Hunt around in there for the default panel settings.In /usr/share there is a directory called xfce4 which seems to be the only possibility, but I can't find anything in there that looks at all promising.  See first screenshot.  Am I missing something?

---

### Post by Bearly Able on 2011-08-09
> **JKyleOKC said:**
> 
Check the "groups" membership of both users; in Xubuntu at least, the "sudo" group doesn't control much of anything. The critical one is either "adm" or "admin" (both exist and I never can remember which is the one that controls sudo access; just checked, though, and it's "admin"). The very first user created, during the install process, becomes a member of this critical group automatically. Later users must be added by hand.
The account with the problem is the original user account, and "sudo" works just fine on it.  Both users have administrator accounts and are members of both "admin" and "adm" groups.
> **JKyleOKC said:**
> 
Take a look at the sudoers file via "gksudo mousepad /etc/sudoers" and you'll find the critical information near the end of the file.

I've looked at the file, and it says "ALL" for admin,, sudo and root.

Thanks for your help so far.  Any other ideas?

---

### Post by JKyleOKC on 2011-08-09
Stranger and stranger!

I'm pretty much clutching at straws now; take a look in your .config/xfce4/actions directory, which on my system contains just one file and that file has only two lines in it, both ending with "=0" which appear to correspond with the two settings of the "action buttons" applet.

I'm pretty much convinced that it has to be something in the configuration of that one user account, but really have no good idea where to look in the hidden files of the home directory. I don't think it could be anything wrong in the system directories, since if it was, the other account would be showing the same problem...

---

### Post by JKyleOKC on 2011-08-09
Very wild thought: could it be that somehow an "invisible" character has gotten into the group data for the affected user account? I had something similar happen last week as I was sending a URL link to a customer via E-mail, and the link was not working. When I sent it again, it worked.

Try creating a new user, adding that user to the "admin" group, then logging it out and back in, to see if this new user has a full five-button "quit" window. If that works, you can try removing the affected user from the "admin" group, logging out and back in, then adding the user back into "admin", logging out and in again, and seeing whether that cures the problem.

The log out and back in dance is necessary any time you make changes to a user's privileges, since some of them are read from disk only during the log-in process and there's no list of just which ones are involved.

As I said, this is a wild thought, but it's possible that some bit of electrical noise at just the wrong time could have made such a change in the stored settings for the user...

---

### Post by Bearly Able on 2011-08-09
Thanks again.  I'm at home now and won't get a chance to try your suggestions until Friday, but I'll post back then and let you know how it goes.

---

### Post by whatthefunk on 2011-08-09
> **Lesley Lutomski said:**
> Thanks, but it doesn't help.  "Quit" is what it's been set to all along and that only logs me out.  I might try your other suggestion if I get really desperate, but I'm loathe to start messing about with etc/sudoers when I'm not entirely sure what I'm doing!

I didn't actually delete it - it vanished of its own accord for no apparent reason.
OK, well I have a directory called panel, with several files inside it, including one called "panels.xml".  See second screenshot.
In /usr/share there is a directory called xfce4 which seems to be the only possibility, but I can't find anything in there that looks at all promising.  See first screenshot.  Am I missing something?

It looks to me like xfce panel creates a separate file for each item on the panel.  So the file clock-5.rc controls the clock, pager-3.rc controls the desktop pager etc.  Then this is all controlled by the panel.xml file.

Try to restore the panel defaults.

1. Go to ~/.config/xfce4/panel and copy the file panels.xml to someplace else in your home directory.  This is your backup in case things go wrong.

2. Go back to ~/.config/xfce4/panel and delete the panels.xml file.

3.  Restart the panel by opening up a terminal and typing 
```
xfce4-panel
```

This should get a new default panel.  If it doesn't...

4.  Open up a panel and enter this in:
```
cp /etc/xdg/xfce4/panel/default.xml ~/.config/xfce4/panel/panels.xml
```

This will copy the panel defaults to your config folder.

5.  Restart the panel
```
xfce4-panel
```

6.  If none of this worked, restore your backup to ~/.config/xfce4/panel/panel.xml 

Hope this helps!

---

### Post by Bearly Able on 2011-08-13
> **JKyleOKC said:**
> Stranger and stranger!

I'm pretty much clutching at straws now; take a look in your .config/xfce4/actions directory, which on my system contains just one file and that file has only two lines in it, both ending with "=0" which appear to correspond with the two settings of the "action buttons" applet.Yes, this one's the same.
> **JKyleOKC said:**
> 
I'm pretty much convinced that it has to be something in the configuration of that one user account, but really have no good idea where to look in the hidden files of the home directory. I don't think it could be anything wrong in the system directories, since if it was, the other account would be showing the same problem... I agree.  This gave me the bright idea to try to copy and paste the contents of the panels directory from the working account to the other, but it made no difference.
> **JKyleOKC said:**
> 
Try creating a new user, adding that user to the "admin" group, then logging it out and back in, to see if this new user has a full five-button "quit" window. Yep, that works fine (even though I set up the new user account from the dodgy one!). > **JKyleOKC said:**
> If that works, you can try removing the affected user from the "admin" group, logging out and back in, then adding the user back into "admin", logging out and in again, and seeing whether that cures the problem.Well, the idea seemed good to me, but unfortunately, it didn't work.  I'm back to the log-out only button.
> **whatthefunk said:**
> 
Try to restore the panel defaults.

1. Go to ~/.config/xfce4/panel and copy the file panels.xml to someplace else in your home directory.  This is your backup in case things go wrong.

2. Go back to ~/.config/xfce4/panel and delete the panels.xml file.

3.  Restart the panel by opening up a terminal and typing 
```
xfce4-panel
```

This should get a new default panel.OK up to delete panels.xml, which didn't close the panels, so I tried to log out and back in again.  This time, the "quit" button would only close the panels, not log out!  So I logged out, logged in again, the panels were back as before, there was a new panels.xml file and the "quit" button was back to being log-out only.
> **whatthefunk said:**
> 
This should get a new default panel.  If it doesn't...

4.  Open up a panel and enter this in:
```
cp /etc/xdg/xfce4/panel/default.xml ~/.config/xfce4/panel/panels.xml
```

This will copy the panel defaults to your config folder.
I've just realised I missed this suggestion yesterday (I was a bit pressed for time) so I'll try that on Monday and hope it works.

Thanks again, guys, for all your suggestions.

---

### Post by Bearly Able on 2011-08-26
> **whatthefunk said:**
> 

4.  Open up a panel and enter this in:
```
cp /etc/xdg/xfce4/panel/default.xml ~/.config/xfce4/panel/panels.xml
```

This will copy the panel defaults to your config folder.

So it does.  (I don't have a default.xml - it's also panels.xml.)  The problem is that when I log out and back in again, the new file has been miraculously replaced by the old one.  I've tried unchecking "Save session on log out" but it makes no difference.  Whatever I do I end up with the old file back in place, which makes no sense to me.

Any further ideas woulds be *most* welcome!

---

### Post by Bearly Able on 2011-09-11
Anyone?

---

### Post by Toz on 2011-09-11
I believe xubuntu/xfce writes out to that file on exit. Try logging out, going to the first tty (Ctrl+Alt+F1), logging into text mode there, executing the command, then Ctrl+Alt+F7 to return the gui and logging back in again.

The other thing to consider, is that if you're running xubuntu, the location of the default xubuntu panel file is actually **/etc/xdg/xdg-xubuntu/xfce4/panel/default.xml**. The one at **/etc/xdg/xfce4/panel/default.xml** is the xfce default. Small difference.

---

### Post by Bearly Able on 2011-09-23
Thanks for your suggestion - didn't get a chance to try it until now.

The good news is - that did get me a new default panel.  The bad news is - it still has the same duff log-out button.  (By the way, the file was /etc/xdg/xdg-xubuntu/xfce4/panel/**panels.xml**, not /etc/xdg/xdg-xubuntu/xfce4/panel/default.xml.)

Thanks for your help.  Any further suggestions will be gratefully received!

---

### Post by Toz on 2011-09-23
Try going to Settings->Settings Manager->Session and Startup, and checking the "Prompt to logout" checkbox. Then change the properties of the action button to "Quit".

Does that help?

---

### Post by Bearly Able on 2011-09-30
Toz - you are a star!  That's finally fixed it.  I'm most grateful, as is my friend.  (She worked for several years as a nurse in Toronto, and has very fond memories of the place and the people.)

---

### Post by Toz on 2011-09-30
Too funny - most of us are a good natured bunch. lol.

---

