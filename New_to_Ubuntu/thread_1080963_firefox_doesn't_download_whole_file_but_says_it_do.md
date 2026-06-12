---
title: "firefox doesn't download whole file but says it does"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by Brandel Valico on 2009-02-26
Okay here's one that has me stumped. I have two computers where the downloads in Firefox will say they are 100% done. But they don't download the entire file. Instead they only download roughly 10% of it. 

Anyone have any idea's why this may be happening. One is running Hardy (fresh install) the other is Intrepid ( upgraded from Hardy not a fresh install) I'm thinking it's a Firefox issue and will be trying to un-install and re-install Firefox on both. But am curious if anyone else has seen this issue.

***EDIT*** Figured out the site being downloaded from had a faulty server sending false information. ***

---

### Post by Philo1 on 2009-02-26
I haven't heard anything of this manner with ff and am quite puzzled. Are you using the default ff download manager in ff or is it add on your using? What about if you open a file such as a .odt or something rather than saving it, does that work? I realize your download status is the issue your trying to resolve, however if you choose save vs open with does anything differ occur...same result or what exactly?

---

### Post by Brandel Valico on 2009-02-26
The Intrepid computer uses the default download manager. The Hardy one uses the Download bar plugin. (Where instead of opening the new window it opens a taskbar at the bottom to show the download progress.) Both are set to save the file. It opens files fully if I set them to open say pdf's or the like. Defiantly a weird thing. My other two computers work just fine with no issues using FF.

---

### Post by kidux on 2009-02-26
I've seen that happen before if the data stream gets interrupted. I usually try to use wget if it's a large file. All you need to do is copy the link location (right click) then open a terminal and type wget, then right click and paste the link. It should download without any problems, but be warned it will save in whatever the CWD is.

---

### Post by Philo1 on 2009-02-26
I would imagine that your not running any AV software, right?

---

### Post by Philo1 on 2009-02-26
> **kidux said:**
> I've seen that happen before if the data stream gets interrupted. I usually try to use wget if it's a large file. All you need to do is copy the link location (right click) then open a terminal and type wget, then right click and paste the link. It should download without any problems, but be warned it will save in whatever the CWD is.

Kidux - For clarification purposes, data stream being that which is interrupted as far a drop in connection, to much traffic or what exactly? wget is simply a work around GNU app I'm guessing, but I'm the intuitive type and am just seeking clarification as far as why ff bolos. Any clue -- thanks --

---

### Post by kidux on 2009-02-26
> **Philo1 said:**
> Kidux - For clarification purposes, data stream being that which is interrupted as far a drop in connection, to much traffic or what exactly? wget is simply a work around GNU app I'm guessing, but I'm the intuitive type and am just seeking clarification as far as why ff bolos. Any clue -- thanks --
Dropped connection certainly, packet collisions on the network, or simply bad data from the website itself. Usually, my trouble is the latter with the webhost sending incomplete header information or FF interpreting the header info wrong, which tells FF it has all the data when it only has partial.

Wget is a CLI tool that acts much like a torrent program in that it will retry the download until it gets the full amount, and a great feature is that it allows you to continue the download even after data interruption, such as from a power outage. It's also available for Windows as well.

---

### Post by Philo1 on 2009-02-26
Good deal, thanks for the update.

---

### Post by Brandel Valico on 2009-02-26
Nope no AV program installed.

Will give Wget a try if the re-install of FF doesn't do the trick.

---

