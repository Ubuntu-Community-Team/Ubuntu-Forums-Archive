---
title: "Firefox Helper Applications - Skype"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by rigg-a-mortice on 2009-09-16
I am trying to download skype to run on my 9.04 installation. I am using Firefox 3.5.2

(Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.2) Gecko/20090803 Ubuntu/9.04 (jaunty) Shiretoko/3.5.2)

When I try to download skype I receive the following message - /tmp/skype-ubuntu-intrepid_2.1.0.47-1_i386-2.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.

I would appreciate someone explaining this to me in plain English and also telling me in detail what I need to do to overcome the problem.

Many thanks.

---

### Post by sisco311 on 2009-09-16
go to Edit -> Preferences -> Applications, search for "DEB files" and change the *Action* to *Use gdebi-gtk*.

gdebi-gtk is located under /usr/bin.

---

### Post by ashwinhgtx on 2009-09-16
> **rigg-a-mortice said:**
> I am trying to download skype to run on my 9.04 installation. I am using Firefox 3.5.2

(Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.2) Gecko/20090803 Ubuntu/9.04 (jaunty) Shiretoko/3.5.2)

When I try to download skype I receive the following message - /tmp/skype-ubuntu-intrepid_2.1.0.47-1_i386-2.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.

I would appreciate someone explaining this to me in plain English and also telling me in detail what I need to do to overcome the problem.

Many thanks.

Instead of selecting 'Open', select 'Save' and save it on your desktop. 

After that just double click the .deb installer file. Enter your password and start talking.

---

### Post by rigg-a-mortice on 2009-09-16
Many thanks, worked once I got my head around it, I am not used to LINUX file structures.

---

