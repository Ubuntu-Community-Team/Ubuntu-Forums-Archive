---
title: "How do i install Adobe Reader 9.0?"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by goldblattster on 2009-05-16
I downloaded Adobe Reader from Adobe's website and it came as a .bin file. Ubuntu cannot open this. Therefore, how can I install Acrobat Reader?

---

### Post by philinux on 2009-05-16
system>admin>synaptic package manager.

Search acroread. 

Install from there.

---

### Post by doug1212 on 2009-05-16
I think that the Canonical partner repo has to be activated in software sources.
Doug.

---

### Post by gandaran on 2009-05-16
> **goldblattster said:**
> I downloaded Adobe Reader from Adobe's website and it came as a .bin file. Ubuntu cannot open this. Therefore, how can I install Acrobat Reader?
you have to enable the archive-canonical partner repository in software sources then install from synaptic or command line apt-get.

---

### Post by goldblattster on 2009-05-16
Thank you for your reply, good sir!
The thing is, when I search acroread in synaptic, there arent any entries (see attached screenshot)
apt-get cannot find anything either.

---

### Post by Paqman on 2009-05-16
Acroread is in [Medibuntu]("http://www.medibuntu.org/") isn't it?

I don't bother personally. Evince will read pdfs quite happily and it's installed by default.

---

### Post by mikewhatever on 2009-05-16
Acroread is in Medibuntu repository, so you need to add Medibuntu to you sources.
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

---

### Post by goldblattster on 2009-05-16
thank you good sirs/maams

---

### Post by PA_Dummy on 2009-05-16
Another solution:

When you see the following in the Adobe site:


+++++++++++++++++++++++++++++++++++++++
Adobe Reader
Adobe Reader 9.1

Linux (.bin), English

Different language or operating system?
43.2 MB
+++++++++++++++++++++++++++++++++++++++++++

DO NOT ACCEPT THE .bin file

Click on: Different language etc,

On the next screen select "Linux 386 .DEB"

Download the .deb file into a directory..  

Run sudo dpkg -i  *.deb

Look under "Applications" for the menu entry.

_

---

### Post by gandaran on 2009-05-16
> **mikewhatever said:**
> Acroread is in Medibuntu repository, so you need to add Medibuntu to you sources.
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)
not anymore for jaunty 9.04!

---

### Post by mikewhatever on 2009-05-16
> **gandaran said:**
> not anymore for jaunty 9.04!

You might want to check that again.
[Binary packages available in jaunty]("http://packages.medibuntu.org/jaunty/index.html").
It's just that the version is not 9.0, but an older one.

---

### Post by gandaran on 2009-05-16
> **mikewhatever said:**
> You might want to check that again.
[Binary packages available in jaunty]("http://packages.medibuntu.org/jaunty/index.html").
It's just that the version is not 9.0, but an older one.
I have theres no acroread from medibuntu in synaptic, so you check again! 
if you have acroread in the medibuntu repo in jaunty then you have added the wrong medibuntu ubuntu version repo to jaunty sources lists.
acroread in jaunty is only available from the canonical partner repo now!

---

### Post by Paqman on 2009-05-17
> **gandaran said:**
> not anymore for jaunty 9.04!

Here's the [full list of the Jaunty repos]("http://packages.ubuntu.com/jaunty/allpackages"). No acroread.

Medibuntu is well worth subscribing too anyway. Lots of good stuff in there.

---

### Post by philinux on 2009-05-17
On mine, Jaunty, it's in Main.

However on further inspection it's coming from the partner repo under third party software.

---

### Post by goldblattster on 2009-05-17
> **PA_Dummy said:**
> Another solution:

When you see the following in the Adobe site:


+++++++++++++++++++++++++++++++++++++++
Adobe Reader
Adobe Reader 9.1

Linux (.bin), English

Different language or operating system?
43.2 MB
+++++++++++++++++++++++++++++++++++++++++++

DO NOT ACCEPT THE .bin file

Click on: Different language etc,

On the next screen select "Linux 386 .DEB"

Download the .deb file into a directory..  

Run sudo dpkg -i  *.deb

Look under "Applications" for the menu entry.

_

Thank you! I overlooked that link...

---

### Post by sanika on 2009-07-02
You can download the latest version of acroread from [ftp://ftp.adobe.com/pub/adobe/reader/unix/9.x/9.1.2/](ftp://ftp.adobe.com/pub/adobe/reader/unix/9.x/9.1.2/). There is an excellent post about installer formats [http://blogs.adobe.com/acroread/](http://blogs.adobe.com/acroread/). The post mentions the commands to be used for different installers. For the .bin installer, do the following:

   chmod +x AdbeRdr9.1.2-1_i486linux_enu.bin 
  ./AdbeRdr9.1.2-1_i486linux_enu.bin --install_path=<path_where_you_want_to_install_acror  ead>. By default, acroread will be installed inside /opt.

---

### Post by poetofzwan on 2009-10-14
In karmic beta, I found that acroread was found in partner repos that can be enables from system -> administration -> software sources.

---

