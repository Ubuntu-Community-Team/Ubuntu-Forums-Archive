---
title: "Can't open .deb package?"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by iggy pop on 2010-02-14
Why can't i open a .deb package? I wanted the latest version of clamtk so i downloaded the latest version 'clamtk_4.23-1_all.deb' to my desktop in the form of a .deb package. I double clicked on the package and nothing happened so i then right clicked on the package and selected: Open with GDebi Package Installer and once again nothing happened. Could someone enlighten this old fool please.

---

### Post by wojox on 2010-02-14
Open your terminal and try:

```
sudo dpkg -i downloaded_package.deb
```

```
sudo apt-get -f install
```

---

### Post by Sir Jasper on 2010-02-14
Hi,

I do not know the answer to your question. However, you might try to download the debian version of Avast to your desktop and double click on that and see if it appears (probably under Accessories).

The avast detection rate is some 10% higher than clam´s (95%+ v 85%+) in independent tests. Also you should find its on demand scan is significantly (i.e. many times) faster.

However, the twice daily updates of Avast are full (so broadband is ideal) whereas clam is incremental (better for dial-up).

You can of course use both since as both are on-demand scanners there is no conflict.

I use Wine, so I only check my Home directory. My opinion is - if you need protection use clam, avast or another product, but if you are trying to protect any windows-user contacts then your efforts are likely to be as ¨a drop in the ocean¨ and they need their own protection.

My regards

Added:

Just a thought - I do not know what is best - but did you use Synaptic, or another method, to uninstall the old version first?

---

### Post by audiomick on 2010-02-14
> **iggy pop said:**
> ...downloaded the latest version 'clamtk_4.23-1_all.deb' to my desktop in the form of a .deb package. I double clicked on the package and nothing happened so i then right clicked on the package and selected: Open with GDebi Package Installer and once again nothing happened...
for what it is worth, as far as I know, that should have worked...:confused:

---

### Post by iggy pop on 2010-02-14
Have tried what wojox suggested and got this output:

dpkg: error processing downloaded_package.deb (--install):
cannot access archive: no such file or directory
Errors were encountered while processing:
downloaded_package.deb

Yes i did use Synaptic to remove the older version first

---

### Post by wojox on 2010-02-14
Sorry. You need to go into the directory you downloaded it to and run:

```
sudo dpkg -i clamtk_4.23-1_all.deb
```

---

### Post by iggy pop on 2010-02-14
I opened a terminal and typed: sudo dpkg -i clamtk_4.23-1_all.deb
and it appeared to be installing but i did notice the text: Errors were encountered while processing clamtk.

I did however find the virus scanner under Applications but for some reason it wouldn't start. So i went back to the terminal and typed: clamtk and got the following output:

iggy@iggy-desktop:~$ clamtk
Can't locate Net/DNS.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/perl5/ClamTk/App.pm line 18.
BEGIN failed--compilation aborted at /usr/share/perl5/ClamTk/App.pm line 18.
Compilation failed in require at /usr/share/perl5/ClamTk/Prefs.pm line 18.
BEGIN failed--compilation aborted at /usr/share/perl5/ClamTk/Prefs.pm line 18.
Compilation failed in require at /usr/bin/clamtk line 19.
BEGIN failed--compilation aborted at /usr/bin/clamtk line 19.
iggy@iggy-desktop:~$

---

### Post by iggy pop on 2010-02-14
Have now got clamtk up and running. Thanks for all the help and advice

---

