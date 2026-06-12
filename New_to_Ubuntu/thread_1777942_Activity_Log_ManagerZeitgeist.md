---
title: "Activity Log Manager/Zeitgeist"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by avnd on 2011-06-08
Hello there!  I was searching for an application that did something like what CCleaner does in Windows. I came across this application called 'Activity Log Manager'. Here's the link.   [http://ubuntu4beginners.blogspot.com/2011/05/clear-tweak-zeitgeist-historys-settings.html](http://ubuntu4beginners.blogspot.com/2011/05/clear-tweak-zeitgeist-historys-settings.html)  I'm not sure if I'm safe following commands with sudo without knowing what it does. I wasn't able to find it in 'Ubuntu Software Center' or in the 'Synaptic Package Manager' which makes me all the more iffy. Can anyone who knows better offer me some guidance here?  Thanks!

---

### Post by Paqman on 2011-06-08
What you probably want is something like Bleachbit, which you can get through the Software Centre.

---

### Post by madmax75 on 2011-06-08
Yep, Bleachbit is great.

---

### Post by jaacko on 2011-06-08
Hi!

I looked at the link on your post and decided what the commands listed there do.

Why activity-log-manager can't be found in the Software center is because it's not in the official repositories. So to install it, you first need to add the repository to your computer. That's what the first line of the code does.

The second line first updates your local database of packages, i.e. the list of available packages (and their versions) in the repositories. Then the rest of the second line then upgrades your installed packages in case newer versions exist in the repositories.

The repository added in the first line containt a newer version of the zeitgeist-daemon (activity-log-manager needs the newer version to work). What the third line of the code does is that it shuts down currently running zeitgeist-daemon and then restarts it so that the new version kicks in.

Finally, the last line installa the activity-log-manager package.

```
sudo add-apt-repository ppa:zeitgeist/ppa
sudo apt-get update && sudo apt-get upgrade
zeitgeist-daemon --replace

sudo apt-get install activity-log-manager

```

I have the activity-log-manager installed on my own computer (from that same repository) and it's working fine. What the program does is that it let's you control what kind of data the zeitgeist daemon logs.

Hope this helps.

---

### Post by avnd on 2011-06-08
Thank you for your replies Jaacko, Madmax75 and Paqman.    I eventually tried both and 'Bleachbit' and 'Activity Log Manager'. Both were pretty simple and nice with Bleachbit offering me finer choices a la CCleaner.     Can someone please clear one thing to me? Am I right when I feel more confident installing something from the 'Ubuntu Software Centre' or 'Synaptics Package Manager' than when installing something that's not in the repositories?    Thanks!   P.S. I'm sorry about the way the post is cluttered without paragraphs. I try editing this but it ends up in the same way. I start typing in a new line after pressing 'Enter', but it ends up in the same line. I'd also love a tip to correct this (if it's not out of place). :)

---

### Post by wildmanne39 on 2011-06-08
> **avnd said:**
> Thank you for your replies Jaacko, Madmax75 and Paqman.    I eventually tried both and 'Bleachbit' and 'Activity Log Manager'. Both were pretty simple and nice with Bleachbit offering me finer choices a la CCleaner.     Can someone please clear one thing to me? Am I right when I feel more confident installing something from the 'Ubuntu Software Centre' or 'Synaptics Package Manager' than when installing something that's not in the repositories?    Thanks!   P.S. I'm sorry about the way the post is cluttered without paragraphs. I try editing this but it ends up in the same way. I start typing in a new line after pressing 'Enter', but it ends up in the same line. I'd also love a tip to correct this (if it's not out of place). :)
Hi, yes it is safer to install packages from the software center or synaptic, I almost never install anything that is not in one of those two, however there will be time probably that you might want to.

---

### Post by 3rdalbum on 2011-06-09
Activity Log Manager just helps you limit what sorts of file opening operations get logged. These are logged to make Ubuntu's search system smarter and more relevant. Removing these logs will not make your system faster - in fact, it will make it more time-consuming for you to find files on your computer.

If you have a concern about certain "embarassing" file opens being logged and searchable, then go ahead and use Activity Log Manager. But the way you were comparing it to CCleaner sounded like you were looking for something to make your system faster.

There's very little maintenance you need to do on Ubuntu, it tends to just keep running quickly forever.

---

