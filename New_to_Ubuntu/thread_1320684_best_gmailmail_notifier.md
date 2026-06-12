---
title: "best gmail/mail notifier?"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by rygar on 2009-11-09
I'm looking for a really good gmail (or imap) notifier for ubuntu (9.10)

i tried checkgmail 1.13 and i like it a lot: it allows me to launch evolution when i double click, and has a very nifty pop-up notify that allows me to mark as read, archive, etc without opening up a mail client.

the main thing i dont like about it is that i can only set it up to work with ONE gmail account, and i use two (one for work).  programs like cgmail allow me to do this, but lacks many other features.  i also like cgmail because it works with notifyosd, but im not sure if it would be possible to integrate checkgmail's pop-up into notifyosd, so not a big deal...

what else do you use?  is there anything out there better than checkgmail?

---

### Post by RobinJ1995 on 2009-11-09
Applications > Ubuntu Software Center > Search for "Gmail"

---

### Post by jensbodal on 2009-11-20
It's very easy to find out which options are available, but it's not so easy to find out which options people prefer

---

### Post by krige on 2010-04-10
My favorite is "Gmail Notifier":
[http://notifier.geekysuavo.org/](http://notifier.geekysuavo.org/)
You can find it Ubuntu Software Center.

---

### Post by Rubicon421 on 2010-07-14
I know this is an old tread but does anyone have any new options they have found for a good notifier for gmail? 

I like checkgmail but there are a few issues that make me want to keep looking for something better. 

-when you click the icon it opens a new window to the gmail login page. Even if you have it set to remember your login info it still wants you to login every time before it goes to your inbox. Mine is set to remember it so when I click the icon it opens the login page and my user name and password are already filled in. I just have to click "sign in" then it goes to the inbox. Anybody know a way to make it go straight to the inbox? 

-the other issue is that it shows your password in the URL when it opens the new window to the login page. There has to be a more secure method, either by tweaking this program or using another one altogether.

---

### Post by krige on 2010-07-14
I have found a simple and lightweight highly Ubuntu 10.04 integrated GMail Notifier which takes advantages of the new and nice notify-osd and indicator-apple:
[https://launchpad.net/gm-notify](https://launchpad.net/gm-notify)

---

### Post by Freelance Physicist on 2010-07-25
@Rubicon421

Your problem with going directly to your gmail page is solved by starting checkgmail with the -no-login option.  You may have to login to the gmail web page one more time after that.  This also solves the problem of your password being in the web address.

In order to check on multiple accounts, use the -profile= option.  Say you have a work email address and a home email address.  You can check both by running:

checkgmail -profile=work

and

checkgmail -profile=home

The first time you run these, you'll be able to enter the information for these two gmail addresses.  Each can have separate preferences like icons and whatnot.

In total, here's the best way to start checkgmail

checkgmail -no-login -profile=work; checkgmail -no-login -profile=home

You can have as many profiles as necessary.

---

### Post by Anuovis on 2010-07-25
It looks like *Mail Notification* might suit your needs. You can set multiple mail accounts and it works as a stand-alone app showing a notice when new mail arrives. I am using this myself. Check it out.

[http://www.nongnu.org/mailnotify/](http://www.nongnu.org/mailnotify/)
You can install it through *Ubuntu Software Center*, just input the name in the search box.

---

### Post by rburkartjo on 2010-07-25
still like checkGmail

---

### Post by DJohnson1966 on 2010-07-25
i use webmail notifier plug in on firefox

---

### Post by Rubicon421 on 2010-07-28
> **Freelance Physicist said:**
> @Rubicon421

Your problem with going directly to your gmail page is solved by starting checkgmail with the -no-login option.  You may have to login to the gmail web page one more time after that.  This also solves the problem of your password being in the web address.

In order to check on multiple accounts, use the -profile= option.  Say you have a work email address and a home email address.  You can check both by running:

checkgmail -profile=work

and

checkgmail -profile=home

The first time you run these, you'll be able to enter the information for these two gmail addresses.  Each can have separate preferences like icons and whatnot.

In total, here's the best way to start checkgmail

checkgmail -no-login -profile=work; checkgmail -no-login -profile=home

You can have as many profiles as necessary.


This sounds like the solution I am looking for but I'm not quite sure how to use it. Do you add the line you mentioned to the settings in checkgmail or is it something you do in the terminal? Also, I'm guessing that I should replace the words "work" and "home" with the actual email address right?

---

### Post by AshRice on 2010-07-28
I'm a fan of the one built into Docky.

---

### Post by Freelance Physicist on 2010-07-28
> **Rubicon421 said:**
> This sounds like the solution I am looking for but I'm not quite sure how to use it. Do you add the line you mentioned to the settings in checkgmail or is it something you do in the terminal? Also, I'm guessing that I should replace the words "work" and "home" with the actual email address right?

You type these commands into the terminal.  If you use Alt+F2, you need to type each version of checkgmail on their own lines (no semicolons).  Or, if you want checkgmail to start when the computer starts up, you can add the versions of checkgmail in separate lines under System->Preferences->Startup Applications with each profile getting its own entry (again, no semicolons).

You don't need to replace "home" and "work" with the actual email addresses.  You can use any string of characters you want (though, if you want spaces or other non-alphanumeric characters you'll need to use quotations marks).  These are just names for the profiles that checkgmail will read to get to the email addresses.  The first time you run
```
checkgmail -no-login -profile=home
```
checkgmail will create prefs-home.xul in ~/.checkgmail and likewise for "work".  The actual email addresses will be stored in these files.  It's fine to use your email address to name the profile like so:
```
checkgmail -no-login -profile=something@example.com
```
How do you start checkgmail?  Applications menu?  Terminal?  Automatic running at startup?

---

### Post by Rubicon421 on 2010-07-29
OK, I ran the code in the terminal using home as the profile name. This opened up the checkgmail preferences window and all the fields were blank. So I re-entered my user name, password and checked the box for it to remember it. I closed out the window, closed and reopened checkgmail and it still does the same thing. 

And I have checkgmail selected to open at startup using the context menu option in the mint menu.

---

### Post by Freelance Physicist on 2010-07-29
If you want to use the profile feature, you have to use the -profile= option every time.  So, change the command in the startup dialog to 
```
checkgmail -no-login -profile=home
```
Then create new entries for your other email addresses, i.e., -profile=work, etc.

---

### Post by Rubicon421 on 2010-07-30
OK, adding the -no login option to the start up fixed it for me. I'm not the OP but it's solved on my end. And I don't see the user name and password in the URL anymore which makes me feel much better about using this program.

---

### Post by Rubicon421 on 2010-08-06
For some reason this fix did not apply to checkgmail when it opens from autostart at login. But if I close it and reopen it through the menu then it works fine.

---

### Post by Freelance Physicist on 2010-08-06
Which problem isn't fixed?

---

### Post by Rubicon421 on 2010-08-06
when I restart, checkgmail opens on start up and when I click the icon, it still goes to the login page. But if I close it and reopen it from the menu, then it goes straight to the inbox. 

It seems like there are two instances of it on my system and the one in the start up was not affected by adding the no login option.

---

### Post by Freelance Physicist on 2010-08-06
Could you post the commands you use to start checkgmail on startup?

---

### Post by Rubicon421 on 2010-08-06
I'm running Linux Mint 9, and in the Mint menu there is a right click option to run at start up. I used that on the menu entry for checkgmail and in the properties, under command I have:

checkgmail -no-login

It autostarts at login but still goes to the login page. But if I close it and reopen it using the same short cut that is set to autostart then it works and goes right to the inbox.

---

### Post by Freelance Physicist on 2010-08-06
That's odd.  I'm not sure what's going on with that.  You could try deleting the gmail cookies in firefox and then logging in one more time through firefox before trying again through checkgmail.  If that doesn't work, I don't know what's going on.  You might want to file a bug report.  Here's the homepage: [http://checkgmail.sourceforge.net/](http://checkgmail.sourceforge.net/)

---

### Post by ALF102 on 2010-08-06
Well, I've been using Mozilla Thunderbird for a long time now. You can set up multiple account with that also.

---

### Post by theleftofsatan on 2010-08-09
> **Rubicon421 said:**
> I'm running Linux Mint 9, and in the Mint menu there is a right click option to run at start up. I used that on the menu entry for checkgmail and in the properties, under command I have:

checkgmail -no-login

It autostarts at login but still goes to the login page. But if I close it and reopen it using the same short cut that is set to autostart then it works and goes right to the inbox.
I had the same problem.

Go to preferences and change the command from 
> firefox %uto > firefox [https://www.gmail.com/](https://www.gmail.com/)

---

### Post by Freelance Physicist on 2010-08-09
> Go to preferences and change the command from
```
firefox %u
```
to
```
firefox https://www.gmail.com/
```
The problem with this solution is that clicking on links within emails will open up the gmail page instead.  %u stands for the link you want to open, not just the link to open when you click on the checkgmail icon.  This will also happen with the Open link beneath the email subjects.

---

### Post by Jazzy_Jeff on 2010-08-10
I personally just launch evolution and then use alltray to minimize it to the tray.

---

### Post by jesuisbenjamin on 2010-08-12
Hi there,

i installed cGmail just now but the application doesn't want to start up, any idea why?
thanks.
B.

---

### Post by jesuisbenjamin on 2010-08-13
Bong!

---

### Post by jesuisbenjamin on 2010-08-14
Anyone with ideas? Thanks

---

### Post by Pavluha88 on 2010-08-16
> **krige said:**
> My favorite is "Gmail Notifier":
[http://notifier.geekysuavo.org/](http://notifier.geekysuavo.org/)
You can find it Ubuntu Software Center.

It has serious security bug. It allows anybody who has access to your PC to see password for an y accounts you have set up on this program. When you press "check mail" it is opening new browser window and together with login send your password not encrypted so you can just see it in web-address.

---

### Post by ajgreeny on 2010-08-16
> **Pavluha88 said:**
> It has serious security bug. It allows anybody who has access to your PC to see password for an y accounts you have set up on this program. When you press "check mail" it is opening new browser window and together with login send your password not encrypted so you can just see it in web-address.
Are you sure about that?

I see no indication of a password in the Firefox addressbar when I use it to connect to my gmail account using either the "Check now" or the "Go to Inbox" buttons.  Maybe they could be seen by a hacker if he or she really wanted to, but that is true of most things, unless you have a system so surrounded by security that it is practically unusable.  There is no "Check Mail" option available in the right click to the icon on my system, only the "Check now", and that simply brings up a notification of "X unread messages" or "No unread mail".

Are we talking about the same notifier application?  There is a big difference between "Gnome gmail notifier" and "gmail-notify"

---

### Post by Pavluha88 on 2010-08-16
here was double msg.

---

### Post by Pavluha88 on 2010-08-16
Totally sure. See print screen on the link: ```
http://img706.imageshack.us/img706/5176/bugjrt.jpg
``` I reported program author on this and he agreed about the bug and said that working out how to fix it.


Can smb advice really good mail notification program so it is in gnome tool bar as icon and can work with different mail servers (imap, pop) and be stable. I checked too many of them and still can't find best solution. 
cgmail - it does not save set up e-mail accounts and I have to set up from beginning after each pgm boot again. 
Standard gmail-notify works well but it is only for one account and for gmail only.
mail-notification - does not work well - not checking gmail account, some problems with booting etc. 

Does smb knows really easy e-mail checker for GNOME?

---

### Post by ajgreeny on 2010-08-16
> **Pavluha88 said:**
> Totally sure. See print screen on the link: ```
http://img706.imageshack.us/img706/5176/bugjrt.jpg
``` I reported program author on this and he agreed about the bug and said that working out how to fix it.


Can smb advice really good mail notification program so it is in gnome tool bar as icon and can work with different mail servers (imap, pop) and be stable. I checked too many of them and still can't find best solution. 
cgmail - it does not save set up e-mail accounts and I have to set up from beginning after each pgm boot again. 
[COLOR=Red]Standard gmail-notify works well but it is only for one account and for gmail only.[/COLOR]
mail-notification - does not work well - not checking gmail account, some problems with booting etc. 

Does smb knows really easy e-mail checker for GNOME?
OK, as I suspected, we were talking about different applications.  There is obviously a confusion between **gnome-gmail-notifier** and plain **gmail-notify**, wiith some people interchanging the names and thus getting me totally confused, largely by omitting the "gnome" part of the name in most cases.

Either way, I am fine as I am using gmail-notify, not gnome-gmail-notifier

---

### Post by Pavluha88 on 2010-08-17
> **ajgreeny said:**
> OK, as I suspected, we were talking about different applications.  There is obviously a confusion between **gnome-gmail-notifier** and plain **gmail-notify**, wiith some people interchanging the names and thus getting me totally confused, largely by omitting the "gnome" part of the name in most cases.

Either way, I am fine as I am using gmail-notify, not gnome-gmail-notifier

Are you able to set up gmail-notify for two or more accounts?

---

### Post by ajgreeny on 2010-08-18
> **Pavluha88 said:**
> Are you able to set up gmail-notify for two or more accounts?
I haven't got a clue.  I only have one email address, so can not even check that for you.  However I can't see any obvious way to set up more than one, so perhaps there is no such way available.

---

### Post by marc88 on 2010-09-14
you know some other email notifier for Hotmail?
I Popper, however, does not work because I need to post a pop3s

---

