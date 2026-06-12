---
title: "'Failed to download repository information'"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by s1wood on 2011-03-13
For the last couple of weeks both Update Manager and Synaptic have been refusing to reload and have been telling me there is a problem with my repository. Software Center has been refusing to authenticate items. The odd thing is that new updates have been appearing as normal and installing.
When I click Check on Update manager it says 'Failed to download repository information' - check your internet connection' and the Details are
>W:Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg](http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
, E:Some index files failed to download, they have been ignored, or old ones used instead.<

which is pretty much what Synaptic says.

I have tried uninstalling and reinstalling Synaptic from the terminal but it makes no difference.

Any suggestions?

Susan

---

### Post by smileyacid on 2011-03-13
Have you recently added any new repositories?
Have you tried software source settings for alternate download mirror?

---

### Post by s1wood on 2011-03-14
I wouldn't know how to do either of those things! 
But now you mention it I think the problem may have started about the time I installed LibreOffice from the website - is that likely?

Susan

---

### Post by shamballa on 2011-03-16
From the Update Manager - click Settings and then enter your password, check the sources you are having trouble with.

---

