---
title: "How can I use an application installed by another user?"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by Rob625 on 2010-09-16
Hello Ubuntu Forums!

I am a Windows user of long standing. Every few years I have a go at escaping from the Microsoft asylum and switching to Linux, but the inspiration usually doesn't last long.

I have just done my second Ubuntu install. Even the first one, which was on a home-built desktop pc with a 6-year-old motherboard, left me impressed by the slickness and usability. This time, maybe, I will go on. The second one is on a modern laptop, and works even better.

But I am stuck on something that must be obvious. This time I didn't call the first account 'rob', because I wanted to save that for the account I will use every day, without special privileges; instead I called it 'admin0'. Then when the install was all done, I created another account 'rob'.

I like the Google Chrome browser, so I logged on as admin0, downloaded it, and installed it. All OK so far.

Then I logged off admin0 and logged on as rob. My question is, how do I use Chrome? Where do I find it? I tried downloading again, and installing (still as rob), but if I click Applications, Internet, I don't see it.

Thanks
Rob

---

### Post by sandyd on 2010-09-16
> **Rob625 said:**
> Hello Ubuntu Forums!

I am a Windows user of long standing. Every few years I have a go at escaping from the Microsoft asylum and switching to Linux, but the inspiration usually doesn't last long.

I have just done my second Ubuntu install. Even the first one, which was on a home-built desktop pc with a 6-year-old motherboard, left me impressed by the slickness and usability. This time, maybe, I will go on. The second one is on a modern laptop, and works even better.

But I am stuck on something that must be obvious. This time I didn't call the first account 'rob', because I wanted to save that for the account I will use every day, without special privileges; instead I called it 'admin0'. Then when the install was all done, I created another account 'rob'.

I like the Google Chrome browser, so I logged on as admin0, downloaded it, and installed it. All OK so far.

Then I logged off admin0 and logged on as rob. My question is, how do I use Chrome? Where do I find it? I tried downloading again, and installing (still as rob), but if I click Applications, Internet, I don't see it.

Thanks
Rob
how did you download it?

---

### Post by Rob625 on 2010-09-16
> how did you download it?
I used Firefox to Google Chrome, then clicked to open google-chrome-stable-current-i386.deb with "GDebi Package Installer (default)". 

It said "same version is already installed". 

True, but how  do I get to use it?

- Rob

---

### Post by JKyleOKC on 2010-09-16
If all Windows users were as security-conscious as you, there would be much less malware in the wild!

Unfortunately, this specific security precaution of running without administrative privilege isn't necessary with Linux, because only one special user (named "root") has such privileges. In Ubuntu's distribution, the root user is disabled, and the first user created is allowed to gain temporary root status by prefixing the command with "sudo" (or for a graphic interface such as Nautilus, "gksudo"). The Windows equivalent is the "run as" option shown on context menus.

Also, rather than all configuration being crammed into a system-wide registry, Linux stores specific users' configuration details as hidden files in their home directories. As you've discovered, this prevents one user from general access to the menus customized by another user.

Your admin0 account is the only one currently permitted to use "sudo" for installation and general system configuration chores, but you can add this capability to "rob" by making rob a member of the "admin" group. You can only do this when logged in as admin0, but one you've done the addition, you won't need the admin0 account any more. For everyday operation, both accounts are perfectly safe. The requirement for the "sudo" prefix, which asks for your login password each time you use it (but won't ask again for 15 minutes after the first use), protects the system itself.

The Chrome browser may well be available to "rob" with no need to make any changes other than adding it to rob's own menu, or if you prefer putting a launcher for it on the panel (like the Windows taskbar) or desktop. To find out just where the program files for it are, open a terminal window and type "which chrome" (if that's the program name; I don't use it myself, and Linux is case-sensitive--"chrome" and "Chrome" are two different names, not the same as in Windows).

It'll take a while to get used to the Linux way of doing things, which in many cases (such as being case-sensitive) is very different from Windows. However before long it'll feel quite comfortable. Welcome to the free software world!

---

### Post by sandyd on 2010-09-16
> **Rob625 said:**
> I used Firefox to Google Chrome, then clicked to open google-chrome-stable-current-i386.deb with "GDebi Package Installer (default)". 

It said "same version is already installed". 

True, but how  do I get to use it?

- Rob
Try running
```

google-chrome
```
in a terminal

---

### Post by Calash on 2010-09-16
It is not under Applications->Internet?

It should be there no matter what account you install it under.

Lets check and see if it is installed correctly.

Hold the alt key and tap the F2 button.  You will get Run Application line.  Type the following there.

```

google-chrome

```

Let us know if it runs or not under your user account.


On a side note:  The Software Center is the preferred starting point to locate and install software.  It takes a bit of getting use to coming from Windows but in the long run it is the better option for supportability.

A .deb file is the next best option but unless the application has automatic update checking built in you will have to keep it up to date by hand.

---

### Post by Rob625 on 2010-09-16
Got it now, thanks!

> Hold the alt key and tap the F2 button. 
This worked: I typed "go" and it filled in "google-chrome".

That let me start Chrome.

Next, I rightclicked Applications, Edit Menus and added an item with Command google-chrome. The thing is, before, I didn't know what to type as Command in Create Launcher.

>  you can add this capability to "rob" by making rob a member of the "admin" group
I take your point, but I think I'll try to stick to rob not being an admin, until I get more used to things. At some point I may give accounts to my wife and children, and they won't have these privileges; I want to know what their experience will be.

> open a terminal window
How do I do that?

Is there an equivalent of Windows Start, All Programs, where I can browse for apps?

Thanks
Rob

---

### Post by JKyleOKC on 2010-09-16
> **Rob625 said:**
> I take your point, but I think I'll try to stick to rob not being an admin, until I get more used to things. At some point I may give accounts to my wife and children, and they won't have these privileges; I want to know what their experience will be.I think you missed my main point, which is that **neither** admin0 nor rob are admin accounts in normal operation. Unlike Windows, Linux user accounts do not have admin privileges by default.

What adding rob to the "admin" group would do is simply allow rob to request admin privilege temporarily.

Since Windows doesn't make a big deal of user groups, their function isn't widely known. The purpose is to allow special permissions to some, but not all, of the users. Windows does have such groups, in NT and XP at least, but you have to go behind the scenes as system administrator to find them. In Linux, every user has a primary group and can belong to any other group or groups. Every file has three sets of permissions: one set for the file owner, one set for the owning group, and a third for everyone else. It's similar to the Windows ACL approach, but not identical to it.

Incidentally, I did a bit of searching for the menu details, and found a document at /usr/share/doc/menu/html/index.html which describes in great detail how the Debian menu system works, and how to modify it. It's a bit opaque with jargon, but no worse than say the manuals for the PDP 11/70 or the IBM 1620 were :) and while it claims that the hierarchy must follow the official Debian structure, there's nothing that will keep it from working if you replace that with your own.

However, you may want to look closely at the "standard" Linux directory structure before making major changes, since it does reflect a very different approach from that used by Windows or most any mainframe system. For instance, shared libraries are usually either in /lib or /usr/lib (those that have been customized for a distribution go into /usr/lib). If you move them elsewhere, programs may stop working -- and using links, either symbolic or hard ones, can also introduce gremlins.

---

