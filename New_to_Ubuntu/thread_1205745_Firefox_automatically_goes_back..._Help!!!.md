---
title: "Firefox automatically goes back... Help!!!"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by Daedalus6 on 2009-07-06
Hello;

I have been testing the Linux waters for about a year, and made the full switch a few months ago. (Free from Windows, free at last!) However, am finally hitting a snag that I cant fix on my own or with pre-existing forum topics. Any help would be much appreciated! 

Here is the problem: when using Firefox, the browser automatically goes back to whatever page was first opened in that tab. Originally this only seemed to happen when typing in a text entry field (frustrating enough), but now this occurs whenever I open a new page in the same tab. So, it goes to the new page for a split second and then immediately returns to the old one. Clicking the forward button or any other link does the same thing. This makes the browser essentially unusable, had to find a different computer for this post.

Already tried:
- Reinstalling the firefox package (no change)
- Fussing with keyboard & shortcut settings (couldnt find anything that made a difference)
- Looking online for help in forums (seems to be a unique/undocumented problem)
- Slamming head on desk ](*,)(no result other than mild physical discomfort)

Details:
- Ubuntu 9.04
- Firefox 3.0.11
- Computer: homemade desktop

I have a relatively clean and recent install of Ubuntu. I have used other flavors, and even the same flavor before without having this problem. No other programs are behaving strangely.

Any ideas on whats causing this?

---

### Post by Celauran on 2009-07-06
No clue what is causing this, though it could be a corrupted file in your ~/.mozilla directory. Try either deleting or renaming that directory and see if the problem persists.

---

### Post by LowSky on 2009-07-06
go to your home folder, hit the key combo CTRL+H to show hidden files

find the .mozilla folder andopen it to find the firefox profile and delete it. things should go back to normal

please save your bookmarks prior to deleting anything, you will lose them

---

### Post by Daedalus6 on 2009-07-06
Okay, I tried it...

When opened, Firefox now rapidly flickers between two different start pages. It happens a bit to fast to actually copy down the addresses. And, I am now seeing the same behavior in the folder browser. #-o

Apparently this is a bigger problem than Firefox. I had read in some other forum topics that people had similar issues with their mouse or keyboard reading weird input, so I tried a little experiment:

- With the mouse unplugged, using the keyboard to navigate, the problem was temporarily fixed but returned within a few minutes.
- With the keyboard unplugged, using the mouse to navigate, the problem appeared right away.

So, this seems all manner of screwed up. Thoughts?

---

### Post by lovinglinux on 2009-07-06
> **Celauran said:**
> No clue what is causing this, though it could be a corrupted file in your ~/.mozilla directory. Try either deleting or renaming that directory and see if the problem persists.

It's usually a firefox corrupted profile, but there are other mozilla applications that store their profiles inside ~/.mozilla, so deleting it is not recommended and it's unnecessary, since you can achieve the same results by deleting the firefox folders inside it.

Nevertheless, there also no reason to delete the entire profile if you can pinpoint the culprit inside it. Most common Firefox issues can be traced back to a single profile file. See the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567) for common symptoms and solutions.

---

### Post by NoBugs! on 2009-07-06
Have you tried running
```
firefox --safe-mode
```

---

### Post by lovinglinux on 2009-07-06
> **Daedalus6 said:**
> Okay, I tried it...

When opened, Firefox now rapidly flickers between two different start pages. It happens a bit to fast to actually copy down the addresses. And, I am now seeing the same behavior in the folder browser. #-o

Apparently this is a bigger problem than Firefox. I had read in some other forum topics that people had similar issues with their mouse or keyboard reading weird input, so I tried a little experiment:

- With the mouse unplugged, using the keyboard to navigate, the problem was temporarily fixed but returned within a few minutes.
- With the keyboard unplugged, using the mouse to navigate, the problem appeared right away.

So, this seems all manner of screwed up. Thoughts?

I had a similar problem in Hardy. When I right-clicked anything inside Firefox or Nautilus, the system would select a random option from the context menu. The problem was mitigated if I hold down the right button for a second, instead of just clicking. Unfortunately, I don't know a solution or the reason why this happened and this problem went away and came back sometimes without explanation.

I'm not experiencing this problem since I installed Jaunty.

---

### Post by Daedalus6 on 2009-07-06
Running Firefox in safe mode and clearing the .mozilla folder doesnt have any effect on the problem. It is behaving as if something is sending a constant command to go back, which is affecting the folder browser and even other programs like Rhythmbox. 

Weird thing is, the experiment earlier with the mouse and keyboard must mean that whatever is constantly telling the computer to go back is coming from the computer itself...

At this point, I am resorting to the brute force solution of a clean install. Hopefully this fixes the problem, and as I reinstall the various things that may have broken it, testing between each one will show exactly what messed it up in the first place.

---

### Post by lovinglinux on 2009-07-06
> **Daedalus6 said:**
> Running Firefox in safe mode and clearing the .mozilla folder doesnt have any effect on the problem. It is behaving as if something is sending a constant command to go back, which is affecting the folder browser and even other programs like Rhythmbox. 

Weird thing is, the experiment earlier with the mouse and keyboard must mean that whatever is constantly telling the computer to go back is coming from the computer itself...

At this point, I am resorting to the brute force solution of a clean install. Hopefully this fixes the problem, and as I reinstall the various things that may have broken it, testing between each one will show exactly what messed it up in the first place.

Do you use wireless network and a wireless mouse at the same time? Those little rats can "move around by themselves" due to the router wireless signal interference. Turning off the mouse doesn't help. You have to unplug the wireless receptor.

I have a wireless mouse that I simple can't use, due to this problem.

---

### Post by Daedalus6 on 2009-07-06
Nope, no wireless mouse or keyboard... 

Just did the clean install, booted Firefox and it started spazzing out again, flipping rapidly between two home pages. Folder browser had the same problem of immediately returning to the original location when navigating anywhere else.

Anyone know what is happening?

---

### Post by lovinglinux on 2009-07-06
> **Daedalus6 said:**
> Nope, no wireless mouse or keyboard... 

Just did the clean install, booted Firefox and it started spazzing out again, flipping rapidly between two home pages. Folder browser had the same problem of immediately returning to the original location when navigating anywhere else.

Anyone know what is happening?

Do you have a separate home partition?

Since you did a fresh install of Ubuntu, I think the problem might be related to your settings on your home partition. You could try to create a new user and log in with that account to see if the problem persists.

---

### Post by Daedalus6 on 2009-07-06
Creating a new user worked for about 30 seconds before having the same problem.

After reverting to 8.04 everything seems to be working fine... hopefully no-one else will have this problem.

---

