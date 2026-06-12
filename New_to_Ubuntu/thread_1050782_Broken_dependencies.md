---
title: "Broken dependencies"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by itsvan on 2009-01-26
im running hardy heron

i try fixing it with this         sudo apt-get -f install
but get this

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libhtml-parser-perl: Depends: perlapi-5.10.0
  perl: Depends: perl-base (= 5.10.0-11.1ubuntu2.2) but 5.8.8-12ubuntu0.3 is installed
  uuid-dev: Depends: libuuid1 (= 1.41.3-1ubuntu1) but 1.40.8-2ubuntu2 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies


what can i do?? i cant upgrade or install anything :(

---

### Post by omkarwagh on 2009-01-26
well basically you have packages with their dependent packages of the right versions not installed.
try one of the following methods:-
1.install the correct version number of the package needed. e.g., perl-base (= 5.10.0-11.1ubuntu2.2). if it is not available in your repository, download it manually from a website(google for it. it's quite easy to find it). and then install it by double clicking on the .deb file you just downloaded.
2.force the errant packages to have a version number for which their dependencies are available. this can be done from the synaptic menu. 

this usually works for me.
regards

---

### Post by mc4man on 2009-01-26
You may want to take a moment to see why your trying to use Intrepid versions of perl and uuid-dev in Hardy. While you won't have much difficulty forcing a higher version of perl and it's few dependencies, that may cause issues with packages that depend on perl.
As far as uuid-dev I believe that will lead to needing a higher version of libc6 which will eventually cause some significant problems.

---

