---
title: "url desktop shortcut"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by als123 on 2010-01-22
Hello all,

I was curious if it is possible to put a shortcut on the desktop to a website I visit on a regular basis.  I'd like to click this link that opens firefox and goes directly there.

Thanks for any help with this issue.

---

### Post by Enigmapond on 2010-01-22
Just save the page as an .html to you desktop and make sure that FF is set as default to open this type of file.

---

### Post by xpod on 2010-01-22
With Firefox i just drag the sites icon from directly before the address onto the desktop.It opens again with Firefox without any further configuration.

---

### Post by als123 on 2010-01-22
Thank you both for your responses.  Xpod's worked the best of the two, giving me only one icon instead of the two that Enigmapond's did.

thanks again

---

### Post by SPazzo on 2010-01-22
Be sure to mark your thread as solved in the Thread Tools.

---

### Post by jev242 on 2010-12-09
I'd like to re-open the issue
if you drag and drop a URL from Firefox to the Desktop or inside Nautilus, you get a file named "Link_to_whatever_that_web_site's_name_is"

but if you view the same file through a Terminal or through an xTerm, then the file name appears to be "Link_to_whatever_that_web_site's_name_is.desktop"

so there is a ".desktop" part of the file name that is hidden in the Desktop or in Nautilus
how do I make the complete filename to appear in the Desktop or in Nautilus ???

---

### Post by ticket on 2011-01-02
I'd like to add:

The icon you get is different to the one you get if you drag the url to the gnome taskbar first, and then from there to the desktop.

The second method gives a proper launcher, but 'Properties' reports both types of icons to be "HTML document (text/html)" and the file permissions of both are reported as unknown.

Wish I knew what was going on!

---

### Post by jev242 on 2011-01-03
I just verified that what "ticket" said

so, here's the complete observation for someone who has the knowledge to answer this question:

the test link is [www.google.com](www.google.com) accessed with Firefox

task1:
drag and drop the [www.google.com](www.google.com) URL from Firefox to the Ubuntu (10.10) desktop or inside a Nautilus file explorer window

it will appear as a yellow star named "Link to Google"
but when the same filename is viewed through a Terminal or an xTerm the name is "Google.desktop" (the "Link to" portion is actually gone despite of what I reported by mistake in my previous post)

when "Link to Google" or "Google.desktop" is viewed in a text editor it contains the following lines:

------>
[Desktop Entry]
Encoding=UTF-8
Name=Link to Google
Type=Link
URL=http://www.google.com/
Icon=gnome-fs-bookmark
<------

task2:
drag and drop the [www.google.com](www.google.com) URL from Firefox to the Ubuntu (10.10) Gnome panel (taskbar) - a little globe will appear in the Gnome panel- and then drag that globe to the desktop

the link now looks like a globe and it is named "Google"
a Terminal or an xTerm shows the name as "www.google.com.desktop"

when "Google" or "www.google.com.desktop" is viewed in a text editor it contains the following lines:

------>
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Name=Google
Comment=Open URL: [http://www.google.com/](http://www.google.com/)
Icon=applications-internet
Name[en_US]=Google
Comment[en_US]=Open URL: [http://www.google.com/](http://www.google.com/)
Icon[en_US]=applications-internet
URL=http://www.google.com/
Type=Link
<------

obviously, this is a man made situation and therefore there is an explanation (which I don't have)

---

### Post by ticket on 2011-02-10
One thing I notice is that running 'properties' on a firefox url shortcut, shows it as type "HTML document (text/html)", whereas I think firefox (or gnome or nautilus, whichever is responsible) should have created it as type "application/x-desktop"

---

### Post by jev242 on 2011-02-15
I wonder if this is the right thread to ask the questions, it has been over 2 months now but no-one has posted any possible answers to my question ........

---

### Post by ticket on 2011-04-09
Bump for an answer.

---

### Post by bobodod on 2011-05-23
This has been an issue for a long time:

[https://bugs.launchpad.net/ubuntu/+source/mozilla-firefox/+bug/194191](https://bugs.launchpad.net/ubuntu/+source/mozilla-firefox/+bug/194191)


My comments on it were all here before I found that earlier bug report:

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/475587](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/475587)

---

### Post by jev242 on 2011-08-04
thanks [bobodod]("http://ubuntuforums.org/member.php?u=287046"), at least there has been formal bug reports
my next question now is, how, when and where do I find about the fixes, if any ?

---

### Post by Fotja on 2012-09-14
check this:
[http://www.addictivetips.com/ubuntu-linux-tips/how-to-create-desktop-shortcuts-for-websites-in-ubuntu-11-10-tip/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-create-desktop-shortcuts-for-websites-in-ubuntu-11-10-tip/)

---

### Post by sandyd on 2012-09-14
**Necromancy - Thread closed**
Please do not post in threads more than a year old as per the Ubuntu Forums Code of Conduct.([http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy))

Thanks!

---

