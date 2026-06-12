---
title: "What is it with these updates?"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by PaulWhipp on 2009-01-07
I'm in trouble with the updates again. There is a question at the end of this tale, which I would be very grateful for help with.

Something about that little red arrow that appears in the top right corner always persuades me to click it and carry out the recommended updates to my 8.10 system.

It seems that it is almost always a bad thing to do because, more often than not, the updates fail and give me a load of corrupt package issues followed by a world of hurt as I try to put things right manually.

Apparently this shouldn't happen. Perhaps it only happens to me... I've switched sources, tried just going to 'main'... Whatever. I've done it again, and its done it again. First with perl and then with the next updates (I buried my head in the sand regarding the perl failure because the system still seemed to be working fine).

Now, the red arrow is there again but I can't give in to the temptation any more because the existing packages are in such a mess. Luckily my system still seems to work fairly well but I can no longer install any packages... possibly the safer scenario - but I really would like to update and perhaps one day load OO3...

I hate the idea of reinstalling. Not only does it take me an age to relocate and configure all my development tools (I'm still not sure how I got my lampp, mysql command lines etc. working in the first place - and don't get me started on the subversion command line and integration with Zend studio!).

In any event, re-installing feels wrong because the problem hasn't been fixed, its just been flushed away - washed into the distance ready to come and plague me again when I start clicking on that little red arrow once more.

So I try:

sudo dpkg --configure -a

I believe that this should tell me what's wrong and then I can re-install or fix things up bit by bit...

I wont bore you with the full report it provided. Suffice to say that it finished with:

Errors were encountered while processing:
 libgdbm-dev
 gawk
 ufw
 ghostscript
 perl
 cups-bsd
 tex-common
 m4
 libroman-perl
 cups
 prosper
 texi2html
 debiandoc-sgml
 texlive-base-bin
 preview-latex-style
 libsgmls-perl
 doc-base
 sgmlspl
 tipa
 autoconf
 texlive-common
 texlive-latex-extra
 libtext-format-perl
 automake
 lmodern
 texlive-latex-extra-doc
 texlive-humanities-doc
 texlive-base
 texlive-generic-recommended
 texlive-doc-base
 texlive-pstricks-doc
 dvipdfmx
 texlive-fonts-recommended
 texlive-pictures
 texlive-pictures-doc
 texlive-base-bin-doc
 texlive-latex-recommended-doc
 texlive-latex-recommended
 texlive-pstricks
 texlive-humanities
 texlive-latex-base
 texlive-fonts-recommended-doc
 texlive-generic-extra
 latex-beamer
 texlive-latex-base-doc
 latex-xcolor
 pgf

The list was shorter on my first attempt but I tried to use build-dep on doc-base which was in the original list. This resulted in all those extra texlive entries plus a few others.

So... my initial thought: try using apt-get to reinstall or fix one or two of the items on the list and see where that goes has dramatically increased the length of the list and the apparent problems.

Perhaps its perl. As a popular scripting language, I figure it could underlie a lot of other problems with installations. After a clean and an update, I try

sudo apt-get -f install perl

and I'm rewarded with a very similar list to the previous one plus another crash report and a few segmentation faults for good measure.

Does anyone know if/where there is a guide that can take me through repairing and reinstalling the broken packages effectively in an appropriate way?

---

### Post by Anicka on 2009-01-07
Sorry to hear that you find the updates problematic. But I think that you should bore us with the full message from "sudo dpkg --configure -a". That might help us to figure out where the root of the problem lies.

---

