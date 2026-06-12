---
title: "Medibuntu Repository &quot;Error Message&quot;"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by pstefanini on 2009-10-05
I'm not sure what I have done.  I went to the Medibuntu "Repository HowTo" site and pasted in the text indicated in my terminal as directed.  (Note:  I wanted to try "Real Player" and understand this is what I needed to do):

*sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update*

I tried to install the software updates indicated but ran into the following error message:

[I]W: Failed to fetch [http://le-web.org/repository/dists/stable/Release.gpg](http://le-web.org/repository/dists/stable/Release.gpg)  Could not resolve 'le-web.org'

W: Failed to fetch [http://le-web.org/repository/dists/stable/main/i18n/Translation-en_US.bz2](http://le-web.org/repository/dists/stable/main/i18n/Translation-en_US.bz2)  Could not resolve 'le-web.org'

W: Some index files failed to download, they have been ignored, or old ones used instead.[/I]


I'm not sure what that means or what I may have done wrong.  Any guidance is appreciated!  Thank you in advance for any assistance!  Phil

---

### Post by pstefanini on 2009-10-05
Folks:  I may have figured this out myself... I unchecked the offending repository and the update downloaded. Thank you.

---

