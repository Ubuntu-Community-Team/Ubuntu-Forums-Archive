---
title: "Need Database for Addresses."
date: 2010-11-09
forum: New to Ubuntu
---

### Post by gordon33 on 2010-11-09
Hello All

I will need a Database for addresses and a membership number for an organization.  I see OOo has a Database but I can not find one in my Ubuntu 10.04.  How can I get The OOo Database going on my computer?

Gordon

---

### Post by SuaSwe on 2010-11-10
I believe you should be able to install it using the Synaptic Package Manager (System > Administration) or apt-get via Terminal. Search for it in SPM and see what comes up. :)

---

### Post by jtarin on 2010-11-10
Go to System>Administration>Synaptic package Manager and enter the search term ```
OpenOffice.org Base
```

---

### Post by gordon33 on 2010-11-10
Hello SuaSwe, and jtarin

Thank you for your help.

I went to System>Administration>Synaptic Package Manager and enter the search term Code:  OpenOffice.org-Base.

I saw OpenOffice.org-base in the Synaptic Package Manager list.  When I went to Mark OpenOffice.org-base for installation I got a box with a warning I took a screen shot of the warning that came up (please see attachment.  Is this Warning any thing I need to be concerned about?  Or, should I do the Installation along with the Additional Required Changes.

I noticed OpenOffice.org-base-core was installed.  Does OpenOffice.org-base-core give me the database I need?  If so how I would I access it?

Gordon33

---

### Post by jtarin on 2010-11-10
I don't think there is anything to be concerned about.

---

### Post by gordon33 on 2010-11-10
Hello jtarin

What about OpenOffice.org-base-core was installed. Does OpenOffice.org-base-core give me the database I need? If so how I would I access it?

Gordon33

---

### Post by gordon33 on 2010-11-10
Hello jtarin

I got additional warnings when I went to Apply the Marked OpenOffice.org-Base (please see attachment).  It looks so serious.

Gordon33

---

### Post by HermanAB on 2010-11-10
You can also try Rekall:
[http://www.rekallrevealed.org/kbExec.py](http://www.rekallrevealed.org/kbExec.py)

Rekall is a front end that needs a SQL backend to function.

and Gaby:
[http://www.0d.be/projects/gaby/](http://www.0d.be/projects/gaby/)

Gaby is very nice and simple and may be in the repos.  Gaby is probably what you are really looking for.

and maybe you can get this page about OOo Base to load:
[http://homepage.ntlworld.com/garryknight/linux/oodbase.html](http://homepage.ntlworld.com/garryknight/linux/oodbase.html)

---

### Post by gordon33 on 2010-11-10
Hello HermanAB

Thank you I will look in to the options you provided.

Gordon33

---

### Post by jtarin on 2010-11-10
> **gordon33 said:**
> Hello jtarin

I got additional warnings when I went to Apply the Marked OpenOffice.org-Base (please see attachment).  It looks so serious.

Gordon33That only means the package manager cannot authenticate the source, but stop and think.....it is in one of the repositories that is in your apt listings so it should be no problem. Remember...this is not MS Windows.

---

### Post by gordon33 on 2010-11-12
Hello jtarin

Thank you, I will install OpenOffice.org-base and see what happens.


Gordon33

---