### Post by PaulWhipp on 2009-01-07
Thanks Anicka - no problem:

 
~ $ sudo dpkg --configure -a
Setting up libgdbm-dev (1.8.3-3) ...
Segmentation fault
dpkg: error processing libgdbm-dev (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gawk (1:3.1.6.dfsg-0ubuntu1) ...
Segmentation fault
dpkg: error processing gawk (--configure):
 subprocess post-installation script returned error exit status 139
Setting up ufw (0.23.2) ...
dpkg: error processing ufw (--configure):
 subprocess post-installation script killed by signal (Segmentation fault)
Setting up ghostscript (8.63.dfsg.1-0ubuntu6.1) ...
Segmentation fault
dpkg: error processing ghostscript (--configure):
 subprocess post-installation script returned error exit status 139
Setting up perl (5.10.0-11.1ubuntu2.2) ...
Segmentation fault
dpkg: error processing perl (--configure):
 subprocess post-installation script returned error exit status 139
Setting up cups-bsd (1.3.9-2ubuntu6) ...
dpkg: error processing cups-bsd (--configure):
 subprocess post-installation script killed by signal (Segmentation fault)
Setting up tex-common (1.11) ...
dpkg: error processing tex-common (--configure):
 subprocess post-installation script killed by signal (Segmentation fault)
Setting up m4 (1.4.11-1) ...
Segmentation fault
dpkg: error processing m4 (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of libroman-perl:
 libroman-perl depends on perl (>= 5.6.0-16); however:
  Package perl is not configured yet.
dpkg: error processing libroman-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups:
 cups depends on ghostscript; however:
  Package ghostscript is not configured yet.
dpkg: error processing cups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of prosper:
 prosper depends on ghostscript; however:
  Package ghostscript is not configured yet.
 prosper depends on tex-common (>= 0.7); however:
  Package tex-common is not configured yet.
dpkg: error processing prosper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texi2html:
 texi2html depends on perl; however:
  Package perl is not configured yet.
dpkg: error processing texi2html (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of debiandoc-sgml:
 debiandoc-sgml depends on libroman-perl; however:
  Package libroman-perl is not configured yet.
 debiandoc-sgml depends on perl (>= 5.6.0-16); however:
  Package perl is not configured yet.
dpkg: error processing debiandoc-sgml (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-base-bin:
 texlive-base-bin depends on perl; however:
  Package perl is not configured yet.
dpkg: error processing texlive-base-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of preview-latex-style:
 preview-latex-style depends on tex-common; however:
  Package tex-common is not configured yet.
 preview-latex-style depends on texlive-base-bin; however:
  Package texlive-base-bin is not configured yet.
dpkg: error processing preview-latex-style (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsgmls-perl:
 libsgmls-perl depends on perl (>= 5.6.0-16); however:
  Package perl is not configured yet.
dpkg: error processing libsgmls-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of doc-base:
 doc-base depends on perl (>= 5.6.0-16); however:
  Package perl is not configured yet.
dpkg: error processing doc-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sgmlspl:
 sgmlspl depends on libsgmls-perl; however:
  Package libsgmls-perl is not configured yet.
 sgmlspl depends on perl; however:
  Package perl is not configured yet.
dpkg: error processing sgmlspl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tipa:
 tipa depends on texlive-base-bin; however:
  Package texlive-base-bin is not configured yet.
dpkg: error processing tipa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of autoconf:
 autoconf depends on perl (>> 5.005); however:
  Package perl is not configured yet.
 autoconf depends on m4 (>= 1.4.8); however:
  Package m4 is not configured yet.
dpkg: error processing autoconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-common:
 texlive-common depends on tex-common (>= 1.8); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-extra:
 texlive-latex-extra depends on preview-latex-style; however:
  Package preview-latex-style is not configured yet.
 texlive-latex-extra depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libtext-format-perl:
 libtext-format-perl depends on perl (>= 5.6.0-16); however:
  Package perl is not configured yet.
dpkg: error processing libtext-format-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of automake:
 automake depends on autoconf (>= 2.60); however:
  Package autoconf is not configured yet.
dpkg: error processing automake (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lmodern:
 lmodern depends on tex-common (>= 1.10); however:
  Package tex-common is not configured yet.
dpkg: error processing lmodern (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-extra-doc:
 texlive-latex-extra-doc depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-extra-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-humanities-doc:
 texlive-humanities-doc depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-humanities-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-base:
 texlive-base depends on texlive-base-bin (>= 2007-13); however:
  Package texlive-base-bin is not configured yet.
 texlive-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-recommended:
 texlive-generic-recommended depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
 texlive-generic-recommended depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-generic-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-doc-base:
 texlive-doc-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-doc-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pstricks-doc:
 texlive-pstricks-doc depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-pstricks-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dvipdfmx:
 dvipdfmx depends on tetex-base | texlive-base-bin; however:
  Package tetex-base is not installed.
  Package texlive-base-bin is not configured yet.
 dvipdfmx depends on tetex-bin | texlive-base-bin; however:
  Package tetex-bin is not installed.
  Package texlive-base-bin is not configured yet.
dpkg: error processing dvipdfmx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended:
 texlive-fonts-recommended depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
 texlive-fonts-recommended depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-fonts-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pictures:
 texlive-pictures depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
 texlive-pictures depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-pictures (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pictures-doc:
 texlive-pictures-doc depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-pictures-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-base-bin-doc:
 texlive-base-bin-doc depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-base-bin-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended-doc:
 texlive-latex-recommended-doc depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-recommended-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pstricks:
 texlive-pstricks depends on texlive-generic-recommended (>= 2007-11); however:
  Package texlive-generic-recommended is not configured yet.
 texlive-pstricks depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
 texlive-pstricks depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-pstricks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-humanities:
 texlive-humanities depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-humanities (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
 texlive-latex-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended-doc:
 texlive-fonts-recommended-doc depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-fonts-recommended-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-extra:
 texlive-generic-extra depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
 texlive-generic-extra depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-generic-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-beamer:
 latex-beamer depends on tetex-extra | texlive-latex-base; however:
  Package tetex-extra is not installed.
  Package texlive-latex-base is not configured yet.
dpkg: error processing latex-beamer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base-doc:
 texlive-latex-base-doc depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-base-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-xcolor:
 latex-xcolor depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing latex-xcolor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pgf:
 pgf depends on latex-xcolor (>= 2.00-1); however:
  Package latex-xcolor is not configured yet.
 pgf depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing pgf (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgdbm-dev
 gawk
 ufw
 ghostscript
 perl
 cups-bsd
 tex-common
 m4
 libroman-perl
 cups
 prosper
 texi2html
 debiandoc-sgml
 texlive-base-bin
 preview-latex-style
 libsgmls-perl
 doc-base
 sgmlspl
 tipa
 autoconf
 texlive-common
 texlive-latex-extra
 libtext-format-perl
 automake
 lmodern
 texlive-latex-extra-doc
 texlive-humanities-doc
 texlive-base
 texlive-generic-recommended
 texlive-doc-base
 texlive-pstricks-doc
 dvipdfmx
 texlive-fonts-recommended
 texlive-pictures
 texlive-pictures-doc
 texlive-base-bin-doc
 texlive-latex-recommended-doc
 texlive-latex-recommended
 texlive-pstricks
 texlive-humanities
 texlive-latex-base
 texlive-fonts-recommended-doc
 texlive-generic-extra
 latex-beamer
 texlive-latex-base-doc
 latex-xcolor
 pgf

I hope this is useful. Let me know if there is anything else I can post/do that will help. I'm particularly keen to find a general way to solve this kind of problem or some reliable way to say goodbye to the package issues that seem to precipitate these problems.

---

### Post by Anicka on 2009-01-07
Looks very much as it is perl being the bad guy (a lot of "however, package perl is not yet configured") You can check this by running "dpkg -C" (note the capital C). It should tell you what needs to be done, but it has a tendency not to work very well with complex problems like this.

So you should try this:```
sudo dpkg --configure --force-configure-any perl
```That will try to configure perl, but also any package that perl depends on or that could help to configure it. If that works you can try to rerun```
sudo dpkg --configure -a
```if not you can try to rerun the same command but also add any package that the error message is complaining about. If that is not enough, try```
sudo dpkg --configure --force-all perl
```That really should work, but if not the killer command should be```
sudo dpkg --configure --force-all -a
```That will try even harder to configure the broken packages, but could be hazardous.

Any info that you want about dpkg , you can find by typing dpkg --help, dpkg --force-help or man dpkg.

Good luck and let me know what happens.

---

### Post by PaulWhipp on 2009-01-07
I agree that issues with the perl update seem to be the root cause and are probably the key thing I need to fix in order to get everything else sorted. At the moment all the install/clean up attempts seem to be hitting the same "errors were encountered while processing:..." problem.

Thanks for those commands The results of my trying them are at the bottom of this post.

Given the errors I thought I'd try working up the 'dependency tree', starting with reinstalling any of the packages that the problem packages depend upon that have no dependencies. That doesn't seem to work though - it just shuffles the order they appear on the error while processing list.


~ $ sudo dpkg --configure --force-configure-any perl
Setting up perl (5.10.0-11.1ubuntu2.2) ...
Segmentation fault
dpkg: error processing perl (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 perl

~ $ sudo dpkg --configure --force-all perl
Setting up perl (5.10.0-11.1ubuntu2.2) ...
Segmentation fault
dpkg: error processing perl (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 perl

The 'sudo dpkg --configure --force-all -a' command must have overflowed a buffer because this is the entire contents of the terminal window after invoking it:

dpkg: error processing gawk (--configure):
 subprocess post-installation script returned error exit status 139
Setting up ufw (0.23.2) ...
dpkg: error processing ufw (--configure):
 subprocess post-installation script killed by signal (Segmentation fault)
Setting up ghostscript (8.63.dfsg.1-0ubuntu6.1) ...
Segmentation fault
dpkg: error processing ghostscript (--configure):
 subprocess post-installation script returned error exit status 139
Setting up perl (5.10.0-11.1ubuntu2.2) ...
Segmentation fault
dpkg: error processing perl (--configure):
 subprocess post-installation script returned error exit status 139
Setting up cups-bsd (1.3.9-2ubuntu6) ...
dpkg: error processing cups-bsd (--configure):
 subprocess post-installation script killed by signal (Segmentation fault)
Setting up tex-common (1.11) ...
dpkg: error processing tex-common (--configure):
 subprocess post-installation script killed by signal (Segmentation fault)
Setting up m4 (1.4.11-1) ...
Segmentation fault
dpkg: error processing m4 (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: texi2html: dependency problems, but configuring anyway as you request:
 texi2html depends on perl; however:
  Package perl is not configured yet.
Setting up texi2html (1.78-1) ...
Segmentation fault
dpkg: error processing texi2html (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dvipdfmx: dependency problems, but configuring anyway as you request:
 dvipdfmx depends on tetex-base | texlive-base-bin; however:
  Package tetex-base is not installed.
 dvipdfmx depends on tetex-bin | texlive-base-bin; however:
  Package tetex-bin is not installed.
Setting up dvipdfmx (1:20071115-1) ...

Configuration file `/etc/texmf/texmf.d/80DVIPDFMx.cnf', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvipdfm/glyphlist.txt', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvipdfm/pdfglyphlist.txt', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvipdfm/cid-x.map', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvipdfm/dvipdfmx.cfg', does not exist on system.
Installing new config file as you request.
update-texmf: Basic configuration file /etc/texmf/texmf.d/05TeXMF.cnf missing.
Exiting.
warning: Configuration file texmf.cnf not found! Searched these directories:
/usr/share/texmf/web2c:/usr/share/texmf-texlive/web2c:/usr/local/share/texmf/web2c
Trying to proceed...
mktexlsr: Done.

dpkg: libsgmls-perl: dependency problems, but configuring anyway as you request:
 libsgmls-perl depends on perl (>= 5.6.0-16); however:
  Package perl is not configured yet.
Setting up libsgmls-perl (1.03ii-32) ...
dpkg: doc-base: dependency problems, but configuring anyway as you request:
 doc-base depends on perl (>= 5.6.0-16); however:
  Package perl is not configured yet.
Setting up doc-base (0.8.16) ...
Illegal instruction
dpkg: error processing doc-base (--configure):
 subprocess post-installation script returned error exit status 132
dpkg: sgmlspl: dependency problems, but configuring anyway as you request:
 sgmlspl depends on perl; however:
  Package perl is not configured yet.
Setting up sgmlspl (1.03ii-32) ...
dpkg: autoconf: dependency problems, but configuring anyway as you request:
 autoconf depends on perl (>> 5.005); however:
  Package perl is not configured yet.
 autoconf depends on m4 (>= 1.4.8); however:
  Package m4 is not configured yet.
Setting up autoconf (2.61-7ubuntu1) ...

Configuration file `/etc/emacs/site-start.d/50autoconf.el', does not exist on system.
Installing new config file as you request.
Segmentation fault
dpkg: error processing autoconf (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: texlive-common: dependency problems, but configuring anyway as you request:
 texlive-common depends on tex-common (>= 1.8); however:
  Package tex-common is not configured yet.
Setting up texlive-common (2007.dfsg.1-2) ...

dpkg: libtext-format-perl: dependency problems, but configuring anyway as you request:
 libtext-format-perl depends on perl (>= 5.6.0-16); however:
  Package perl is not configured yet.
Setting up libtext-format-perl (0.52-21) ...
dpkg: automake: dependency problems, but configuring anyway as you request:
 automake depends on autoconf (>= 2.60); however:
  Package autoconf is not configured yet.
Setting up automake (1:1.10.1-3) ...
Segmentation fault
dpkg: error processing automake (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: lmodern: dependency problems, but configuring anyway as you request:
 lmodern depends on tex-common (>= 1.10); however:
  Package tex-common is not configured yet.
Setting up lmodern (1.010x-5) ...

Configuration file `/etc/X11/fonts/Type1/lmodern.scale', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/updmap.d/10lmodern.cfg', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/defoma/hints/lmodern.hints', does not exist on system.
Installing new config file as you request.
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing lmodern (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: libroman-perl: dependency problems, but configuring anyway as you request:
 libroman-perl depends on perl (>= 5.6.0-16); however:
  Package perl is not configured yet.
Setting up libroman-perl (1.22-2) ...
Setting up texlive-latex-extra-doc (2007.dfsg.2-1ubuntu1) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-latex-extra-doc (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: cups: dependency problems, but configuring anyway as you request:
 cups depends on ghostscript; however:
  Package ghostscript is not configured yet.
Setting up cups (1.3.9-2ubuntu6) ...
Installing new version of config file /etc/apparmor.d/usr.sbin.cupsd ...
dpkg: error processing cups (--configure):
 subprocess post-installation script killed by signal (Segmentation fault)
Setting up texlive-humanities-doc (2007.dfsg.2-1ubuntu1) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-humanities-doc (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: debiandoc-sgml: dependency problems, but configuring anyway as you request:
 debiandoc-sgml depends on perl (>= 5.6.0-16); however:
  Package perl is not configured yet.
Setting up debiandoc-sgml (1.2.9) ...

Setting up texlive-doc-base (2007.dfsg.1-1) ...

update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-doc-base (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-pstricks-doc (2007.dfsg.2-1ubuntu1) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-pstricks-doc (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: texlive-base-bin: dependency problems, but configuring anyway as you request:
 texlive-base-bin depends on perl; however:
  Package perl is not configured yet.
Setting up texlive-base-bin (2007.dfsg.2-3ubuntu1) ...

Configuration file `/etc/texmf/dvipdfm/config/config', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/alt-rule.pro', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/canonex.cfg', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/config.bakoma', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/config.canonex', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/config.cms', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/config.cx', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/config.deskjet', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/config.dvired', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/config.epson', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/config.ibmvga', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/config.ljfour', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/config.luc', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/config.mbn', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/config.mga', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/config.mirrorprint', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/config.ot2', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/config.ps', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/config.qms', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/config.toshiba', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/config.unms', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/config.xyp', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/cx.cfg', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/deskjet.cfg', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/dfaxhigh.cfg', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/dvired.cfg', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/epson.cfg', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/ibmvga.cfg', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/ljfour.cfg', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/qms.cfg', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/dvips/config/toshiba.cfg', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/tex/generic/config/pdftexconfig.tex', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/xdvi/XDvi', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/xdvi/xdvi.cfg', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/texdoctk/texdocrc.defaults', does not exist on system.
Installing new config file as you request.
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-base-bin (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: preview-latex-style: dependency problems, but configuring anyway as you request:
 preview-latex-style depends on tex-common; however:
  Package tex-common is not configured yet.
 preview-latex-style depends on texlive-base-bin; however:
  Package texlive-base-bin is not configured yet.
Setting up preview-latex-style (11.84-0ubuntu2) ...
warning: Configuration file texmf.cnf not found! Searched these directories:
/usr/share/texmf/web2c:/usr/share/texmf-texlive/web2c:/usr/local/share/texmf/web2c
Trying to proceed...
mktexlsr: Done.

Setting up texlive-pictures-doc (2007.dfsg.1-2) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-pictures-doc (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-base-bin-doc (2007.dfsg.2-3ubuntu1) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-base-bin-doc (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-latex-recommended-doc (2007.dfsg.1-2) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-latex-recommended-doc (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-fonts-recommended-doc (2007.dfsg.1-2) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-fonts-recommended-doc (--configure):
 subprocess post-installation script returned error exit status 1
Setting up texlive-latex-base-doc (2007.dfsg.1-2) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-latex-base-doc (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: texlive-base: dependency problems, but configuring anyway as you request:
 texlive-base depends on texlive-doc-base (>= 2007); however:
  Package texlive-doc-base is not configured yet.
 texlive-base depends on texlive-base-bin (>= 2007-13); however:
  Package texlive-base-bin is not configured yet.
Setting up texlive-base (2007.dfsg.1-2) ...

Configuration file `/etc/texmf/metafont/misc/modes.mf', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/updmap.d/10texlive-base.cfg', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/language.d/09texlive-base.cnf', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/fmt.d/10texlive-base.cnf', does not exist on system.
Installing new config file as you request.
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-base (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: texlive-generic-recommended: dependency problems, but configuring anyway as you request:
 texlive-generic-recommended depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
Setting up texlive-generic-recommended (2007.dfsg.1-2) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-generic-recommended (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: texlive-fonts-recommended: dependency problems, but configuring anyway as you request:
 texlive-fonts-recommended depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
Setting up texlive-fonts-recommended (2007.dfsg.1-2) ...

Configuration file `/etc/texmf/updmap.d/10texlive-fonts-recommended.cfg', does not exist on system.
Installing new config file as you request.
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-fonts-recommended (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: texlive-pictures: dependency problems, but configuring anyway as you request:
 texlive-pictures depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
Setting up texlive-pictures (2007.dfsg.1-2) ...

Configuration file `/etc/texmf/tex/latex/pict2e/pict2e.cfg', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/updmap.d/10texlive-pictures.cfg', does not exist on system.
Installing new config file as you request.
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-pictures (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: texlive-pstricks: dependency problems, but configuring anyway as you request:
 texlive-pstricks depends on texlive-generic-recommended (>= 2007-11); however:
  Package texlive-generic-recommended is not configured yet.
 texlive-pstricks depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
Setting up texlive-pstricks (2007.dfsg.2-1ubuntu1) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-pstricks (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: texlive-latex-base: dependency problems, but configuring anyway as you request:
 texlive-latex-base depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
Setting up texlive-latex-base (2007.dfsg.1-2) ...

Configuration file `/etc/texmf/tex/latex/config/color.cfg', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/tex/latex/config/graphics.cfg', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/tex/latex/config/hyperref.cfg', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/updmap.d/10texlive-latex-base.cfg', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/fmt.d/10texlive-latex-base.cnf', does not exist on system.
Installing new config file as you request.
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-latex-base (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: texlive-generic-extra: dependency problems, but configuring anyway as you request:
 texlive-generic-extra depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
Setting up texlive-generic-extra (2007.dfsg.2-1ubuntu1) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-generic-extra (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: texlive-latex-extra: dependency problems, but configuring anyway as you request:
 texlive-latex-extra depends on texlive-pictures (>= 2007-11); however:
  Package texlive-pictures is not configured yet.
 texlive-latex-extra depends on texlive-latex-base (>= 2007-11); however:
  Package texlive-latex-base is not configured yet.
Setting up texlive-latex-extra (2007.dfsg.2-1ubuntu1) ...

Configuration file `/etc/texmf/tex/latex/contour/contour.cfg', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/texmf/updmap.d/10texlive-latex-extra.cfg', does not exist on system.
Installing new config file as you request.
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-latex-extra (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: texlive-latex-recommended: dependency problems, but configuring anyway as you request:
 texlive-latex-recommended depends on texlive-latex-base (>= 2007-11); however:
  Package texlive-latex-base is not configured yet.
Setting up texlive-latex-recommended (2007.dfsg.1-2) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-latex-recommended (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: texlive-humanities: dependency problems, but configuring anyway as you request:
 texlive-humanities depends on texlive-latex-base (>= 2007-11); however:
  Package texlive-latex-base is not configured yet.
Setting up texlive-humanities (2007.dfsg.2-1ubuntu1) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing texlive-humanities (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: tipa: dependency problems, but configuring anyway as you request:
 tipa depends on texlive-base-bin; however:
  Package texlive-base-bin is not configured yet.
 tipa depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
Setting up tipa (2:1.3-12) ...

Configuration file `/etc/texmf/updmap.d/20tipa.cfg', does not exist on system.
Installing new config file as you request.
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing tipa (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: prosper: dependency problems, but configuring anyway as you request:
 prosper depends on ghostscript; however:
  Package ghostscript is not configured yet.
 prosper depends on tex-common (>= 0.7); however:
  Package tex-common is not configured yet.
 prosper depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 prosper depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
 prosper depends on texlive-pstricks; however:
  Package texlive-pstricks is not configured yet.
Setting up prosper (1.00.4+cvs.2007.05.01-3) ...
update-updmap: cannot read /etc/texmf/updmap.d/00updmap.cfg
dpkg: error processing prosper (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: latex-xcolor: dependency problems, but configuring anyway as you request:
 latex-xcolor depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
Setting up latex-xcolor (2.11-1) ...
warning: Configuration file texmf.cnf not found! Searched these directories:
/usr/share/texmf/web2c:/usr/share/texmf-texlive/web2c:/usr/local/share/texmf/web2c
Trying to proceed...
mktexlsr: Done.

dpkg: pgf: dependency problems, but configuring anyway as you request:
 pgf depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
Setting up pgf (2.00-1) ...
warning: Configuration file texmf.cnf not found! Searched these directories:
/usr/share/texmf/web2c:/usr/share/texmf-texlive/web2c:/usr/local/share/texmf/web2c
Trying to proceed...
mktexlsr: Done.

dpkg: latex-beamer: dependency problems, but configuring anyway as you request:
 latex-beamer depends on tetex-extra | texlive-latex-base; however:
  Package tetex-extra is not installed.
  Package texlive-latex-base is not configured yet.
Setting up latex-beamer (3.07-1ubuntu1) ...
warning: Configuration file texmf.cnf not found! Searched these directories:
/usr/share/texmf/web2c:/usr/share/texmf-texlive/web2c:/usr/local/share/texmf/web2c
Trying to proceed...
mktexlsr: Done.

Processing triggers for menu ...
Errors were encountered while processing:
 libgdbm-dev
 gawk
 ufw
 ghostscript
 perl
 cups-bsd
 tex-common
 m4
 texi2html
 doc-base
 autoconf
 automake
 lmodern
 texlive-latex-extra-doc
 cups
 texlive-humanities-doc
 texlive-doc-base
 texlive-pstricks-doc
 texlive-base-bin
 texlive-pictures-doc
 texlive-base-bin-doc
 texlive-latex-recommended-doc
 texlive-fonts-recommended-doc
 texlive-latex-base-doc
 texlive-base
 texlive-generic-recommended
 texlive-fonts-recommended
 texlive-pictures
 texlive-pstricks
 texlive-latex-base
 texlive-generic-extra
 texlive-latex-extra
 texlive-latex-recommended
 texlive-humanities
 tipa
 prosper
~ $

---

### Post by stchman on 2009-01-07
If your system works the way you want, you can always turn automatic updates off for good.  Go to 

System--->Administration--->Update Manager

There should be an option to turn off updates.

---

### Post by PaulWhipp on 2009-01-07
Tempting. I hate leaving problems unfixed though and I'm sure some of those updates must be useful.

Does anyone know where there is some *real* documentation on dpkg. I've googled and found lots of brief guides and the manual entry. I'd hate to think that the next step is to go directly to the source code.

dpkg appears to store a list of configuration actions or triggers that are retried as new packages are installed. This makes sense to allow for configuration dependencies but in many cases (mine at least), something in this list is repeatedly failing with a segmentation fault. If I could review the list and dig into dpkg's behaviour more deeply I might be able to come up with a general approach to solving this type of issue.

---

### Post by stchman on 2009-01-08
I apologize, you have to go to:

System--->Administration--->Software Sources and click the Update tab.

There are boxes that can be unchecked for updates.

---

### Post by PaulWhipp on 2009-01-08
I've set updates to only happen weekly but I don't want to turn them off. The security updates can be important, particularly as I sometimes run websites off my local machine for testing purposes.

I need to fix the broken configuration and I need to learn enough about it to be able to fix these update issues in future.

---

### Post by Anicka on 2009-01-08
Hallo!

I have found a new approach that you could try. [http://ubuntuforums.org/showthread.php?t=942572](http://ubuntuforums.org/showthread.php?t=942572)
In this thread there are some things that you can try. Look especially at the posts 6, 16 and 12+14. Of course for you it would be the perl package and not the libc6.

---

### Post by cariboo on 2009-01-08
The first thing you should do is to go to System-->Administration-->Synaptic Package Manager-->Edit-->Fix Broken Packages and completely remove all the broken packages. Next go to Settings-->Repositories, then click the download from dropdown and select other, click Select Best Server and let it run through all the servers, when it is  done click Choose Server, then let it update.

When the update is done click the status button, then highlight Installed Upgradable, next click Mark all Upgrades. Then click apply and follow the prompts.

Jim

---

### Post by PaulWhipp on 2009-01-08
Thanks Anicka, that post looks very interesting. I'll go through it in detail and post what I find here.

---

### Post by PaulWhipp on 2009-01-08
Thanks Jim, no broken packages are shown for fixing.

---

### Post by Elfy on 2009-01-08
You could run 

```
sudo dpkg -C
```

That should give you a bit more information about what is required, -C is audit.
Depending on what gets reported you could also

```
sudo dpkg -s *packagename*
``` for those, thats hould give you some idea what can be done.

---

### Post by PaulWhipp on 2009-01-08
Thanks forestpixie. 'sudo dpkg -C' does give a more friendly looking summary of my problems (listed below).

The info from 'sudo dpkg -s <name>' is also clear and looks useful (I haven't listed these results because there are so many). Pretty much everything in the list reports 'install ok half-configured'.

The big question now is - how do I fix these 'half-configured' entries?

~ $ sudo dpkg -C
[sudo] password for paul: 
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 ghostscript-x        The GPL Ghostscript PostScript/PDF interpreter - X Displa
 apt-rdepends         Recursively lists package dependencies

The following packages are only half configured, probably due to problems
configuring them the first time. The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 prosper              LaTeX class for writing transparencies
 texlive-humanities-doc TeX Live: Documentation files for texlive-humanities
 texlive-base         TeX Live: Essential programs and files
 texlive-generic-recommended TeX Live: Miscellaneous generic macros
 texi2html            Convert Texinfo files to HTML
 texlive-doc-base     TeX Live: Base documentation
 texlive-pstricks-doc TeX Live: Documentation files for texlive-pstricks
 texlive-fonts-recommended TeX Live: Recommended fonts
 texlive-base-bin     TeX Live: Essential binaries
 texlive-pictures     TeX Live: Packages for drawings graphics
 libgdbm-dev          GNU dbm database routines (development files)
 texlive-pictures-doc TeX Live: Documentation files for texlive-pictures
 doc-base             utilities to manage online documentation
 gawk                 GNU awk, a pattern scanning and processing language
 texlive-base-bin-doc TeX Live: Documentation files for texlive-base-bin
 texlive-latex-recommended-doc TeX Live: Documentation files for texlive-latex-
 texlive-latex-recommended TeX Live: LaTeX recommended packages
 texlive-pstricks     TeX Live: PSTricks packages
 texlive-humanities   TeX Live: LaTeX support for the humanities
 tipa                 system for processing phonetic symbols in LaTeX
 texlive-latex-base   TeX Live: Basic LaTeX packages
 autoconf             automatic configure script builder
 texlive-fonts-recommended-doc TeX Live: Documentation files for texlive-fonts-
 texlive-generic-extra TeX Live: Miscellaneous extra generic macros
 texlive-latex-base-doc TeX Live: Documentation files for texlive-latex-base
 ufw                  program for managing a netfilter firewall
 texlive-latex-extra  TeX Live: LaTeX supplementary packages
 ghostscript          The GPL Ghostscript PostScript/PDF interpreter
 perl                 Larry Wall's Practical Extraction and Report Language
 automake             A tool for generating GNU Standards-compliant Makefiles
 cups-bsd             Common UNIX Printing System(tm) - BSD commands
 lmodern              scalable PostScript and OpenType fonts based on Computer 
 tex-common           common infrastructure for building and installing TeX
 m4                   a macro processing language
 texlive-latex-extra-doc TeX Live: Documentation files for texlive-latex-extra
 cups                 Common UNIX Printing System(tm) - server

---

### Post by Elfy on 2009-01-09
Looks a bit hellish, you say > Pretty much everything in the list reports 'install ok half-configured'. does that mean that some things say differently?

Try to deal with each seperately

```
sudo dpkg --configure ghostscript-x
sudo dpkg --configure apt-rdepends
```

Can you please use code tags around posts with long lists.

I showed someone else how to do so here - [http://ubuntuforums.org/showpost.php?p=6513105&postcount=6](http://ubuntuforums.org/showpost.php?p=6513105&postcount=6)

---

### Post by PaulWhipp on 2009-01-12
thanks forestpixie. If my machine wasn't generally still working OK I would truly be in hell.

I think its best to focus on one problem - I have a suspicion that perl is at the root of these issues because it was a perl upgrade that seemed to trigger the problems and it is a scripting language that is used a lot. So:
```
~ $ sudo dpkg --configure perl
Setting up perl (5.10.0-11.1ubuntu2.2) ...
Segmentation fault
dpkg: error processing perl (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 perl

```

Thought I'd try a reinstall but it dropped same into the same error message list I'm getting most of the time:

```

~ $ sudo apt-get install --reinstall perl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 23 not upgraded.
37 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Segmentation fault
Setting up gawk (1:3.1.6.dfsg-0ubuntu1) ...
Segmentation fault
dpkg: error processing gawk (--configure):
 subprocess post-installation script returned error exit status 139
Setting up perl (5.10.0-11.1ubuntu2.2) ...
Segmentation fault
dpkg: error processing perl (--configure):
 subprocess post-installation script returned error exit status 139
...

```

So - my revised problem is just to try to fix perl. If there is some way I can 'suspend' the package management's attempt to fix all the other stuff it might help but I'm open to any advice I can get or any pointer to documentation that will help me.

---

### Post by LowSky on 2009-01-12
you could always go into synaptic, track down perl, remove it, reboot then reinstall it.

---

### Post by PaulWhipp on 2009-01-12
Hi LowSky,

That is a good idea and it was one of the first things I thought to try.

There is an enormous list of dependencies relating to perl including firefox, gedit etc. that would have to be removed too.

If it comes to it I suppose I could list them all and then reinstall the lot but it would be a very big job that could well rival a complete reinstall of 8.10 so I'm saving this as a last but one resort.

Finding some way to effectively reinstall perl without hitting the segmentation fault is the key I think but I don't know how to do that yet.

---

### Post by kansasnoob on 2009-01-12
> **cariboo907 said:**
> the first thing you should do is to go to system-->administration-->synaptic package manager-->edit-->fix broken packages and completely remove all the broken packages. Next go to settings-->repositories, then click the download from dropdown and select other, click select best server and let it run through all the servers, when it is  done click choose server, then let it update.

When the update is done click the status button, then highlight installed upgradable, next click mark all upgrades. Then click apply and follow the prompts.

Jim

+1!

---

### Post by kansasnoob on 2009-01-12
Well, to me a picture is worth a thousand words! My 8.10 software sources:

[ATTACH]99664[/ATTACH]

[ATTACH]99665[/ATTACH]

[ATTACH]99666[/ATTACH]

I'm wondering if you're not getting updates that you shouldn't be?

Like maybe you "ticked" everything that could be "ticked"!

---

### Post by mc4man on 2009-01-12
There are 2 different perl versions in intrepid, why don't you take a look in synaptic and see which is installed. (Intrepid or Intrepid-updates (if you highlight it, under packages tab, is force version available?
Also tie that in with whether intrepid updates is enabled in software sources

---

### Post by PaulWhipp on 2009-01-13
Thanks kansasnoob.

I have had some issues with repositories but my settings are very similar to yours save that the server points to Australia and the updates are only set to be weekly.

---

### Post by PaulWhipp on 2009-01-13
Thanks mc4man,

Updates is enabled and I believe it was the attempt to update perl that started this nightmare.

I'm not sure what you mean by the 'packages tab' in synaptic but the perl package displays its version as 5.10.0-11ubuntu2

This is the package I believe need to either reinstall and configure or just configure (there may be others but this one would be a great start).

---

### Post by PaulWhipp on 2009-01-14
btw kansasnoob, I don't know if this is a feature of living a in Queensland but the 'select best server' does nothing. It hangs like this:

[IMG]http://www.paulwhippconsulting.com.au/images/posts/select_best_server.png[/IMG]

I gave it half an hour just in case it was being really slow.

I left it on the australian server option and proceeded with your instructions. There was a long list of installable upgrades.

As usual the upgrades failed with the crash and 'an error occurred' :
```
E: /var/cache/apt/archives/cups_1.3.9-2ubuntu6.1_i386.deb: subprocess dpkg-deb --control returned error exit status 2
E: /var/cache/apt/archives/nvidia-glx-177_177.82-0ubuntu0.1_i386.deb: subprocess pre-installation script returned error exit status 139
E: /var/cache/apt/archives/samba_2%3a3.2.3-1ubuntu3.4_i386.deb: subprocess new post-removal script returned error exit status 139
```

I think this is another symptom of the underlying configuration issues. 

However, when I went back to the installed (upgradable) list, it now only has cups and nvidia-glx-177 on it.

I tried again and it crashed again but no longer showed cups.

Hmm... third time lucky?
Sadly not -
```
E: /var/cache/apt/archives/samba_2%3a3.2.3-1ubuntu3.4_i386.deb: subprocess new post-removal script returned error exit status 139
E: /var/cache/apt/archives/nvidia-glx-177_177.82-0ubuntu0.1_i386.deb: subprocess pre-installation script returned error exit status 139
```

After this ```
dpkg -C
``` still reports pretty much the same long list of problems:

```
The following packages are in a mess due to serious problems during
installation. They must be reinstalled for them (and any packages
that depend on them) to function properly:
 samba                a LanManager-like file and printer server for Unix

The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 dnsutils             Clients provided with BIND
 openssl              Secure Socket Layer (SSL) binary and related cryptographi
 libopal-2.2          Open Phone Abstraction Library - successor of OpenH323
 bind9-host           Version of 'host' bundled with BIND 9.X
 transmission-gtk     free, lightweight BitTorrent client (graphical interface)
 smbclient            a LanManager-like simple client for Unix
 ghostscript-x        The GPL Ghostscript PostScript/PDF interpreter - X Displa
 libisccfg40          Config File Handling Library used by BIND
 libbind9-40          BIND9 Shared Library used by BIND
 libdns43             DNS Shared Library used by BIND
 apt-rdepends         Recursively lists package dependencies
 ntpdate              client for setting system time from NTP servers
 cups                 Common UNIX Printing System(tm) - server

The following packages are only half configured, probably due to problems
configuring them the first time. The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 prosper              LaTeX class for writing transparencies
 texlive-base         TeX Live: Essential programs and files
 texlive-generic-recommended TeX Live: Miscellaneous generic macros
 texi2html            Convert Texinfo files to HTML
 texlive-doc-base     TeX Live: Base documentation
 texlive-pstricks-doc TeX Live: Documentation files for texlive-pstricks
 texlive-fonts-recommended TeX Live: Recommended fonts
 texlive-base-bin     TeX Live: Essential binaries
 texlive-pictures     TeX Live: Packages for drawings graphics
 libgdbm-dev          GNU dbm database routines (development files)
 libssl0.9.8          SSL shared libraries
 texlive-pictures-doc TeX Live: Documentation files for texlive-pictures
 xterm                X terminal emulator
 doc-base             utilities to manage online documentation
 gawk                 GNU awk, a pattern scanning and processing language
 texlive-base-bin-doc TeX Live: Documentation files for texlive-base-bin
 texlive-latex-recommended-doc TeX Live: Documentation files for texlive-latex-

 texlive-latex-recommended TeX Live: LaTeX recommended packages
 texlive-pstricks     TeX Live: PSTricks packages
 texlive-humanities   TeX Live: LaTeX support for the humanities
 samba-common         Samba common files used by both the server and the client
 tipa                 system for processing phonetic symbols in LaTeX
 texlive-latex-base   TeX Live: Basic LaTeX packages
 autoconf             automatic configure script builder
 texlive-fonts-recommended-doc TeX Live: Documentation files for texlive-fonts-
 texlive-generic-extra TeX Live: Miscellaneous extra generic macros
 texlive-latex-base-doc TeX Live: Documentation files for texlive-latex-base
 ufw                  program for managing a netfilter firewall
 texlive-latex-extra  TeX Live: LaTeX supplementary packages
 ghostscript          The GPL Ghostscript PostScript/PDF interpreter
 perl                 Larry Wall's Practical Extraction and Report Language
 automake             A tool for generating GNU Standards-compliant Makefiles
 cups-bsd             Common UNIX Printing System(tm) - BSD commands
 lmodern              scalable PostScript and OpenType fonts based on Computer 
 tex-common           common infrastructure for building and installing TeX
 m4                   a macro processing language
 texlive-latex-extra-doc TeX Live: Documentation files for texlive-latex-extra
```

If only I could reinstall them!

So back to my question - how can I reinstall perl? If I can do one, I can probably do them all.

---

### Post by mc4man on 2009-01-14
What i meant was to see if there was a version of perl to force back to and what may happen if that was possible. (in other words force back to intrepid version if intrepid updates is installed


If you where to search it in synaptic, highlight perl and then in the synaptic panel click 'package' in the drop down is an option to 'force version'. If it's grayed out no version to force back to.

---

### Post by PaulWhipp on 2009-01-14
Thans mc4man, got it, tried it. same error occurs.

I've noticed that the text "running post installation trigger libc6" comes up just before the error, even though this package is not directly involved. Then we get something like (it doesn't really matter which package because any install is likely to generate a similar message):

[IMG]http://www.paulwhippconsulting.com.au/images/posts/Screenshot-8.png[/IMG]

---

### Post by mc4man on 2009-01-14
I should have tried that first, you can't force perl back due to perl-base, so actually nothing at all should have happened. (literally 

While it probably won't help you could try to reinstall perl-base and perl at the same time.

---

### Post by PaulWhipp on 2009-01-15
After doing the synaptic block of updates recommended earlier in this thread everything seemed much the same as before but I shut the machine down overnight.

It would not initialise X windows on the restart. I suspected the failed attempt to update the nvidia drivers so after removing my second monitor and using a basic xorg.conf with default (non nvidia) drivers I've got the machine back up.

Sadly I think there is no option but to reinstall. None of these package reinstall attempts are addressing the core issue which is the segmentation fault and/or 139 error that is occuring every time I try to reinstall/remove or install pretty much anything. It seems likely that the perl 'upgrade' caused this by failing at some critical stage.

I suppose the big issue is the fact that updates are not reversible. If an update is attempted and it fails, my system is broken. I can't undo and try the whole thing again. If only I didn't have to earn a living I'd happily spend a month or more digging into the depths of this issue. Hopefully someone at canonical will recognise that its this kind of failure that keeps ubuntu restricted to geeks (or wannabe geeks like me :))

Now I'm going to lose at least a day and probably several days work rebuilding this system. Perhaps this time I'll keep good enough logs so that it doesn't take me so long next time (much as I'd like to think there wont be a next time).

---

### Post by PaulWhipp on 2009-01-18
I've reinstalled the system and updated without issues.

However it was a long process, taking me most of the weekend, and I'm still not finished with a few things such as configuring subversion, mysql command line etc.

If you are unlucky enough to get into a similar mess:

Backup everything using 'cp -rvp ...' to an ext3 or ext2 drive. In my case a 27gb tarball would have been unmanageable for selective restoration. Lucky I tried it before relying on it. Other drive types (such as NTFS) will lose important permissions information associated with the files.

Make a separate back up of Evolution (use File | Backup settings...) - the folders will be restored in your home directory but your stored accounts information may be lost otherwise. All of the other built in applications seem fine working off the configuration information in the home directory hidden files.

It seems that packages are now installing without issues so it does look as though there was something broken deep in the old system. Now I'll never know.

Thanks to everyone who tried to help in this thread!

---

### Post by ellen.marie on 2009-01-19
Anicka, your reply to PaulWhipp and others was helpful to me...I, too, am having trouble with updates. I get an error message that states simply

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Can you tell me what I should do?  I am new to Ubuntu and NOT a "techy" person.

Also, as you wrote to someone, is it really OK to disable updates?  What might go wrong in the future if I don't install updates?

Thanks.

---

### Post by clive littlewood on 2009-01-19
Hi

It would have been better to start a new post but Hey

Open a terminal Apps > Accessories > Terminal

Then do what the error requested : sudo dpkg --configure -a

You will be asked for your password

Type this in (nothing will be shown in the terminal)

Then enter

Everything should now be OK          :)

Clive

---

### Post by PaulWhipp on 2009-01-19
Hi ellen.marie

Regarding turning updates off -

Updates are enhancements that generally improve the security of your system and fix any bugs existing with the applications you are using. They are considered by the developer to be important fixes (enhancements wait for the next release of ubuntu).

Their importance to the typical user is often very low or non existent but the developer has to worry about the 1 in 1000 users who might experience the security flaw or issue.

Your machine is pretty secure out of the box (ubuntu doesn't have anything to let the hackers get at your machine running by default and to date there has been almost no problem with viruses on desktop systems). I consider it a lot more secure than a standard Microsoft windows system, for example.

If you are happy with your system, you can turn updates off.

However, if you do need an update in future and you turn them on again, you are likely to be beset by a long list of updates.

Personally I keep updates turned on (set to once a fortnight) but, from the sound of it, if I were you I'd turn them off and just keep an eye out for the six monthly new ubuntu versions.

---

### Post by tomthumb99 on 2009-02-17
Does anybody have a road map or listing with the bare min 8.10 module/progs installs are needed or checked against under Synapse manager.  I too get crushed each time during an update install.  I wish the core programs would be marked, the brief description does not tell you if its core to the OS.  The "libc" install usually kills my whole X windows setup, takes 2-3 days to fix.  Yes, I run with nvidia restricted drivers but the install/upgrades should work with that. Last question, any work around the segementation fault.

---

### Post by PaulWhipp on 2009-02-17
Hi tomthumb99,

libc was the crux of the problems for me and the only way I fixed it in the end was a complete reinstall. The reinstallation was a pain but since then all of the updates have completed successfully without issue.

The last update included an update for libc6 and I did not have any issues with my display drivers (also nvidia restricted).

I think that the trouble is that once you have the segmentation fault problem on an update, its associated with triggers that may fire on any subsequent update (or new installation) and it can therefore screw all sorts of things up over time.

ubuntu desktop is intentionally a 'complete' installation like MS Windows with Office Pro bundled in for free. It includes a lot of applications you may not need but which might come in handy. If you can get your update problems resolved, I'd leave it alone unless you are really short of space or bandwidth.

If you do want to strip it down, once you've got your system in a state where you can install a package without errors, back it up. Then you could go through the applications removing any that you don't use. Once uninstalled, you wont get any updates relating to them. You can always reinstall them again later if you find you want to use them.

One word of warning on this - when I uninstalled Open office it took out a lot of fonts that the system assumes are present so I ended up with bizarre blank pop up boxes and menus. Installing OO3 did not put them back.

---

